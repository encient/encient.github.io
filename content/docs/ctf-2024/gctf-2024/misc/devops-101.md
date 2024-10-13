---
title: "DevOps 101"
description: ""
summary: ""
date: 2024-10-14T01:07:04+08:00
lastmod: 2024-10-14T01:07:04+08:00
draft: false
menu:
  docs:
    parent: ""
    identifier: "devops-101-a68960563f03163365bcd8f5d2f031f1"
weight: 70
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---
## Description
![](devops1.png)


## Solution
![](devops6.png) <br>   
Credentials are given in the VM. It is a challenge related to GitLab. GitLab is open source and it is normally used for DevOps and DevSecOps projects. <br>   


![](devops5.png) <br>   
Once signed in, we can see that there is only one project. We can go through the project and explore. <br>   

![](devops2.png) <br>   
In commit section, we will see several comments that have weird strings. The first part of the string has an equal sign as the first character. Therefore, I suspected that it is a base64 string, but in reversed order. <br>   

![](devops3.png) <br>   
We can find other parts of the string in the commit. <br>   

![](devops4.png)

