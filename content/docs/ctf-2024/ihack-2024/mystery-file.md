---
title: "Mystery File"
description: ""
summary: ""
date: 2024-07-29T11:31:07+08:00
lastmod: 2024-07-29T11:31:07+08:00
draft: false
menu:
  docs:
    parent: ""
    identifier: "mystery-file-1cee6fd72170b6c3ead54580a6818c84"
weight: 40
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---
## Description
A company has engaged your team to conduct a Digital Forensics and Incident Response (DFIR) analysis on their compromised image servers. During the investigation, your team discovered a suspicious file named "program.bin" in an unconventional binary. The nature of this file, including its content and unusual placement, strongly suggests that it could be a malicious payload or a backdoor script. The team is tasked with analyzing this file to determine its purpose and potential threat. <br>   
Attachment: `mystery file.zip`

## Solution
![](mys-1.png) <br>   
By using `file` command to see the file type, we know that it is a zip file. After unzipping it, it gives us `config.dat` which seems like a file with plaintext. <br>   

![](mys-2.png) <br>   
Looking into the file, it seems like it is heavily obfuscated. However, instead of the .dat file, it looks more like a bash script as it contains `eval`. <br>

> 💡 `eval` in Bash programming language is mostly used to execute command. <br>    

Therefore, we proceed to search for tools that can perform bash script deobfuscation. Here are the tools that can be used:
- [tio.run](https://tio.run/#)
- [DeBash](https://dsh.deno.dev/)
- [Bash Frustrator](https://github.com/anubhavanonymous/Bash_Frustator)

![](mys-3.png) <br>   
We used Bash Frustrator which is a Python tool to deobfuscate the script.

![](mys-4.png) <br>   
After the first deobfuscation process, the script seems like no change and still has long unreadable strings. However, we noticed that `eval` became `echo`, and the script is actually shorter compared to the previous script. Therefore, we think that the script might have several layer of obfuscation. <br>   

![](mys-5.png) <br>   
After several times of deobfuscation, we can finally read and understand the script. There is a function which has encoded command. <br>   

![](mys-6.png) <br>   
Decode the command and we will get the content. We need to visit the URL to get the flag. <br>    

![](mys-7.png) <br>   


## Flag
`ihack24{0bfusc4t3d_thr34t3}`