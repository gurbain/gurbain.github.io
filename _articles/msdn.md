---
title: Mass-Spring Damper Networks, emerging locomotion on compliant structures
subtitle: Morphological properties of mass-spring networks for optimal locomotion learning. Published in Frontiers in Neurorobotics (2017).
date: 2017-03-27
context: Ghent University &mdash; HBP
category: PhD
sectors: [Academic]
tags: [Compliant Robotics, Neurorobotics, Machine Learning, Python, ML Control Policy]
thumbnail: /img/msdn/thumb.png
hero_image: /img/msdn/hero.png
---

## Robotic embodiment

The combination of brain-inspired AI and robotics is at the core of [our work in the Human Brain Project](http://neurorobotics.net/). Applying machine learning methods to control robots is not as straightforward as it may seem: robots generally evolve in noisy and continuously changing environments, but on the other hand, their **mechanical complexity can be an asset to simplify the control**. This is studied through the fields of embodiment and morphological computation. Extreme examples &mdash; like McGeer's passive walker &mdash; have shown that mechanical structures can produce natural behavior with no controller at all.

<figure>
<iframe style="aspect-ratio:16/9;width:100%;max-width:640px;display:block;margin:0 auto" src="https://www.youtube.com/embed/CK8IFEGmiKY" frameborder="0" allowfullscreen></iframe>
<figcaption>Video illustration of the passive walker principles. Source: Ngoya Inst. Tech on youtube</figcaption>
</figure>

## Towards a formalization

Recent investigations tried to formalize the relation between the dynamical complexity of a mechanical system and its capability to require simple control. To extend this research, we developed a basic simulator of **mass-spring-damper (MSD) networks** and optimized a naive locomotion controller to provide them with efficient gaits in terms of traveled distance and dissipated power.

Three experiments were done in open-loop to determine the influence of the **size of a structure** (number of nodes), the **compliance** (inverse of spring stiffness) and the **saturation at high powers**.

<figure>
<iframe style="aspect-ratio:16/9;width:100%;max-width:640px;display:block;margin:0 auto" src="https://www.youtube.com/embed/E8Mo0UZuP0I" frameborder="0" allowfullscreen></iframe>
<figcaption>A video illustration of the main research results published in our paper.</figcaption>
</figure>

In the second part of the work, we demonstrated the capacity of realizing closed-loop control in a very simple way, requiring very few numerical computations.

<figure>
<img src="/img/msdn/cl.png" alt="Closed-loop learning pipeline">
<figcaption>The principal components in the closed-loop learning pipeline consist in a readout layer which is trained at each time step, and a signal mixer that gradually integrates the feedback in the actuation signal. Source: Urbain et al., <em>Frontiers in Neurorobotics</em>, 2017.</figcaption>
</figure>

## Our contribution

A full discussion of the results is accessible directly in the [Frontiers article](http://journal.frontiersin.org/article/10.3389/fnbot.2017.00016) under Creative Commons license.

This work was realized at Ghent University together with [Jonas Degrave](http://317070.github.io/), [Francis wyffels](https://be.linkedin.com/in/francis-wyffels-198b894), [Joni Dambre](https://be.linkedin.com/in/joni-dambre-4886381) and Benonie Carette. It is mainly academic and provides a methodology to optimize a controller for locomotion, along with indications on what we can expect from its complexity to realize this experiment. The same knowledge was reused later in the project to conduct similar experiments on quadruped robots both in the real world and in simulation using the [Neurorobotics Platform (NRP)](https://neurorobotics.net/) developed in HBP.

## Going further

- [Full paper (open access)](https://www.frontiersin.org/articles/10.3389/fnbot.2017.00016/full).
- Simulator code: [github.com/Gabs48/SpringMassNetworks](https://github.com/Gabs48/SpringMassNetworks).
- Follow-up on HyQ: [Compliance and cerebellum-inspired control on HyQ]({{ '/articles/hyq/' | relative_url }}).
