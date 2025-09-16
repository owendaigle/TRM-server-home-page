---
layout: post
title: Buck converter for computer fan
post_date: 2025/09/16
update_date: 2025/09/16
topic: Electronics
author: Owen Daigle
description: I was too hot, so I hooked up a 12VDC computer fan to a buck converter to get the right speed.  

---



The other day I was too hot, and I did not have a fan to cool off. So I took a computer fan and hooked it up to a DC power supply. I did not want it running at full speed though since that is loud. 

I originally had it connected to my variable dc power supply to get whatever voltage I wanted, but it is kind of annoying. I have a bunch of fixed voltage DC power supplies at like 15V, 12V, 9V, 7.4V, 6V, 5V, etc, but I don't want to keep switching them out, and also it is still limiting me with discrete values of voltage. 

So I connected a 15VDC power supply to a buck converter, and then connected the buck converter to the fan. Now it works well and I can relatively easily change the voltage using a screwdriver. 

# Next Steps

Now I kind of want to take this to the extreme and design a circuit that converts 120VAC to 1-12VDC controlled through a potentiometer. I just need to actually decide to do this, it has been too busy the past few weeks...