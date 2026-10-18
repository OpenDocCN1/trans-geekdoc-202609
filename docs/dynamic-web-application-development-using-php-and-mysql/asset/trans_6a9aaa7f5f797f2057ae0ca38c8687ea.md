
## SUMMARY

在本章中，我们首先重新审视了字符串以及如何对其进行操作。我们举例说明了各种标准库函数，这些函数可实现字符串操作，例如反转字符串或对其进行加密。

然后我们介绍了数组的概念，并说明了如何在 PHP 中创建简单数组和多维数组。我们研究了数组需要如何转换为字符串才能通过表单传递，并最后研究了标准 PHP 库中的一些函数，这些函数可帮助我们操作数组，例如统计数组中数据的出现次数、对数组进行排序以及实现栈。

## References and further reading

Refsnes Data. PHP 字符串函数. http://www.w3schools.com/php/php_ref_string.asp
Tizag.com PHP 教程：数组. http://www.tizag.com/phpT/arrays.php

## Files, Cookies, Sessions and Email

### LEARNING OBJECTIVES

- 了解什么是文件以及如何打开和关闭文件
- 了解如何从文件中读取数据
- 了解如何创建新文件
- 了解如何使用 Cookie
- 了解如何使用 Session
- 了解如何从表单上传文件到服务器
- 了解如何从 PHP 语言中生成电子邮件消息
- 了解如何生成 (X)HTML 电子邮件消息

### INTRODUCTION

在本章中，我们集中讨论与“文件”有关的所有内容。我们首先解释什么是文件以及它们如何被创建。我们说明了如何读取文件中的数据，以及文件如何成为长期存储信息的有效手段。我们还介绍了如何操作简单文件，并研究了 PHP 提供的一些使操作更轻松的函数。然后我们研究 Cookie 和 Session 在 PHP 环境中的作用，并解释虽然它们是文件，但具有非常具体且重要的作用。

我们研究如何使用表单界面将文件上传到服务器。文件上传非常重要，如果你想实现基于表单的远程文档共享系统。接下来我们介绍电子邮件的概念以及如何在 PHP 中创建电子邮件。虽然你可能不会把电子邮件看作文件，但它是在 PHP 脚本之外创建和存储的文档，因此我们认为在本章中包含电子邮件是合适的。

### 12.1 Files

从物理上讲，文件是可以被操作的有序字符集合。计算机将文件用于各种不同的用途，因此从逻辑上讲，文件可以被视为数据记录集合、计算机程序、电子邮件或文字文档。大多数情况下，计算机使用文件将信息存储在存储设备（如磁盘驱动器）上以便以后访问。PHP 包含大量用于文件操作和创建的函数。我们首先来看如何打开和关闭文件。

### Opening and Closing a File

在我们能够读取文件内容或更改/添加数据之前，需要先打开文件。打开文件会在 PHP 脚本和文件本身之间建立一个链接。这种链接通过一种称为资源（resource）的特殊类型来维护。PHP 使用名为 fopen() 的函数来打开文件：

```
filestream = fopen (filename, mode);
```

fopen() 函数需要打开的文件名和一个指示打开文件模式的字符串。该函数返回指向已打开文件的流资源。文件可以以多种不同的模式打开，这些模式列在表 12.1 中。

好吧，文件指针是什么？文件指针存储在打开文件时返回的资源流中。该指针“指向”文件中的某个位置。例如，当文件被打开以读取其内容时，文件指针位于文件的开头，并在每次读取时在文件中移动。对于以末尾写入方式打开的文件，文件指针指向文件的末尾，因为新数据通常写入此处。

PHP 允许你在本地机器上以及远程机器上打开文件（如果安全权限允许）。远程文件可通过 HTTP 或 FTP 连接访问。

### TABLE 12.1 File open modes

| 模式 | 描述 |
|------|-------------|
| r | 仅用于读取；将文件指针置于文件开头。 |
| r+ | 用于读取和写入；将文件指针置于文件开头。 |
| w | 仅用于写入；将文件指针置于文件开头并将文件截断为零长度；如果文件不存在，尝试创建它。 |
| w+ | 用于读取和写入；将文件指针置于文件开头并将文件截断为零长度；如果文件不存在，尝试创建它。 |
| a | 仅用于写入；将文件指针置于文件末尾；如果文件不存在，尝试创建它。 |
| a+ | 用于读取和写入；将文件指针置于文件末尾；如果文件不存在，尝试创建它。 |
| x | 创建并仅用于写入；将文件指针置于文件开头；如果文件已存在，fopen() 函数调用失败。 |
| X+ | 创建并用于读取和写入；将文件指针置于文件开头；如果文件已存在，fopen() 函数调用失败。 |

### FIGURE 12.1 File pointers

![](img/b2471264f405d17994ef173e4b9cec92_362_0.png)

如果文件名以 http:// 开头，则会打开到指定服务器的 HTTP 连接并返回指向请求文件的指针。

图 12.1 说明了文件指针的概念，其中文件以两种模式打开。

一旦完成对文件的访问，应关闭它以释放内存并通知操作系统你已完成对文件的使用。在 PHP 中，使用 fclose() 函数关闭文件：

```
fclose (filestream);
```

fclose() 函数需要要关闭的文件的资源流，并根据是否能够关闭文件返回 true 或 false。以下脚本说明了这两个函数的使用，目前这是一个相当无用的示例（我们稍后会稍作改进）：

```
<?php
// File: example12-1.php

$fileTextFile = fopen ("text.txt",'a');

if (!fclose($fileTextFile) )
    echo "<p>Error closing file!</p>";
else
    echo "<p>File Closed</p>";
?>
```

上述脚本没有输出（除非在打开或关闭文件时出现问题）。

| NOTE | 如果你在 UNIX 系统上运行，则需要确保你对正在写入的目录具有正确的权限。 |

### Reading from a file

可以使用 fgetc() 函数从文件中读取单个字符。该函数的语法如下：

```
character = fgetc (filestream);
```

fgetc() 函数接收要读取的文件的文件流资源，并返回从文件中读取的字符。

在继续之前，让我们创建一个文本文件用于示例。创建一个包含以下文本的简单文本文件，并将其保存为 'files' 子目录中的 'text.txt'：

- 1. The quick brown fox jumped over the lazy dog.
- 2. The quick brown fox jumped over the lazy dog.
- 3. The quick brown fox jumped over the lazy dog.
- 4. The quick brown fox jumped over the lazy dog.

以下脚本使用 fgetc() 函数读取并显示 'text.txt' 文件的第一个字符：

```
<?php
// File: example12-2.php

$fileTextFile = fopen ("files/text.txt",'r');

$strChar = fgetc($fileTextFile);
echo "<p>$strChar</p>";

if (!fclose($fileTextFile) )
    echo "<p>Error closing file!</p>";
?>
```

上述脚本的输出为：

1

要读取整个文件，我们需要实现一个循环结构。我们还需要某种方法来确定文件的末尾。feof() 函数可用于检查文件指针是否位于文件末尾。该函数如下所示：

```
feof (filestream);
```

该函数需要一个文件流参数，并根据是否已到达文件末尾返回 true 或 false。让我们修改之前的脚本以使用此函数并读取整个文件：

```
<?php
// File: example12-3.php

$fileTextFile = fopen ("files/text.txt",'r');
```
