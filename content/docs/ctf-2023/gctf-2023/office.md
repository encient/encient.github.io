---
title: "Office"
description: ""
summary: ""
date: 2024-04-03T20:14:47+08:00
lastmod: 2024-04-03T20:14:47+08:00
draft: false
menu:
  docs:
    parent: "gctf-2023"
    identifier: "office-748e7451bf246f77c91c615e3f905c55"
weight: 180
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---
Format cell

## Description
I heard there are hidden information here, can you find it for me? <br>
Attachment: `challenge.xlsx`

## Solution
![](office-1.png) <br>   
The given tab in the excel sheet does not give us any useful information. We can try to search for hidden tabs. <br>   

![](office-2.png) <br>   
In Hidden3 tab, we will see that there are hidden texts in the cells. Changing the font colour or the fill colour will not help in revealing the text. <br>   

![](office-3.png) <br>   
Therefore, we can select all cells to change the format of the cells. <br>   

![](office-4.png) <br>   
Change the format to text so that the hidden text will be visible. <br>   

![](office-5.png) <br>   
Once the hidden texts are shown, we can kind of see that it is a QR code. We can apply rules to the cells so that it will fill with colour automatically. <br>   

![](office-6.png) <br>   
Image above shows the rules set by us to colour the cell. <br>   

![](office-7.png) <br>   
Once the new rule is applied, a clear QR code will be shown and it will redirect us to the flag. <br>   

## Flag
`GCTF2023{F0rmatt1ng_c311s_t0_h1d3_inf0rm4t10n}`