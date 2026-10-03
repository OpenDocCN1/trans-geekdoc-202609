
## DB_Common 类成员

`DB_Common` 类的方法可以在数据库连接上调用，用于执行查询和从数据库中获取信息等目的。方法包括：

- `DB_Common::affectedRows()`: 返回受查询影响的行数。
- `DB_Common::disconnect()`: 断开数据库连接。
- `DB_Common::getAll()`: 返回查询的所有行。
- `DB_Common::getAlloc()`: 以关联数组的形式返回所有行。
- `DB_Common::getCol()`: 返回指定列中的所有行。
- `DB_Common::get()`: 返回第一行第一列的值。
- `DB_Common::getRow()`: 返回第一行。
- `DB_Common::nextId()`: 允许你对作为主键列的唯一值建立额外控制。
- `DB_Common::query()`: 发送 SQL 查询字符串。

## DB_Result 类成员

`DB_Result` 成员可以在结果集上调用，结果集是在数据库上运行查询后存在的内容。

- `DB_Result::fetchInto()`: 将行提取到指定的变量中。
- `DB_Result::fetch()`: 提取行。
- `DB_Result::free()`: 销毁结果集。
- `DB_Result::numCols()`: 返回列数。
- `DB_Result::numRows()`: 返回行数。

## 模型电子邮件系统

我们的模型电子邮件系统主要组成部分如下：

- TCP/IP 服务器
- 邮件传输代理 (MTA，又称 SMTP 服务器)
- 邮件队列
- 邮件用户代理 (MUA，又称邮件客户端)
- 邮件取回程序，又称 POP/IMAP 服务器
- 邮件列表管理器 (MLM)

让我们更详细地检查这些内容。对于记得这个比喻的人，我们将使用一个俗气但贴切的比喻：邮件服务器大宅。

### TCP/IP 服务器

可视化 TCP/IP 服务器的一种方法是将其看作守在“邮件服务器大宅”门口回答每一次敲门声的门童。实际上，如果你把每一个独立的部分看作一扇门，那么 TCP/IP 服务器更像是一个坐在小隔间里、监控多个出入处视频摄像头的安保人员。在某些情况下，将其想象成一栋只有一扇大门的老式大宅更简单且更具画面感。

门童实际上并不与任何访客说话。他只是在听到敲门声时开门，识别出这种交互的类型，并叫来正确的人（比如管家或快递员）来处理请求。第二个具有说话角色的人将接管工作，找出访客想要什么。

重点不在于开门——而在于知道有一扇门需要打开。TCP/IP 服务器维护着一个它负责的服务列表。

知名的 TCP/IP 服务器包括：

- `inetd`（通常在 Unix 集中默认找到的 TCP/IP 服务器，见 `https://www.google.org/software/inetutils/inetd.html`）
- `xinetd`（`inetd` 的安全替代品，见 `www.xinetd.org`）
- Dan Bernstein 的 `tcpserver`（通常与 `qmail` 一使用，见 `http://cr.yp.to/ucscpi-tcp.html`）

### 邮件传输代理，又称 SMTP 服务器

邮件传输代理是每个邮件服务器的核心，也是我们在本次讨论中从根本上进行简化的部分。

MTA 最重要的任务是从另一个 SMTP 服务器接收邮件，并将其递送到正确收件人的邮件队列中。这涉及的内容比想象的要得多，但我们在这里详述。此外，MTA 还会收集发出的邮件并发送到其他 SMTP 服务器。

因此，MTA 的位置大致相当于服务器大宅的管家。他被门童传唤来处理邮件，并询问访客（当然是极有礼貌地）：“你是谁，你想什么？”如果访客恰好是已知的垃圾邮件发送者，管家可能会拒绝接收来自该地址的任何信件。如果访客未识别为垃圾邮件发送者，管家将检查信封，确认预期收件人是否是邮件大宅的居民。如果不是，他会在信封上写“退回发件人，地址无法送”，并将其投入信箱。最后，如果收件人被识别且信息良好，管家会将信件放在银盘上，并带到收件人的休息室（实际上是他们的主目录或其他邮件队列位置）并将其留在那里。

实际的 SMTP 协议——一个服务器向另一个服务器请求的对话，“你是谁，你想什么？”——大致如下（`sendhost` 和 `receipthost` 是虚拟服务器）：

```
220 receipthost SMTP
HELO
250 receipthost
Mail From:<sender@sendhost>
250 ok
RCPT TO:<receiver@receipthost>
250 ok
DATA
354 Go ahead
Body of message.
250 Message accepted for delivery
QUIT
221 receipt closing connection
```

知名的 MTA——以及对应的 URL——包括：

- `sendmail` (`www.sendmail.org`)
- `qmail` (`www.qmail.org`)
- `zmmailer` (`www.zmailer.org`)
- `postfix` (`www.postfix.org`)

### 邮件队列

管家放置信件的银盘比比邮件队列箱。不同的邮件系统使用不同类型的邮件存储。在我们所讨论的层面上，主要的区别在于新消息是简单地放在长队列的末尾（类似于目录中一卷上面转录了你收过的所有邮件文本的单卷卷纸），还是成为它自己的一个独立文件。

一些知名的格式：

- `mbox`（Unix 使用）
- `maildir`（与 `qmail` 密切相关）

### 邮件用户代理 (MUA，又称邮件客户端)

邮件用户代理是用户与之交互以读取和发送邮件的软件。它是系统的客户端。

### 邮件取回程序，又称 POP/IMAP 服务器

实现取回程序的结果之一是，现在客户端可以从目录接收邮件。这在连接较慢时特别有用。

POP3（有时被称为 POP）仅仅是验证名称、密码和邮件队列位置。如果有新消息，它会将它们转发给客户端。某些 POP 系统可以配置为远程删除消息，但大多数只会转发并保留。用户可以花任何的时间进行离线阅读和回复，然后连接到 SMTP 服务器发送。

流行的 POP 服务器包括：

- `qpopper` (`www.eudora.com/qpopper/index.html`)
- `qmail-pop3d` (`www.qmail.org`)

IMAP 是一种更新且更强大的邮件取回协议。IMAP 不是转发后即忘记，而是允许本地客户端/服务器体验的模拟。潜在的缺点是，在相对快速的 POP3 数据转储中，只要用户在阅读和回复，每个客户端都必须保持与 IMAP 服务器的连接——因此该过程是相当实时的。IMAP 服务器的学习、安装和维护要困难一些。

最流行的 IMAP 服务器是：

- `Washington` (`www.washington.edu/imap`)
- `Cyrus` (`http://asg.web.cmu.edu/cyrus`)

> 理解 POP 和 IMAP 差异的优秀指南是 Terry Gray 的论文《Messaging Access Paradms and Protocols》，见 `www.imap.org/papers/imap vs.pop.html`。

还有类程序被称为邮件取回。最著名的是 Eric Raymond 的 `Fetchmail` (`http://www.tuxedo.org/eisr/fetchmail`)，它在拨号连接时特别有用。它实现了 POP、IMAP 以及其他协议。

### 邮件列表管理器

最后，没有邮件列表管理器，邮件服务器是不完整的。这是一个帮助自动发送大量电子邮件的软件软件包。将这个程序想象成邮件服务器大宅的社交秘书：她的工作是为无休止的派对发送邀请，由 Mansion 的居民提供。不用多说，她在每次邀请后都必须写出一封又一封的副本——然后将它们分批投入寄出的邮件袋。她还处理所有的回复，使用一套标准脚本进行回答，类似于处理 RSVP 接受回执。

常见的 MLM（多级营销）包括：

- [Majordomo](www.greatcircle.com/majordomo)
- [MailMan](www.list.org)
- [ezml (for qmail)](www.ezml.org)

所以，这就是我们的模型邮件服务器。现在你已经牢牢地掌握了电子邮件的基本架构，剩下的部分就轻而易举了。

## 使用 PHP 接收电子邮件

基于 Web 的邮件客户端——从 POP/IMAP 服务器下载邮件并通过 SMTP 服务器进行中继——因为其便利性和平台无关性，正在占据越来越大的市场。此外，对于那些使用共享或公共计算机的人来说，网页邮箱是可用于开发这些最实用应用程序的工具之一。

如果你想使用自己的 POP 或 IMAP 客户端，现在你拥有所有的开发选项，从从零开始编写到从下拉菜单中选择不同的主题或皮肤。我们按照工作量从多到少的顺序对主要的进行讨论。

### 从零实现

用一句话说：我们可不是在开玩笑。在现在，从零重新实现的唯一可以想象的理由是为了大学项目，在这种情况下，你不需要解释如何做它，因为你想自己思考清楚。

全球的免费网页邮箱提供者几乎是付钱让你使用他们的服务，你可以将其配置为连接任何地方的任何 POP 服务器。此外，ISP 现在在提供连接的同时也提供网页邮箱。极其稀缺的网页邮箱应用程序在不向消费者收取费用的情况下进入市场，非常乐意让大型 Web门户网站勤奋的工程师为我们处理个人电子邮件账户。

如果你下心构建自己的自定义基于 Web 的电子邮件应用，现在有许多完整的 PHP 网页邮箱客户端免费使用并附带源代码，你将不得不刻意把事情做得（正如永恒的 Tina Turner 所说）*优美*……且*简单*。

### 修改他人的 PHP 代码

如果你有某些原因需要用 PHP 编写自己的邮件客户端，请利用“源码”的力量——即开源的力量——让自己稍微轻松一点。至少考虑看一眼代码，看看是否有你尚未想到的事情——考虑到用户行为的随机性，这种情况在消费级应用中非常常见。

对于那些希望获得最小帮助的人，从查看 Manuel Lemos 的电子邮件类开始。作者是 PHP 社区的知名成员，提供了一个用于 POP3 的几个用于 SMTP 的以及一个用于编写 MIME 消息的。在这些基础上添加一些精美的界面，你就成功了一大半。你可以在这里找到它们：

`www.phpclasses.org`

该网站没有标准的 URL；它在世界各地的地点都有镜像。你必须访问上面的 URL 并点击进入特定的镜像，然后进入“E-mail（邮件）”部分。小心使用任何不是由 Manuel 或 Richard 这样已知良好开发者编写的代码。

对于那些想从全功能基于 Web 的电子邮件客户端源代码开始的人来说，现在有很多可用选择。

一个名为 `IMP` 的惊人的、全功能的、时尚且支持良好的 IMAP 和 POP3 客户端由 `Horde.org` (`www.horde.org/imp`) 那些乐于友善的系统提供，并遵循 GPL 协议。

另一个流行的的选择是 `SquareMail`，它是一个符合 HTML 标准的 IMAP 客户端，带有一个酷炫的插件，用于时钟模块或 POP3 获取等扩展功能。这是前五个源码网页邮箱项目之一，位于 `http://squaremail.org`。

在 `SourceForge` 上快速搜索将揭示几个候选者，每个都有自己的优势和哲学。`JaMail` (`http://javmail.org`) 具有其独特的优势。`SourceMail` (`http://sourcemail.org`) 提供了唯一可以想象的理由，在大学项目中重新实现它。`Teak` (`http://teak.org`) 是另一个可以考虑的选项。

```php
<?php
$address = 'receiver@receipthost';
$subject = 'A Sample Subject Line';
$body = 'Body of the e-mail\r\nlines separated by the newline\ncharacter.';
$extra_header = 'From: me@sendhost\r\nbcc:\nphb@sendhost\r\nContent-type: text/plain\r\nX-mailer: PHP/*';
$phpversion();

$mailsend = mail($address, $subject, $body, $extra_header);
echo $mailsend;
?>
```

这个“额外”字段有些奇怪，因为它包含了数类通常情况下会有自己独立字段的类型信息。我们的任务不是好奇这为什么；我们的任务是解释你可能想要放入此字段的各种内容：

> `mail()` 在 PHP 认为它已成功发送了邮件时返回 `TRUE`。它与实际上是否发送或接收了任何邮件没有任何关系。有无数种情况可能出现错误：错误的电子邮件地址、SMTP 守护进程设计或配置错误、本地网络状况等。它返回 `TRUE` 的含义不仅仅是“PHP 已经对输入应用了函数而没有发生严重阻塞”。

## PHP 邮件的更多乐趣

除了使用 PHP 构建完整的邮件客户端外，当你的 Web 网站发生特定事件时，使用 `mail()` 函数发送偶发邮件也是很常见的。

### 从表单发送邮件

从表单发送邮件可能是 PHP `mail()` 函数最流行的应用。它是一个比 HTML 的 `mailto` 链接标签功能强得多的替代方案，后者无疑会导致从客户端机器的邮件程序发送电子邮件。

为什么使用服务器端方法而不是客户端方法来发送邮件？毕竟，在很多情况下，它更慢、更尴尬，而且对于你这个忙于脚的 Web 开发者来说，工作显然更多。可能让你决定选择这种方法的原因包括：

- 你的大部分观众使用浏览器、Web 邮箱或两者。
- 你想对收到的消息实施更严格的语法限制。
- 你想在发送邮件的同时将联系信息存入数据库。
- 你希望减少不需要的邮件（垃圾邮件）。
- 你希望避免从主邮件账户进行 SMTP 中继。

这种基于表单的发送邮件页面可以用于许多用途，例如请求、报告 Bug 和获取技术支持。

列表 37-1 是这类经常发送邮件的类型简单示例。

**列表 37-1：电子邮件表单**

```html
<html>
<head>
<title>titlehelp.html</title>
</head>
<body>
<center>
<table width="550">
<tr bgcolor="FF9933" align="center"><BR>
<h3>The ThrillerGuide.com</h3>
<td><p>那本惊悚小说的名字叫什么？<BR>
表单Form></p></td></tr></tr>
<tr><td>你是否曾读过一本令人难忘的惊悚小说，但现在想不起名字了？请尽力填写下方所有的字段，点击按钮提交，我们将搜索资源并通过电子邮件回给你。</td></tr>
</table>
</center>

<FORM post-ACTION="Titlehelp.php">
<P>名：<input type="text" size=30 name="FirstName">
<P>姓：<input type="text" size=30 name="LastName">
<P>您的电子邮件地址：<input type="text" size=30 name="Email">
<P>书中情节大约发生在哪一年？
<input type="text" size=4 name="Year">
<P>你还记得书中的任何设定吗？
<input type="text" size=30 name="Setting">
<P>主角的性别是： <br>
<ul>
  <input TYPE="radio" NAME="Gender" VALUE=1>女性<br>
  <input TYPE="radio" NAME="Gender" VALUE=2>男性<br>
  <input TYPE="radio" NAME="Gender" VALUE=3>男女各一<br>
  <input TYPE="radio" NAME="Gender" VALUE=4>两个男性<br>
  <input TYPE="radio" NAME="Gender" VALUE=5>两个女性<br>
</ul>
<p>当第一本书出版时，它是：<br>
<ul>
  <input TYPE="radio" NAME="Status" VALUE=1>畅销书<br>
  <input TYPE="radio" NAME="Status" VALUE=2>评论界青睐<br>
  <input TYPE="radio" NAME="Status" VALUE=3>两者都不是<br>
  <input TYPE="radio" NAME="Status" VALUE=4>我不知道<br>
</ul>
<p>请告诉我们关于这部作品你记得的任何事情（情节、角色、设定、颜色、电影版本等）：<br>
<textarea name="Other" ROWS=6 COLS=50></textarea>
<p><input type="submit" name="Submit"></p>
</body>
</html>
```
