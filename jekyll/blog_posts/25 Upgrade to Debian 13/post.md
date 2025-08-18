---
layout: post
title: Upgrading to Debian 13
post_date: 2025/08/18
update_date: 2025/08/18
topic: Software
author: Owen Daigle
description: Upgrading my desktop to Debian 13 from Debian 12. It was very easy 

---

This is something I have been dreading for awhile, simply because I did not know how it would go and for how long my main desktop would be out of service. I know I could wait a long time before upgrading, but I was curious as well. 

I followed the documentation [here](https://www.debian.org/releases/trixie/release-notes/upgrading.en.html) and it went very well. The only issue I ran into was it did not like my docker package that was installed, it refused to upgrade this package. In the middle of the upgrade this caused the upgrade to just stop until I fixed this. I just ran some command (i cant remember the exact syntax) to force dpkg to override the package and update docker. Then I resumed the update and it went fine!!

I have not tested out everything yet, but from what I can tell it was a success. I had no major problems with the update at all. I did not even have a stock system. I have a lot of packages installed, some of which from the debian repository, but many of them are either from debian-backports or other sources. For example, I used a backported kernel and NVIDIA driver since my CPU was not supported by the 6.1 kernel of Debian 12. The upgrade process took care of this with no problems. 

I really thought I would regret starting the update from 12 to 13 since it would take a lot of effort to get my workstation back up and running, but it really surprised me. 

Great job Debian team!!