---
title: "HyQ, end-to-end neural network locomotion on a 90 kg quadruped robot"
subtitle: Reflex-based locomotion on a hydraulic quadruped, studied during a research stay at IIT Genoa.
date: 2018-09-15
context: Ghent University &mdash; IIT &mdash; HBP
category: PhD
sectors: [Academic]
tags: [Robotics, Legged Robots, Compliant Robotics, Neurorobotics, Machine Learning, Reinforcement Learning, Docker, ROS, Python, C/C++, Gazebo/MuJoCo/Isaac, Tensorflow, ML Control Policy, Model Predictive Control]
thumbnail: /img/hyq/hero.png
hero_image: /img/hyq/hero.png
mathjax: true
---

## Context

Between **June and September 2018** I spent four months as a visiting researcher in the Dynamic Legged Systems (DLS) group at **[IIT, Genoa](https://dls.iit.it/)**, under Claudio Semini and Victor Barasuol, as part of my PhD at Ghent University and within the [Human Brain Project]({{ '/articles/hbp/' | relative_url }}). The DLS group designs and operates **[HyQ](https://dls.iit.it/)**, a hydraulically actuated 90&nbsp;kg quadruped whose active-impedance joints can emulate any ratio of stiffness and damping. I joined the team working on HyQ&rsquo;s locomotion stack and ran two series of experiments that later became the two papers summarised below: one on the role of **joint compliance**, one on a **cerebellum-inspired stance controller**.


## Method

Both papers share the same reflex-based architecture, built on top of HyQ&rsquo;s Reactive Controller Framework (RCF). Three layers:

- **Active compliance** at the joints, emulating a rotational spring-damper $$\tau_f = \tau_{ext} + K_p(q_d - q) + K_d(\dot q_d - \dot q)$$, with tunable $$K_p$$ and $$K_d$$.
- **Reflex-based motion controller**: a feed-forward neural network that takes only the four Ground Reaction Forces (GRFs) as inputs and outputs the eight hip and knee joint positions and speeds. It is inspired by an **Extreme Learning Machine** (time buffer + random hyperbolic-tangent hidden layer + linear readout), with the readout trained by FORCE:
$$\mathbf{W}^{\mathrm{out}}_{k+1} = \mathbf{W}^{\mathrm{out}}_{k} - \mathbf{P}_{k+1}\,\mathbf{x}_{k}\,\mathbf{e}^{T}_{k+1}$$
- **Cerebellum-inspired stance module** sitting above the reflex layer, which corrects posture and balance based on which foot is supposed to be in contact.

<figure>
  <img src="/img/hyq/cereb_architecture.png" alt="Three-layer control architecture diagram">
  <figcaption>The shared three-layer architecture: robot + active compliance (bottom), reflex-based motion controller (middle), cerebellum-inspired posture module (top). Source: Urbain et al., ICRA 2020.</figcaption>
</figure>

## Paper 1: Effect of compliance on morphological control

Using this architecture as a probe, I swept 3,600 impedance settings on HyQ in simulation to understand how does compliance interact with the control task and if we could illustrate a transfer of morphological computation to compliant bodies? 

We observed that the cost of Transport grows almost exponentially with stiffness in the closed-loop system. In other words, the **biologically-inspired control architecture shows good performance *only* on compliant bodies**.

<figure>
  <img style="aspect-ratio:16/9;width:100%;max-width:700px;"  src="/img/hyq/compliance_stabilization.png" alt="COT, power, speed and accuracy as a function of stiffness">
  <figcaption>This figure shows the end-effector trajectories of the right front foot (red), the left front foot (purple), and also the trunk&rsquo;s center of mass (green). The experiment is repeated for two compliance values discussed in the paper: compliant (top), and stiff (bottom). It shows a deteriorated locomotion cycle at higher stiffness. Source: Urbain et al., <em>Autonomous Robots</em>, 2021.</figcaption>
</figure>


More details are discussed in the paper [Effect of Compliance on Morphological Control of Dynamic Locomotion with HyQ](https://biblio.ugent.be/publication/8698429/file/8698434.pdf).

<figure>
<iframe style="aspect-ratio:16/9;width:100%;max-width:700px;display:block;margin:0 auto" src="https://www.youtube.com/embed/2BUtWXqTzQY?si=2d0E7CN_tvdc2bPd" frameborder="0" allowfullscreen></iframe>
  <figcaption>A short video presentation of the paper published in <em>Autonomous Robots</em>.</figcaption>
</figure>

## Paper 2: Cerebellum-inspired stance control

In a second paper, I used the same control architecture to answer if a biologically-inspire *cerebellum controller* (top layer of the architecture) was helping to stabilize the locomotion control. To that goal, I implemented two different architecture for that *cerebellum controller*:

- **Predictive Stance Estimator (PSE)**: $$\mathrm{PSE}=f(t)$$, driven only by the desired gait pattern, biologically motivated by studies in human ataxia.
- **Reactive Stance Estimator (RSE)**: $$\mathrm{RSE}=f(z_{\mathrm{FR}},z_{\mathrm{FL}},z_{\mathrm{HL}},z_{\mathrm{HR}})$$, driven by the reflex network's own foot-height predictions, mimicking a feedback signal from the spinal chord to the cerebellum.

Over twelve experimental trials on the real HyQ, **all PSE trials reproduced the target gait**; **five out of six RSE trials diverged**. From a dynamic point of view, this indicates that reflex-based locomotion requires the clock signal to stabilize its limit cycle and achieve robust locomotion.

<figure>
  <img src="/img/hyq/cereb_nrmse.png" alt="NRMSE of neural predictions for PSE and RSE trials">
  <figcaption>NRMSE of the reflex-network predictions. Green: PSE trials, stable through the test phase. Red: RSE trials, diverging during closing/testing. Source: Urbain et al., ICRA 2020.</figcaption>
</figure>

More insights are provided in the paper [Stance Control Inspired by Cerebellum Stabilizes Reflex-Based Locomotion on HyQ](https://arxiv.org/pdf/2003.09327).

## Going further

Alongside the two published studies, I also got HyQ to **locomote end-to-end in simulation using deep reinforcement learning**, specifically using **TRPO** (Trust Region Policy Optimization), on the same Gazebo simulation model as the experiments presented here. The results and the code were never published however.

To follow-up on this subject:

- PhD thesis: [Biologically inspired locomotion of compliant robots](https://biblio.ugent.be/publication/8720560), UGent, 2021.
- Code Repository: [gurbain/hyq_ml on GitHub](https://github.com/gurbain/hyq_ml).
- DLS group and HyQ platform: [dls.iit.it](https://dls.iit.it/).
- Mass-spring network precursor: [Mass-spring networks for locomotion]({{ '/articles/msdn/' | relative_url }}).