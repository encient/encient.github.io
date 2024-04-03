---
title: "Wireshark 1"
description: ""
summary: ""
date: 2024-04-03T19:26:25+08:00
lastmod: 2024-04-03T19:26:25+08:00
draft: false
menu:
  docs:
    parent: "gctf-2023"
    identifier: "wireshark-1-6a8ae2c6a2a2ff56bebdf51a23e9cb03"
weight: 130
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---
Search string within packets

## Description
It's cleartext :3 <br />
Attachment: `challenge.pcap`

## Solution
### Solution 1: Search String
Since the challenge description says that the flag is in cleartext, we can straightaway search for the flag within the packets.
![](wireshark-1-1.png) <br />
`Edit` --> `Find Packet`
<br>    
![](wireshark-1-2.png) <br />
We can search for packet details that contain the string which is the flag format `gctf` and we will get the flag. 

### Solution 2: Filter Data
![](wireshark-1-3.png) <br />
We can also use the filter to filter for text data to get the flag.

## Flag
`GCTF{fl4g_in_tcpdump_ez}`