---
title: 'using inotify for long running R scripts '
author: jvera
date: '2018-05-09'
slug: using-inotify-for-long-running-r-scripts
categories:
  - tricks
tags:
  - file management
  - base R
---

Sometimes your Rscript takes a long time to run. Not for computation requirements but for the kind of processes involved, for instance when calling APIs with time limits and such (I'd use big data architectures otherwise).

Last week I was working on one of such projects, and one of the requirements was: the user must provide an excel file via web interface to Rserver, and then computation begins. At the end, the results file is emailed to user. The kind of third party services I must use are of the very strict & picky kind, so no one can use the app (or any other process) to call the very same third party services meanwhile. I'm not very fond of Shiny so I decided to go the *FlexDashboards* path. Simpler and cleaner, just 10 lines to render a webpage to upload a file.

Now, things are getting interesting.

I have to assume the user is not going to have the browser opened for hours, sometimes over a working day or more, depending on the uploaded file amount of rows, so the secondary process firing API calls MUST be isolated from the Flexdashboard process.  I read some vignettes from packages like *future* or *later*, but didn't seem to fill my needs, so I decided to rely on posix commands.

My first approach was to launch a secondary process using a system call from Flexdashboard R.

```r

 system("nohup Rscript api_calls.R 2>&1 &")

```
But...how to block any other user from using the same page. Or any other similar process by the way. The answer that came to mind first: lockfile. A very easy POSIX command. So the POSIX way got the top position.

```r
  system("lockfile -r 0 /home/user/my_analysis/web.lock")

```

Discarded CRON. Not very eager to check upload folder every few minutes. Not a pretty strategy.

So inotify came the obvious way to solve it. In case you don't know, inotify is a kernel submodule you can monitor in real time any file event with. Monitoring events like IN_ACCESS, IN_CREATE, IN_DELETE......using a CRON-like interface. You choose what to do and more important, WHEN to do it. Two events are key: uploaded file, and end of API calls.
One more twist. Running Flexdashboard process belongs to "shiny" user, while API calls are running under R user. Other users/apps can use API calls so they must be blocked too. Unix/Linux permissions are built so any given user cannot write/delete any other user's folder.

So Let's see how to monitor both mentioned events and circumvent permission issues.

To write lockfiles for every user when a new Excel file is uploaded.

```bash
> sudo incrontab -e

/home/shiny/uploaded_files/ IN_CREATED /scripts/generate_lockfiles.sh

```

Easy to check if any lockfile is present at the beginning of the Flexdashboard page and block any other upload. Be nice to users and show a message explaining why they can't upload a file.
When the Rscript is started one of the first lines must write a lockfile and delete it at the end when the results file is emailed to user so inotify could unblock the website as follows:

```bash
/home/R/process_status/ IN_DELETED /scripts/delete_lockfiles.sh

```
As Flexdashboard process is checking if lockfile is present, when deleted any user is able to upload a new file and start all over again.
I've omitted the detailed scripts as you surely can get the idea. Hope this helps someone.

