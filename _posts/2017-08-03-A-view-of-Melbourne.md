---
layout: post
title:  "A view on Melbourne"
date:   2017-08-03 19:11:01 -0600
tags: geo-visualisation Python R ggplot
description: A brief analysis on Melbourne data
custom_css: leaflet
custom_js: leaflet
---

A brief exploratory data anlysis on City of Melbourne industry and employment demographics

| Source | URL         | Datetime |
|:-------------|:------------------|:------|
| data.gov.au          | [http://data.gov.au/dataset/bars-and-pubs-with-patron-capacity](http://data.gov.au/dataset/bars-and-pubs-with-patron-capacity) |  2017-07-10 8:50pm  |
| data.gov.au          |  [https://data.melbourne.vic.gov.au/Economy/Employment-by-block-by-industry/b36j-kiy4/data](https://data.melbourne.vic.gov.au/Economy/Employment-by-block-by-industry/b36j-kiy4/data) |  2017-07-29 1:39pm  |
| City of Melbourne      |  [http://melbourne.geografia.com.au/industries](http://melbourne.geografia.com.au/industries) |  2017-08-05 7:17pm  |

### Licensed venues: number of patrons
![Geo plot]({{ site.baseurl | prepend:site.url}}/img/Numberofpatrons.png){: .center-image } Screenshot of visualisation - Number of licensed patrons by venue - Melbourne CBD [739x445 495K]

Code used to create chart: [https://github.com/axelk2014/afl-datablog/blob/master/Melbourne%20Venue%20map.ipynb](https://github.com/axelk2014/afl-datablog/blob/master/Melbourne%20Venue%20map.ipynb)

### Melbourne Employment numbers by industry
![bar chart]({{ site.baseurl | prepend:site.url}}/img/Melbourne_employmentnumbers.png){: .center-image } <i>source:http://melbourne.geografia.com.au/industries</i> <br>
Employment numbers by industry - City of Melbourne.  [1000x800 91K]

### Melbourne city Economic output by industry
![bar chart]({{ site.baseurl | prepend:site.url}}/img/Melbourne_economicoutput.png){: .center-image } <i>source:http://melbourne.geografia.com.au/industries</i> <br>
Economic output by industry - City of Melbourne.  [1000x800 96K]


### Sample of industry types by employment - Melbourne Docklands
![stacked bar chart]({{ site.baseurl | prepend:site.url}}/img/CLUEplot.png){: .center-image } Melbourne city council areas - employment type   [800x600 78K]



<b>From the City of Melbourne data website on industry census collection:</b><br>
<i>"A team of up to 6 surveyors conducts a field survey which involves visiting every establishment in every building in the Census area (City of Melbourne municipality). Every commercial property is surveyed at least once every two years."</i>
