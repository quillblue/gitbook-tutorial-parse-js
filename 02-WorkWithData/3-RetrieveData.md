##获取博客数据

回到你的`blog.js`文件，现在到了借助之前的测试代码从Parse.com取出博客数据到你的网站的时候了。

首先，从Parse.com上获取Blog类的结构，并据此生成一个JavaScript对象：

```JavaScript
var Blog = Parse.Object.extend("Blog");
```
想象一个博客的首页，你可能需要一次性获取一堆blog的信息，而不是一篇一篇去获得。由属于同一类的一系列对象构成的列表在Parse中被称为集合(Collection)，让我们来定义一个集合：

```JavaScript
var Blogs = Parse.Collection.extend({
    model: Blog
});
```
请注意`Blog`和`Blogs`都是类。它们分别是blog和blogs的抽象模板。你可以定义某一篇特定的博文或是一系列的博文，这些便是它们生成的实例。

所以为了能够获得一个所有你在Parse.com上添加的博文的集合，你需要创建一个Blogs集合的实例（请注意在这里首字母不应该大写）：

```JavaScript
var blogs = new Blogs();
```
如果我们不指定其他的参数，只是选择获取这么一个带有数据的集合，它默认会返回`Blog`表里的所有记录。

让我们取出来并把它写到控制台里去：

```JavaScript
blogs.fetch({
    success: function(blogs) {
        console.log(blogs);
    },
    error: function(blogs, error) {
        console.log(error);
    }
});
```

再次尝试在你的本地服务器里加载网站，并查看开发者工具中的控制台里的信息，你应该能够看到这个：

![控制台中显示的blog数据](https://s3.amazonaws.com/cms-assets.tutsplus.com/uploads/users/435/posts/22047/image/08-console-log-data.png)
现在你已经成功从数据库中获取了数据。