---
title: "Dev(Sec?)Ops"
description: ""
summary: ""
date: 2024-10-14T01:07:10+08:00
lastmod: 2024-10-14T01:07:10+08:00
draft: false
menu:
  docs:
    parent: ""
    identifier: "devsecops-5e864cea1e1b5dbce258bafc1a5053bf"
weight: 80
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---
## Description 
![](devsecops1.png) <br>  
This is the continuation of DevOps 101 challenge. I wasn't able to solve this challenge during the competition due to time limitation, so I continued solving it after the competition ends because this challenge looks unique and interesting XD.

![](devsecops2.png) <br>  
These are the files we have in the VM. In order to understand more about GitLab, you can watch some [quick tutorials](https://www.youtube.com/watch?v=z7nLsJvEyMY).

## Solution
![](devsecops3.png) <br>   
`.gitlab-ci.yml` is used to define our project stages and jobs. `include` specifies those files to be included. This means that the 3 yml files in `jobs` folder are also included for this project. <br>   

From DevOps 101 challenge, you can see that there is a variable named `$FLAG`. I thought that it would be the flag and I tried it. <br>
Steps:
1. `nano build.yml` - add `- echo "$FLAG"`
2. `git add`, `git commit`, and `git push`
3. View job log

![](devsecops4.png) <br>   
![](devsecops5.png) <br>   
![](devsecops6.png) <br>   
Apparently the `$FLAG` variable does not contain the flag :p <br>   
![](devsecops7.png) <br>   
Looking back to the commit, we can see that there might be another variable named `REAL_FLAG`.

![](devsecops8.png) <br>   
So I tried again with `$REAL_FLAG` variable this time. <br>   

![](devsecops9.png) <br>   
Then we got the flag.

## Alternative Methods
The challenge creator shared two alternative methods to solve this challenge:
1. Declare `$REAL_FLAG` in one of the yml file, then reference it to `variables.yml` file 
2. Use `printenv` command to print all environment variables, and we will be able to see the `$REAL_FLAG` variable.

## Idea of the Challenge
According to the challenge creator, the idea of this challenge is about the misconfigurations of the variable. Both variables are set as "Visible". Although `$REAL_FLAG` is not shown in the commit, it still can be called and the output can be seen in job logs. <br>
Challenge creator (D4RKN19HT):
*the misconfig is, if you don't mask the variable, it will be visible in job logs if you echo it*

![](devsecops10.png) <br>   
The screenshot above shows the `$REAL_FLAG` variable in admin user's view.