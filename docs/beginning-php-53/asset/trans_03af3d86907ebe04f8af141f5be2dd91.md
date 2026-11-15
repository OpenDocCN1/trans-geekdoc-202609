

接下来是 checkDateOfBirth()，这是一个回调函数，用于检查输入的日期是否有效。如你所料，这使用 PHP 的 checkdate() 函数来进行检查。因为被检查的元素包含多个字段值，HTML_QuickForm 提供了一个按字段名索引的关联数组，包含这些值。checkDateOfBirth() 提取这三个值并将它们传递给 checkdate() 进行检查，将 checkdate() 的返回值（true 或 false）返回给调用代码：

```php
function checkDateOfBirth( $value ) {
    return checkdate( $value["M"], $value["d"], $value["Y"] );
}
```

最后一个函数 calculateDays() 在处理表单时被调用。首先，它创建两个时间戳：$currentDate，用于存储当前日期和时间；以及 $dateOfBirth，用于存储输入的出生日期。这两个时间戳均使用 mktime() 创建。出生日期的月、日、年分量从存储在表单 dateOfBirth 字段中的三元素关联数组中提取：

```php
$currentDate = mktime();
$dateOfBirth = mktime( 0, 0, 0, $values["dateOfBirth"]["M"],
    $values["dateOfBirth"]["d"], $values["dateOfBirth"]["Y"] );
```

既然两个日期都存储在时间戳中，计算两者之间的秒数，进而计算天数就很容易了：

```php
$secondsOld = $currentDate - $dateOfBirth;
$daysOld = (int) ( $secondsOld / 60 / 60 / 24 );
```

最后，该函数向访问者显示输出。首先，它调用 PHP 的 date() 函数以友好的格式显示访问者的出生日期，然后告诉访问者他多少天大了：

```php
echo "<p>You were born on " . date( "l, F jS, Y", $dateOfBirth ) . ".</p>";
echo "<p>You are " . number_format( $daysOld ) . " day" . ( $daysOld != 1 ? "s" : "" ) . " old!</p>";
```

通过将秒数差除以（60 * 60 * 24）来计算天数差并不完全准确，因为一天并不总是 24 小时长（至少在使用夏令时的时区中）。不过，对于此脚本的目的来说，这已经足够了。

## DateTime：PHP 日期/时间处理的未来

从版本 5.2 开始，PHP 引入了几个有用的日期和时间处理类：

- DateTime 用于存储和操作日期和时间
- DateTimeZone 用于表示时区

在撰写本文时，这些类相对实验性且功能不完善；不过，它们已经很有用。与传统的 PHP 日期和时间函数相比，它们具有许多优势，包括：

- 对时区的优雅处理
- 能够存储和处理 1901 年之前和 2038 年之后的日期
- 更容易的日期操作

例如，以下代码创建一个表示洛杉矶时区 1948 年 2 月 13 日的新 DateTime 对象，然后从日期中减去三个月，并显示结果：

```php
$dtz = new DateTimeZone( "America/Los_Angeles" );
$dt = new DateTime( "13-Feb-1948", $dtz );
$dt->modify( "-3 months" );

// Displays "Thu, 13 Nov 1947 00:00:00 -0800"
echo $dt->format( DateTime::RFC2822 );
```

首先，代码创建一个表示洛杉矶时区的新 DateTimeZone 对象，然后创建一个表示该时区 1948 年 2 月 13 日午夜的新 DateTime 对象。接下来，代码调用 DateTime 对象的 modify() 方法。这个非常实用的方法接受一个与传递给 strtotime() 相同格式的修改字符串，并相应地调整日期和时间。

最后，代码调用 DateTime 对象的 format() 方法将日期作为字符串返回。format() 接受与 date() 函数相同类型的格式字符串。在此示例中，使用类常量 DateTime::RFC2822 以 RFC2822 格式格式化日期，即 "D, d M Y H:i:s O"。注意，显示的日期字符串中的时区偏移量比格林威治标准时间晚八小时——即洛杉矶时间。

DateTime 类目前缺少一些有用的功能；然而，如果你偏好面向对象的方法，或需要处理通常 1901–2038 年范围之外的日期，它绝对值得一看。有关 DateTime 和相关类的更多信息，请参阅 http://www.php.net/manual/en/book.datetime.php。

## 使用 HTTP

Web 服务器和浏览器使用 HTTP（超文本传输协议）相互通信，这是一套规范如何从 Web 服务器请求和检索数据的规则。

大多数情况下，您无需深入了解 HTTP 的工作原理，因为每当访问者访问您的网页或 PHP 脚本时，HTTP 通信都会自动发生。不过，偶尔了解 HTTP 中涉及的一些过程可能很有用，因为 PHP 让您对这些过程有一定控制。例如，如果您了解 HTTP 响应头的工作原理，可以使用 PHP 脚本创建自定义响应头，从而让脚本显示图像或将浏览器重定向到新页面，等等。

在接下来的章节中，您将探索 Web 浏览器如何向 Web 服务器发出 HTTP 请求；服务器随后如何将 HTTP 响应发回浏览器；以及您如何影响服务器与浏览器之间的 HTTP 通信。

### 了解 HTTP 请求

每当浏览器想要显示存储在 Web 服务器上的网页或其他资源（如图像文件）时，浏览器首先连接到服务器（通常通过端口 80，即 HTTP 端口），然后向服务器发送各种信息，称为 *请求消息*。请求消息按顺序由以下部分组成：

- 请求行：告诉 Web 服务器浏览器要检索哪个资源（URL）
- HTTP 头列表：这些可选的文本行允许浏览器向服务器发送额外信息，例如 Cookie 和浏览器可以接受的字符集
- 空行：请求行和任何头之后需要的空行
- 可选的消息体：例如，可能包含通过 POST 方法发送的表单数据

消息中的每一行必须以回车符后跟换行符结束。

请求行是请求中最重要的部分，因为它告诉服务器将哪个资源发送回浏览器。以下是典型的请求行：

```
GET /about/index.php HTTP/1.1
```

请求行由三部分组成：请求方法（此处为 `GET`）、要检索的 URL（`/about/index.php`）以及要使用的 HTTP 版本（大多数现代浏览器使用 `HTTP/1.1`）。其他请求方法包括 `POST`（用于发送大量表单数据）和 `HEAD`（类似于 `GET`，但要求服务器仅返回响应头，而不是实际内容）。

可以从浏览器向服务器发送许多 HTTP 请求头。以下是一些常见的请求头：

| 头部 | 描述 | 示例 |
| :--- | :--- | :--- |
| Accept | 浏览器接受的返回内容的 MIME 内容类型列表。 | Accept: text/html, application/xml |
| Accept-Charset | 浏览器接受的返回内容的字符集列表。 | Accept-Charset: ISO-8859-1, utf-8 |
| Accept-Encoding | 浏览器接受的返回内容的压缩方法列表。 | Accept-Encoding: gzip, deflate |
| Accept-Language | 浏览器接受的返回内容的语言列表。 | Accept-Language: en-gb, en |
| Cookie | 此服务器之前发送的 HTTP Cookie（有关 Cookie 的更多信息，请参见第 10 章）。 | Cookie: name=fred |
| Host | 这是唯一的强制性头，且仅在进行 HTTP/1.1 请求时才强制。由于大多数 Web 服务器应用程序可以在单台机器上为多个域提供网站服务，浏览器会发送 Host 头来告诉服务器它正在从哪个网站请求资源。 | Host: www.example.com |
| Referer | 当访问者单击链接以查看新页面时，大多数浏览器会在 Referer 头中发送包含链接的页面的 URL。Web 服务器通常会将 Referer URL 与请求的页面 URL 一起记录下来。这样，Webmaster 就可以查看服务器日志以了解访问者来自何处。 | Referer: www.example.com |
| User-Agent | 关于浏览器的信息，例如其类型和版本。（您在第 15 章中学习了如何访问这些信息。） | User-Agent: Mozilla/5.0 (Macintosh; U; Intel Mac OS X 10.5; en-GB; rv:1.9.0.5) Gecko/2008120121 Firefox/3.0.5 |

因此，完整的浏览器请求（假设没有请求体）可能如下所示：

```
GET /about/index.php HTTP/1.1
Host: www.example.com
Accept: text/html, application/xml
Accept-Charset: ISO-8859-1,utf-8
Accept-Encoding: gzip,deflate
Accept-Language: en-gb,en
Cookie: name=fred
Referer: www.example.com
User-Agent: Mozilla/5.0 (Macintosh; U; Intel Mac OS X 10.5; en-GB;
rv:1.9.0.5) Gecko/2008120121 Firefox/3.0.5
```

### 探索 HTTP 响应

当 Web 服务器收到来自浏览器的 HTTP 请求时，它会发送回一个 HTTP 响应。通常，这包括浏览器请求的内容以及一些关于内容的信息，但它也可能返回一个错误（例如，如果找不到内容）。

