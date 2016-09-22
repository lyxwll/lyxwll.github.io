# Android Studio 之 Live Templates 高效利用

标签： AndroidStudio

---

在编辑器中使用用Ctrl + J 快捷键可以调出Live Templates，可以自动补全所设置模板的代码，善用它能够在很大程度上减少开发所需时间。

### 设置位置
- File --> Settings --> Editor --> Live Templates

### Live Templates语法

可以为每个Template指定名字和语句，并且指定适用的文件类型和语句块（修改底部的Applicable in … 即可）      
在语句中使用$...$ 表示待输入的变量（字符串内也可以用），你在每次输入的时候相同的变量会一起改变。（如在语句中含有两个$i$，则你使用模板时改变其中一个的值，另一个也会一起改变）      
可以使用**Edit Variable** 对它进行一部分修改，它可以修改以下部分：               

| Name        | Expression  | Default Value  | Skip if defined  |
| --------   | -----:  | :----:  | :-----: |
| 计算机     | \$1600  |   5     |         |


在**Expression**内有很多供使用的非常方便的函数，如className(), methodName()等等。设置Expression后别忘了勾选Skip if defined， 这样在使用的时候光标就不会再停留在这个变量处。   

###常用Android模板示例 

**findViewById** 以下所有$cast$变量的expression值均为expectedType().



示例：


**Bitmap**初始化 $resource$ 设置defaultValue为"getResources()"

    
