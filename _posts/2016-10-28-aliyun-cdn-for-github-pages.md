---
layout: post
title: "用阿里云CDN“加速” Github Pages"
categories: 折腾
tags:
---
## 配置过程

初始状态：imrickysu.github.io已经和blog.rickysu.com绑定

1. 开通阿里云CDN
2. 开通阿里云OSS
3. OSS控制台：一键快速添加CDN加速
  - Bucket名字：随意
  - 要加速的域名：blogcdn.rickysu.com
4. OSS控制台：Bucket属性
  - 静态网站->默认首页:index.html (否则显示you’re not the owner of this bucket)
  - 回源设置 ->添加规则: 镜像 imrickysu.github.io

## 性能结果

多访问两次后，首页2秒加载完毕，但比较后结果让我跌眼镜：

即使load多次了，blogcdn.rickysu.com需要2.34s load完所有内容，而原始的blog.rickysu.com只需要561ms。

## 碰到过的问题

1. 如果只开通CDN: cdn.rickysu.com，CDN回源无论设置为blog.rickysu.com, 还是imrickysu.github.com，访问cdn.rickysu.com的时候都会显示404，而且默认404是个空白页面，我是将404设置改为公益404后才发现。
2. OSS Bucket 一定要设置默认首页，否则显示 you’re not the owner of this bucket
3. OSS Bucket 镜像一定要写 github.io 的地址。如果写 blog.rickysu.com 就返回 502.


