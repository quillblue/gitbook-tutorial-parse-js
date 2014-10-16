##在页面上展示数据

###第1步 清理HTML
在我们把博客数据渲染到页面之前，我们首先需要为它准备一个HTML模板。

去掉`.blog-main`里面的所有内容，用一个简单的代码占位容器(container)替代：

```html
<div class="col-sm-8 blog-main">
    <div class="main-container"></div>
</div>
```

然后，当你查看原来的博客模板的时候，你会发现一篇博文的HTML结构可以被简化成如下的形式：

```html
<div class="blog-post">
    <h2 class="blog-post-title"><a href="#">博文标题</a></h2>
    <p class="blog-post-meta">作者与发布时间</p>
    <div>一些正文内容</div>
</div>
```
我们所要做的仅仅是用我们在Parse.com上的每篇博文的数据替换掉那些占位文字。

第2步 准备博客模板
我们首先需要把HTML变成一个能够读取一个数据对象，然后根据这个数据对象渲染成一段HTML代码的模板。

在本例中，我们希望这个模板能够读取一个包含有博文的数组：

```JavaScript
[{
    title: 'Hello World',
    content: '第一帖'
}, {
    title: '又一篇博客',
    content: '<p>可以写HTML哦</p>'
}, ...]

```
然后把它渲染成下面这样的HTML：
```html

<div class="blog-post">
    <h2 class="blog-post-title"><a href="#">Hello World</a></h2>
    <p class="blog-post-meta">作者与发布时间</p>
    <div>第一帖</div>
</div>
<div class="blog-post">
    <h2 class="blog-post-title"><a href="#">又一篇博客</a></h2>
    <p class="blog-post-meta">作者与发布时间</p>
    <div><p>可以写HTML哦</p></div>
</div>
```
在这篇教程中我会向你演示如何使用[handlebars.js](http://handlebarsjs.com/)完成这一步骤，但是你同样可以使用[underscore.js](http://underscorejs.org/#template)，[mustache](http://mustache.github.io/)或者其他你喜欢的模板。

为了使用[handlebars.js](http://handlebarsjs.com/)，我们首先在`index.html`里`parse.js`下面引用它：
```JavaScript
<!-- Handlebars.js -->
<script src="//cdnjs.cloudflare.com/ajax/libs/handlebars.js/2.0.0/handlebars.min.js"></script>
```

随后，让我们在清理过的单篇博文的HTML中为handlebars添加一个特殊的`<script>`标签，就在那些引用JavaScript文件的`<script>`标签上面。此外，我们将它的id命名为`#blogs-tpl`。这样的话handlebars会知道这是一个模板，而你也可以很方便地定位到它。
```html
<script id="blogs-tpl" type="text/x-handlebars-template">
    <div class="blog-post">
        <h2 class="blog-post-title"><a href="#">标题</a></h2>
        <p class="blog-post-meta">作者与发布时间</p>
        <div>一些内容</div>
    </div>
</script>
```
接下来，为了让handlebars清楚该把标题和内容的值放在哪里，你需要把“标题”替换为`{{title}}`而把“一些内容”替换为`{{{content}}}`。handlebars会把双层大括号内的内容识别为一个变量。

```html
<script id="blogs-tpl" type="text/x-handlebars-template">
    <div class="blog-post">
        <h2 class="blog-post-title"><a href="#">{{title}}</a></h2>
        <p class="blog-post-meta">At time by an author</p>
        <div>{{{content}}}</div>
    </div>
</script>
```
你可能注意到了在内容这一块我们使用了三层大括号`{{{}}}`而不是两层`{{}}`。这是因为handlebars.js默认情况下会去掉所有HTML的部分。使用三层大括号`{{{}}}`可以保留内容中的所有HTML格式。

对于`#blogs-tpl`你还需要做的最后一件事情是使用`{{#each blog}} {{/each}}`把博客模板括起来，这样的话它就能读取一个由对象组成的集合，然后逐个地去渲染每个对象：

```html
<script id="blogs-tpl" type="text/x-handlebars-template">
    {{#each blog}}
    <div class="blog-post">
        <h2 class="blog-post-title"><a href="#">{{title}}</a></h2>
        <p class="blog-post-meta">At time by an author</p>
        <div>{{{content}}}</div>
    </div>
    {{/each}}
</script>
```

第3步 渲染博文
我们现在已经有了一个模板，让我们回到`blog.js`，在这里把那些博文渲染到页面上。

为了完成这一部，你需要为博文集合创建一个视图(view)。视图的概念源于[MVC(模型-视图-控制器)框架](http://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller)，而Parse遵循这一框架。我不会在这里深入阐述MVC框架，你只需要知道一个面向博文集合视图的实例能够为这个集合生成HTML并处理其所有事件，而一个视图类就是那样一个实例的抽象模板。

这可能会比较拗口且让人迷糊，但是当我们写代码的时候这一切会变得清楚许多。

所以我们首先来创建一个`BlogsView`类：

```JavaScript
var BlogsView =  Parse.View.extend({
    template: Handlebars.compile($('#blogs-tpl').html()),
    render: function(){ 
        var collection = { blog: this.collection.toJSON() };
        this.$el.html(this.template(collection));
    }
});
```

就像我们从`Parse.Object`继承得到`Blog`类还有从`Parse.Collection`继承得到`Blogs`类一样，你可以简单地`从Parse.View`继承得到一个新的视图类，这样的话它就拥有了所有Parse预先定义好的值和函数方法。

在这里，变量`template`获取了我们之前创建好的模板。随后，`render()`函数从`this.collection`中读取到数据，转化为JSON格式，使用handlebars模板进行渲染，然后交给`this.$el`。

接下来，让我们修改`blogs.fetch()`运行`成功`时的回调函数，让它能够创建一个BlogsView的新实例，渲染那个示例，然后把它放到页面上的`$('.main-container')`中。

```JavaScript
success: function(blogs) {
    var blogsView = new BlogsView({ collection: blogs });
    blogsView.render();
    $('.main-container').html(blogsView.el);
}
```

请注意，当你创建BlogsView的一个新实例时，你把你从Parse服务器上获取的存放在blogs里的博文数据复制到了this.collection中以供render()函数进行渲染。而在往$('.main-container')里填入内容时，你使用到了blogsView.el的值，它就是由render()函数创建的this.$el的内容（在这里blogsView.$el等价于$(blogsView.el)）。这就是视图类和视图实例的工作方式。

现在刷新一下页面：http://localhost/blog/

![渲染后的博客](https://s3.amazonaws.com/cms-assets.tutsplus.com/uploads/users/435/posts/22047/image/09-blogs-rendered.png)

可以看到它开始正常工作了，现在你可以把它推送到你的GitHub Page上。你已经拥有了一个能够正常使用的动态站点，而如果你愿意花一点时间改动一下博客模板或者修改一点点代码的话，你可以很容易地创建作品集或者其他类型的内容页面:)