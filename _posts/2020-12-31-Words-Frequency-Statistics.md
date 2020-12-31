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

![image.png](https://upload-images.jianshu.io/upload_images/3785456-abcd0e51ec377467.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![image.png](https://upload-images.jianshu.io/upload_images/3785456-55d0c74fd34e5607.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![image.png](https://upload-images.jianshu.io/upload_images/3785456-93b79e2cfd447698.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![image.png](https://upload-images.jianshu.io/upload_images/3785456-b38ca47b4896ed7d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![image.png](https://upload-images.jianshu.io/upload_images/3785456-05e51dfcf653573f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![image.png](https://upload-images.jianshu.io/upload_images/3785456-abdb39f8871af0a6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![image.png](https://upload-images.jianshu.io/upload_images/3785456-50a1122bc187ba69.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![image.png](https://upload-images.jianshu.io/upload_images/3785456-38442c11e68ccc4f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![image.png](https://upload-images.jianshu.io/upload_images/3785456-9a23c577bbb3279d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 后记

百度，别人说的不如我说的好，我觉得我讲的蛮清楚的。另外github的图床又被墙了，用简书的还是不错的，但愿长久能用（虽然一次贴一张，但是至少能用）。原图可以暂时贴到一个ppt里，然后贴简书上，最后再把地址贴到md文件里，就这样了。

## Ref

- 百度：关键词`excel 统计 频数`

## Log

2020-12-31 小焱创建。