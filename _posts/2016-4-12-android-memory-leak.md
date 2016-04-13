---

layout:     post
title:      "Android内存泄漏" 
subtitle:   " \"C'est la vie !\""
date:       2016-04-12 16:50:00
author:     "Wangll"
header-img: "img/ranger_rebecca.jpg"

tag:

   - Android

---


转载自:[http://niorgai.github.io/2015/03/03/Android内存泄漏/](http://niorgai.github.io/2015/03/03/Android内存泄漏/)

-------

以下内容提取于[Android进程的内存管理分析](http://blog.csdn.net/gemmem/article/details/8920039)及[Android内存泄漏分析及调试](http://blog.csdn.net/gemmem/article/details/13017999).

Android中的内存分为：
> * native进程：采用C/C++实现，不包含dalvik实例的进程。
> * java进程：Android中运行于dalvik虚拟机之上的进程。每一个java进程都是存在于一个native进程中。

内存空间是一定的，所以在对象无用时就要回收一些对象来留出空间。当Java Garbage Collection开始运行时，它会从他了解还存活的对象作为内存遍历的根节点(GC Root)，遍历heap内存空间，没有直接或间接引用到GC Root的对象便会被回收。

而Android内存泄漏便是指进程中的对象，虽然没有使用价值了，但它仍然有直接或间接的引用到GC Root，那么该对象便不会被GC回收，导致内存持续被占用，使可用内存变小。

##常见的内存泄漏

1. 查询数据库没有关闭Cursor。
2. 使用BaseAdapter作为适配器时没有复用convertView。可以参考ListView与BaseAdapter优化.
3. bitmap没有回收，可以参考Bitmap相关:管理Bitmap内存.
4. 注册对象后没有反注册，比如Broadcast Receiver等。
5. handler问题，如果handler是非静态的，会导致Activity或者Service不被回收，所以应当注册为静态内部类，同时在onDestroy时停止线程:mThread.getLooper().quit();
6. Activity被静态引用，特别是缓存bitmap时，解决方法可以考虑使用Application的context代替Activity的context。
7. View在callback中被引用,可能回调还没有结束,但是view处于引用状态,无法回收。
8. WebView的泄露问题:在魅族上面发现webView打开再关闭就会内存泄露..目前使用的解决方法是在webview外面嵌套一层layout作为container.在Activity的onDestroy中调用container.removeAllViews()方法.
9. Dialog导致Window泄露,如果需要在dialog依附的Activity销毁前没有调用dialog.dismiss().会导致Activity泄露。

##检测内存泄露的方法
1. Android Studio 自带的 Memory Monitor,手动触发GC可以看得比较直观,但是dump出来的文件需要处理才能用MAT打开,利用 sdk/platforms-tool/ 下的 hprof-conv 文件,命令为:

    /hprof-conv source output

2. MAT这篇文章分析得比较透彻。
3. Leakcanary,检测一些容易忽略的内存泄露很好用。
4. adb shell dumpsys meminfo [包名]可以看到内存使用情况。

##一些值得注意的地方

> * 理论上来说,当你退出一个 Activity 后,强制GC一次,内存值应该回到跟进入 Activity 差不多的状态,否则就有可能是内存泄露了.但是有可能是图片加载库中对新 Activity 中加载的图片做了内存缓存,然而这部分内存 GC 可能暂时不会回收.

> * 比如在应用中我使用了 Fresco 去加载本地图库中的图片, Fresco 对这些图片做了内存缓存,然而这部分的图片其实是不需要在内存中缓存的.





[1]: https://www.zybuluo.com/mdeditor?url=https://www.zybuluo.com/static/editor/md-help.markdown
[2]: https://www.zybuluo.com/mdeditor?url=https://www.zybuluo.com/static/editor/md-help.markdown#cmd-markdown-高阶语法手册
[3]: http://weibo.com/ghosert
[4]: http://meta.math.stackexchange.com/questions/5020/mathjax-basic-tutorial-and-quick-reference

