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
Sometimes you'd need to calculate date diffs from a vector or a data frame. It's very easy and I'll show you three different methods. Using dplyr and pipes, easy peasy!

Take into account that lubridate has three classes or different ways, to define time spans.

1. Duration: a span of time in seconds with no start time
2. Interval: same as duration, but having an associated start time
3. Period: time span between units larger than seconds (days, months, weeks, years...)

We'll be using three methods here: 
- simple substraction
- base difftime
- lubridate %--% Periods operator

```
# 

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