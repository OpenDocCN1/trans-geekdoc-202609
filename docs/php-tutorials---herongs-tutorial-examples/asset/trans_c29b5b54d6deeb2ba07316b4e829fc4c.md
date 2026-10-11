
浏览完上述示例后，你现在应该很清楚如何处理任何单一语言的非 ASCII 字符了。你可以选择使用 UTF-8 或特定语言的编码。

如果你想在单个 PHP 脚本中包含多种语言的字符，则必须使用 UTF-8 编码。以下是创建支持多种语言的 UTF-8 PHP 脚本的步骤。

1. 在 Windows 系统上，运行“开始”>“所有程序”>“附件”>“记事本”。

2. 在记事本中，输入以下 PHP 脚本：

```
<?php
#  HelpUtf8MultiLanguages.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
#
   print('<html>');
   print('<meta http-equiv="Content-Type"'.
      ' content="text/html; charset=utf-8"/>');
   print('<body>');
   print('<b>Test</b><br/>');
   print('English: Hello world!<br/>');
   print('Spanish: ¡Hola mundo!<br/>');
   print('Korean: 여보세요 세계 !<br/>');
   print('Chinese: 你好世界!<br/>');
   print('</body>');
   print('</html>');
?>
```

3. 不要尝试自己输入那些问候语。访问 Google 语言工具网站 [google.com/language_tools](http://www.google.com/language_tools)。你可以输入 "Hello world!" 并将其翻译成其他语言。在翻译输出页面上，只需复制那些翻译并粘贴回记事本。这不会导致乱码，因为 Google 网站、Windows IE 和记事本都支持 UTF-8。

4. 选择“文件”>“另存为”菜单。输入文件名 `HelloUtf8MultiLanguages.php`。在“编码”字段中选择“UTF-8”，然后点击“保存”按钮。

5. 将 `HelloUtf8MultiLanguages.php` 复制到 `c:\apache\htdocs`。确保你的 Internet 信息服务正在运行本地默认网站。

6. 现在使用 `http://localhost/HelloUtf8MultiLanguages.php` 运行 Internet Explorer (IE)。你应该能看到所有字符都正确显示。

7. 在 IE 窗口中，选择“查看”>“编码”菜单。你应该会看到已选中 UTF-8。

[PHP 教程 - Herong 的教程示例](#part0001.xhtml)

∟ 从输入表单接收非 ASCII 字符

本章提供关于 Web 表单中非 ASCII 字符的教程示例和说明。主题包括从 Web 输入表单接收非 ASCII 字符的基本规则；使用 `$_REQUEST` 数组接收通过 GET 或 POST 方法提交的非 ASCII 字符的示例；处理以 UTF-8 和 ISO-8859-1 编码提交的非 ASCII 字符的示例。

> [从输入表单接收非 ASCII 字符的基本规则](#part0179.xhtml)

> [使用 GET 方法接收非 ASCII 字符](#part0180.xhtml)

> [使用 POST 方法接收非 ASCII 字符](#part0181.xhtml)

> [以 UTF-8 编码接收非 ASCII 字符](#part0182.xhtml)

> [解码 HTML 实体](#part0183.xhtml)

要点：

*   非 ASCII 字符在网页上的记录方式取决于页面的 "charset" 设置。
*   当输入字符串传输到服务器时，会应用 URL 编码。
*   PHP CGI 模块在将输入字符串解析到 `$_REQUEST` 时应用 URL 解码。
*   我的建议是为你的输入页面使用 "charset=utf-8"。无需担心 HTML 实体转换。

[PHP 教程 - Herong 的教程示例](#part0001.xhtml)

∟ [从输入表单接收非 ASCII 字符](#part0178.xhtml)

∟ 从输入表单接收非 ASCII 字符的基本规则

本节介绍在不同步骤中如何管理非 ASCII 字符串的基本规则，以确保本地化文本字符串可以在 HTML 表单中输入，并被处理这些表单的 PHP 脚本正确接收。

正如你从前几章所见，当 PHP 脚本涉及基于 Web 的应用程序时，它们总是用在 Web 服务器之后。PHP 脚本预期生成 HTML 文档并将其传回 Web 服务器。非 ASCII 字符通过 PHP 脚本进入 HTML 文档大约有四种方式：a) 作为字符串字面量输入；b) 从 HTTP 请求接收；c) 从文件检索；d) 从数据库检索。

在本章中，我们将重点关注如何处理在 HTTP 请求中接收到的非 ASCII 字符。以下是该场景涉及的步骤：

```
C1. 键盘上的按键序列
      |
      |- 语言输入工具（可选）
      v
C2. 字节序列
      |
      |- Web 浏览器
      v
C3: HTTP 请求
      |
      |- Internet TCP/IP 连接
      v
C4. HTTP 请求
      |
      |- Web 服务器
      v
C5. CGI 变量和输入流
      |
      |- PHP CGI 接口
      v
C6. PHP 内置变量和输入流
```

根据我的经验，以下是与这些步骤相关的一些基本规则：

1. **页面编码** - 在 HTML 页面中输入的字符串将根据页面的 "charset" 设置立即进行编码。例如，如果页面具有 "charset=iso-8859-1"，双字节 Unicode 字符将被编码为 "`&#nnnnn;`" 形式的 HTML 实体，其中 "nnnnn" 代表 Unicode 字符代码的十进制值。例如，"`&#20320;`" 是作为 HTML 实体编码的 Unicode 字符。

如果页面具有 "charset=utf-8"，双字节 Unicode 字符将被编码为 UTF-8 字节序列。例如，"`\xE4\xBD\xA0`" 是作为 UTF-8 字节序列编码的 Unicode 字符。

2. **URL 编码** - Web 浏览器在将所有输入字符串作为 HTTP 请求的一部分发送到服务器时，会对其应用 "x-www-form-urlencoded"。URL 编码将所有非 ASCII 字节转换为 "`%xx`" 形式，"xx" 是字节的十六进制值。URL 编码还将特殊字符转换为 "`%xx`" 形式，空格字符 " " 除外。它将被转换为 "`+`"。

例如，如果页面 "charset=iso-8859-1"，一个 Unicode 字符被输入到页面中。它将立即被编码为 HTML 实体，如 "`&#20320;`"。发送到服务器时，它将再次被编码为 "`%26%2320320%3B`"。

如果页面具有 "charset=utf-8"，同一个 Unicode 字符被输入到页面中。它将立即被编码为 UTF-8 字节序列，如 "`\xE4\xBD\xA0`"。发送到服务器时，它将再次被编码为 "`%E4%BD%A0`"。

3. 从步骤 "C3" 到 "C4"，Internet 将保持 URL 编码的输入字符串原样。

4. 从步骤 "C4" 到 "C5"，Web 服务器将保持 URL 编码的输入字符串原样。

5. 从步骤 "C5" 到 "C6"，PHP CGI 接口为你做了一些有趣的事情：

*   如果输入是通过 GET 方法提交的，`$_SERVER['QUERY_STRING']` 将原样存储 URL 编码的输入字符串。
*   如果输入是通过 POST 方法提交的，URL 编码的输入字符串将保持在输入流中。
*   PHP 从 `$_SERVER['QUERY_STRING']` 或输入流中解析输入字符串到一个名为 `$_REQUEST` 的数组中。在此解析过程中，应用了 URL 解码。所有输入字符串被转换回它们在页面上输入时的样子。

6. 你想如何处理输入数据中的字符由你决定。你可以将它们输出回 HTML 文档，或存储在文件中。当然，你也可以应用任何你想要的转换。

在下面的章节中，我将展示一些示例 PHP 脚本来验证这些规则。

[PHP 教程 - Herong 的教程示例](#part0001.xhtml)

∟ [从输入表单接收非 ASCII 字符](#part0178.xhtml)

∟ 使用 GET 方法接收非 ASCII 字符

本节提供一个教程示例，说明如何在 HTML 表单中输入非 ASCII 字符并使用 GET 方法正确接收它们。HTML 表单使用 iso-8859-1 编码。

我们知道，可以使用两种方法在 HTML 表单中提交输入数据：GET 和 POST。让我们先使用 GET 方法。我编写了以下 PHP 脚本来演示非 ASCII 字符在上一节描述的步骤中是如何被管理的。
