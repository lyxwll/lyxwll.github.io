---    

layout:     post
title:      "Android Studio导入项目" 
subtitle:   " \"C'est la vie !\""
date:       2016-04-25 14:53:00
author:     "Wanglili"
header-img: "img/emily.jpg"

tag:
   - Android     

---   


#Android Studio导入项目     


**转载自：[http://ask.android-studio.org/?/article/21](http://ask.android-studio.org/?/article/21)**     


Android Studio默认使用 **Gradle** 构建项目， **Eclipse** 默认使用**Ant**构建项目。建议Android Studio导入项目时，使用 **Gradle** 构建项目。    


##导入 Eclipse 项目        
本例中，使用到的 Eclipse 项目结构如图：   
![img](/img/2016-4-25/001.png)  

> e-demo 为主项目， appcompat_v7 为 library 项目。    


**通过Generate Gradle build files 项目**     

Google官方建议是通过本方法进行Android Studio导入 Eclipse 项目。

这种方式有一个好处就是兼容 **Eclipse** 的文件目录结构，通过版本控制中的文件过滤，可以在一个项目组中，同时使用 **Eclipse** 和**Android Studio**。

###讲解1

**File --> Export**       
![img](/img/2016-4-25/002.png) 

###讲解2

选择导出类型。选择 **Android --> Generate Gradle build files** 。     
![img](/img/2016-4-25/003.png)    

点击 Next 。

###讲解3

很长一段英语（完全看不懂是什么意思）。    
![img](/img/2016-4-25/004.png)  

点击 Next 。

###讲解4

选择要导出的项目。      
![img](/img/2016-4-25/005.png)     

因为我的 e-demo 项目依赖了 appcompat_v7 项目，所以我将 e-demo 和 appcompat_v7 都选择了导出。

点击 **Next** 。

###讲解5

最终确认要导出的项目。     
![img](/img/2016-4-25/006.png) 

**Force overriding of existing files** 表示覆盖导出文件。使用 **Generate Gradle build files** 的方式导出项目，会在项目目录中生成一些文件。这里的覆盖文件指的就是覆盖这些可能已经生成过的文件。如果你之前有使用这种方式导出过项目，建议勾选。

点击 **Finish** 。

###讲解6

这一步没有什么好说的，直接点击 **Finish** 。        
![img](/img/2016-4-25/007.png)    

###讲解7

**Finish** 点击完毕，并没有弹出窗口显示导出的项目，就好像什么事情都没有做一样。其实，使用这个方式导出项目，是在项目中添加了一些文件，我们可以到项目目录下去看一看这些生成文件。

工作空间目录下：      
![img](/img/2016-4-25/008.png)    

e-demo 目录如下：     
![img](/img/2016-4-25/009.png)    

appcompat_v7 目录下：      
![img](/img/2016-4-25/010.png)

我们可以发现：在工作空间目录下，多出了 **gradle** 文件夹和 **build.gradle** 、 **build.gradle** 、 **gradlew** 、 **gradlew.bat** 、 **settings.gradle** 文件；在 e-demo 目录下多出了 **build.gradle** 文件； 在 appcompat_v7 目录下多出了 build.gradle 文件。这些文件和文件夹都和 Gradle 有关系，用于构建项目。这些文件以及文件夹的作用，我们以后再说。

###讲解8

由于 **Eclipse** 的 **ADT** 插件已经很久没有更新了，自动生成的 **Gradle** 编译设置已经跟不上Android Studio的更新速度，所以我们需要手动修改一些内容。

打开工作空间目录下的 gradle --> wrapper --> gradle-wrapper.properties 。修改一下内容： distributionUrl=http\://services.gradle.org/distributions/gradle-a.b.c-all.zip --> distributionUrl=https\://services.gradle.org/distributions/gradle-2.2.1-all.zip   

打开工作空间目录下的 **build.gradle** 文件。修改以下内容：

classpath 'com.android.tools.build:gradle:0.x.+' --> classpath 'com.android.tools.build:gradle:1.0.0' 。

之所以这么设置，是因为： **Eclipse** 导出的 **Gradle** 设置已经不是Android Studio 1.0 所支持的 **Gradle** 已及 **Gradle 插件**版本，需要手动更为支持的版本。否则轻则必须不能离线导入项目，重则项目导入失败。

###讲解9

打开Android Studio，选择 **Open an existing Android Studio project**。       
![img](/img/2016-4-25/011.png)

###讲解10

此时会弹出一个框，让你选择文件夹，这个时候需要注意的就是，你需要选择原来的 **Eclipse** 的工作空间目录，而不是 **e-demo** 目录。     
![img](/img/2016-4-25/012.png)   

点击 **OK** 。

###讲解11

设置导入选项。      
![img](/img/2016-4-25/013.png)   










