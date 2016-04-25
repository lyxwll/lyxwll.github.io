---
layout:     post
title:      "Android Studio的下载与安装" 
subtitle:   "\"C'est la vie !\""
date:       2016-04-22 11:20:00
author:     "Wangll"
header-img: "img/ranger_rebecca.jpg"

tag:    
   - Android Studio
---

#Android Studio 的下载与安装


**转载自：[http://stormzhang.com/devtools/2014/11/25/android-studio-tutorial1/](http://stormzhang.com/devtools/2014/11/25/android-studio-tutorial1/)**


**Windows环境下Android Studio的安装**
###准备工具

- JDK安装包。      
  要求：JDK7及以上版本。   

安装 JDK 并配置 JDK 环境变量。   
> 请使用传统的 JAVA_HOME 环境变量名称。很多人会被提醒 JVM 或者 JDK 查找失败，几乎都是因为 JDK 版本或者没有使用 JAVA_HOME 这个环境变量名称的原因。

- Android Studio安装文件	        
  
  因为Google Android的一些官方网站在国内访问有限制，原因你懂得。所以在开始下载安装Studio之前，你需要自备梯子，关于如何翻墙有很多种方法，这里就不做过多介绍，私以为作为一个Android开发者，不懂翻墙基本没法做下去。所以这点投入是值得的，这里推荐大家直接[购买VPN](https://www.ytvpn.com/?r=a9b90a505050781a)吧，因为我曾经折腾了很多翻墙的玩意，要么不稳定，要么速度慢，后来想通了，凡是花点钱能解决的问题都不是问题，这里推荐云梯VPN，价格算是很便宜的了，别再问我速度、稳定性如何，我已经使用并续费快两年了。（通过这个链接购买的，你的账户可以优惠10元）   


###下载     

官方下载有两个地方，均需要翻墙。

- [Android Developer官网](http://developer.android.com/sdk/installing/studio.html)    
Android开发者官网的网站，可直接下载，但是这个网站貌似只更新Beta和正式版，目前只更新到Beta 0.8.14版本。

- [Android Tools Project Site](http://tools.android.com/download/studio/canary)    
Android开发工具的网站，上面链接是Studio的canary渠道，列出了Studio各种实时预览版等。   

**说明：**     
> 1. 32位系统和64位系统是同一个安装文件。    
> 2. 如果电脑中已经安装过Android Studio，可以使用压缩文件版本。
> 3. 可以根据电脑中有没有Android SDK来选择下载是否包含SDK的安装文件。   
> 4. 建议使用包含SDK的安装包（exe）。

###安装

安装过程中的下一步之类的简单操作，不会进行截图讲解，因为你只需要点击 next 。

**讲解1**    
![img](/img/2016-4-22/001.png)     

**第一个选项：**Android Studio程序，必选。**第二个选项：**Android SDK 如果你的电脑中，已经存在 Android SDK 可以不勾选。 **第三个选项** 和 **第四个选项** 都和虚拟机有关系，如果你不使用虚拟机或者SDK中的虚拟机，可以不勾选。    

**讲解2**   
![img](/img/2016-4-22/002.png) 

选择Android Studio和 Android SDK 的安装目录。**PS:最好不要安装在C盘。**    

**讲解3**   

![img](/img/2016-4-22/003.png)    

如果你在 **讲解1** 中勾选了 **HAXM** （也就是第四个选项. **HAXM** 用以为虚拟机提供加速服务，详细内容，请自行搜索），就会出现这一步。
你需要根据自己机器的内容大小来设置这个值，一般建议默认即可。

**讲解4**    

![img](/img/2016-4-22/004.png)  

Android Studio的运行需要 **VC++** 环境，Android Studio安装的过程中，会自动安装。这也是为什么建议使用安装包（exe）的原因。
有些人的电脑使用 **36X** 类的软件会禁止安装 **VC++** 环境，请注意放行。   

**讲解5**    

![img](/img/2016-4-22/005.png)   

一般不出意外，你就看到这个界面。说明你的Android Studio已经安装成功了。   

### 运行Android Studio  

**讲解6**    

![img](/img/2016-4-22/006.png)

每一次安装，都会显示这个界面。用以选择导入Android Studio的配置文件。   

- **第一个选项** ：使用以前版本的配置文件夹。
- **第二个选项** ：导入某一个目录下的配置文件夹。
- **第三个选项** ：不导入配置文件夹。

如果你以前使用过Android Studio，可以选择到以前的版本。如果你是第一次使用，可以选择第三项。

**讲解7**    

![img](/img/2016-4-22/007.png)   

这是在检查你的 **Android SDK** 。有人会在这里卡上很长时间，很大的原因就是：网络连接有问题。可以通过配置 **hosts** 的方式来解决。如果检查需要更新，则会让你安装，从而会有后面 **讲解8 - 讲解11** 。
如果想跳过这一步，可以进行如下操作：
在Android Studio安装目录下的 **bin 目录**下，找到 **idea.properties** 文件，在文件最后追加 **disable.android.first.run=true** 。

**讲解8**    

![img](/img/2016-4-22/008.png)   

点击Next进入选择设置类型向导页。

**讲解9**    

![img](/img/2016-4-22/009.png)    

这里有两个选项“**Standard**”和“**Custom**”，即标准和自定义，如果你本机的**Android SDK**没有配置过，那么建议直接选择“**Standard**”, 点击“**Finish**”按钮。  

**讲解10**    

![img](/img/2016-4-22/010.png)   

如果你 **讲解9** 中选择第一个选项的话，会显示这个界面。选择 **Accept** 点击 **Finish** 进行安装即可。   

**讲解11**    

![img](/img/2016-4-22/011.png)   

如果你 **讲解9** 中选择第二个选项的话，会显示这个界面。需要你选择一个安装目录，需要注意的是： **这个目录中不能包含空格以及汉字。不建议使用默认的%APPDATA%目录** 。点击 **next** 后可以看到类似 **讲解10** 的页面，选择 **Accept** 点击 **Finish** 进行安装。

**讲解12**    

![img](/img/2016-4-22/012.png)   

当你更新完 **Android SDK** ，你就会看到这个界面。直到这个界面才说明，你可以使用**Android Studio**了。    

- **选项1** ： 创建一个Android Studio项目。
- **选项2** ： 打开一个Android Studio项目。
- **选项3** ： 导入官方样例，会从网络上下载代码。此功能在以前的测试版本中是没有的，建议多看一看官方给的范例。
- **选项4** ： 从版本控制系统中导入代码。支持 **CVS** 、 **SVN** 、 **Git** 、 **Mercurial** ， 甚至**GitHub**。
- **选项5** ： 导入非Android Studio项目。比如纯生的 **Eclipse** Android项目， **IDEA Android**项目。如果你的 Eclipse 项目使用官方建议导出（即使用 **Generate Gradle build files** 的方式导出），建议使用 **选项2** 导入。
- **选项6** ： 设置。
- **选项7** ： 帮助文档。

如果一些选项不能点击，说明你的 **JDK** 或者 **Android SDK** 目录指向有问题，请看下面的 设置 **JDK 或者 Android SDK目录** 。


###新建项目  

**讲解13**    

![img](/img/2016-4-22/013.png)    

在这个页面我们可以新建项目，也可以导入项目本地或者GitHub上的项目等，左边可以查看最近打开的项目等，这里我直接新建项目。

然后到如下界面：   

![img](/img/2016-4-22/014.png)  

我们填上项目名称和报名以及项目路径等然后”Next”。  

![img](/img/2016-4-22/015.png)    

这个页面支持你适配TV、Wear、Glass等，我们只选择第一项就ok，选好最小SDK然后”Next”。    

![img](/img/2016-4-22/016.png)   

这个页面选择一个Activity模板，和Eclipse很像，我们直接选择一个Blank Activity好了。

![img](/img/2016-4-22/017.png)    

点击”Finish”后等一会出来如下一个进度条，很多人容易卡在这里，这里需要下载Gradle，只第一次会下载，有点慢，需要翻墙，大家也耐心等待下。    

![img](/img/2016-4-22/018.png)   

下载成功后变看到如下完整的项目界面：  
![img](/img/2016-4-22/019.png)    

至此一个简单的Studio项目就完成了，图片中也可以看到默认是一个白色主题，不够酷炫？Studio默认自带一款高大上的黑色主题，只需要简单修改下就OK。

到**Preference** -> **Appearance** 下更改主题到 **Darcula**。   

![img](/img/2016-4-22/020.png)   

之后我们再来看一下更改后的主题：   

![img](/img/2016-4-22/021.png)    


###其他 

**导入以前版本的Android Studio项目**

> 修改项目中的一些文件中的内容。   
1. 项目根目录下 build.gradle。
'com.android.tools.build:gradle:0.x.x' --> 'com.android.tools.build:gradle:1.0.0'   
2. 项目根目录下 gradle/wrapper/gradle-wrapper.properties 。
http\://services.gradle.org/distributions/gradle-x.x.x-all.zip --> http\://services.gradle.org/distributions/gradle-2.2.1-all.zip   
3. 具体 Module 目录下的 build.gradle 。
很多 Gradle 字段改名，需重新对应起来，更改详情看下图。[图片来源](http://tools.android.com/tech-docs/new-build-system/migrating-to-1-0-0)。    

![img](/img/2016-4-22/022.png)    


**设置 JDK 或者 Android SDK 目录**

有时很多人运行Android Studio会提醒你 JDK 或者 Android SDK 不存在，你需要重新设置。你需要到全局的 Project Structure 页面下进行设置。进入全局的 Project Structure 页面方法如下：

- 方法1:  
![img](/img/2016-4-22/023.png)   

选择 **Configure** --> **Project Defaults** --> **Project Structure**   

- 方法2:   
![img](/img/2016-4-22/024.png)    

选择 **File** --> **Other Settings** --> **Default Project Structure**    

![img](/img/2016-4-22/025.png) 
   
在此页面下设置 **JDK** 或者 **Android SDK** 目录即可。  
