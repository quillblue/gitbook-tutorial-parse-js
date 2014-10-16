##创建Blog类

现在，我们将开始在Parse.com上创建Blog类。

###第1步 添加一个Blog类
首先，访问你在Parse.com的管理面板，找到你的项目，然后点击"Core" - "Data" （也称数据浏览器）。随后，点击“Add Class（添加一个类）”

![在Parse.com上添加一个Blog类](https://s3.amazonaws.com/cms-assets.tutsplus.com/uploads/users/435/posts/22047/image/04-Parse-add-Blog-class.png)

如屏幕截图所示，你需要为你的博文创建一个自定义的类。我们把它命名为`Blog`。在给类命名时需要注意永远让类名能够清楚明白地表示它所存储的内容。

如你所见，你现在在Parse.com上拥有了一个空的自定义的类：
![Parse.com上新创建的自定义类](https://s3.amazonaws.com/cms-assets.tutsplus.com/uploads/users/435/posts/22047/image/05-Parse-empty-class.png)

每一个自定义的类都带有四项系统属性：
- objectId：创建一个新实例时Parse自动生成的唯一标识符，这样的话整个程序能够清楚你需要的是哪一个实例。
- createdAt：当你初次创建一个实例时Parse自动申城的时间戳
- updatedAt：一个有Parse自动生成并更新的时间戳，记录了这个实例最近一次被更改的时间
- ACL：一个定义了谁可以读写这个实例的对象层面上的权限控制列表。如果没有定义的话，它将继承类层面的权限控制策略。我们将在之后的教程中讨论这一属性的使用，此时你可以仅仅选择留空。

###第2步 向Blog类中添加列
接下来，让我们开始向Blog类中添加一些属性。简单起见，我们现在只添加两个属性：`title`（标题）和`content`（内容）。

点击**"+ Col"**（添加新列）按钮来创建一个新的列。将列类型设置为String(字符串)，并命名为`title`。

![在Parse.com上添加数据列](https://s3.amazonaws.com/cms-assets.tutsplus.com/uploads/users/435/posts/22047/image/07-Parse-add-row.png)
重复上述步骤来创建一个`content`的列，值类型同样设置为String。


###第3步 添加一些博文
到了添加博文的时间了！点击**"+ Row"**（添加新行）按钮，在标题和内容两个单元格上双击以添加一些内容：
![在Parse.com上添加博文](https://s3.amazonaws.com/cms-assets.tutsplus.com/uploads/users/435/posts/22047/image/07-Parse-add-row.png)

请注意，你可以在内容这一列中使用HTML标签。事实上，所有类型为字符串的列都支持使用HTML标签，但请不要滥用。在这个例子中，标题列中就不应该包含HTML格式的内容。

正如我之前提到的那样，由于Parse.com支持让你以这样的方式管理你的数据库，如果你自己不想写一个的话你完全可以把它作为你的管理面板。而一旦你学会了如何在自己的网站上展示这些数据，你可以很轻松地创造一些自己的动态博客或者作品集页。在下一部分中，我将会教你如何做到这些。
