---
layout: post
title: "用 python 怎样获得 txt 文件中的某一列数据"
categories: []
header-img: ""
tags: [Python,一列,txt ]
description: 
---

## 源起

无论是 SBE911-917 还是SBE37 来说，最后总归是要总结成 几列整齐的数据的。也就是说，是一个 M 行 N 列的矩阵，数据间用'空格'或者“,”等进行了分隔。而我们想要的就是提取某一列或某几列的数据，做成一个或者几个 List 或者其他适合的格式。随后呢，我们可以针对一列数据，根据其相互之间的差值关系，找到参考点之后取平均值和标准差，来找到这些数，取个平均值，最后做出 13~15 个行的一个 2~3 列的数据矩阵。这个数据矩阵，直接拷贝到飞飞的那个软件就直接出报告了。再就是，想着最高压力值，要取 10 个，计算不确定度的时候要用。



## 方法

### 示例代码如下

```
import codecs
 
f = codecs.open('data.txt', mode='r', encoding='utf-8') # 打开txt文件，以‘utf-8'编码读取
line = f.readline()  # 以行的形式进行读取文件
list1 = []
while line:
  a = line.split()
  b = a[2:3]  # 这是选取需要读取的位数
  list1.append(b) # 将其添加在列表之中
  line = f.readline()
f.close()
 
for i in list1:
  print(i)
```









## Ref

-   python读取txt文件并取其某一列数据的示例https://www.jb51.net/article/156557.htm
-   python 读取.csv文件数据到数组(矩阵)的实例讲解https://www.jb51.net/article/142047.htm
-   Python While 循环语句https://www.runoob.com/python/python-while-loop.html

## ChangeLog

-   2020-03-07 小焱创建。
-   