---
title: "Projects"
layout: splash
permalink: /projects/

header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/unsplash-image-1.jpg

excerpt: "Choose from the various projects!"

feature_row_txt:
  - title: "Programming"
    excerpt: "* [PyOrbit Contributions](/projects/pyorbit/)\n* [Gauntlet OOP Codesample](/projects/gauntlet/)\n* [PIC Code](/projects/pic-code/)\n* [QuadTree Implementation](/projects/qtree/)\n* [A* Maze Solver](/projects/a-star/)"

  - title: "Circuit Designs"
    excerpt: "* [LNA](/projects/lna/)" #"* [Audio Preamp](/projects/audio-amp/)\n* [RF Oscillator](/projects/oscillator/)\n* [LNA](/projects/lna/)"

  - title: "Hobbies"
    excerpt: "* [Electric Bass Guitar](/projects/bass-guitar/)\n* [Wooden Furniture](/projects/wooden-furniture/)"

feature_row2:
  - image_path: /assets/my_images/finished_bass_recliner.png
    title: "Custom Bass Guitar"
    excerpt: 'This is a fun project I finish during the 2020 Summer. Hopefully, I can learn to play it soon.'
    url: /projects/bass-guitar/
    btn_label: "Read More"
    btn_class: "btn--primary"

feature_row3:
  - image_path: /assets/my_images/startScreen.png
    title: "Gauntlet OOP Codesample"
    excerpt: 'During the 2020 quaritine, I started this project to make a complete demonstration of my OOP skills. Typically tedious and boring, I decided to create a codesample that was greatly influenced my by nastalgia for the classic NES video game *Gauntlet*.'
    url: "/projects/gauntlet/"
    btn_label: "Read More"
    btn_class: "btn--primary"

feature_row4:
  - image_path: /assets/my_images/SelfConDist.png
    title: "PyOrbit Contributions"
    excerpt: 'A collection of work involing my research done at Oak Ridge National Laboratory.'
    url: "/projects/pyorbit/"
    btn_label: "Read More"
    btn_class: "btn--primary"
---

<!-- {% include feature_row id="intro" type="center" %} -->

{% include feature_row_txt %}

{% include feature_row id="feature_row2" type="left" %}

{% include feature_row id="feature_row3" type="right" %}

{% include feature_row id="feature_row4" type="left" %}
