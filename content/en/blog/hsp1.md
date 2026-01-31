---
title: "HomeServer Chronicles #1 : Hardware"
date: 2026-01-30T09:56:43-08:00
draft: false
tags:
  - blog
  - homeserver
categories: homeserver
description: Part 1 of a series on the construction of my homeserver.
---
I've been meaning to get around to writing about my homeserver for some time now but I've been so focused on getting it to a *perfect* state that I neglected to consider that it doesn't need to be *perfect* for me to talk about it. 
<br><br>
In this post I will outline **why** I am building a (new) homeserver and **what** I chose to meet those goals. In [later posts](https://sinjin.dev/en/tags/homeserver) I will go more into the software aspects. But first, let me tell you how I got where I am.

## Why
### The Story Begins...
In my sophomore year at university, I cobbled together a server to tinker with as I was curious about self-hosting and thought it would be a good learning experience. I had repurposed an old **4th gen i5** from my roommate's now-decommissioned gaming computer and got the absolute cheapest components to support it from eBay. This ended up teaching me quite a bit about server management over the following years as I hosted more and more services that I used with some regularity. 
### Disaster Strikes!
Once I opened the server up to friends to have them play some Minecraft on it while others were streaming movies from my **DVD** collection that I had ripped, the age of the hardware began to show. The integrated graphics on the CPU was not new enough to support hardware transcoding of **HEVC** video files (of which most of my collection was comprised after a lengthy re-encoding session), and so when some people were streaming movies, others were robbed of their Minecraft experience! This was absolutely unacceptable and so something had to change. I had also not allocated nearly enough storage for my movie collection (even after switching to a more space efficient encoding) and so it was due for a storage upgrade as well.

So with those problems in mind, here's what I ended up building.

## What

### CPU
For the **CPU**, I went with the [i5-10600](https://pcpartpicker.com/product/hftKHx/intel-core-i5-10600-33-ghz-6-core-processor-bx8070110600) for a number of reasons. The foremost consideration was the integrated **GPU**, specifically for its **UHD Graphics 630** media engine. As far as hardware-accelerated transcoding goes, **NVIDIA** is king, but if you've been on the internet anywhere in the last 4 years, you know that NVIDIA GPUs are not the easiest thing to get, especially at a reasonable price. **Intel** pretty much leads the market on integrated transcoding hardware though, so having an Intel CPU makes the most sense given my use case. The power draw, while not a major consideration, was a nice addition. I'm sure that some of you may be cringing at the idea of using a workstation-grade consumer CPU in a server environment, but for the case of specifically low user-count self-hosted apps, video transcoding, and Minecraft server hosting, it makes the most sense. 

### GPU
None :)
<br>
At least not yet. I'm open to adding a discrete graphics card in the future to tinker more with running AI inference locally.

### Motherboard
The motherboard that I went with is the [MSI Z490-A Pro](https://pcpartpicker.com/product/KXpmP6/msi-z490-a-pro-atx-lga1200-motherboard-z490-a-pro), though this choice was questionable in hindsight. There's nothing wrong with it functionally, but the main reason I chose it at the time was the massive amount of onboard SATA connections. Now, obviously I could've used an HBA card and connected my drives to that, giving me much more freedom in terms of motherboard choice, but having the numerous m.2 slots and a 2.5 gig ethernet port all-in made it a lot easier on me to hit the ground running without playing PCIe peripheral picker.

### Case
For the case, I went with the [Fractal Design R5](https://pcpartpicker.com/product/sjX2FT/fractal-design-case-fdcadefr5bk), which is a kind of pricey (and large) case, but I'm very happy with it so far. In terms of size, it is a blessing and a curse. Anyone who has built computers will tell you all about the woes of trying to build in a small form factor case. This case has no such issues. Even with the whopping **8** hard drive bays (not hot swap, unfortunately), the interior of the case is so roomy that I could sleep in it if I had to. It also has 2x**5.25 inch** expansion bays which will allow me to install my disk reader to continue digitizing my parents' DVD collection, which is a plus. All of those niceties pale in comparison to the single most important feature that made me fork over the cash to get this behemoth: the **sound dampening**. The case interior is lined with a heavy felt and has rubber rings on almost every component that connects to any other panel in the case. The case even came with dozens of rubber feet for each of the hard drive caddies to stop vibration noise. Having the server in my bedroom, this is a must. The old server would groan and rattle whenever anyone started watching a movie, and that was starting to drive me mad, and I was certainly not going to sell my kidney to do an all-flash NAS.

### Storage
Speaking of hard drives, I was a Facebook Marketplace warrior for months searching for the deal of a lifetime. I got incredibly lucky to get some relatively low spin-up time drives from someone who was upgrading their 4TB drives to 16TB (I see visions of my future), and so I ended up paying ~$20 per drive for 6 drives after setting aside 2 due to SMART issues and giving one away as a gift. I'm planning on using the drives that I've set aside as a cold backup for the mission-critical data from the main server so that I'm not wearing them down by having them spin up and down repeatedly or having them on perpetually. I'm purposely avoiding discussing the specifics of storage as I think it is better outlined in my post on the software stack. I will mention that I have the OS and app specific config/databases on an M.2 NVME SSD.

### Other Components
For completeness: I went with 32GB of DDR4 RAM (overkill for now, but nice to have), an 850W power supply given future GPU and HDD considerations, and I'm using a cooler master CPU cooler since I might end up overclocking to squeak out some more MC ticks. Nothing exciting to report on these fronts.

## Conclusion?
I don't have a real conclusion to make as this was more a ramble on the parts as a means of documenting exactly what is in the computer and less advice on what others should do. I hope you got what you were looking for from this, peace.