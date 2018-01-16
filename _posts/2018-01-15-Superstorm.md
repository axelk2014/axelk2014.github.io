---
layout: post
title:  "Superstorm"
date:   2018-01-15 16:16:01 -0600
tags: weather visualisation bash R ggplot
description: An investigation on the Melbourne 2017 "Superstorm"
---

Previous weather analysis link:
[here]({{ site.baseurl | prepend:site.url}}/_posts/2017-05-31-the-weather)

### Background

In the last week of November 2017, Victorian authorities, media and the Bureau of Meteorology collectively freaked out at the forecast of an imminent "Superstorm".

A sample of the coverage before and during:

- [Nov 30 - BOM warns Victoria to be hit by 'unprecedented' thunderstorms, flash flooding](http://www.abc.net.au/news/2017-11-29/thunderstorm-warning-issued-for-victoria/9207056)
>"Victoria is set to be drenched with up to three times its monthly rainfall average mostly over two days with "unprecedented" thunderstorms"
"Mr Williams said there could be rainfall of up to 300 millimetres in the state's north-east ranges."

- [Dec 1 - Melbourne weather: Victorians warned that worst of forecast super storm yet to come](http://www.theage.com.au/victoria/melbourne-weather-recordbreaking-rainfall-begins-its-journey-from-victorias-west-20171130-gzwd54.html)
>"Premier Daniel Andrews advised workers on Friday afternoon to head home early and said people needed to be vigilant and take the weather warnings seriously."

- [Dec 2 - Melbourne weather: Victorians warned not to be complacent as worst of super storm to hit on Saturday](http://www.theage.com.au/victoria/melbourne-weather-victorians-warned-not-to-be-complacent-as-worst-of-super-storm-to-hit-on-saturday-20171201-gzx9ge.html)
>"While Melbourne has so far escaped the worst of the storm, city residents have been warned to expect more rain on Saturday evening, bringing the risk of flash flooding."

Additionally, every phone registered in Victoria received a text message from the SES (State Emergency Service) on the 1st of December:
"SMS from VicSES. Flooding is expected across Victoria this weekend. Heaviest rain on Saturday. Check on family & friends. Stay informed"

<b>Note:</b> This is the first time ever, that the Victorian authorities have sent a text message to all phones. It was unprecedented and certainly raised the level of drama around this event.

To be fair, it is likely that the signals did warrant a response and Victoria's government and agencies don't have the best record for safety and managing emergencies, so erring on the side of caution is a good thing. So good on them.

Let's look at some charts....


### Rain rain

**Method:** Scrape the 6 day forecast from bom.gov.au every day for a period of time then compare with actuals (also downloaded from the BOM) to see how accurate their forecast is.

![Melbournerainfall_day4]({{ site.baseurl | prepend:site.url}}/img/1024x745_melbourne_Day-4_forecast_2018-01-15_chart.png)

What you are looking at here is a chart of actual recorded rainfall (darker blue columns) plotted against forecasted rainfall (columns off-white). This particular chart is the 4 day forecast, i.e What the BOM said about about Thursday on a Monday. The maximum values are labelled.

![Melbournerainfall_day2]({{ site.baseurl | prepend:site.url}}/img/1024x745_melbourne_Day-2_forecast_2018-01-15_chart.png)

This chart shows the same actuals data as above, but with the 2 Day forecast plotted against it.

![Melbournerainfall_difference_day2]({{ site.baseurl | prepend:site.url}}/img/1024x745_melbourne_Rainfall_vs_Forecast_Day-2_2018-01-15_difference_chart.png)

This plot shows the variation of the forecasted rainfall vs the actual rainfall. Note the large spike near the right hand side, this will become interesting later on....

For comparison, lets look at another city - Darwin:

![Darwinrainfall_day2]({{ site.baseurl | prepend:site.url}}/img/1024x745_darwin_Day-2_forecast_2018-01-15_chart.png)

2 points of interest:
1. There is a clearly delineated rainy season and dry season in Darwin.<br><br>
1. The forecasted level of rain did not approach the top 5 recorded rainfall days.

Further data would be needed to confirm, however the significant variability in rainfall forecasts is consisted in other major cities.


### Superstorm

Anecdotally, the Melbourne 2017 "Superstorm" was supposed to occur on Fri 1st Dec to Sunday 3rd Dec.

The forecasted rainfall for that week was relatively modest until a couple of days before:


#### Forecasts - Day 6 to Day 1

-- dotted red lines indicate dates of the "Superstorm"

| Forecast Day | Chart        | Dimensions |
|:-------------|:------------------|:------|
| <h3>6</h3> | [![Day6](https://axelk2014.github.io/img/1024x745_Nov-Dec_2017-melbourne_Day-6_forecast_2018-01-13_chart.png){: .center-image } | 1024x745 PNG 112k|
| <h3>5</h3> | [![Day5](https://axelk2014.github.io/img/1024x745_Nov-Dec_2017-melbourne_Day-5_forecast_2018-01-13_chart.png){: .center-image } | 1024x745 PNG 111k|
| <h3>4</h3> | [![Day4](https://axelk2014.github.io/img/1024x745_Nov-Dec_2017-melbourne_Day-4_forecast_2018-01-13_chart.png){: .center-image } | 1024x745 PNG 113k|
| <h3>3</h3> | [![Day3](https://axelk2014.github.io/img/1024x745_Nov-Dec_2017-melbourne_Day-3_forecast_2018-01-13_chart.png){: .center-image } | 1024x745 PNG 113k|
| <h3>2</h3> | [![Day2](https://axelk2014.github.io/img/1024x745_Nov-Dec_2017-melbourne_Day-2_forecast_2018-01-13_chart.png){: .center-image } | 1024x745 PNG 114k|
| <h3>1</h3> | [![Day1](https://axelk2014.github.io/img/1024x745_Nov-Dec_2017-melbourne_Day-1_forecast_2018-01-13_chart.png){: .center-image } | 1024x745 PNG 114k|


As you can see it was not until the 2 day forecast that the forecasted level of rain jumped significantly, and the day before wildly over-estimated rain levels.


## The Takeaway

- There is a significant increase in variability in rainfall forecast vs temperature forecast (see previous post on temperature forecasting [here]({{ site.baseurl | prepend:site.url}}/_posts/2017-05-31-the-weather))
- Even in locales where there is a strong cyclical pattern,  rainfall forecast is inaccurate.



<br>

---
