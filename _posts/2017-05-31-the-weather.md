---
layout: post
title:  "The Weather -- (work in progress)"
date:   2018-05-22 16:16:01 -0600
tags: weather visualisation bash R ggplot
description: An investigation on the accuracy of BOM forecasts
---

<i>Original post written 19/6/17</i><br>
<i>Last updated: 2018-05-22</i>

Work in progress.

To answer the question: How accurate is the weather forecast 6 days out?

**Method:** Scrape the 6 day forecast from bom.gov.au every day for a period of time then compare with actuals (also downloaded from the BOM) to see how accurate their forecast is.

<br>

## Full temperature record

Initially on this project, I used the defaults for ggplot charts:

The lighter background makes it more difficult to see the contrast between the thin lines (forecast data) with the ribbon (actual data). Specifically, the feature of interest in the chart is the overlap (and lack of overlap) between the ribbon and the lines.

![adelaide_day1]({{ site.baseurl | prepend:site.url}}/img/adelaide_Day-5_forecast_2017-06-12_zoomed.png)

So once the problem of the visualisation is identified, it was easier to explore options to overcome it. I landed on a dark background with bright lines, and decreased the opacity to 70%, which makes it easy to identify the difference between the forecast and the actual data.

![adelaide_day2]({{ site.baseurl | prepend:site.url}}/img/adelaide_Day-2_forecast_2017-06-18_chart.png)

However the chart only provides a limited understanding of how different (or inaccurate) the forecast is from the actual data. The interest for this visualisation is to see how the forecast improves (or not) as the forecasted day approaches. To do this, an animated view of the forecasted data vs the actual data will show how how the forecast data converges to actual.

### Animations

For each chart below:
- Each animation shows the forecasted day range (thin coloured line counting down from 6 day forecast to 1 day forecast.
- Long dashed line in blue showing the date of the maximum temperature range (actual)
- Short dashed line (coloured by day) showing the date of the maximum temperature range (forecast)  

| City | Link         | Dimensions |
|:-------------|:------------------|:------|
| Adelaide | [![Adelaide](https://axelk2014.github.io/img/adelaide_anim_tn.png)](https://axelk2014.github.io/img/Adelaide_temp.gif){: .center-image } | 1200x600 GIF 696k|
| Brisbane | [![Brisbane](https://axelk2014.github.io/img/brisbane_anim_tn.png)](https://axelk2014.github.io/img/Brisbane_temp.gif){: .center-image } | 1200x600 GIF 341k|
| Darwin | [![Darwin](https://axelk2014.github.io/img/darwin_anim_tn.png)](https://axelk2014.github.io/img/Darwin_temp.gif){: .center-image } | 1200x600 GIF 175k|
| Hobart | [![Hobart](https://axelk2014.github.io/img/hobart_anim_tn.png)](https://axelk2014.github.io/img/Hobart_temp.gif){: .center-image } | 1200x600 GIF 460k|
| Melbourne | [![Melbourne](https://axelk2014.github.io/img/melbourne_anim_tn.png)](https://axelk2014.github.io/img/Melbourne_temp.gif){: .center-image } | 1200x600 GIF 516k|
| Perth | [![Perth](https://axelk2014.github.io/img/perth_anim_tn.png)](https://axelk2014.github.io/img/Perth_temp.gif){: .center-image } | 1200x600 GIF 637k|
| Sydney | [![Sydney](https://axelk2014.github.io/img/sydney_anim_tn.png)](https://axelk2014.github.io/img/Sydney_temp.gif){: .center-image } | 1200x600 GIF 421k|

<br>
## City based forecast

Looking at each city actual and forecast data, exactly how different is the forecast from the actual.

As data is supplied with minimum and maximum temperature, let's examine them separately.

To evaluate and compare, I created a side by side comparison. The "interest" of the chart is to see how each forecasted day compares to each other as well as the actual data.

Using the same colour schemes above, for aesthetic reasons only, I created the following:

| Type | Thumbnail link        | Dimensions |
|:-------------|:------------------|:------|
| Maximum | [![Total](https://axelk2014.github.io/img/total-maximum_tn.png)](https://axelk2014.github.io/img/total-maximum.png){: .center-image } | 1024x745 PNG 133k|
| Minimum | [![Brisbane](https://axelk2014.github.io/img/total-minimum_tn.png)](https://axelk2014.github.io/img/total-minimum.png){: .center-image } | 1024x745 PNG 128k|

### Note on colours***

With comparative boxplots, the primary interest is the thick "median" line. When you reverse the colours and the boxplot is drawn with white lines on a darker background, the 'contrast' seems less than dark lines on a lighter background.

And if I changed the boxplot line colours by forecasted day, you lose not only the number label for the median, but imply there is a difference between each boxplot (ignoring the values). The boxplots all measure the exact same thing, so coding the colours of the day to each boxplot does not add any information to the chart.

Compare them here:

| White lines/dark background | Coloured lines/dark background |
|:-------------|:------------------|
|[![whitelines](https://axelk2014.github.io/img/total-minimum-dark.png)](https://axelk2014.github.io/img/total-minimum-dark.png){: .center-image } | [![colourelines](https://axelk2014.github.io/img/total-minimum-darkv2.png)](https://axelk2014.github.io/img/total-minimum-dark_colouredlines.png){: .center-image } |

<br>

| Source | URL         | Datetime |
|:-------------|:------------------|:------|
| BOM - Melb max temp | [http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=122&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=086338](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=122&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=086338)|  ad hoc  |
| BOM - Melb min temp |	[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=123&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=086338](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=123&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=086338)	|  ad hoc  |
| BOM - Melb rainfall |	[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=136&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=086338](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=136&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=086338)	|  ad hoc |
| BOM - Adelaide rainfall |	[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=136&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=023090](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=136&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=023090)	|  ad hoc |
| BOM - Adelaide max temp |	[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=122&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=023090](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=122&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=023090)	|  ad hoc  |
| BOM - Adelaide min temp |	[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=123&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=023090](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=123&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=023090)	|  ad hoc  |
| BOM          |	[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=122&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=040913](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=122&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=040913)	|  ad hoc  |
| BOM          |	[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=123&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=040913](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=123&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=040913)	|  ad hoc  |
| BOM          |	[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=136&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=040913](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=136&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=040913)	|  ad hoc  |
| BOM          |	[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=122&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=014015](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=122&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=014015)	|  every day  |
| BOM          |	[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=123&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=014015](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=123&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=014015)	|  every day  |
| BOM          |	[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=136&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=014015](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=136&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=014015)	|  every day  |
| BOM          |	[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=122&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=094029](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=122&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=094029)	|  every day  |
| BOM          |	[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=123&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=094029](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=123&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=094029)	|  every day  |
| BOM          |	[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=136&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=094029](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=136&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=094029)	|  every day  |
| BOM          |	[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=122&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=009225](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=122&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=009225)	|  every day  |
| BOM          |	[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=123&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=009225](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=123&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=009225)	|  every day  |
| BOM          |	[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=136&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=009225](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=136&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=009225)	|  every day  |
| BOM          |	[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=122&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=066062](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=122&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=066062)	|  every day  |
| BOM          |	[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=123&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=066062](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=123&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=066062)	|  every day  |
| BOM          |	[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=136&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=066062](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=136&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=066062)	|  every day  |
|BOM |[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=122&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=086338](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=122&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=086338)|every day|
|BOM |[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=123&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=086338](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=123&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=086338)|every day|
|BOM |[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=136&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=086338](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=136&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=086338)|every day|
|BOM |[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=136&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=023090](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=136&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=023090)|every day|
|BOM |[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=122&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=023090](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=122&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=023090)|every day|
|BOM |[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=123&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=023090](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=123&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=023090)|every day|
|BOM |[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=122&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=040913](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=122&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=040913)|every day|
|BOM |[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=123&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=040913](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=123&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=040913)|every day|
|BOM |[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=136&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=040913](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=136&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=040913)|every day|
|BOM |[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=122&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=014015](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=122&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=014015)|every day|
|BOM |[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=123&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=014015](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=123&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=014015)|every day|
|BOM |[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=136&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=014015](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=136&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=014015)|every day|
|BOM |[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=122&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=094029](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=122&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=094029)|every day|
|BOM |[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=123&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=094029](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=123&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=094029)|every day|
|BOM |[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=136&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=094029](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=136&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=094029)|every day|
|BOM |[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=122&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=009225](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=122&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=009225)|every day|
|BOM |[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=123&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=009225](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=123&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=009225)|every day|
|BOM |[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=136&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=009225](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=136&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=009225)|every day|
|BOM |[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=122&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=066062](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=122&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=066062)|every day|
|BOM |[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=123&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=066062](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=123&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=066062)|every day|
|BOM |[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=136&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=066062](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=136&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=066062)|every day|

<br>

---
