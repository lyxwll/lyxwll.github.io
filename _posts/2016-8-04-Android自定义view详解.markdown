## Android自定义view详解    

###从继承开始

懂点面向对象语言知识的都知道：封装，继承和多态，这是面向对象的三个基本特征，所以在自定义View的时候，最简单的方法就是继承现有的View。

    public class SketchView extends View{
        public SketchView(Context context) {
            super(context);
          }
        public SketchView(Context context, AttributeSet attrs) {
            super(context, attrs);
         }
        public SketchView(Context context, AttributeSet attrs, int defStyleAttr) {
            super(context, attrs, defStyleAttr);
        }
    }             
    
通过上面这段代码，我定义了一个SketchView，继承自View对象，并且复写了它的三个构造方法，我主要来分析一下这三个构造方法：
+ 第一个构造方法就是我们普通在代码中新建一个view用到的方法，例如:

    SketchView sketchView = new SketchView(this);    
    	
就这样，一个自定义的view就被新建出来了，然后可以根据需求添加到布局里。

+ 第二个构造方法就是我们一般在xml文件里添加一个view:

    <me.shaohui.androidpractise.widget.SketchView
           android:layout_width="match_parent"
           android:layout_height="match_parent"
           android:layout_marginRight="16dp"
           android:layout_marginTop="16dp" />

这样，我们就把一个SketchView添加到布局文件里，并且加了一些布局属性，宽高属性以及margin属性，这些属性会存放在第二个构造函数的AttributeSet参数里。   

+ 第三个构造函数比第二个构造函数多了一个int型的值，名字叫defStyleAttr，从名称上判断，这是一个关于自定义属性的参数，实际上我们的猜测也是正确的，第三个构造函数不会被系统默认调用，而是需要我们自己去显式调用，比如在第二个构造函数里调用调用第三个函数，并将第三个参数设为0。



















