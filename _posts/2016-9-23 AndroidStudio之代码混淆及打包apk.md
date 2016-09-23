##AndroidStudio之代码混淆及打包apk                 

####反编译APK     
如何反编译apk文件擦查看源码呢？再此，给大家推荐两篇博客，很精简很易懂[《android代码混淆-原来如此简单》](http://www.cnblogs.com/classic/archive/2011/04/27/2030234.html)和 [《Android APK反编译就这么简单 详解》](http://blog.csdn.net/vipzjyno1/article/details/21039349)；             

####代码混淆   

首先，在你的工程目录下，找到**proguard-rules.pro**文件，它就是你要进行编写混淆配置的文件：        
![img](/img/2016-9-23/001.png)                 

光编写该文件还不够哦，你还需要在你**module**的**build.gradle**文件中引用该混淆文件：             
![img](/img/2016-9-23/002.png)                      

好了，知道在哪配置混淆文件后，下面开始讲讲如何配置混淆：           

混淆文件 proguard-rules.pro 参数详解          

```java    
-optimizationpasses 5                                                           # 指定代码的压缩级别
-dontusemixedcaseclassnames                                                     # 是否使用大小写混合
-dontskipnonpubliclibraryclasses                                                # 是否混淆第三方jar
-dontpreverify                                                                  # 混淆时是否做预校验
-verbose                                                                        # 混淆时是否记录日志
-optimizations !code/simplification/arithmetic,!field/*,!class/merging/*        # 混淆时所采用的算法

-keep public class * extends android.app.Activity                               # 保持哪些类不被混淆
-keep public class * extends android.app.Application                            # 保持哪些类不被混淆
-keep public class * extends android.app.Service                                # 保持哪些类不被混淆
-keep public class * extends android.content.BroadcastReceiver                  # 保持哪些类不被混淆
-keep public class * extends android.content.ContentProvider                    # 保持哪些类不被混淆
-keep public class * extends android.app.backup.BackupAgentHelper               # 保持哪些类不被混淆
-keep public class * extends android.preference.Preference                      # 保持哪些类不被混淆
-keep public class com.android.vending.licensing.ILicensingService              # 保持哪些类不被混淆

-keepclasseswithmembernames class * {                                           # 保持 native 方法不被混淆
    native <methods>;
}

-keepclasseswithmembers class * {                                               # 保持自定义控件类不被混淆
    public <init>(android.content.Context, android.util.AttributeSet);
}

-keepclasseswithmembers class * {
    public <init>(android.content.Context, android.util.AttributeSet, int);     # 保持自定义控件类不被混淆
}

-keepclassmembers class * extends android.app.Activity {                        # 保持自定义控件类不被混淆
   public void *(android.view.View);
}

-keepclassmembers enum * {                                                      # 保持枚举 enum 类不被混淆
    public static **[] values();
    public static ** valueOf(java.lang.String);
}

-keep class * implements android.os.Parcelable {                                # 保持 Parcelable 不被混淆
  public static final android.os.Parcelable$Creator *;
}

-keep class MyClass;                                                            # 保持自己定义的类不被混淆
````

以上是最基础的配置，几乎每个项目都需要进行这些地方的混淆（或保持不混淆）。    
如果你仔细看过上方的注释，就会了解一些基本代码混淆策略了。     
只是，这还远远不够，因为你在项目中，总会不可避免的引用第三方的library库或是jar包,那，如果你不能够正确的混淆第三方的资源，可能会导致你的应用无法使用。               
贴出我项目中关于第三方的混淆部分：               

```java              
#如果有引用v4包可以添加下面这行
-keep class android.support.v4.** { *; }
-keep public class * extends android.support.v4.**
-keep public class * extends android.app.Fragment

#如果引用了v4或者v7包，可以忽略警告，因为用不到android.support
-dontwarn android.support.**

#保持自定义组件不被混淆
-keep public class * extends android.view.View {
    public <init>(android.content.Context);
    public <init>(android.content.Context, android.util.AttributeSet);
    public <init>(android.content.Context, android.util.AttributeSet, int);
    public void set*(...);
}

#保持 Serializable 不被混淆
-keepnames class * implements java.io.Serializable
 
#保持 Serializable 不被混淆并且enum 类也不被混淆
-keepclassmembers class * implements java.io.Serializable {
    static final long serialVersionUID;
    private static final java.io.ObjectStreamField[] serialPersistentFields;
    private void writeObject(java.io.ObjectOutputStream);
    private void readObject(java.io.ObjectInputStream);
    java.lang.Object writeReplace();
    java.lang.Object readResolve();
}
 
#保持枚举 enum 类不被混淆      
如果混淆报错，建议直接使用上面的-keepclassmembers class * implements java.io.Serializable即可             
-keepclassmembers enum * {
  public static **[] values();
 public static ** valueOf(java.lang.String);
}
 
-keepclassmembers class * {
    public void *ButtonClicked(android.view.View);
}
 
#不混淆资源类
#-keepclassmembers class **.R$* {
#    public static <fields>;
#}

#xUtils(保持注解，及使用注解的Activity不被混淆，不然会影响Activity中你使用注解相关的代码无法使用) 
-keep class * extends java.lang.annotation.Annotation {*;}
-keep class com.otb.designerassist.activity.** {*;}

#自己项目特殊处理代码（这些地方我使用了Gson类库和注解，所以不希望被混淆，以免影响程序）
-keep class com.otb.designerassist.entity.** {*;}
-keep class com.otb.designerassist.http.rspdata.** {*;}
-keep class com.otb.designerassist.service.** {*;}

##混淆保护自己项目的部分代码以及引用的第三方jar包library（想混淆去掉"#"）
#-libraryjars libs/umeng-analytics-v5.2.4.jar
#-libraryjars libs/alipaysecsdk.jar
#-libraryjars libs/alipayutdid.jar
#-libraryjars libs/weibosdkcore.jar 

# 以libaray的形式引用的图片加载框架,不想混淆（注意，此处不是jar包形式，想混淆去掉"#"）
#-keep class com.nostra13.universalimageloader.** { *; }

###-------- Gson 相关的混淆配置--------
-keepattributes Signature
-keepattributes *Annotation*
-keep class sun.misc.Unsafe { *; }

###-------- pulltorefresh 相关的混淆配置---------
-dontwarn com.handmark.pulltorefresh.library.**
-keep class com.handmark.pulltorefresh.library.** { *;}
-dontwarn com.handmark.pulltorefresh.library.extras.**
-keep class com.handmark.pulltorefresh.library.extras.** { *;}
-dontwarn com.handmark.pulltorefresh.library.internal.**
-keep class com.handmark.pulltorefresh.library.internal.** { *;}

###---------  reservoir 相关的混淆配置-------
-keep class com.anupcowkur.reservoir.** { *;}

###-------- ShareSDK 相关的混淆配置---------
-keep class cn.sharesdk.** { *; }
-keep class com.sina.sso.** { *; }

###--------------umeng 相关的混淆配置-----------
-keep class com.umeng.** { *; }
-keep class com.umeng.analytics.** { *; }
-keep class com.umeng.common.** { *; }
-keep class com.umeng.newxp.** { *; }

###-----------MPAndroidChart图库相关的混淆配置------------
-keep class com.github.mikephil.charting.** { *; }
````                   
以上的配置，即是对一个项目的混淆配置了，相对比较完整，大家可以依葫芦画瓢，写更多的配置，对于一些第三方项目的使用，一般官方会给出如何配置混淆，大家需要小心，别忘了配置。     

好啦，如果你已经写好自己的混淆配置文件，不要忘了在build.gradle文件中再次配置下，打开混淆文件：   

```Java            
buildTypes {
        debug {
            // 显示Log
            buildConfigField "boolean", "LOG_DEBUG", "true"


            versionNameSuffix "-debug"
            minifyEnabled false
            zipAlignEnabled false
            shrinkResources false
            signingConfig signingConfigs.assist
        }

        release {
            // 不显示Log
            buildConfigField "boolean", "LOG_DEBUG", "false"

            //混淆
            minifyEnabled true

            //Zipalign优化
            zipAlignEnabled true

            // 移除无用的resource文件
            shrinkResources true
            //加载默认混淆配置文件
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
            //签名
            signingConfig signingConfigs.<span style="font-family: Arial, Helvetica, sans-serif;">assist</span>
        }
    }
````

- **release**节点下，**minifyEnabled**设置为**true**。

####导出APK　　　　

 学会了如何混淆你的项目代码之后，接下来，我们看下，如何使用Android Studio导出APK文件吧。
（1）Android Studio菜单Build->Generate Signed APK 　　　　　　　　　　　
![img](/img/2016-9-23/003.png)      

（2）弹出签名选择、创建窗口        
![img](/img/2016-9-23/004.png)      

（3）创建密钥库及密钥，创建后会自动选择刚创建的密钥库和密钥（已拥有密钥库跳过）     
    点击**“Create new...”**按钮创建密钥库              
![img](/img/2016-9-23/005.png)            

**Key store path**：密钥库文件的地址                
**Password/Confirm**：密钥库的密码              
**Alias**：密钥名称              
**Password/Confirm**：密钥密码           
**Validity(years)**：密钥有效时间              
**First and Last Name**：密钥颁发者姓名             
**Organizational Unit**：密钥颁发组织              
**City or Locality**：城市           
**Country Code(XX)**：国家          

（4）选择已存在密钥库及密钥（在（3）中创建密钥库后跳过此步骤）            
    点击**“Choose existing...”**按钮找到密钥库文件     
    **Key store password**输入已选择的密钥库文件的密码     
    点击**Key alias**后的“...”按钮，选择或者创建一个密钥        
![img](/img/2016-9-23/006.png)

（5）点击“Next”按钮，选择保存路径后，点击“Finish”按钮完成              
![img](/img/2016-9-23/007.png)














