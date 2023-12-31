---
title: "Forensics"
description: ""
summary: ""
date: 2023-12-30T18:53:00+08:00
lastmod: 2023-12-30T18:53:00+08:00
draft: false
menu:
  docs:
    parent: ""
    identifier: "Forensics-b22d0627f3346b1f7d591dd693704296"
weight: 999
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---

DNS exfiltration using tshark
```bash
tshark -r <PACKET_FILE> -T fields -e dns.qry.name -Y "ip.dst_host==<IP_ADDRESS>" > <TXT_FILE>
# OR
tshark -r <PACKET_FILE> “dns.flags.response == 0"
```

<br>
   
<br>

Parse evtx files with [dumpevtx](https://github.com/Velocidex/evtx)
```bash
mkdir <OUT_DIR>
find '<EVTX_DIR>' -name "*.evtx" -size +69k -print0 | while read -d $'\0' file
do ./dumpevtx parse "${file}" --output="${file}.txt" 2>/dev/null
	mv "${file}.txt" output/
done
```