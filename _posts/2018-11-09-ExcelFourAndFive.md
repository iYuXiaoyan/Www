---
layout: post
title: Excel四舍六入五成双问题解决方案
date: 2018-11-09
categories: blog
tags: excel,四舍六入,解决方案,最佳实践
description: Excel四舍六入五成双问题解决方案
---


## 背景介绍

搞计量工作的人都知道：在计量领域里，数字修约规则不是通常认为的“四舍五入”，而是“四舍六入五考虑”（俗称—四舍六入五成双）。但是在微软出的excel表格软件中默认的修约函数是ROUND函数，其默认的修约规则是四舍五入。这样造成的后果就会造成我们在计算示指和标准值的差的时候，会经常造成1位数的差异。这个问题怎么解决呢，笔者想到了一个解决方案，下面给大家介绍一下。

## 思路

建立一个自定义函数Round5函数，替代Round函数，一劳永逸解决这个问题。

## 1.编写一个Round5函数

首先，新建一个excel空表，点击“开发工具”—“Visual Basic”—“模块”—“模块1”中插入下列代码：

```
Public Function Round5(rng As Double, number As Integer) As Double

    Round5 = Round(rng, number)

End Function
```

点保存，并将这个文件保存为一个“四舍六入五成双模板.xlam”格式的文件（当然叫做Round5.xlam也很好）。当然，你可以保存在C盘根目录下，或者保存在目录“C:\Users\Administrator\AppData\Roaming\Microsoft\AddIns”下。当然，这个目录是根据你office软件安装的目录有所不同的，如果默认的话，就是这个位置了。

注意，这里建立了自定义函数之后，最关键的步骤就是保存成一个xlam格式的文件，否则这个函数以后无法调用到其他的exlcel工作表里。

## 2.加载Round5模块

新建立一个excel空表格，点击“开发工具”—“加载项”—选中你刚才做的xlam文件—点确定。

好了，从现在开始，你以后就可以在你这台电脑的任何一个打开的excel里，直接在excel表中直接调用Round5函数了。

## 3.加强版应用

大家都知道的ROUND函数有两个参数ROUND（参数1,参数2）。参数1是你要引用的哪个cell单元格（例如D6），参数2是一个小数位的保留位数。那么这里自定义的函数Round5也是有同样的参数。那么我们就想，在使用excel的时候小数位数可能根据我们的需要，现场决定是保留2位3位还是其他位数。这个问题怎么快速解决呢？

很简单，就是你定义一个单元格作为你保留位数的这个参数的存储位置，例如D6单元格。你在D5单元格里写上“保留位数”。在引用保留位数参数的时候，你就直接在第二个参数的位置上添上D6就好了。

当然我们还认为这样不够好，还要手动敲，如果点一下就解决了，多好啊。那么还有更进一步的玩法。

就是在D6的旁边增加一个小按钮。具体的方法是：开发工具—插入—表单控件—找到那个上下的小箭头，拉到D6的旁边。右键选中这个小控件，点设置控件格式，单元格链接，电导您的D6单元格上。好了，试试吧。

## ChangeLog

- 2018-11-09 下午小焱创建。
- 2018-11-30 增加了抬头，修改了几个错别字。