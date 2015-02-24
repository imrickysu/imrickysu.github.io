---
layout: post
title:  "My Git Notes"
categories: 总结
tags:
- Git
---
这两周在和客户一起写一个SDK下的C程序。我们一起用Git协作得很欢乐。我一直都是Git小白，从前都是一个人用Git，用来记录版本更新，从来没有和别人协作过，这次算是体验到了Merge和Branch的乐趣。

很想在公司内部也推广Git，因此记录一些现在掌握的内容，作为一个草稿将来可以让不熟悉Git的人很容易用起来。

##Git能缓解什么痛苦

##Git结构

##Git基本用法
### 从远程全新下载Repo
git clone

### 本地新建Repo
git init

### 添加监视文件
git add

### 确认添加版本
git commit

### 切换版本
git branch

### 从远程下载更新
git pull

git fetch --all

### 将更新推送到远程
git push

### 配置参数
列出现在的全局参数 `git config -global -l`

设置名字 `git config --global user.name <username>`

设置Email `git config --global user.email <email>`

设置Proxy `git config --global http.proxy <http_proxy>:<port>`

取消某个参数 `git config --global --unset <param name>`

##工具
### SourceTree

### Git Bash

### Github

### BitBucket

## 协作的经验
