---
title: "Shark of Wire"
description: ""
summary: ""
date: 2023-12-30T21:10:50+08:00
lastmod: 2023-12-30T21:10:50+08:00
draft: false
menu:
  docs:
    parent: ""
    identifier: "shark-d27be5e6f7ea7ecaa367f471d169ca76"
weight: 70
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---

## Description
OMG! I lost all my network history data, luckily I got capture some data on a **pcap** file, maybe the flag is inside the file.
<br>     
Attachment: `network_data.pcap`

## Solution 1
![[CTF Writeups/SKR CTF/Forensics/Attachment/shark-of-wire-1.png]]
Use `Protocol Hierarchy` to have an overview of the pcap file.

![](shark-of-wire-2.png)
We can see that there are several protocols. HTTP protocol is available and there are some line-based text data. Let's try to filter that out and see what's inside.


## Solution 2
![](shark-of-wire-3.png)
Another quicker way to solve this is to find the strings of the flag in packets.

![](shark-of-wire-4.png)
Choose `Packet Details` to see the details of the packet and type the flag format which is "skr" (case insensitive). The flag will be shown in the packet.

