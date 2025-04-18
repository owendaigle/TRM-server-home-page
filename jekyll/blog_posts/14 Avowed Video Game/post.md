---
layout: post
title: Getting Avowed to run on old hardware
post_date: 2025/04/18
update_date: 2025/04/18
topic: Video Games
author: Owen Daigle
description: Getting the 2025 video game Avowed running on my computer. I guess underclocking sometimes helps????

---

![avowed-background](./Splash.jpg)

The video game Avowed was released in early 2025, and I wanted to *play* the game. Usually for me, *play* is usually defined as getting the game up and running, seeing if there are any hurdles I need to jump through, optimizing the game so it works fine on my hardware, completing the tutorial and then finally playing  for a few hours, and then never touching the game again as I get bored of it. LOL!!

For this game I thought it might be a challenge getting it to run well on my computer since my computer did not even come close to meeting the minimum requirements. It requires minimum a GTX 1070, and recommends a RTX 3080, and I have a cheap GTX 1650... It was a lot more work than I thought getting it to work. 

# Problems encountered

Firstly, it *refused to even run out of the box*. I was running it using the default proton GE version I usually use, so I decided to update that to the newest and still it did not work. Then I tried my system wine and for some reason it worked!! Now I know proton is better for games with more optimizations so I found a different build of proton and that worked. Same version, just built by a different person. I don't know what was up with my regular proton version, maybe something got corrupt, but it does not matter. 

After this, technically it *ran*, but at like 2 fps. After setting all the settings to minimum, still only like 10fps. Tried closing all other programs on my computer and restarting the WM and still it was unplayable. Reduced the resolution as well to 720p (the lowest) and it still did not work well at all. I then relaunched the game using mangohud to monitor system performance, and my GPU was sitting at 100% usage, but only using about 30W. This is a GTX 1650 with a dedicated power connector, so it is definitely getting more power than that (in theory up to 225w from the PSU, although practically the power limit is 85W on the board). Also the VRAM was completely maxed out. I figured that might be the issue so I closed everything running on my computer, and was able to reduce VRAM to around 500mb before launching the game. This helped a little bit. I also tested a bunch of wine settings to slightly improve performance, I can't remember exactly what I did, but I was able to get the performance to around 15fps with some tinkering. 

Now the game was playable (I know 15fps is not great, but in my opinion I don't mind playing at those framerates, I have done so before). So I tried it, and after a few minutes, it would hard crash. This is the problem that I spent weeks troubleshooting, I have literally probably spent 20+ hours looking up solutions, trying everything I could possibly think of, combine through the config files for the game and testing all the settings, reducing resolution to 640*480, everything I could try. I thought the issue could be I was still VRAM limited since I was maxed out still, but that was really just a wild guess. I did not have anything to support that claim. 

I did not think it was temperature related since the GPU sat at under 55 C (the fan did not even turn on) and the GPU also was under 55 C, but I played with fan settings on GPU and CPU anyways. I increased the fan speeds, and then added extra fans to my computer, and they did literally nothing. It still crashed. I have kind of been completely stumped for the last week, I had tried literally everything I can think of, I even tried the game on a more powerful computer with an RTX 3070 ti, and while it was much better, it still crashed every couple hours. And lots of people online have a similar experience with high end setups. 

Really I was at a point where I had only a few ideas to what could cause it:
- VRAM limit (I cannot test this since I do not have a better GPU I can throw in to test)
- Linux problems (I don't think so since it runs on steam deck and is rated gold on protondb)
- NVIDIA driver problems (idk, I hope not but I cannot really test for this)

# Overclocking?

And I could not test for any of these. Today I thought of overclocking. I did not think it would help, since I can only increase the clocks of the core which the core is not even being maxed out. But I decided to try it. I was able to get it running about 100 MHz faster core clocks, and 350MHz faster memory clocks, and it was stable through stress tests, and all other games I played. Once I opened avowed though, it **IMMIDIATELY** crashed. And it did this EVERY SINGLE TIME. It was the same type of crash as before, but way sooner. 

Now this was weird. I had already done the steps to check that this is actually an issue with the overclocking, and not something else that caused it, so I decided that since the overclock made the game more unstable, would an underclock make it more stable?? Yes it did. I underclocked by about 200 MHz and **the game is now rock solid**. As well as performance has greatly improved. Now at 1080p I can play on low settings and get 20-30fps rather than 15 or so on 720p. *This is amazing*. 
![underclock-results](image.png)

Now I am still confused about why this is the case. Typically when an underclock is needed it is due to failing hardware, or not enough cooling performance. I doubt the failing hardware since my GPU works fine in all other tasks even extreme stress tests (although it could be this due to the GPU being 6 years old, and having been run 24/7 for this whole time). I also doubt the cooling issue since it is one of those monster 2 fan cards, that always stays under 60 C. I know that it could technically be getting way hotter on a different part of the chip than the sensor, but would it really cause one part of the chip to be ~55 C and another part to be overheating at ~100 C? That just seems a bit extreme to me. Although it could be like the memory is overheating or something since there is no sensor on there. 

Really I don't know what caused the problems, and why an underclock fixed it, but this was a fun project, and I am glad I have a solution (as weird as it is). I spend so long on this project, I do not even remember half of the things I tested, but I tried a lot, and the solution ended up being really weird. There must be a logical explanation to this, but I am not sure of it. 