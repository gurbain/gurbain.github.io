---
title: "Eriksbo: an autonomous spraying robot"
subtitle: 15 km of plant borders, ecological herbicides, and a robot that sprays only where it needs to.
date: 2024-01-01
context: Exobotic Technologies
category: Exobotic
tags: [Robotics, AGV, Navigation, Machine Vision, Embedded Linux, ROS, Docker, Python, C/C++]
thumbnail: /img/exobotic/eriksbo/aerial.jpg
hero_image: /img/exobotic/eriksbo/aerial.jpg
---

## Context

[Eriksbo Plantskola](https://eriksbo.se/) is a Swedish plant nursery with **15 km of plant borders to treat**. When they switched from conventional to ecological, biologically-based herbicides, the spraying frequency jumped from once every two months to **once every two weeks**, and blanket-spraying at that cadence was no longer economically viable. At [Exobotic](https://www.exobotic.com/) we partnered with Farm-NG and [ILVO](https://ilvo.vlaanderen.be/) to deliver an autonomous spot-spraying robot. In this project, I owned the software-engineering side, from architecture to field-ready product.

<figure>
  <img src="{{ '/img/exobotic/eriksbo/spraying.jpg' | relative_url }}" alt="The Eriksbo spraying robot operating between plant rows">
  <figcaption>The Amiga robot freshly shipped at Exobotic, before integration of hardware and tools. Photo: exobotic.com.</figcaption>
</figure>

## My role

As the senior software engineer on the project, I was responsible for:

- **Software architecture** of the whole robot, from low-level drivers to the field-operator UI.
- **Sensor and compute-hardware selection** to fit the architecture and the payload constraints.
- **Real-time embedded OS** setup so the stack runs safely and deterministically in the field.
- **Implementation**, together with my colleagues at Exobotic.
- **Navigation strategies**, based on RTK-GNSS teach-and-repeat, with seamless switch to visual navigation based on the tree rows detection.
- **Operator UI** to set up routes, configure spraying quantities, start missions and review results, with a return-to-dock on low battery or empty tank.
- **Fleet monitoring** system so Exobotic engineers can track robot health remotely and feed learnings back into the algorithms.

This project was a turning point for Exobotic: we moved from one-off demonstrators to a real product that has to work every day in production.

## Technical aspects

- **Platform.** A [Farm-NG Amiga](https://farm-ng.com/), 4-wheel-drive skid-steer, 200 kg payload.
- **Spot-spraying payload.** Co-developed with ILVO: a camera head, NDVI-based weed detection and fast solenoid nozzles that pulse only when the pixel below is labelled *weed*.
- **Software stack.** A modular suite based on Embedded Linux, Docker and ROS2.

## Results

The robot was delivered in December 2025. As the nursery owner put it: *&ldquo;With ecological herbicides, the frequency of spraying has to go way up. With 15 km of plant borders to spray on a bi-weekly basis, we had to look into automating this task.&rdquo;*

Further reading:

- Exobotic project page: [Eriksbo spraying robot](https://www.exobotic.com/solutions/blog-post-eriksbo-spraying-robot).
- Visual-navigation upgrade: [Exobotic on LinkedIn](https://www.linkedin.com/posts/exobotictec_agtech-ai-robotics-activity-7293653495197368320-DgIv/).
- Weed-detection partner: [ILVO](https://ilvo.vlaanderen.be/).
