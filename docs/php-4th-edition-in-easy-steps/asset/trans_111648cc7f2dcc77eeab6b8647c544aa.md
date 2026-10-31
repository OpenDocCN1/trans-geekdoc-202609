
# 使用 PHP 读取和写入文件

能够读取和写入位于 Web 服务器上的文件对于记录信息和提供页面内容非常有用。为了处理文件，必须首先使用 PHP `fopen()` 函数创建“filestream”对象。这需要两个参数来指定文件的名称或路径以及文件“mode”。文件模式决定要执行的操作性质，并将文件指针放置在文件内的合适位置：

| 文件模式 | 操作 |
| --- | --- |
| r | 打开已存在的文件进行读取<br>文件指针从文件开头开始 |
| w | 丢弃现有文件的所有内容或如果不存在则创建新文件<br>文件指针从文件开头开始 |
| a | 打开已存在的文件并保留所有内容<br>文件指针从文件末尾开始 |
| r+ | 打开文件以便读取或写入<br>文件指针从文件开头开始 |
| w+ | 打开文件以便写入或读取<br>丢弃现有文件的所有内容或如果不存在则创建新文件<br>文件指针从文件开头开始 |
| a+ | 打开文件以便读取或写入并保留所有内容<br>文件指针从文件末尾开始 |

![image](images/snake.jpg)

当作为 `fopen()` 函数的参数提供时，文件模式说明符必须出现在引号内。

如果创建文件流的尝试失败，最好始终使用 `die()` 函数提供替代方案。

![image](images/hot.jpg)

将解释性消息指定为 `die()` 函数的参数。

当文件流成功创建后，可以通过将文件流和字节大小指定为 `fread()` 函数的参数来读取文件。如果要读取整个文件，使用 `filesize()` 函数指定要读取的文件的字节大小会很方便。

完成任何文件操作后，必须通过将其指定为 `fclose()` 函数的参数来销毁文件流。

![image](images/pg125_1.jpg)

![image](images/pg125_2.jpg)

`manifesto.txt`

![image](images/1b.jpg)使用语句开始一个 PHP 脚本以尝试打开纯文本文件进行读取，或在失败时退出脚本

```php
<?php
$filestream = fopen('manifesto.txt', 'r') or die('Unable to open file!');
```

![image](images/commonb.jpg)

`read.php`

![image](images/2b.jpg)接下来，添加一条语句以在成功时读取文本文件并显示其全部内容

```php
echo fread($filestream, filesize('manifesto.txt'));
```

![image](images/3b.jpg)现在，记得关闭文件流

```php
fclose($filestream);
```

![image](images/4b.jpg)将文档保存到你的 Web 服务器的 `/htdocs` 目录中，命名为 `read.php`，与要读取的纯文本文件并列，然后通过 HTTP 打开页面以在浏览器窗口中查看文本文件内容

![image](images/pg125_3.jpg)

![image](images/forget.jpg)

与 HTML 文档中的 PHP 块不同，纯 PHP 脚本不需要关闭 `?>` 标签。

![image](images/forget.jpg)

请注意，此处的输出未保留行结束符——但第126页的示例[此处](#chapter08.xhtml#sec62) 保留了。

## 读取行

![image](images/pg126_1.jpg)

一旦创建了“filestream”对象，其内容就可以通过将文件流指定为 PHP `fgets()` 函数的参数一次读取一行。要读取每一行，可以在循环中重复调用此函数。`feof()` 函数可以确定何时到达文件末尾并结束循环：

![image](images/pg126_2.jpg)

![image](images/forget.jpg)

`feof()` 函数在到达文件末尾时返回 true。

![image](images/1b.jpg)使用语句开始一个 PHP 脚本以尝试打开纯文本文件进行读取，或在失败时退出脚本

```php
<?php
$filestream = fopen('manifesto.txt', 'r') or die('Unable to open file!');
```

![image](images/commonb.jpg)

`readlines.php`

![image](images/2b.jpg)接下来，添加一个循环以在成功时逐行读取文本文件并显示其全部内容

```php
while (!feof($filestream)) {
    echo fgets($filestream).'<br>';
}
```

![image](images/3b.jpg)现在，记得关闭文件流

```php
fclose($filestream);
```

![image](images/4b.jpg)将文档保存到你的 Web 服务器的 `/htdocs` 目录中，命名为 `readlines.php`，与要读取的纯文本文件并列，然后通过 HTTP 打开页面以查看文本文件行

![image](images/pg126_3.jpg)

![image](images/hot.jpg)

倒数第二行实际上并非空——它包含一个不可见的换行字符。

## 读取字符

![image](images/pg127_1.jpg)

一旦创建了“filestream”对象，其内容就可以通过将文件流指定为 PHP `fgetc()` 函数的参数一次读取一个字符。要读取每个字符，可以在循环中重复调用此函数。`fgetc()` 函数在到达文件末尾时会返回 false 并可结束循环：

![image](images/pg127_2.jpg)

![image](images/pg127_3.jpg)

`title.txt`

![image](images/1b.jpg)使用语句开始一个 PHP 脚本以尝试打开纯文本文件进行读取，或在失败时退出脚本

```php
<?php
$filestream = fopen('title.txt', 'r') or die('Unable to open file!');
```

![image](images/commonb.jpg)

`readchars.php`

![image](images/2b.jpg)接下来，添加一个循环以在成功时逐字符读取文本文件并显示其全部内容

```php
while ($char = fgetc($filestream)) {
    echo $char.' * ';
}
```

![image](images/3b.jpg)现在，记得关闭文件流

```php
fclose($filestream);
```

![image](images/4b.jpg)将文档保存到你的 Web 服务器的 `/htdocs` 目录中，命名为 `readchars.php`，与要读取的纯文本文件并列，然后通过 HTTP 打开页面以查看文件字符

![image](images/pg127_4.jpg)

![image](images/forget.jpg)

`fgetc()` 函数在流中没有更多字符可获取时返回 false。

## 写入文件

![image](images/pg128_1.jpg)

一旦创建了指定写入模式的“filestream”对象，即可创建文本文件。可以通过将文件流和文件名指定给 PHP `fwrite()` 函数将文本写入文件。为了格式化文本，还可以写入不可打印的不可见字符以创建换行和制表符间距：

| 字符 | 描述 |
| --- | --- |
| `\n` | 换行<br>向下移动到新行 |
| `\r` | 回车<br>移动到行首 |
| `\t` | 制表符<br>沿行移动到下一个制表位 |

![image](images/1b.jpg)使用语句开始一个 PHP 脚本以分配文本，包括用于格式化的不可打印字符

```php
<?php
$poem = "\r\n\tI never saw a man who looked";
$poem .= "\r\n\tWith such a wistful eye";
$poem .= "\r\n\tUpon that little tent of blue";
$poem .= "\r\n\tWhich prisoners call the sky";
```

![image](images/commonb.jpg)

`write.php`

![image](images/2b.jpg)接下来，为要写入的文件分配一个名称

```php
$filename = 'poem.txt';
```

![image](images/3b.jpg)尝试创建纯文本文件以供写入，或在失败时退出脚本

```php
$filestream = fopen($filename, 'w') or die('Unable to open file!');
```

![image](images/4b.jpg)写入文件并显示总共写入了多少字节的确认信息

```php
$num = fwrite($filestream, $poem);
if ($num) {
    echo "$num bytes written to $filename";
}
```

![image](images/5b.jpg)现在，记得关闭文件流

```php
fclose($filestream);
```

![image](images/snake.jpg)

包含不可打印字符的字符串必须用双引号括起来，以便 PHP 能解释它们。

![image](images/6b.jpg)将文档保存到你的 Web 服务器的 `/htdocs` 目录中，命名为 `write.php`，然后通过 HTTP 打开页面以查看文本文件已写入的确认信息

![image](images/pg129_1.jpg)

