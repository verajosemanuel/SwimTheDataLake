---
title: 'one function a day: multiway tables with ftable'
author: jvera
date: '2019-05-23'
slug: one-function-a-day-multiway-tables-with-ftable
categories:
  - packages
tags:
  - data wrangling
---

it´s usual to make confusion tables or cross tables when we have vectors of same lenght to compute and cross classify them, but some other issues arise when we have several dimensions (more than two).

Since this is a common situation but it´s not so common to know the easy solution, so here comes `ftable` function from package *stats*.

Let´s use Titanic dataset for an example:

```r
data(Titanic)
ftable(Titanic)

                   Survived  No Yes
Class Sex    Age                   
1st   Male   Child            0   5
             Adult          118  57
      Female Child            0   1
             Adult            4 140
2nd   Male   Child            0  11
             Adult          154  14
      Female Child            0  13
             Adult           13  80
3rd   Male   Child           35  13
             Adult          387  75
      Female Child           17  14
             Adult           89  76
Crew  Male   Child            0   0
             Adult          670 192
      Female Child            0   0
          
```
