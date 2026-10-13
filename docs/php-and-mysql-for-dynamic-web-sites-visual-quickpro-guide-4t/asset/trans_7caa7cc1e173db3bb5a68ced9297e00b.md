
编码是一个庞大的主题，但你最需要理解的是：文件中使用的编码决定了可以表示哪些字符（因此，也决定了可以使用哪些语言）。要选择一种编码，你必须首先确认你的文本编辑器或集成开发环境（IDE）——无论你用什么应用程序来创建 HTML 和 PHP 脚本——能否使用该编码保存文档。有些应用程序允许你在首选项或选项区域设置编码；而另一些则在你保存文件时设置编码。

要向 Web 浏览器指明编码，有一个对应的 `meta` 标签：

```
<meta http-equiv="content-type" content="text/html; charset=utf-8" />
```

`charset=utf-8` 部分表明正在使用 UTF-8 编码，即 8 位 Unicode 转换格式的简称。Unicode 是一种可靠地表示每种字母表中每个符号的方式。撰写本书时，Unicode 的第 6 版——即当前版本——支持超过 99,000 个字符！

如果你想创建一个多语言网页，UTF-8 是首选，本书的示例也将使用它。当然，你也可以不这么做。但无论你使用什么编码，都要确保 XHTML 页面指明的编码与你的文本编辑器或 IDE 中实际设置的编码相匹配。如果不匹配，当你在 Web 浏览器中查看页面时，很可能会看到乱码。

---

### 脚本 1.2

这个第一个 PHP 脚本不执行任何操作，但演示了 PHP 脚本的编写方式。在深入复杂的 PHP 代码之前，它也将作为一个测试脚本使用。

---

```
1  <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML
      1.0 Transitional//EN" "http://www.w3.org/
      TR/xhtml1/DTD/xhtml1-transitional.dtd">
2  <html xmlns="http://www.w3.org/1999/
      xhtml" xml:lang="en" lang="en">
3  <head>
4      <meta http-equiv="Content-Type"
          content="text/html; charset=utf-8" />
5      <title>Basic PHP Page</title>
6  </head>
7  <body>
8      <!-- Script 1.2 - first.php -->
9      <p>This is standard HTML.</p>
10 <?php
11 ?>
12  </body>
13  </html>
```

---

### HTML5

撰写本书时，HTML 的下一个主要版本——HTML5——正在积极开发和讨论中，但尚未准备好用于生产环境，这就是为什么我选择不在书中使用它。事实上，当我开始写这本书的第五版时，HTML5 可能仍未发布，而浏览器对该语言的广泛采用将需要更长的时间。尽管如此，作为一个令人振奋的未来发展方向，本书将偶尔提及你可以期待随时间推移而引入和支持的特性。

---

任何写在这些标签内的内容都将被 Web 服务器视为 PHP 处理，意味着 PHP 解释器会解析该代码。PHP 标签之外的任何文本都会作为常规 HTML 立即发送给 Web 浏览器。（因为 PHP 最常用于创建在 Web 浏览器中显示的内容，所以 PHP 标签通常放在页面主体的某个位置。）

除了将 PHP 代码放在 PHP 标签内，你的 PHP 文件还必须具有正确的扩展名。扩展名告诉服务器以特殊方式处理该脚本，即将其作为 PHP 页面处理。大多数 Web 服务器对标准 HTML 页面使用 `.html`，对 PHP 文件使用 `.php`。

在进入步骤之前，请明白你必须已经拥有一个可用的 PHP 安装环境！这可能是在托管网站上，也可能是在你自己的电脑上，遵循[附录 A](#app01.html#app01)“安装”中的说明操作后即可，该附录可从 peachpit.com 免费下载。

#### 创建基本 PHP 脚本

**1.** 在文本编辑器或 IDE 中创建一个新文档，命名为 `first.php`（**[脚本 1.2](#ch01.html#ch01ex02)**）。

通常你使用什么应用程序并不重要，无论是 Adobe Dreamweaver（一个功能强大的 IDE）、TextMate（一款优秀且流行的 Mac 纯文本编辑器），还是 vi（一款缺乏图形界面的 Unix 纯文本编辑器）。尽管如此，某些文本编辑器和 IDE 会让 HTML 和 PHP 的编写与调试变得更容易（反之，Windows 上的记事本做某些事会让编码变得更难：别用记事本！）。如果你还没有钟爱的应用程序，请搜索网络或使用本书对应的论坛（**[www.LarryUllman.com/forums/](http://www.LarryUllman.com/forums/)**）来寻找一个。

**2.** 创建一个基本的 HTML 文档：

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
  <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
  <title>Basic PHP Page</title>
</head>
<body>
  <!-- Script 1.2 - first.php -->
<p>This is standard HTML.</p>
</body>
</html>
```

虽然本书全程使用这种语法，但你可以更改 HTML 以匹配你打算使用的任何标准（例如 HTML 4.0 Strict）。同样，如果你对这些 HTML 代码不熟悉，请参阅专门的 (X)HTML 资源。

**3.** 在结束 `body` 标签之前，插入 PHP 标签：

```
<?php
?>
```

这些是正式的 PHP 标签，也称为 XML 风格标签。虽然 PHP 支持其他类型的标签，但我建议你使用正式类型，本书也将始终如此。

**4.** 将文件保存为 `first.php`。

请记住，如果你不使用适当的 PHP 扩展名保存文件，脚本将无法正常执行。（不使用记事本的原因之一就是它会偷偷给 PHP 文件加上 `.txt` 扩展名，从而导致许多麻烦。）

**5.** 将文件放置在 Web 服务器的适当目录中。

如果你在自己的电脑上运行 PHP（推测是遵循了[附录 A](#app01.html#app01)中的安装说明），你只需将文件移动、复制或保存到电脑上的特定文件夹。如果你不知道正确的目录是什么，请查阅[附录 A](#app01.html#app01)或你特定 Web 服务器的文档以确定正确的目录。

如果你在托管服务器上运行 PHP（即在远程计算机上），你需要使用文件传输协议（FTP）应用程序将文件上传到适当的目录。你的托管公司会提供访问权限和其他必要信息。

**6.** 在 Web 浏览器中运行 `first.php`。

![Image](graphics/01_figure_01_a.jpg)

虽然它看起来像任何其他（简单的）HTML 页面，但这实际上是一个 PHP 脚本，也是本书其余示例的基础。

因为 PHP 脚本需要由服务器解析，所以你绝对必须通过 URL 访问它们（即浏览器地址栏必须以 `http://` 开头）。你不能像在其他应用程序中打开文件那样直接在 Web 浏览器中打开它们（那种情况下地址会以 `file://` 或 `C:\` 或类似路径开头）。

如果你在自己的电脑上运行 PHP，你需要使用类似 `http://localhost/first.php`、`http://127.0.0.1/first.php` 或 `http://localhost/~<user>/first.php`（在 Mac OS X 上，将 `<user>` 替换为你的实际用户名）这样的 URL。如果你使用 Web 主机，你需要使用 `http://your-domain-name/first.php`（例如 **[http://www.example.com/first.php](http://www.example.com/first.php)**）。

**7.** 如果你看不到类似图中所示的结果，开始调试！

学习任何编程语言的一部分就是掌握调试。这是一个有时痛苦但绝对必要的过程。对于这个第一个例子，如果你看不到一个简单但完全有效的网页，请遵循以下步骤：

**1.** 确认你拥有一个可用的 PHP 安装环境（测试说明见[附录 A](#app01.html#app01)）。
