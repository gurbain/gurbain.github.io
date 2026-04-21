---
title: "Arboto, a spin-off of Exobotic dedicated to tree nurseries"
subtitle: How a camera payload for a robot turned into a digital inventory product for plant nurseries.
date: 2022-06-01
context: Exobotic Technologies
category: Exobotic
tags: [Robotics, Machine Vision, 3D Vision, Deep Learning, Python]
thumbnail: /img/arboto/drone-nursery.png
hero_image: /img/arboto/drone-nursery.png
mathjax: true
---

## From a robot payload to a product

During a project between [Exobotic](https://www.exobotic.com/) and [ILVO](https://ilvo.vlaanderen.be/), we discussed with tree nursery owners and realised that our robot payloads could solve a much bigger pain than weeds for them: they were losing **weeks every season to walking every row, caliper in one hand, notebook in the other**, measuring trunk diameters to update their stock and their prices.

With my colleagues at Exobotic, we initiated a **spin-off, [Arboto](https://www.arboto.eu/)**, focused on that specific problem: help plant nurseries keep an accurate, up-to-date inventory of their plants, with diameter, species, position on the map, and everything a sales desk needs to quote a tree without walking it first.

<figure>
  <img src="{{ '/img/arboto/drone-nursery.png' | relative_url }}" alt="Aerial view of a European tree nursery with straight rows of young trees">
  <figcaption>The target environment: a European tree nursery, tens of thousands of trees in straight rows. Photo: arboto.eu.</figcaption>
</figure>

## My role

- **Co-initiator of the spin-off**, together with colleagues at Exobotic.
- **Collecting customer needs**, and translating to specifications and features to build arboto offer in an agile loop.
- **Machine-learning pipelines** for tree measurement. Two generations were designed.

### Generation 1 &mdash; cameras-only measurement

The first pipeline relied on stereo-depth + segmentation, no instrumented tree. The robot drives slowly along the row and for each tree captures several views at known ego-motion.

1. **3D depth estimation**, producing a dense depth map per view.
2. **Image Segmentation**, to detect the tree on the image, with the capability to differentiate it from the supporting bamboo, generally located just next to the tree trunk.
3. **Diameter measurement**, using statistical aggregation across different views, assigned to a tree position using the RTK-GPS pose at capture time. A single view is wrong by a few millimetres but it can reduce over a dozen views from slightly different angles if averaged smartly.

<div class="media-row">
  <figure class="media-row__card"><img src="{{ '/img/exobotic/land-a2/img_3359.jpeg' | relative_url }}" alt="Land-A2 robot carrying the measurement payload between young trees"></figure>
  <figure class="media-row__card"><img src="{{ '/img/exobotic/land-a2/img_3365.jpeg' | relative_url }}" alt="View down a nursery row as the robot moves along it"></figure>
</div>

The end result: with only a **depth camera and a GNSS sensor**, the payload measures trunk diameter at 1 m above ground with **~3 mm accuracy**, with no per-tree calibration.

### Generation 2 &mdash; smart labels

The second generation trades the depth reconstruction for a **smart label** attached to each tree. A ML model detects the label in the camera stream, measures the current trunk diameter up to **1 mm accuracy**, and associates it with the GPS coordinates of the tree.

<figure>
  <img src="{{ '/img/arboto/og-image.jpg' | relative_url }}" alt="Arboto smart label on a tree with the digital tree record displayed next to it">
  <figcaption>A smart Arboto label on a tree, with the live tree record (ID, species, size, row, status) linked to it. Photo: arboto.eu.</figcaption>
</figure>

## The Arboto product today

[Arboto](https://arboto.eu/) has since turned into a self-standing startup with its own product. In short: **&ldquo;just drive, measure everything.&rdquo;**

- **Smart labels.** The nursery labels its trees once with Arboto QR tags.
- **arbo-Eye.** A vehicle-mounted camera device that **reads every label automatically** as it passes, continuously, with no stopping &mdash; covering entire fields in minutes instead of hours.
- **Cloud inventory.** Scans flow straight into an Arboto dashboard: a live, up-to-date inventory with species, diameters, measurement history, positions on the field map, and a public scan page for visitors.

<div class="media-row">
  <figure class="media-row__card"><img src="{{ '/img/arboto/arbo-eye-render.png' | relative_url }}" alt="Render of the arbo-Eye vehicle-mounted scanning device"></figure>
  <div class="media-row__video">
    <iframe src="https://www.youtube.com/embed/8nhTXDUCgcE?rel=0&modestbranding=1" title="arbo-Eye demo" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
  </div>
</div>

## Going further

- Arboto (the spin-off): [arboto.eu](https://www.arboto.eu/).
- Scientific partner on the original project: [ILVO](https://ilvo.vlaanderen.be/).
- Exobotic Land-A2 platform: [exobotic.com/platforms](https://www.exobotic.com/platforms).
- The 4WD/4WS robot this pipeline originally ran on: [Land-A2 robot]({{ '/articles/land-a2/' | relative_url }}).
