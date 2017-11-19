---
title: My Docker images for R
author: jvera
date: '2017-11-19'
slug: my-docker-images-for-r
categories:
  - systems
tags:
  - Docker
---

This month I reached the dreaded "2 hours limit" at Docker Hub on building my Docker images. The images are built but the message shown is "error". You can still use it, but on the front desk, seems that I'm not doing a good job. Clearly, something to fix.

So entered a hard refactoring week trying to make my images available again with no error message. 
My first attempt was to split TidyViz into several images, one for GIS, one for stats and ML, the other for Rmarkdown and reporting...the issue is I ended with a nightmare of unmantainable images with many dependencies not satisfied and as a result, several unusable images.

So I step back, and tried the KISS approach (keep it simple). Lighter images, less packages, less dependencies, faster load times, and a companion website listing recommended packages just in case someone needs to go forward (working on it).

I offer three images:

- Tidyviz-base, just with wrangling and stats packages. Ready for working with Rstudio server. Based on Rocker.

- Tidyviz, the complete set of my most used packages, from *base* image adding Textmining and more.

- Tidyviz-Shiny. Just adding shiny to the game, just in case you need to serve shiny reports from the same container.


Here, my link to the brand new Docker images.

https://hub.docker.com/u/jvera/
