---
title: "Godam Secrets"
description: ""
summary: ""
date: 2023-12-30T21:06:48+08:00
lastmod: 2023-12-30T21:06:48+08:00
draft: false
menu:
  docs:
    parent: ""
    identifier: "godam-secrets-eeb7c74b05cc4f77de2fc742d654b7e6"
weight: 15
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---
## Description
We managed to recover part of Godam's hard drive in his house, but we couldn't find anything suspicious. We hope you can help us in finding his secret.
<br>     
Attachment: `godam_hard_drive.zip`

## Solution
We were given Mozilla folder which contains the Firefox browser details. There are a lot of them, so we have to know which is the exact file that we have to investigate. This [video](https://www.youtube.com/watch?v=RKgGa6Rc2N8) tells us that we can analyze the artefacts with several information, shown below:
- Browser history: `places.sqlite`
- Browser cookies: `cookies.sqlite`
- Form data (data entered into forms and search boxes): `formhistory.sqlite`

![](godam-secrets-1.png)
We can use `sqlitebrowser` to analyze the mentioned files. We can go through the browser history in `/home/godam/.mozilla/firefox/profile/places.sqlite`. Note that there is a page with title "666 club". We know that this is related and suspicious as the secret letter (from previous steganography challenge - Secret Letter) is written by 666 club.

![](godam-secrets-2.png)
Visiting the URL will show us an authentication page which needs a secret key. The secret key is the flag of the previous challenge which is `SKR{hidden_text_in_color_hex_code}`. 

![](godam-secrets-3.png)
We can also get the secret key from `/home/godam/.mozilla/firefox/profile/formhistory.sqlite`.

![](godam-secrets-4.png)
Once authenticated, we can see that there is a post about flag in the website. It seems like the alphabets are reversed.

![](godam-secrets-5.png)
We can reverse it back by using [CyberChef](https://gchq.github.io/CyberChef/) or any other online tool to read the content of the post. The flag is the combination of all the capital letters in the content of the post.