# 更高效地定制bootstrap

首先下载bootstrap源码，下载后就不需要对其做任何的改动了。我们单独建立一个文件夹（文件目录只要能引用到bootstrap的scss文件就可以），取名为custom-bootstrap，其中包含以下三个文件：

custom-variables.scss:

这个文件包含你要定制的变量。

custom-other.scss:

这个文件中包含了那些无法通过修改变量完成定制的内容，比如增加或禁用button的text-shandow属性。

custom-bootstrap.scss

这是新的「核心」文件。我们将把它编译成CSS。与原始的 SCSS文件一样，它使用下面的命令来引入上面那两个自定义文件（记住要保证文件正确的引用顺序）

    @import "../bootstrap/less/bootstrap"; //这个引用到原有的bootstrap文件
    @import "custom-variables"; 
    @import "custom-other.less";   
    @import "../bootstrap/less/utilities"; //我们同样要引用原生的utilities.scss