---
title: My favourite snippets
author: jvera
date: '2018-05-29'
slug: my-favourite-snippets
categories:
  - tricks
tags:
  - Rstudio
---

A hidden gem from Rstudio is snippets feature. A well known option in any other editor (Atom, VS Code, Notepad ++....) seems that for R people is not a very used tool. For what I know some developers tend to code a full Add-in for things that can be achieved easily just adding a snippet to your Rstudio configuration.

Doing this is easy. The graphical way is getting to Rstudio Tools > Global Options > Code > Enable Code Snippets (Edit Snippets)

![snippets](/images/snippets.png)

You can see is a very simple syntax. Placeholder for cursor and strings that must be inserted preceded by dollar sign and curly braces. (here a succint description https://support.rstudio.com/hc/en-us/articles/204463668-Code-Snippets )

The file way is getting to folder where snippets are saved. I'm sure it depends on every system but usually is:

```r
~/.R/snippets/r.snippets
```

editing the file content to add yours is an easy task. My favourite are:


A slightly modified for inserting a title before timestamp:

```r
snippet ts
	"#" ${0} `r paste(date(), "------------------------------\n")`
```

The second one to insert the magrittr pipe I use most (instead the default one)

```r
snippet mp
	${1:object} %<>% ${0}
```
And a third, for a similar case, but using different names for e very object:

```r
snippet p
     ${1:object} <- ${2:dataset} %>% ${0}
```
