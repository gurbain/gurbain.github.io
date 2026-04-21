---
title: Tigrillo &mdash; a bio-inspired compliant quadruped
subtitle: A small compliant quadruped platform for experiments on spiking CPGs, reservoir computing and transfer learning.
date: 2017-07-03
context: Ghent University &mdash; HBP
category: PhD
tags: [Robotics, Legged Robots, Compliant Robotics, Neurorobotics, Spiking Neural Networks, Embedded Linux, ROS]
thumbnail: /img/tigrillo/thumb.jpg
hero_image: /img/tigrillo/hero.png
---

## A small compliant quadruped for brain-inspired control

Tigrillo is the bio-inspired compliant quadruped platform I used throughout most of my PhD at AIRO &mdash; Ghent University. It is designed to be a **cheap, reproducible, compliant testbed** for experiments on Central Pattern Generators (CPGs), reservoir computing and transfer learning between simulation and the real world.

The robot uses tendon-driven actuators and spring-loaded knees to produce the passive compliance needed to study morphological computation on a real device &mdash; rather than purely in simulation.

## Bio-inspired controllers

On the control side, we developed a stack of bio-inspired controllers built around:

- **Central Pattern Generators** producing the basic rhythmic leg trajectories;
- **Liquid State Machines** (reservoir computing on spiking neural networks) as a general-purpose non-linear readout;
- **SpiNNaker** neuromorphic hardware (Spin3 board) mounted directly on the robot to run the spiking part in real time on dedicated neural hardware.

<figure>
<img src="/img/tigrillo/reservoir.png" alt="Reservoir computing architecture">
<figcaption>The spiking reservoir architecture running on SpiNNaker Spin3, embedded on the robot.</figcaption>
</figure>

## Simulation and sim-to-real

To iterate safely, Tigrillo was simulated in **MuJoCo / Gazebo** and integrated into the [HBP Neurorobotics Platform](http://neurorobotics.net/) so the same brain models could be tested in simulation and on the physical robot. This enabled a series of sim-to-real experiments using **domain randomization** techniques to close the reality gap &mdash; see the [simulation-to-reality post]({{ '/articles/simtoreal/' | relative_url }}).

<figure>
<img src="/img/tigrillo/simulation.png" alt="Tigrillo simulation in Gazebo">
<figcaption>The Tigrillo robot and its Gazebo simulation, used to train CPGs in simulation before transferring to the real platform.</figcaption>
</figure>

## Transfer learning

A large part of the experiments ran on the transition from **artificial neural networks** (trained offline with standard deep-learning tools) to **spiking neural networks** (deployable on neuromorphic hardware and biologically plausible). We worked on recipes for weight transfer, layer-by-layer distillation, and online fine-tuning on the robot.

## Going further

- [Tigrillo &mdash; hardware details and electronics]({{ '/articles/tigrillodev/' | relative_url }}).
- [Simulation-to-reality with domain randomization]({{ '/articles/simtoreal/' | relative_url }}).
- [Mass-Spring Damper Networks]({{ '/articles/msdn/' | relative_url }}) &mdash; the simulated foundation of this line of work.
- [SpiNNaker](https://apt.cs.manchester.ac.uk/projects/SpiNNaker/) at the University of Manchester.
