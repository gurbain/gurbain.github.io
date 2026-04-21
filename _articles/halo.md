---
title: Camera Sensor Fusion for Zero-Gravity Navigation
subtitle: Six-month Master thesis at MIT's Space Systems Lab on the HALO hardware extension for the SPHERES nano-satellites.
date: 2014-12-01
context: MIT Space Systems Lab
category: Student
tags: [3D Vision, Machine Vision, Industrial Cameras, C/C++]
thumbnail: /img/halo/inspect3.png
hero_image: /img/halo/hero.png
mathjax: true
---

## SPHERES &mdash; a testbed for experiments in zero gravity

If you were asked to picture an astronaut, you would probably imagine him in his space suit floating on the border between the blue curve of the earth atmosphere and the darkness of deep space. In practice, sending an astronaut out of his vehicle for an EVA (Extra-Vehicular Activity) is quite costly and hazardous, and many challenges had to be solved before being able to send a human being in such a hostile environment.

Robots are therefore good candidates to replace some EVAs for external damage inspection and repair &mdash; but a major challenge remains to perform safe and reliable navigation in a spatial environment. The [SPHERES](https://en.wikipedia.org/wiki/SPHERES) testbed has been imagined and designed by the [MIT Space Systems Lab](http://ssl.mit.edu/) then sent to the International Space Station in the first decade of this century to allow scientists and astronauts to conduct experiments in real zero-gravity: swarm robotics, vehicle rendezvous and docking, visual navigation, actuation through electromagnetic fields or gyroscopes, fluid mechanics, modular deployment, junior robot competitions, and more.

<iframe style="aspect-ratio:4/3;width:100%;max-width:560px;display:block;margin:0 auto" src="https://www.youtube.com/embed/MXLsu04QNHA" frameborder="0" allowfullscreen></iframe>

## A new hardware extension to improve visual navigation

Among the challenges induced by visual navigation in space, **accurate and reliable sensing** is of great importance. In a spatial environment, luminosity is either extremely dark or too bright for common sensors and the landscape includes large patches of uniform color with few visible details. This leads to failure of classical vision algorithms based on corner detection, which require detail and contrast. Another constraint is purely technical: it is difficult to embed a lot of computation power in a small satellite that has to navigate without external help.

To cope with these issues, a new extension for the SPHERES nano-satellites was proposed, called [HALO](https://en.wikipedia.org/wiki/SPHERES#HALO) (sent to the ISS at the end of 2016). It can support multiple cameras with different properties to merge their outputs into a more reliable and accurate representation of the external scene. In my thesis, I investigated different algorithms to realize this fusion between a 3D Time-of-Flight (ToF) camera, a stereoscopic camera setup and a thermographic camera.

<figure>
<img src="/img/halo/inspect3.png" alt="HALO hardware enclosing a SPHERES nano-satellite">
<figcaption>One SPHERES nano-satellite is encapsulated in the HALO hardware, which embeds extra batteries, an external Linux computer, four gyroscopes, a ToF camera, a thermographic camera and a stereoscopic setup. The full system and project is named INSPECT.</figcaption>
</figure>

## A probabilistic approach to fuse the sensor images

After discussions and bibliographic research, I focused on designing a procedure for **automatic calibration of the ToF and the stereoscopic camera** together, and **merging dense 3D point clouds** constructed from their outputs. Those tasks were realized using probabilistic theory and Bayes estimation. Tests were performed with three degrees of freedom on an air-cushion table, then with six degrees of freedom during parabolic flight sessions in a NASA Zero-G plane.

Though the automatic calibration method performed really well, the fusion algorithm failed to show significant improvements. It was concluded that the approach was not totally appropriate to work with such low-accuracy sensors and mechanical setup &mdash; but there was no time to implement new ideas before the end of the thesis.

<figure>
<img src="/img/halo/inspect4.png" alt="Camera setup and point cloud after fusion">
<figcaption>Left: a representation of the camera setup and the probability distribution for the ToF camera. Right: an example of the dense point cloud after fusion.</figcaption>
</figure>

## Going further

- [Master thesis PDF](https://github.com/gurbain/Master_thesis/raw/master/final/Gabriel_Urbain_PFE.pdf)
- [INSPECT paper at the 45th International Conference on Environmental Systems, 2015](http://hdl.handle.net/2346/64547) &mdash; D. Steinberg, T. Sheerin, G. Urbain.
- [NASA SPHERES](https://en.wikipedia.org/wiki/SPHERES), [HALO](https://en.wikipedia.org/wiki/SPHERES#HALO).
