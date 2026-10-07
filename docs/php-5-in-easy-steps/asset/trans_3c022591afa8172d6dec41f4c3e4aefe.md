

# 打开与关闭文件

PHP 的 fopen() 函数用于从文件中读取文本、向文件中写入文本以及向文件追加文本。它需要两个参数：文件名和操作模式。

文件模式可以指定为下表中的六个选项之一：

| 模式 | 目的 |
|---|---|
| r | 只读模式打开文件。将文件指针放在文件开头。 |
| r+ | 读写模式打开文件。将文件指针放在文件开头。 |
| w | 只写模式打开文件。将文件指针放在文件开头并将文件截断为零长度。如果文件不存在，将尝试创建它。 |
| w+ | 读写模式打开文件。将文件指针放在文件开头并将文件截断为零长度。如果文件不存在，将尝试创建它。 |
| a | 只写模式打开文件。将文件指针放在文件末尾。如果文件不存在，将尝试创建它。 |
| a+ | 读写模式打开文件。将文件指针放在文件末尾。如果文件不存在，将尝试创建它。 |

![](img/7faa63a7fa0add8f53300594ebae949f_86_0.png)

如果尝试打开文件失败，fopen() 返回 false，否则它返回一个引用该文件的文件指针。在对打开的文件进行更改后，使用 fclose() 函数关闭它以断开文件指针。fclose() 函数需要文件指针作为参数，并在关闭成功时返回 true，失败时返回 false。

下一页的示例演示了如何打开文件、读取文件，然后正确关闭文件。

# 读取文件

可以使用 fopen() 函数打开文件，它需要两个参数：指定文件名和上一页列出的文件模式之一。fopen() 函数返回一个引用该文件的文件指针，可用于读取文件内容。

然后可以使用 fread() 函数读取文件，该函数也需要两个参数：文件指针和以字节为单位的文件长度。

可以使用 filesize() 函数找到文件的长度，它接受文件名作为参数并返回以字节为单位的文件大小。

因此，使用 PHP 读取文件的技术遵循以下模式：

- 使用 fopen() 打开文件
- 使用 filesize() 获取文件长度
- 使用 fread() 读取文件内容
- 使用 fclose() 关闭文件

以下示例将文本文件的内容赋值给一个变量，然后在页面上显示这些内容。

![](img/7faa63a7fa0add8f53300594ebae949f_87_0.png)

```html
<html><head><title>Reading a file</title></head>
<body>
<?php
$filename = "quote.txt";
$file = fopen($filename, "r");
$filesize = filesize($filename);
$text = fread($file, $filesize);
fclose($file);
echo("File Size: $filesize bytes");
echo("<pre>$text</pre>");
?>
</body></html>
```

# ...接上

![](img/7faa63a7fa0add8f53300594ebae949f_88_0.png)

quote.txt

```
quote.txt - 记事本
文件 编辑 视图 收藏 帮助
海瓦萨之歌
作者 Henry Wadsworth Longfellow 1807-1822
-------------------------------------------------------------
By the shores of Gitche Gumee,
By the shining Big-Sea-water,
Stood the wigam of Nokomis,
Dark behind it rose the forest,
Rose the black and gloomy pine trees,
Rose the firs with cones upon them;
Bright before it beat the water,
Beat the clear and sunny water,
Beat the shining big-sea-water.
```

```
Reading a file
文件 编辑 视图 收藏   帮助
地址: http://localhost/readfile.php [前往]
File Size: 419 bytes
The Song of Hiawatha
作者 Henry Wadsworth Longfellow 1807-1822
-------------------------------------------------------------
By the shores of Gitche Gumee,
By the shining Big-Sea-water,
Stood the wigam of Nokomis,
Dark behind it rose the forest,
Rose the black and gloomy pine trees,
Rose the firs with cones upon them;
Bright before it beat the water,
Beat the clear and sunny water,
Beat the shining big-sea-water.
Done Local intranet
```

7. 使用 PHP 处理文件 | 87

# 写入文件

可以使用 PHP fwrite() 函数写入新文件，或向现有文件追加内容。这需要两个参数：文件指针和要写入的数据字符串。可选地包含第三个整数参数来指定要写入的数据长度。如果包含了第三个参数，将在达到指定的长度（字节）后停止。

使用 fopen() 函数获取文件指针，参数指定文件名和第 85 页列出的写入模式之一。

向文件写入后，应使用 fclose() 函数关闭它，该函数需要文件指针。

可以使用 file_exists() 函数测试文件是否存在，如果文件存在则返回 true，不存在则返回 false。以下示例创建了一个新文件并向其中写入文本。

![](img/7faa63a7fa0add8f53300594ebae949f_89_0.png)

```php
<?php
$filename = "test.txt";
$file = fopen($filename, "w");
fwrite($file, "This is some test text.\n");
fclose($file);

if (file_exists($filename)) {
    echo "The file exists.";
} else {
    echo "The file does not exist.";
}
?>
```

# 记录日志

写入文件的能力使得 PHP 可以轻松地记录页面访问者的详情，并对网站开发有所帮助。

通过记录环境变量 HTTP_REFERER 的值，发现访问者是如何到达页面的是特别有趣的。它包含了用户为了到达你的页面所遵循的页面 URL。

通过记录页面访问者的 IP 地址，可以发现访问者返回的频率；这存储在环境变量 REMOTE_ADDR 中。

以下脚本演示了如何记录这些访问者详情，以及他们的浏览器类型和访问页面的时间。

![](img/7faa63a7fa0add8f53300594ebae949f_91_0.png)

```php
<?php
#为环境变量值赋值
$address = $_SERVER['REMOTE_ADDR'];
$referer = $_SERVER['HTTP_REFERER'];
$browser = $_SERVER['HTTP_USER_AGENT'];

# 打开日志文件
$file = fopen("log.html", "a");

# 写入访问时间
$time = date("H:i ds F");
fwrite($file, "<b>$time</b> $time<br>");

# 如果可用，写入用户的 IP 地址
if ($address != null) {
    fwrite($file, "<b>IP Address:</b> $address<br>");
}

# 如果可用，写入跳转页面的 URL
if ($referer != null) {
    fwrite($file, "<b>Referer:</b> $referer<br>");
}

# 写入用户的浏览器详情
fwrite($file, "<b>Browser:</b> $browser<hr>");

# 关闭日志文件
fclose($file);
?>
```

![](img/7faa63a7fa0add8f53300594ebae949f_91_1.png)

