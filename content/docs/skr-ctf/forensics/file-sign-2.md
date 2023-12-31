---
title: "File Signature 2"
description: ""
summary: ""
date: 2023-12-30T21:00:55+08:00
lastmod: 2023-12-30T21:00:55+08:00
draft: false
menu:
  docs:
    parent: ""
    identifier: "file-sign-2-7edfd439b1c7b99bc7d990cef44d2317"
weight: 30
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---

## Description
My friend said that the previous flag is not the real message! Is this file the one that reveals the truth?
<br>    
Attachment: `file`

## Solution
![](file-signature-2-1.png)
Upon running `binwalk` command, we can see that there is a zip file embedded in this JPEG image.

```bash
binwalk -e file
```
Try extracting the file by running the command above and you will get the zip file.

![](file-signature-2-2.png)
It requires a password. The password is `skr` (which is quite guessy imo).

```bash
cat secret_msg
```
Use `cat` command to see the content in `secret_msg` and you will get the flag.