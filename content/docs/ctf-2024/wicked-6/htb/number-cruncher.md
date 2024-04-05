---
title: "Number Cruncher"
description: ""
summary: ""
date: 2024-04-04T17:10:53+08:00
lastmod: 2024-04-04T17:10:53+08:00
draft: false
menu:
  docs:
    parent: ""
    identifier: "number-cruncher-13b2efbbb7360fe778c6e58ed4ff9ebe"
weight: 400
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---

## Description
Our brand new number-crunching program makes data impossible to retrieve! To prove it, try and decode this crunched up flag! <br>   
Attachment: `cruncher`, `flag.crunched`

## Solution
From the description, we know that the flag has been encrypted and has been outputted to `flag.crunched`. <br>   

![](numcrunch-1.png) <br>   
By looking at the encoded flag, we can see that it is in hex format. <br>   

![](numcrunch-2.png) <br>   
By using [Ghidra](https://ghidra-sre.org/), we can take a closer look into one of the functions named `crunch` which seems to be the function that encrypts the flag. From the function, we can see that the input is being xored `^` by the hex key `b3`. <br>   

![](numcrunch-3.png) <br>   
Therefore, we can go to [CyberChef](https://gchq.github.io/CyberChef/) to decode and decrypt it to get the flag.

## Flag
`HTB{uncrunch1ng_d4t4_f0r_fun_n_pr0f1t}`