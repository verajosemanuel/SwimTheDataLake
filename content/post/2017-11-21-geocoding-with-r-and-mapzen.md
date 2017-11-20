---
title: Geocoding with R and mapZen
author: jvera
date: '2017-11-21'
slug: geocoding-with-r-and-mapzen
categories:
  - packages
tags:
  - geo
---
The most widely used service for Geocoding is Google Maps, but you'd hit the limits early in your project if you don't have a paid account. I often place data on a map, so I need precise geocoding.
It's not unlikely you had to test some other geocodig options 'til you get the budget for a Google Maps Professional account. I've been in that situation myself a couple of times.

Here, I'm going to describe my approach using the free **MapZen.** geocoding service.  We'll use *rmapzen* package but first of all you'll need to get a unique mapzen key for you project (https://mapzen.com/documentation/overview/api-keys/)

```r
library(mapzen)
library(rio)
library(magrittr)

# import data to geocode

df <- rio::import("locations.xlsx") 


# pasted country for better results if it's not in data

df$complete_address<- paste0(df$address,", France")

mapzen_df <- data.frame()


# sometimes you have a lot of repeated adresses
# so, let's geocode just unique adresses

unique_adresses <- unique(df$complete_adress)

i <- 0

for (address in unique_adresses) {
  
  tryCatch({
    mapzen_df <- rbind(mapzen_df, mz_geocode(address, api_key = "insert_your_mapzen_key_here" ))
    
    i=i+1
    message <- paste0(i,": ", address)
    print(message)
    
  }, error=function(e){cat("ERROR :",conditionMessage(e), "\n")})
   
  
}

# join the original df with the geocoded one

final_df <-  inner_join(df, mapzen_df)

```