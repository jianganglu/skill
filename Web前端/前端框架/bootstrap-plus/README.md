# 更高效地定制bootstrap

bootstrap 已经作为前端开发必不可少的框架之一，应用bootstrap使得我们对布局、样式的设定变得非常简单。

但bootstrap提供的默认样式往往不能满足我们的需求，从而定制化bootstrap成为我们经常需要做的工作，本文就如何更高效更可维护地定制bootstrap做一下探讨。

如下图，在你的button 中加入bootstrap的class: btn btn-primary,就可以将默认的button（左边）变成右边的样式。

(src/img/btn.png)

可如果我们想应用自己的样式呢？比如我们想要拥有圆角的button。

##通常，我们可以直接覆盖bootstrap的样式。

我们在自己的项目目录下新建my-custom.css文件，加入如下代码：

    .btn {
       -webkit-border-radius: 20px;
       -moz-border-radius: 20px;
       border-radius: 20px;
    }

将my-custom.css文件引用放到bootstrap.css文件后面，我们定义的btn样式就会覆盖原有的样式（注：这里的‘覆盖’指的是增量叠加式的覆盖）。

    <link rel="stylesheet" href="boostrap.css">
    <link rel="stylesheet" href="my-custom.css">

但这种方法有它的优缺点，

优点：不会改变你的工作流程。你可以快速直接修改你的样式，即使是你的网站引用了其他的类似bootstrap的框架样式，你都可以在同一个地方进行统一的定制。

缺点：但是对于更彻底的修改(比如重新设计导航栏)或是非局部的修改(比如修改适用于整个网站的高亮颜色)来说，这样东一块，西一块的覆盖样式更像是一种打补丁式的解决方案。而且你的新样式要添加到Bootstrap的默认样式表里，让本已经100 KB的文件越发臃肿。如果你不仅仅想要做一些覆盖，那就要考虑一种更具扩展性的方法了。

##另一种方法是生成一个自定义构建的bootstrap。

我们可以使用官方的 构建器 ，你可以对bootstrap中样式变量进行自定义。如下图所示：

(src/img/bootstrap.png)

bootstrap 是基于less定制的，如果你不熟悉less语法，建议到其官网（ http://lesscss.org/ ）或者中文网（ http://less.bootcss.com/ http://www.bootcss.com/p/lesscss/ ）学习一下，很简单，了解并学会使用它用不了多长时间。

定制好你的变量后点击download按钮就会生成一套属于你的bootstrap框架了。

当然，这种方法也有它的优缺点，

优点：相比上一种方法，它简便了你对整体网站的修改。

缺点：首先你很难一开始就确定网站所有的样式风格，当然你可以在确定好了后再生成一个最终版本。所以这就引入一个问题，如果你还要时不时更换你的样式，你同样需要找到bootstrap样式源文件编辑，你可能还要用到第一种方法，比如我要使用圆角的带阴影的button，光定制就不能满足我的需求，再者，如果面对bootstrap升级的问题，你还需要重新根据你的样式构建一个新版本的bootstrap，这样要真的做起来，会非常的麻烦。

##最后一种方法是深度定制bootstrap less

首先获得bootstrap的 源码 ，

打开源码，你会发现Bootstrap的样式是用 LESS 而不是CSS写的。LESS 是一种动态样式表语言，相比于CSS，它支持多种 优秀特性 ，包括选择器嵌套，创建变量(就像在上面生成器中使用的)。一旦写完，你可以选择将LESS代码预先或在运行时编译成 CSS。如果你喜欢 Sass，可以使用这个适用于 Sass的Bootstrap 。

在 less 文件夹中，你会看到许多 按照组件来划分 的 LESS 文件。