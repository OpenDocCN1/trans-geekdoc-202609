
try
{
    xhrRequest = getXMLHttpRequest();
}
catch(error)
{
    document.write("Cannot run Ajax code using this browser");
}
if(xhrRequest != null)
{
    xhrRequest.onreadystatechange = processYahooNewsFeed;
    xhrRequest.open("GET", "http://rss.news.yahoo.com/rss/topstories", true);
    xhrRequest.send(null);
}
</script>
</body>
</html>

图 7.16 显示了页面在检索到 feed 中的第一项时的外观。当然，实际内容每天都会发生变化。

图 7.16 使用 Ajax 在网页中包含的 Yahoo 新闻 feed 的一部分

![](img/b2471264f405d17994ef173e4b9cec92_240_0.png)

并使用它来验证包含信用卡号码、日期和浮点数等字段的表单。

### 7.4

在名为 ‘mouseover.js’ 的外部文件中，编写两个 JavaScript 函数，通过使用 logo 的两个不同版本并在鼠标经过 logo 位置时在它们之间切换来为 WebHomeCover logo 添加动画效果。以下是一个 XHTML 页面，其中包含一个锚点，该锚点使用 ‘onmouseover’ 和 ‘onmouseout’ 事件来触发 JavaScript 函数。

```
<?xml version="1.0"?>
<!DOCTYPE html PUBLIC
    "-//W3C//DTD XHTML 1.1//EN"
    "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">
    <head>
        <meta http-equiv="Content-Script-Type" content="text/javascript"/>
        <title>Mouse over logo</title>
        <script type="text/javascript" src="mouseover.js"></script>
    </head>
    <body>
        <!-- File: Exercise7-4.htm -->
        <h2>WebHomeCover Logo</h2>
        <div>
            <a href="http://www.webhomecover.com" onmouseover="mouseOver()" onmouseout="mouseNotOver()">
            <img src="webhomecoverlogo.gif" alt="WebHomeCover logo" id="logo"/>
            </a>
        </div>
    </body>
</html>
```

你需要实现 ‘mouseOver’ 和 ‘mouseNotOver’ 函数。在这些函数中，使用 getElementById 方法导航到 ‘logo’（‘img’ 元素）并将 ‘src’ 属性的名称设置为两个图像文件名之一（每个函数一个）。这两个文件（随 CD 提供）是 ‘webhomecoverlogo.gif’ 和 ‘webhomecoverinverted.gif’。

### 7.5

编写一个名为 ‘processWeatherFeed’ 的 Ajax 函数，该函数访问 RSS 文档中的第一个 title 元素和第二个 description 元素，将它们连接在一起并将其内容写入 XHTML 文档的一个元素。你可以使用各种 RSS 天气 feed 的 URI。例如，Yahoo 提供了一个简单的 RSS URI 用于天气 feed，其中你附加一个 ‘p’ 请求参数，其值为某个位置。例如，以下 URI 将获取英国伦敦的天气。

http://weather.yahooapis.com/forecastrss?p=UKXX0085

你可以通过从 Yahoo 天气主页面导航来查找任何全球天气位置的代码：

http://weather.yahoo.com/

你还可以使用其他天气 feed，例如 RSSWeather.com。以下是使用其 RSS feed 访问伦敦天气的 URL

```
http://www.rssweather.com/icao/EGLC/rss.php
```

你会在网上找到其他 feed，具体取决于它们的配置方式，你可能能够连接它们。记住所有 RSS feed 都使用相同的 XML 文档结构，因此你可以创建一个通用函数，能够读取任何 RSS feed 的数据，而不仅仅是我们到目前为止所做的新闻或天气。

### SUMMARY

在本章中，我们在之前介绍的 JavaScript 语法基础上，探索了 DHTML、表单验证和 Ajax 的一些方面。我们首先描述了 JavaScript 的一些特性，这些特性让我们能够使用 DOM 导航到 XHTML 文档的各个部分并动态更改其状态。然后我们研究了 JavaScript 的一个重要方面，即客户端验证。我们以研究 Ajax 的一些基本方面作为本章的结尾，Ajax 使用 JavaScript 与服务器通信并在无需重新加载的情况下更改当前页面的内容。

### References and further reading

- Dutta, S. (2006) *原生 XMLHttpRequest 对象*. http://blogs.msdn.com/ie/archive/2006/01/23/516393.aspx
- Garrett, J.J. (2005) *Ajax：一种新的 Web 应用程序方法*. http://www.adaptivepath.com/publications/essays/archives/000385.php
- Zakas, N., McPeak, J. and Fawcett, J. (2006) *专业 Ajax*. Wrox/Wiley 2006

## Introduction to PHP

## PHP 简介

### LEARNING OBJECTIVES

### 学习目标

- Be aware of the PHP language and understand what it can be used for
- 了解 PHP 语言并理解它可以用作什么
- Understand that PHP can be embedded within (X)HTML documents using tags to denote the start and end of PHP code
- 理解 PHP 可以使用标记嵌入到 (X)HTML 文档中以表示 PHP 代码的开始和结束
- Understand how it is possible to jump in and out of PHP within a document and what the PHP parser does when it interprets a document
- 理解在文档中如何进出 PHP 以及 PHP 解析器在解释文档时做什么
- Understand and be able to use the echo construct effectively
- 理解并能够有效地使用 echo 构造
- Understand how PHP instructions should be separated
- 理解 PHP 指令应如何分隔
- Understand why you should comment your PHP scripts and be able to do so
- 理解为什么应该注释你的 PHP 脚本并能够做到
- Understand the different PHP types that are supported and how to use PHP variables
- 理解支持的不同 PHP 类型以及如何使用 PHP 变量
- Understand what a PHP constant and a predefined variable are and be able to use them
- 理解 PHP 常量和预定义变量是什么并能够使用它们
- Understand what an expression is, the role of operators and operands and operator precedence
- 理解表达式是什么、运算符和操作数的作用以及运算符优先级

### INTRODUCTION

### 引言

Welcome to the PHP scripting language. In this chapter, we begin by introducing you to the PHP language. We explain what PHP is and how it works by introducing you to your first PHP script and show you how you can view the output that it generates within a Web browser.
欢迎使用 PHP 脚本语言。在本章中，我们首先向你介绍 PHP 语言。我们通过介绍你的第一个 PHP 脚本来解释 PHP 是什么以及它如何工作，并向你展示如何在 Web 浏览器中查看它生成的输出。

We shall provide an introduction to script syntax and explain how and why it is important for you to comment your PHP scripts carefully. We shall introduce the concept of variables and describe how you use them. We shall examine the different types of data which a variable can store and the differences between them. We will also examine PHP operands and operators and explain how these go together to form expressions.
我们将提供脚本语法的介绍并解释为什么以及如何仔细注释你的 PHP 脚本很重要。我们将介绍变量的概念并描述如何使用它们。我们将检查变量可以存储的不同数据类型以及它们之间的差异。我们还将检查 PHP 操作数和运算符并解释它们如何组合形成表达式。

In conclusion, we cover all the basic fundamental PHP constructs and syntax you need to know before you can start doing some of the really interesting and powerful things we cover in later chapters. By the end of this chapter, you will be familiar with creating PHP scripts, saving them and viewing their output using a browser of your choice. It is worthwhile pointing out that PHP is widely supported by a large community of developers and you will find a comprehensive annotated manual online at http://www.php.net/manual/en/ if there are some PHP language concepts we introduce that you would like to investigate further. Anyway, we have a lot to get through, so let’s get started.
总之，我们涵盖了在开始做本章后面涵盖的一些真正有趣和强大的事情之前你需要了解的所有基本 PHP 构造和语法。到本章结束时，你将熟悉创建 PHP 脚本、保存它们并使用你选择的浏览器查看其输出。值得指出的是，PHP 得到大量开发人员社区的广泛支持，如果你想进一步研究我们介绍的一些 PHP 语言概念，你可以在网上找到一份全面的注释手册，网址为 http://www.php.net/manual/en/。无论如何，我们有很多内容要学习，所以让我们开始吧。

### 8.1 Welcome to PHP

### 8.1 欢迎使用 PHP

According to the PHP web site (www.php.net) ‘PHP is a widely-used general-purpose scripting language that is especially suited for Web development and can be embedded into HTML’.
根据 PHP 网站（www.php.net）‘PHP 是一种广泛使用的通用脚本语言，特别适合 Web 开发并且可以嵌入到 HTML 中’。

PHP is a scripting language which can be combined within (X)HTML documents to enable the creation of dynamic web systems. By doing this you can overcome one of the more serious limitations of (X)HTML documents – they are static in nature. What we mean by this
PHP 是一种脚本语言，可以与 (X)HTML 文档结合使用以实现动态 Web 系统的创建。通过这样做，你可以克服 (X)HTML 文档的一个更严重的限制——它们本质上是静态的。我们所说的这个意思

FIGURE 8.1 How PHP works

图 8.1 PHP 的工作原理

![](img/b2471264f405d17994ef173e4b9cec92_245_0.png)

is that a standard (X)HTML document is stored on a server and, when requested, displayed to a user via a web browser. The document that is displayed does not change. It might have some clever JavaScript or plug-in which provides a degree of user interaction but it cannot change the fundamental content it contains nor interface with a database to reflect new dynamic up-to-date content each time it is loaded. By using PHP, you can accomplish all of these things.
是标准 (X)HTML 文档存储在服务器上，并在请求时通过 Web 浏览器显示给用户。显示的文档不会改变。它可能有一些巧妙的 JavaScript 或插件提供一定程度的用户交互，但它不能改变其包含的基本内容，也不能与数据库接口以在每次加载时反映新的动态最新内容。通过使用 PHP，你可以完成所有这些事情。

PHP is a hypertext pre-processor (it's where the name PHP comes from) which means that it processes the hypertext document before it is served to the browser. PHP is therefore a server-side scripting language and all the work is done at the server before it is sent to the client (your web browser). Figure 8.1 illustrates how PHP works.
PHP 是一个超文本预处理器（这就是 PHP 这个名字来源），这意味着它在文档提供给浏览器之前处理超文本文档。因此 PHP 是一种服务器端脚本语言，所有工作都在发送到客户端（你的 Web 浏览器）之前在服务器上完成。图 8.1 说明了 PHP 的工作原理。

If you look closely at Figure 8.1, you see that a user has requested a PHP document from a web server. If the document had been a simple (X)HTML document, the server would have simply sent it to the client web browser. Because the document is a PHP document, the server passes the document to the PHP interpreter. This parses through the document searching for any PHP commands. When it finds any it removes them and replaces them with any output that the PHP commands generate. When it has finished parsing the document, the resulting document with the PHP removed is sent to the user's browser. It sounds complex but it is easier if you see it working for yourself.
如果你仔细观察图 8.1，你会看到用户已从 Web 服务器请求了一个 PHP 文档。如果该文档是一个简单的 (X)HTML 文档，服务器只需将其发送给客户端 Web 浏览器。由于该文档是 PHP 文档，服务器会将文档传递给 PHP 解释器。解释器会解析文档以查找任何 PHP 命令。当它找到任何命令时，它会删除它们并用 PHP 命令生成的任何输出替换它们。当它完成解析文档后，去除了 PHP 的结果文档将被发送到用户的浏览器。这听起来很复杂，但如果你自己看到它工作，就会更容易理解。

### 8.2 Your first PHP script

### 8.2 你的第一个 PHP 脚本

Welcome to your first PHP script, which is commonly known as a 'hello world' application, as all it does is display the words 'Hello, World':
欢迎使用你的第一个 PHP 脚本，它通常被称为 'hello world' 应用程序，因为它所做的只是显示单词 'Hello, World'：

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN"
"http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">
<head>
<title>PHP Script</title>
<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1" />
</head>
<body>
<?php
echo "<p>Hello, World</p>";
?>
</body>
</html>
```

Okay, this does look very complicated for an introductory script but that is because we have chosen to embed the PHP script into an (X)HTML document which conforms to the W3C recommendations and standards. This is a very good thing to do as it ensures the quality and consistency of web documents, but it does make things a little complex for the beginner.
好吧，这对于一个入门脚本来说看起来确实很复杂，但这是因为我们选择将 PHP 脚本嵌入到符合 W3C 建议和标准的 (X)HTML 文档中。这是一件非常好的事情，因为它确保了 Web 文档的质量和一致性，但它确实使初学者的事情变得有点复杂。

Don’t worry about understanding the script at the moment but type the script into your chosen editor and save it as ‘example8-1.php’ in your web server directory. Exactly how you do this depends on the editor you are using, the web server and the PHP environment
目前不要担心理解脚本，但将脚本输入到你选择的编辑器中并将其保存为 ‘example8-1.php’ 到你的 Web 服务器目录中。具体如何操作取决于你使用的编辑器、Web 服务器和 PHP 环境
