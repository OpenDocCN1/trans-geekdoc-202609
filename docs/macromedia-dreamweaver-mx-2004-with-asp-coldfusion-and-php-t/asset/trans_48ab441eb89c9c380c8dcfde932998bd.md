

两个页面版本之间的区别在于，原始页面的所有 ASP/ColdFusion/PHP 代码都被处理和移除，其输出值写入 XHTML 作为常规 XHTML。

两个页面版本还有一些相似之处：原始中写入的所有标准 XHTML 代码，包括 <body> 和 <p> 标签，以及大部分文本，都原封不动地传递到页面的输出版本。

## 你已学到的内容

在本课中，你已经：

- 了解了展示、文档逻辑和内容之间的关系（第 106–109 页）
- 探索了五种主要服务器模型的优缺点（第 109–112 页）
- 设置了本地 Web 服务器和服务器模型（第 112–130 页）
- 在 Dreamweaver 中定义了动态站点（第 130–135 页）
- 开发了 Web 表单（第 136–138 页）
- 创建了一个收集并显示来自 Web 表单数据的页面（第 139–144 页）

## 在页面之间传递数据

### 第 5 课

动态 Web 页面的显著特征是，浏览器中显示的内容不是像静态 HTML 那样编码在页面中，而是在页面被提供时即时插入页面中的。这意味着，开发动态 Web 应用程序的核心技能是知道如何捕获和嵌入数据，以便在提供 Web 页面时可以将其插入其中。

在上一课结束时，你初步体验了这一过程，当时你将用户在表单中输入的名字显示在另一个页面上。为了完成此任务，你使用 ASP、ColdFusion 或 PHP 代码来捕获 firstName 变量，并将其内联插入常规 XHTML 代码中。虽然这是一个简单的小应用程序，但你在第 4 课结束时实现的表单到 Web 的传输，代表了动态站点开发的很大一部分。

![](img/43fd0127a958864ab2d93e28efe683e7_155_0.png)

> 在本课中，你将把数据从 URL 传递到用户硬盘上的 cookie 中，以创建持久动态数据。

你可能已经知道，动态 Web 站点开发远不止表单和表单变量。你知道可以将数据库内容嵌入 Web 页面，并且你可能也听说过 cookie，它在客户端计算机上存储少量信息以供日后使用。因此，构建动态 Web 页面通常意味着处理来自不同来源的几种不同类型的数据，并将其输出到标准 XHTML 页面中。

在本课中，你将探索在 Web 页面中捕获和嵌入数据的另外两种方法（也称为**绑定**）。在这样做时，你将发现从编码角度看，这些绑定数据的方法彼此非常相似。然而，你还将看到每种方法都提供了其他方法不具备的独特优势。在本课中，你不会为 Newland Tours 做任何事情；这些文件本身也不会特别吸引人或有用。但它们将教你很多关于将数据绑定到 Web 页面这一核心技能的内容。

当你学习每种绑定数据的方法时，你还将了解更多关于 Web 使用的 HTTP 协议。该协议的性质决定了我们将数据绑定到 Web 页面的方式，理解 HTTP 协议基础知识可以揭开动态 Web 页面内部工作原理的许多神秘面纱。随着本书的深入，除了表单、数据库和 cookie 数据之外，你还将学习几种更多将数据绑定到 Web 页面的方法，以及何时和为何使用每种技术。

## 你将学到的内容

在本课中，你将：

- 了解 HTTP 协议，以及它如何使开发人员能够创建动态站点
- 发现 GET 和 POST 之间的区别
- 编码和检索查询字符串或 URL 变量
- 编码和检索 cookie
- 使用动态数据创建 cookie

## 预计时间

本课大约需要 75 分钟完成。

## 课程文件

起始文件：

- Lesson05/Start/newland/about.asp
- Lesson05/Start/newland/contact.asp
- Lesson05/Start/newland/generic_template.asp
- Lesson05/Start/newland/index.asp
- Lesson05/Start/newland/profiles.asp
- Lesson05/Start/newland/test_form.asp
- Lesson05/Start/newland/test_form_processor.asp
- Lesson05/Start/newland/tours.asp

完成的文件：

- Lesson05/Complete/newland/about.asp
- Lesson05/Complete/newland/animal_home_page.asp
- Lesson05/Complete/newland/animal_questions.asp
- Lesson05/Complete/newland/contact.asp
- Lesson05/Complete/newland/generic_template.asp
- Lesson05/Complete/newland/index.asp
- Lesson05/Complete/newland/profiles.asp
- Lesson05/Complete/newland/test_form.asp
- Lesson05/Complete/newland/test_form_processor.asp
- Lesson05/Complete/newland/test_form_processor_cookies.asp
- Lesson05/Complete/newland/tours.asp

## 了解 HTTP 协议

Web 上的页面使用 HTTP 协议进行传输。该协议规定了用户（或在某些情况下是系统）如何通过万维网向服务器发出请求，以及服务器如何响应这些请求。了解该协议的基础知识将有助于你了解动态页面的工作原理。

从本质上讲，HTTP 协议是一个事务系统。客户端向服务器发送请求，服务器将响应发送回客户端。请求的一部分是 URL（统一资源定位符）。当你在浏览器中点击链接时，会向包含所需文件的服务器发送请求。

大多数人没有意识到的是，客户端计算机发送给服务器的内容远不止 URL 请求。它还会发送关于自身的大量信息，包括浏览器（称为 **用户代理**）、用户名、IP 地址、可接受的文件类型（例如 GIF 和 JPEG）以及多个数据源。请求包含标头和正文；刚才指定的大部分信息都在标头中发送。当然，人们没有意识到这一点发生的原因是，标头对人类用户不可见。

服务器收到请求后，如果可以，就会进行响应。它会查看请求的文档，如果该文档中有任何服务器端代码（例如 ASP VBScript、ColdFusion 标记语言或 PHP 代码），服务器就会处理这些指令。完成后，它会移除服务器端代码，并将服务器端代码的输出与文档中的 XHTML 合并，然后全部在响应正文中发送回客户端。响应（与请求一样）包含一个标头，其中包含供客户端系统使用的信息（例如文档大小和类型以及响应的日期和时间）。用户对此事务能看到的基本上只有 URL 和输出的 XHTML 页面。

下图表示一个 HTTP 事务。实心矩形表示用户可见的文档，而虚线矩形表示对用户隐藏的文档。

![](img/43fd0127a958864ab2d93e28efe683e7_159_0.png)

如果你在第 4 课结束时曾好奇 test_form_processor.asp 究竟是如何访问用户在该页面表单中输入的数据的，那么请求就是你的答案。当你点击提交按钮时，firstName 变量及其值是在请求消息正文中发送的。换句话说，HTTP 请求和响应消息的隐藏部分使得可以在客户端和服务器之间来回发送数据值，从而使这些数据可用于服务器上的 ASP、ColdFusion 或 PHP 脚本。这也意味着，如你将在本课中看到的，服务器可以将数据发送回客户端，并附带指示将数据存储在 cookie 中。

在我们开始探讨如何利用 HTTP 协议来促进动态 Web 开发之前，还有一个关于该协议的重要行为你需要知道：一旦服务器将响应发送给客户端，它就会忘记整个事务。也就是说，如果客户端向服务器发出第二个请求，服务器不知道这是刚才发出请求的同一客户端。因此，HTTP 被称为 **无状态协议**。

HTTP 协议的无状态性是开发 Web 应用程序的人面临的一个重大问题。如果 Web 在每个页面之间都忘记你是谁，你如何通过在线购物车的连续页面？如果你有一个多部分调查，如何确保在第 1 页输入的数据被插入到

