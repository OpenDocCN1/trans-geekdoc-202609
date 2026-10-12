
# 本章提供了关于 HTML 文档中非 ASCII 字符的教程示例和说明

主题包括在 HTML 文档中使用非 ASCII 字符的基本规则；使用 UTF-8 和 ISO-8859-1 编码的法文字符示例；使用 UTF-8 和 GB2312 编码的中文字符示例。

## 要点

* 在一个 HTML 文档中只能使用一种编码方案。您应该使用 `<meta>` 标签来指定编码名称。

## 在 HTML 文档中使用非 ASCII 字符的基本规则

本节介绍了在不同步骤中应如何管理非 ASCII 字符串的基本规则，以确保本地化文本字符串可在 HTML 文档中使用，并在浏览器窗口中正确显示。

正如您从前几章所见，基于 Web 的应用程序总是将信息作为 HTML 文档传递给用户界面。应用程序既可以从文件系统获取静态 HTML 文档，也可以从 PHP 脚本生成动态 HTML 文档。

首先，让我们集中讨论如何在静态 HTML 文档中处理非 ASCII 字符。以下是录入 HTML 文档并将其传递给用户界面所涉及的步骤和技术：

```
H1. 来自键盘的按键序列
      |
      |- 文本编辑器
      v
H2. HTML 文档
      |
      |- Web 服务器
      v
H3. HTTP 响应
      |
      |- Internet TCP/IP 连接
      v
H4. HTTP 响应
      |
      |- Web 浏览器
      v
H5. 屏幕上的可视字符
```

根据我的经验，以下是与这些步骤相关的一些基本规则：

1. 您必须首先确定 HTML 文档中要使用的字符编码方案。对于大多数人类书写语言，您有两个选项：a) 使用特定于该语言的编码方案；b) 使用 Unicode 方案。例如，对于中文字符，您可以使用 `GB2312`（一种简体中文字符方案）或 `UTF-8`（一种 Unicode 字符方案）。我过去建议选“a”。但从现在起，我建议选“b”，因为 Unicode 方案可以支持所有语言的所有字符。

2. PHP 似乎是一门不错的语言。字符串数据类型被定义为字节序列，类似于 C 语言。这与 Java 语言不同，后者将字符串定义为 Unicode 字符序列。PHP 中的字符串字面量可以接受任意字节序列。因此，您可以使用任何编码方案将非 ASCII 字符作为 PHP 字符串字面量输入。

3. 从步骤 `H1` 到 `H2`，您需要选择一款支持您所选编码方案的优秀文本编辑器。此步骤的最终目标很简单——HTML 文档中的字符必须使用所选编码方案存储在文件中。不要低估这一步的难度。它可能会让人非常沮丧，因为大多数计算机键盘仅支持字母。您可能不得不使用特定语言的输入法软件将字母转换为特定语言的字符。编辑器有时也可能在内存中以一种编码方案存储字符，而在保存文件到硬盘时提供另一种编码方案供您选择。

4. 从步骤 `H3` 到 `H4`，是 Internet 将数据从 Web 服务器发送到 Web 浏览器的工作。HTTP 响应将原样传输给浏览器。附加在 HTTP 响应中的 HTML 文档中的字符也将保持原样。

5. 从步骤 `H4` 到 `H5`，浏览器打开接收到的 HTML 文档，并将编码字符显示为特定语言的书写字符。为此，浏览器需要您的帮助。第一项帮助是将 HTML 文档中使用的字符编码名称 `charset` 指定为 `<meta>` 标签。第二项帮助是确保浏览器可以访问为指定编码方案设计的字符字体文件。

如果在 `<meta>` 标签中未指定字符编码名称，某些浏览器将尝试根据 HTML 文档内容检测编码方案。如果不成功，浏览器将使用默认编码方案。例如，Internet Explorer (IE) 使用 `Western European`（西欧语言）作为默认编码方案。`Western European` 似乎是指 `ISO-8859-1` 标准。

## HTML 文档中的法文字符 - UTF-8 编码

本节提供了一个教程示例，说明如何使用 Unicode UTF-8 编码在 HTML 文档中输入和使用法文字符。HTML 文档应包含带有 `charset=utf-8` 的 meta 标签，并以 UTF-8 格式存储。

让我们先在 UTF-8 编码中尝试一些法文字符。

1. 在 Windows 系统上，运行 `开始 > 所有程序 > 附件 > 记事本`。

2. 在记事本中，输入以下 HTML 文档：

```html
<html>
<!-- HelpUtf8French.html
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
-->
<meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
<body>
<b>Help</b><br/>
English: System load is very high.<br/>
French: L'utilisation de système est très haute.<br/>
</body>
</html>
```

3. 要输入法文字符 `e with grave`（带重音符的 e），可以运行 `开始 > 所有程序 > 系统工具 > 字符映射表`。在字符映射表中选择 `e with grave`。单击“选择”按钮，然后单击“复制”按钮。返回记事本并按 `Ctrl-V` 将 `e with grave` 粘贴到 HTML 文档中。

4. 选择菜单 `文件 > 另存为`。输入文件名 `HelpUtf8French.html`。在“编码”字段中选择 `UTF-8`，然后单击“保存”按钮。

5. 将 `HelpUtf8French.html` 复制到 `c:\apache\htdocs`。确保您的 Internet 信息服务正在运行本地默认网站。

6. 现在使用 `http://localhost/HelpUtf8French.html` 运行 Internet Explorer (IE)。您应该会看到法文字符正确显示，如下所示：

```
Help
English: System load is very high.
French: L'utilisation de système est très haute.
```

7. 在 IE 窗口中，选择菜单 `查看 > 编码`。您应该会看到已选中 UTF-8。

请注意我是如何指定 `<meta>` 标签的：

```html
<meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
```

另一件您应该了解的有趣事情是记事本如何存储 UTF-8 文件。当您使用 UTF-8 编码在记事本中存储文件时，它会在文件开头插入一个 UTF-8 标记（3 字节）。在命令窗口中使用 `type` 命令，您将看到这一点：

```
herong> type HelpUtf8French.html

<html>
<!-- HelpUtf8French.html
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
-->
<meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
<body>
<b>Help</b><br/>
English: System load is very high.<br/>
French: L'utilisation de système est très haute.<br/>
</body>
</html>
```

UTF-8 标记的十六进制值为 `0xEFBBBF`。Web 服务器会将其发送给客户端。IE 浏览器不会在页面上显示它，但如果需要，它会用它来检测编码方案。不确定其他浏览器对此标记的行为会如何。

## HTML 文档中的法文字符 - ISO-8859-1 编码

本节提供了一个教程示例，说明如何使用 Unicode ISO-8859-1 编码在 HTML 文档中输入和使用法文字符。HTML 文档应包含带有 `charset=ISO-8859-1` 的 meta 标签，并以 ANSI 格式存储。

现在我们知道了如何在 UTF-8 编码方案中使法文字符在 HTML 文档中正常工作。接下来让我们看看如何在 ISO-8859-1 编码方案中在 HTML 文档中使用法文字符。

1. 在 Windows 系统上，运行 `开始 > 所有程序 > 附件 > 记事本`。

2. 在记事本中，输入以下 HTML 文档：

```html
<html>
<!-- HelpIsoFrench.html
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
-->
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1"/>
<body>
<b>Help</b><br/>
English: System load is very high.<br/>
French: L'utilisation de système est très haute.<br/>
</body>
</html>
```

3. 要输入法文字符 "e with grave"，可以运行 `Start > All Programs > System Tools > Character Map`。在字符映射表中选择 "e with grave"。点击 `Select` 按钮，然后点击 `Copy` 按钮。回到记事本并按 `Ctrl-V` 将 "e with grave" 粘贴到 HTML 文档中。

4. 选择菜单 `File > Save as`。输入文件名 `HelpIsoFrench.html`。在 `Encoding` 字段选择 "ANSI" 并点击 `Save` 按钮。注意 ANSI 是微软定义并在 Windows 系统上使用的编码方案。ANSI 包含的字符比 ISO-8859-1 多，但它与 ISO-8859-1 兼容。

5. 将 `HelpIsoFrench.html` 复制到 `c:\apache\htdocs`。确保 Internet Information Service 正在运行本地默认网站。

6. 现在使用 `http://localhost/HelpIsoFrench.html` 运行 Internet Explorer (IE)。你应该能看到法文字符正确显示，如下所示：

```
Help
English: System load is very high.
French: L'utilisation de système est très haute.
```

7. 在 IE 窗口中，选择菜单 `View > Encoding`。你应该看到选中了 "Western European"。同样，"Western European" 是 ISO-8859-1 的另一个名称。

很简单，对吧？我们可以让它更简单。你可以移除 `HelpIsoFrench.html` 中的 `<meta>` 标签设置。法文字符仍会在 IE 窗口中显示。这是因为 ISO-8859-1 是 IE 的默认编码方案。

## 中文字符 - UTF-8 编码

本节提供了一个教程示例，说明如何使用 Unicode UTF-8 编码在 HTML 文档中输入和使用中文字符。HTML 文档应包含一个带有 `charset=utf-8` 的 meta 标签，并以 UTF-8 格式存储。

现在让我们来处理中文字符。它们绝对比法文字符难处理得多。我的第一个示例展示了如何使用 UTF-8 编码处理 HTML 文档中的中文字符。

1. 在 Windows 系统上，运行 `Start > All Programs > Accessories > Notepad`。

2. 在记事本中，输入以下 HTML 文档：

```html
<html>
<!-- HelpUtf8Chinese.html
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
-->
<meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
<body>
<b>说明</b><br/>
这是一份非常间单的说明书…<br/>
</body>
</html>
```

3. 正如我在这本书前面提到的，输入中文字符并非易事。你需要使用中文 Windows 系统，或在非中文 Windows 系统上使用中文输入工具。如果你没有任何中文输入工具，可以直接访问雅虎中文网站 `http://www.yahoo.com.cn/`，复制一些中文字符，然后粘贴到记事本中。雅虎中文网站采用 UTF-8 编码。

4. 选择菜单 `File > Save as`。输入文件名 `HelpUtf8Chinese.html`。在 `Encoding` 字段选择 "UTF-8" 并点击 `Save` 按钮。

5. 将 `HelpUtf8Chinese.html` 复制到 `c:\apache\htdocs`。确保 Internet Information Service 正在运行本地默认网站。

6. 现在使用 `http://localhost/HelpUtf8Chinese.html` 运行 Internet Explorer (IE)。你应该能看到中文字符正确显示。

7. 在 IE 窗口中，选择菜单 `View > Encoding`。你应该看到选中了 UTF-8。

## 中文字符 - GB2312 编码

本节提供了一个教程示例，说明如何使用 GB2312 编码在 HTML 文档中输入和使用中文字符。HTML 文档应包含一个带有 `charset=GB2312` 的 meta 标签，并以 GB2312 格式存储。

我们准备好测试使用 GB2312 编码方案的 HTML 文档中的中文字符了。

1. 这次我们不能使用记事本，因为记事本与 GB2312 编码不兼容。它实际上会将 GB2312 编码转换为 UTF-8 编码。所以不要使用记事本。

你需要获取另一个文本编辑器，如 Jext，来帮助你以 GB2312 编码输入中文字符。

2. 在一个好的文本编辑器中，输入以下 HTML 文档：

```html
<html>
<!-- HelpGb2312Chinese.html
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
-->
<meta http-equiv="Content-Type" content="text/html; charset=gb2312"/>
<body>
<b>??</b><br/>
????????????<br/>
</body>
</html>
```

当我将此 HTML 文档复制到本书中时，我必须用 "?" 替换所有 GB2312 编码的中文字符，因为我的书是用 UTF-8 编码方案编写的 HTML 文档。要遵循我的教程，每当你看到 "?" 时，只需输入任意中文字符即可。

3. 以 GB2312 编码输入中文字符也需要一些中文输入工具。如果你没有任何中文输入工具，可以直接访问我的 GB2312 页面 `https://www.herongyang.com/gb2312_gb/`，打开页面源代码，复制一些中文字符，然后粘贴到编辑器中。我的 GB2312 页面采用 GB2312 编码。警告：不要从 IE 浏览器窗口复制中文字符。浏览器窗口的复制功能假设为 UTF-8 编码，会损坏复制的字符。

4. 选择菜单 `File > Save as`。输入文件名 `HelpGb2312Chinese.html` 并点击 `Save` 按钮。

5. 将 `HelpGb2312Chinese.html` 复制到 `c:\apache\htdocs`。确保 Internet Information Service 正在运行本地默认网站。

6. 现在使用 `http://localhost/HelpGb2312Chinese.html` 运行 Internet Explorer (IE)。你应该能看到中文字符正确显示。

7. 在 IE 窗口中，选择菜单 `View > Encoding`。你应该看到选中了 Gb2312。

仍然不难做，对吧？关键点是使用兼容 GB2312 的编辑器。

## HTML 文档中的多语言字符

本节提供了一个教程示例，说明如何使用 Unicode UTF-8 编码在单个 HTML 文档中输入和使用多种语言的字符。
