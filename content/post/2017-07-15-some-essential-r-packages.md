---
title: Some essential R packages
author: jvera
date: '2017-07-15'
slug: some-essential-r-packages
categories:
  - packages
tags: []
---

For me, there’s a bunch of packages considered as “essential” ‘cause in the end, sooner or later I use them in any project that involved opening the RStudio regardless of the type of issue that I’m trying to address.
At some point in the process I need to present preliminary data (knitr, rmarkdown, janitor), display graphs (ggplot2, ggthemes, ggThemeAssist, gridBase, grid, corrplot) or simply manipulate data (dplyr, tidyr, stringr).
So I use the same snippet to load them at the beginning of any script. [code snippet at the end of post]
I start loading pacman, that saves me the trouble of checking if the mentioned package is installed or not, and installs it and/or loads it in the environment as needed.
I will briefly comment on some of them:

- tidyverse: try install.packages (“tidyverse”) , it is the shortest way of installing following packages in a single call: ggplot2, dplyr, tidyr, readr, purr, tibble, hms, stringr, lubridate, forcats, DBI, haven, http, jsonlite, readxl, rvest , Xml2, modelr, broom.
Notice that loading through command library(tidyverse) only loads the essentials, namely: ggplot2, tibble, tidyr, readr, purrr, and dplyr.

- corrplot: my favorite option when plotting all the existing correlations in the data set.
rticles, rmdformats, tufte: Various additions and different themes to increase the available output formats. Especially for HTML and PDF.

- RDocumentation: adds the help documentation from this site inside the RStudio environment.
janitor: I love the way it helps, combined with magrittr, the exploratory analysis applied to any data set. I’ll talk more on this package in the future. Promise.

- formatR: Easy code formatting improves readability.

- ggThemeAssist: An excellent wizard to modify the parameters for your graphic objects generated with ggplot2.

- rio: Import and export data the easy way. Many different formats with an extremely simple syntax. It is a meta-package actually, that incorporates some of the best in this area.

```
if (!require(pacman)) install.packages(“pacman”)
p_load(“devtools”, “corrplot”, “tidyverse”, “knitr”, “RDocumentation”,
 “janitor”, “rticles”, “data.table”, “formatR”, “ggThemeAssist”, “ggthemes”,
 “rio”, “magrittr”, “microbenchmark”, “reshape2”, “rmarkdown”,
 “gridBase”, “grid”, “plyr” )
```