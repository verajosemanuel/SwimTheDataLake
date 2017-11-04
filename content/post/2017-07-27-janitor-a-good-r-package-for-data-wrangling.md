---
title: janitor, a good R package for Data Wrangling
author: jvera
date: '2017-07-27'
slug: janitor-a-good-r-package-for-data-wrangling
categories:
  - packages
tags:
  - data wrangling
---
We all know the many hours spent cleaning and wrangling data. Sometimes I think my actual job is not “Data Scientist” but “Data Cleaner”.
Data, as you surely know, is not often in the best shape, so for many people like me, one of the most appreciated tools is the one that makes cleaning easy.

When I started working on what now is called data science I used python a lot for data wrangling but R is the “de facto best tool” for cleaning and munging right now due to the many good packages developed for that purpose.
I’m going to mention today one of my favourites: janitor

Janitor, combined with magrittr pipes is one of the best in class for cleaning data. Just a glimpse on my most used janitor functions:
```r
clean_names()
```

handles problematic variable names, returning only lowercase letters with underscore as separator, and many other improvements to colnames.
```r
tabyl()
```

Improved “table” command. Automatically returns a dataframe with percentages (or valid percentages if NAs are present).
```r
crosstab()
```

There’s many crosstab functions already, but janitor improved it returning a data frame, calculating frequencies, and table wise percentages. Imagine PivotTable from Excel but working on dataframes.
```r
adorn_crosstab()
```
Hunts down and examine duplicated records. Returns the duped records and their count.

```r
get_dupes()
```

Importing from Excel this kind of numeric date values is an usual issue. This function converts to actual dates.
```r
excel_numeric_to_date()
```
When importing from Excel it’s not so unfrequent to import empyt cols or rows. Discard them with this easy command.
```r
remove_empty_cols()
remove_empty_rows()
```

check documentation for code examples and features https://github.com/sfirke/janitor