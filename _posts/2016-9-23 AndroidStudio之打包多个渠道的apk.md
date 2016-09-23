## AndroidStudio之打包多个发布渠道的apk文件         


####首先配置清单文件：AndroidMainFest.xml        

```Java   
<meta-data  
   android:name="UMENG_APPKEY"  
   android:value="您申请的key值" />     

<meta-data  
   android:name="UMENG_CHANNEL"  
   android:value="${UMENG_CHANNEL_VALUE}" />    
````


