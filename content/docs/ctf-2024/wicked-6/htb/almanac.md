---
title: "Almanac"
description: ""
summary: ""
date: 2024-04-04T17:10:45+08:00
lastmod: 2024-04-04T17:10:45+08:00
draft: false
menu:
  docs:
    parent: ""
    identifier: "almanac-9351f7342cb96dfe2d09aa07ab00d1a6"
weight: 300
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---

## Description
You've managed to steal Biff's secret sports channel almanac! Could he have hidden a flag somewhere inside? <br>   
Attachment: `almanac`

## Solution
![](almanac.png) <br>   
By using `file` command to see the file type, we know that it is an 64 bit ELF file. <br>   

```bash {frame="none"}
strings almanac | grep -i htb
```
As my first step of solving simple reverse engineering challenges, I will use `strings` command to see if we can get any information or even flag. For this challenge, we can easily get the flag using this command. 

## Flag
`HTB{7h15_b00k_t3ll5_th3_futur3!}`