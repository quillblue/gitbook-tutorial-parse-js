##Bootstrap静态HTML模板
现在，让我们为要做的博客系统准备一个静态网页的版本。为了让大家能够更轻松地完成整个教程，我直接使用了[Bootstrap](http://getbootstrap.com/)提供的[博客模板](http://getbootstrap.com/examples/blog/)。如果你对于Bootstrap相当熟悉，或是已经有了一个设计完成的静态网页，你可以按照你自己的方式完成这一部分。如果你对于Bootstrap并不熟悉，可以按着教程继续往下做。

###第1步 下载Bootstrap
首先，[下载Bootstrap](http://getbootstrap.com/getting-started/#download)（我们目前使用的版本是3.2.0），解压后放到`XAMPP/xamppfiles/htdocs/blog`文件夹下。

![](https://cms-assets.tutsplus.com/uploads/users/435/posts/21997/image/12-bootstrap.png)


###第2步 从Bootstrap基础模板开始
将下面给出的Bootstrap基础模板复制到`index.html`，这个模板包含了基本的HTML结构，并且引用了`bootstra.css.min`，`bootstrap.js`和`jquery.min.js`。从这样的一个模板开始可以节约不少时间。
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Bootstrap 101 Template</title>

    <!-- Bootstrap -->
    <link href="css/bootstrap.min.css" rel="stylesheet">

    <!-- HTML5 Shim and Respond.js IE8 support of HTML5 elements and media queries -->
    <!-- WARNING: Respond.js doesn't work if you view the page via file:// -->
    <!--[if lt IE 9]>
    <script src="https://oss.maxcdn.com/html5shiv/3.7.2/html5shiv.min.js"></script>
    <script src="https://oss.maxcdn.com/respond/1.4.2/respond.min.js"></script>
    <![endif]-->
</head>
<body>
    <h1>Hello, world!</h1>

    <!-- jQuery (necessary for Bootstrap's JavaScript plugins) -->
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js"></script>
    <!-- Include all compiled plugins (below), or include individual files as needed -->
    <script src="js/bootstrap.min.js"></script>
</body>
</html>
```
刷新并确认网页能够正常显示。

![](https://cms-assets.tutsplus.com/uploads/users/435/posts/21997/image/13-bootstrap-index.png)

###第3步 复制博客模板示例

打开Bootstrap提供的博客示范：[http://getbootstrap.com/examples/blog/](http://getbootstrap.com/examples/blog/)
在网页上点击右键，选择“**查看网页源代码**”。我们需要将`body`里面的所有内容复制到我们的`index.html`来替换掉基础模板中的`<h1>Hello, world!</h1>`。

请不要复制`<script>`标签里的内容，因为我们已经有了我们所需要用到的所有JavaScript文件。

现在，你的页面应当是这样的：

![](https://cms-assets.tutsplus.com/uploads/users/435/posts/21997/image/14-blog-index.png)

###第4步 复制示例博客的样式并加入到index.html中
你可能已经注意到页面的样式还没有完全正确，那是因为我们还需要一个基于bootstrap基础样式编写的样式表`blog.css`。
你可以在源代码里找到它：[http://getbootstrap.com/examples/blog/blog.css](http://getbootstrap.com/examples/blog/blog.css)

把文件复制到你的`blog/css`文件夹下。

在`index.html`中`bootstrap.min.css`下面引用这个css：
```html
<!-- Bootstrap -->
<link href="css/bootstrap.min.css" rel="stylesheet">
<link href="css/blog.css" rel="stylesheet">
```

现在样式应该已经完全正确了。就此我们得到了我们所需要的静态模板。
![](https://cms-assets.tutsplus.com/uploads/users/435/posts/21997/image/15-blog-style.png)
