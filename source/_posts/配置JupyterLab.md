---
title: 配置JupyterLab
tags: 气宗
abbrlink: c7d42074
date: 2023-06-04 19:50:37
---
<!--more-->

嘛，要用服务器很麻烦的啦。
还得是JupyterLab。
我就在自己账户下配置了jupyterlab。轻松愉快。
1. 安装conda
自己百度，此处略。
2. 进入conda环境，安装Jupyter Lab
```
conda install -c conda-forge jupyterlab
```
之前用pip安装不是缺少这个包就是那个包，conda装挺好的。
3. 配置JupyterLab
设置密码，当然不设置也可以（笑
后面会说token登录
```
from jupyter_server.auth import passwd
passwd()
```
输入密码，然后verify，会生成一个加密的字符串。存一下。
之后生成配置文件。
```
jupyter lab --generate-config
```
会得到一个默认配置文件的位置，在隐藏文件夹`.jupyter/jupyter_lab_config.py`下面。打开它。里面有一万行注释。不管，直接加几行：
```
c.NotebookApp.ip = "*" # 允许所有ip访问
c.NotebookApp.open_browser = False # 不打开浏览器
c.NotebookApp.port = 8899 # 不用默认端口8888是美德
c.NotebookApp.allow_remote_access = True # 允许远程访问
c.NotebookApp.notebook_dir = '/home/username/jupyter_project' # 指定jupyter工作目录，我还没指定，据说不指定打开jupyter会404，但我没有404（笑
```
4. 启动jupyter
远端开一下
```
nohup jupyter lab &
```
在浏览器输入`[ip地址]:端口/lab`
回车就进了。
然后需要输入密码。如果设置了密码那就输入设置的密码，没设置那就会要token
那token嘛就这么看
```
jupyter lab list
```
会给一个网址，复制token填进去。

关掉就kill掉jupyter进程就好了。

