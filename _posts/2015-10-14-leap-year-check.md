---
layout:     post
title:      "闰年识别系统" 
subtitle:   "渣练手"
date:       2015-10-14 09:00:00
author:     "Cyzus"
header-img: "img/hello-world.jpg"
tag:
   - python
---



今天带来了一个小程序——闰年识别



### 原理 ###


我们都知道闰年的机制是“四年一闰，百年不闰，四百年一闰”，所以小程序如下所示：

>year = input ("pleaz input year:" )
if (year % 100 == 0) and (year % 400 == 0) or (year % 100 == 1) and (year % 4 == 0):
&#8195;&#8195;print ("this is a leap year")
else:
>&#8195;&#8195;print ("this isn't a leap year")

### 包装 ###

加上包装

>var = 1
while var == 1 :
&#8195;&#8195;    year = input ("pleaz input year:" )
&#8195;&#8195;    if (year%100 == 0) and (year%400 == 0) or (year%100 == 1) and (year%4 == 0):
&#8195;&#8195;&#8195;&#8195;        print ("this is a leap year")
&#8195;&#8195;    else:
&#8195;&#8195;&#8195;&#8195;        print ("this isn't a leap year")
        import time
        for a in range (1,4):
            time.sleep (0.2)
            print "..."
 >           time.sleep (0.2)

