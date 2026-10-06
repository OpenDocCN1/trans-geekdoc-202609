

# 304 附录

GET /projects/12345 HTTP/1.1
Accept: application/json

![](img/6a422bfe4f2691ab7de274bb6978b0eb_338_0.png)

```
HTTP/1.1 200 OK
{
  "id": "12345",
  "projectName": "My Project"
}
```

**图 A.1** HTTP 协议概览。

# 统一资源定位符 (URL)

HTTP 使用 URL 作为数据或服务所在的唯一地址。请求被发送到 URL，由服务器处理请求并向客户端发送回执响应。URL 通常出现在浏览器的地址栏中。示例包括：

- *https://www.google.com*
- *https://launchany.com/effective-api-programs/*
- *https://deckofcardsapi.com/api/deck/new/shuffle*

URL 由以下项目组成：

- **协议 (Protocol):** 用于连接的协议（例如 http [不安全] 或 https [安全]）。
- **主机名 (Hostname):** 要连接的服务器（例如 api.example.com）。
- **端口号 (Port number):** 一个范围从 0 到 65535 的数字，用于识别服务器上请求所在的进程（例如 https 使用 443，http 使用 80）。
- **路径 (Path):** 所请求的资源路径（例如 /projects）。默认路径为 /，表示主页。
- **查询字符串 (Query string):** 包含要传递给服务器的数据。以问号开头，包含 name=value 键值对，并使用 符号 作为它们之间的分隔符（例如 ?page=1&per_page=10）。

# HTTP 请求

| 协议 | 主机名 | 端口 | 路径 | 查询字符串 |
|---|---|---|---|---|
| https | api.mycompany.example | 443 | /projects | page=2 |

**图 A.2** 统一资源定位符 (URL) 的组成元素。

图 A.2 展示了 URL 的元素。

# HTTP 请求

一个 HTTP 请求由几个部分组成：HTTP 方法、路径、标头（Header）和消息体（Message Body）。

HTTP 方法告知服务器客户端想要请求什么类型的交互。常见的 HTTP 方法有 GET（请求数据）和 POST（提交数据）。用于 Web 端 API 的常用方法将在本附录稍后部分详细介绍。

路径是 URL 中引用服务器上资源的部分。该资源可以是静态文件（如图像），也可以是执行动态请求处理的代码。

标头告知服务器关于客户端的信息以及请求的细节。标头由 `name:value` 格式的标头字段组成。与 Web 端 API 一起常用的 HTTP 请求标头包括：

- **Accept**: 告知服务器客户端支持哪些内容类型。示例可能 image/gif 和 image/jpeg。如果客户端愿意接受任何类型的响应，则使用 `"*"`。此标头通常用于内容协商，后文将详述。

- **Content-Type**: 告知服务器请求体的内容类型。在使用需要消息体的 HTTP 方法（例如 POST）提交数据时使用。

- **User-Agent**: 提供一个自由格式的字符串，表示发出请求的 HTTP 客户端类型。这可能指示特定的浏览器类型和版本，也可以经过自定义以指示特定的辅助库或命令行工具。

# 306 附录

```
GET http://www.google.com/HTTP/1.1
User-Agent: Mozilla/5.0 [en] (X11; Linux 2.2.013 i686)
Host: google.com
Accept: image/gif, image/x-bitmap, image/jpeg/*
Accept-Encoding: gzip
Accept-Language: en
Accept-Charset: iso-8859-1, "*,utf-8
```

图 A.3 对 https://www.google.com 发送 HTTP 请求的逐行检查。

- **Accept-Encoding**: 告知服务器客户端能够处理哪些压缩支持（如果有）。这允许服务器使用 gzip 或压缩格式压缩响应，以减少响应的字节大小。

消息体在提交数据时为服务器提供详细信息，根据服务器的要求，它可以是人类可读或二进制。对于使用 GET 的检索请求，消息体可能为空。
图 A.3 展示了发送到 Google 的 HTTP 请求示例，该请求请求包含搜索表单的主页，并进行了逐行记录。

# HTTP 响应

一旦服务器接收到请求，就会处理请求并发送响应。响应由三个部分组成：响应码、响应标头和响应体。

响应码是一个对应成功或错误代码的数字，指示请求是否可以完成。发送的响应码必须是 HTTP 规范中列出的之一，并在后文中详细介绍。每个响应只允许一个响应码。

响应标头告知客户端请求的结果。标头由 `name:value` 格式的标头字段组成。与 Web 端 API 一起常用的 HTTP 响应标头包括：

- **Date**: 响应的日期。
- **Content-Location**: 响应的完整 URL。如果请求导致重定向并可能需要客户端更新其资源 URL，则此项有用。
- **Resource**: 响应的长度（字节为单位）。

# 常用 HTTP 方法

```
HTTP/1.1 200 OK
Date: Fri, 13 Nov 2020 22:16:05 GMT
Content-Length: 79
Content-Type: text/html
Connection: close
```

**图 A.4** 对 https://www.google.com 发送 HTTP 请求的逐行检查。（注：此处原文逻辑似乎错乱，已根据语境翻译）

- **Accept-Encoding**: 告知服务器客户端能够处理哪些压缩支持（如果有）。

...

# 常用 HTTP 方法

HTTP 方法告知服务器客户端想要请求什么类型的交互。常见的 HTTP 方法有 GET（请求数据）和 POST（提交数据）。

在 Web 端 API 中常用的 HTTP 方法包括：

- **GET**: 从服务器检索资源。
- **HEAD**: 请求响应标头但不响应体。
- **POST**: 向服务器提交数据，通常用于存储或计算。
- **PUT**: 向服务器提交数据，通常作为现有数据的替换。
- **PATCH**: 向服务器提交数据，通常作为现有数据的部分更新。
- **DELETE**: 删除服务器上的现有资源。

HTTP 方法具有客户端需要考虑的重要语义：安全性 (Safety) 和等幂性 (Idempotence)。

安全方法表示 HTTP 方法不会产生副作用，例如修改数据。这通常适用于 GET 和 HEAD 方法，因为它们用于检索且不修改数据。

等幂性方法确保在提交相同请求时产生相同的副作用。这适用于 GET 和 HEAD 方法，因为没有数据被修改。PUT 和 DELETE 由 HTTP 规范保证是等幂的，因为 PUT 将资源替换为全新的表示，而 DELETE 从服务器删除资源。

POST 不保证是等幂的，因为每次随后的请求可能会创建新资源，或以无法保证产生相同结果的方式修改数据（例如增加值）。同样，PATCH 不是等幂的，因为它修改的是部分字段，而不是整个资源。

图 A.5 总结了用于 Web 端 API 的常用 HTTP 方法的语义。

| 方法 | 安全性 | 等幂性 |
|---|---|---|
| GET | 是 | 是 |
| POST | 否 | 否 |
| PUT | 否 | 是 |
| PATCH | 否 | 否 |
| DELETE | 否 | 是 |
| HEAD | 是 | 是 |
| OPTIONS | 是 | 是 |

