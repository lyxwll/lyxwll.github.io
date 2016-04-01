---
layout:     post
title:      "python解决一元二次方程" 
subtitle:   "渣练手"
date:       2015-10-19 09:00:00
author:     "Cyzus"
header-img: "img/hello-world.jpg"
tag:
   - python
---



*又来一波程序~~今天分享的是如何搞定一元二次方程*

## 新方法 ##

很多人反映我敲太多字，懂的实际上并没有多少，于是我决定把教程写在代码里了，不喜勿喷


### 参考 ###
> 
 #!usr/bin/env python  
 # -*- coding: utf-8 -*-  
  
>from __future__ import division #除法纠正  
>import math  
  
>def oneandtwo():  
&#8195;&#8195;     '''''判断方程的根；若方程有根，则将其解出来'''  
&#8195;&#8195;     delta=b**2-4*a*c #根的判别式  
&#8195;&#8195;     print u'判别式大小为：',delta  
    print  
&#8195;&#8195;     if delta<0:  
&#8195;&#8195;&#8195;&#8195;          print u'根的判别式小于0，方程无解！'  
&#8195;&#8195;    else:  
&#8195;&#8195;         x1=(-b+math.sqrt(delta))/(2*a) #第一个根  
&#8195;&#8195;         x2=(-b-math.sqrt(delta))/(2*a) #第二个根  
&#8195;&#8195; &#8195;&#8195;         print u'方程的两根是:\n\nx1=%f\nx2=%f'%(x1,x2)  
&#8195;&#8195; &#8195;&#8195;         print  
  
>if __name__=='__main__':  
&#8195;&#8195;     print u'输入一元二次方程的系数（a,b,c）：'  
&#8195;&#8195;     print  
&#8195;&#8195;     stra=raw_input(u'请输入系数 a：')  
&#8195;&#8195;     strb=raw_input(u'请输入系数 b：')  
&#8195;&#8195;     strc=raw_input(u'请输入系数 c：')  
&#8195;&#8195;     print  
&#8195;&#8195;     print u'方程是：(%s)*x^2+(%s)*x+(%s)=0'%(stra,strb,strc)  
&#8195;&#8195;     print  
&#8195;&#8195;     #将输入的字符串转换为浮点数  
&#8195;&#8195;     a=float(stra)  
&#8195;&#8195;     b=float(strb)  
&#8195;&#8195;     c=float(strc)  
>&#8195;&#8195;     oneandtwo() #调用并打印出方程的两个根  

于是就这样吧