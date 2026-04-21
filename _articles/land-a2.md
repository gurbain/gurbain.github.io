---
title: "Land-A2: an agile 4WD/4WS robot for rough terrain"
subtitle: An electric tool-carrier designed for muddy tree-nursery aisles, with zero-turn kinematics and an RTK-GPS stack built from scratch.
date: 2022-01-01
context: Exobotic Technologies
category: Exobotic
tags: [Robotics, AGV, Navigation, Electromechanics, Embedded Systems, ROS, Python, C/C++]
thumbnail: /img/exobotic/land-a2/hero.webp
hero_image: /img/exobotic/land-a2/hero.webp
---

## Context

Tree nurseries are one of the nastiest outdoor environments a robot can be asked to work in: limited grip, constant mud, narrow aisles, bamboo stakes everywhere, and saplings the owner really does not want touched. At [Exobotic](https://www.exobotic.com/) we designed **Land-A2**, an electric tool-carrier meant to operate exactly in that environment, carrying sensor and treatment payloads along rows week after week. I was the main software engineer on the project and followed the electromechanical design closely.

## Electromechanical design

The engineering bet is **agility over size**: rather than scaling up wheels and horsepower to plough through, Land-A2 is small, light, and highly manoeuvrable. It runs on **4-wheel drive with 4-wheel independent steering**, so it can do true zero-radius turns and crab sideways into and out of a row without changing heading. A skid-steer would dig ruts and damage the soil around the trees; with 4WS the wheels roll rather than scrub.

- **Wheel motors.** In-hub electric drive, **100 Nm nominal / 320 Nm peak** per wheel, designed in-house.
- **Speed &amp; payload.** Up to ~6 km/h, **200 kg** centrally-mounted payload.
- **Chassis.** Patent-pending modular construction with adjustable wheelbase, spring-damped suspension, and a centrally-rotating payload area to reduce sensor vibration.
- **Batteries.** Quick-swap modules for field replacement, no tools required.

<div class="media-row" style="grid-template-columns: repeat(4, 1fr); gap: 10px;">
  <figure class="media-row__card" style="margin:0;"><img src="{{ '/img/exobotic/land-a2/chassis-pair.webp' | relative_url }}" alt="Pair of side chassis modules in the workshop" style="width:100%; height:220px; object-fit:cover; display:block;"></figure>
  <figure class="media-row__card" style="margin:0;"><img src="{{ '/img/exobotic/land-a2/banner.png' | relative_url }}" alt="Chassis side modules on the assembly bench" style="width:100%; height:220px; object-fit:cover; display:block;"></figure>
  <figure class="media-row__card" style="margin:0;"><img src="{{ '/img/exobotic/land-a2/wiring.png' | relative_url }}" alt="Electrical wiring inside a chassis module" style="width:100%; height:220px; object-fit:cover; display:block;"></figure>
  <figure class="media-row__card" style="margin:0;"><img src="{{ '/img/exobotic/land-a2/cad.png' | relative_url }}" alt="CAD render of the Land-A2 chassis" style="width:100%; height:220px; object-fit:cover; display:block;"></figure>
</div>

## Navigation and software stack

This is where I spent most of my time on Land-A2. The goal was a stack an operator with no robotics background can drive: *draw a route, press start, come back later.*

- **Sensors.** Dual-antenna **RTK-GPS** (centimetre position *and* heading, no motion needed for yaw), low-mounted **LiDAR**, multiple cameras and active IR / white lighting. The dual-antenna choice is load-bearing in a nursery, where scrub vegetation causes near-ground occlusions.
- **Navigation.** RTK-GPS waypoint following with smooth interpolation, plus a higher-level planner for row entry/exit, headland turns and speed adaptation. An optional **visual-only mode** (used at sites like [Eriksbo]({{ '/articles/eriksbo/' | relative_url }})) keeps the robot running where GPS is unreliable.
- **Obstacle avoidance.** Two-stage: a LiDAR occupancy map stops the robot on anything unexpected, and an **AI classifier** on the cameras filters out false positives (tall grass, shadows, leaves) so it will still drive close to the trees.
- **Operator UI &amp; stack.** A web-based GUI to record paths by teleop, edit waypoints and start/pause/return-home, on top of ROS 2 on Ubuntu Server, containerised with Docker, orchestrated as `systemd` services.

<div class="media-row">
  <figure class="media-row__card"><img src="{{ '/img/exobotic/land-a2/img_3359.jpeg' | relative_url }}" alt="Land-A2 between rows of young trees at the nursery"></figure>
  <figure class="media-row__card"><img src="{{ '/img/exobotic/land-a2/img_3365.jpeg' | relative_url }}" alt="Land-A2 driving down a muddy nursery row"></figure>
</div>

## In the spotlights

Land-A2 has been shown at agricultural fairs and used in live customer demonstrations. Three LinkedIn posts give a flavour:

<div class="linkedin-cards">
  <a class="li-card" href="https://www.linkedin.com/posts/exobotictec_robot-robotics-agtech-activity-6990261808108339200-NYH_/" target="_blank" rel="noopener">
    <div class="li-card__img" style="background-image:url('{{ '/img/exobotic/linkedin/land-a2-reveal.jpg' | relative_url }}');"></div>
    <div class="li-card__body">
      <div class="li-card__head"><span class="li-card__logo">in</span><span class="li-card__company">Exobotic Technologies</span></div>
      <p class="li-card__title">Meet Land-A2</p>
      <p class="li-card__desc">First public unveiling of the 4WD/4WS platform.</p>
    </div>
  </a>
  <a class="li-card" href="https://www.linkedin.com/posts/exobotictec_sima2022-wearesima-agtech-activity-6995852851189055488-tAq5/" target="_blank" rel="noopener">
    <div class="li-card__img" style="background-image:url('{{ '/img/exobotic/linkedin/sima2022-landa2.jpg' | relative_url }}');"></div>
    <div class="li-card__body">
      <div class="li-card__head"><span class="li-card__logo">in</span><span class="li-card__company">Exobotic Technologies</span></div>
      <p class="li-card__title">SIMA 2022 &mdash; Paris</p>
      <p class="li-card__desc">Land-A2 on the Exobotic stand at the SIMA international agtech fair.</p>
    </div>
  </a>
  <a class="li-card" href="https://www.linkedin.com/posts/exobotictec_agribex2023-livedemo-fair-activity-7138941051066544128-xRTT/" target="_blank" rel="noopener">
    <div class="li-card__img" style="background-image:url('{{ '/img/exobotic/linkedin/agribex-livedemo.jpg' | relative_url }}');"></div>
    <div class="li-card__body">
      <div class="li-card__head"><span class="li-card__logo">in</span><span class="li-card__company">Exobotic Technologies</span></div>
      <p class="li-card__title">Agribex 2023 live demo</p>
      <p class="li-card__desc">Land-A2 running a live autonomy demo in Brussels.</p>
    </div>
  </a>
  <a class="li-card" href="https://www.linkedin.com/posts/exobotictec_still-going-strong-after-5-days-40-hours-activity-7139901635153006592-vhPm/" target="_blank" rel="noopener">
    <div class="li-card__img" style="background-image:url('{{ '/img/exobotic/linkedin/agribex-endurance.jpg' | relative_url }}');"></div>
    <div class="li-card__body">
      <div class="li-card__head"><span class="li-card__logo">in</span><span class="li-card__company">Exobotic Technologies</span></div>
      <p class="li-card__title">5 days, 40 hours of demo</p>
      <p class="li-card__desc">Endurance run at the Agribex fair.</p>
    </div>
  </a>
</div>

## Going further

- Exobotic blog post: [Land-A2 prototype](https://www.exobotic.com/solutions/blog-post-arboto-prototype-robot-vehicle).
- Platforms overview: [exobotic.com/platforms](https://www.exobotic.com/platforms).
- Feature article (FR, Hectares magazine): [Comment est-ce fabriqu&eacute; &ndash; les robots d&rsquo;Exobotic Technologies](https://hectares.maglr.com/hectares-2023-001-fr/comment-est-ce-fabrique-les-robots-dexobotic-technologies).
- Follow-up on the camera-only perception pipeline: [Arboto &mdash; tree-measurement spin-off]({{ '/articles/arboto/' | relative_url }}).
