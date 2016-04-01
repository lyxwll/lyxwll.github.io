---

layout:     post

title:      "傻瓜都可以利用github pages建博客" 

subtitle:   " \"今日，你我都是小白\""

date:       2015-06-21 09:00:00

author:     "Cyzus"

header-img: "img/2015-6-21-github-build-blog/The-New-Internet.jpg"

tag:

   - github
   - lesson

---

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

 - _layouts：这文件夹里面存放你每个页面的设计，一般有default.html（默认页面）和posts.html（博文页面）

 - _includes：这个文件夹里的的内容将会通用到你博客每个页面，起到一种便利的作用

 - _posts：这里面装的就是你的博文啦，记住，要用markdown语法写，要不上传会失败的。

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





 
 

