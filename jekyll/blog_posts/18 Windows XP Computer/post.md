---
layout: post
title: Windows XP Computer
post_date: 2025/05/25
update_date: 2025/05/25
topic: Random
author: Owen Daigle
description: Getting Windows XP installed on an old computer. 

---

I have wanted to get a windows XP computer for awhile, idk why but I thought it would be cool.

I recently decided to put one together with the following specs:

| - | - |
| CPU | Core 2 Duo E6600 |
| GPU | NVIDIA 9800GTX |
| RAM | 2GB Corsair XMS2 DDR2 |
| PSU | BFG 500W PSU |
| Storage | 240GB SSD |
| MOBO | Asus P5B Deluxe |
| Case | Some rando that looks decently old |
| Monitor | 19in 1440*900 acer monitor | 
| KB | Old HP PS/2 random |
| MOUSE | Old HP PS/2 random |

## Initial Setup
Initially, I put the whole thing together, and it would not boot. After some troubleshooting I found out that some of my RAM was not working right. I initially had 2x2gb RAM, but I switched to 2x1gb RAM. While I tried 4x1GB, for some reason it would only recognize 3GB regardless of what slots I used, and somehow all 4 sticks worked when tested individually. So I am not sure what is going on (bios even only recognizes 3gb, so I do not think it is an issue with 32 bit os only being able to point to 3gb ram)

After this, it seemed to boot fine, but it would not boot my windows XP boot USB running VENTOY. I know sometimes VENTOY does not work, so I burned an install disk. That worked fine. Once it was installed, I installed drivers for the chipset, GPU, USB, etc. I also installed DX9, .NET, and a few other windows tools. Then I installed some useful software like MS office 2003, Daemon Tools for a virtual CD ROM, and some other programs. 

## Video Games
Moving onto video games, I installed a few such as KOTOR 1, KOTOR 2, Unreal tournament, TESIV Oblivion, TESV Skyrim. 

Oblivion flat out would not work with Daemon tools. I think this was an issue with the DRM. While I could try to find a nocd crack online, I did not want to. So I just burned an oblivion disk. This worked perfectly. 

My skyrim version refused to launch the launcher. It kept giving me an error about a missing ini file. I did not really want to troubleshoot, so I just manually launched the game executable `TESV.exe` which worked fine. I just had to modify the settings such as game resolution in the config ini file manually, which was quite simple. 

Unreal Tournament also worked perfectly, no problems. 

KOTOR 1 gave me lots of problems, and I still cannot get it working. I run the game executable, and it just shows up the start menu. I click on play and it shows a loading screen for a few seconds, but then that disappears, and then nothing. The process ends on windows. So I am not really sure how to troubleshoot this. There are no logs, I tried using Damon tools for the disk image, and using my real disk. I tried compatability mode for win 98, and even win xp. Nothing worked. For now I have given up with this. 

KOTOR 2 also gave me problems. I have not spent much time with this, but I think it is a problem with Daemon tools. It tells me that I need to insert the play disk even when I have mounted using daemon tools. I think I will need to burn an actual install disk rather than use my ISO.

> NOTE: I have the real install disks somewhere for all these games, I just use the ISO images since I have those stored on my NAS from when I took backups of all the disks. I am burning copies since I cannot remember where I put those install disks. But I actually legally own these games, I am not just stealing them. 

## Future
Well in the future, I need to find some speakers for this computer. Currently it has no sound since I somehow have no speakers lying around here. Back where I usually live, I have a box of them, but I am away from home for work. I do not have extra speakers with me. 

Also, I want to get KOTOR 1 and KOTOR 2 working, as well as the original baldurs gate. I have the CDs for that game as well (or I have the ISOs, I have no idea where the physical disks are)

Then I might try to create a LAN with it, and a couple other computers. I do not want to connect to the internet, but I could make a simple LAN or VLAN with a few other computers just to easily transfer files. I am not sure what protocols I can get working on WIN XP, but I think probably SMB should work.