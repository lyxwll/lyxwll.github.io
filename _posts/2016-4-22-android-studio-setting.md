---

layout:     post
title:      "Android Studio的基本设置" 
subtitle:   " \"C'est la vie !\""
date:       2016-04-22 14:50:00
author:     "Wanglili"
header-img: "img/ranger_rebecca.jpg"
tag:

   - AndroidStudio

---


**转载自:[http://stormzhang.com/devtools/2014/11/28/android-studio-tutorial2/](http://stormzhang.com/devtools/2014/11/28/android-studio-tutorial2/)**




## 项目结构 ##

当我们新建一个项目的目录结构默认是这样的:    
![img](/img/2016-4-22/026.png)

可以看到和Eclipse的目录结构有很大区别，Studio一个窗口只能有一个项目，而Eclipse则可以同时存在很多项目，如果你看着不习惯可以点击左上角进行切换。

![img](/img/2016-4-22/027.png)     

切换到“project”模式下的目录结构是这样的，我个人也更习惯这种格式。

![img](/img/2016-4-22/028.png)

和Eclipse的区别有如下：

- 1、Studio中有**Project** 和 **Module** 的概念，前面说到Studio中一个窗口只能有一个项目，即Project，代表一个workspace，但是一个Project可以包含多个Module，比如你项目引用的Android Library, Java Library等，这些都可以看做是一个Module;

- 2、上述目录中将java代码和资源文件（图片、布局文件等）全部归结为src，在src目录下有一个main的分组，同时划分出java和res两个文件夹，java文件夹则相当于Eclipse下的src文件夹，res目录结构则一样。    
 

##偏好设置    

进入后你也许发现字体大小或者样式不符合你的习惯，比如我是觉得代码太小看起来伤眼，**Darcular**主题默认的字体是12，我个人更习惯14的字体大小。没关系，到 **Preferences** (设置)页面搜索 **Font** 找到 **Colors&Fonts** 下的 **Font** 选项，我们可以看到默认字体大小是12，但是无法修改，需要先保存才可以修改，点击 **Save as...** 输入一个名字，比如 **MyDarcular**，然后就可以修改字体大小和字体样式了。   

![img](/img/2016-4-22/029.png)

点击确定之后再回到页面发现字体是变大了，但是Studio默认的一些字体大小如侧边栏等确没有变化，看起来很不协调，如下图：   

![img](/img/2016-4-22/030.png)

强迫症的你肯定无法忍受，没关系，这里也同样可以设置，到 **Preferences** -> **Appearance** 修改如图所示就ok，这里同样不仅可以更改字体大小，也可以选择不同的字体,点击OK，这次页面字体就完全对你胃口了。      

![img](/img/2016-4-22/031.png)

调整之后再看下效果：    

![img](/img/2016-4-22/032.png)


##界面设置

默认的 Android Studio 为灰色界面，可以选择使用炫酷的黑色界面。
**Settings** --> **Appearance** --> **Theme** ，选择 **Darcula** 主题即可。   
![img](/img/2016-4-22/033.png)       

##字体设置
**系统字体设置**

如果你的Android Studio界面中，中文显示有问题，或者选择中文目录显示有问题，或者想修改菜单栏的字体，可以这么设置。
**Settings** --> **Appearance** ，勾选 **Override default fonts by (not recommended)** ，选择一款支持中文的字体即可。我使用的是 **微软雅黑** ，效果不错。    
![img](/img/2016-4-22/033.png)    

**编程字体设置**

此部分会修改编辑器的字体，包含所有的文件显示的字体。
**Settings** --> **Editor** --> **Colors & Fonts** --> **Font** 。默认系统显示的 **Scheme** 为 **Defualt** ，你是不能编辑的，你需要点击右侧的 **Save As...** ，保存一份自己的设置，并在当中设置。之后，在 **Editor Font** 中即可设置字体。
**Show only monospaced fonts** 表示只显示等宽字体，一般来说，编程等宽字体使用较多，且效果较好。    

![img](/img/2016-4-22/034.png) 

**Settings** --> **Editor** --> **Colors & Fonts** 中可以还可以设置字体的颜色，你可以根据你要设置的对象进行选择设置，同时你也可以从网络上下载字体颜色设置包导入。    


##代码格式设置
如果你想设置你的代码格式化时显示的样式，你可以这么设置。
**Settings** --> **Code Style** 。同样的， **Scheme** 中默认的配置，你无法修改，你需要创建一份自己的配置。             

![img](/img/2016-4-22/035.png)    


##默认文件编码    
无论是你个人开发，还是在项目组中团队开发，都需要统一你的文件编码。出于字符兼容的问题，建议使用 **utf-8** 。中国的 Windows 电脑，默认的字符编码为 **GBK** 。
**Settings** --> **File Encodings** 。建议将 **IDE Encoding** 、 **Project Encoding** 、 **Properties Fiels** 都设置成统一的编码。    

![img](/img/2016-4-22/036.png)    


##其他设置    

**1.**Android Studio编辑区域，在中部会有一条竖线。这条线是用以提醒程序员，一行的代码长度最好不要超过这条线。如果你不想显示这条线，可以这么设置。    
**Settings** --> **Editor** --> **Appearance** ，取消勾选 **Show right margin (configured in Code Style options)** 。     

![img](/img/2016-4-22/037.png)    

**2.**显示行号     
**Settings** --> **Editor** --> **Appearance** ，勾选 **Show line numbers** 。   
![img](/img/2016-4-22/038.png)

**3.**显示空格。我习惯显示空格，这样就能看出缩进是 tab 缩进还是空格缩进。建议使用空格缩进。     
**Settings** --> **Editor** --> **Appearance** ，勾选 **Show whitespaces** 。     
![img](/img/2016-4-22/039.png)   

**4.**去除拼接检查。我个人觉得没用，所以禁用掉。      
**Settings** --> **Inspections** --> **Spelling** ，取消勾选。     
![img](/img/2016-4-22/040.png)

**5.**插件。Android Studio和Eclipse一样，都是支持插件的。Android Studio默认自带了一些插件，如果你不使用某些插件，你可以禁用它。      
**Settings** --> **Plugins** ，右侧会显示出已经安装的插件列表。取消勾选即可禁用插件。    
![img](/img/2016-4-22/041.png)

我个人禁用了一下插件:

- **CVS Integration** ： **CVS** 版本控制系统，用不到。
- **Google Cloud Tools For Android Studio** ： **Google云** 用不到。
- **Google Login** ： Google账号登录，**Google Cloud Tools For Android Studio** 插件需用，用不到。
- **hg4idea** ： **Mercurial** 版本控制系统，用不到。

这里需要注意的是，如果禁用了2和3选项，将导致不能使用导入官方样例的功能（ **import sample** ）。

你可以在 **Browse repositories** 页面中，搜索插件并安装。
我个人额外安装的插件：   
- **gitignore support** ： **Git** 版本控制系统中 **.gitignore** 文件管理插件。    


**6.** 检查更新。Android Studio支持自动检查更新。之前尚未发布正式版时，一周有时会有几次更新。你可以设置检查的类型，用以控制更新类型。      
**Settings** --> **Updates** 。勾选 **Check for updates in channel** ，即开通了自动检查更新。你可以禁用自动检查更新。右侧的列表，是更新通道。   

- **Stable Channel** ： 正式版本通道，只会获取最新的正式版本。
- **Beta Channel** ： 测试版本通道，只会获取最新的测试版本。
- **Dev Channel** ： 开发发布通道，只会获取最新的开发版本。
- **Canary Channel** ： 预览发布通道，只会获取最新的预览版本。

以上4个通道中， **Stable Channel** 最稳定，问题相对较少， **Canary Channel** 能获得最新版本，问题相对较多。


**7.**自动导入。当你从其他地方复制了一段代码到Android Studio中，默认的Android Studio不会自动导入这段代码中使用到的类的引用。你可以这么设置。     
**Settings** --> **Editor** --> **Auto Import** ，勾选 **Add unambiguous improts on the fly** 。    
![img](/img/2016-4-22/042.png)    


##运行    

接下来运行程序，运行和 **Eclipse** 中比较像，点击菜单栏的绿色箭头直接运行：    
![img](/img/2016-4-22/043.png)   

**Studio** 默认安装会启动模拟器，如果想让安装到真机上可以配置一下。在下拉菜单中选择 **Edit Configurations** 选择提示或者是USB设备。     
![img](/img/2016-4-22/044.png)     
![img](/img/2016-4-22/045.png)

##常用功能   
在Studio菜单栏的右边有这样几个常用的功能，如图分别是 Gradle同步、AVD Manager、SDK Manager、DDMS：       
![img](/img/2016-4-22/046.png)   

**Gradle同步** 在你项目运行或者更改Gradle配置的时候都要点击下这个按钮，会下载相应的依赖

**AVD Manager** 模拟器管理

**SDK Manager** 就是管理你的SDK版本

**DDMS** 即 Dalvik Debug Monitor Service，Dalvik调试监控服务。

##创建模拟器
建议在创建模拟器前把 **SDK Manager** 中的 **Tools、Extras** 都更新到最新。

点击 **AVD Manager** 按钮：     
![img](/img/2016-4-22/047.png)

点击图中的创建按钮：    
![img](/img/2016-4-22/048.png)

选择一个设备，这里我选择 Nexus 5，然后Next：      
![img](/img/2016-4-22/049.png)

这里选择一个系统版本，这里以5.0为例，然后Next：     
![img](/img/2016-4-22/050.png)

由于各位的屏幕尺寸不一样，建议这里Scale一栏选择Auto，然后点击Finish接着可以看到我们已经创建好一个5.0的模拟器了：    
![img](/img/2016-4-22/051.png)

这次我们再运行，选择模拟器启动看下最终效果（模拟器的启动很慢，大家耐心等待）：     
![img](/img/2016-4-22/052.png)      
![img](/img/2016-4-22/053.png)

























 
 

