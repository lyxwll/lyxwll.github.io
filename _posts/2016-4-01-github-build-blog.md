---

layout:     post
title:      "使用github pages搭建个人静态博客" 
subtitle:   " \"C'est la vie !\""
date:       2016-04-01 09:50:00
author:     "Wangll"
header-img: "img/ranger_rebecca.jpg"

tag:

   - github
   - lesson

---

**转载自:[http://cyzus.github.io/2015/06/21/github-build-blog/](http://cyzus.github.io/2015/06/21/github-build-blog/)**

### 1.前言 ###

鉴于我自身建站经历，不熟悉各种编码语言，口袋里没有多少钱，却殷切希望拥有一个独立的个人博客，在翻阅了各种教程后，看完各种眼花缭乱的代码后，终于将这个网站在github pages上搞出来了。在此，我不希望大家都重蹈覆辙，为了方便大家，我在此为大家做一个傻瓜教程

### 2.了解github ###

说了那么多，首先得了解一下什么是github，<b>GitHub是一个共享虚拟主机服务，用于存放使用Git版本控制的软件代码和内容项目(引自维基百科）。</b>说白了github就是开发者的百度云（有人说是Facebook），用来存储或者共享自己写的代码，非常便利，是近年来很火爆的一个网站服务。


### 3.为什么选择github? ###

能看到我的这篇文章的道友应该都知道，为什么我们要在github上建站？

github有一个很有爱的项目，叫做github pages，这个项目是给开发者建立一个私人页面，上面用来分享新颖的想法和自己写的代码，而且最主要的是，这个是免费而且没有空间流量限制的。这也就是我为什么放弃了自由度很高的，却需要支付高昂的主机费的wordpress，而转投了github pages阵营。

那么废话少说，开始我们的教程吧

### 4.注册github账号 ###

打开[https://github.com/](https://github.com/)站点，注册一个账号

![img](/img/2015-6-21-github-build-blog/sign-up.jpg)

拿到了这个账号你就可以做两件事啦

 1. 建立咱们的博客
 2. 托管自己写的代码

我们今天主要讨论的当然还是建立博客~

### 5.完成注册 ###

注册完后别急着关掉页面，先选择free来明确你<del>老子就是冲着免费来的</del>态度，然后甭管别的，直接点击下面绿色的*Finish sign up*

![img](/img/2015-6-21-github-build-blog/free.jpg)

接着，到你的邮箱**验证账号**，这样你才能之后生成你的个人主页

### 6.创建仓库 ###

接下来到这个页面去创建一个新仓库
[https://github.com/new](https://github.com/new)

这个新仓库就将是存放你即将拥有的博客的地方

注意，你的仓库名不能随便取，这样会导致github混乱，取名的格式应该为“**用户名.github.io**”

后面的操作照配图做就可以了

![img](/img/2015-6-21-github-build-blog/build-repository.jpg)

### 7.进入仓库设置 ###

建完仓库后，在当前页面右边选择Settings，进入设置页面，在这里生成你的github pages

![img](/img/2015-6-21-github-build-blog/settings.jpg)

### 8.自动生成博客 ###

在设置页面往下拉，在github pages那一栏点击“**launch automatic page generator**”

![img](/img/2015-6-21-github-build-blog/generate.jpg)

### 9.编辑用户界面 ###

到这一步，其实是让你编辑你的页面上所展示的信息，如果你就只想有这一面的话，你就可以开始编辑了

title是页面的标题
tagline是页面宣传词（这么理解吧）
body就是正文了

![img](/img/2015-6-21-github-build-blog/edit1.jpg)

记住编辑是用markdown语言，如果你编辑完了（如果你要想有我这样的有很多页面的博客事实上根本不用管它），直接点下面的绿色按钮，“**continue to layouts**”

![img](/img/2015-6-21-github-build-blog/edit2.jpg)

### 10.公布页面 ###

这一步对于只要一个展示页面的同学来说，应该算是终结了，选择一个喜欢的主题模板，然后点击“**Publish page**”，你的页面就公布出来了！

![img](/img/2015-6-21-github-build-blog/choose-themes.jpg)

如果还想继续做博客，那就继续看吧。

### 11.预览页面 ###

在继续教程前，你可以先预览一下你的页面，但实际你最后做出的效果会和这个比起来好几百倍，但你可以先确认一下能不能显示出页面来

### 12.下载安装github ###

下载属于你的系统的github，并安装

Windows：[https://windows.github.com/](https://windows.github.com/)

Mac：        [https://mac.github.com/](https://mac.github.com/)

我之后就用Windows示范了

### 13.克隆你的仓库 ###

登录你的账号，在左上角点击“**+**”，然后选择“**clone**”，点击存放你博客的仓库，把它克隆到本地，并选择存放克隆文件位置，一般默认就好

![img](/img/2015-6-21-github-build-blog/clone.jpg)

默认的位置在我的文档下的github文件夹里

### 14.选择主题框架 ###

这时候，你就该真正考虑一下你的博客主题风格了，如果你前端开发的功底不好，就不建议频繁更换主题了，虽然要改也不是不行，只是要折腾就是了

到这个网站选择你喜欢的模板
[http://jekyllthemes.org/](http://jekyllthemes.org/)

![img](/img/2015-6-21-github-build-blog/themes-serious.jpg)

我就以这套模板为范例来进行教程，因为这个极其精简，可塑性（后期更改性）极强，推荐一下
[http://jekyllthemes.org/themes/cool-concise-high-end/](http://jekyllthemes.org/themes/cool-concise-high-end/)

![img](/img/2015-6-21-github-build-blog/cool-concise-high-end.jpg)

点击“**downlod**”，把它下载下来吧

### 15.应用主题 ###

打开存放你克隆下来仓库的文件夹，把里面的文件全部都删了（没错），除了隐藏文件夹“**.git**”不要删就好了，然后把模板里的东西全部拖到你的原博客仓库里

![img](/img/2015-6-21-github-build-blog/apply.jpg)

### 16.配置博客 ###

 我先简单介绍一下这个仓库里的内容，你根据自身需要用文本编辑器来修改内容

![img](/img/2015-6-21-github-build-blog/list.jpg)

 - index.html：这是你博客的主页面，里面的内容就是你的主页了

 - _config.yml：这是你博客的基本配置文件，里面有你博客的名字，以及存放博主的一些基本信息

 - _layouts：这文件夹里面存放你每个页面的设计，一般有default.html（默认页面）和posts.html（博文页面）。这是模板文件存放的位置。模板需要通过YAML front matter来定义，后面会讲到，{ { content }}标记用来将数据插入到这些模板中来。

 - _includes：这个文件夹里的的内容将会通用到你博客每个页面，起到一种便利的作用。   
 可以用来存放一些小的可复用的模块，方便通过{ % include file.ext %}（去掉前两个{中或者{与%中的空格，下同）灵活的调用。这条命令会调用_includes/file.ext文件。

 - _posts：这里面装的就是你的博文啦，记住，要用markdown语法写，要不上传会失败的。       
 你的动态内容，一般来说就是你的博客正文存放的文件夹。他的命名有严格的规定，必须是2012-02-22-artical-title.MARKUP这样的形式，MARKUP是你所使用标记语言的文件后缀名，根据_config.yml中设定的链接规则，可以根据你的文件名灵活调整，文章的日期和标记语言后缀与文章的标题的独立的。

那么以上就是一个Jekyll规范的博客的基本内容了，想想也不难吧

### 17.上传到github ###

现在你已经把博客基本配置完成了，那么就该把它上传到github公布吧

打开github软件，你会发现changes那栏多了数字，这就是你本地文件发生改变数目的情况，在“**summary**”随便写串东西记录一下，然后按“**commit to master**”，等“**Sync**”出现数字后，你就戳那里同步到github吧！

![img](/img/2015-6-21-github-build-blog/upload.jpg)

![img](/img/2015-6-21-github-build-blog/sync.jpg)

### 18.后记 ###

稍等一会儿，打开你的网站，就会发现你的博客已经神奇的出现了，
比如我的：http://cyzfiles.github.io/

那么教程到这儿也差不多完了，之后你可以在**_posts** 文件夹里继续撰写博文，然后按照**第17步** 上传到github即可


##使用Disqus管理评论

模板部分到此就算是配置完毕了，但是Jekyll只是个静态页面的发布系统，想做到关爽场倒是很容易，如果想要评论呢？也很简单。

现在专做评论模块的产品有很多，比如[Disqus](https://disqus.com/)，还有国产的多说，Disqus对现在各种系统的支持都比较全面，到写博客为止，多说现在仅是WordPress的一个插件，所以我这里暂时也使用不了，多说与国内的社交网络紧密结合，还是有很多亮点的，值得期待一下。我先选择了Disqus。

我们选择最下面的Universal Code就好，然后会看到一个介绍页面，把下面这段代码复制到你的模板里面，可以只复制到显示文章的模板中：  

```html
<div id="disqus_thread"></div>
<script type="text/javascript">
    /* * * CONFIGURATION VARIABLES: EDIT BEFORE PASTING INTO YOUR WEBPAGE * * */
    var disqus_shortname = 'example'; // required: replace example with your forum shortname 这个地方需要改成你配置的网站名
    /* * * DON'T EDIT BELOW THIS LINE * * */
    (function() {
        var dsq = document.createElement('script'); dsq.type = 'text/javascript'; dsq.async = true;
        dsq.src = 'http://' + disqus_shortname + '.disqus.com/embed.js';
        (document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(dsq);
    })();
</script>
<noscript>Please enable JavaScript to view the <a href="http://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
<a href="http://disqus.com" class="dsq-brlink">blog comments powered by <span class="logo-disqus">Disqus</span></a>
```

配置完之后，你也可以做一些异步加载的处理，提高性能，比如我就在最开始页面打开的时候不显示评论，当你想看评论的时候，点击“显示评论”再加载Disqus的模块。代码很简单，你可以参考我的写法。

```js
$('#disqus_container .comment').on('click',function(){
        $(this).html('加载中...');
        var disqus_shortname = 'beiyuu';
        var that = this;
        BYB.includeScript('http://' + disqus_shortname + '.disqus.com/embed.js',function(){$(that).remove()}); //这是一个加载js的函数
});
```

如果你不喜欢Disqus的样式，你也可以根据他生成的HTML结构，自己改写样式覆盖它的，Disqus现在也提供每个页面的评论数接口，帮助文档在这里可以看到。

##代码高亮插件

如果写技术博客，代码高亮少不了，有两个可选插件[DlHightLight代码高亮组件](http://mihai.bazon.net/projects/javascript-syntax-highlighting-engine)和[Google Code Prettify](http://code.google.com/p/google-code-prettify/)。DLHightLight支持的语言相对较少一些，有js、css、xml和html，Google的高亮插件基本上任何语言都支持，也可以自定义语言，也支持自动识别，也有行号的特别支持。

Google的高亮插件使用也比较方便，只需要在`<pre>`的标签上加入`prettyprint`即可。所以我选择了Google Code Prettify。

 
 
