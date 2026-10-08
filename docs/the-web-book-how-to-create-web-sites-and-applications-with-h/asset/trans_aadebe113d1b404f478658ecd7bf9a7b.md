
提供一些现成的 JS 代码，用于在一堆数据中查找特定的 cookie。

关于 cookies，还有一件值得了解的事情：每个 cookie 都有一个到期时间，这是在 cookie 创建时设定的。当 cookie 过期时，它会被从计算机中删除。任何随后尝试读取其值的操作都不会返回任何内容。

到期日期可以是：a) 具体的日期和时间，例如 2011 年 5 月 4 日；b) 时长，例如从现在起 31 天；或者 c) 当用户关闭其浏览器时立即生效。如果在创建 cookie 时未指定到期日期，则默认采用选项 C。

Cookies 是一项非常实用的功能，大多数 Web 开发者都会在网站上使用。它允许你存储关于特定访问者的信息，而无需强制他们在你的网站上创建账户并登录。但关于 cookies，有一条你需要知道的黄金法则，如果你打算使用它们的话。虽然只有创建它的网站才能读取 cookie，但任何拥有管理员权限的 PC 用户都可以读取并修改其计算机上的任何 cookie。这是因为 cookie 无非是一个小型数据文件，尽管它有着奇怪的名字，并且通常存储在硬盘上难以找到的位置。但它毕竟是一个文件，并且可以像其他任何文件一样被访问。这种状况允许出现一种称为“cookie 投毒”的情况，即计算机用户故意更改 cookie 的值。

让我们重新审视之前的示例，其中名为 `last-book-browsed` 的 cookie 被设置为“defeating the hacker, by robert schifreen”。如果他电脑上安装了必要的软件，访问图书馆网站的访客可以将 cookie 的值更改为“defeating the afanc, by Rohan Stevenson”。这样，下次他访问图书馆网站时，他将被引导至该 MP3 曲目页面，而不是那本黑客书籍的页面。

这重要吗？完全不重要。但这巧妙地说明了使用 JavaScript 和 HTML 进行客户端 Web 编程的黄金法则。让我们考虑另一个例子，看看原因。

如果用户希望购买书籍，图书馆网站要求他们创建账户并登录。他们部署的处理身份验证（即登录）的机制如下：

1.  要求用户提供其用户名和密码
2.  如果这些详细信息正确，则在用户计算机上设置名为“is_logged_in”的 cookie，其值为“YES”。
3.  每次用户希望访问受保护的页面时，检查 is_logged_in cookie 的值，只有当其值为 YES 时才继续。

许多网站实际上都使用类似的技术。但希望你可以看到其中的缺陷。如果访客向其 PC 上的 `is_logged_in` cookie 投毒，并将值从 NO 更改为 YES，他就可以绕过网站的所有安全措施。

因此，务必出于方便的目的使用 cookies。但不要将用于任何与安全相关的内容，或者需要确保在不知情的情况下 cookie 的值没有被更改的事情。对于此类事项，你需要改用服务器端编程，这将在后面介绍。

# 大家早上好！

这里还有一个 JavaScript 程序示例。要使用它，请将其复制并粘贴到你的 `jtest.html` 文件中，替换其中已有的内容，使用 PSPad。但在这样做之前，请通读代码，看看你能否弄清楚它是做什么的。

```html
<HTML>
<body>
Good
<script type="text/javascript">
var d = new Date()
var time = d.getHours()
if (time < 12)
{
document.write(" morning ")
}
if (time >= 12)
{
document.write(" day ")
}
</script>
everyone!
</body>
</HTML>
```

该程序显示一条由三个单词组成的消息。第一个单词是文件标准 HTML 组件的一部分，为“Good”。同样，最后一个单词是“everyone!”。中间，第二个单词由一些 JavaScript 生成，根据访问者 PC 上的时间是在中午之前还是之后，显示“day”或“morning”。这是一种简单技巧，你可能想在自己的页面上使用。

## 获取屏幕尺寸

在我们结束对 Javascript 的简短探索之前，这里还有一个示例。它展示了为什么客户端编程以及能够查询访问者 PC 和浏览器的各种功能如此有用。

```html
<HTML>
<body>
<script language="javascript">
var w = screen.width;
var h = screen.height;
if ((w=1024) and (h=768))
{
document.write("<img src=normal-pic.jpg>");
}
if ((w > 1280) and (h > 1024))
{
document.write("<img src=bigger-pic.jpg>");
}
</script>
</body>
</HTML>
```

这是一个简单网页的代码，除了包含一张图片外没有其他内容。但是，巧妙之处在于 JavaScript 代码，它查找访问者计算机的屏幕宽度和高度，然后使用 document.write 即时生成 HTML 代码。具体来说，它生成两个不同的 `<img>` 标签之一。如果屏幕分辨率是 1024 乘以 768，则加载 normal-pic.jpg 图像。但如果分辨率更高，则显示 bigger-pic.jpg 文件。

## JavaScript 工具包和框架

如果你喜欢编写客户端代码，但不想学习一门全新的语言，请考虑使用现成的工具包或框架。市面上有几种此类产品，其中包含大量现成的 JavaScript 效果，你可以在网页中调用。其中最受欢迎的是 jQuery，你可以在 www.jquery.com 找到它。最好的消息是，它完全免费。

jQuery 框架使用简单。只需将单个 jquery.js 文件复制到你的 web 服务器上，然后在 HTML 页面的 `<head>` 部分使用几行代码加载它。从那时起，你想在网页上实现的每个效果通常只是几行特殊的 jQuery 代码。例如，以下是使一段文本通过优雅地在另一段文本上方滑动而揭示其内容的 jQuery 命令：

```javascript
$("div.contentToChange p.firstparagraph:hidden").slideDown("slow");
$("div.contentToChange p.firstparagraph:visible").slideUp("slow");
```

在 jQuery 网站上还有更多示例和教程，如果你想在自己的网页中包含视觉效果，它绝对值得一看。

顺便说一下，上述代码引用了所谓的 DOM，即文档对象模型（Document Object Model），这是一种指代 HTML 页面上特定项目的方法。它是 HTML 规范的一部分，而与 jQuery 无关。DOM 以及使用一种名为 Ajax 的技术对其进行操纵，目前未包含在这本书中，但将来可能会添加。如果你希望包含，请通过 **www.the-web-book.com** 与我联系。

## 查找更多信息

正如你可能已经发现的，JavaScript 是任何开发网页的人都非常有用的工具。然而遗憾的是，该语言并非如上一章所暗示的那样易于使用。在你的当地图书馆或亚马逊等网站上搜索，你会找到一些关于 JavaScript 的优秀书籍，其中一些长达 1000 页左右。它确实是一种非常复杂、功能齐全的语言。但如果你不想麻烦和花钱买书，对“javascript tutorial”的 Google 搜索将引导你找到许多有用的在线资源。

由于 JS 完全是客户端的，你也可以查看其他人的代码。只需在查看你认为可能使用 JavaScript 的任何页面时，使用浏览器中的“查看源”选项，然后搜索 `<script>` 标签。实际上，搜索 `<script>` 而不是 `<script language="javascript">`，因为“language=javascript”部分实际上是可选的（尽管是不良做法），这样将找到这两种情况。

也有大量现成的 JavaScript 程序可供从各种网站下载，其中许多免费使用。我喜欢的网站之一是 **www.hotscripts.com**，其中有数千个这样的程序可用。**www.dynamicdrive.com** 网站是另一个有用的资源，它也免费提供许多 Javascript 代码供下载。

JavaScript 最常用于导航和菜单。你可能已经看到过带有各种有趣菜单效果的网站，例如看起来像 Windows 应用程序的下拉菜单，或者在屏幕上滑动的菜单，这样无论你怎么滚动页面，菜单总是位于中间。几乎所有这些都是通过…
