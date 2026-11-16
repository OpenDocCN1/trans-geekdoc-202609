

BODY命令仅获取正文部分：

```
BODY 71
222 71 <95kvcb$qcn$3@toye.p.sourceforge.net> body
Wow it works!
.
```

HEAD命令仅显示头部块：

```
HEAD 71
221 71 <95kvcb$qcn$3@toye.p.sourceforge.net> head
Path: localhost!lists.php.net!php-test-return-122-news-php.test-toye.php.net
From: neobundy@dreamwiz.com
Newsgroups: php.test
Subject: Does it work?
Date: 4 Feb 2001 17:24:33 -0800
Lines: 2
Approved: php-test@lists.php.net
Message-ID: <95kvcb$qcn$3@toye.p.sourceforge.net>
NNTP-Posting-Host: localhost.localdomain
X-Trace: toye.p.sourceforge.net 981336273 27765 127.0.0.1 (5 Feb 2001 01:24:33 GMT)
X-Complaints-To: news@news.php.net
NNTP-Posting-Date: 5 Feb 2001 01:24:33 GMT
Mailing-List: contact php-test-help@lists.php.net; run by ezmlm
X-To: php-test@lists.php.net
X-Lines: 1
Xref: localhost php.test:71
.
```

发出QUIT命令向新闻服务器道别：

```
QUIT
205 .
Connection closed by foreign host.
#
```

## NNTP服务器响应代码

与SMTP一样，NNTP服务器返回一个三位数的响应代码，后跟注释字符串。响应代码的第一个数字表示前一条命令的成功、失败或进度：

| 响应代码 | 描述 |
|---|---|
| 1xx | 信息性消息 |
| 2xx | 命令成功 |
| 3xx | 命令到目前为止成功，发送其余部分（例如发布文章） |
| 4xx | 命令本身正确，但因某种原因无法执行 |
| 5xx | 命令未实现、不正确，或发生了致命程序错误 |

代码中的第二个数字表示功能响应类别：

| 响应代码 | 描述 |
|---|---|
| x0x | 连接、设置和杂项消息 |
| x1x | 新闻组选择 |
| x2x | 文章选择 |
| x3x | 分发功能 |
| x4x | 发布 |
| x8x | 非标准（私有实现）扩展 |
| x9x | 调试输出 |

某些服务器响应包含数字和名称等参数。例如，当我们使用数字参数71发出ARTICLE命令时，服务器响应：

```
ARTICLE 71
220 71 <95kvcb$qcn$3@toye.p.sourceforge.net> article
```

通常，1xx代码可以忽略或按需显示。代码200或201在初始连接到NNTP服务器时发送，具体取决于发布权限：200表示“允许发布”，201表示相反。当NNTP服务器断开连接时会返回代码400，5xx代码表示命令因某种原因无法执行。

本章将使用的一组选定命令的可能服务器响应代码列在以下表格中：

| 命令 | 响应代码 |
|---|---|
| 建立连接时 | 200 – 允许发布<br>201 – 不允许发布 |
| ARTICLE<br>BODY<br>HEAD<br>NEXT | 服务器维护一个指向当前文章的内部指针（您可以使用NEXT命令将此指针移动到下一篇文章）<br>220 – 已检索包含头部和正文块的文章<br>221 – 已仅检索头部块的文章<br>222 – 已仅检索正文块的文章<br>223 – 内部指针已设置为该文章，请单独请求文本<br>412 – 未选择新闻组<br>420 – 未选择当前文章（NEXT）<br>423 – 该组中不存在这样的文章编号<br>430 – 未找到这样的文章 |
| GROUP | 211 – 已选择组<br>411 – 不存在这样的组 |
| LIST | 215 – 以下是新闻组列表 |
| POST | 340 – 命令正确，发送文章<br>240 – 文章已成功发布<br>441 – 发布失败<br>440 – 不允许发布 |
| QUIT | 205 – 正在关闭连接 |
| 其他 | 400 – 服务已停止<br>500 – 命令未识别<br>501 – 语法错误<br>502 – 访问限制或权限被拒绝 |

要向特定新闻组发布文章，您需要使用正则表达式测试每个命令的服务器响应代码，如下所示：

- **建立连接时**
  如果返回201代码，我们无法在此新闻服务器上发布文章。

- GROUP
  如果返回411代码，指定的组不存在。

- POST
  最初服务器应响应340代码。如果返回440，则不允许发布。发送文章数据后，应返回240代码；否则表示发布失败。

- QUIT
  我们应该从服务器获得205代码。

您不必担心其他命令，因为它们将在下一章中讨论的PHP IMAP函数中实现。NNTP唯一缺少的功能是发布。在下一节中，我们将创建一个NNTP类来填补这一空白。但是，我们不是看到一些特定于NNTP的新头部吗？我们需要先处理掉它们。

## 新闻文章的结构

如您所见，文章很像电子邮件消息。前面描述的大多数电子邮件头部也会包含在文章中。然而，文章没有Cc、Bcc或To等电子邮件特定头部。新闻文章也由头部和正文块组成，两者之间用两个CR/LF对分隔的空行分开：第一个结束最后一个头部字段，第二个单独占一行。每行之间也由CR/LF对分隔。

文章应具有的最小强制性头部如下：

- Path
  文章到达新闻服务器所经历的路径。转发文章的每个新闻服务器都会自动将其名称添加到此头部。每个服务器由路径分隔符"!"分隔。例如：
  localhost!lists.php.net!php-test-return-122-news-php.test-toye.php.net

- From
  文章作者的电子邮件地址。没有此头部无法发布文章，且服务器无法自动生成。例如，Wankyu Choi
  <wankyu@whatever.com>。

- Newsgroups
  应发布文章的一个或多个新闻组。多个组之间用逗号分隔，头部值内部不包含空格。

- Subject
  与可以没有主题的电子邮件消息不同，文章应包含Subject头部字段。如果文章是对另一篇文章的后续回复，主题通常以"Re:"开头。例如，Re: A question!。

- Date
  发布文章的日期和时间与电子邮件消息的格式相同。如果缺失，服务器会创建此头部。例如，4 Feb 2001 17:24:33 -0800。

- Message-ID
  文章的消息ID，与电子邮件消息有相同的限制。例如，<95kvcb$qcn$3@toye.p.sourceforge.net>。

- NNTP-Posting-Host
  用于发布文章的主机名。它由服务器自动添加。例如，news.whatever.com。

其他大量使用的可选头部包括：

- Reply-To
  应向其发送对文章任何回复的电子邮件地址。如果没有此头部，所有电子邮件回复都将发送到From头部中的地址。

- References
  当前文章作为后续回复的先前文章的消息ID列表，由空格分隔。该头部在创建属于新闻组的消息线程列表中起关键作用。例如，References: <95kvcb$qcn$3@toye.p.sourceforge.net> <390F4E9C.80D6BBCB@whatever.net>。

- Approved
  负责批准文章在受管控新闻组中发布的人员的电子邮件地址。

- Lines
  文章正文中的行数。

- Organization
  作者所在机构的名称。

我们不会在此详细介绍新闻文章的所有细节。向新闻组发布文章只需要几个头部。其他头部要么是信息性头部，要么是新闻服务器的控制消息。如需完整讨论，请参阅RFC 1036。

废话不多说，让我们看看如何创建一个NNTP类，帮助您向选定的新闻组发布文章。

## 创建NNTP类

我们将创建的NNTP类在外观上基本与先前构建的SMTP类相同，但我们需要buildHeaders()和talk()方法的新版本。我们可以省略一些电子邮件头部，但需要添加几个新头部。新的talk()方法解析NNTP服务器响应代码。我们可以扩展My_Smtp_Mime_Mail类来创建My_Nntp类。

## 属性

```php
<?php
// my_nntp_class.php

include("./my_smtp_mime_mail_class.php");

class My_Nntp extends My_Smtp_Mime_Mail
{
```

