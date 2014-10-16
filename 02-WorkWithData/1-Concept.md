##类与实例的概念

在我们开始写代码之前，我需要解释下类和实例分别是什么。如果你对于这些概念非常熟悉，你可以选择跳过这一部分。

根据维基百科，类的定义是这样的：

> 类是定义同一类所有对象的变量和方法的原型。当调用某个类的构造函数创建了一个对象时，这个对象被称为是这个类的一个实例。

如果对你来说这些概念太抽象了，我们现在就把它放到我们要做的博客系统的语境里去。 

###一个Blog类

考虑所有博客都拥有哪些组件。它们可能都有一个标题、一个作者、一页内容、一个创建时间等等。那些共有的属性组成了一个所有博文通用的模板，也就是Blog类：

![一个Blog类](https://s3.amazonaws.com/cms-assets.tutsplus.com/uploads/users/435/posts/22047/image/01-a-blog-class.png)

###一个Blog实例
当我们拥有了`Blog`类之后，任意一篇符合这个模板的博文都会成为Blog类都会成为`Blog`类的一个实例：

![一个Blog实例](https://s3.amazonaws.com/cms-assets.tutsplus.com/uploads/users/435/posts/22047/image/02-a-blog-instance.png)

为了便于区分我们是在说`Blog`类还是某一篇特定的博文，我们始终将类名的首字母大写。所以Blog会用来指代Blog类而blog则会指代一个blog实例。这一条规范不仅适用于本教程，也适用于你要写的JavaScript代码。

此外，你可能会注意到在Parse.com上对象(object)这个词会出现很多次。在JavaScript中，类和实例都属于对象，所以我会尽量避免使用对象这个词以免产生歧义。但是Parse上这一词指代的是实例，我们会在这篇教程的后续章节中使用这个词。

###一个Blog表
由于一个类定义了它的实例的所有属性，所以我们可以很容易地将一个特定类的所有实例存在一张表里：每一列是一个属性，而每一行便是一个实例。

![一个Blog表](https://s3.amazonaws.com/cms-assets.tutsplus.com/uploads/users/435/posts/22047/image/03-a-blog-table.png)

这就是你在Parse.com上存储数据的方式。