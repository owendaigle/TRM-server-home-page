---
layout: post
title: Website Jekyll Rewrite
post_date: 2025/02/13
update_date: 2025/02/13
topic: Programming
author: Owen Daigle

---

I have been working on this project for awhile off and on. 

In fact, it started a few years ago with me wanting to move to some better server backend (with real server side code support) such as flask or django, but that never took off (although there are a [couple branches of my old site](https://github.com/owendaigle/trmWebsite/tree/flask-rewrite-thingy-thingy-thing) for those). I just never really could see the benefit of all those fancy server side features. They would have been cool back when I wanted a better website for the NPA (No Parents Allowed) club me and my cousins were apart of, but unfortunately, I have gotten old and boring now, so I don't really want to do that anymore... :-(

About 6 months ago I thought of changing to a simpler static website framework that is more focused on the content so I can easily make content in markdown with some generative code in it, and then have something compile and turn into a simple static site. Jekyll fit the bill perfectly so I started working on it on and off (due to life and constantly getting distracted by other stuff).

Part of my goal was for it to integrate with the old html parts of my site, so I did not want to use any of the prebuilt convenience templates online, and I also wanted to learn and understand what is going on, so I mostly built it from scratch (with "stealing" some code from other people such as the minima theme). So I spent a long time finding how it worked, testing multiple things, looking at [other people's websites](ivanmeler.github.io) and such, and finally a couple days ago, I finished up the work and got started on deployment. 

# Deployment

With my past setup, I would make some changes to the website, upload to github, and then ssh into my server and `git pull` the new code where apache2 would serve it. This worked well, but could be optimized. It was much better than my very old system though (before I used git) where I had to physicaly connect a drive to the server, physically connect my display, kb, mouse and then copy over the files (this is what I actually did when I was younger and thought git was some huge complex scary software...).

So I basically made a short shell script that would run every 15 minutes through cron, and it would `git pull`, then build the site into a directory called `./_site` in the jekyll directory. Then apache2 would serve that website on port 91 (since 80 is already being used) and then this can be sent through my reverse proxy and bound to port 80 on my wan [odaigle.xyz](https://odaigle.xyz). This mostly worked, but I had a couple problems. 

1. The apache server would only serve the default `/var/www/html` directory.
2. The cron script would not run correctly (unable to find bundle and jekyll commands) when run through cron, but ran just fine manually.

The first problem was simple to fix, and it was just I forgot to put the config file in the `./sites-enabled` directory, I had put it in the `./sites-available` only...

The second one was a bit harder to diagnose, but after some testing, it became quite obvious the problem, and one I should have seen right away. The cronjob did not have the same PATH variable as the user I was running as, so I just simply provided the absolute paths to the executables.

# Conclusion??

Well this is nice since I hope to write quick summaries about some of the cool stuff I do (at least things I think are cool).

Now I have a place that I can actually put these summaries, and I do not have to worry about the format. In fact, I could even just type up a quick markdown file, save it somewhere, and then at a later date add it to the site!! Simple!!