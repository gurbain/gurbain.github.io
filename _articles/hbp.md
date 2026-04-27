---
title: PhD at AIRO (Ugent), five years on biologically inspired locomotion within HBP project
subtitle: My doctoral work on compliant robot locomotion at Ghent University, funded by the Human Brain Project.
date: 2020-09-01
context: Ghent University &mdash; HBP
category: PhD
sectors: [Healthcare, Academic]
tags: [Robotics, Neurorobotics, Proposal Writing, Public Speaking, TensorFlow, Gazebo/MuJoCo/Isaac]
thumbnail: /img/hbp/brain-wiring.jpg
hero_image: /img/hbp/brain-wiring.jpg
---

Between October 2015 and September 2020, I did my PhD at [AIRO](https://airo.ugent.be), the AI and Robotics research group of IDLab &mdash; Ghent University, imec, funded by the [Human Brain Project](https://www.humanbrainproject.eu/) (HBP). AIRO had been an early bet on physical AI: several of my fellow PhD students had hand-rolled deep-learning kernels in CUDA back when that was still unusual, and later moved to DeepMind, contributing to projects like WaveNet and AlphaGo. Two strands ran in parallel during my time there: AIRO&rsquo;s home agenda on machine learning and robotics, with its load of daily chats with my the rest of the team about recent AI and robotics advance, and HBP&rsquo;s neurorobotics ambition of plugging spiking brain models into embodied robots, with regular pluridisciplinar meetings all over Europe.

## My PhD thesis

**[Biologically inspired locomotion of compliant robots](https://biblio.ugent.be/publication/8720560)**, supervised by Francis wyffels and Joni Dambre. The thesis tackles three questions:

1. How to **transfer learned controllers from simulation to real compliant robots**.
2. The **trade-off between mechanical compliance and controller complexity** in dynamic locomotion.
3. Whether **reflex-based control on compliant structures** can be stabilised by **cerebellum-inspired stance correction**.

Three platforms supported the experiments: a simulated [mass-spring-damper network]({{ '/articles/msdn/' | relative_url }}), the in-house [Tigrillo]({{ '/articles/spinngrillo/' | relative_url }}) compliant quadruped, and the [HyQ]({{ '/articles/hyq/' | relative_url }}) hydraulic quadruped at IIT Genoa.

## Publications

Most of the papers below are also documented as standalone blog posts.

**Journal articles**

- 2021 &mdash; Urbain et al. *Effect of compliance on morphological control of dynamic locomotion with HyQ.* Autonomous Robots. &rarr; [blog post]({{ '/articles/hyq/' | relative_url }}).
- 2019 &mdash; Vandesompele, Urbain et al. *Populations of spiking neurons for reservoir computing: closed-loop control of a compliant quadruped.* Cognitive Systems Research. &rarr; [blog post]({{ '/articles/spinngrillo/' | relative_url }}).
- 2019 &mdash; Massi, Vannucci, &hellip;, Urbain et al. *Combining evolutionary and adaptive control strategies for quadruped robotic locomotion.* Frontiers in Neurorobotics.
- 2019 &mdash; Vandesompele, Urbain et al. *Body randomization reduces the sim-to-real gap for compliant quadruped locomotion.* Frontiers in Neurorobotics. &rarr; [blog post]({{ '/articles/simtoreal/' | relative_url }}).
- 2017 &mdash; Urbain et al. *Morphological properties of mass-spring networks for optimal locomotion learning.* Frontiers in Neurorobotics. &rarr; [blog post]({{ '/articles/msdn/' | relative_url }}).

**Conference papers**

- 2020 &mdash; Urbain et al. *Stance control inspired by cerebellum stabilizes reflex-based locomotion on HyQ.* ICRA. &rarr; [blog post]({{ '/articles/hyq/' | relative_url }}).
- 2019 &mdash; Vandesompele, Urbain et al. *Closed-loop control of a compliant quadruped with spiking neural networks.* BICA Meeting.
- 2018 &mdash; Urbain et al. *Design of a bio-inspired compliant quadruped robot for closed-loop locomotion control.* 2nd HBP Student Conference. &rarr; [blog post]({{ '/articles/spinngrillo/' | relative_url }}).
- 2018 &mdash; Urbain et al. *Calibration method to improve transfer from simulation to quadruped robots.* International Conference on Simulation of Adaptive Behavior (SAB).

## Inside the HBP Neurorobotics Platform

Within HBP, I belonged to the [Neurorobotics subproject](https://neurorobotics.net/) (SP10), whose mission was to connect spiking neural networks and simulated brain models to physical or simulated robots in a unified software stack: the **Neurorobotics Platform (NRP)**. Within my PhD, I:

- Contributed to the **NRP open-source codebase** (Python / C++ / ROS), particularly on the robotic side &mdash; Gazebo integration, hardware-in-the-loop with the NRP, transfer-learning utilities.
- Deployed [Tigrillo]({{ '/articles/tigrillodev/' | relative_url }}) on the NRP as a **reference platform** for closed-loop experiments with spiking CPGs.
- Acted as a practical &ldquo;user&rdquo; during integration phases: reporting bugs, **shaping the Python user API**, and **co-running tutorials** with the core platform team (TUM, Fortiss, SSSA, KTH).

The platform has since evolved and now lives on the [EBRAINS](https://ebrains.eu/) infrastructure.

## Education and community

Research consortiums of that size live and die on their education and community programmes. I was elected **Student Representative at the HBP Education Programme Committee** (a mandate that ran until May 2020), representing ~150 HBP-funded PhDs across Europe in strategic discussions about schools, grants and workshops. Beyond the day-to-day science, I organised, chaired or contributed to a steady stream of HBP events:

- **Pisa, Jan 2020** &mdash; scientific chair of the *4th HBP Student Conference*.
- **Belgrade, Jul 2019** &mdash; chair and committee member of the *HBP Young Researcher Event*.
- **Ghent, Feb 2019** &mdash; host and scientific chair of the *3rd HBP Student Conference*.
- **Stockholm, May 2018** &mdash; technical demonstration and lightning talk at the *HBP SGA1 European Review*.
- **Tokyo, Apr 2018** &mdash; presentation at the *Europe&ndash;Japan Neurorobotics Workshop*.
- **Brussels, Nov 2017** &mdash; demonstration at the *European Robotics Week 2017*.
- **Obergurgl &amp; Manchester (2016&ndash;2017)** &mdash; lightning talks and posters at the *HBP Schools on the Future of Neuroscience, AI and Computing*.


## Going further

- Full PhD thesis: [Biologically inspired locomotion of compliant robots](https://biblio.ugent.be/publication/8720560), UGent, 2020.
- Home group: [AIRO @ IDLab &mdash; Ghent University, imec](https://airo.ugent.be).
- Neurorobotics Platform: [neurorobotics.net](https://neurorobotics.net/) (now hosted on [EBRAINS](https://ebrains.eu/)).
