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
> 第一个构造方法就是我们普通在代码中新建一个view用到的方法，例如:





















