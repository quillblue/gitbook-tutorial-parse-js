#设置开发环境
我们将从设置开发环境开始。你将需要一个本地测试服务器、一个Web服务器、一个数据服务器和版本控制工具。如前文所述，这篇教程不需要读者了解后端架构。我们将一步一步地教你来完成整个网站。如果你已经安装了上述工具，可以跳过这一部分。

##第1步 安装XMAPP
在试用了几种不同的解决方案之后，我发现用XAMPP来搭建本地测试服务器是最方便的，因此这篇教程中我将使用XAMPP作为本地测试服务器。

如果你还没有XAMPP,可以从[这里](https://www.apachefriends.org/index.html)下载符合你的操作系统的版本并完成安装。
![XAMPP网站](https://cms-assets.tutsplus.com/uploads/users/435/posts/21997/image/01-XAMPP-Website)
XAMPP网站

我使用的是Mac OS，所以从现在起我将用它来演示。如果你使用的是其他操作系统，过程应该是相似的。

> 译者注：在原作者的建议下，我使用在Windows系统下（使用的是Windows 8.1专业版）完成了整个流程。对于Windows和Mac OS下有显著区别的操作，我将在相应的位置下面予以注明。

安装完成后，启动XAMPP，启动“Apache Web Server”
![](https://cms-assets.tutsplus.com/uploads/users/435/posts/21997/image/02-XAMPP-App.png)
XAMPP - Manage Servers - Start Apache Web Server


XAMPP在Windows下运行时的界面
现在如果你在浏览器中访问[http://localhost/](http://localhost/)的话你可以看到XAMPP的默认页，这代表XMAPP已经成功启动运行。

![](https://cms-assets.tutsplus.com/uploads/users/435/posts/21997/image/03-XAMPP-Localhost.png)
XAMPP处于运行状态时的localhost页面


##第2步 创建一个新的GitHub Page
现在让我们在[GitHub](http://github.com)创建一个新的版本库(repo)。为了简洁好记，我把它命名为`blog`。为了让它能够成为Web服务器，我们需要把它设置为一个[GitHub Page](http://pages.github.com)。

首先，添加一个叫`gh-pages`的新分支
<img>

然后进入设置面板，将`gh-pages`作为默认分支
<img>

好的，然后我们打开终端，使用命令行将GitHub上的分支复制到XAMPP的`htdocs`文件夹
```
$ cd /Applications/XAMPP/xamppfiles/htdocs
$ git clone https://your-git-HTTPS-clone-URL-here
```
>Windows用户可以选择使用Cygwin等工具来完成类似于*nix环境下的命令行操作。但如果你不习惯命令行的操作模式，你可以使用GitHub for Windows或是Tortoise Git来完成GitHub的相关操作，并选用你熟悉的编辑器完成修改相关文件的操作。

打开刚才你复制了Git版本库进去的文件夹，创建一个`index.html`，然后在里面写入`Hello World`。
```    
$ cd blog
$ echo 'hello world' > index.html
```

访问你的[http://localhost/](http://localhost/)，确认网页能够正常显示。.

<img>Localhost - hello world

现在我们把它推送到GitHub上

```
$ git add index.html
$ git commit -am "Add index.html"
$ git push
```

几分钟后，访问http://yourusername.github.io/reponame, 你将可以看到你的index.html出现在了上面。
<img>GitHub Page - hello world

##第3步  注册Parse.js账户
GitHub Page能够托管静态页面，但是并不能实现后端动态生成页面。幸运的是，我们现在有了Parse.js。我们可以使用Parse.com作为我们的数据服务器，并使用JavaScript与它进行通信。由此，我们只需要在GitHub上托管HTML,CSS和JavaScript文件。

如果你没有一个[Parse.com](http://parse.com)账号，请注册一个。
<img>

现在，你已经在云端拥有了自己的数据服务器。