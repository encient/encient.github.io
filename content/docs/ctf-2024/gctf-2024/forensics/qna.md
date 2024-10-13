---
title: "Qna"
description: ""
summary: ""
date: 2024-10-14T01:03:02+08:00
lastmod: 2024-10-14T01:03:02+08:00
draft: false
menu:
  docs:
    parent: ""
    identifier: "qna-120fcdcba71abdd31e79ccd7bdfabe54"
weight: 999
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---
## Description
![](qna1.png) <br>   
Challenge description hints that the flag might be the answer of the Microsoft Security questions. Challenge attachments are all the registry files which hint that this might be something related to registry.

## Solution
![](qna2.png) <br>   
Through initial research, I found a [reddit post](https://www.reddit.com/r/sysadmin/comments/eatkjq/windows_10_security_questions_answers_stored/) mentioning that the answer to the security questions are stored in LSA secrets in the registry. After researching more, I decided to search for alternative solution as I think this might not be the solution as the process of decrypting is quite hard. <br>   
![](qna3.png) <br>   
After searching for tools to get the Windows Security answer, I found this [tool](https://www.nirsoft.net/utils/security_questions_view.html#google_vignette). Installing it and running it immediately shows us the result. 