
# 使用 Firefox

我并不想引发关于哪个 Web 浏览器最好的讨论，而且由于 Internet Explorer（至今仍然！）是使用最多的浏览器，你最终需要使用它进行测试，但我个人认为 Firefox（可从 **[www.mozilla.com](http://www.mozilla.com)** 免费获取）是 Web 开发者的最佳 Web 浏览器。Firefox 提供了其他浏览器没有的可靠性和调试功能。如果你想在日常浏览中坚持使用 IE 或 Safari，那随你便，但进行 Web 开发时，请使用 Firefox。

# 使用 Firefox 的插件小工具

![Image](graphics/08_figure_09_i.jpg)

Firefox 的 Web Developer 小工具提供了快速访问许多有用工具的途径。

除了是一个很棒的 Web 浏览器之外，广受欢迎的 Firefox 浏览器拥有大量 Web 开发者会欣赏的功能。此外，你可以通过安装任何可用的免费小工具来扩展 Firefox 的功能。特别是 Web Developer 小工具，它提供了快速访问很棒工具的途径，例如显示表格边框、显示 CSS、验证页面等。我也经常使用这些插件：Firebug、DOM Inspector 和 HTML Validator 等。

# 在另一个浏览器中测试页面

PHP 代码通常与浏览器无关，这意味着无论客户端是什么，你都会得到一致的结果。HTML 则不然。有时特定浏览器的怪癖会影响渲染的页面。在另一个浏览器中运行同一个页面是判断这是 HTML 问题还是浏览器怪癖的最简单方法。

***

> **Tip**
>
> 解决任何类型问题的第一步是了解导致问题的原因。在调试时，请记住每种技术——HTML、PHP、SQL 和 MySQL——所扮演的角色。如果你的页面看起来不对劲，那是 HTML 问题。如果你的 HTML 是由 PHP 动态生成的，这仍然是 HTML 问题，但你需要处理 PHP 代码来修正它。

***

# 书籍勘误

如果你遵循本书中的示例操作但某些东西无法正常工作，你应该怎么做？

**1.** 将你的代码或步骤与书中的内容仔细核对。

**2.** 使用书后的索引查看我是否在前面的页面中引用过某个脚本或函数（你可能错过了重要的用法规则或提示）。

**3.** 查阅 PHP 手册中特定函数的说明，确认该函数在你的 PHP 版本中是否可用，并验证该函数的用法。

**4.** 查看书籍的勘误页面（通过支持网站 **[www.LarryUllman.com](http://www.LarryUllman.com)**），看看代码中是否存在已被报告的错误。不过暂时不要在那里发布你的具体问题！

**5.** 三次检查你的代码，并使用本章概述的所有调试技术。

**6.** 搜索书籍的支持论坛，看看其他人是否遇到过这个问题，以及是否已经确定了解决方案。

**7.** 如果一切都失败了，使用书籍的支持论坛寻求帮助。提问时，请务必包含所有相关信息（PHP 版本、MySQL 版本、你采取的调试步骤及结果等）。

***

# 显示 PHP 错误

当出现问题时，PHP 提供了非常有用且描述性强的错误消息。不幸的是，PHP 在使用默认配置运行时不会显示这些错误。这种策略对于正式服务器是合理的，因为你不希望最终用户看到 PHP 特定的错误消息，但这也让初学者感到更加困惑。要查看 PHP 的错误，你必须开启 `display_errors` 指令，可以在单个脚本中开启，也可以针对整个 PHP 配置开启。

要在脚本中开启 `display_errors`，请使用 **`ini_set()`** 函数。该函数接受一个指令名称和该指令应具有的设置作为参数：

```php
ini_set('display_errors', 1);
```

在脚本中包含此行将为该脚本开启 `display_errors`。唯一的缺点是，如果你的脚本有语法错误导致完全无法运行，你仍然会看到空白页面。要让整个服务器的 PHP 显示错误，你需要编辑其配置，这在 [附录 A](#app01.html#app01) 的“[配置 PHP](#app01.html#app01lev1sec5)”一节中讨论。

## 开启 display_errors

**1.** 在文本编辑器或 IDE 中创建一个新的 PHP 文档，命名为 **`display_errors.php`** (**[脚本 8.1](#ch08.html#ch08ex01)**)：

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"  
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">  
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">  
<head>  
  <meta http-equiv="Content-type" content="text/html; charset=iso-8859-1" />  
  <title>Displaying Errors</title>  
</head>  
<body>  
<h2>Testing Display Errors</h2>  
<?php # Script 8.1 - display_errors.php
```

**脚本 8.1.** `ini_set()` 函数可用于告诉 PHP 脚本显示可能发生的任何错误。

***

```html
1  <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML  
       1.0 Transitional//EN"  
2          "http://www.w3.org/TR/xhtml1/DTD/  
             xhtml1-transitional.dtd">  
3  <html xmlns="http://www.w3.org/1999/  
       xhtml" xml:lang="en" lang="en">  
4  <head>  
5      <meta http-equiv="Content-Type"  
            content="text/html; charset=utf-8" />  
6      <title>Displaying Errors</title>  
7  </head>  
8  <body>  
9  <h2>Testing Display Errors</h2>  
10  <?php # Script 8.1 - display_errors.php  
11  
12  // Show errors:  
13  ini_set('display_errors', 1);  
14  
15  // Create errors:  
16  foreach ($var as $v) {}  
17  $result = 1/0;  
18  
19  ?>  
20  </body>  
21  </html>
```

***

**2.** 在初始 PHP 标签之后，添加：

```php
ini_set('display_errors', 1);
```

从脚本的这一点开始，发生的任何错误都将被显示。

**3.** 制造一些错误：

```php
foreach ($var as $v) { }  
$result = 1/0;
```

要测试 `display_errors` 设置，脚本至少需要有一个错误。第一行甚至不尝试做任何事，但保证会导致错误。这里实际上有两个问题：首先，引用了一个不存在的变量（**`$var`**）；其次，在 **`foreach`** 循环中将非数组（**`$var`**）当作数组使用。

第二行是经典的除以零错误，这在编程语言或数学中都是不允许的。

**4.** 完成页面：

```php
?>  
</body>  
</html>
```

**5.** 将文件保存为 **`display_errors.php`**，将其放在你的 Web 目录中，并在 Web 浏览器中测试。

![Image](graphics/08_figure_10_a.jpg)

开启 `display_errors`（针对该脚本）后，页面会在错误发生时报告错误。

**6.** 如果你愿意，将第一行 PHP 代码改为：

```php
ini_set('display_errors', 0);
```

然后保存并重新测试脚本。

![Image](graphics/08_figure_11_b.jpg)

关闭 `display_errors`（针对该页面）后，相同的错误不再被报告。不幸的是，它们依然存在。

***

> **Tip**
>
> `ini_set()` 函数可用于调整的 PHP 设置是有限制的。具体哪些可以更改、哪些不能，请参阅 PHP 手册。

***

> **Tip**
>
> 顺便提醒一下，在脚本中更改 `display_errors` 设置仅在该脚本运行期间有效（即，它不能有解析错误）。要始终查看发生的任何错误，你需要在 PHP 的配置文件中启用 `display_errors`（同样，请参阅附录）。

***

# 在 PHP 中调整错误报告
