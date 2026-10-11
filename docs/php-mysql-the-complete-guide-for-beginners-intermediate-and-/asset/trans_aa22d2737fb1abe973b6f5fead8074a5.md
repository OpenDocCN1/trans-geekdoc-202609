
现在我们得到... `int(3) 0 => foo 1 => 2 => baz` 导入到 `SplFixedArray` 并从 `SplFixedArray` 导出

你也可以使用 `fromArray` 和 `toArray` 方法将普通的 PHP 数组导入到 `SplFixedArray` 中并从中导出。

![](Image01527.jpg)

1 2 3 4 5

反向操作。

![](Image01528.jpg)

![](Image01529.jpg)

1 2 3 4 5

# 第 81 章：IMAP

## 第 81.1 节：连接到邮箱

要对 IMAP 账户执行任何操作，首先需要连接到它。为此，你需要指定一些必需的参数：

- 邮件服务器的服务器名称或 IP 地址
- 你希望连接的端口

| 协议 | 端口 |
| --- | --- |
| IMAP | 143 或 993 (安全) |
| POP | 110 或 995 (安全) |
| SMTP | 25 或 465 (安全) |
| NNTP | 119 或 563 (安全) |

- 连接标志（见下文）

| 标志 | 说明 | 选项 |
| --- | --- | --- |
| `service` | 使用哪种服务 | `imap`, `pop3`, `nntp`, `smtp` |
| `user` | 用于在服务器上登录的远程用户名 | |
| `authuser` | 远程认证用户；如果指定了此项，则使用该用户名的密码（例如管理员） | |
| `anonymous` | 作为匿名用户远程访问 | |
| `debug` | 在应用程序的调试日志中记录协议遥测数据 | |
| `secure` | 不要通过网络传输明文密码 | |
| `norsh` | 不要使用 rsh 或 ssh 来建立预认证的 IMAP 会话 | |
| `ssl` | 使用安全套接字层加密会话 | |
| `validate-cert` | 验证来自 TLS/SSL 服务器的证书 | 启用 |
| `novalidate-cert` | 不验证来自 TLS/SSL 服务器的证书，如果服务器使用自签名证书则需要此项。谨慎使用 | 禁用 |
| `tls` | 强制使用 start-TLS 加密会话，并拒绝连接到不支持它的服务器 | |
| `notls` | 不要使用 start-TLS 加密会话，即使服务器支持它 | |
| `readonly` | 请求以只读模式打开邮箱（仅限 IMAP；在 NNTP 上被忽略，在 SMTP 和 POP3 上会报错） | |

你的连接字符串看起来会像这样：

![](Image01531.jpg)

请注意，如果连接字符串中的任何字符是非 ASCII 字符，则必须使用 `utf7_encode($string)` 对其进行编码。

要连接到邮箱，我们使用 `imap_open` 命令，它返回一个指向流的资源值：

![](Image01532.jpg)

## 第 81.2 节：安装 IMAP 扩展

要在 PHP 中使用 [IMAP 函数](http://www.php.net/imap)，你需要安装 IMAP 扩展：

**Debian/Ubuntu 与 PHP5**

![](Image01533.jpg)

**Debian/Ubuntu 与 PHP7**

![](Image01534.jpg)

**基于 YUM 的发行版**

![](Image01535.jpg)

**Mac OS X 与 php5.6**

![](Image01536.jpg)

## 第 81.3 节：列出邮箱中的所有文件夹

一旦你连接到了邮箱，你会想看看里面的内容。第一个有用的命令是 `imap_list`。第一个参数是从 `imap_open` 获取的资源，第二个是你的邮箱字符串，第三个是模糊搜索字符串（`*` 用于匹配任何模式）。

![](Image01537.jpg)

输出应该看起来类似于这样：

![](Image01538.jpg)

你可以使用第三个参数来过滤这些结果，如下所示：

![](Image01539.jpg)

```
$folders = imap_list($mailbox, "{imap.example.com:993/imap/tls/secure}", "*.Sent");
```

| Sent |
| --- |

现在结果只包含名称中带有 `.` 的条目：

![](Image01540.jpg)

**注意**：使用 `*` 作为模糊搜索将递归返回所有匹配项。如果你使用 `%`，它将仅返回当前指定文件夹中的匹配项。

## 第 81.4 节：在邮箱中查找消息

你可以使用 `imap_headers` 返回邮箱中所有消息的列表。

![](Image01541.jpg)

结果是一个字符串数组，具有以下模式：

![](Image01542.jpg)

```
[标志] [消息-ID])[DD-MM-YYYY] [发件人地址] [主题截断至 25 字符] ([大小] 字符)
```

以下是每行可能的样子示例：

```
A       1)19-Aug-2016 someone@example.com Message Subject (1728 chars)
D       2)19-Aug-2016 someone@example.com RE: Message Subject (22840 chars)
U       3)19-Aug-2016 someone@example.com RE: RE: Message Subject (1876 chars)
N       4)19-Aug-2016 someone@example.com RE: RE: RE: Message Subje (1741 chars)
```

| 符号 | 标志 | 含义 |
| --- | --- | --- |
| A | Answered | 消息已回复 |
| D | Deleted | 消息已删除（但未移除） |
| F | Flagged | 消息被标记/加星以引起注意 |
| N | New | 消息是新的且未被查看 |
| R | Recent | 消息是新的且已被查看 |
| U | Unread | 消息未读 |
| X | Draft | 消息是草稿 |

请注意，此调用可能需要相当长的时间来运行，并可能返回一个非常大的列表。

```
imap_num_msg($mailbox)
```

另一种方法是根据需要单独加载消息。你的每封电子邮件都会被分配一个从 1（最旧）到 `imap_num_msg($mailbox)` 值的 ID。

有许多函数可以直接访问电子邮件，但最简单的方法是使用 `imap_header`，它返回结构化的头部信息：

![](Image01544.jpg)

![](Image01545.jpg)

# 第 82 章：HTTP 认证

在本主题中，我们将制作一个 HTTP 头部认证脚本。

## 第 82.1 节：简单认证

**请注意：仅将此代码放在页面的头部，否则将无法工作！**

![](Image01546.jpg)

# 第 83 章：WebSockets

Socket 扩展的使用实现了基于流行的 BSD sockets 的套接字通信函数的低级接口，提供了作为套接字服务器和客户端的可能性。

## 第 83.1 节：简单的 TCP/IP 服务器

基于 PHP 手册中找到的示例的最小示例：[http://php.net/manual/en/sockets.examples.php](http://php.net/manual/en/sockets.examples.php)

```
telnet 127.0.0.1 5000
```

创建一个监听 5000 端口的 websocket 脚本。使用 putty、终端运行（localhost）。

此脚本会回复你发送的消息（作为 ping-back）。

![](Image01547.jpg)

![](Image01548.jpg)

# 第 84 章：BC Math（二进制计算器）

| 函数 | 说明 | 参数 |
| --- | --- | --- |
| `bcadd` | 将两个任意精度数字相加。 | `left_operand` (string)：左操作数。<br>`right_operand` (string)：右操作数。<br>`scale` (int, 可选)：结果中小数点后的位数。 |
| `bccomp` | 比较两个任意精度数字。 | `left_operand` (string)：左操作数。<br>`right_operand` (string)：右操作数。<br>`scale` (int, 可选)：比较中使用的小数点后位数。 |
| `bcdiv` | 将两个任意精度数字相除。 | `left_operand` (string)：左操作数。<br>`right_operand` (string)：右操作数。<br>`scale` (int, 可选)：结果中小数点后的位数。 |
| `bcmod` | 获取任意精度数字的模数。 | `left_operand` (string)：左操作数。<br>`modulus` (string)：模数。 |
| `bcmul` | 将两个任意精度数字相乘。 | `left_operand` (string)：左操作数。<br>`right_operand` (string)：右操作数。<br>`scale` (int, 可选)：结果中小数点后的位数。 |

