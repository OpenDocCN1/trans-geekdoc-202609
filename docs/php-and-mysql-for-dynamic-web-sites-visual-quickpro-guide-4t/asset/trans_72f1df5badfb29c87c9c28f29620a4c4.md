

## 理解空白字符

使用 PHP 时，你会将数据（如 HTML 标签和文本）发送给 Web 浏览器，浏览器随即会将这些数据渲染为最终用户所看到的 Web 页面。因此，你用 PHP 所做的工作通常是在创建 Web 页面的 *HTML 源代码*。牢记这一点，有三个值得注意的 *空白字符*（额外的空格、制表符和空行）区域：你的 PHP 脚本中、你的 HTML 源代码中，以及渲染后的 Web 页面中。

PHP 通常对空白字符不敏感，这意味着你可以随意安排代码的间距，以使脚本更具可读性。HTML 通常也不敏感。具体来说，HTML 中唯一影响渲染页面的空白字符是单个空格（多个空格仍会被渲染为一个）。如果你的 HTML 源代码中的文本分布在多行上，并不意味着它在渲染后的页面中会显示为多行（![Image](graphics/graycircle-e.jpg) 和 ![Image](graphics/graycircle-f.jpg)）。

要改变渲染后 Web 页面中的间距，请使用 HTML 标签 `<br />`（换行，旧版 HTML 标准中为 `<br>`）和 `<p></p>`（段落）。要改变用 PHP 创建的 HTML *源代码*的间距，你可以：

*   在多行中使用 `echo` 或 `print`。
*   在双引号内打印换行符（`\n`），这等同于按下 Enter 或 Return 键。

---

### 编写注释

创建可执行的 PHP 代码只是编程过程的一部分（诚然，这是最重要的部分）。任何编程工作中另一个次要但仍至关重要的方面是为代码编写文档。事实上，当有人问我什么特质能区分初级程序员和经验丰富的程序员时，我坚定的回答是：对注释的良善且彻底的使用。

在 HTML 中，你可以使用特殊标签添加注释：

```html
<!-- Comment goes here. -->
```

HTML 注释可在源代码中查看，但不会出现在渲染后的页面中（请参阅上一节中的 ![Image](graphics/graycircle-e.jpg) 和 ![Image](graphics/graycircle-f.jpg)）。

PHP 注释的不同之处在于它们根本不会被发送给 Web 浏览器，这意味着最终用户甚至无法在查看 HTML 源代码时看到它们。

PHP 支持三种注释语法。第一种使用井号或数字符号（`#`）：

```php
# This is a comment.
```

第二种使用双斜杠：

```php
// This is also a comment.
```

这两种方式都会导致 PHP 忽略从该符号开始直到行尾（当你按下 Return 或 Enter 键时）的所有内容。因此，这两种注释仅用于单行。它们也常用于在包含 PHP 代码的同一行末尾添加注释：

```php
print 'Hello!'; // Say hello.
```

第三种风格允许注释跨越多行：

```php
/* This is a longer comment
that spans two lines. */
```

**脚本 1.4。** 这些基本注释演示了可在 PHP 中使用的三种注释语法。

---

```php
1   <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML
        1.0 Transitional//EN" "http://www.w3.org/
        TR/xhtml1/DTD/xhtml1-transitional.dtd">
2   <html xmlns="http://www.w3.org/1999/
        xhtml" xml:lang="en" lang="en">
3   <head>
4       <meta http-equiv="Content-Type"
            content="text/html; charset=utf-8" />
5       <title>Comments</title>
6   </head>
7   <body>
8   <?php

9   # Script 1.4 - comments.php
10  # Created March 16, 2011
11  # Created by Larry E. Ullman
12  # This script does nothing much.

13  echo '<p>This is a line of text.<br />
            This is another line of text.</p>';

14  /*
15  echo 'This line will not be
            executed.';
16  */

17  echo "<p>Now I'm done.</p>";
        // End of PHP code.

18  ?>
19  </body>
20  </html>
```

---

#### 为脚本添加注释

**1.** 在文本编辑器或 IDE 中新建一个 PHP 文档，命名为 `comments.php`，从初始 HTML 开始（**[脚本 1.4](#ch01.html#ch01ex04)**）：

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <title>Comments</title>
</head>
<body>
```

**2.** 添加初始 PHP 标签并编写第一批注释：

```php
<?php
# Script 1.4 - comments.php
# Created March 16, 2011
# Created by Larry E. Ullman
# This script does nothing much.
```

每个脚本应包含的首批注释之一是一个介绍性块，列出创建日期、修改日期、创建者、创建者联系方式、脚本用途等。有人建议 Shell 风格的注释（`#`）在脚本中更醒目，因此最适合此类标注。

**3.** 向 Web 浏览器发送一些 HTML：

```php
echo '<p>This is a line of text.<br />This is another line of text.</p>';
```

此处具体做什么并不重要，只要生成一些供 Web 浏览器显示的内容即可。为了多样化，`echo` 语句将打印一些 HTML 标签，包括一个换行符（`<br />`）以增加生成的 HTML 页面的间距。

**4.** 使用多行注释将第二条 `echo` 语句注释掉：

```php
/*
echo 'This line will not be executed.';
*/
```

通过用 `/*` 和 `*/` 包裹任意 PHP 代码块，你可以使该代码失效，而无需将其从脚本中删除。稍后移除注释标签，即可重新激活该部分 PHP 代码。

**5.** 在第三条 `echo` 语句后添加最后一条注释：

```php
echo "<p>Now I'm done.</p>"; // End of PHP code.
```

这最后一条（多余的）注释展示了如何在行尾放置注释，这是一种常见做法。注意此处消息由双引号括起，因为单引号会与撇号冲突（请参阅本章前面的“[需要转义](#ch01.html#ch01sb03)”侧边栏）。

**6.** 关闭 PHP 部分并完成 HTML 页面：

```php
?>
</body>
</html>
```

**7.** 将文件保存为 `comments.php`，将其放入 Web 目录，并在 Web 浏览器中测试 ![Image](graphics/circle-a.jpg)。

![Image](graphics/01_figure_09_a.jpg)

![Image](graphics/circle-a.jpg) [脚本 1.4](#ch01.html#ch01ex04) 中的 PHP 注释不会出现在 Web 页面或 HTML 源代码中 ![Image](graphics/graycircle-b.jpg)。

**8.** 如果你想一探究竟，请在 Web 浏览器中查看源代码，以确认 PHP 注释确实不在那里 ![Image](graphics/circle-b.jpg)。

![Image](graphics/01_figure_10_b.jpg)

![Image](graphics/circle-b.jpg) [脚本 1.4](#ch01.html#ch01ex04) 中的 PHP 注释在客户端浏览器中无处可寻。

---

> **提示**
>
> 你不应该嵌套多行注释（`/* */`）（将一个放在另一个里面）。这样做会导致问题。

---

> **提示**

