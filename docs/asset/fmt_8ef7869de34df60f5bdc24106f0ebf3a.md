
在完成上述示例后，你应该已经熟悉如何处理任何单一语言的非 ASCII 字符了。你可以选择使用 UTF-8 或特定语言的编码。

如果你想在单个 HTML 文档中包含多种语言的字符，则必须使用 UTF-8 编码。以下是创建支持单个 HTML 文档中多种语言的 UTF-8 HTML 文档的步骤。

1. 在 Windows 系统上，运行 `Start > All Programs > Accessories > Notepad`。

2. 在记事本中，输入以下 HTML 文档：

```html
<html>
<!-- HelloUtf8MultiLanguages.html
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
-->
<meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
<body>
<b>Test</b><br/>
English: Hello world!<br/>
Spanish: ¡Hola mundo!<br/>
Korean: 여보세요 세계 !<br/>
Chinese: 你好世界!<br/>
</body>
</html>
```

3. 不要尝试自己输入那些问候语。访问 Google 语言工具网站 `http://www.google.com/language_tools`。你可以输入 "Hello world!" 并将其翻译成其他语言。在翻译输出页面上，只需复制那些翻译并粘贴回记事本。这不会造成损坏，因为 Google 网站、Windows IE 和记事本都支持 UTF-8。

4. 选择菜单 `File > Save as`。输入文件名 `HelloUtf8MultiLanguages.html`。在 `Encoding` 字段选择 "UTF-8" 并点击 `Save` 按钮。

5. 将 `HelloUtf8MultiLanguages.html` 复制到 `c:\apache\htdocs`。确保 Internet Information Service 正在运行本地默认网站。

6. 现在运行 Internet Explorer (IE) 并打开 `http://localhost/HelloUtf8MultiLanguages.html`。你应该能看到所有字符都正确显示。

7. 在 IE 窗口中，选择菜单“查看”>“编码”。你应该能看到已选中 UTF-8。

# PHP 教程 - Herong 的教程示例

## 在 PHP 脚本字符串字面量中使用非 ASCII 字符

本章提供关于 PHP 脚本中非 ASCII 字符的教程示例和说明。主题包括：在 PHP 脚本中将非 ASCII 字符作为字符串字面量使用的基本规则；使用 UTF-8 和 ISO-8859-1 编码处理法文字符的示例；使用 UTF-8 和 GB2312 编码处理中文字符的示例。

> HTML 文档中使用非 ASCII 字符的基本规则
>
> 字符串字面量中的法文字符 - UTF-8 编码
>
> HTML 文档中的法文字符 - ISO-8859-1 编码
>
> 字符串字面量中的中文字符 - UTF-8 编码
>
> 字符串字面量中的中文字符 - GB2312 编码
>
> 字符串字面量中的多语言字符

### 要点：

*   PHP 字符串数据类型被定义为字节序列。
*   PHP 字符串字面量可以包含几乎任何编码方案下的几乎所有非 ASCII 字符。
*   编码方案的最佳选择是 UTF-8。
*   在 PHP 脚本中使用 UTF-8 编码需要一个良好的 UTF-8 兼容编辑器。
*   PHP 脚本通过 `print()` 函数生成 HTML 文档，这是一个字节流输出函数，默认不提供编码转换。

## 在 PHP 脚本字符串字面量中使用非 ASCII 字符

### HTML 文档中使用非 ASCII 字符的基本规则

本节介绍关于非 ASCII 字符串在不同步骤中应如何管理的基本规则，以确保本地化文本字符串可用于 PHP 脚本字符串字面量，并在浏览器窗口中正确显示。

正如你从前几章所见，当 PHP 脚本涉及基于 Web 的应用程序时，它们总是用于 Web 服务器之后。PHP 脚本预期生成 HTML 文档并将其传回 Web 服务器。非 ASCII 字符通过 PHP 脚本进入 HTML 文档大约有四种方式：a) 作为字符串字面量输入；b) 从 HTTP 请求接收；c) 从文件检索；d) 从数据库检索。

在本章中，我们将重点关注如何在 PHP 脚本中将非 ASCII 字符作为字符串字面量包含进去。以下是该场景涉及的步骤：

```
A1. 键盘按键序列
      |
      |- 文本编辑器
      v
A2. PHP 文件
      |
      |- PHP CGI 引擎
      v
A3. HTML 文档
```

根据我的经验，以下是与这些步骤相关的一些基本规则：

1.  你必须确定在 PHP 脚本文件中使用的字符编码方案。对于大多数语言，你有两个选项：a: 使用特定于该语言的编码方案；b: 使用 Unicode 方案。例如，对于中文字符，你可以使用 `GB2312`（简体中文字符方案）或 `UTF-8`（Unicode 字符方案）。我过去建议用“a”。但今天，我建议用“b”，因为 Unicode 方案可以支持所有语言的所有字符。

2.  从步骤“A1”到“A2”，你需要选择一个支持你已决定的编码方案的优秀文本编辑器。此步骤的最终目标很简单——字符串字面量中的字符必须使用决定的编码方案存储在 PHP 文件中。不要低估这一步的难度。它可能会让人非常沮丧，因为大多数计算机键盘仅支持字母。你可能不得不使用特定语言的输入法软件将字母转换为特定语言的字符。编辑器有时也可能在内存中以一种编码方案存储字符，而在保存文件到硬盘时提供不同的编码方案。

3.  在 PHP 中，字符串数据类型被定义为字节序列，类似于 C 语言。这与 Java 语言不同，后者将字符串数据类型定义为 Unicode 字符序列。PHP 中的字符串字面量也被视为字节序列。这是一个很好的特性。它允许我们以几乎任何编码方案输入非 ASCII 字符。

4.  所有 PHP 内置字符串函数都假设字符串是字节序列。例如，`strlen()` 返回给定字符串的字节数，而不是特定语言的字符数。要将字符串作为字符序列进行管理，我们需要使用多字节字符串函数 `mb_*()`。

5.  从步骤“A2”到“A3”，HTML 文档主要通过 `print()` 函数从 PHP 脚本生成。`print()` 函数会将指定字符串中的每个字节完美地复制到 HTML 文档中。这保证了以任何编码方案编码的任何非 ASCII 字符都将被正确复制到 HTML 文档中。同样，这与 JSP 页面不同，后者如果你使用基于字符的输出流函数，字符串将根据指定的编码方案转换为字节流。

6.  如果你确实想在 `print()` 函数调用期间将一种编码方案转换为另一种编码方案，可以使用 `mb_output_handler` 作为输出缓冲区上的回调函数：`ob_start("mb_output_handler")`。

## 在 PHP 脚本字符串字面量中使用非 ASCII 字符

### 字符串字面量中的法文字符 - UTF-8 编码

本节提供一个教程示例，说明如何使用 Unicode UTF-8 编码在 PHP 字符串字面量中输入和使用法文字符。PHP 脚本文件应以 UTF-8 格式存储。

首先，让我们先在 UTF-8 编码中试用一些法文字符。

1.  在 Windows 系统上，运行“开始”>“所有程序”>“附件”>“记事本”。

2.  在记事本中，输入以下 PHP 脚本：

```php
<?php
#### HelpUtf8French.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
#
   print('<html>');
   print('<meta http-equiv="Content-Type"'.
      ' content="text/html; charset=utf-8"/>');
   print('<body>');
   print('<b>Help</b><br/>');
   print('English: System load is very high.<br/>');
   print('French: L\'utilisation de système est très haute.<br/>');
   print('</body>');
   print('</html>');
?>
```

3.  要输入法文字符“带重音符号的 e (è)”，可以运行“开始”>“所有程序”>“系统工具”>“字符映射表”。在字符映射表上选择“带重音符号的 e”。点击“选择”按钮，然后点击“复制”按钮。返回记事本并按 `Ctrl-V` 将“带重音符号的 e”粘贴到你的 PHP 脚本中。

4.  选择菜单“文件”>“另存为”。输入文件名 `HelpUtf8French.php`。在“编码”字段中选择“UTF-8”，然后点击“保存”按钮。

5.  将 `HelpUtf8French.php` 复制到 `c:\apache\htdocs`。确保你的 Internet 信息服务正在运行本地默认网站。

6.  现在运行 Internet Explorer (IE) 并打开 `http://localhost/HelpUtf8French.php`。你应该能看到法文字符正确显示，如下所示：

```
Help
English: System load is very high.
French: L'utilisation de système est très haute.
```

7.  在 IE 窗口中，选择菜单“查看”>“编码”。你应该能看到已选中 UTF-8。

另一件你应该知道的有趣事情是记事本如何存储 UTF-8 文件。当你使用 UTF-8 编码在记事本中存储文件时，它会在文件开头插入一个 UTF-8 标记（3 字节）。在命令窗口中使用“type”命令，你将看到这一点：

### HTML 文档中的法文字符 - ISO-8859-1 编码

本节提供了一个教程示例，说明如何使用 ISO-8859-1 编码在 PHP 字符串字面量中输入和使用法文字符。PHP 脚本文件应以 ANSI 格式存储。

现在我们知道如何让法文字符在 UTF-8 编码方案的 PHP 字符串字面量中工作了。接下来让我们看看如何让它们在 ISO-8859-1 编码方案中工作。

1. 在 Windows 系统上，运行“开始”>“所有程序”>“附件”>“记事本”。

2. 在记事本中，输入以下 PHP 脚本：

```php
<?php
#### HelpIsoFrench.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
#
   print('<html>');
   print('<meta http-equiv="Content-Type"'.
      ' content="text/html; charset=iso-8859-1"/>');
   print('<body>');
   print('<b>Help</b><br/>');
   print('English: System load is very high.<br/>');
   print('French: L\'utilisation de système est très haute.<br/>');
   print('</body>');
   print('</html>');
?>
```

3. 要输入法文字符“带重音符的 e”，可以运行“开始”>“所有程序”>“系统工具”>“字符映射表”。在字符映射表中选择“带重音符的 e”。点击“选择”按钮，然后点击“复制”按钮。返回记事本并按 `Ctrl-V` 将“带重音符的 e”粘贴到 PHP 脚本中。

4. 选择菜单“文件”>“另存为”。输入文件名 `HelpIsoFrench.php`。在“编码”字段中选择“ANSI”，然后点击“保存”按钮。请注意，ANSI 是微软定义并在 Windows 系统上使用的编码方案。ANSI 包含的字符比 ISO-8859-1 多。但它与 ISO-8859-1 兼容。

5. 将 `HelpIsoFrench.php` 复制到 `c:\apache\htdocs`。确保 Internet 信息服务正在运行本地默认网站。

6. 现在使用 `http://localhost/HelpIsoFrench.php` 运行 Internet Explorer (IE)。您应该会看到法文字符正确显示，如下所示：

```
Help
English: System load is very high.
French: L'utilisation de système est très haute.
```

7. 在 IE 窗口中，选择菜单“查看”>“编码”。您应该会看到选中了“西欧语言”。同样，“西欧语言”是 ISO-8859-1 的另一个名称。

很简单，对吧？我们甚至可以让它更简单。您可以移除 `HelpIsoFrench.html` 中的 `<meta>` 标签设置。法文字符仍将在 IE 窗口中显示。这是因为 ISO-8859-1 是 IE 的默认编码方案。

### 字符串字面量中的中文字符 - UTF-8 编码

本节提供了一个教程示例，说明如何使用 Unicode UTF-8 编码在 PHP 字符串字面量中输入和使用中文字符。PHP 脚本文件应以 UTF-8 格式存储。

现在让我们来处理中文字符。它们绝对比法文字符更难处理。我的第一个示例将向您展示如何使用 UTF-8 编码在 PHP 脚本中处理中文字符。

1. 在 Windows 系统上，运行“开始”>“所有程序”>“附件”>“记事本”。

2. 在记事本中，输入以下 HTML 文档：

```php
<?php
#### HelpUtf8Chinese.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
#
   print('<html>');
   print('<meta http-equiv="Content-Type"'.
      ' content="text/html; charset=utf-8"/>');
   print('<body>');
   print('<b>说明</b><br/>');
   print('这是一份非常间单的说明书…<br/>');
   print('</body>');
   print('</html>');
?>
```

3. 正如我在这本书前面提到的，输入中文字符并非易事。您需要使用中文 Windows 系统，或在非中文 Windows 系统上使用中文输入工具。如果您没有任何中文输入工具，可以直接访问雅虎中文网站 `http://www.yahoo.com.cn/`，复制一些中文字符，然后粘贴到记事本中。雅虎中文网站采用 UTF-8 编码。

4. 选择菜单“文件”>“另存为”。输入文件名 `HelpUtf8Chinese.php`。在“编码”字段中选择“UTF-8”，然后点击“保存”按钮。

5. 将 `HelpUtf8Chinese.php` 复制到 `c:\apache\htdocs`。确保 Internet 信息服务正在运行本地默认网站。

6. 现在使用 `http://localhost/HelpUtf8Chinese.php` 运行 Internet Explorer (IE)。您应该会看到中文字符正确显示。

7. 在 IE 窗口中，选择菜单“查看”>“编码”。您应该会看到选中了 UTF-8。

### 字符串字面量中的中文字符 - GB2312 编码

本节提供了一个教程示例，说明如何使用 GB2312 编码在 PHP 字符串字面量中输入和使用中文字符。PHP 脚本文件应以 GB2312 格式存储。

我想我们已经准备好测试在 GB2312 编码方案的 PHP 脚本中的中文字符了。

1. 这一次，我们不能使用记事本，因为记事本与 GB2312 编码不兼容。它实际上会将 GB2312 编码转换为 UTF-8 编码。所以不要使用记事本。

您需要获取另一个文本编辑器，如 Jext，来帮助您以 GB2312 编码输入中文字符。

2. 在一个好的文本编辑器中，输入以下 HTML 文档：

```php
<?php
#### HelpGb2312Chinese.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
#
   print('<html>');
   print('<meta http-equiv="Content-Type"'.
      'content="text/html; charset=gb2312"/>');
   print('<body>');
   print('<b>??</b><br/>');
   print("????????????<br/>");
   print('</body>');
   print('</html>');
?>
```

当我将此 HTML 文档复制到本书中时，我不得不将所有 GB2312 编码的中文字符替换为“?”，因为我的书是用 UTF-8 编码方案编写的 HTML 文档。要遵循我的教程，每当您看到“?”时，只需输入任意中文字符即可。

3. 以 GB2312 编码输入中文字符也需要一些中文输入工具。如果您没有任何中文输入工具，可以直接访问我的 GB2312 页面 `https://www.herongyang.com/gb2312_gb/`，打开页面的源代码，复制一些中文字符，然后粘贴到编辑器中。我的 GB2312 页面采用 GB2312 编码。警告，不要从 IE 浏览器窗口复制中文字符。浏览器窗口的复制功能假设为 UTF-8 编码，会损坏复制的字符。
