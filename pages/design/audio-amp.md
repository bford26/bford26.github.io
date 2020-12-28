---
layout: single
title: "Audio Pre-amp"
permalink: /projects/audio-amp/
classes: wide-nosb-toc
author_profile: false
toc: true

# input and output gain stages 
titled_gallery:
  - image_path: /assets/my_images/audio_amp/input_gain.png
    title: "Input Gain Stage"
    type: "top-titles"

  - image_path: /assets/my_images/audio_amp/output_gain.png
    title: "Output Gain Stage"
    type: "top-titles"

# ploted results
# gallery2:
---


This audio pre-amp is a part of the Custom Bass Guitar project. This pre-amp is used to provide more control over the sound of the bass. Specifications for this project were derived from available pre-amps, specifically the [Aguilar OBP-3TKPP](https://www.aguilaramp.com/pickup-series/obp-preamps/).

## Target Specifications

* 3-Band Equilizer
  * 40 Hz: $\pm$ 16 dB
  * 450 Hz: $\pm$ 13 dB
  * 6.5 kHz: $\pm$ 13 dB
* Input Impedance 1 M$\Omega$
* Output Impedance 100 $\Omega$
* 9 or 18 Volt PS
  
## Materials

* Amplifier
  * TL072
* Potentiometers
  * 100k$\Omega$ Linear
  * 25k$\Omega$ Log

<details>
  <summary>Resistors</summary>
    1. 10k
    2. 1.1k
    3. 2.2k
    4. 1M
</details>

<details>
  <summary>Capacitors</summary>
    1. 68n
    2. 10 $\mu$
    3. 470 $\mu$
    4. 0.68 $\mu$
    5. 4n
</details>

## Circuit Design

Due to the circuit size, the link below opens a zoomable image to see the entire circuit. However, the entire circuit is detialed below.

External Link: [Full Circuit Schematic](https://bford26.github.io/assets/my_images/audio_amp/full_circuit.PNG){: target="_blank" }

### Power Supply

Below is the power supply used for the circuit. Notice the voltage divider, which is used to provide room for the signal to swing from $V_{cc}/2$ instead of ground because we do not actually have a negitive voltage for negative rail.

![Power Supply](/assets/my_images/audio_amp/power_supply.png){: .align-center  width="60%" }

### Input Stage

The input stage of this circuit will set both the input resistance and -3dB $f_{low}$ point, which should be below 10 Hz. 

![Input Stage](/assets/my_images/audio_amp/input_stage.png){: .align-center}

### Gain Stages

These stages bridge the input and output stages to the Boost/Cut circuit, which are used to tune the baseline gain. The coupling capacitors cause some drop in the gain, which is counter acted by these stages. Note in the gain stage directly after the input stage a capacitor provides a feedback path, which is used to reduce the range for this circuit. This was used to hopefully save some DC power. The capacitor sets the $-3dB$ high frequency, ~27 kHz.

<!-- ![Input Gain Stage](/assets/my_images/audio_amp/input_gain.png){: .align-center}

![Output Gain Stage](/assets/my_images/audio_amp/output_gain.png){: .align-center} -->

{% include titled_gallery %}

### Kenneth James Boost/Cut Circuit

![Gain Stage](/assets/my_images/audio_amp/summing_feedback.png){: .align-center}

### Active Filters Stage

The active filter stage consists of a 3 band pass filters. The targeted frequency were 40, 450, and 6,500 Hz.

![Active Filters](/assets/my_images/audio_amp/gain_filters.png){: .align-center}

## Simulation Results




## Future Work

Currently, no real circuit has been made a tested. This is only the design, so hopefully I can order a PCB after I maKe a perf board prototype and verify the circuit. For the prototype I am only missing the two 25k pots and a handful of the capacitors, which I plan to purchase from the UTK parts store.

## Resources

* Sampson, Dave. "Bass Guitar Preamp Design", Baltika Group. [link](http://press.baltikagroup.com/wp-content/uploads/2014/07/Bass-Guitar-Preamp-Design.pdf)
* "The Top 10 Operational Amplifiers on SnapEDA", SnapEDA. Oct. 2019. Web. [link](https://blog.snapeda.com/2019/10/23/the-top-10-operational-amplifiers/)
<!-- * [link]() -->