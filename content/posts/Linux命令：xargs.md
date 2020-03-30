---
title: "Linux命令：xargs"
date: 2020-03-30T19:05:20+08:00
description: ""
featured_image: ""
categories: "Linux"
tags: []
---


`xargs`是一个很好用的命令，常用于遍历上一个管道输出的内容然后执行命令。

比如：

```bash
kubectl get -n <NAMESPACE> pods -l role=<ROLE> -o go-template --template '{{range .items}}{{printf "%s\n" .metadata.name}}{{end}}' | xargs -i kubectl exec -n <NAMESPACE> -c <CONTAINER> {} -- bash -c 'echo hello world'
```

比如这个命令就是遍历`kubectl get`根据label找到的Pod的名字，然后依次使用`kubectl exec`在Pod的container里面执行命令。

常用参数：

`-i`: 可以使用`{}`占位符来代表上一次遍历的项，而不是追加在最后面。

`-t`: 执行命令前先打印命令。

`-r`: 如果遍历内容为空，则不执行命令，防止报错。
