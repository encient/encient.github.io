---
title: "Master Hidden Within the Slides"
description: ""
summary: ""
date: 2024-04-03T20:19:31+08:00
lastmod: 2024-04-03T20:19:31+08:00
draft: false
menu:
  docs:
    parent: "gctf-2023"
    identifier: "master-hidden-within-the-slides-eebc4135af55a0afce3b284e5bfe7b89"
weight: 190
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---
PowerPoint slide master

## Description
Just made a presentation, with flag. <br>
Attachment: `challenge.pptx`

## Solution
Hint is already given within the challenge title, which is slide master.

![](master-1.png) <br>   
Slide master is a feature that allows us to control the format of the entire presentation ([source](https://support.microsoft.com/en-us/office/what-is-a-slide-master-b9abb2a0-7aef-4257-a14e-4329c904da54)). To go to slide master settings, go to `View` --> `Slide Master`. <br>   

![](master-2.png) <br>   
Scroll through all the slides and we will see a suspicious string. <br>   

![](master-3.png) <br>   
Decode the string by using [CyberChef](https://gchq.github.io/CyberChef/) and we will get the flag.

## Flag
`GCTF{Sl1d3sss_M4staaaaaaa}`