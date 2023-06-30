---
title: conda env下没有python
abbrlink: 7e7d79c3
date: 2023-06-28 13:32:23
tags:
---
一般用conda新建一个环境是这样的：
`conda create -n your_env`
那这个就不包含解释器
得这么整
`conda create -n your_env python=3.9`
那已经安装了一个空的咋办：
`conda install -n your_env python`

ps: `-n` 是 `--name`的缩写
