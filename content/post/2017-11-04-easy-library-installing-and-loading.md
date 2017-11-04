---
title: Easy library installing and loading
author: jvera
date: '2017-11-04'
slug: easy-library-installing-and-loading
categories:
  - packages
tags:
  - Rstudio
---
I tend to use package managers for library load and management: pacman

https://cran.r-project.org/web/packages/pacman/vignettes/Introduction_to_pacman.html

With pacman::p_load() instead of 5 lines of code to load 5 common packages, like this:

```R
library(dplyr)
library(tidyr)
library(Hmisc)
library(magrittr)
library(janitor)

```

You can write one line

```r
pacman::p_load(dplyr, tidyr, Hmisc, janitor, magrittr)
```

if the package is not available on the system, it will first install it (through install.packages), and only then try to load it again. Same as library installr

```r
installr::require2
```

All of this, on the very first part of any R file.