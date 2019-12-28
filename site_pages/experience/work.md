---
layout: subpage
title: Work
permalink: /experience/work
menu: Experience
---

# Oct 2018 - Present _Diamond Light Source_

## **Graduate Software Systems Engineer**

[Diamond Light Source](https://www.diamond.ac.uk) is the UK's national synchrotron.
If you're new to synchrotrons, like I used to be, they are circular particle accelerators which are carefully designed to produce
extremely bright beams of light across the electromagentic spectrum, from infra-red to x-rays.
This provides the basis for a wide range of research at the molecular level and below.
There are many synchrotrons around the world, specialised for different applications relevant to the research done in the country.
Find out more [here.](https://lightsources.org/)

I am currently working across two teams at Diamond: _Beamline Controls_ and _High Level Applications_.

As a member of the _Beamline Controls_ team, I am working to support the research activites by ensuring that motors move, detectors measure and
safety systems protect, when they are needed, together.
This is an incredibly complicated task, as there are millions of data points to track and provide input into.
Diamond uses an open source control system for this purpose known as [EPICS](https://epics.anl.gov/).
Learning about the intricacies of EPICS and contributing to the global collaboration is an ongoing task for all our engineers.
In July I represented Diamond at the EPICS conference at [ITER](https://www.iter.org/), discussing our work into using web
applications for display and control.

In the _High Level Applications_ team, we work to produce software tools which can be used across a number of the systems in use at Diamond.
This ranges from tools with user interfaces and interaction with our databases which are used in the control room in live operations, to supporting our underlying build infrastructure.
This requires familiarity with a range of programming languages in use at Diamond - primarily _Python_, _Java_, _C++_ and _JavaScript_ - and has been very interesting so far as a place for me to test my ideas and develop work to a high standard quickly.

My most recent project, which is now looking to continue and develop, has been working on a web-based user interface to EPICS which fulfills all the requirements provided by our existing tools while providing the advantages of modern web applications.
Diamond is not a company which has been responsible for many web apps before so we have been working on a prototype to help us build up knowledge.
We decided to base our application around the core technologies of [React](https://reactjs.org/), [Redux](https://redux.js.org/) and [TypeScript](https://www.typescriptlang.org/).
Our project is open source so you van view our progress, and contribute, [here](https://github.com/dls-controls/cs-web-proto).

This required me to quickly learn how to write in JavaScript, then TypeScript, which I did not have much experience of before, and then quickly apply it to the React/Redux framework for web applications, which I had only had explained to me at a very high level.
This was quite an intense period of learning but I certainly do have a much better idea of how modern web applications are put together now!
(Although some of it still seems like magic!)

Before that, I worked to implement a machine learning algorithm to aid [Macomolecular Crystallography (MX)](https://www.diamond.ac.uk/Instruments/Techniques/Diffraction/MX) work at Diamond.
The general concept it to look at data as it comes out and provide users with an idea about which experiments will yield better data.
This project is documented here: <https://python-topaz3.readthedocs.io/en/latest/>

As part of this project, I worked on the automated data analysis infrastructure, and led meetings across teams to lay out a path for the future.
Here are some related links:

- Automated data analysis at Diamond: <https://github.com/DiamondLightSource/python-zocalo>
- Examples for new developers: <https://python-zocalo-examples.readthedocs.io/en/latest>
- Diamond specific implementations: <https://github.com/DiamondLightSource/python-zocalo-dls>

### Key Skills

- Working as part of a much larger company than I have experienced before
- EPICS Control System
- Large scale build and deployment
- Advanced Python, JavaScript, TypeScript, React, C/C++
- Continuous Integration (CI) and associated tools
- Git version control
- Presenting to a wide range of audiences (EPICS Collaboration vs public tours of Diamond)

# June - August 2016 _University of Southampton_

## **Internet of Things Internship**

After summer of second year, I had a great opportunity to experience my university from another side, working within the Electronics and Computer Science (ECS) department at Southampton.
The project involved working very independently to build on an initial concept for a weather station built around a Raspberry Pi.
Alongside the product itself, a series of tutorials would be written which would allow others to very easily replicate the setup and to install the software I designed.

Within a short time scale, this involved evaluation of multiple sensors and communication systems, as well as finding a suitable open source interface and store for the weather data.
Unfortunately, the main site we were hoping to use, which was hosted by the [Royal Meteorological Society](https://www.rmets.org/) to aid citizen scientists, was going through some major maintenance work at the time and so was unavailable.
Therefore, an open source third party solution was found.
The final system also used the [NMEA 0183](https://en.wikipedia.org/wiki/NMEA_0183) interface which was originally developed for GPS at sea but has now been adapted to a wide range of solutions.
This would allow any future work to easily interface to the device.

Selecting the correct hardware to recommend was a real challenge.
Temperature and pressure sensors are now extraordinarly cheap, but weather specific sensors vary wildy in range.
Simple devices are less than £50 with a big gap to the £1000 bracket for sophisticated devices.
With the aim to promote usage, the cheaper devices were recommended in the end with options in the software to interface to other hardware in the future.

In addition to the core aims of my project, I also helped out around the office with various PhD projects and experiments!
This was also a great opportunity to learn about the challenges of the postgraduate life.
I also learned about how to implement cloud computing principles with a [Microsoft Azure](https://azure.microsoft.com/en-gb/) workshop and helped to plan and execute sessions for the department's yearly [Smallpiece](https://www.smallpeicetrust.org.uk/) scheme, which helps young people get a head start in electronics.

### Key Skills

- Learning about version control with SVN
- Fast prototyping
- Product evaluation
- Writing tutorials
- Self-motivation and independent work

# September 2013 - September 2014, June - August 2015 _Breathing Buildings_

## **Engineering Internship**

I have chose to join together two separate periods at [Breathing Buildings](https://www.breathingbuildings.com/)
because they followed on from each other quite naturally.

Having left school, I began a [Year IN Industry (YINI)](https://www.etrust.org.uk/the-year-in-industry) to learn what it really means to be an engineer!
I was delighted to be working at a small company in Cambridge which was working to revolutionise ventilation!
Having developed the system as a Professor at the local uni, our CEO was working at a governmental level to decrease the energy spent ventilating buildings in Britain, exchanging powerful air conditioning for small fans which use the natural properties of air to create appropriate indoor atmospheres.
Shaun has gone on to become a director at [The Royal Institution](https://www.rigb.org/about/news/spring-2018/director-announcement) - yes, _that_ Royal Institution.

As a new member of the Project Delivery team, my first job was to learn everything I could about the work Breathing Buildings did: products, suppliers, sales methods, controls, site work, commissioning.
