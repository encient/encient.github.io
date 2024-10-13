---
title: "Stop Slacking Off"
description: ""
summary: ""
date: 2024-10-14T00:55:46+08:00
lastmod: 2024-10-14T00:55:46+08:00
draft: false
menu:
  docs:
    parent: ""
    identifier: "stop-slacking-off-eb30e14a9251843d44a54dd9e37bf6aa"
weight: 999
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---
## Description
![](slack1.png) <br>
Challenge description hints that this is something related to Slack. The challenge is quite straight forward as only Slack folder is given to the participants.

## Solution
![](slack2.png) <br>   
From this [post](https://medium.com/@jeroenverhaeghe/forensics-finding-slack-chat-artifacts-d5eeffd31b9c), we know that all chats are stored in leveldb format. I did not able to find any leveldb viewer that allows me to view the file. <br>   

![](slack3.png) <br>   
Therefore, I tried to search for parsers online for parsing Slack artifacts and found this [tool](https://github.com/0xHasanM/Slack-Parser?tab=readme-ov-file). <br>   


![](slack4.png) <br>   
