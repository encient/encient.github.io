---
title: "Find Me 2"
description: ""
summary: ""
date: 2024-10-14T01:07:24+08:00
lastmod: 2024-10-14T01:07:24+08:00
draft: false
menu:
  docs:
    parent: ""
    identifier: "find-me-2-96e1a5cd1810be4706e83f41f61f11b1"
weight: 60
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---
### Description
![](findme21.png) <br>   
Challenge description gives a hint that we need to make contact with him, which means we might need to message him or send an email to him. It also mentions that he dislikes replying through socials, hence email might be the way.


## Solution
![](findme22.png) <br>   
In his GitHub profile, we can get his LinkedIn and several GitHub repositories. <br>   


![](findme23.png) <br>   
His LinkedIn profile gives us a hint to email him, showing that we are on the right path. Since we can't find his email from his LinkedIn, we can try to search through his GitHub repositories. <br>

![](findme24.png) <br>   

`MyInfo` repo looks most interesting for me as it might contain his information like email. Looking through the commit, we can see the latest commit deleted a portion of code, which is the flag.   <br>   


![](findme25.png) <br>  
Just copy and run the Python script and it will print out the hacker's email. <br>   

![](findme26.png) <br>  
Send an email to this guy and we will get an immediate automatic reply, with the flag.
