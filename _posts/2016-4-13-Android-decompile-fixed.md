---

layout:     post
title:      "Android安全攻防战，反编译与混淆技术完全解析（上）" 
subtitle:   " \"C'est la vie !\""
date:       2016-04-13 13:50:00
author:     "Wangll"
header-img: "img/ranger_rebecca.jpg"

tag:

   - Android

---


转载自:郭霖大神的[http://blog.csdn.net/guolin_blog/article/details/49738023](http://blog.csdn.net/guolin_blog/article/details/49738023)

##反编译

我们都知道，[Android](http://lib.csdn.net/base/15)程序打完包之后得到的是一个APK文件，这个文件是可以直接安装到任何Android手机上的，我们反编译其实也就是对这个APK文件进行反编译。Android的反编译主要又分为两个部分，一个是对代码的反编译，一个是对资源的反编译，我们马上来逐个学习一下。 

在开始学习之前，首先我们需要准备一个APK文件，为了尊重所有开发者，我就不拿任何一个市面上的软件来演示了，而是自己写一个Demo用来测试。 
这里我希望代码越简单越好，因此我们建立一个新项目，在Activity里加入一个按钮，当点击按钮时弹出一个Toast，就这么简单，代码如下所示：
```
 public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        Button button = (Button) findViewById(R.id.button);
        button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Toast.makeText(MainActivity.this, "you clicked button", Toast.LENGTH_SHORT).show();
            }
        });
    }
}
```

activity_main.xml中的资源如下所示：
```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:paddingBottom="@dimen/activity_vertical_margin"
    android:paddingLeft="@dimen/activity_horizontal_margin"
    android:paddingRight="@dimen/activity_horizontal_margin"
    android:paddingTop="@dimen/activity_vertical_margin">
    
      <Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Button"/>

</RelativeLayout>
    
```


然后我们将代码打成一个APK包，并命名成Demo.apk，再把它安装到手机上，结果如下所示： 













