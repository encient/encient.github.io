---
title: "Frequency"
description: ""
summary: ""
date: 2024-04-03T20:08:32+08:00
lastmod: 2024-04-03T20:08:32+08:00
draft: false
menu:
  docs:
    parent: "gctf-2023"
    identifier: "frequency-174564ca6cc8bf5d40872ed650bf8f32"
weight: 170
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---
Audio steganography - spectrogram

## Description
I can hear flag...I think....or I am insane? <br>
Attachment: `challenge.wav`

## Solution
Listening to the audio file will give us some weird "alien" sound. There is no useful information from the audio. Therefore, we can try analyzing the audio using tools like [Audacity](https://www.audacityteam.org/) or [Sonic Visualizer](https://www.sonicvisualiser.org/download.html).

![](frequency-1.png) <br>   
Waveform of the audio does not give us any useful information. In audio steganography, most of the time people hide information in the spectrogram. <br>   

![](frequency-2.png) <br>   
Therefore, we can try to view the audio in spectrogram. Spectrogram is a visual representation of the frequency of a signal and the amplitude, which is useful for hiding information. <br>   

![](frequency-3.png) <br>   
This is the spectrogram of the audio, which shows the flag. <br>   

## Flag
`GCTF2023{this_fl4g_sounds_weirddddddd}`