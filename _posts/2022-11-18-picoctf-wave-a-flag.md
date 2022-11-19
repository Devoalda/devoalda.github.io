---
layout: post
title: PicoCTF - Wave a flag
date: '2022-10-12 10:37:00 +0800'
categories: [CTF, PicoCTF]
tags: [ctf,picoctf]     
author: dev1
math: true
---
# Description
Can you invoke help flags for a tool or binary? [This program](https://mercury.picoctf.net/static/1b1b6b2b4b3b4b3b4b3b4b3b4b3b4b3b/warm) has extraordinarily helpful information...

# Process
![Wave a flag](/assets/img/WaveAFlag.png){: width="972" height="589" }
_Hex Editor in VSCode_

The flag is found in the file, but it is not in plain sight. Using a hex editor, the flag can be found.
The word binary triggered me to use some sort of hex editor to view the file. I used VSCode to view the file, and found the flag.

# Flag
```
picoCTF{b1scu1ts_4nd_gr4vy_6635aa47}
```
{: file="flag.txt" }