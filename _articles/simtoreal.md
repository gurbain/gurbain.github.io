---
title: From simulation to reality
subtitle: Bridging the learning gap on a compliant quadruped robot using domain randomization.
date: 2018-01-01
context: Ghent University &mdash; HBP
category: PhD
tags: [Robotics, Legged Robots, Machine Learning, Compliant Robotics, Neurorobotics, Reinforcement Learning]
thumbnail: /img/simtoreal/hero.png
hero_image: /img/simtoreal/hero.png
---

Research on adaptive locomotion has been conducted for many years, especially through neurophysiological and biomechanical studies generally carried out independently. However, those complex motor behaviors originate from interactions between the neural system, the musculoskeletal system and the environment, which makes exhaustive *in vivo* research hard to realize in practice. Embodied experiments on real robots are a promising solution to test the models in closed loop, but the latter generally require a long learning phase that can hardly be conducted on the real robot. A large community of researchers try to pre-train the models in simulation, but faces [the reality gap when transferring results on real platforms](https://www.ncbi.nlm.nih.gov/pubmed?Db=pubmed&Cmd=ShowDetailView&TermToSearch=10984047).

In [his last paper](https://www.frontiersin.org/articles/10.3389/fnbot.2019.00009/full), Alexander Vandesompele investigates the role of **body-parameter randomization** as a promising method of regularization during the transfer of a locomotion controller from simulation to reality. He used the [Tigrillo platform]({{ '/articles/tigrillodev/' | relative_url }}), the compliant quadruped whose electronics and software have been presented in a previous post. I had the opportunity to help with the design of some of the experiments, on what seems a good direction for improvements in robot learning.

## Going further

To better understand the challenges behind the sim-to-real gap, I recommend the following keynote lecture from **Pieter Abbeel**, a specialist in advanced reinforcement learning for robotics:

<iframe style="aspect-ratio:16/9;width:100%;max-width:640px;display:block;margin:0 auto" src="https://www.youtube.com/embed/MBQTu8P1N4M" frameborder="0" allowfullscreen></iframe>

The [BAIR Lab](https://bair.berkeley.edu/), led by Pieter Abbeel, has become a reference on bridging the sim-to-real gap.

Related reading:

- A. Vandesompele, G. Urbain, H. Mahmud, F. wyffels, J. Dambre. *Body Randomization Reduces the Sim-to-Real Gap for Compliant Quadruped Locomotion.* Frontiers in Neurorobotics, 2019. [Open access](https://www.frontiersin.org/articles/10.3389/fnbot.2019.00009/full).
