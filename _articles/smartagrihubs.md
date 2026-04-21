---
title: "A drone that lands on its own: SmartAgriHubs"
subtitle: Autonomous drone flight, a docking ground station, and a 5G image pipeline for hyperspectral crop inspection.
date: 2021-06-15
context: Exobotic Technologies
category: Exobotic
tags: [Robotics, UAV, Navigation, Machine Vision, Embedded Linux]
thumbnail: /img/exobotic/smartagrihubs/demo-poster.webp
hero_image: /img/exobotic/smartagrihubs/demo-poster.webp
---

<figure>
  <video controls preload="metadata"
         poster="{{ '/img/exobotic/smartagrihubs/demo-poster.webp' | relative_url }}"
         style="width:100%; aspect-ratio: 16/9; background:#000; border-radius: var(--radius-md);">
    <source src="{{ '/img/exobotic/smartagrihubs/sah-demo-2021.mp4' | relative_url }}" type="video/mp4">
  </video>
  <figcaption>SmartAgriHubs demo, 2021. Credit: Exobotic Technologies.</figcaption>
</figure>

## Context

Under the Horizon 2020 [SmartAgriHubs](https://www.smartagrihubs.eu/) programme, [Exobotic](https://www.exobotic.com/), Robovision and Proximus joined ILVO and UGent around a single question: can a drone inspect a maize or potato field autonomously, week after week, and feed an AI-driven variable-rate sprayer? In June 2021 the consortium publicly demonstrated what **5G, AI-based weed detection and an autonomous drone** can do together to produce real-time task maps for site-specific spraying. I was technical lead on Exobotic&rsquo;s side of the demo.

## Technical aspects

Three building blocks had to fit together:

- **Autonomous charging ground station.** A compact outdoor enclosure that opens on request, guides the drone to a centred landing via a physical centering mechanism and a visual fiducial, and tops up the battery wirelessly between flights, so nobody has to be on the field to flip switches or swap batteries.
- **Closed-loop autonomous flight.** A PX4 autopilot driven by a MAVLink mission-manager on the companion computer. Takeoff and landing are synchronised with the station door; waypoints follow terrain at fixed AGL; the hyperspectral camera shutter is triggered in the loop, and each frame is logged with its GPS fix, IMU state and image id for downstream stitching.
- **5G imagery pipeline.** Hyperspectral frames are heavy; streaming them to the cloud as they are captured, rather than dumping to an SD card after the flight, collapses the inspect/decide turnaround to flight-time plus seconds. Robovision&rsquo;s vision pipeline turns them into segmented crop tiles and an actionable spray map.

## Results

The consortium flew a full closed loop (drone takeoff, hyperspectral capture, cloud inference, spray map) on real maize and potato plots. As a SmartAgriHubs representative put it: *&ldquo;the autonomous drone takeoff and landing solution of Exobotic is an important step towards truly autonomous drone flights, overcoming current limitations imposed by the balance between weight and battery size.&rdquo;*

Further reading:

- Exobotic project page: [SmartAgriHubs Ground Station](https://www.exobotic.com/solutions/blog-post-smartagrihubs-ground-station).
- AI4Agriculture at Agrifood Technology: [agrifoodtechnology.be](https://www.agrifoodtechnology.be/en/news/ai4agriculture).
- SmartAgriHubs programme: [smartagrihubs.eu](https://www.smartagrihubs.eu/).
