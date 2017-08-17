---
layout: post
title:  "Australian Car Industry - some charts"
date:   2017-05-30 16:16:01 -0600
tags: car-industry visualisation tableau R ggplot time-series
description: Some visualisations of ABS car industry data
---

Some sample graphs created in ggplot (Fig 1) and Tableau (Fig 2 to 5) from 931401.xls (ABS dataset on Austalian Motor Car Sales - April 2017 - non seasonally adjusted data)

### Seasonal decomposition
![Time series]({{ site.baseurl | prepend:site.url}}/img/Totalsales-grouped.png){: .center-image }<b>Figure 1:</b> Seasonal decomposition - Total vehicle sales (with SUV and Passenger cars) (1994-2016)  [1024x747 213K]

In the year 2000, Australia introduced the GST ([https://www.taxsuperandyou.gov.au/node/133/take](https://www.taxsuperandyou.gov.au/node/133/take)). This may account for the signal around the year 2000 on the chart.

R file used to create chart: [https://github.com/axelk2014/carindustry/blob/master/carIndustry.R](https://github.com/axelk2014/carindustry/blob/master/carIndustry.R)

### Total Sales - stacked
![stacked bar chart]({{ site.baseurl | prepend:site.url}}/img/SalesNewMotorVehicles_AU.png){: .center-image }<b>Figure 2:</b> stacked bar chart - Australian Motor Vehicle Sales (1994-2017)   [8759x1000 1.3MB]

### Total Sales
![Time series]({{ site.baseurl | prepend:site.url}}/img/Totalsales.png){: .center-image }<b>Figure 3:</b> time series- Total Vehicle Sales (1994-2016)   [1000x638 203K]

### Total Passenger Car Sales
![Time series]({{ site.baseurl | prepend:site.url}}/img/PassengerSales.png){: .center-image }<b>Figure 4:</b> time series- Passenger Vehicle Sales (1994-2016)   [1000x638 214K]

### Total SUV Sales
![Time series]({{ site.baseurl | prepend:site.url}}/img/SUVsales.png){: .center-image }<b>Figure 5:</b> time series- Sports Utility Vehicle Sales (1994-2016)  [1000x638 160K]


| Source | URL         | Datetime |
|:-------------|:------------------|:------|
| ABS          | [http://www.abs.gov.au/AUSSTATS/abs@.nsf/DetailsPage/9314.0April%202017?OpenDocument](http://www.abs.gov.au/AUSSTATS/abs@.nsf/DetailsPage/9314.0April%202017?OpenDocument) |  2017-05-24 11:44am  |
