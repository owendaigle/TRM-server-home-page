---
layout: post
title: Updating the Minecraft Server
post_date: 2025/04/16
update_date: 2025/04/16
topic: Servers
author: Owen Daigle
description: Updating the Minecraft server to 1.21

---

I decided to upgrade the MC server since it was way past time to do this.

Technically the MC server could be joined from almost any version due to a proxy I set up that lets people connect on almost any version using viaversion and viabackwards. This worked really well except for that my main world did not actually have any of the newer features from past 1.17. 

Actually upgrading the server was quite easy, I had to install a newer java version which I did, while java 21 was not in the debian repos, I just added a custom source and then installed from there. This gave problems since some of my other minecraft worlds are still on older minecraft versions, and I do not want to upgrade them just yet, so I just kept both java installations and just used the absolute paths to each binary since I don't feel like building a whole other container for the other server. I just had to modify my startup services to change the path. 

Upgrading the plugins was fine as well for most of them, except 1 plugin that was not updated for 1.21. That one did not work, so I guess I just have to deal with it. 

The only real problem I ran into was that the new 1.21 runs so slow on my machine, and I need to regenerate all the chunks to fill in the space below y=0. I kind of fixed this by installing a prerendering plugin `chunky` to prerender a large chunk of the world, but when people inevitably venture into new terrain, it will just be slow. There is nothing I can really do about that when running a ryzen 3 2200g. 

Now part of the reason it ran so well is since I have been streamlining how I do these updates for a long time, and lots of my server architecture is very good. I took a system wide backup before I did this using proxmox backup server which allows me to either restore the entire VM if I want, or to download copies of the individual files and then restore that myself. For the actual server, I have all the minecraft worlds setup as systemd services, so I can just shut them all down with `systemd stop mc*` and start them similarly. They will all gracefully shut down, and then let me do the upgrades. 