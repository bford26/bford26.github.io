---
title: "Projects"
layout: splash
permalink: /projects/
date: 2016-03-23T11:48:41-04:00

header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/unsplash-image-1.jpg
#   actions:
#     - label: "Download"
#       url: "https://github.com/mmistakes/minimal-mistakes/"
  caption: "Photo credit: [**Unsplash**](https://unsplash.com)"

excerpt: "Choose from the various project types, or see the more iconic displayed further down the page."

intro: 
  - excerpt: ''

feature_row:
  - image_path: assets/images/unsplash-gallery-image-1-th.jpg
    alt: "placeholder image 1"
    title: "Programming"
    
    excerpt: 
    " * PyOrbit Contributions
      * *Gauntlet* OOP Codesample 
      *  PIC Code 
      *  QuadTree Implementation
      *  A* Maze Solver
    "

    url: "#test-link"
    btn_label: "Read More"
    btn_class: "btn--primary"

  - image_path: /assets/images/unsplash-gallery-image-2-th.jpg
    image_caption: "Image courtesy of [Unsplash](https://unsplash.com/)"
    alt: "placeholder image 2"
    title: "Circuit Designs"

    excerpt: "Audio Preamp, RF Oscillator, LNA"

    url: "#test-link"
    btn_label: "Read More"
    btn_class: "btn--primary"

- image_path: /assets/images/unsplash-gallery-image-3-th.jpg
    image_caption: "Image courtesy of [Unsplash](https://unsplash.com/)"
    alt: "placeholder image 2"
    title: "Hobby Projects"

    excerpt: "Bass Guitar, Wooden Furniture"

    url: "#test-link"
    btn_label: "Read More"
    btn_class: "btn--primary"


feature_row2:
  - image_path: /assets/images/unsplash-gallery-image-2-th.jpg
    alt: "placeholder image 2"
    title: "Placeholder Image Left Aligned"
    excerpt: 'This is some sample content that goes here with **Markdown** formatting. Left aligned with `type="left"`'
    url: "#test-link"
    btn_label: "Read More"
    btn_class: "btn--primary"
feature_row3:
  - image_path: /assets/images/unsplash-gallery-image-2-th.jpg
    alt: "placeholder image 2"
    title: "Placeholder Image Right Aligned"
    excerpt: 'This is some sample content that goes here with **Markdown** formatting. Right aligned with `type="right"`'
    url: "#test-link"
    btn_label: "Read More"
    btn_class: "btn--primary"
feature_row4:
  - image_path: /assets/images/unsplash-gallery-image-2-th.jpg
    alt: "placeholder image 2"
    title: "Placeholder Image Center Aligned"
    excerpt: 'This is some sample content that goes here with **Markdown** formatting. Centered with `type="center"`'
    url: "#test-link"
    btn_label: "Read More"
    btn_class: "btn--primary"
---

{% include feature_row id="intro" type="center" %}

{% include feature_row %}

{% include feature_row id="feature_row2" type="left" %}

{% include feature_row id="feature_row3" type="right" %}

{% include feature_row id="feature_row4" type="center" %}