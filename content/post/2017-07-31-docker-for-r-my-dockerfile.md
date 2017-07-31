---
title: Docker for R, first steps
author: jvera
date: '2017-07-31'
slug: docker-for-r-my-dockerfile
categories:
  - systems
tags:
  - Docker
---

Sometimes, you need to replace your hard disk, upgrade your o.s. or recently bought a new laptop. When this time comes, it’s a real pain to get your Rstudio up and running with all you favourite packages and settings.

Solomon Hykes, gave birth to Docker thinking on apps unattached to a machine, readily available, working the same no matter how you interface with them.

i’m not going to explain what Docker is ’cause there’s a lot of information to read on the internet. Just my two cents on working with a containerized Rsudio.

I use rocker/tidyverse version from Dirk Eddelbuettel, installing all my favourite packages (not much needed since this image is provided with complete tidyverse).

https://hub.docker.com/r/rocker/hadleyverse/

Just a command to install Docker on linux:

```
curl -fsSL https://get.docker.com/ | sh
```

Pull the image from repo and start a container:

```
docker run -d -p 8787:8787 rocker/hadleyverse
```

Connect to port 8787 with your browser (rstudio as user and password) to check if your Rserver is up and running.

When container is generated you can start it with:

```
docker start mycontainer --interactive /bin/bash
```

“mycontainer” is a name I’ve given using the name modifier when starting the docker container from the image.

/bin/bash at the end makes a terminal available to connect to it. You can see it’s a simple plain linux machine.

List your containers:

```
docker ps -a
```

Sharing data with host:

```
docker start mycontainer --interactive -v ~/dockerdata:/data /bin/bash
```

dockerdata folder is located at home folder in my host o.s. and data folder belongs to container. Any file you place there, will be available for the container to use, and vice versa. Maybe you need a Shiny Server, so run a Dockerized Shiny and share the same folder so you can develop your viz in Rstudio and serve with Shiny.

https://hub.docker.com/r/rocker/shiny/

list all your attached volumes command:

```
docker volume ls -q
```

delete all volumes command:

```
docker volume rm $(docker volume ls -q)  
```

How to delete a container:

```
docker rm mycontainer
```

Dockerfiles are text files recipe-like where you can define what is your favourite app configuration, this way your development environment can be packaged up and moved to all sorts of different systems.

My only concern is deploying Docker on production systems. I’m not really into it. I think the best Docker can do for you is to avoid the hassle of building and setting your favourite tools for development.