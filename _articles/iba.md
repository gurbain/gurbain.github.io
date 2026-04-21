---
title: IBA DynamicARC &mdash; anti-collision &amp; motion clearance
subtitle: Contributing to the safety envelope of a proton-arc therapy gantry.
date: 2025-05-01
context: RBAI &mdash; Ion Beam Applications (IBA)
category: RBAI
tags: [Robotics, Electromechanics, Control & Planning, Safety, Medical, EMA/FDA Validation, Consulting]
thumbnail: /img/iba/dynamicarc.png
hero_image: /img/iba/dynamicarc.png
---

[IBA](https://www.iba-protontherapy.com/) presents [DynamicARC](https://www.iba-protontherapy.com/dynamicarc-0) as *&ldquo;the first spot-scanning proton arc method&rdquo;*, enabling *&ldquo;simultaneous dynamic beam delivery at variable energies while the gantry is rotating&rdquo;*. According to IBA, treatment is delivered from multiple directions for enhanced tumour coverage and healthy-tissue sparing, and the average delivery time can be reduced by up to 58&nbsp;% compared to current IMPT methods.

## My contribution

Under an RBAI engagement, I am working on the **anti-collision and motion-clearance systems** of the DynamicARC gantry: the mechatronic layer responsible for ensuring that no moving body enters a region it should not, at any point during a treatment.

The approach combines **camera-based sensors** with a **3D kinematics model** of the gantry, couch and surrounding equipment, so that real-time observation can be cross-checked against the geometric envelope of the planned trajectory.

## Going further

- Official IBA DynamicARC page: [iba-protontherapy.com/dynamicarc-0](https://www.iba-protontherapy.com/dynamicarc-0).
- Broader freelance context: [Starting RBAI]({{ '/articles/rbai/' | relative_url }}).
