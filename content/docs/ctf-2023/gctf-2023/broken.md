---
title: "Broken"
description: ""
summary: ""
date: 2024-04-03T18:36:55+08:00
lastmod: 2024-04-03T18:36:55+08:00
draft: false
menu:
  docs:
    parent: "gctf-2023"
    identifier: "broken-c1dd630cd839462470552ede374238d0"
weight: 110
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---
Corrupted PDF

## Description
I got this pdf and it's very important to me. WHY CAN'T IT OPEN OMG!
<br />
Attachment: `challenge.pdf`

## Solution
The PDF file given is corrupted and the content cannot be read.
![](broken-1.png) <br />
We can use `exiftool` to check the metadata of the file. There is a warning says that this file has an invalid xref table.
![](broken-2.png) <br />
We can search the internet for online tools that can repair corrupted PDF files.
![](broken-3.png) <br />
Once fixed, scroll through the PDF file and we will see the flag at the bottom of the file.

## Flag
`GCTF2023{M3_4nd_my_Br0k3n_h3art}`
