---
title: 'Atom for R: keeping settings in sync'
author: jvera
date: '2017-11-20'
slug: atom-for-r-keeping-settings-in-sync
categories:
  - systems
  - tricks
tags:
  - Atom
  - Editor
---

![Atom Editor](/images/atomlogo.jpeg)

Last week I was working on some projects involving Posix and R code. I tend to use Atom Editor for such code instead of Rstudio, and sometimes I think the one an only valid contender against Rstudio is Atom Editor. With Hydrogen, Linter, and R language Syntax/autocomplete addins is a full featured editor. Plus, dark mode rocks!

One of the most useful features Atom has and Rstudio hasn't is setting syncs via Github. You can keep all your settings and installed packages in sync between different machines just using **Sync-Settings** package.

Here the steps:

1- Install sync-settings package

2- Create a GitHub access token for Atom: **Settings > Developer settings > Personal Access Tokens**. Be sure to check the CREATE GIST permission on.

3- Copy access token so Sync-settings config dialog

4- Go to GitHub and create a new GIST. Only the name is needed, so be sure is named **packages.json**. Description can be empty. Put some words into the file to save (it will be overwritten on first backup). You can keep settings public or private. Choose the kind of gist you prefer on saving.

5- Copy the gist ID to sync-setting config dialog (the last part of the gist url after username)

6- Open Atom commmand palette (Ctrl + Shift + P) and choose

```

sync-settings:backup

```

Et voilà, all your settings are there for any other Atom installation you have. Just install *Sync-Settings* package and choose 

```

syncing-settings:restore

```

Cheers,
    
