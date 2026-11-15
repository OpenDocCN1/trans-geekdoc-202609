

![](img/ae7820c36e8f24c1623d26668b28e80e_779_0.png)

图 28.4 简单输出，后台有大量技术

## JavaScript 的编码与解码

Ajax 应用程序在客户端和服务器之间传输大量数据时，几乎完全依赖一种特殊格式：JSON（参见 http://json.org）。JSON 基于 JavaScript 语法特性，可非常紧凑地表示数组和对象。简单调用 JSON.parse() JavaScript 函数即可将 JSON 格式的数据转换为 JavaScript 值。返回路径——即将 JavaScript 值转换为 JSON 字符串——由 JSON.stringify() 执行。

使用 PHP，您可以非常轻松地生成和解码 JSON 数据。相应的函数称为 json_encode() 和 json_decode()。请参考以下示例：

```php
<?php
class A {
    public $b;
    function __construct($c) {
        $this->b = $c;
    }
}

$data = [1, "hello", true, new A("xyz")];
echo json_encode($data);
// Output: [1, "hello",true,{"b": "xyz"}]
var_dump(json_decode("[1,\"hello\",true,{\"b\":\"xyz\"}]"));
// Output: array(4) {
// [0]=>
// int(1)
// [1]=>
// string(5) "hello"
// [2]=>
// bool(true)
// [3]=>
// object(stdClass)#2 (1) {
//   ["b"]=>
//   string(3) "xyz"
// }
// }
?>
```

第 27 章也讨论了与 REST API 相关的 JSON。

## 28.4 Web 套接字

Ajax 相当不错，但性能并不特别出色；毕竟，整个东西仍然基于 HTTP。使用 Web 套接字或 Web 套接字协议，存在一种可能的替代方案。这是一种非常高性能的全双工通信协议，能够以非常简单的方式与服务器交换数据。HTTP 仍在使用，但仅用于建立连接。

Web 套接字具有众多优势。除了性能更好之外，Web 套接字协议还提供双向性，这意味着即使在建立连接后，服务器也可以持续向客户端发送数据。与常见的 HTTP 拉取方式（客户端请求数据，只有此时服务器才发送数据）相比，这种方式自然显得过时。

> **Web 套接字标准化**
> 
> Web 套接字协议是互联网工程任务队（IETF）的官方 RFC：RFC 6455（https://tools.ietf.org/html/rfc6455）。
> 
> W3C 也曾在 www.w3.org/TR/websockets 长期设有 Web 套接字专区。起初在大约十年的时间里不再维护；此后已转移至 Web 超文本应用技术工作组（WHATWG）的 https://websockets.spec.whatwg.org/，该技术的所有后续工作均在此进行。

要让应用程序使用 Web 套接字，客户端和服务器必须做好相应准备。客户端必须通过 JavaScript 发送 Web 套接字连接请求，服务器必须能够相应处理。后者使用 PHP 自带资源相当耗时，因此我们使用外部组件。

### 28.4.1 服务器

Web 套接字协议有多个版本，服务器的任务之一是正确支持每个版本；如我们稍后将看到，浏览器大致会自动完成此操作。但我们不是自己实现一切，而是依赖一个名为 Ratchet 的成熟包。在趣味 URL http://socketo.me（参见图 28.5）上，有关该包的信息和可在线试用的演示，但没有直接下载。

目前，Ratchet 只能通过 Composer 包管理器安装。在第 38 章中，您将找到更多相关信息；此外，您还将学习如何在系统上安装 Composer。对于以下说明，我们假设此操作已完成。

![](img/ae7820c36e8f24c1623d26668b28e80e_781_0.png)

图 28.5 Ratchet 主页

现在通过 Composer 在项目目录中安装 Ratchet 包：

```
composer require cboden/ratchet
```

如果您没有全局安装 Composer，但 composer.phar 可用，请使用以下命令：

```
php /path/to/composer.phar require cboden/ratchet
```

然后 Ratchet 将安装在系统上。甚至支持自动加载；vendor/autoload.php 文件已相应创建或调整。只需 require "vendor/autoload.php"（如有必要可自定义路径）即可加载 Ratchet 所需的所有类（参见图 28.6）。

![](img/ae7820c36e8f24c1623d26668b28e80e_782_0.png)

图 28.6 通过 Composer 安装 Ratchet

Ratchet 具有一个同名命名空间及其下的若干类。让我们先看看 MessageComponentInterface 接口，它定义了四个方法：

- onOpen()
  建立与 Web 套接字服务器的连接时调用
- onClose()
  与 Web 套接字服务器的连接再次关闭时调用
- onMessage()
  向服务器发送消息时调用
- onError()
  发生错误时调用

在我们的示例中，我们想要实现一个简单的服务器，将所有发送给它的消息原样返回。因此，我们只需为 onMessage() 方法提供具体实现。这可以如下所示：

```php
class EchoServer implements Ratchet\MessageComponentInterface {
    public function onOpen(Ratchet\ConnectionInterface $conn) {}
    public function onMessage(Ratchet\ConnectionInterface $from, $msg) {
        $from->send($msg);
    }

    public function onClose(Ratchet\ConnectionInterface $conn) {}

    public function onError(Ratchet\ConnectionInterface $conn, Exception $e) {}
}
```

接下来，我们需要确保为 Web 套接字调用实现一个端点。为此，我们需要 Ratchet 中的一些类（此处未显示相关命名空间）：

- IoServer 是 Ratchet 中服务器的通用基类。
- HttpServer 创建可接收 HTTP 请求的服务器。
- WsServer 基于 HTTP 服务器实现 Web 套接字服务器。

以下嵌套调用为我们的 EchoServer 实现创建 Web 套接字服务器，并在端口 12345 上运行：

```php
$server = Ratchet\Server\IoServer::factory(
    new Ratchet\Http\HttpServer(
        new Ratchet\WebSocket\WsServer(
            new EchoServer()
        )), 12345);
$server->run();
```

清单 28.4 展示了完整代码的概览：自动加载、类实现和服务器实例化。

```php
<?php
require "./vendor/autoload.php";

class EchoServer implements Ratchet\MessageComponentInterface {
    public function onOpen(Ratchet\ConnectionInterface $conn) {
    }

    public function onMessage(Ratchet\ConnectionInterface $from, $msg) {
        $from->send($msg);
    }

    public function onClose(Ratchet\ConnectionInterface $conn) {
    }

    public function onError(Ratchet\ConnectionInterface $conn, Exception $e) {
    }
}

$server = Ratchet\Server\IoServer::factory(
    new Ratchet\Http\HttpServer(
        new Ratchet\WebSocket\WsServer(
            new EchoServer())), 12345);
$server->run();
?>
```

清单 28.4 带有 Ratchet 的 Web 套接字服务器（"echo.php"）

现在可以在命令行中启动此服务器：

```
php echo.php
```

### 28.4.2 客户端

唯一缺少的是客户端——因此也是 JavaScript。Web 套接字的编程接口看起来非常简单，基本由以下组件组成：

- WebSocket 是基类。
- send() 方法向服务器发送消息。
- 有一系列事件，与清单 28.4 中的服务器实现类似，例如 open 和 message。

在与服务器建立连接时，其地址会传递给 WebSocket 类的构造函数。3 我们使用 ws:// 作为协议，因此在本例中 URL 为 ws://127.0.0.1:12345：Web 套接字协议，本地运行的服务器，端口 12345。

以下代码在连接建立后（open 事件）向服务器发送经典的 "Hello world" 消息：

```javascript
var ws = new WebSocket("ws://127.0.0.1:12345");
ws.onopen = function() {
    ws.send("Hello world!");
}
```

3 当然，严格来说它在 JavaScript 中不是类，也不是构造函数，但在这种情况下功能非常相似，因此我们将沿用此描述。

