## Android自定义view详解    

###从继承开始

懂点面向对象语言知识的都知道：**封装**，**继承**和**多态**，这是面向对象的三个基本特征，所以在自定义View的时候，最简单的方法就是继承现有的View。

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

> 关于第三个参数defStyleAttr,其实也可以拿出来说一整篇文章，有想详细了解的读者可以去看下本篇文章最后的第三个参考链接，我在这里只是简单的说一下：defStyleAttr指定的是在Theme style定义的一个attr，它的类型是reference,主要生效在obtainStyledAttributes方法里，obtainStyledAttributes方法有四个参数，第三个参数是defStyleAttr，第四个参数是自己指定的一个style，当且仅当defStyleAttr为0或者在Theme中找不到defStyleAttr指定的属性时，第四个参数才会生效，这些指的都是默认属性，当在xml里面定义的，就以在xml文件里指定的为准，所以优先级大概是：xml>style>defStyleAttr>defStyleRes>Theme指定，当defStyleAttr为0时，就跳过defStyleAttr指定的reference，所以一般用0就能满足一些基本开发。  

###Measure->Layout->Draw    

在学会如何写一个自定义控件之前，了解一个控件的绘制流程是必要的，在Android里，一个view的绘制流程包括：Measure，Layout和Draw，通过onMeasure知道一个view要占界面的大小，然后通过onLayout知道这个控件应该放在哪个位置，最后通过onDraw方法将这个控件绘制出来，然后才能展现在用户面前，下面我将挨个分析一下这三个方法的作用。    

+ **onMeasure 测量**，通过测量知道一个一个view要占的大小，方法参数是两个int型的值，我们都知道，在java中，int型由4个字节（32bit）组成，在MeasureSpce中，用前两位表示mode，用后30位表示size。       
       @Override
	    protected void onMeasure(int widthMeasureSpec, int heightMeasureSpec) {
	        int widthMode = MeasureSpec.getMode(widthMeasureSpec);
	        int widthSize = MeasureSpec.getSize(widthMeasureSpec);
	        int heightMode = MeasureSpec.getMode(heightMeasureSpec);
	        int heightSize = MeasureSpec.getSize(heightMeasureSpec);
	        int measuredHeight, measuredWidth;
	        if (widthMode == MeasureSpec.EXACTLY) {
	            measuredWidth = widthSize;
	        } else {
	            measuredWidth = SIZE;
	        }
	        if (heightMode == MeasureSpec.EXACTLY) {
	            measuredHeight = heightSize;
	        } else {
	            measuredHeight = SIZE;
	        }
	        setMeasuredDimension(measuredWidth, measuredHeight);
	    }  
   



















