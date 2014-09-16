##设置并连接到Parse数据库
为了使我们的静态博客动态化，我们首先需要在[Parse.com](http://parse.com)上为它建立一个数据库。

###第1步 创建一个新应用
打开 [Parse.com 仪表面板](https://www.parse.com/apps)，点击“**Create New App**”（创建新应用）

我们现在把它取名为`blog`

![](https://cms-assets.tutsplus.com/uploads/users/435/posts/21997/image/16-parse-new-app.png)

创建完成之后，点选“**Quickstart Guide - Data - Web - Existing project**”

![](https://cms-assets.tutsplus.com/uploads/users/435/posts/21997/image/17-parse-sdk.png)

###第2步 在index.html中引用Parse.js
根据速成指南，首先需要在你的`index.html`里引用`Parse.js`。不过你可以把它放在`jQuery`下面而不是`<head>`里面
```html
<!-- jQuery (necessary for Bootstrap's JavaScript plugins) -->
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js"></script>
<!-- Parse.js -->
<script src="//www.parsecdn.com/js/parse-1.2.19.min.js"></script>
```
###第3步 测试Parse SDK
随后，根据你的Application ID和JavaScript Key在你的`blog/js`文件夹下创建一个`blog.js`，并填入一些测试代码。你可以在速成指南中找到Application ID、JavaScript Key和测试代码：
```JavaScript
$(function() {

    Parse.$ = jQuery;

    // Replace this line with the one on your Quickstart Guide Page
    Parse.initialize("W8vTW6MTre3g0ScTeyPzqc6Uzj2KZoQ6GBv0j6ZC", "VVayP3EdZ6QH0QMttzpWgeJ2if4f2m8QjA10SaFQ");

    var TestObject = Parse.Object.extend("TestObject");
    var testObject = new TestObject();
    testObject.save({foo: "bar"}).then(function(object) {
        alert("yay! it worked");
    });

});
```

保存文件，然后在`index.html`里`bootstrap.min.js`下方引用这一JavaScript文件。
```html
<!-- Include all compiled plugins (below), or include individual files as needed -->
<script src="js/bootstrap.min.js"></script>
<script src="js/blog.js"></script>
```

再次在你的localhost中刷新`index.html`，这时你应该能够看到这条弹框消息：

![](https://cms-assets.tutsplus.com/uploads/users/435/posts/21997/image/18-parse-alert.png)

这代表你已经成功连接到了你在云端的数据库:)

这时如果你去查看Parse.com上你的“**Data Browser**”(数据浏览器)时，你可以看到你刚才创建的测试对象。
![](https://cms-assets.tutsplus.com/uploads/users/435/posts/21997/image/19-parse-data-browser.png)
