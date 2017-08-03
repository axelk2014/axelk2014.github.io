---
layout: post
title:  "A view on Melbourne"
date:   2017-08-03 19:11:01 -0600
tags: geo-visualisation Python
description: A brief analysis on Melbourne data
custom_css: leaflet
custom_js: leaflet
---

A brief analysis on Melbourne CBD industry demographics

| Source | URL         | Datetime |
|:-------------|:------------------|:------|
| data.gov.au          | [http://data.gov.au/dataset/bars-and-pubs-with-patron-capacity](http://data.gov.au/dataset/bars-and-pubs-with-patron-capacity) |  2017-07-10 8:50pm  |
| data.gov.au          |  https://data.melbourne.vic.gov.au/Economy/Employment-by-block-by-industry/b36j-kiy4/data
](https://data.melbourne.vic.gov.au/Economy/Employment-by-block-by-industry/b36j-kiy4/data) |  2017-07-29 1:39pm  |

### Licensed venues: number of patrons
![Geo plot]({{ site.baseurl | prepend:site.url}}/img/Numberofpatrons.png){: .center-image } Number of licensed patrons by venue - Melbourne CBD [739x445 495K]

Python notebook create chart: [https://github.com/axelk2014/carindustry/blob/master/carIndustry.R](https://github.com/axelk2014/carindustry/blob/master/carIndustry.R)]

From the Melbourne data website:
"A team of up to 6 surveyors conducts a field survey which involves visiting every establishment in every building in the Census area (City of Melbourne municipality). Every commercial property is surveyed at least once every two years."

### Sample of industry types by employment - Melbourne Docklands
![stacked bar chart]({{ site.baseurl | prepend:site.url}}/img/CLUEplot.png){: .center-image } Melbourne city council areas - employment type   [800x600 78K]
