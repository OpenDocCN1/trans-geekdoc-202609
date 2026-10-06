

# 第三部分：在实践中使用 PHP

| 头部 | 描述 | 示例 |
| --- | --- | --- |
| Cookie | 之前由此服务器发送的 HTTP cookie（有关 cookie 的更多信息请参见第 10 章）。 | Cookie: name=fred |
| Host | 这是唯一强制性的头部，且仅在发送 HTTP/1.1 请求时需要。由于 Web 服务器可以在单台机器上为多个域名提供网站服务，浏览器会发送 Host 告诉服务器它正在从哪个站点请求资源。 | Host: www.example.com |
| Referer | 当访问者点击指向新页面的链接时，浏览器会将包含该链接的页面 URL 发送到 Referer 头部中。Referer URL 通常会被 Web 服务器连同请求的页面 URL 一起记录。这样，网站管理员可以通过服务器日志查看访问者来自哪里。 | Referer: www.example.com |
| User-Agent | 关于浏览器的信息，例如其类型和版本。（你在第 15 章中学习了如何访问这些信息）。 | User-Agent: Mozilla/5.0 (Macintosh; U; Intel Mac OS X 10.5; en-GB; rv:1.9.0) Gecko/20080810121 Firefox/3.0.5 |

因此，一个完整的浏览器请求（假设没有请求体）可能如下：

```
GET /about/index.php HTTP/1.1
Host: www.example.com
Accept: text/html, application/xml
Accept-Charset: ISO-8859-1,utf-8
Accept-Encoding: gzip, deflate
Accept-Language: en-gb, en
Cookie: name=fred
Referer: www.example.com
User-Agent: Mozilla/5.0 (Macintosh; U; Intel Mac OS X 10.5; rv:1.9.0.5) Gecko/20080810121 Firefox/3.0.5
```

# 探索 HTTP 响应

当 Web 服务器接收浏览器的 HTTP 请求时，它会返回一个 HTTP 响应。通常这包括浏览器请求的内容，以及一些关于内容的信息，但也可能返回错误（例如，如果找不到该内容）。

# 第 16 章：PHP 与外部世界

与请求一样，响应通常包含四个部分：

- 状态行（status line）：它告诉 Web 浏览器请求的状态。
- HTTP 头部列表：这些可选头部包含响应的额外信息，例如返回内容的类型和长度。
- 一个空行：在请求行和任何头部之后必须有一个空行。
- 可选的消息体（message body）：通常包含返回的内容，例如 Web 页面标记或编码后的图像数据。

HTTP 状态行由一个状态码和一个对应的理由短语（即状态码的纯英文版本）组成。常见的状态码包括：

| 状态码 | 理由短语 | 描述 |
|---|---|---|
| 200 | OK | 浏览器的请求成功。后续将是请求的内容（如果有）。 |
| 301 | Moved Permanently | 永久移动。请求的资源现在位于不同的 URL。新 URL 将出现在 Location 头部中。浏览器在未来的请求中应使用新 URL。 |
| 302 | Found | 找到。请求的资源临时位于不同的 URL。新 URL 将出现在 Location 头部中。浏览器在未来的请求中应继续使用现有 URL。 |
| 400 | Bad Request | 请求错误。浏览器发送的请求无效（例如，语法不正确）。 |
| 403 | Forbidden | 禁止。浏览器正尝试访问它没有权限访问的资源（例如，受密码保护的文件）。 |
| 404 | Not Found | 未找到。在服务器上找不到浏览器请求的资源。 |
| 500 | Internal Server Error | 内部错误。服务器处理请求时出现问题。 |

# 第三部分：PHP 实践

许多响应头部与其对应的请求头部相似或完全相同。以下是 Web 服务器发送的几个常见响应头部：

| 头部 | 描述 | 示例 |
| --- | --- | --- |
| Date | 响应的日期和时间。 | Date: Mon, 05 Jan 2009 10:07:20 GMT |
| Content-Length | 后续内容的长度（字节）。 | Content-Length: 8704 |
| Content-Type | 后续内容的 MIME 类型。 | Content-Type: text/html |
| Location | 请求 URL 的备选 URL。通常与 301 和 302 状态码一起使用，将浏览器重定向到新 URL。 | Location: http://www.example.com/new.php |
| Server | 关于 Web 服务器的信息，例如其类型和版本。 | Server: Apache/1.3.34 (Debian) PHP/5.2.0-8+etch13 mod_perl/1.29 |
| Set-Cookie | 请求浏览器存储 HTTP cookie。 | Set-Cookie: name=Fred; expires=Mon, 05-Jan-2009 10:22:21 GMT; path=/; domain=example.com |

以下是浏览器请求 HTML 页面后 Web 服务器返回的示例：

```
HTTP/1.x 200 OK
Date: Mon, 05 Jan 2009 10:19:52 GMT
Server: Apache/2.0.59 (Unix) PHP/5.2.5 DAV/2
X-Powered-By: PHP/5.2.5
Content-Length: 395
Keep-Alive: timeout=15, max=96
Connection: Keep-Alive
Content-Type: text/html
```
```html
<!DOCTYPE html> //W3//DTD HTML 1.0 Strict//EN//"http://www.w3.org/TR/html41/strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xmlns:lang="en" lang="en">
<head>
<title>About Us</title>
<link rel="stylesheet" type="css" href="common.css" />
</head>
<body>
<h1>About Us</h1>
<p>We specialize in widgets for all occasions.</p>
</body>
</html>
```

# 第 16 章：PHP 与外部世界

当访问者点击指向新页面的链接时，浏览器会将包含该链接的页面 URL 发送到 Referer 头部中。Referer URL 通常会被 Web 服务器 连同请求的页面 URL 一起记录。这样，网站管理员可以通过服务器日志查看访问者来自哪里。当 Web 服务器接收到浏览器的 HTTP 请求时，它会返回一个 HTTP 响应。通常这包括浏览器请求的内容，以及一些关于内容的信息，但也可能返回错误（例如，如果找不到该内容）。与请求一样，响应通常包含四个部分：

- 状态行（status line）：它告诉 Web 浏览器请求的状态。
- HTTP 头部列表：这些可选头部包含响应的额外信息，例如返回内容的类型和长度。
- 一个空行：在请求行和任何头部之后必须有一个空行。
- 可选的消息体（message body）：通常包含返回的内容，例如 Web 页面标记或编码后的图像数据。

HTTP 状态行由一个状态码和一个对应的理由短语（即状态码的纯英文版本）组成。常见的状态码包括：

| 状态码 | 理由短语 | 描述 |
|---|---|---|
| 200 | OK | 浏览器的请求成功。后续将是请求的内容（如果有）。 |
| 301 | Moved Permanently | 永久移动。请求的资源现在位于不同的 URL。新 URL 将出现在 Location 头部中。浏览器在未来的请求中应使用新 URL。 |
| 302 | Found | 找到。请求的资源临时位于不同的 URL。新 URL 将出现在 Location 头部中。浏览器在未来的请求中应继续使用现有 URL。 |
| 400 | Bad Request | 请求错误。浏览器发送的请求无效（例如，语法不正确）。 |
| 403 | Forbidden | 禁止。浏览器正尝试访问它没有权限访问的资源（例如，受密码保护的文件）。 |
| 404 | Not Found | 未找到。在服务器上找不到浏览器请求的资源。 |
| 500 | Internal Server Error | 内部错误。服务器处理请求时出现问题。 |

许多响应头部与其对应的请求头部相似或完全相同。以下是 Web 服务器发送的几个常见响应头部：

| 头部 | 描述 | 示例 |
| --- | --- | --- |
| Date | 响应的日期和时间。 | Date: Mon, 05 Jan 2009 10:07:20 GMT |
| Content-Length | 后续内容的长度（字节）。 | Content-Length: 8704 |
| Content-Type | 后续内容的 MIME 类型。 | Content-Type: text/html |
| Location | 请求 URL 的备选 URL。通常与 301 和 302 状态码一起使用，将浏览器重定向到新 URL。 | Location: http://www.example.com/new.php |
| Server | 关于 Web 服务器的信息，例如其类型和版本。 | Server: Apache/1.3.34 (Debian) PHP/5.2.0-8+etch13 mod_perl/1.29 |
| Set-Cookie | 请求浏览器存储 HTTP cookie。 | Set-Cookie: name=Fred; expires=Mon, 05-Jan-2009 10:22:21 GMT; path=/; domain=example.com |

以下是浏览器请求 HTML 页面后 Web 服务器返回的示例：

```
HTTP/1.x 200 OK
Date: Mon, 05 Jan 2009 10:19:52 GMT
Server: Apache/2.0.59 (Unix) PHP/5.2.5 DAV/2
X-Powered-By: PHP/5.2.5
Content-Length: 395
Keep-Alive: timeout=15, max=96
Connection: Keep-Alive
Content-Type: text/html
```
```html
<!DOCTYPE html> //W3//DTD HTML 1.0 Strict//EN//"http://www.w3.org/TR/html41/strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xmlns:lang="en" lang="en">
<head>
<title>About Us</title>
<link rel="stylesheet" type="css" href="common.css" />
</head>
<body>
<h1>About Us</h1>
<p>We specialize in widgets for all occasions.</p>
</body>
</html>
```

（注：由于提供的原文中存在大量重复的段落和表格，根据“不要重复输出原文”的原则，此处译文保留了核心内容并进行了翻译。）

