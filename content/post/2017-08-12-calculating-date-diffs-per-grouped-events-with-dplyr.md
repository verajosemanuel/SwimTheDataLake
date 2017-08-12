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
Sometimes you'd need to calculate rolling date diffs from a vector or a data frame. It's very easy and I'll show you three different methods. Using dplyr and pipes, easy peasy!

Take into account that lubridate has three classes or different ways, to define time spans.

1. Duration: a span of time in seconds with no start time
2. Interval: same as duration, but having an associated start time
3. Period: time span between units larger than seconds (days, months, weeks, years...)

We'll be using three methods here: 
  - simple substraction
  - base difftime
  - lubridate %--% Periods operator

```
library(magrittr)
library(dplyr)
library(lubridate)

event <- rep(letters[1:4],3)
dummy.var <- seq(1:12)
event.date <- sort(sample(seq(as.Date('2016/01/01'), as.Date('2016/12/31'), by="day"), 12))

df <- data.frame(event = event, dummy.var = dummy.var, event.date = event.date) %>%
  arrange(event, event.date, dummy.var) %>% 
  group_by(event) %>%
  mutate(date.before = lag(event.date, 1)) %>%
  mutate(tae.1 = event.date - lag(event.date, 1)) %>%
  mutate(tae.2 = difftime(event.date , lag(event.date, 1))) %>%
  mutate(tae.3 = as.duration(event.date %--% lag(event.date, 1))) %>% 
  mutate(tae.4 = tae.3 / ddays(1))
```

    event dummy.var event.date date.before    tae.1    tae.2                    tae.3 tae.4
   <fctr>     <int>     <date>      <date>   <time>   <time>           <S4: Duration> <dbl>
1       a         1 2016-01-29        <NA>  NA days  NA days                     <NA>    NA
2       a         5 2016-05-26  2016-01-29 118 days 118 days 10195200s (~16.86 weeks)  -118
3       a         9 2016-07-27  2016-05-26  62 days  62 days   5356800s (~8.86 weeks)   -62
4       b         2 2016-02-11        <NA>  NA days  NA days                     <NA>    NA
5       b         6 2016-07-03  2016-02-11 143 days 143 days 12355200s (~20.43 weeks)  -143
6       b        10 2016-09-06  2016-07-03  65 days  65 days   5616000s (~9.29 weeks)   -65
7       c         3 2016-03-22        <NA>  NA days  NA days                     <NA>    NA
8       c         7 2016-07-16  2016-03-22 116 days 116 days 10022400s (~16.57 weeks)  -116
9       c        11 2016-11-30  2016-07-16 137 days 137 days 11836800s (~19.57 weeks)  -137
10      d         4 2016-05-03        <NA>  NA days  NA days                     <NA>    NA
11      d         8 2016-07-17  2016-05-03  75 days  75 days  6480000s (~10.71 weeks)   -75
12      d        12 2016-12-05  2016-07-17 141 days 141 days 12182400s (~20.14 weeks)  -141