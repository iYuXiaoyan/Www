---
layout: post
title: "词频统计方法研究"
date: 2020-12-31
categories: [blog]
header-img: ""
tags: [词频,统计,excel,countif ]
description: 采用excel简单几步就可以将大量的数据（104万多行）进行统计，按照词频进行排序。
---

## 概述

采用excel简单几步就可以将大量的数据（104万多行）进行统计，按照词频进行排序。

## 源起

现在手里有一张excel表，一列数据里有很多种类的数据，其中有很多数据是重复的。现在，我想要知道有多少种不同的数据，而每种数据的数量是多少（词频）。如果能够解决这个问题，那么可以用社会工程学的技术来做各字典，来破解相关的密码，当然还可以有其他的作用，例如李笑来当年把很多年的卷子整理起来，然后把所有的单词搞出来，弄个词频分布。中文涉及到分词的问题，英文就好多了，每个单词是一个独立的意思。

## 正文

主要思路：从后往前说。想要获得词频多少，并且按照数量多少进行排序，那么先是要将重复的原始数据进行合并分类。分类好了之后，再用excel 的countif()函数来获得相应的数量。都弄完了之后进行排序，扩展排序。

具体的方法不再赘述，方法请见图。

![image.png](https://cdn.jsdelivr.net/gh/iyuxiaoyan/pic_bed/images/3785456-abcd0e51ec377467.png)

![image.png](https://cdn.jsdelivr.net/gh/iyuxiaoyan/pic_bed/images/3785456-55d0c74fd34e5607.png)

![image.png](https://cdn.jsdelivr.net/gh/iyuxiaoyan/pic_bed/images/3785456-93b79e2cfd447698.png)

![image.png](https://cdn.jsdelivr.net/gh/iyuxiaoyan/pic_bed/images/3785456-b38ca47b4896ed7d.png)

![image.png](https://cdn.jsdelivr.net/gh/iyuxiaoyan/pic_bed/images/3785456-05e51dfcf653573f.png)

![image.png](https://cdn.jsdelivr.net/gh/iyuxiaoyan/pic_bed/images/3785456-abdb39f8871af0a6.png)

![image.png](https://cdn.jsdelivr.net/gh/iyuxiaoyan/pic_bed/images/3785456-50a1122bc187ba69.png)

![image.png](https://cdn.jsdelivr.net/gh/iyuxiaoyan/pic_bed/images/3785456-38442c11e68ccc4f.png)

![image.png](https://cdn.jsdelivr.net/gh/iyuxiaoyan/pic_bed/images/3785456-9a23c577bbb3279d.png)

## 测试新图床

仔细研究了下文，得到了一个非常好的图床解决方案，太棒了！

在win10下调试通过。

-   [Github+jsDelivr+PicGo 打造稳定快速、高效免费图床](https://www.itrhx.com/2019/08/01/A27-image-hosting/)
-   [免费CDN：jsDelivr + Github](https://www.itrhx.com/2019/02/10/A18-free-cdn/)

## 图床继续测试

正确的引用方式应该是：https://cdn.jsdelivr.net/gh/iyuxiaoyan/pic_bed/images/3785456-05e51dfcf653573f.png

我的网页还是现实不出来，问题出在了哪里？

![image.png](https://cdn.jsdeliver.net/gh/iyuxiaoyan/pic_bed/images/3785456-05e51dfcf653573f.png)

明白了，应该是delivr我写成了deliver。

https://cdn.jsdelivr.net/gh/iyuxiaoyan/pic_bed/images/3785456-05e51dfcf653573f.png

测试：

![](https://cdn.jsdelivr.net/gh/iyuxiaoyan/pic_bed/images/3785456-05e51dfcf653573f.png)

以下测试使用gif图：

![img](https://cdn.jsdelivr.net/gh/iyuxiaoyan/pic_bed/images/20210106150357.gif)

## 后记

百度，别人说的不如我说的好，我觉得我讲的蛮清楚的。另外github的图床又被墙了，用简书的还是不错的，但愿长久能用（虽然一次贴一张，但是至少能用）。原图可以暂时贴到一个ppt里，然后贴简书上，最后再把地址贴到md文件里，就这样了。

## Ref

- 百度：关键词`excel 统计 频数`
- [Github+jsDelivr+PicGo 打造稳定快速、高效免费图床](https://www.itrhx.com/2019/08/01/A27-image-hosting/)
- [免费CDN：jsDelivr + Github](https://www.itrhx.com/2019/02/10/A18-free-cdn/)

## Log

- 2020-12-31 小焱创建。测试新图床通过。
- 2020-01-06  try gif.