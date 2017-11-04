---
title: 'file.choose: empowering useRs'
author: jvera
date: '2017-07-20'
slug: file-choose-empowering-users
categories:
  - tricks
tags:
  - base R
  - file management
---

Sometimes when sharing your analysis, via Rmarkdown or the brand new NoteBook, the data file is located at the user’s computer, making unusable the default path from your own pc.
But it’s easy to allow users to choose the data file to be imported and perform code execution using this file.
it’s an easy command:
```r
myFile <- file.choose()
```
a dialog will be opened for the user to browse file system and choose the file.
If you need to load a folder to process all the files within, don’t worry:
```r
myFolder <- choose.dir()
```
As you can imagine, sometimes it’s a tough decision to leave to user’s consideration the proper files. That’s the hard part.

The code, it’s the easy part.