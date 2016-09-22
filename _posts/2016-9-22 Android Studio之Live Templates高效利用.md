# Android Studio 之 Live Templates 高效利用

标签： AndroidStudio              
------
转载:[http://blog.csdn.net/zuiwuyuan/article/details/48201185](http://blog.csdn.net/zuiwuyuan/article/details/48201185)      
[http://blog.csdn.net/DesmondJ/article/details/47017205](http://blog.csdn.net/DesmondJ/article/details/47017205)
------

在编辑器中使用Ctrl + J 快捷键可以调出Live Templates，可以自动补全所设置模板的代码，善用它能够在很大程度上减少开发所需时间。

### 设置位置
- File --> Settings --> Editor --> Live Templates

### Live Templates语法

可以为每个Template指定名字和语句，并且指定适用的文件类型和语句块（修改底部的Applicable in … 即可）      
在语句中使用$...$ 表示待输入的变量（字符串内也可以用），你在每次输入的时候相同的变量会一起改变。（如在语句中含有两个$i$，则你使用模板时改变其中一个的值，另一个也会一起改变）      
可以使用**Edit Variable** 对它进行一部分修改，它可以修改以下部分：               

| Name        | Expression  | Default Value  | Skip if defined  |
| ------------   | -----:  | :----:  | :-----: |
| 你所定义的所有 $...$ | 为变量赋特殊值 |  默认值 |使用时是否跳过编辑 |

在**Expression**内有很多供使用的非常方便的函数，如className(), methodName()等等。设置Expression后别忘了勾选Skip if defined， 这样在使用的时候光标就不会再停留在这个变量处。   

###常用Android模板示例 

**findViewById** 以下所有$cast$变量的expression值均为expectedType().

| Name        | Templates Text  | 
| ------------| :-----:  |
| fdv         | findViewById(R.id.$resId$); |
| fdvc        | ($cast$) findViewById(R.id.$resId$); |
| fdv_child   | $root$.findViewById(R.id.$resId$); |
| fdvc_child  | ($cast$) $root$.findViewById(R.id.$resId$); |     

示例：    
![img](/img/2016-9-22/0001.gif)  

**Bitmap**初始化 $resource$ 设置defaultValue为"getResources()"             

| Name        | Templates Text  | 
| ------------| :-----:  |
| bmp_res     | Bitmap $var$ = BitmapFactory.decodeResource($resource$, R.id.$resId$); |   

示例:   
![img](/img/2016-9-22/0002.gif)              

**Log** 以下$method_name$ 的expression值为 className(), $method_name$ 的expression值为methodName()。     
  
| Name      | Templates Text  | 
| ----------| :-----:  |
| tag       | private static final String TAG = “$class_name$”; |
| ld        | Log.d(TAG, “$method_name$” + $content$); |
| li        | Log.i(TAG, “$method_name$” + $content$); |
| le        | Log.e(TAG, “$method_name$” + $content$); |     
| lv        | Log.v(TAG, “$method_name$” + $content$); |
| lw        | Log.w(TAG, “$method_name$” + $content$); |      

示例:    
![img](/img/2016-9-22/0003.gif)            

**for循环**          

| Name      | Templates Text  | 
| ----------| :-----:  |
| foreach   | for ($i$ : $data$) { $cursor$ } |
| fiter     | for ($i$=$start$; $i$<$end$; $i$++) { $cursor$ } |
| fiter_with_init  | for (int $i$=$start$; $i$<$end$; $i$++) { $cursor$ } |

示例:    
![img](/img/2016-9-22/0004.gif)             

**常量定义**       

| Name      | Templates Text  | 
| ----------| :-----:  |
| ci        | public static final int $VAR$ = $VALUE$; |
| cs        | public static final String $VAR$ = $VALUE$; |

### 添加方法注释模版    

方法注释模版，大家肯定都不陌生，就是方法上方添加的备注的模板，用过Eclipse的人都知道，当你在方法名前加上/**，再敲击下回车键，系统会自动生成注释信息。 可Android Studio却并没像Eclipse那样有那么良好的默认注释模板，那Android Studio如何设置注释模板呢？

**步骤**     
1.File -> Setting -> Editor -> Live Templates       

2.点击+，创建一个**Template Group** :     
![img](/img/2016-9-22/0005.png)              

3.填个你要的**group**名，我的叫**MyTemplates**
![img](/img/2016-9-22/0006.png)      

4.选中你刚刚创建的**Group**，创建**Live Template**     
![img](/img/2016-9-22/0007.png)                     
![img](/img/2016-9-22/0008.png)                  

**Abbreviation**:表示这个注释的快捷方式，你敲cmt加回车，模板就出来了
**Description**: 表示这个模板描述
**Template text**：模板的内容

5. 要设置你这个mct快捷键在哪里生效，我的选择是在声明的时候生效，也即你在方法名上使用快捷键**Ctrl + J**选择mct就可以了。     
![img](/img/2016-9-22/0009.png) 

6. 编辑模板信息中的变量
   我的Template text有定义了三个变量 desc,date,time,后面两个我要生成日期和时间，所以我们要编辑这两个变量；点击Edit variables，在弹窗里分别为date 和time就是设置对应的方法，date()这个方法会生成日期，time()这个方法会生成时间

![img](/img/2016-9-22/0010.png)      

到此，一个简单的模板即定义好了。接下来可以测试使用。     

7.效果如下:       

![img](/img/2016-9-22/0011.png)      
![img](/img/2016-9-22/0012.png)








