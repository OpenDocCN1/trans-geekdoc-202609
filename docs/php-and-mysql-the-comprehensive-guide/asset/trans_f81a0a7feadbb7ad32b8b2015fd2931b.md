

![](img/ae7820c36e8f24c1623d26668b28e80e_731_0.png)

### 图 26.3 POST 请求的结果

你也可以通过自己设置 HTTP 请求，以“手动”方式发送相同的请求。为此，你必须先打开与 Web 服务器的套接字连接，然后自己输入所有必要的数据。相关的函数是 fsockopen()。它为你提供套接字连接的句柄。你需要五个参数（尽管出于可读性原因，示例中使用了具名参数，但仍遵循正确的顺序）：

- 1. 流名称（在示例中，tcp://）
- 2. 端口号（HTTP 通常为 80，HTTPS 通常为 443）
- 3. 带有错误号的返回变量
- 4. 带有错误消息的返回变量
- 5. 超时时间（以秒为单位）

然后，你可以使用 fwrite() 将数据发送到套接字，并使用 fgets() 读取返回值。请查看以下完整清单。

```
<h1>Result of the POST request</h1>
<pre>

<?php
$socket = fsockopen(
    hostname: "tcp://pecl.php.net",
    port: 80,
    error_code: $errorcode,
    error_message: $errormsg,
    timeout: 30
);
$data = "search_string=HTTP&search_in=packages";
fwrite($socket, "POST /search.php HTTP/1.1\r\n");
fwrite($socket, "Host: pecl.php.net\r\n");
fwrite($socket, "Accept: */*\r\n");
fwrite($socket, "Content-length: " . strlen($data) . "\r\n");
fwrite($socket, "Content-type: application/x-www-form-urlencoded\r\n");
fwrite($socket, "\r\n$data\r\n");
while (!feof($socket)) {
    echo htmlspecialchars(fgets($socket, 4096));
}
fclose($socket);
?>
</pre>
```

### 清单 26.4 通过套接字发送 POST 请求 ("http-4.php")

如图 26.4 所示，POST 请求成功。但是，返回值是 HTTP 代码 302，表示“已找到，但不是实际目标页面”。你可以在 Location HTTP 标头中看到原因：正在执行重定向到 http://pecl.php.net/package-results.php?pkg_name=HTTP。

![](img/ae7820c36e8f24c1623d26668b28e80e_732_0.png)

### 图 26.4 套接字 POST 请求的结果

**注意**
PECL 网站当然随时可能发生更改。因此，无法保证代码将来仍以完全相同的方式工作。

### FTP 流

使用类型为 `ftp://user:password@ftp.domain.xy/path/file` 或 `ftps://user:password@ftp.domain.xy/path/file` 的 FTP 流，你可以像处理常规文件一样处理 FTP 服务器上的文件（参见前一章）。如果对 `fopen()` 使用文件模式 `"rb"`，则可以从 FTP 服务器下载文件；使用 `"wb"` 或 `"xb"`，则可以创建文件。还有另一个选项：你可以向 FTP 文件追加数据——即也可以使用 `"ab"` 模式。

## 26.2.3 PHP 流

在表 26.1 列出的流中，有一个特别有趣：`php://filter`。PHP 已经为流包含了预定义的过滤器：如果你向这些过滤器写入数据，数据将被自动转换。要试用以下示例，你仍然需要前一章中的 `test.txt` 文件，其内容如下：

人生皆是考试
而我们只是考生

你可以在过滤器中输入以下数据：

- 对于 resource，指定要访问的流的名称。
- 使用 read，可以指定在读取时应用的过滤器。
- 使用 write，可以定义在写入时使用的过滤器。

以下清单显示了一个示例。

```
<pre>
<?php
echo htmlspecialchars(
file_get_contents(
"php://filter/read=string.toupper/resource=test.txt"
)
);
?>
</pre>
```

### 清单 26.5 "string.toupper" 过滤器 ("filter-1.php")

图 26.5 显示了结果：`string.toupper` 将流数据转换为大写字母。

![](img/ae7820c36e8f24c1623d26668b28e80e_734_0.png)

### 图 26.5 过滤器的结果

以下四个过滤器是 PHP 内置的：

- 1. string.rot13 执行 ROT13 编码。²
- 2. string.strip_tags 使用 strip_tags() 函数预处理所有数据——即，删除所有标记。
- 3. string.tolower 将所有数据转换为小写（与 strtolower() 相同）。
- 4. string.toupper 将所有数据转换为大写（与 strtoupper() 相同）。

还有一些转换过滤器：

- convert.base64-decode 对 Base64 数据进行解码（与 base64_decode() 相同）。
- convert.base64-encode 将数据编码为 Base64 格式（与 base64_encode() 相同）。
- convert.quoted-printable-decode 对可打印引用数据进行解码（与 quoted_printable_decode() 相同）。
- convert.quoted-printable-encode 将数据编码为可打印引用格式（与 quoted_printable_encode() 相同）。

在前一章保存访客留言数据时，我们本可以特别使用 Base64 过滤器。

当然，这些只是非常有限的选项。幸运的是，PHP 提供了定义自己流的选项。为此，你需要一个自己的类，该类继承自 php_user_filter。该类中必须有一个 filter() 方法，用于处理数据。该方法的返回类型必须设置为 int，以避免弃用警告。方法内部的过程始终相同，因此你将通过复制并粘贴来操作（此示例也是以这种方式创建的）。关键的一行（也是你始终要修改的一行）是修改 $bucket->data 的那一行。此属性始终包含当前查看的数据，并且也是可写的。以下是一个类，其中所有数据都使用 htmlspecialchars() 进行处理：

² 从 a 到 z 和 A 到 Z 的每个字母字符都被替换为与原字符相隔 13 个字符位置的 ASCII 码对应的字符。

```
class htmlspecialchars_filter extends php_user_filter {
    function filter($in, $out, &$consumed, $closing): int
    {
        while ($bucket = stream_bucket_make_writeable($in)) {
            $bucket->data = htmlspecialchars($bucket->data);
            $consumed += $bucket->datalen;
            stream_bucket_append($out, $bucket);
        }

        return PSFS_PASS_ON;
    }
}
```

使用 stream_filter_register()，你可以在系统下以自选名称注册该类：

```
stream_filter_register(
    "string.htmlspecial",
    "htmlspecialchars_filter"
);
```

stream_get_filters() 函数可用于检查过滤器是否已实际注册到系统中。然后你也可以使用该过滤器。以下流名称打开 test.txt 文件，将内容转换为大写，并转换 HTML 特殊字符；你可以在图 26.6 中看到输出：

php://filter/read=string.toupper|string.htmlspecial/resource=test.txt

![](img/ae7820c36e8f24c1623d26668b28e80e_735_0.png)

### 图 26.6 所有过滤器——以及我们过滤器的结果

请考虑以下完整清单。

```
<?php
class htmlspecialchars_filter extends php_user_filter {
    function filter($in, $out, &$consumed, $closing): int
    {
        while ($bucket = stream_bucket_make_writeable($in)) {
            $bucket->data = htmlspecialchars($bucket->data);
            $consumed += $bucket->datalen;
            stream_bucket_append($out, $bucket);
        }
        return PSFS_PASS_ON;
    }
}
stream_filter_register(
    "string.htmlspecial",
    "htmlspecialchars_filter"
);
echo "<h1>Filter</h1><pre>";
echo htmlspecialchars(print_r(stream_get_filters(), true));
echo "</pre><h1>Result</h1><pre>";
echo file_get_contents(
    "php://filter/read=string.toupper|string.htmlspecial/resource=test.txt"
);
echo "</pre>";
?>
```

### 清单 26.6 自定义过滤器的使用 ("filter-2.php")

> **注意**
> 
> 使用 `stream_filter_append()`，还可以使用函数将过滤器追加到流中——使用 `stream_filter_prepend()`，甚至可以将其添加到过滤器列表的开头。

## 26.2.4 压缩流

我们将要介绍的最后几种流类型处理压缩数据。支持的两种文件格式与当前发布 PHP 源代码的格式相同：gzip 和 bzip2。PHP 为两种归档方法都提供了单独的函数，但使用流时，你可以获得标准化的访问。

写入数据非常简单——像往常一样，使用 PHP 的文件函数。以下脚本再次打开 `test.txt` 文件，并将其保存为 GZ 和 BZ2 格式。

