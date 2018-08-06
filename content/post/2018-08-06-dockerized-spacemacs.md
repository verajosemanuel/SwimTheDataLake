---
title: Dockerized Spacemacs on Windows
author: jvera
date: '2018-07-22'
slug: dockerized-spacemacs
categories:
  - tricks
tags:
  - emacs
---

I was talking the other day of setting Spacemacs on Windows with no privileges. Sometimes it's not even possible to do so, but you have Cygwin/mintty/babun + Docker engine on your machine for testing purposes. So here is the way of having a spacemacs running on Docker in no time.

![dockerized spacemacs](/images/dockerized_spacemacs.jpg)

Main steps are:

1- install xinit and xorg on your *nix-terminal

2- set display and run dockerized spacemacs

First step is easy, just install xinit and xorg. This commands here are for babun, but I'll assume you know how to install on your preferred POSIX layer.

```r
$ pact install xinit xorg
```

Then activate display and start x server:

```r
$ export DISPLAY=<your-machine-ip>:0.0

$ startxwin -- -listen tcp & xhost + <your-machine-ip>
```

Be careful not to close this terminal windows and just issue a docker command to get (pull) the spacemacs official image.

Assuming this is the first run:

```r
docker run --name my_desired_name -e DISPLAY="$DISPLAY" -v <my woring dir>:/mnt/workspace spacemacs/emacs25:develop
```

And voilá, docker will start to pull all layers and build the container for you. At the end you'll have a completely functional spacemacs dockerized window. 
Work with it, test it, config to your likings and remember to commit all changes (see Docker help).

subsequent uses of container must be done using `start` command:

```r
docker start my_desired_name
```

Bon appetit!