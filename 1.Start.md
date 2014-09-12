#准备工作




Bootstrap Static HTML Template

Now  let's prepare a static version of the blog system we are going to make. To show you how fast you can bootstrap through this, I will just utilize the example blog template from Bootstrap. Again, if you are already pretty familiar with Bootstrap or you have a static website designed already, feel free to do it your way. If you are new to Bootstrap, follow along.

Step 1: Download Bootstrap
First, download Bootstrap (currently we are using version 3.2.0 here), unzip it, and put its content in your XAMPP/xamppfiles/htdocs/blog folder. 

Put Bootstrap in blog folder
Step 2: Start With Bootstrap's Basic Template
Then, edit index.html to have the basic template of Bootstrap. It provides a basic HTML structure with links to bootstrap.min.css, bootstrap.min.js, and jquery.min.js. Starting with a template like this will save you a lot of time.

01
02
03
04
05
06
07
08
09
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
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
Refresh and make sure it's working.

Add Bootstrap basic template
Step 3: Copy the Example Blog Template Over
Now, move on an open the example blog from Bootstrap: http://getbootstrap.com/examples/blog/

On the webpage, right click and choose "View Source". We want to copy all the content in <body> over to our index.html and replace the <h1>Hello, world!</h1> in the basic template.

Don't copy the <script> tags since we already have all the Javascript files we need.

You should now have this page:

Add example blog template
Step 4: Copy the Example Blog Style and Add It in index.html
Notice the styles are not right yet. That's because we need blog.css, the blog specific stylesheet built on top of bootstrap basic styles.

Go ahead and find it from the source code: http://getbootstrap.com/examples/blog/blog.css

Copy that file, and put in your blog/css folder.

Link it in index.html below bootstrap.min.css:

1
2
3
<!-- Bootstrap -->
<link href="css/bootstrap.min.css" rel="stylesheet">
<link href="css/blog.css" rel="stylesheet">
And now the styles should be right, and we have our static template ready.

Static template
Setup and Connect to the Parse Database

To make our static blog dynamic, we need to first setup it's own database on Parse.com.

Step 1: Create a New App
Go to Parse.com dashboard, and click "Create New App". 

Let's call it Blog for now.

Create a blog app on Parsecom
Once it's created, go to "Quickstart Guide - Data - Web - Existing project"

Parse Quickstart Guide
Step 2: Add Parse.js in index.html
Following the Quickstart Guide, add Parse.js to your index.html first. But instead of putting it in <head>, you can put it just below jQuery:

1
2
3
4
<!-- jQuery (necessary for Bootstrap's JavaScript plugins) -->
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js"></script>
<!-- Parse.js -->
<script src="//www.parsecdn.com/js/parse-1.2.19.min.js"></script>

Advertisement
Step 3: Test Parse SDK
Moving on, create a blog.js under your blog/js folder with your Application ID and JavaScript key, and some test code. They all can be found in your Quickstart Guide:

01
02
03
04
05
06
07
08
09
10
11
12
13
14
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
Save it, and link this JavaScript file in your index.html, below bootstrap.min.js.

1
2
3
<!-- Include all compiled plugins (below), or include individual files as needed -->
<script src="js/bootstrap.min.js"></script>
<script src="js/blog.js"></script>
Now, refresh index.html on your localhost again, and you should be able to see this alert message:

Success alert message
That means now you are connected to your Blog database in the cloud :)

If you check your "Data Browser" on Parse.com now, you will see the TestObject you just created.

Parse Data Browser
Conclusion

Today, we have set up all the servers we need: XAMPP as our local testing server, GitHub Pages as our web server, and Parse.com as our data server. We also have a basic blog template in place, and it's now connected to the database.

In the next session, I will teach you how to add blog posts from Parse's data browser, retrieve it with JavaScript, and render it on the front end.

Check the source file if you got stuck. And please leave a comment if you meet any difficulties following along.
