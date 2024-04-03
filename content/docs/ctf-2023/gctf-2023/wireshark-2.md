---
title: "Wireshark 2"
description: ""
summary: ""
date: 2024-04-03T19:34:04+08:00
lastmod: 2024-04-03T19:34:04+08:00
draft: false
menu:
  docs:
    parent: ""
    identifier: "wireshark-2-2c6934c3dbdf21f74606e58856c500fd"
weight: 140
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---
Export HTTP object

## Description
I remember there is a compressed file. Please find it and expose the secret! Same challenge file as Wireshark #1.

## Solution
Challenge description mentioned file, so we can try to search for objects in the export section. <br>     

![](wireshark-2-1.png) <br />
`File` --> `Export Objects` --> `HTTP` <br />

We chose to export HTTP objects as we can see that there are HTTP protocols in the packets. You can always choose other protocols to see whether there are any other objects transferred. However, the most common one is HTTP. <br>     

![](wireshark-2-2.png) <br />
Given hint is compressed file, we know that we need to focus on the zip file. We can then choose the `secret.zip` file and save it. <br>   

![](wireshark-2-3.png) <br />
However, the zip file is not able to be extracted or unzipped as it is corrupted. It is shown that the end-of-central-directory is not found. <br>     

![](wireshark-2-4.png) <br />
After some research, we found the signature of the corrupted part. <br>     

```bash {frame="none"}
hexedit secret.zip
```
![](wireshark-2-8.png) <br />
Edit the corrupted part with the correct signature and the zip file will be fixed. <br>    

![](wireshark-2-5.png) <br />
However, the zip file requires a password. The string in secret.txt did not work out for it. Therefore, we thought of bruteforcing the password. <br>     

```bash {frame="none"}
zip2john secret.zip > secret.hash
```
Use `zip2john` to generate hash for the zip file.

```bash {frame="none"}
john --wordlist=/usr/share/wordlists/rockyou.txt secret.hash
```
Then, use John the Ripper tool to bruteforce the password using `rockyou.txt` wordlist.

![](wireshark-2-6.png) <br />
The zip file password will be cracked successfully and the password is `batman`.

![](wireshark-2-7.png) <br />
Upon submitting the correct password, it will give us a file named “flag”. View it and get the flag.

## Flag
`GCTF2023{C0rrupted_Z1p_f1l3s}`