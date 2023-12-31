---
title: "A Thousand Words"
description: ""
summary: ""
date: 2023-12-30T21:15:24+08:00
lastmod: 2023-12-30T21:15:24+08:00
draft: false
menu:
  docs:
    parent: ""
    identifier: "a-thousand-words-5a0e57105d7e5c6d7cc5b0a06a27820c"
weight: 10
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---

## Description
A picture worth a thousand words...
<br>     
Attachment: `github.com.jpg`

## Solution
```bash
strings github.com.jpg
```
Use `strings` command to view the printable text of the image.

![](a-thousand-words-1.png)
We can see that there is a line which is related to SKRCTF and flag. Since the image name is `github.com.jpg`, it kind of gives us a hint that this might be a URL.

![](a-thousand-words-2.png)
Go to the [website](https://github.com/Hong5489/SKRCTF/blob/master/flag.jpg) and we will see that there is another image. Download and analyze it. 

![](a-thousand-words-3.png)
By using the same command which is `strings`, we will notice that there is a suspicious cipher in the last line of the image.

![](a-thousand-words-4.png)
Put it into [CyberChef](https://gchq.github.io/CyberChef) and decipher it. CyberChef is a useful tool for CTF players for cryptographic operations like decoding and decrypting. By decoding 3 times of Base64, the flag will be shown in the output section.