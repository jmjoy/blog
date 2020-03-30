---
title: "Linux命令: xargs"
date: 2020-03-30T19:05:20+08:00
description: ""
featured_image: ""
categories: "Linux"
tags: []
---

`xargs`是一个很好用的命令，常用于遍历上一个管道输出的内容然后执行命令。

比如（*这个博客主题有点问题，渲染下面的code失败，用图片代替*）：

![xargs command](/static/images/Linux命令-xargs/深度截图_选择区域_20200330200035.png)

比如这个命令就是遍历`kubectl get`根据label找到的Pod的名字，然后依次使用`kubectl exec`在Pod的container里面执行命令。

常用参数：

`-i`: 可以使用`{}`占位符来代表上一次遍历的项，而不是追加在最后面。

`-t`: 执行命令前先打印命令。

`-r`: 如果遍历内容为空，则不执行命令，防止报错。

