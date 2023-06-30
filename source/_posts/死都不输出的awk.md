---
title: '= =|||死都不输出的awk'
tags: 气宗
abbrlink: 12b473ed
date: 2023-06-04 19:48:23
---
<!--more-->

在用JupyterLab做查字典的时候，发现死都不输出，给ChatGPT验代码能通过，跑demo能通过。
```
awk 'NR==FNR{a[$3]=$0;next} NR>FNR{if($1 in a) print a[$1]}' file1 file2 > file3
```
但就是死都不输出，挨个换输入文件发现问题出在字典里。
字典是直接从电脑通过JupyterLab拷贝过去的。可能出了和^M那个一样的莫名奇妙的问题。所以手动复制一个副本，愉快跑通。