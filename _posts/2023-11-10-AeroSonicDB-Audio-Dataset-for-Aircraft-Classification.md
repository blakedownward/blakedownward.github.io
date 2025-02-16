---
layout: post
title: AeroSonicDB (YPAD-0523) Dataset for Acoustic Detection and Classification of Aircraft
image: "/posts/AeroSonicDB-Technical-Report-arXiv.png"
tags: [Audio, Signal Processing, Dataset, Deep Learning, Open Source, Machine Listening]
---

AeroSonicDB is a completely novel, open-source audio dataset for research and development in the field of Environmental Sound Classification and Machine Listening.

> **Tip:** Clone the following repo to download the dataset and start training an acoustic aircraft detection model. [github.com/aerosonicdb/AeroSonicDB-YPAD0523](https://github.com/aerosonicdb/AeroSonicDB-YPAD0523)

---

## Project Introduction:

AeroSonicDB originally started as a challenge for me to apply advanced machine learning and audio signal processing techniques to a novel task. With the abscense of open-source datasets or models to leverage, this project would require me to deliver an end-to-end deep learning solution, complete with all the bumps and critical decisions faced by machine learning engineers.

Not only did this project propel and deepen my understanding of signal processing in general, but it led to developing wide variety of technical and soft skills, such as:
- Delpoying a remote, standalone device (Raspberry Pi 4B) interfaced with a software-defined radio and GPS.
- Collaborating with an industry expert to open-source the dataset and present a paper with benchmark results.
- Collecting data and running inference at the edge with a microcontroller (Arduino Nano Sense).
- Developing a custom front-end application for verifying and annotating audio files - vastly reducing the time spent labelling samples.

<p align="center">
  <img src="{{site.url}}\img\posts\AeroSonicDB-Technical-Report-arXiv.png" width="600"/>
</p>

## Key Takeaways:

- Popular dataset with two citations and approx 2,000 downloads in 12 months.
- Ready to use pipeline can allow beginners to start training a detection model within minutes.
- AI assistance built into later versions of the annotation application to speed up annotation even further.
- Training tiny models to run inference in real-time on a low cost, low energy microcontroller.


