---
title: "File Signature"
description: ""
summary: ""
date: 2023-12-30T21:00:08+08:00
lastmod: 2023-12-30T21:00:08+08:00
draft: false
menu:
  docs:
    parent: ""
    identifier: "file-sign-9238efcb229c81d1f66369224cda9ebc"
weight: 20
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---

## Description
Kuki send me a weird file that no file extensions, can you figure what file is this??
<br>     
Attachment: `file`

## Solution
![](file-signature-1.png)
The file is given without any extension and hence we do not know what is the file type. Use `file` command to check the file type of the file, and it shows that the file is in JPEG format.

![](file-sgnature-2.png)
Use `mv` command to rename the file with extension. Then, use `eog` command to view the image. The flag will be shown in the image.


