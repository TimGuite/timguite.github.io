---
layout: subpage
title: Work
permalink: /experience/work
menu: Experience
---

# Oct 2018 - Present *Diamond Light Source*
## **Graduate Software Systems Engineer**

[Diamond Light Source](https://www.diamond.ac.uk) is the UK's national synchrotron.
If you're new to synchrotrons, like I used to be, they are circular particle accelerators which are carefully designed to produce
extremely bright beams of light across the electromagentic spectrum, from infra-red to x-rays.
This provides the basis for a wide range of research at the molecular level and below.
There are many synchrotrons around the world, specialised for different applications relevant to the research done in the country.
Find out more [here.](https://lightsources.org/)

As a member of the controls team, I am working to support the research activites by ensuring that motors move, detectors measure and
safety systems protect, when they are needed, together.
This is an incredibly complicated task, as there are millions of data points to track and provide input into.
Diamond uses an open source control system for this purpose known as [EPICS](https://epics.anl.gov/).
Learning about the intricacies of EPICS and contributing to the global collaboration is an ongoing task for all our engineers.
In July I represented Diamond at the EPICS conference at [ITER](https://www.iter.org/), discussing our work into using web
applications for display and control.

In my latest project, I have been working to implement a machine learning algorithm to aid [Macomolecular Crystallography (MX)](https://www.diamond.ac.uk/Instruments/Techniques/Diffraction/MX) work at Diamond.
The general concept it to look at data as it comes out and provide users with an idea about which experiments will yield better data.
This project is documented here: https://python-topaz3.readthedocs.io/en/latest/

As part of this project, I worked on the automated data analysis infrastructure, and led meetings across teams to lay out a path for the future.
Here are some related links:

- Automated data analysis at Diamond: <https://github.com/DiamondLightSource/python-zocalo>
- Examples for new developers: <https://python-zocalo-examples.readthedocs.io/en/latest>
- Diamond specific implementations: <https://github.com/DiamondLightSource/python-zocalo-dls>

### Key Skills

- Working as part of a much larger company than I have experienced before
- EPICS Control System
- Large scale build and deployment
- Continuous Integration (CI) and associated tools
- Git version control
- Advanced Python
- Presenting to a wide range of audiences (EPICS Collaboration vs public tours of Diamond)

# June - August 2016 *University of Southampton*
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