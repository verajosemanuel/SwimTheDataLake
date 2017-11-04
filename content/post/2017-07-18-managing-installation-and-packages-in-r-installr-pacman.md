---
title: 'managing installation and packages in R: installR & pacman'
author: jvera
date: '2017-07-18'
slug: managing-installation-and-packages-in-r-installr-pacman
categories:
  - packages
tags:
  - management
---

Mentioned yesterday the useful library _pacman_ , so a brief comment about it is due. But I'm going to recommend _installR_ for managing updates first (packages and R itself).  With a console command, and just for windows users, it's so easy to keep your Rstudio updated.

```r
install.packages(“installr”)
library(installr)

# with update command a wizard is opened, checking version and updating accordingly

updateR()
```

[link to InstallR vignette] (https://cran.r-project.org/web/packages/installr/installr.pdf)

I recommend to have a look at the vignette for many useful commands regarding this package.

Managing non installed packages that are used on your code is a bit more easily managed with Pacman (yes, THAT pacman)


```r
# installing (traditional way, just for checking pacman library)

if (!require(“pacman”)) install.packages(“pacman”)

# suppose your code needs tm, party, stringi, caret, e1071, randomforest and gbm

pacman::p_load( tm, party, stringi, caret, e1071, randomForest, gbm)
```
[link to pacman vignette] (https://cran.r-project.org/web/packages/pacman/vignettes/Introduction_to_pacman.html)

This way, you don’t have to issue a two step process to check if package is installed and load it.  Pacman does it for you, mananging installation and loading as needed. If package is installed, attaches it, if not, starts installation and loading.
