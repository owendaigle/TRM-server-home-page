---
layout: post
title: Self Hosting SeaFile
post_date: 2025/08/07
update_date: 2025/08/07
topic: Software
author: Owen Daigle
description: Finally getting fed up with pCloud and switching to self hosted SeaFile. It was quite easy using docker. 

---

![my seafile logo](mylogo.png)

## Background

I have gone through a few storage solutions over the past few years. Originally I used google drive, which worked fine except for obviously *I do not like not being in control of my files*, and also most importantly it did **not have a Linux client**. While there were some unofficial ones, none of them seemed to work right for me. Some of them would just sync the entire directory to my system which used too much storage, some would keep everything online which I am fine with but then some programs on my computer would not be able to open these files without me manually copying them off of the drive and onto a fully local folder on my machine (this should work since it is supposed to download the file temporarily when accessed, but not all programs seemed to work with that). 

I then tried a few others like mega, dropbox, and pcloud. Dropbox did not work too well with Linux, and was *expensive*, and mega was blocked by both my school and work. pCloud was decent, it worked, it had an ok linux client, and it was not too expensive. So I **went for it**. I still did not like that I did not have control over my data, so I had to be careful what I uploaded. For example, while I can take a backup of one of my windows install disks, I cannot upload that to pCloud since their TOS does not allow it even though it is a backup copy I made and do not intend to distribute. But whatever. 

pCloud also had some other issues such as it would often randomly complain I was using all my storage (I was not even at 25%) and *refuse to let me upload anything without restarting my computer*. This happened almost **daily** on both my windows tablet, and Windows VM. I contacted pCloud support, and they were not helpful. There were some other problems like sometime it would not upload files, and sometimes I would try to access a file and it would not work until I manually copied it into a local directory (this was rare, but it happened and I did not notice a pattern). 

## Seafile

I had been wanting to set up some self hosted service for awhile, but I did not want to do nextcloud since it is too complex. I recently found out about seafile, and decided to give it a try. I set up my config to *bind mount the db and config files on my local ssd in a vm*, and the data storage was running on an nfs share on my nas. It worked out of the box. I tested out some more stuff and it kept workig with no problems. I have been using it for a few weeks with only minor problems such as once it took a couple minutes to sync a file, but it mostly works well. 

It was **really easy** to set up, I simply used the given *docker compose file*, created the directories for the files, connected it to my reverse proxy and domain, and I was good! I had some problem at the start with SSL, which was a known problem with django. This was where my domain was not added as a trusted domain in the config files. It was a simple change and then it was fixed. 

Now this was quite easy for me because I have been getting a lot better using docker and I also have the **infrastructure** in place to not have to worry about the hardware anymore. I have the storage with redundancy built in, I have the computer power, and since the database is being stored on the system ssd (which is a VM running on a compute server) it gets **backed up daily** onto the backup server so if anything does happen, I am fine. 

This is not to say my system is perfect, I still have more work to do. Firstly the actual data is not being backed up. It stored in a raid array with redundancy, so if a drive dies it is fine, but if I mess up and *accidentally delete the directory* I am out of luck. I have kind of compensated for that by putting it in a directory that can only be read by one specific NFS share which is only accessible by that computer, but still it is not a real solution. Secondly I do not have any sort of **UPS** system for the computers so if there is a power outage I could lose some data. This is just due to a lack of funds. Thirdly there is no high availability built in. I could easily go for HA at a system level using proxmox, but for that the actual system images would need to be hosted on a network drive, which is not ideal when I only have a single gigabit interface on each device, so I do not use this. I could also do this at an application level using kubernetes, which I hope to do someday, but not now, that is a project for later. 