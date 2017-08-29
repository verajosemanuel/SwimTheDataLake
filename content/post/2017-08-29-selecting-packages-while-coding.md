---
title: Selecting packages while coding
author: jvera
date: '2017-08-29'
slug: selecting-packages-while-coding
categories:
  - packages
tags:
  - help
---

Sometimes, you must choose a package to achieve some results while you're coding. Let's say, you're wrangling data and noticed you need a quick way of getting the mode of a vector. Base R does not provides such a method/function, but we can get a package to make our life easier (mode is not a hard working function you can code, but let's use it for the sake of the hint described here).

My usual procedure is to reach RDocumentation website, search for _mode_ function, and found this three:

  - modeest
  - pracma
  - modes
  
Now, inside your preferred R code editor (hope you're using Rstudio) just use packagemetrics package to get info to compare:


```

library(packagemetrics)

mode_packages <- c("modeest","pracma","modes")

mode_metrics <- package_list_metrics(mode_packages)

metrics_table(mode_metrics)


```

This way you get a nifty table with some information about these packages  to help you choose.

![package metrics table](/images/mode.png)

