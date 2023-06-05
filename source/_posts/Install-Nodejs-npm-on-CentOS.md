---
title: Install Nodejs & npm on CentOS
date: 2023-06-04 19:45:06
tags: 
- 气宗
- 工欲善其事
---
<!--more-->
要用jupyter插件离不开JavaScript。
那要用JS就得装Node.js和npm。
那装吧。
```
wget https://npmmirror.com/mirrors/node/v18.16.0/node-v18.16.0-linux-x64.tar.xz
tar -xvf node-v18.16.0-linux-x64.tar.gz
```
装在`root/Downloads/`目录下面。
然后cd到`usr/bin/`下，加个软链。
```
sudo ln -s /root/Downloads/node-v18.16.0-linux-x64/bin/node node
```
然后我们来node一下，哦豁，报错了。
```shell
[root@primary bin]# ./npm
node: /lib64/libm.so.6: version `GLIBC_2.27' not found (required by node)
```
得，GLIBC版本低，更新。参考https://www.cnblogs.com/dingshaohua/p/17103654.html
丁少华dalao的解决方案

```
wget http://ftp.gnu.org/gnu/glibc/glibc-2.28.tar.gz
tar xf glibc-2.28.tar.gz 
cd glibc-2.28/ && mkdir build  && cd build
../configure --prefix=/usr --disable-profile --enable-add-ons --with-headers=/usr/include --with-binutils=/usr/bin
```
报错，更新make和gcc
```
# 升级GCC(默认为4 升级为8)
yum install -y centos-release-scl
yum install -y devtoolset-8-gcc*
mv /usr/bin/gcc /usr/bin/gcc-4.8.5
ln -s /opt/rh/devtoolset-8/root/bin/gcc /usr/bin/gcc
mv /usr/bin/g++ /usr/bin/g++-4.8.5
ln -s /opt/rh/devtoolset-8/root/bin/g++ /usr/bin/g++

# 升级 make(默认为3 升级为4)
wget http://ftp.gnu.org/gnu/make/make-4.3.tar.gz
tar -xzvf make-4.3.tar.gz && cd make-4.3/
./configure  --prefix=/usr/local/make
make && make install
cd /usr/bin/ && mv make make.bak
ln -sv /usr/local/make/bin/make /usr/bin/make
```
好，继续报错。
```
LD_LIBRARY_PATH shouldn't contain the current directory
```
问题不大，我们把这个变量删了。
先看一眼变量长啥样，copy下来以便恢复。
```
echo $LD_LIBRARY_PATH # copy this path
LD_LIBRARY_PATH=
```
然后回过头去编译glibc。编译通过，`make && make install`安装 重新添加LD_LIBRARY_PATH。
```
vim /etc/profile
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH[刚复制的路径]

source /etc/profile
```
有个要点，千万不要加空格。不然一会儿就`ls`都用不了了，系统会崩。会 段错误(吐核)。


**PS: 简单起见，`conda install nodejs`解决一切问题。（笑**
