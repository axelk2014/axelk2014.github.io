---
layout: post
title:  "The Force effect"
date:   2017-12-28 14:54:01 -0600
tags: R ggplot
description: Can micro-transactions in EA games affect share price?
---

# Question: Did the added micro-transactions to EA Games Star Wars Battlefront 2 affect the share price?

If you are not a gamer, you may have missed the furore surrounding the release of Star Wars: Battlefront 2 on November 17, 2017.

Briefly, days before launch (after all the pre-launch game previews had been played and reviews had been written), Electronic Arts (EA) introduced a "micro-transaction" mechanic in the game. Players now had to spend money to receive upgrades, characters, and weapons "essential" to progress within the game - critically this 'feature' was not active for all the pre-release previews that were released.

It all kicked off with [this](https://www.reddit.com/r/StarWarsBattlefront/comments/7c6bjm/it_takes_40_hours_to_unlock_a_hero_spreadsheet/) Reddit post that detailed how many hours a gamer would have to play to get these upgrades vs spending money and receiving them.
People weren't happy. After spending ~$60 (USD) for game, it is reasonable to expect you can play the full game without additional expense.

So the internet blew up in fury, and EA games came under significant PR blowback, not only for the micro-transactions, but also for the tepid response to gamers concerns. Eventually, as the story goes, the noise got so loud, that EA reversed their decision and removed access to some the upgrades via micro-transactions and changed the playing time required to get the additional gear.

*There's more to the story and if interested, see the links below*

One thing that all the (negative) coverage stated was that EA games had introduced this game mechanic to appeal more to their shareholders, the implication being that increasing share price was the motivation behind this.
<hr>
**Note:** Micro-transactions are not a new thing in games, and many different publishers have got some sort of micro-transactions in their games;  gamers have not liked it. This particular issue blew up and became a bit of a focal point for micro-transactions as an issue.
<hr>


I decided to investigate: did the introduction of micro-transactions and the subsequent negative press affect the share price so much that it forced EA to change strategy on a newly released game?


## Top-selling video games ever
First let's get some context. According to wikipedia, this is the list of the top-selling games of all times (measured in units sold not revenue).

![BestSellingGames]({{ site.baseurl | prepend:site.url}}/img/1024x800_Listofbestsellinggames_publisher.png){: .center-image } <b>Figure 1: </b>List of best-selling games ever, coded by Publisher [1024x800 159K]

What this chart shows is a few things:
- the biggest selling game of all  is Tetris, followed by Minecraft (insert some comment here about the popularity of blocks)
- EA has a number of titles in the list but not near the top 5

## EA Games share performance with major game release dates

Disclosure: I am not a financial analyst or anything even close to it, so keep that in mind when reviewing the following analysis.

Let's review how the share price performed for EA games major releases over the last 10 years.

![Shareperformance]({{ site.baseurl | prepend:site.url}}/img/1024x680_shareperformance.png){: .center-image }<b>Figure 2: </b> EA share performance with major game release dates [1024x680 167K]

Looking only at this graph it does not seem that the release of any game results in a direct increase of share price. The increases seem to happen in between release dates.

Let's examine the share price in more detail.

### Detailed share performance
This table lists some of the major game release dates, with the share price on the day of release.

{% include stockpriceperformance.html %}

The sparklines show the share price performance in the 15 day trading period before and after the release. The blue and green dots show the maxima and minima respectively, and in column 4 ("- 15 days") the rightmost point in the sparkline is release day share price, and in column 5, it is the leftmost point.


### Insights:
- of the games sampled, less than half resulted in an increase in share price.
- where there was a gain, it was modest (single digits percentage points)
- the biggest decrease in share price was 15 days after FIFA10  (approx 11% decrease)
- the largest dollar value decrease was after the release of Star Wars Battlefront 2 of $-7.99
- from 2015, there was a big jump in share price (over 90%)



## Takeaway
Based on the sampled games, it suggests that the share price fell after Star Wars Battlefront 2 was released; however it also shows that the share price falls after most game releases.

The share performance chart (Figure 2) shows increases in share price in between game releases. It is possible that there are games I have not included in the visualisation that contributed to this, however FIFA, Battlefield and Star Wars would be considered major properties for EA. And of course there are likely many other factors not considered in this analysis that could affect share price.

So, did the micro-transaction increase share price ? Clearly not in this case, however does the introduction of micro-transactions improve the share performance in general? Further research would be required...

### Further research:
- Compare share price performance of other video game publishers (Nintendo, Rockstar)
- Understand the Video game sales cycle (is a "15 day after release date" a reasonable metric?)
- Detail the total revenue gained from sales (not just units sold)
- See if other listed games companies share prices are affected with games that do have micro-transactions


### Links:
- Original story on Reddit post that started it all: [https://www.theringer.com/features/2017/12/2/16725196/reddit-fighting-microtransaction-exploitation-in-video-games](https://www.theringer.com/features/2017/12/2/16725196/reddit-fighting-microtransaction-exploitation-in-video-games)
- Honest Game Trailers of [Star Wars Battlefront 2](https://www.youtube.com/watch?v=DreMDPj3s94) devotes a some time to this controversy
- big thanks to [this](https://leonawicz.github.io/HtmlWidgetExamples/ex_dt_sparkline.html) guy for the detailed post on using mixed sparkline tables in R
<br>
<br>

| Source | URL         | Datetime |
|:-------------|:------------------|:------|
| Nasdaq         | [http://www.nasdaq.com/symbol/ea/historical](http://www.nasdaq.com/symbol/ea/historical) |  2017-12-11 08:18am |
| wikipedia.org        |  [https://en.wikipedia.org/wiki/List_of_best-selling_video_games](https://en.wikipedia.org/wiki/List_of_best-selling_video_games) |  2017-12-04 12:30pm  |
| Game release dates      |  mix of Google and Wikipedia |  2017-12-04   |
