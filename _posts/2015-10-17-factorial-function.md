---
layout:     post
title:      "python阶乘小程序" 
subtitle:   "渣练手"
date:       2015-10-17 09:00:00
author:     "Cyzus"
header-img: "img/hello-world.jpg"
tag:
   - python
---



又来一波程序~~今天分享的是阶乘程序

## 阶乘 ##

这个程序的体验是这样的，要求用户输入一个正整数，比如说输入“5”，程序便会输出120，是由1 * 2 * 3 * 4 * 5得来的，阶乘是没有任何简便的公式的，那么要怎么做才能让python得出答案呢

### 思路 ###

既然没有公式，我们只能让python做暴力计算了，搞一个有限循环，循环次数就是输入的值。内容就是从1开始乘，每次循环都让乘数加1。于是有了思路就可以开始编程了

### 流程 ###

 1. 系统请求用户输入正整数
 2. 用户输入
 3. 系统确认输入数值是否有效（正整数），无效的话提示error
 4. 设定计算初始值为1
 5. 确认循环次数为用户输入数值
 6. 一次循环里的算法是：设定的初始值乘以已经循环的次数
 8. 循环完输出最终计算值
 9. 可选：永久循环，从头开始，要求用户输入正整数
 

### 参考 ###

>var = 1
while var ==1:
&#8195;&#8195;      num = input ("input a num:")
&#8195;&#8195;      if num%1 == 0:
&#8195;&#8195;  &#8195;&#8195;          cal = 1
&#8195;&#8195;  &#8195;&#8195;          for count in range(1,num+1):    
&#8195;&#8195;  &#8195;&#8195;  &#8195;&#8195;              cal = cal*count
&#8195;&#8195;  &#8195;&#8195;          print cal
&#8195;&#8195;        else:
> &#8195;&#8195;  &#8195;&#8195;         print "invalid number"

看完后是不是发现其实很简单？


欢迎大家评论！！