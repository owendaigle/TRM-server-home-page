---
layout: post
title: Networking issues on Linux
post_date: 2025/07/12
update_date: 2025/07/12
topic: Networking
author: Owen Daigle
description: Not being able to ping other devices on the same network but being able to ping the wan??? Finally found a solution. 

---

# Background
I have a network where I am living currently (obviously). This one has 3 vlans. `10.0.1.0/24` is my admin network with no ineternet access. `10.0.2.0/24` is not used for anything. `10.0.3.0/24` is my main that I have all my devices on (I know this defeats the purpose of having multiple vlans, but whatever). I also have a wifi network for each of these vlans. 

Now I have been having no problems with these vlans on most of my devices. The one exception was my main desktop which could connect to the internet, and had no issues there, but when communicating with other devices on the local network it would fail to do so. 

# Troubleshooting
So this is a weird problem. I tried pinging from other devices (2) to this desktop (1), and they also failed to get through. 

I then tested the ethernet cable (connected to the same switch) with another device (2) and it had no problems if I took another computer (3) and tried to ping (2), or took (2) and tried to ping (3). But when I replaced (2) with (1), and connected (2) and (3) to either wifi or ethernet on `10.0.3.0/24`, (2) could reach (3) and vice versa, but neither could (2) or (3) reach (1) or vice versa. 

So I knew that the network infrastructure was fine, it was something wrong with the computer (1). I tried recreating the interface (removing it and generating it again) and still problems. I also manually configured it on (1) and replicated this same manual configuration on (2), (obviously not at the smae time) and it worked on (2), but not (3). I also tried (1) on wifi, ethernet1 `eno1` or ethernet 2 over usb c, neither had any better results. 

I thought is must then be something more in depth. There was no firewall or AV that could potentially cause problems (i know, I am dangerous), so it must be something conflicting with it. 

After a lot of looking into it, and looking at different places, I checked the routing table by doing `ip route show` and it gave me some interesting results. I saw that there were multiple routes configured for `10.0.3.0/24`. One of them was the one I wanted, but somehow there was an lxc bridge created using that same ip range. I know I had been playing around with LXCs sometime in the past, and I guess I had set up a bridge using `10.0.3.0/24` which somehow ended up being the same ip that I use for my network now!! Weird how the world works... 🤣🤣🤣🤣🤣 🤪

```bash
default via 10.0.3.1 dev eno1 proto dhcp src 10.0.3.103 metric 100 
10.0.3.0/24 dev lxcbr0 proto kernel scope link src 10.0.3.1 linkdown 
10.0.3.0/24 dev eno1 proto kernel scope link src 10.0.3.103 metric 100 
172.17.0.0/16 dev docker0 proto kernel scope link src 172.17.0.1 linkdown 
172.18.0.0/16 dev br-37bb0b91ccaa proto kernel scope link src 172.18.0.1 
172.19.0.0/16 dev br-2453e8a17ad8 proto kernel scope link src 172.19.0.1 linkdown 
172.20.0.0/16 dev br-41d77aec266c proto kernel scope link src 172.20.0.1 
```

At least now it seems to be working fine. So another problem solved and something new learned!! 🤓