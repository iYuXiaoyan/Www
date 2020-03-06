---
layout: post
title: "Python 读取 txt 文档中特定字符串之间的字符串 "
date: 2019-03-06
categories: [blog]
header-img: ""
tags: [Python,txt,read,between characters ]
description: Python Read Data Between Characters In Txt
---

## 概述

找到了一种用  python 直接读取 txt 文件中特定字符串之间的字符串的方法。代码感觉冗余，方法有点笨，但是可以解决问题，先用起来。

## 缘起

我出具 CTD 压力传感器的校准证书，原始数据的获得项目中有一项是被校仪器的“系数”，通常在我们原始的文件夹下将仪器自身的系数“刻”出来。我在早期版本的用于计算仪器 N 值的 PNvalue 软件中需要调用到PTCA0、PTCSB0、PTEMPA0等一系列的仪器自身的系数，让其参与后期的计算。但是最早的脚本文件中需要在 sheel 中手动粘贴一行用空格隔开的这一系列的系数，感觉不大方便。于是我想到了，如果能软件能够直接读取这些`PTCA0=`标记之后的这些数据，将这些数据作为函数的返回值，就可以直接别调用到我的核心函数中进行计算了。

于是，核心的问题在于，如何读取这个 txt 文本文件中特殊标记的字符串之间的数据。经过一番检索之后，发现了下面的这种方法可以满足我的要求。

## 正文

### 待处理 txt 文件例子

下面这些内容是存放在一个叫做“xs.txt”的文件夹下。这是一台非常老的 SBE37-SM，它的压力数据格式不是很具有代表性，比如后期的新产品中这些字段已经发生了变化，例如PTCSB0不存在了，换成了“PTEMPA0”等。但是方法是一样的，只要将相关的字段进行替换即可满足我们的需要。

```
dc
SBE37-SM V 2.6b  5500
temperature:  12-feb-08
    TA0 = -2.913355e-05
    TA1 = 2.813583e-04
    TA2 = -2.823956e-06
    TA3 = 1.618099e-07
conductivity:  17-jun-16
    G = -1.011881e+00
    H = 1.414795e-01
    I = -2.204936e-04
    J = 3.629065e-05
    CPCOR = -9.570000e-08
    CTCOR = 3.250000e-06
    WBOTC = 4.026385e-05
pressure S/N 2391910, range = 508 psia:  05-oct-07
    PA0 = 4.012457e-01
    PA1 = 2.399009e-02
    PA2 = 1.583314e-09
    PTCA0 = 5.330795e+01
    PTCA1 = 4.757130e-01
    PTCA2 = -1.207956e-02
    PTCSB0 = 2.582450e+01
    PTCSB1 = 5.000000e-04
    PTCSB2 = 0.000000e+00
    POFFSET = 0.000000e+00
rtc:  12-feb-08 
    RTCA0 = 9.999963e-01
    RTCA1 = 1.463308e-06
    RTCA2 = -2.925257e-08
S>
```

### 程序代码

```
import re
#文本所在TXT文件#获得 xs.txt 中的参数。
file = 'xs.txt'
f = open(file, 'r')
buff = f.read()
#关键字1,2(修改引号间的内容)
Mark_SN1 = 'pressure S/N '#获得 SN
Mark_SN2 = ', range'

Mark_range1 = 'range = '#获得 range
Mark_range2 = ' psia'

Mark_PA0_1 = 'PA0 = '  # 获得 PA0
Mark_PA0_2= ' '

Mark_PA1_1 = 'PA1 = '  # 获得 PA1
Mark_PA1_2 = ' '

Mark_PA2_1 = 'PA2 = '  # 获得 PA2
Mark_PA2_2 = ' '

Mark_PTCA0_1 = 'PTCA0 = '  # 获得PTCA0
Mark_PTCA0_2 = ' '

Mark_PTCA1_1 = 'PTCA1 = '  # 获得PTCA 1
Mark_PTCA1_2 = ' '

Mark_PTCA2_1 = 'PTCA2 = '  # 获得PTCA 2
Mark_PTCA2_2 = ' '


Mark_PTCSB0_1 = 'PTCSB0 = '  # 获得PTCSB0
Mark_PTCSB0_2 = ' '

Mark_PTCSB1_1 = 'PTCSB1 = '  # 获得PTCSB1
Mark_PTCSB1_2 = ' '


Mark_PTCSB2_1 = 'PTCSB2 = '  # 获得PTCSB2
Mark_PTCSB2_2 = ' '

Mark_POFFSET_1 = 'POFFSET = '  # 获得POFFSET
Mark_POFFSET_2 = ' '

Mark_RTCA0_1 = 'RTCA0 = '  # 获得RTCA0
Mark_RTCA0_2 = ' '


Mark_RTCA1_1 = 'RTCA1 = '  # 获得RTCA1
Mark_RTCA1_2 = ' '

Mark_RTCA2_1 = 'RTCA1 = '   # 获得RTCA2#?å
Mark_RTCA2_2 = ' '

#清除换行符,请取消下一行注释

#buff = buff.replace('\n','')
pat_SN = re.compile(Mark_SN1+'(.*?)'+Mark_SN2, re.S)
pat_range = re.compile(Mark_range1+'(.*?)'+Mark_range2, re.S)
pat_PA0 = re.compile(Mark_PA0_1+'(.*?)'+Mark_PA0_2, re.S)
pat_PA1 = re.compile(Mark_PA1_1+'(.*?)'+Mark_PA1_2, re.S)
pat_PA2 = re.compile(Mark_PA2_1+'(.*?)'+Mark_PA2_2, re.S)

pat_PTCA0 = re.compile(Mark_PTCA0_1+'(.*?)'+Mark_PTCA0_2, re.S)
pat_PTCA1 = re.compile(Mark_PTCA1_1+'(.*?)'+Mark_PTCA1_2, re.S)
pat_PTCA2 = re.compile(Mark_PTCA2_1+'(.*?)'+Mark_PTCA2_2, re.S)

pat_PTCSB0 = re.compile(Mark_PTCSB0_1+'(.*?)'+Mark_PTCSB0_2, re.S)
pat_PTCSB1 = re.compile(Mark_PTCSB1_1+'(.*?)'+Mark_PTCSB1_2, re.S)
pat_PTCSB2 = re.compile(Mark_PTCSB2_1+'(.*?)'+Mark_PTCSB2_2, re.S)

pat_POFFSET = re.compile(Mark_POFFSET_1+'(.*?)'+Mark_POFFSET_2, re.S)

pat_RTCA0 = re.compile(Mark_RTCA0_1+'(.*?)'+Mark_RTCA0_2, re.S)
pat_RTCA1 = re.compile(Mark_RTCA1_1+'(.*?)'+Mark_RTCA1_2, re.S)

pat_RTCA2 = re.compile(Mark_RTCA2_1+'(.*?)'+Mark_RTCA2_2, re.S)#?

result_SN = pat_SN.findall(buff)
result_range = pat_range.findall(buff)
result_PA0 = pat_PA0.findall(buff)
result_PA1 = pat_PA1.findall(buff)
result_PA2 = pat_PA2.findall(buff)
result_PTCA0 = pat_PTCA0.findall(buff)
result_PTCA1 = pat_PTCA1.findall(buff)
result_PTCA2 = pat_PTCA2.findall(buff)
result_PTCSB0 = pat_PTCSB0.findall(buff)
result_PTCSB1 = pat_PTCSB1.findall(buff)
result_PTCSB2 = pat_PTCSB2.findall(buff)
result_POFFSET = pat_POFFSET.findall(buff)
result_RTCA0 = pat_RTCA0.findall(buff)
result_RTCA1 = pat_RTCA1.findall(buff)
result_RTCA2 = pat_RTCA2.findall(buff)

SN = result_SN[0]
rangeNO = result_range[0]
PA0 = float(result_PA0[0])
PA1 = float(result_PA1[0])
PA2 = float(result_PA2[0])
PTCA0 = float(result_PTCA0[0])
PTCA1 = float(result_PTCA1[0])
PTCA2 = float(result_PTCA2[0])

PTCSB0 = float(result_PTCSB0[0])
PTCSB1 = float(result_PTCSB1[0])
PTCSB2 = float(result_PTCSB2[0])
POFFSET = result_POFFSET[0]

RTCA0 = float(result_RTCA0[0])
RTCA1 = float(result_RTCA1[0])
RTCA2 = float(result_RTCA2[0])

print('SN 为:',SN)
print('range 为:', rangeNO)
print('PA0 为:', PA0)
print('PA1 为:', PA1)
print('PA2 为:', PA2)
print('PTCA0 为:', PTCA0)
print('PTCA1 为:', PTCA1)
print('PTCA2 为:', PTCA2)

print('PTCSB0 为:', PTCSB0)
print('PTCSB1 为:', PTCSB1)
print('PTCSB2为:', PTCSB2)

print('POFFSET 为:', POFFSET)

print('RTCA0  为:', RTCA0)
print('RTCA1  为:', RTCA1)
print('RTCA2  为:', RTCA2)
# ChangeLog
# 2020-03-06 小焱创建。
```

### 程序运行后

```
SN 为: 2391910
range 为: 508
PA0 为: 0.4012457
PA1 为: 0.02399009
PA2 为: 1.583314e-09
PTCA0 为: 53.30795
PTCA1 为: 0.475713
PTCA2 为: -0.01207956
PTCSB0 为: 25.8245
PTCSB1 为: 0.0005
PTCSB2为: 0.0
POFFSET 为: 0.000000e+00
rtc:
RTCA0  为: 0.9999963
RTCA1  为: 1.463308e-06
RTCA2  为: 1.463308e-06
```

## 结论

-   该方法可以完成文本文件中特定字符之间的数据提取。
-   该方法感觉比较笨，我是直接套用了提取少量关键词的方法，来干了一件提取大量关键词的工作，后面有点复制粘贴的意思。理论上应该有比这个更高明的方法。
-   代码中虽然最后是以 print 的形式打印出来，实际上将上述代码封装到一个函数中，返回多个参数，然后调用这个函数的时候直接返回你要的关键词，这样的用法才是优雅的。

## Ref

-   [Python3 获取一大段文本之间两个关键字之间的内容方法](https://www.jb51.net/article/148660.htm)
-   [python多进程提取处理大量文本的关键词方法](https://www.jb51.net/article/148660.htmhttps://www.jb51.net/article/141528.htm)
-   [Python文本处理简单易懂方法解析](https://www.jb51.net/article/176720.htm)

## ChangeLog

2020-03-06 小焱创建。