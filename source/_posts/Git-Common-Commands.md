---
title: Git常用命令
date: 2023-05-16 23:00:42
tags:
  - [Git]
categories:
  - [命令\操作手册]
description: 本文章记录在使用Git过程中常用到的一些命令
---

## 初始化本地仓库并推送到远程仓库

```
git init //初始化git仓库
git remote add origin [xxx.git] //链接到远程仓库
git push -u origin master //推送到远程仓库
```

注意：此方法需要在Github中将默认main分支修改为master分支



## 解决从远程仓库获取最新代码时发生版本冲突的问题

```
git remote -v  //查询当前远程的版本
git fetch origin master //获取远端的origin/master分支
git log -p master..origin/master //查看本地分支与远端的origin/master的版本差异
git merge origin/master //合并远端分支origin/master到当前分支
```



## 解决将本地仓库推送到远程仓库时发生版本冲突的问题

```
git pull --rebase origin master	//将远程库中的更新合并到本地库中
git push origin master	//推送至远程仓库
```



## 生成ssh-key

```
git config --global user.name "xxx"
git config --global user.email "xxx@xx.com"

ssh-keygen -t rsa -C "xxx@xx.com"
```

接下来将id_rsa.pub中的内容粘贴到github的SSH Keys中。
