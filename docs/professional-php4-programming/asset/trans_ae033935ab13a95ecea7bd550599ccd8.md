

```php
$sql = 'SELECT COUNT(*) AS matched FROM users WHERE username='
. $username . "' AND password='" . $password . "'";
$result = mysql_query($sql);

$array = mysql_fetch_array($result);
$windows['main']->disconnect($disconnect_id);
$windows['main']->destroy();

if ($array['matched'])
    loadSearchPage();
else
    quit("Authentication failed\n");
}
```

我们最后两个函数，quit() 和 destroyWnd()，都用于退出程序。quit() 接受一个参数，在退出程序之前将其打印到命令行，而 destroyWnd() 被我们的登录窗口和搜索窗口用作回调，因此如果用户单击窗口装饰中的 X，他们将相应地退出程序：

```php
function quit($msg)
{
    printf($msg . "\n");
    gtk::main_quit();
}

function destroyWnd()
{
    gtk::main_quit();
}
}
```

代码的最后几行加载 PHP-GTK 扩展，如“Hello World”示例中所述。然后我们调用 loadMainWindow() 函数显示登录页面，最后，与所有 PHP-GTK 应用程序一样，我们调用 gtk::main() 来启动 PHP-GTK 的主循环：

```php
if (strtoupper(substr(PHP_OS, 0, 3)) == 'WIN')
    dl('php_gtk.dll');
else
    dl('php_gtk.so');

loadMainWindow();
gtk::main();
?>
```

给读者的一个小练习可能是修改 quit() 函数，使其不再向命令行输出错误消息，而是弹出一个小对话框告诉用户错误信息（提示：看看 GtkDialog）。

成品的几个截图：

![](img/9cf7789dba9b16ef3f8576d5aea89186_768_0.png)

![](img/9cf7789dba9b16ef3f8576d5aea89186_768_1.png)

![](img/9cf7789dba9b16ef3f8576d5aea89186_768_2.png)

虽然执行简单任务需要大量代码，但并不总是需要自己编写所有这些代码。幸运的是，PHP-GTK 支持一个名为 Glade 的应用程序，它是一个 GUI 构建器。您可以使用 Glade 设计 GUI 并将设计存储为 XML 文件。然后通过将其声明为 GladeXML 对象类的新实例来将 XML 文件加载到 PHP-GTK 中，它将运行您设计的 GUI。介绍 Glade 超出了本入门章节的范围，但 PHP-GTK 手册中有关于它的信息，Wrox Press 出版的《Professional Linux Programming》（ISBN 1-861003-01-3）中也有一个关于使用 Glade 的很好的章节。

我希望这次对 PHP-GTK 的了解能让你和我当初听说可以用 PHP 创建 GUI 应用程序时一样兴奋。它为这门语言增添了全新的维度，并希望能证明对 PHP 社区是一项有价值的资产。

## 资源

- http://sourceforge.net/projects/libedit/
- http://cnswww.cns.cwru.edu/~chet/readline/rltop.html
- http://www.php.net/manual/en/ref.readline.php
- http://gtk.php.net/
- http://gtk.php.net/docs.php
- php-gtk-general-subscribe@lists.php.net
- http://developer.gnome.org/doc/API/gtk/
- http://glade.gnome.org/

## 摘要

在本章中，我们介绍了将 PHP 用作命令行脚本解释器的用法。这使您可以创建交互式脚本，并可从命令行执行。

首先，我们创建了一个用于分析 NCSA 格式 Web 日志的静态脚本。该脚本的设置方式是只能分析一个日志。然后我们扩展了该脚本，以便您可以通过命令行传递各种参数，从而创建一个灵活的脚本，能够处理发送给多个管理员的各种日志。

我们还介绍了以一个简单的数字猜测游戏形式创建交互式脚本的方法。该脚本使用了 libedit 库，并演示了创建更复杂的交互式 shell 脚本时使用的一些方法。

接下来，我们研究了 PHP-GTK，这是一个编写的 PHP 扩展，用于允许客户端、跨平台 GUI 应用程序编程。尽管在撰写本文时该项目仍处于开发阶段，但它允许构建相当复杂的应用程序。

最后，我们为数据库章节中创建的库应用程序创建了一个 PHP-GTK 前端。

![](img/9cf7789dba9b16ef3f8576d5aea89186_771_0.png)

## 21 PHP XML

在最简单的层面上，XML 是结构化文本。我们周围充斥着结构化文本。本书是结构化文本，因为它包含章节、小标题和段落。一封信是结构化文本，因为它通常包含日期、称呼和段落。书籍或信件的每个部分都由该文档的结构定义。为了使结构可见，可以使用标记标签（类似于 HTML）来标记这些部分。用于标记文档的标签是 XML 的基础。XML 是以常见的人类和机器可读格式编写结构化文本的一种方法。

XML 可用于描述任何类型的结构化文本，包括其他标记语言。基于 XML 的标记语言有十几种。它们用于描述从图形到数学方程式的一切。为了控制本章篇幅，我们将只查看在 PHP 中实现并用于读写 XML 文件的 XML 部分。具体来说，我们将查看一个基本的 XML 文件、指定 XML 文件部分的一种方法（XPath），以及一种称为 SML 的简化 XML 格式。

要了解有关不同 XML 标准的更多信息，请参阅万维网联盟 (W3C)。W3C 是管理诸如 XML 之类互联网标准的组织。他们负责发布和维护 XML 规范和建议系列。有关更多信息，请访问其网站：http://www.w3.org/。

在本章中，我们将查看：

- XML、SML 和 XPath 的基础知识
- 作为数据存储的 XML 以及程序化交互
- 允许与 XML 文档交互的 PHP API（SAX、DOM 和 PRAX）

- API 实际应用示例
- PHP 的 Sablotron XSL 支持

在撰写本章时，PHP 中对 XML 的支持仍被视为实验性。当代码行为出乎意料且不一致时，这种实验性特点就会体现出来。

### XML 概述

与 HTML 文档一样，XML 文档有标签和数据。与 HTML 不同，XML 标签可以命名为几乎任何名称。例如，<B>、<Bb> 和 <4f5gt6G> 都是有效的（开始）XML 标签，但前面列表中只有 <B> 是有效的 HTML。与 HTML 文档一样，XML 文档可以在开始标签和结束标签之间包含数据，例如 <B>text</B> 和 <Bb>some text</Bb>。在 XML 中，组合的开始标签、数据和结束标签被称为元素。

![](img/9cf7789dba9b16ef3f8576d5aea89186_773_0.png)

元素由一个开始标签和一个结束标签、多个可选属性、可选字符数据内容和子元素（子节点）组成，被视为一个节点。在元素中有开始标签和结束标签，例如 <first></first> 或 <last></last>。标签名称必须是唯一的，并且区分大小写。元素可以作为其他元素的容器，也可以包含字符数据。属性是元素的一部分，例如 <first id="4">，其中 id="4" 是属性，first 是元素的名称。属性类似于数组，因为两者都具有键值对。

文档中的 XML 标签必须具备两个特征。它们必须是：

- 格式正确

如果所有标签都已关闭、所有元素都正确嵌套且所有属性都用引号括起来，则 XML 文件被视为格式正确。

- 有效

有效文档是必须“格式正确”并符合引用的文档类型定义 (DTD) 或架构的文档。

现在让我们看看所有这些概念在 XML 文件中的样子：

以下 XML 既不是格式正确的，也不是有效的：

```
<root>
    <title>
    <name>some text</title>
    </name>
```

