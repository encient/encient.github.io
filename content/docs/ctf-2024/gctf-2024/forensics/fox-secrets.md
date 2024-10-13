---
title: "Fox Secrets"
description: ""
summary: ""
date: 2024-10-14T00:56:07+08:00
lastmod: 2024-10-14T00:56:07+08:00
draft: false
menu:
  docs:
    parent: ""
    identifier: "fox-secrets-9e96632fde43e3cb3edc96a56c5595a3"
weight: 999
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---
## Description
![](fox1.png) <br>   
Challenge description hints that we need to find the password from Firefox. This might be the saved password of the user. The attachment given is an `ad1` file, so we need to use FTK Imager to open the file and navigate to Firefox file location.

## Solution
![](fox2.png) <br>   
Through some [research](https://support.mozilla.org/en-US/kb/profiles-where-firefox-stores-user-data), we will know that the Firefox saved passwords are stored in these two files, located in the Firefox user profile:
```PowerShell {frame="none"}
C:\Users\<your Windows login username>\AppData\Roaming\Mozilla\Firefox\Profiles\
```

![](fox3.png) <br>   
However, all the usernames and passwords are encrypted. <br>   

![](fox4.png) <br>   
There are several tools online to decrypt it, the tool I used is [this](https://github.com/unode/firefox_decrypt), which is found from a [YouTube tutorial](https://www.youtube.com/watch?v=DltXmGoaLVs).
