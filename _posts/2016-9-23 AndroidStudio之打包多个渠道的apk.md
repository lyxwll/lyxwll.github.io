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

####在工程的build.gradle文件中配置     

```Java    
android {  
    signingConfigs {  
        designerassist {  
            keyAlias 'designerassist.keystore'  
            keyPassword 'otb2015'  
            storeFile file('E:/workspace/otb/designerhelper/designerassist.keystore')  
            storePassword 'otb2015'  
        }  
    }  
    compileSdkVersion 19  
    buildToolsVersion '22.0.1'  
  
    productFlavors {  
        wandoujia {}  
        baidu {}  
        c360 {}  
        uc {}  
        qq {}  
        xiaomi {}  
        meizu {}  
        c91 {}  
        huawei {}  
        lenovo {}  
        wangyi {}  
        yidong {}  
        mgyapp {}  
        anzhuoapk {}  
        tianyi {}  
        appchina {}  
        nduoa {}  
        umeng {}  
  
        productFlavors.all { flavor ->  
            flavor.manifestPlaceholders = [UMENG_CHANNEL_VALUE: name]  
        }  
    }  
`````

**说明：**     
其中name的值对相对应各个productFlavors的选项值，这样就达到自动替换渠道值的目的了。       
这样生成apk时，选择相应的Flavors来生成指定渠道的包就可以了，而且生成的apk会自动帮你加上相应渠道的后缀，非常方便和直观。大家可以自己反编译验证。      
你只需要按照上面的配置写就好了，当然，是根据你的需要选择不同的平台。    

**打包：**    
首先，你需要先配置下gradle环境：       
在系统变量里添加两个环境变量：    
> 1.1 变量名为：GRADLE_HOME，变量值就为gradle的根目录；所以变量值为：C:\Users\ningshuai\.gradle\wrapper\dists\gradle-2.2.1-all\c64ydeuardnfqctvr1gm30w53      

> 1.2 在系统变量里PATH里面添加gradle的bin目录;值为：C:\Users\ningshuai\.gradle\wrapper\dists\gradle-2.2.1-all\c64ydeuardnfqctvr1gm30w53\gradle-2.2.1\bin      
  
 配置完变量后，便可以打包了，打开命令行，切换到你的项目目录下，你会发现自己的目录中有**graldew.bat**这个文件：     
 
 ![img](/img/2016-9-23/008.png)     
 
 接下来，你就可以直接输入命令：**gradle assembleRelease**，就可以一次性生成所有的渠道包了：   
 
![img](/img/2016-9-23/009.png)      

所有生成的apk在项目的build\outputs\apk下：      

![img](/img/2016-9-23/010.png)          

如果只是想生成单个渠道的包呢？可以用命令行单独生成，比如：    
**gradle assembleWandoujiaRelease**          
当然，除此之外，你还可以直接通过Android studio导出相应平台的apk文件：    

![img](/img/2016-9-23/011.png)









