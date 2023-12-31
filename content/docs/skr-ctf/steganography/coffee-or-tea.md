---
title: "Coffee or Tea"
description: ""
summary: ""
date: 2023-12-30T21:28:18+08:00
lastmod: 2023-12-30T21:28:18+08:00
draft: false
menu:
  docs:
    parent: ""
    identifier: "coffee-or-tea-7c92919d08a48769642fa8ac560ad95d"
weight: 20
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---

## Description
We found a poem in Kuki Godam's desktop, we are thinking if it is hiding a message with some weird pictures...

## Solution
There are some written words and some pictures in the given PNG file. There are 8 pictures in a row for all 12 pictures. Hint given in the question telling us that text can be written in number format. Since there are 8 pictures, it seems like it represents 8 bits, which we can convert the picture into binary, then convert the binary to strings.

```bash
SKR{I_w
00110000 01110101 01001100 01000100
_pRe
01100110 00110011 01110010
_c
00110000 01000110 01000110 01000101 01000101
ee}
```

Use [online tool](https://www.rapidtables.com/convert/number/binary-to-ascii.html) to convert the binary to ascii, then combine with the written words, and you will get the flag.