---
title: Processing mail using R
author: jvera
date: '2017-07-23'
slug: processing-mail-using-r
categories:
  - tricks
tags:
  - email
---
After a long time seeking for R packages to connect to a remote mailbox (not Gmail), I’ve had to admit that there’s no such feature right now in R.
Tested a pair of Python scripts but too much convoluted to my needs. It’s an incredible issue that having more than 10 thousand packages available on CRAN, none of them was suitable for my needs.
Some readers suggested tm.plugin.mail added to tm package, but my core feature is to connect to a remote mailbox. So, not a valid help.
At the end, good old Bash saved my day.
It’s a really easy process (but be aware that maybe you’ll end not using R at all): connect to mail account using fetchmail and then use R to read local mailbox.
From that moment, to the end, it’s the usual text parsing with tm Corpora. Some hints:
```r
library(tm)
library(tm.plugin.mail)
mbox <- MBoxSource(“/var/spool/mail/user”, encoding = “UTF8”)
```
sometimes it’s very useful to keep a text backup for each mail message.
```r
convert_mbox_eml(mbox = “/var/spool/mail/user”, dir = “/home/user/my_mail_text”)
```
or getting Corpora alive right from mailbox
```r
mail_messages <- VCorpus(MBoxSource(“/var/spool/mail/user”, encoding = “UTF8”), readerControl = list(reader = readMail))
```
some cleaning
```r
mail_messages <- tm_map(mail_messages, removeCitation)
mail_messages <- tm_map(mail_messages, removeSignature)
```
take a peek at content
```r
mail_messages[[1]]$meta$author
mail_messages[[1]]$meta$heading
mail_messages[[1]]$meta$header
```
If you don't need to connect to a remote server this can be fine. Otherwise, you'll have to resort to other language.