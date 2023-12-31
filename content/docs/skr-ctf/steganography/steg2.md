---
title: "Steganography 2"
description: ""
summary: ""
date: 2023-12-30T21:35:15+08:00
lastmod: 2023-12-30T21:35:15+08:00
draft: false
menu:
  docs:
    parent: ""
    identifier: "steg2-746d48a40241a8df6d4cf4d5ac4b80df"
weight: 40
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---

## Description
Find a way to decode the payload that was hidden in the image file. You don't need to wink your eyes. The password is skr.

## Solution
The question says that there is a payload hidden in the image file and is password protected.

```bash
steghide extract -sf hackersteg.jpg
```
Therefore, we can try it with `steghide` and extract the text file which contains the flag.

```bash
cat steganopayload26011.txt
```
`cat` command is used to read the contents in the text file.

<br>     

> 💡 Why steghide? This comes with experience, where you will know that you have to use this tool most of the time when there is something embedded in the file and is password protected. So don't give up, practice makes perfect.