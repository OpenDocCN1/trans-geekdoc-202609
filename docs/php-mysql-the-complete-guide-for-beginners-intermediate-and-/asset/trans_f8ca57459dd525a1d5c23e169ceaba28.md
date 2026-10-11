

这将返回以下输出：

![](Image01212.jpg)

此技术可用于避免对 `$_POST` 数组进行后处理循环，使您的代码更精简、更简洁。

## 第 55.6 节：使用 HTTP PUT 上传文件

[PHP 提供支持](http://php.net/manual/en/features.file-upload.put-method.php)某些客户端用于在服务器上存储文件的 HTTP PUT 方法。PUT 请求比使用 POST 请求的文件上传简单得多，它们看起来类似这样：

![](Image01213.jpg)

在您的 PHP 代码中，您可以这样做：

![](Image01214.jpg)

此外，[这里](http://stackoverflow.com/questions/12005790/how-to-receive-a-file-via-http-put-with-php) 您可以阅读关于通过 HTTP PUT 接收文件的有趣 SO 问答。

# 第 56 章：类型转换与非严格比较问题

## 第 56.1 节：什么是类型转换？

PHP 是一门弱类型语言。这意味着，默认情况下，它不要求表达式中的操作数类型相同（或兼容）。例如，您可以将数字追加到字符串后面，并期望它能正常工作。

![](Image01215.jpg)

输出将为：

![](Image01216.jpg) string(24) "This is example number 1"

PHP 通过自动将不兼容的变量类型转换为允许执行请求操作的类型来实现这一点。在上述情况下，它会将整数字面量 `1` 转换为字符串，从而使其可以连接到前面的字符串字面量上。这被称为类型转换。这是 PHP 一个非常强大的功能，但如果您不了解它，也可能导致您拔光头发，甚至引发安全问题。

请看下面的例子：

![](Image01217.jpg)

其意图似乎是程序员正在检查变量是否具有值 `1`。但如果 `$variable` 的值是 `"1 and a half"` 会怎样？答案可能会让您感到惊讶。

![](Image01218.jpg)

结果是：

![](Image01219.jpg) bool(true)

为什么会发生这种情况？因为 PHP 意识到字符串 `"1 and a half"` 不是整数，但为了将其与整数 `1` 进行比较，它需要是整数。PHP 不会报错，而是启动类型转换并尝试将变量转换为整数。它通过获取字符串开头所有可以转换为整数的字符并进行转换来实现这一点。一旦遇到无法作为数字处理的字符，就会停止。因此 `"1 and a half"` 被转换为整数 `1`.

诚然，这是一个非常牵强的例子，但它用于演示该问题。接下来的几个例子将涵盖我在真实软件中遇到的由类型转换引起的一些错误情况。

## 第 56.2 节：从文件读取

当从文件读取时，我们想知道何时到达了文件末端。已知 `fgets()` 在文件末端返回 `false`，我们可能会将其用作循环的条件。然而，如果最后一次读取返回的数据恰好是某个评估为布尔值 `false` 的值，会导致我们的文件读取循环过早终止。

![](Image01220.jpg)

如果被读取的文件包含空行，`while` 循环将在该处终止，因为空字符串评估为布尔值 `false`。

相反，我们可以使用严格相等运算符显式检查布尔值 `false`：

![](Image01221.jpg)

注意这是一个牵强的例子；在实际生活中，我们会使用以下循环：

![](Image01222.jpg)

或者用以下代码替换整个内容：

![](Image01223.jpg)

## 第 56.3 节：Switch 语句的惊喜

Switch 语句使用非严格比较来确定匹配。这可能导致一些 [令人不快的惊喜](http://stackoverflow.com/questions/4098104/odd-behaviour-in-a-switch-statement)。例如，考虑以下语句：

![](Image01224.jpg)

这是一个非常简单的语句，当 `$name` 是字符串时按预期工作，但在其他情况下可能会导致问题。

例如，如果 `$name` 是整数 `0`，则比较期间会发生类型转换。然而，被转换的是 `case` 语句中的字面量值，而不是 `switch` 语句中的条件。字符串 `"input 1"` 被转换为整数 `0`，这与输入值整数 `0` 匹配。结果是，如果您提供整数 `0` 的值，第一个 `case` 总是会执行。

此问题有几种解决方案：

**显式转换**

可以在比较前将值转换为字符串：

![](Image01225.jpg)

或者也可以使用已知返回字符串的函数：

![](Image01226.jpg)

这两种方法都能确保值的类型与 `case` 语句中的值类型相同。

**避免使用 switch**

使用 `if` 语句将使我们能够控制比较的方式，从而允许我们使用严格比较运算符：

![](Image01227.jpg)

## 第 56.4 节：严格类型

自 PHP 7.0 起，可以通过 [严格类型](http://php.net/manual/en/functions.arguments.php#functions.arguments.type-declaration.strict) 缓解类型转换的一些有害影响。通过将此 `declare` 语句作为文件的第一行包含进来，PHP 将通过抛出 `TypeError` 异常来强制执行参数类型声明和返回类型声明。

![](Image01228.jpg)

例如，这段使用参数类型定义的代码在运行时将抛出一个可捕获的 `TypeError` 类型异常：

![](Image01229.jpg)

同样，这段代码使用了返回类型声明；如果它尝试返回除整数以外的任何内容，也将抛出异常：

![](Image01230.jpg)

# 第 57 章：Sockets

## 第 57.1 节：TCP 客户端 Socket

创建一个使用 TCP（传输控制协议）的 socket

```
$socket = socket_create(AF_INET, SOCK_STREAM, SOL_TCP);
```

确保 socket 成功创建。`onSocketFailure` 函数来自本主题中的处理 socket 错误示例。

```
if (!is_resource($socket)) onSocketFailure("Failed to create socket");
```

将 socket 连接到指定地址。如果连接失败，第二行将优雅地处理失败。

```
socket_connect($socket, "chat.stackoverflow.com", 6667)
    or onSocketFailure("Failed to connect to chat.stackoverflow.com:6667", $socket);
```

向服务器发送数据

`socket_write` 函数通过 socket 发送字节。在 PHP 中，字节数组由字符串表示，通常不区分编码。

![](Image01234.jpg)

从服务器接收数据

以下片段使用 `socket_read` 函数从服务器接收一些数据。

将 `PHP_NORMAL_READ` 作为第三个参数传递，将读取直到遇到 `\r` / `\n` 字节，且该字节包含在返回值中。

相反，传递 `PHP_BINARY_READ` 将从流中读取所需数量的数据。

如果之前调用了 `socket_set_nonblock` 且使用了 `PHP_BINARY_READ`，`socket_read` 将立即返回 `false`。否则，该方法将阻塞，直到接收到足够的数据（达到第二个参数中的长度，或达到行尾），或 socket 关闭。

此示例从假设的 IRC 服务器读取数据。

![](Image01235.jpg)

关闭 Socket

关闭 socket 将释放 socket 及其相关资源。

![](Image01236.jpg)

## 第 57.2 节：TCP 服务端 Socket

Socket 创建

创建一个使用 TCP 的 socket。这与创建客户端 socket 相同。

![](Image01237.jpg)

Socket 绑定

将来自给定网络（参数 2）的特定端口（参数 3）的连接绑定到 socket。

第二个参数通常是 `"0.0.0.0"`，它接受来自所有网络的连接。它也可以

