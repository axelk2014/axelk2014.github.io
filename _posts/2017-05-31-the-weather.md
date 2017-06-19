---
layout: post
title:  "The Weather -- (work in progress)"
date:   2017-06-19 16:16:01 -0600
tags: weather visualisation ggplot
description: An investigation on the accuracy of BOM forecasts
---

Work in progress - post continually updates.

To answer the question: How accurate is the weather forecast 6 days out?

Method: Scrape the 6 day forecast from bom.gov.au every day for a period of time (a year?) then analyse using various statistical tools to see how accurate their forecast is.

| Source | URL         | Datetime |
|:-------------|:------------------|:------|
| BOM          | [http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=123&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=086338](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=123&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=086338)|  every day  |
| BOM          |	[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=123&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=086338](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=123&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=086338)	|  every day  |
| BOM          |	[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=136&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=086338](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=136&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=086338)	|  every day  |
| BOM          |	[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=136&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=023090](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=136&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=023090)	|  every day  |
| BOM          |	[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=122&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=023090](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=122&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=023090)	|  every day  |
| BOM          |	[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=123&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=023090](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=123&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=023090)	|  every day  |
| BOM          |	[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=122&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=040913](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=122&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=040913)	|  every day  |
| BOM          |	[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=123&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=040913](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=123&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=040913)	|  every day  |
| BOM          |	[http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=136&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=040913](http://www.bom.gov.au/jsp/ncc/cdio/weatherData/av?p_nccObsCode=136&p_display_type=dailyDataFile&p_startYear=&p_c=&p_stn_num=040913)	|  every day  |
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


## Visualisations

Initially on this project, I used the defaults for ggplot charts:

The lighter background makes it more difficult to see the contrast between the thin lines (forecast data) with the ribbon (actual data). Specifically, the feature of interest in the chart is the overlap (and lack of overlap) between the ribbon and the lines.

![adelaide_day1]({{ site.baseurl | prepend:site.url}}/img/adelaide_Day-5_forecast_2017-06-12_zoomed.png)

So once the problem of the visualisation is identified, it was easier to explore options to overcome it. I landed on a dark background with bright lines, and decreased the opacity to 70%, which makes it easy to identify the difference between the forecast and the actual data.

![adelaide_day2]({{ site.baseurl | prepend:site.url}}/img/adelaide_Day-2_forecast_2017-06-18_chart.png)

However the chart only provides a limited understanding of how different (or inaccurate) the forecast is from the actual data. The interest for this visualisation is to see how the forecast improves (or not) as the forecasted day approaches. To do this, an animated view of the forecasted data vs the actual data will show how how the forecast data converges to actual.

#### Animations

For each chart below:
- Long dashed line in blue showing the date of the maximum temperature range (actual)
- short dashed line (coloured by day) showing the date of the maximum temperature range (forecast)  

| City | Link         | Dimensions |
|:-------------|:------------------|:------|
| Adelaide | [![Adelaide](https://axelk2014.github.io/img/adelaide_anim_tn.png)](https://axelk2014.github.io/img/adelaide_anim.gif){: .center-image } | 1024x745 GIF 512k|
| Brisbane | ![Brisbane](https://axelk2014.github.io/img/brisbane_anim.gif){: .center-image } | 1024x745 GIF 342k|
| Darwin | ![Darwin](https://axelk2014.github.io/img/darwin_anim.gif){: .center-image } | 1024x745 GIF 184k|
| Hobart | ![Hobart](https://axelk2014.github.io/img/hobart_anim.gif){: .center-image } | 1024x745 GIF 441k|
| Melbourne | ![Melbourne](https://axelk2014.github.io/img/melbourne_anim.gif){: .center-image } | 1024x745 GIF 498k|
| Perth | ![Perth](https://axelk2014.github.io/img/perth_anim.gif){: .center-image } | 1024x745 GIF 480k|
| Sydney | ![Sydney](https://axelk2014.github.io/img/sydney_anim.gif){: .center-image } | 1024x745 GIF 412k|


#### TODO
1. Visualise the data across cities
2. Create a visualisation for rainfall forecast vs rainfall actual
