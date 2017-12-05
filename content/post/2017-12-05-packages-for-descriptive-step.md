---
title: Great packages for understanding your data
author: jvera
date: '2017-12-05'
categories:
  - packages
tags:
  - data wrangling
  - visualization
slug: packages-for-descriptive-step
---

On the first steps of any project, the most usual task is to take a glimpse, figure how our data is distributed, and as fast as possible, be ready for next steps (wrangling and imputation).

In the old days, I've built my own functions to accomplish this task, until some other people did this very same work distributing packages with this target in mind. Many of them are awesome packages (really awesome), allowing you to plot missing values and data distribution, among other tasks, that makes very easy to figure which kind of data are you working with. All of them are worth trying and powerful additions to your R toolset. 

Here my list (descriptions are not my own but from different web sources related to the packages, mainly their github pages):


- **dataMaid**

https://github.com/ekstroem/dataMaid

dataMaid is an R package for documenting and creating reports on data cleanliness.
Data cleaning is an important first step of any statistical analysis. dataMaid provides an extendable suite of test for common potential errors in a dataset. It produces a document with a thorough summary of the checks and the results that a human can use to identify possible errors.


- **desctable**

https://github.com/maximewack/desctable

Easily create descriptive and comparative tables. It makes use and integrates directly with the tidyverse family of packages, and pipes. Tables are produced as data frames/lists of data frames for easy manipulation after creation, and ready to be saved as csv, or piped to DT::datatable() or pander::pander() to integrate into reports.


- **DescTools**

https://cran.r-project.org/web/packages/DescTools/index.html

A collection of miscellaneous basic statistic functions and convenience wrappers for efficiently describing data. The author's intention was to create a toolbox, which facilitates the (notoriously time consuming) first descriptive tasks in data analysis, consisting of calculating descriptive statistics, drawing graphical summaries and reporting the results. The package contains furthermore functions to produce documents using MS Word (or PowerPoint) and functions to import data from Excel. Many of the included functions can be found scattered in other packages and other sources written partly by Titans of R.


- **janitor** 

https://cran.r-project.org/web/packages/janitor/vignettes/introduction.html

The main janitor functions can: perfectly format data.frame column names; provide quick one- and two-variable tabulations (i.e., frequency tables and crosstabs); and isolate duplicate records. Other janitor functions nicely format the tabulation results. These tabulate-and-report functions approximate popular features of SPSS and Microsoft Excel. This package follows the principles of the "tidyverse" and works well with the pipe function %>%. janitor was built with beginning-to-intermediate R users in mind and is optimized for user-friendliness. Advanced R users can already do everything covered here, but with janitor they can do it faster and save their thinking for the fun stuff.


- **naniar**

https://cran.r-project.org/web/packages/janitor/vignettes/introduction.html

Missing values are ubiquitous in data and need to be explored and handled in the initial stages of analysis. 'naniar' provides data structures  and functions that facilitate the plotting of missing values and examination  of imputations. This allows missing data dependencies to be explored with  minimal deviation from the common work patterns of 'ggplot2' and tidy data. 


- **summarytools**

https://github.com/dcomtois/summarytools

Built around three key functions: 1) freq() generates frequency tables reporting counts and proportions (including cumulative) for factors and other discrete data; 2) descr() gives all common central tendency statistics and  measures of dispersion for numerical data; 3) dfSummary() gives as much information as possible on a dataframe's columns in a legible table. freq() and descr() support weights, and all three functions support 'Hmisc' or 'pander' labels.  A variety of output formats are available (plain text, 'rmarkdown' and HTML). An additional misc function, what.is(), displays all common properties of an object (its class, type, mode, attributes, etc.) and extends the base is() function,  checking the object against most is.() functions.


- **tabplot**

https://github.com/mtennekes/tabplot

A tableplot is a visualisation of a (large) dataset with a dozen of variables, both numeric and categorical. Each column represents a variable and each row bin is an aggregate of a certain number of records. Numeric variables are visualized as bar charts, and categorical variables as stacked bar charts. Missing values are taken into account. Also supports large 'ffdf' datasets from the 'ff' package.


- **visdat**

https://github.com/ropensci/visdat

Create preliminary exploratory data visualisations of an entire dataset to identify problems or unexpected features using 'ggplot2'. Initially inspired by csv-fingerprint, vis_dat helps you visualise a dataframe and "get a look at the data" by displaying the variable classes in a dataframe as a plot with vis_dat, and getting a brief look into missing data patterns using vis_miss.



- **xray**

https://blog.datascienceheroes.com/x-ray-vision-on-your-datasets/

The R Package to have X Ray vision on your datasets. This package lets you analyze the variables of a dataset, to evaluate how is the shape of your data. Consider this the first step when you have your data for modeling, you can use this package to analyze all variables and check if there is anything weird worth transforming or even avoiding the variable altogether.




Last two mentions, some working on terminal only but promising.



- **skimr**

https://github.com/ropenscilabs/skimr

The goal of skimr is to provide a frictionless approach to dealing with summary statistics iteratively and interactively as part of a pipeline, and that conforms to the principle of least surprise.
skimr provides summary statistics that you can skim quickly to understand and your data and see what may be missing. It handles different data types (numerics, factors, etc), and returns a skimr object that can be piped or displayed nicely for the human reader.

- **precis**

Hadley Wickam is working on a package for better summarising of data frames called **precis**. This package is designed to replace base::summary() but it's on early development stages.

https://github.com/hadley/precis

