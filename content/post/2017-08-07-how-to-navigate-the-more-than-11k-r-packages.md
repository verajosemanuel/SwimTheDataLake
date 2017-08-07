---
title: How to navigate the world of R packages
author: jvera
date: '2017-08-07'
slug: how-to-navigate-the-more-than-11k-r-packages
categories:
  - packages
tags:
  - help
---
One of the most powerful features of R is the vast package echosystem. But there's more than 11.000 packages just in CRAN, and a thousands more if you take GIT and Bioconductor into account, so the issue is to find the proper package for your needs. 
There’s a lot of sites to search for help if you need a hand when programming in R to choose a package. Here, a list of some of them.

[Rdrr.io](https://rdrr.io/): More than 3.000 online pre-loaded packages for our snippets to test. A complete search engine, and Jupyter Notebooks for our pleasure.

[Rdocumentation](https://www.rdocumentation.org/), one of my favourites. Serching CRAN, Bioconductor and GitHub for descriptions, words, functions or packages that can be very useful on our daily work. Available as R package for you to install on Studio, so you can search from within Rstudio Help tab. No need to open the browser.

[Rseek](https://www.rdocumentation.org/), by Shasha Goodman, based on Google engine, with some useful tabs for books, support forums, packages, docs…and even a “beginner” section. Very useful but sometimes slow.

[CRAN Task Views](https://cran.r-project.org/web/views/) is the official index for all CRAN packages, grouped by Topics (Tasks). They have an `[ndex by name](https://cran.r-project.org/web/packages/available_packages_by_name.html) very useful too. But not too useful if you don’t know the name of the package you’re searching for. Good when need guidance working on specific tasks.

You can get a glimpse of most popular and donwloaded packages with [CRAN downloads log](http://cran-logs.rstudio.com/) . Using *cranlogs* package you can have this info right into your code.

[MetaCran](https://www.r-pkg.org/), one of the most popular websites. Search by author, popularity, downloads, trending….seems to be based on download logs as they are authors of cranlogs package.

[Awesome R](https://awesome-r.com/), CRAN Task Views style, but nicer, linking to tools and packages by sections as an index: IDEs, sintax, data manipulation, graphics….

Dirk Eddelbuettel is the maintainer of [CRANberries](http://dirk.eddelbuettel.com/cranberries/), a well known site offering info on latest uploads to CRAN, updates, and removed packages. You can keep track of your favourite packages. There’s a twitter account available to keep you informed.

[R-exercises](http://www.r-exercises.com/) offering a bunch of tasks to improve your R skills, and a course seeker.

[R Function of the day](http://rfunction.com/) Not really daily updated but monthly. Very useful, writing about packages and tips too.

[CRANtastic!](http://crantastic.org/) not very good looking, but based on CRAN, another search site.

[R Site Search](http://finzi.psych.upenn.edu/search.html) taking package descriptions from CRAN and Bioconductor repos you can search for any term on them.

[CRANsearcher](https://cran.r-project.org/web/packages/CRANsearcher/index.html) RStudio addin capable of searching available CRAN packages directly within RStudio. Install it and search whole CRAN for help from a clean and useful interface in Rstudio.

[PackageMetrics](https://github.com/ropenscilabs/packagemetrics), a part of the 2017 rOpenSci Unconference, a useful package (a work in progress) to generate a comparison table with the main features from packages you prefer.

[Michael Popov App](https://bearloga.shinyapps.io/taskviewr/), a Shiny site to search CRAN repository. Created by Mikhail Popov (@bearloga on Twitter and GitHub) to quickly browse packages and their licenses using a snapshot of task views.

[Open Data CTV](https://github.com/ropensci/opendata), Jaime Ashander, Scott Chamberlain and Thomas Leeper maintain this GitHub site about using R to obtain, parse, manipulate, create, and share open data. 

And last, but not least, the [sos](https://cran.r-project.org/web/packages/sos/index.html) package. Implementing the *findFn()* function, so you can use it in your R code for searching not only on installed packages but in all available packages in CRAN and Bioconductor. No need to get out your favorite IDE.

Feel free to share your favourite help sites via twitter.