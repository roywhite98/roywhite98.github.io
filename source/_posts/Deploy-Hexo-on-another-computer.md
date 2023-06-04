---
title: Deploy Hexo on another computer
date: 2023-06-04 18:41:37
tags: 气宗, 工欲善其事
---
在另一台电脑上部署一下Hexo。
利用git分支来同步hexo。
main branch放静态页面文件
hexo branch放源码

1. 设置hexo branch为default branch
2. 在老电脑上push源文件到hexo branch
3. 在新电脑上clone hexo branch到本地
4. 在新电脑上安装hexo环境
5. 在新电脑上推送源码到hexo branch，生成的静态页面仍推送到main branch，就是这么神奇
6. 使用git add . && git commit -m "message" && git push 更新源文件
7. 使用hexo clean && hexo g && hexo d推送静态到main
8. 然后报了个错，看了一下主题文件夹是空的，copy一下主题过来，hexo d，完成
9. 每次使用前pull一下以保证同步