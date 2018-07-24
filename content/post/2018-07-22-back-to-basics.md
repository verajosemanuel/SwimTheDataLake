---
title: Back to Basics (Emacs + ESS + zsh + byobu)
author: jvera
date: '2018-07-22'
slug: back-to-basics
categories:
  - tricks
tags:
  - Rstudio
---

I think i'm a little bit "old school" or maybe sometimes you have to use the right tool for the task. Some time ago, i discovered I feel more productive staying away from the mouse, so terminals and text editors are my daily working environment from then.

If you use linux, i'm preaching to the choir, and nearly the same if your work involved Mac OS. Sadly, sometimes you have to work using Windows. Yes, sometimes any other option than windows is "forbidden". Only God knows why.

You'll be lucky if they let you activate developer mode (on windows 10) and use the Bash shell Canonical delivered inside the latest windows version, but this could be not your case. So, i'm giving you some hints to setup some near to linux environment using Emacs, ESS, Zsh and byobu (tmux wrapper).

Main steps are:

1- Emacs + Spacemacs (ESS + magit + org mode)

2- Terminal + Zsh + Byobu

Fastest way to get a proper emacs + ESS (emacs speaks statistics) working in no time is using the vigou3 installer, ready to usen in windows (and Mac):

https://vigou3.github.io/emacs-modified-windows/


But as we said, we can not install anything on the machine due to "politics". So let's download latest stable emacs and decompress on our preferred folder. 

http://ftp.rediris.es/mirror/GNU/emacs/

`runemacs.exe` is the executable. Then, clone spacemacs:

```r
$ git clone https://github.com/syl20bnr/spacemacs ~/.emacs.d
```
just activate your favourite layers (magit, ess, org, csv…) and you're done.

Now the trickier part: getting a proper terminal on windows. Powershell is a joke, so let's install zsh.
We're going to use **babun**, built on top of Cygwin, adding a lot of refinements and zsh as default shell.

http://babun.github.io/

Easy to install, but emacs is not running out-of-the-box. You must update the underlying Cygwin. Don't worry, it's an easy task: just execute the *update.bat* file from installed babun folder.

And last, let's install **byobu**, a wrapper for **tmux**, a terminal multiplexer. Babun offers a package manager *"a-la apt-get"* but byobu is not provided this way, so you must install *tmux* and *make* previously.

```r
$ pact install tmux

$ pact install make
```

Download most recent byobu version and uncompress. 

https://launchpad.net/byobu/+download

Configure installation directory, and then *make & install*

```r
$ ./configure --prefix="$HOME/installs/byobu"

$ make

$ make install
```

Add executable PATH to environment:

```r
$ export PATH="$HOME/installs/byobu/bin:$PATH"
```

In Spain we say: "Poor man's happiness is never long lasting one" (poco dura la felicidad en la casa del pobre) and this is the case. Byobu features are not working 100% but this setup can fill your needs almost completely.
