---
layout: post
title: "Moving companies"
date: 2020-06-30 19:05
categories: jekyll update
---

For the last 18 months or so, I've been working at one of the leading research institutions in the UK; a place where electrons are accelerated close to the speed of light, which creates spectacularly bright light over a wide range of wavelengths.
This light is then fired at samples to learn all sorts of things about them.
[Diamond Light Source](www.diamond.ac.uk) is seriously impressive:

<div style="display: block;margin-left: auto; margin-right: auto; width: 50%;">
{% include image.html url="/assets/diamond.jpg" description="Diamond Light Source" %}
</div>

# People can do awesome things

Walking around the inside of Diamond for the first time is pretty special.
The whole place is covered in pipes, and wires, and connectors.
There is steam firing out of holes, bright LED warning signs, and huge, solid looking cannisters with strange chemical names printed in bold lettering.
When you manage to peek inside one of the experimental hutches - where the science happens - it's more of the same, with a few more shiny surfaces. Some computers over here, some million pound x-ray detectors over there, you get the drill!

Having worked on building sites and tried to wire up small electronics projects, the _sheer amount_ of cabling and connections that have all been designed and connected properly is staggering.

# It is possible to do software well

Software is a slightly strange technical field, in that many people working at a high level didn't have a "formal training" - usually referring to a 3/4 year degree in Computer Science or something similar.
I am one of those people, and for a long time I merely tolerated software as a way of getting the things I wanted done: turning on and off an LED at a controllable rate is a favourite!

Because I was programming embedded devices, I learnt C.
And I learnt C within the context of [Atmel Studio](https://www.microchip.com/mplab/avr-support/atmel-studio-7).
Because there are many restrictions in what you can do with software on embedded devices, they can be a good way to get to know the hardware.
However, the tooling surrounding them is... less than modern.

During my time at Diamond I was introduced to a wealth of software engineering practices with many acronyms.
But what it boils down to is that there are now tools and systems available which can really help you to get your software working properly.
Other tools and systems can monitor your software, replicate it, and restart it if it breaks.

# Nobody knows everything

Given the complexity and challenges I have described already, you might not be surprised to learn that there is no single person at Diamond who knows about every detail of the machine and auxialliary components as well as the experts.

My first few meetings at Diamond were a bit daunting, as there seemed to be a never ending stream of acronyms and everyone, apart from me, was nodding along.
However, there are so many different areas to become an expert in at Diamond that as soon as you step beyond outside any immediate team, it's clear that there is a whole _other_ world of knowledge to learn about.
Indeed, Diamond is very special as an organisation, in that it is both **horizontally** and **vertically** integrated.
Some particular purchases and services are outsourced, but the vast majority of what makes Diamond _work_ is made and done at Diamond.
Everything from welding, to accounting, to [devices which suspend samples in mid air with soundwaves](https://www.diamond.ac.uk/Science/Research/Tech-Updates/2019/22-10-2019.html), to the high performance computing clusters, to the PCBs which measure the power flowing through the magnets, to the [podcasts](https://soundcloud.com/user-212409541/sets/shining-a-diamond-light).

Working at Diamond is a study on collaborating with people who know more about a specific thing than you are ever likely to.
It challenges you to be sympathetic to others, both to try and see the problem from their vantage point, and to explain what you are seeing to them.

# Where am I going?

From August, I will be working at [Oxford Nanopore Technology](https://nanoporetech.com/), trying to make the world a better place by contributing to their [VolTRAX](https://nanoporetech.com/products/voltrax) device.
VolTRAX is designed to automate sample preparation, making it easier to turn raw samples into something which can be sequenced. Sequenced as in: read the whole genome sequence by feeding it through a tiny hole in an especially shaped molecular structure while passing and electrical signal across the gap and measuring the differences induced by the different genome bases as they travel through. Here's a video to turn the jargon into images:

<iframe width="100%" height="315" src="https://www.youtube.com/embed/rXfS4wJoVLQ" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

This is a really exciting step for me.
ONT's devices have been to the middle of jungles, the arctic and [into space on the ISS](https://nanoporetech.com/resource-centre/dna-sequencing-microgravity-international-space-station-iss-using-minion).
I'm hoping I can be an important part of their journey and, by doing so, aid genomic research in hard to reach places.

**Thanks to everyone who helped me during my time at Diamond :D**
