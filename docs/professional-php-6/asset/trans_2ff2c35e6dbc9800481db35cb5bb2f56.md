

## 基本 PHP 会话

输入以下代码并将其保存为 firstpage.php：

```php
<?php
session_start();
$_SESSION['favorite_artist'] = 'Tori Amos';
?>
Currently, my favorite artist is Tori Amos. It may also interest you to know that my identifier for this browser session, as allocated by PHP, is
<?=session_id()?>.
<BR><BR>
<A href="secondpage.php">Go to the second page</A>
```

现在开始一段全新的代码。将此命名为 secondpage.php：

```php
<?php
session_start();
?>
Having checked, I can tell you that my favorite artist is still
<?=$_SESSION['favorite_artist']?>. At the moment, my identifier for this browser session, as allocated by PHP, is<?=session_id()?>.
<BR><BR>
<A href="firstpage.php">Go back to the first page</A>
```

运行其中的第一个，你应该会得到一些可预测的输出。假设你最喜欢的艺术家是 Tori Amos，PHP 已为你分配了一个会话标识符，如以下输出所示：

Currently, my favorite artist is Tori Amos. It may also interest you to know that my identifier for this browser session, as allocated by PHP, is balq167mlgor56oqjlc5eldca2. Go to the second page

你可以看到会话标识符长度为 26 个字符。PHP 实际上使用了完整的字母表，以及 0–9。这使得可能的会话标识符数量增加到 36^26。如果你单击链接转到第二页，你应该会看到类似这样的内容：

Having checked, I can tell you that my favorite artist is still Tori Amos. At the moment, my identifier for this browser session, as allocated by PHP is balq167mlgor56oqjlc5eldca2. Go back to the first page

此处需注意两点重要事项。会话标识符是相同的，第二个脚本似乎记住了你的音乐偏好。

这种结果以直接的方式获得。首先，使用 session_start() 告诉 PHP 启用会话，且要在脚本的第一个 HTML 字符之前很久使用。使用 session_start() 很重要，因为发送到 Web 浏览器的会话数据必须放在 HTTP 标头中，而一旦使用任何 HTML（甚至空白字符），就会阻止这种情况发生。

其次，通过向 `$_SESSION` 全局关联数组（或 *哈希*）添加内容来注册会话变量。这可以放在脚本中的任何位置，因为它不会向 Web 浏览器发送任何内容。它只是在服务器端做个记录，你很快就会看到。

在第二页上，像在第一页上一样调用 `session_start()` 来启用会话管理，但现在你可以像在第一页上写入一样从 `$_SESSION` 读取。不出所料，Tori Amos 的值已成功从一个页面保留到下一个页面。这个值已与会话标识符不可分割地关联，这就是服务器记住它的原因。

PHP 如何从第一页记住会话标识符到第二页？查看你服务器上的 `/tmp`。使用 `ls` 对所有以 `sess_`（单词 sess 后跟下划线）开头的文件进行目录列表：

```
$ cd /tmp
$ ls -la sess_*
```

希望你会看到类似这样的目录列表：

```
-rw-r--r-- 1 nobody users 33 2008-08-17 15:23 sess_balq167m1g0r56oqjlc5e1dca2
```

注意一个名为 `sess_` 后跟上一示例中分配给你的会话 ID 的文件。使用你选择的编辑器打开它：

```
pico -w sess_balq167m1g0r56oqjlc5e1dca2
```

你应该会看到类似这样的内容：

```
favorite_artist|s:9:"Tori Amos";
```

对于 Windows 用户，PHP 会话最可能存储在 `C:\\TEMP` 中，但这取决于你如何配置 PHP 和 Apache（或你选择的 Web 服务器）。如果找不到任何文件，可以使用 Windows 内置的搜索功能查找以 `sess_`（会话，后跟下划线）开头的文件。不要忘记包含隐藏文件和文件夹。找到会话后，可以使用记事本或类似的文本编辑器打开它。

会话文件的输出看起来非常直接。希望你注意到你创建的会话变量及其以简单“键-值”对形式的纯文本内容。

实际上，显示的内容可能会让你感到眼熟。这是 PHP 函数 `serialize()` 的输出，即 PHP 数据结构的字符串表示。

无论你在 `$_SESSION` 变量中创建的数据结构多么复杂或大，PHP 都会默认将其内容存储在此文件中。存储此类文件的位置以及存储时间，都是可以在 `php.ini` 中更改的设置。

原生 PHP 会话基本就这么多。现在让我们来看看它们的一些局限性，以了解为什么它们不能用于企业环境。

### 基本 PHP 会话的局限性

以这种方式实现会话存在几个关键问题，其中大部分都与 PHP 在磁盘上存储会话数据的方式有关。

如果你有多台 Web 服务器通过负载均衡设备以轮询方式在它们之间分配流量来处理请求，该怎么办？你将不得不实现某种共享的 `/tmp`（使用 NFS），这将慢得令人绝望。

其次，如果你在共享 Web 服务器上运行（例如，与托管公司一起），`/tmp` 的目录列表对所有人都是可读的，即使其文件内容不可读。鉴于 PHP 将会话标识符用作文件名的一部分，该 Web 服务器上的恶意用户可以非常轻松地获取创建的所有会话标识符的完整列表，以及它们的创建时间。这将再次为轻松的会话劫持敞开大门，如前所述。

第三，这种会话处理实现并不十分安全。前面讨论的任何额外安全措施都未被采用，在这种状态下也很难采用它们。因此，就使用会话的生产 Web 站点的安全环境而言，原生状态下的 PHP 会话处理确实不是一个可行的选择。

第四个限制是速度。通过在磁盘上存储会话数据，PHP 几乎需要在每个请求中读写磁盘。这会让磁盘一直很忙（实际上是不必要地忙），并减慢所有相关方的请求速度。因此，单台服务器能够维持的流量水平会降低，可能会增加你对更高硬件预算的风险。

最后，鉴于你将应用程序的其余数据存储在数据库中，你必然会有时需要构建同时查询会话变量和数据库表的查询。由于会话数据完全在数据库之外，你必须先使用 PHP 提取该数据，然后将其注入 SQL 语句。与执行单个 SQL 查询来提取所需数据相比，这种方法与严重的性能影响相关。例如，在生产服务器上，这可能会变得相当严重。解决此问题的方法是将 PHP 会话管理与数据库集成。

### 创建身份验证类

在本章的最后部分，你将学习如何将 PHP 的会话处理技术调整为与 PostgreSQL 数据库通信，该数据库将用于存储迄今存储在磁盘上的会话数据。同时，你将组合一个类来处理用户身份验证，你应该能够在任何项目中重用它。

### 将 PHP 会话管理连接到数据库

让 PHP 使用数据库而不是服务器的磁盘来存储其数据，比你想象的要容易得多。以下示例使用 PostgreSQL，但这种方法可以轻松适应 MySQL、XML 扁平文件或任何你偏好的方式。

这一切的关键只有一个 PHP 函数：session_set_save_handler。如果你查看该函数的 PHP 手册参考条目，可以非常清楚地看到其语法：

```
bool session_set_save_handler ( string open, string close, string read, string write, string destroy, string gc)
```

其理念很简单。在任何使用会话的页面上使用 session_start() 之前调用此函数。该函数指示 PHP 在发生某些会话行为时调用哪些自定义函数（例如，启动会话、结束会话、读取、写入或销毁会话时）。关于传递给这些方法的参数以及它们必须返回的值，有一些要求。这些在 PHP 手册的 session_set_save_handler 页面上有详细说明，但以下部分介绍了基础知识。

#### open() 函数

每当调用 session_start() 时，就会调用 open() 函数。PHP 传递两个值：如果会话要保存在磁盘上，它认为会话应存储的路径（在本次讨论中可以忽略）以及它用于会话的 cookie 名称（例如，PHPSESSID）。它需要返回 true 值，才能让 PHP 认为会话已成功创建。

#### close() 函数

close() 函数（不要与 destroy() 函数混淆）在任何使用会话处理的 PHP 脚本执行结束时有效调用。就你的目的而言，它除了返回 true 值之外不需要做任何其他事情，尽管如果不再使用数据库连接，关闭它可能会不错。在大多数生产环境中，你将使用一个已为其他目的打开的全局可访问的数据库句柄，因此你无疑会在脚本结束时有代码来再次关闭它。因此，在实践中，此函数只需要返回 true 值。

#### read() 函数

每当尝试从 $_SESSION 哈希中检索变量时，就会使用 read() 函数。它将会话标识符作为其唯一操作数，并期望返回 $_SESSION 整体的序列化表示。你实际上不会在类中使用此函数，因为你将进行自己的会话变量处理。

#### write() 函数

每当尝试更改或添加到 $_SESSION 时，就会使用 write() 函数。它将会话标识符，后跟 $_SESSION 的预序列化表示，作为其两个参数。它期望如果数据成功提交则返回 true。即使未注册会话变量，也会调用此方法，而且这是首次向你揭示生成的会话 ID。

#### destroy() 函数

每当代码中使用 session_destroy 函数时，就会调用 destroy() 函数。执行时必须返回 true。

