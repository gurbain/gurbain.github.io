---
title: Tirigrillo, a microchip on four legs
subtitle: Details on the design, the electronics and the software architecture of the Tigrillo robot.
date: 2017-10-17
context: Ghent University &mdash; HBP
category: PhD
sectors: [Academic]
tags: [Robotics, Legged Robots, Compliant Robotics, Embedded Linux, Electromechanics]
thumbnail: /img/tigrillo/electrical_schema.png
hero_image: /img/tigrillo/hero.jpg
---

## Companion post

This post is the hardware-focused companion to [Tigrillo &mdash; a bio-inspired compliant quadruped]({{ '/articles/spinngrillo/' | relative_url }}). There, I covered why the robot exists. Here, I&rsquo;ll walk through what&rsquo;s inside.

## Mechanical properties

Tigrillo is a compliant quadruped &mdash; that&rsquo;s the whole point. Compliance is implemented with **detachable springs and dampers on the knees**, so the passive stiffness can be changed in minutes with a screwdriver and a stock of calibrated springs. Each leg has **one under-actuated knee** and one actuated hip.

The rest of the mechanical design was constrained by three requirements: **cheap, reproducible, versatile**. The robot weighs ~950 g and fits in a 30&nbsp;cm &times; 18&nbsp;cm box. All mechanical parts are 3D-printed or laser-cut, and the BOM was documented and released on GitHub so anyone in the HBP could rebuild one.

## Electrical architecture

- Four **Dynamixel RX-24F** servomotors (one per hip), chosen as a compromise between weight, torque and fast rotation speed.
- Four analog **Hall-effect knee-angle sensors**, each built around rare-earth magnets attached to the leg and a Hall sensor on the body. The sensor&rsquo;s transfer function is non-linear and requires a per-leg calibration table.
- **IMU** for the body (roll/pitch/yaw), **force sensors** on the feet for ground-contact detection.
- Power supply: **LiPo battery** feeding a DC step-up converter that provides 12&nbsp;V at up to 10&nbsp;A peak to the motors.

<figure>
<img src="/img/tigrillo/electrical_schema.png" alt="Tigrillo electrical schema">
<figcaption>Electrical architecture: power distribution, OpenCM low-level board, Raspberry Pi companion computer, and the Dynamixel chain.</figcaption>
</figure>

## Software architecture

- **Low-level board:** a Robotis **OpenCM** (ARM Cortex-M3) reads the analog sensors, talks to the Dynamixel servos, and publishes position / velocity / torque commands at high rate.
- **High-level board:** a **Raspberry Pi 3** running Ubuntu Mate 16.04 and the [Robot Operating System (ROS)](http://wiki.ros.org/). The CPG controller and the neural-network layers run here and stream commands to the OpenCM over USB.
- **Off-board:** a desktop computer runs the training and monitoring stack, connected to the robot over ROS topics on Wi-Fi.

The clean separation between the three boards made the sim-to-real transfer much easier: everything above the OpenCM can be swapped with a simulator, and the low-level board sees no difference.

## Code and documentation

All software is open-source on GitHub, along with the PCB designs and the mechanical files:

- [gurbain / tigrillo](https://github.com/gurbain/tigrillo) &mdash; software stack, ROS packages, controllers.
- [Tigrillo board documentation](https://github.com/gurbain/tigrillo) &mdash; schematics and BOMs.

## Going further

- [Tigrillo &mdash; the main research post]({{ '/articles/spinngrillo/' | relative_url }}).
- [Simulation-to-reality with domain randomization]({{ '/articles/simtoreal/' | relative_url }}).
