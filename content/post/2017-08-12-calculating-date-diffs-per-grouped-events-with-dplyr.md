---
title: calculating date diffs per event with dplyr
author: jvera
date: '2017-08-12'
slug: calculating-date-diffs-per-grouped-events-with-dplyr
categories:
  - tricks
tags:
  - lubridate
  - dplyr
  - data wrangling
---
![](https://www.rstudio.com/wp-content/uploads/2015/01/dplyr-hexbin-logo.png)
![](http://hexb.in/hexagons/magrittr.png)
![](https://d21ii91i3y6o6h.cloudfront.net/gallery_images/from_proof/9300/small/1447175273/rstudio-hex-lubridate-dot-psd.png)

Sometimes you'd need to calculate rolling date diffs from a vector or a data frame when you're manipulating repeated events from different categories. It's very easy and I'll show you three different methods. Using dplyr and pipes, easy peasy!

Take into account that lubridate has three classes or different ways, to define time spans.

1. Duration: a span of time in seconds with no start time
2. Interval: same as duration, but having an associated start time
3. Period: time span between units larger than seconds (days, months, weeks, years...)

* We'll be using three methods here: 
  * simple substraction
  * base difftime
  * lubridate %--% Periods operator

```r
library(magrittr)
library(dplyr)
library(lubridate)

event <- rep(letters[1:4],3)
event.date <- sort(sample(seq(as.Date('2016/01/01'), as.Date('2016/12/31'), by="day"), 12))

df <- data.frame(event = event, event.date = event.date) %>%
  arrange(event, event.date) %>% 
  group_by(event) %>%
  mutate(previous = lag(event.date, 1)) %>%
  mutate(tae.1 = event.date - lag(event.date, 1)) %>%
  mutate(tae.2 = difftime(event.date , lag(event.date, 1))) %>%
  mutate(tae.3 = as.duration(event.date %--% lag(event.date, 1))) %>% 
  mutate(tae.4 = tae.3 / ddays(1))


      event event.date   previous    tae.1    tae.2                    tae.3 tae.4
   <fctr>     <date>     <date>   <time>   <time>           <S4: Duration> <dbl>
1       a 2016-02-03       <NA>  NA days  NA days                     <NA>    NA
2       a 2016-03-10 2016-02-03  36 days  36 days   3110400s (~5.14 weeks)   -36
3       a 2016-09-08 2016-03-10 182 days 182 days    15724800s (~26 weeks)  -182
4       b 2016-02-20       <NA>  NA days  NA days                     <NA>    NA
5       b 2016-06-26 2016-02-20 127 days 127 days 10972800s (~18.14 weeks)  -127
6       b 2016-09-11 2016-06-26  77 days  77 days     6652800s (~11 weeks)   -77
7       c 2016-03-02       <NA>  NA days  NA days                     <NA>    NA
8       c 2016-08-03 2016-03-02 154 days 154 days    13305600s (~22 weeks)  -154
9       c 2016-10-09 2016-08-03  67 days  67 days   5788800s (~9.57 weeks)   -67
10      d 2016-03-04       <NA>  NA days  NA days                     <NA>    NA
11      d 2016-08-15 2016-03-04 164 days 164 days 14169600s (~23.43 weeks)  -164
12      d 2016-11-16 2016-08-15  93 days  93 days  8035200s (~13.29 weeks)   -93
```