---
title: 'one function a day: filldown'
author: jvera
date: '2019-05-16'
slug: one-function-a-day-filldown
categories:
  - packages
tags:
  - data wrangling
---

Sometimes we need to fill the values in  a vector with previous values when data is missing.
I wrote some convoluted code to do that but, as usual, someone solved the very same problem in an elegant way.

Here comes the function `filldown` from package *MESS*

```r
library(MESS)

myVector <- c(3, NA, NA, NA, 4, NA, NA, 7, NA, NA)

filled.vector <- filldown(myVector)

filled.vector
 [1] 3 3 3 3 4 4 4 7 7 7
```

and done!