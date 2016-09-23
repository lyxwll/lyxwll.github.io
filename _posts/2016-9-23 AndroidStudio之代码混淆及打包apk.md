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
参数 | 解释
------------ | -------------
-optimizationpasses 5  | # 指定代码的压缩级别            
-dontusemixedcaseclassnames  | # 是否使用大小写混合
-dontskipnonpubliclibraryclasses | # 是否混淆第三方jar
-dontpreverify         | # 混淆时是否做预校验
-verbose               | # 混淆时是否记录日志
-optimizations !code/simplification/arithmetic,!field/*,!class/merging/*  | # 混淆时所采用的算法
-keep public class * extends android.app.Activity   | # 保持哪些类不被混淆
-keep public class * extends android.app.Application  |  # 保持哪些类不被混淆
-keep public class * extends android.app.Service     | # 保持哪些类不被混淆
-keep public class * extends android.content.BroadcastReceiver  | # 保持哪些类不被混淆
-keep public class * extends android.content.ContentProvider  |  # 保持哪些类不被混淆
-keep public class * extends android.app.backup.BackupAgentHelper |  # 保持哪些类不被混淆
-keep public class * extends android.preference.Preference   | # 保持哪些类不被混淆
-keep public class com.android.vending.licensing.ILicensingService  |  # 保持哪些类不被混淆

```Java
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























