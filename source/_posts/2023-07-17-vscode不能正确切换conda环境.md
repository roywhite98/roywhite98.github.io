---
title: vscode不能正确切换conda环境
date: 2023-07-17 00:30:22
tags:
- 工欲善其事
---
vscode有个插件叫code runner，非常好看，比控制台直接输出好看多了。
控制台嘛就直接conda activate进去就好，虽然我的默认控制台是powershell进不去会报错，但是只要切换称cmd控制台就没什么问题了。
code runner死都切换不了，怎么处理呢，很简单，
在cmd中先进入目标conda环境，然后用命令启动：`code .`
这样就能运行了。