
那么，你该如何决定需要编写哪种类型的程序呢？应该是客户端的还是服务端的？这完全取决于你想实现的目标，随着后续章节的阅读，这一点会变得更加清晰。这也意味着，要开发功能完善的网站，了解这两种类型会有帮助。

在下一章中，我们将使用**PHP**来讲解服务端编程。在本章的其余部分，我们将讲解客户端 JavaScript 编程。不过，首先，如果你还没有这样做，请按照第 162 页的说明在你的 PC 上安装 PSPad。

启动 PSPad 并连接到你的服务器，这样文件和文件夹列表就会显示在屏幕的左侧。这个列表会让你想起使用 FileZilla 时的样子。这些是你 Web 服务器的内容，通过 PSPad 中的 FTP 组件展示给你。

双击 `public_html` 文件夹，进入服务器上存储可访问网页文件的位置。如果你之前安装了 joomla、wordpress、phpbb 和 plogger 等产品，你会在这里看到它们的文件夹。

我们将创建一个新文件，以便开始探索 JavaScript。因此，右键点击顶部的文件夹图标（那个仅由 2 个点组成的图标），然后选择“新建文件”（New File）。将新文件的名称输入为 `jtest.html` 并按 OK。验证 PSPad 是否已在你的服务器上创建了该文件，它应该出现在列表的底部。

现在，让我们在该文件中创建一个非常简单的网页。双击 `jtest.html` 打开它，并验证你的 PSPad 窗口蓝色标题栏从 `new1.txt` 变为 `jtest.html`。这告诉你正确的文件已打开，并准备就绪以供编辑。

在你的新 `jtest.html` 文件中，键入以下内容：

```html
<HTML>
<body>
This is a JavaScript test
</body>
</HTML>
```

完成后，转到“文件”（File）菜单并点击“关闭”（Close）。点击“是”（Yes）以确认。PSPad 程序现在已直接在 Web 服务器上创建了你的 `jtest.html` 文件。

这是一种与之前不同的工作方式。我们不需要再用 FileZilla 上传测试页面，因为它已经在那里了。我们在“Web Work”文件夹中没有本地副本。

让我们确保它正常工作。退出 PSPad 并打开你的 Web 浏览器。浏览到你的网站和页面。在这种情况下，它是 www.the-web-book.com/jtest.html，这将显示以下内容：

![](img/50e1558b8202f19b96c1cc386ea5ec66_167_0.png)

目前看来很好。但这只是普通的 HTML，而不是 JavaScript，而且这些内容我们之前都见过了。所以让我们来改进一下。

再次启动 PSPad。通过点击“FTP”选项卡，然后点击其下方一行中的第一个图标来连接到服务器。进入你的 `public_html` 文件夹，然后双击你的 `jtest.html` 文件以打开它。

现在，在 `</body>` 标签之前，添加以下内容：

```html
<script type="text/javascript"> alert("Hello There"); </script>
```

完成后，将文件保存到服务器（“文件”、“保存”应该就可以了，因为 PSPad 有其方便内置的 FTP 程序）。然后退出 PSPad，打开你的浏览器，再次浏览到你的 jtest 页面。你应该看到以下内容：

![](img/50e1558b8202f19b96c1cc386ea5ec66_168_0.png)

除了页面上的文本外，现在还有一个带有消息的警告框。这是 HTML 无法单独做到的，但我们的这个小小的 JavaScript 程序使我们能够像这样做聪明的事。

我们的 3 行 JavaScript 代码并不特别聪明。你应该能够毫不费力地理解其工作原理。执行所有繁重工作的那一行是：

```javascript
alert("Hello There");
```

"alert" 命令是创建警告框的那个。

正如我前面提到的，JavaScript 代码与 HTML 代码共存于同一个 .html 文件中。`<script type="text/javascript">` 标签告诉 Web 浏览器你正在从 HTML 切换到 Javascript，然后 `</script>` 标签再切换回 HTML。请注意，这些标签不需要分号，因为它们本身是 HTML 标签而不是 JavaScript 命令。

正如前面讨论过的，JavaScript 是客户端语言，而不是服务端。我将再次重复这一点，因为理解其中的差异至关重要。需要注意的最关键的一点是，由于 JavaScript 代码位于 HTML 文件中，任何使用“查看源文件”（View Source）选项的人都能看到它。如果你再次浏览你的 jtest.html 页面并在 Web 浏览器中选择“查看”、“源文件”选项，你就会明白这意味着什么。屏幕将看起来像这样：

![](img/50e1558b8202f19b96c1cc386ea5ec66_169_0.png)

虽然 JavaScript 非常有用，也很有趣，但任何人都可以在浏览器中查看你的 JS 代码这一事实意味着一件重要的事：切勿将 JavaScript 用于与你网站安全或身份验证相关的任何事项。例如，完全可以用 JavaScript 创建一个密码系统，其中访客被要求输入密码，只有当他正确输入时才会显示“秘密”页面。但如果你用 JavaScript 实现这一点，黑客只需查看你的源代码，找到那部分实际上表示 `如果密码 = 'sesame' 则让他进入` 的代码，从而推断出密码，这就变得微不足道了。

解决这个困境的方法是使用一种编程方法，该方法下的程序代码不会显示在页面上。这正是使用 PHP 等语言进行服务端编程的全部内容，我们稍后会详细介绍。不过，现在让我们回到更多的 Javascript 示例。

再次编辑你的 jtest.html 文件，并用以下内容替换文件的全部内容：

```html
<HTML>
<body>
The current time is:
<script type="text/javascript">
var d = new Date()
document.write(d.getHours())
document.write(",")
document.write(d.getMinutes())
document.write(":")
document.write(d.getSeconds())
</script>
</body>
</HTML>
```

保存文件，浏览到你的 jtest.html 页面，你会看到类似这样的内容：

![](img/50e1558b8202f19b96c1cc386ea5ec66_170_0.png)

让我们更详细地研究一下，你 hopefully 会意识到 Javascript 并不像初看起来那样复杂。首先，这里再次展示代码，并附上行号以辅助后续的解释。

```text
1 <HTML>
2 <body>
3 The current time is:
4 <script type="text/javascript">
5 var d = new Date()
6 document.write(d.getHours())
7 document.write(",")
8 document.write(d.getMinutes())
9 document.write(":")
10 document.write(d.getSeconds())
11 </script>
12 </body>
13 </HTML>
```

第 1、2、3、12 和 13 行你应该很熟悉了。这是标准的 HTML 代码，如前几章所解释的那样。包括“the current time is:”（当前时间是：）这个消息，正如你从屏幕截图中看到的，它会在最终的网页上显示，正如你预期的一样。

第 4 行告诉浏览器我们现在处于 JavaScript 模式，并且随后所有内容都是一个 JavaScript 程序，而不是普通的 HTML。直到第 11 行，该结束程序并告诉 Web 浏览器我们已回到标准的 HTML。

顺便说一下，你可以在 HTML 文件中包含尽可能多的 JS 脚本。只需在每个脚本的开始使用 `<script>` 标签，并以 `</script>` 结束。

现在让我们看看 JS 代码是如何工作的。第 5 行创建了一个名为 d 的新变量，它被设置为当前日期和时间。这就是 JS 中 date() 函数的作用——它返回当前日期和时间。

你要记得，在本章开始时，我指出 JavaScript 是一种客户端编程语言。也就是说，它在 Web 客户端（访客的浏览器）上运行，而不是在 Web 服务器上。通过使用 date() 函数，这一点变得显而易见且重要，因为返回的日期和时间是访客计算机的日期和时间，无论其位于何处。如果用户的计算机上是晚上 7 点，页面将显示小时为 19。

对比一下如果从服务器获取时间会发生什么。英国的晚上 7 点是纽约的下午 2 点。所以如果服务器位于纽约，而基于英国的访客在晚上 7 点检查页面，他被告知时间是下午 2 点。服务端编程有其用途，我们稍后会看到，但获取日期和时间并不一定是其中之一。至少，如果你打算为访客显示它，那就不是。

第 6 行引入了 document.write 语句。这里又是一个你需要理解的基本概念，如果你要涉足 Web 编程。该语句将内容插入到网页中，就好像是你自己编写的一样。但在这种情况下，我们插入的不是预先知道的字面文本。相反，我们插入的是变量 d 的“小时”组件。

其余插入分钟和秒的行，以及几个句号（full stops，此处指逗号和冒号等标点），应该是显而易见的。

在这一点上，理解 document.write 如何工作是至关重要的。所以看看这些示例，它们都产生完全相同的结果：

```html
<html>
<body>
```

要注册本书介绍的 Web 托管公司，请访问 www.the-web-book.com/hosts.html

费用完全相同，但会给我带来一小笔佣金，用于资助本书的开发。谢谢！

