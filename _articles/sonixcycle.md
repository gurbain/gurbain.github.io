---
title: SonixCycle &mdash; browsing Foley sounds by meaning
subtitle: A tool to browse large collections of Foley sounds using perceptual and semantic content. Published at Audio Mostly 2016 &mdash; patented as EP3430535.
date: 2016-10-01
context: UMons &mdash; numediart Institute
category: Student
tags: [Audio Processing, Machine Learning, C/C++, CUDA]
thumbnail: /img/sonixcycle/sonixcycle1.png
hero_image: /img/sonixcycle/hero.png
---

## A search problem for sound designers

Sound designers who produce Foley for films, TV and games typically maintain libraries of tens of thousands of recorded sounds &mdash; footsteps on gravel, doors slamming, cloth rustling, glass breaking, you name it. The problem is very simple to state: when you need &ldquo;a door slamming that sounds tense&rdquo;, how do you find it among 80,000 files?

Traditional solutions rely on **tags typed by a human** at ingest time. This is slow, inconsistent across a team, and blind to everything that isn't in the tag vocabulary. This R&amp;D project &mdash; conducted at the [numediart Institute](https://numediart.org/) of UMons in partnership with Dame Blanche SA and CETIC &mdash; aimed to complement text search with **perceptual and semantic similarity**, so the designer can browse the library the way it actually sounds.

## The pipeline

The core idea was to index each audio file at the level of its local perceptual content, not just its filename. For that we built a pipeline around the [Apache Solr](https://solr.apache.org/) search engine:

<figure>
<img src="/img/sonixcycle/sonixcycle1.png" alt="SonixCycle pipeline">
<figcaption>Each audio file is segmented every 10 ms, and features are extracted per segment: MFCCs, timbre descriptors, temporal envelope, spectral statistics. These features then feed a similarity index in Solr.</figcaption>
</figure>

- **Segmentation.** Every file is sliced into 10 ms windows; features (MFCC, timbre properties) are extracted per window.
- **Feature clustering.** A GPU-accelerated k-means groups features into a learned perceptual vocabulary, then a hierarchical classification layer produces the semantic facet on top.
- **Custom Solr similarity.** Solr's default similarity (TF-IDF / BM25) is designed for text, not for bag-of-audio-features. We injected a **cosine-distance similarity** operating on the audio-feature vector space so that the same Solr front-end handles both textual and perceptual queries.
- **Visualization.** A [t-SNE](https://lvdmaaten.github.io/tsne/) projection of the feature space lets the designer literally *see* regions of the library and explore adjacent sounds.

<figure>
<img src="/img/sonixcycle/sonixcycle2.png" alt="SonixCycle perceptual map">
<figcaption>The 2D t-SNE projection allows visual browsing of the library, where audio files that sound alike are spatially close.</figcaption>
</figure>

## Publication &amp; patent

The interface and the indexing workflow are protected under patent [EP3430535 / WO2017158159](https://worldwide.espacenet.com/patent/search?q=EP3430535). The research paper was published at **Audio Mostly 2016**:

- G. Urbain, C. Frisson, A. Moinet, T. Dutoit. *A Semantic and Content-Based Search User Interface for Browsing Large Collections of Foley Sounds.* [ACM DL](http://dl.acm.org/citation.cfm?id=2986436).

## Going further

- [numediart Institute](https://numediart.org/) &mdash; host lab at UMons.
- [Apache Solr](https://solr.apache.org/) &mdash; search engine the system is built on.
- [t-SNE](https://lvdmaaten.github.io/tsne/) &mdash; the visualization technique used for the perceptual map.
