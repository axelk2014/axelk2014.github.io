---
layout: post
title:  "Critical divergence"
date:   2019-01-06 14:54:01 -0600
tags: python R
description: How much power do review sites hold?
---

# Introduction

Metacritic (https://www.metacritic.com/), is unlike other review site in that the power it seems to hold over the video games industry. Major game developers will often tie in developer bonuses based on achieving a desired Metacritic score. Wall Street analysts use Metacritic scores as a guide to how well a game will perform as the scores are often published before the release date (https://en.wikipedia.org/wiki/Metacritic)

"In other words, a developer’s priority is sometimes not just to make a good game, but to make a game that they think will resonate with reviewers."
https://www.kotaku.com.au/2013/04/metacritic-matters-how-review-scores-hurt-video-games/

There is therefore significant incentive in the industry to "game" (pun intended) the system. However trying to measure the extent to which developers would change a game for Metacritic scores would be impossible for various reasons, namely access to the relevant data like publishing contracts, bonuses, etc...

## Question: By examining solely the Metacritic stats quantitatively, could we show any irregularities between user review scores and critic review scores?

### Scope

Using only at the following dataset sourced from Kaggle [www.kaggle.com/destring/metacritic-reviewed-games-since-2000](https://www.kaggle.com/destring/metacritic-reviewed-games-since-2000), what insights can we get from the review scores, comparing principally the metacritic score (as scored by 'professional' game journalists) vs the userscore (from general users)

### Description of dataset

<b>Metascore</b>: number, range 0-100, score given by critic <br>
<b>Userscore</b>: number, transformed into range 0-100 (original data range from 0-10), score given by users<br>
<b>Genre</b>: character, type of game genre

### Hypotheses
- If the assignment of score is truly random, the distributions of the metascore and userscore will be similar

### Assumptions
- If review scores are gamed in anyway, the shape of the distributions of scores will be different because the scores will not be truly random.

To show the relationship between two variables, the review scores are plotted in a jointplot, with the metascore on the x-axis and the related userscore on the y-axis, we can compare the shape of the score distributions.

![MetascorevsUserscore]({{ site.baseurl | prepend:site.url}}/img/424x424_meta_vs_user.png){: .center-image }<br><b>Figure 1: </b> Jointplot metascore vs userscore [424x424 81K]

Pearson's correlation coefficient (or *<i>Pearson's r</i>*) shows a weak correlation between both review scores (a score closer to 1 or -1 would show a stronger correlation).

If we look at the Coefficient of Determination (aka the R-squared statistic), to see if the critic score ("metascore") has any predictive power of the user score. A high R-squared score (a value close to 1) this would indicate that user reviews follow a similar trend to critic reviews (in other words, critics and users broadly agree on a game.)

Calculating the R-squared value for the entire dataset:

``Total R-squared 0.0246375578588``

If we group by game genre, we get the following results:

```
R-squared by Genre

Genre
Action          0.177404
Adventure       0.336378
Fighting        0.252146
Misc            0.223836
Platform        0.010379
Puzzle          0.426471
Racing          0.106846
Role-Playing   -0.058194
Shooter        -0.039091
Simulation     -0.410312
Sports         -0.831556
Strategy       -1.366932
```

Let's examine the distribution of each score individually:

![FrequencyBoxplots]({{ site.baseurl | prepend:site.url}}/img/525x383_boxplots.png){: .center-image } <br><b>Figure 2: </b>Distribution of metascore and userscore [525x383 57K]

We see there is minor differences in min/max/median values.

Plotted as a frequency histogram:

![FrequencyHistograms]({{ site.baseurl | prepend:site.url}}/img/900x800_frequencyhistograms.png){: .center-image } <b>Figure 3: </b>Frequency Histograms of metascore and userscore with median, mean and skewness annotated [900x800 57K]

The userscore is more left skewed, showing there are more lower scored user reviews than critic reviews. I felt that annotating the kurtosis would be an unnecessary addition to the visualisation without providing any further insight.

### Distributions

There are a number of methods we can use to  compare distributions quantitatively.

If we create a QQ plot, we can see quickly if the distributions are normal - using the car::qqPlot function (not to be mistaken with the more common stats::qqnorm function):

```
library("car")

qqPlot(df.metacritic$metascore)
qqPlot(df.metacritic$userscore)
```

we get the following plots:

![QQplot_metascore]({{ site.baseurl | prepend:site.url}}/img/525x383_metascore_qqPlot.png){: .center-image } <br><b>Figure 4: </b> QQ plot of metascore distribution [525x383 33K]

![QQplot_userscore]({{ site.baseurl | prepend:site.url}}/img/525x383_userscore_qqPlot.png){: .center-image } <br><b>Figure 5: </b> QQ plot of userscore distribution [525x383 29K]

The blue line shows where the distribution of points would be if it was a normal curve, so we can safely say neither metascore or userscore are normal distributions.

To further confirm, we can run a Shapiro-Wilk normality test and/or an Anderson-Darling normality test. There are pros and cons to each statistic, and I've approached this by using both to help validate the result:

```
> shapiro.test(metascores)

	Shapiro-Wilk normality test

data:  metascores
W = 0.96478, p-value < 2.2e-16

> ad.test(metascores)

	Anderson-Darling normality test

data:  metascores
A = 43.186, p-value < 2.2e-16

> shapiro.test(userscores)

	Shapiro-Wilk normality test

data:  userscores
W = 0.91691, p-value < 2.2e-16

> ad.test(userscores)

	Anderson-Darling normality test

data:  userscores
A = 93.681, p-value < 2.2e-16
```

Assuming a 5% significance level, in all cases above <b>p<&#945;</b> is False, therefore we can reject the null hypothesis that the distributions are normal.

The final test we carry out is a two-sample [Kolmogorov-Smirnov](http://www.physics.csbsju.edu/stats/KS-test.html) test. This statistic tests the following null hypothesis:<br>
<center><i>H</i><sub>0</sub>: Both samples are taken from the same distribution.</center>

The results:

```
Two-sample Kolmogorov-Smirnov test

data:  df.metacritic$metascore and df.metacritic$userscore
D = 0.034772, p-value = 1.021e-13
alternative hypothesis: two-sided
```

Again, we see that since at p=0.05 the following statement is False: <br>
<b> p<&#945; </b>, therefore we can reject the null hypothesis that both samples are drawn from the same distribution.

**Insights:**
1. The jointplot shows similar distributions around scores and a weak correlation.
1. The R-squared statistic, for the total dataset or grouped by genre, shows that the metascore is a weak predictor of userscore
1. Both scores are not normal distributions
1. Both scores are not drawn from the same distribution.

The take-away from the final insight was a surprise - since the assumption is that the distribution of the critic scores and user review scores should follow a similar pattern if scores are assigned 'randomly' (with most reviews clustering around higher, more positive, scores) this would suggest further investigation would be required around Metacritic's scoring and weighting methodology.


### Links:
- link to repository for all source code used to generate plots and statistics: https://github.com/axelk2014/critical-divergence
- Reverse engineered Metacritic weighting [https://www.ign.com/boards/threads/metacritics-weighting-scale-revealed-warning-controversy-inside.452936591/](https://www.ign.com/boards/threads/metacritics-weighting-scale-revealed-warning-controversy-inside.452936591/)
- [www.kotaku.com.au/2013/04/metacritic-matters-how-review-scores-hurt-video-games/](https://www.kotaku.com.au/2013/04/metacritic-matters-how-review-scores-hurt-video-games/)

<br>
<br>


### Further research:
- Sentiment analysis of metacritic user reviews comparing to critic reviews to measure how much scores diverge
<br>
<br>




| Source | URL         | Datetime |
|:-------------|:------------------|:------|
| Kaggle         | [https://www.kaggle.com/destring/metacritic-reviewed-games-since-2000](https://www.kaggle.com/destring/metacritic-reviewed-games-since-2000) |  2018-12-02 12:58am |
| Transformed Kaggle dataset with standardised userscores       |  [https://raw.githubusercontent.com/axelk2014/publicdata/master/metacritic-results.csv](https://raw.githubusercontent.com/axelk2014/publicdata/master/metacritic-results.csv) |  2017-12-04 12:30pm  |
