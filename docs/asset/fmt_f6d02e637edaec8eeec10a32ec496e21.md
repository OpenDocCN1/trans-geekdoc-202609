
```html
results.php
<html>
<head></head>
<body bgcolor="#666660" text="#ffffff">
<table cellpadding="30">
<tr>
<td align="top">
<b>结果</b>
<?php
if($filling) {
    if(is_array($filling)) {
        reset($filling);
        while(list($key, $value) = each($filling)) {
            echo("<br>\n");
        }
    } else {
        echo($filling);
    }
}
?>
</td>
<td align="top">
<b>奶酪</b>
<?php echo($cheese); ?>
</td>
<td align="top">
<b>面包</b>
<?php echo($bread); ?>
</td>
</tr>
</table>
</body>
</html>
```

# 第 27 章 + PHP 与 JavaScript 493

诚然，这个表单目前实际上并没有发挥太大作用——其关键点在于，它可以避免一或多次从客户端到服务器的往返。它还展示了 PHP 开发者通过实验性使用 JavaScript 获得的另一个有趣效果。

## 总结

JavaScript 是一种客户端脚本语言，在处理许多不需要服务器端处理的任务时效率极高。并不是每个人都想使用 JavaScript，因为它长期以来存在易用性和安全性问题；但对于那些需要使用的人来说，客户端和服务器端编程语言的结合可以提供极具吸引力的功能组合。

PHP 和 JavaScript 具有不同的对象表示法。JavaScript 使用所谓的“点”表示法，而 PHP 使用“箭头”或 C++ 风格的表示法。JavaScript 是完全面向对象的的，而 PHP 将对象视为一种可选功能。好消息是，你永远不会将一个 JavaScript 对象误认为 PHP 对象，反之亦然。坏消息是，你无法从这两种语言中访问同一个对象。

通常情况下，可以通过客户端和服务器端的方式来实现同一个功能。开启 JavaScript 的浏览器用户可以享受更快的速度和便利性，而没有开启的用户仍然可以获得该功能。这使得考虑使用 JavaScript 变得可能，同时避开了其最大的缺点——即不可预测性导致部分用户群的流失。

或许 PHP 为 JavaScript 提供的最大服务就是实现数据库连接——这导致了我们所说的“动态 JavaScript”。JavaScript 毕竟是纯粹的客户端技术，它无法查询服务器端数据库来获取动态生成内容的数据。如果没有像 PHP 这样的服务器助手，这意味着每当变量数据发生变化时，都必须手动更新 JavaScript。PHP 从数据存储中传递最新变量的能力可以使维护支持 JavaScript 的表单和函数变得不再那么耗费精力。

![](img/5b1cb1f01df587629b183371400fc04a_524_0.png)

# 电子邮件

电子邮件几乎无处不在，基本上是使用 PHP（在某些情况下使用数据库）来发送和接收电子邮件。它假设你对电子邮件系统和协议（如 POP、IMAP 和 SMTP）有基本的了解。

# 理解电子邮件

电子邮件显然是互联网的杀手级应用之一，而且多年来一直基本保持不变。但从 PHP 以及其他邮件列表的帖子来看，即使是现在，还有几个经常被误解或令人沮丧的话题。由于最近的发展，例如更廉价的连接、免费的服务器操作系统以及企业域名的爆炸，让每个人及其祖母都能运行自己的邮件服务器，因此产生了很多挫败感。

我们没有空间或专业知识来解释电子邮件的每一个细节。如果你在简短的概述后对这个主题产生了兴趣，你将希望立即访问国际邮件联盟（International Mail Consortium）网站 `http://www.imc.org`，它将以令人眼花缭乱的细节解释最严苛工程师内心所渴望的互联网邮件的每一个方面和标题。在此期间，我们将坚持最快速、最浅显的解释。

# 一个模型化的电子邮件系统

为了帮助直观理解涉及的大量活动部件，我们将构建一个简单的模型服务器。

这个解释将主要使用 UNIX 术语，简单原因是电子邮件的词汇在 Microsoft 或 Lotus 出现很久以前就已经完善了。Exchange Server 在底层可能非常相似——它甚至有一个名为“sendmail”的守护进程——但我们无法确定这一点，因为我们无法打开盖子查看内部。

# 第 28 章

## 本章内容

- 理解电子邮件
- 使用 PHP 接收电子邮件
- 使用 PHP 发送电子邮件
- 更多电子邮件应用
- 邮件陷阱（gotchas）

# 496 第三部分 高级技巧

专有软件供应商也有一种恼人的习惯，即为某些事物发明自己的术语，而不是使用大家已经熟悉的名字，这种做法极大地阻碍了任何试图理解这些系统的人。由于最近的发展，例如更廉价的连接、免费的服务器操作系统以及企业域名的爆炸，让每个人及其祖母都能运行自己的邮件服务器，因此产生了很多挫败感。我们没有空间或专业知识来解释电子邮件的每一个细节。如果你在简短的概述后对这个主题产生了兴趣，你将希望立即访问国际邮件联盟网站 `http://www.imc.org`。在此期间，我们将坚持最快速、最浅显的解释。模型电子邮件系统的主要部分包括：

- TCP/IP 服务器
- 邮件传输代理 (MTA) a.k. SMTP 服务器
- 用户代理 (MUA) a.k. 客户端
- 邮件检索程序 a.k. POP/IMAP
- 邮件列表管理器 (MLM)

让我们更详细地检查这些部分。支持 JavaScript 的表单和函数。

# TCP/IP 服务器

一种视觉化 TCP/IP 服务器的良好方法是将其想象成 Mail Server 的管家。对于那些开启 JavaScript 的用户，可以享受更快的速度和便利性，而没有开启的用户仍然可以获得该功能。这使得考虑使用 JavaScript 变得可能，同时避开了其最大的缺点——即不可预测性导致部分用户群的流失。

众知的 TCP/IP 服务器包括：

- `inetd`，通常在 UNIX 上 (`http://www.gnu.org/software/inetutils/inetutils.html`)
- `xinetd`，`inetd` 的安全替代 (`http://www.synack.net/xinetd/`)
- Dan Bernstein 的 `tcpserver`，通常配合 `qmail` 使用 (`http://cr.py.to/ucspi.html`)

# 邮件传输代理 . SMTP 服务器

邮件传输代理 (MTA) 是任何邮件服务器的核心，也是我们正在极大简化的部分。

MTA 最重要的任务是从另一个 SMTP 服务器接收电子邮件，并将其递送到正确的收件者的邮件池中。这涉及的内容比想象的要多得多。此外，MTA 还会收集出的邮件并尝试将其发送到其他 SMTP 服务器。

所以 MTA 大致处于 Mail Mansion 管家那样的位置。它被脚童召唤来处理邮件，询问访客（当然是极其礼貌地）：“你是谁？你想什么？”如果访客恰好是已知的垃圾邮件发送者，例如，管家可能会拒绝该地址的邮件。如果访客未被识别为 Mail Mansion 的居民，他会在信封上写下“地址无效”并将其投入出站邮件包。最后，如果收件人被识别且信息良好，管家会将信封放在银托盘上，送到居民的休息室并留在那里。

实际的 SMTP 协议——一个服务器询问另一个服务器“你是谁？你想什么？”的脚本——大致如下（`sendhost` 和 `receipthost` 是虚拟用户名）：

```
220 receipthost SMTP
HELO
250 receipthost
MAIL From:<sender@sendhost>
250 ok
RCPT TO:<receiver@receipthost>
250 ok
DATA
354 Go ahead
Body of message.
250 Message accepted for delivery
QUIT
221 receipthost closing connection
```

# 498 第三部分 ♦ 高级技术

众知的 MTA（邮件传输代理）以及相应的 URL 如下：

| Sendmail | http://www.sendmail.org |
| Qmail | http://www.qmail.org |
| Zmailer | http://www.zmailer.org |

## 邮件轮拨 (Mail spool)

管家将信件放在银托盘上的动作类比于邮件轮拨或邮箱。不同的邮件系统使用不同类型的邮箱。在我们所讨论的层级，主要的区别在于新消息是简单地追加到单个长轮拨的末尾（就像按照接收时间将你转录过的所有邮件顺序写在一张长纸上），还是每条消息都成为目录内部的一个独立文本文件。

一些知名的邮箱格式有：

| mbox | 被许多 UNIX 邮件客户端使用 |
| maildir | 与 qmail 密切相关 |
| mbx | 微软专有格式 |

## 邮件用户代理 (Mail User Agent)，又名本地邮件客户端

现在，信件躺在收件者客厅的银托盘上，而客厅实际上是他们的家庭域名。当邮件服务器大厦的一位居民决定想读邮件时，她会派遣一名女佣去客厅，收集管家留在那里的装满信件的银托盘，带着它们回到卧室，并对着光举起以便她更有格调地阅读。这名女佣就是邮件用户代理（MUA）。

流行的 MUA 及其 URL 包括：

| Pine | http://www.washington.edu/pine |
| Elm | http://www.instinct.org/elm |
| Mutt | http://www.mutt.org |

在很多情况下，MUA 的选择与 MTA 和邮箱的选择紧密相关。例如，Mutt 使用 Qmail 的 `maildir` 社区变得非常易用，而且它似乎是 Qmail 社区的首选 MUA。

## 邮件取回程序 (Mail retrieval program)，又名 POP/IMAP

如果你正好在本地域名的家里，派遣女佣去客厅取邮件就行得通。假设邮件服务器大厦的居民经常去远程域名旅行（记住，远程域名在“本地”的意义上不是由该特定邮件服务器处理的域名之一，它是远程的）。他们将如何获取邮件呢？

# 第 28 章 ♦ 电子邮件 499

简短的答案是，他们会定期向邮件服务器大厦发送请求，另一个管家会转发自上次以来收集在地址对应银托盘上的任何信件。这第二个管家完全不接受邮件——他只负责转发。

这第二个管家需要非常有安全意识。SMTP 管家为他已知居住在住户内的人收发信件是一回事，但任何人都可以请求将邮件转发到某个遥远的地址。因此，二号管家与邮件大厦的每位居民都约定了秘密密码，没有该密码的邮件将不会被转发。

这些电子邮件可以在远程邮件客户端上阅读——越来越多的客户端是基于 Web 且免费或低成本的——例如：

- Microsoft Outlook `http://www.microsoft.com/windows/IE`
- Netscape Communicator `http://www.netscape.com/download/index.html`
- Qualcomm Eudora Light `http://www.eudora.com`
- Hotmail `http://www.hotmail.com`
- AOL 邮件客户端 `http://www.aol.com`

实现邮件取回程序的结果之一是每个平台的客户端都能接收来自 UNIX 服务器的邮件。MUA 仅限于 UNIX 客户端，最好是本地 UNIX 客户端。

有多种邮件取回协议；以及大量产品（通常设计迥然不同）实现了这些协议。最流行的被称为 POP3 和 IMAP。

POP 服务器（有时称为 POP 烤箱机）仅通过与客户端进行这种简单的对话，来验证用户名、密码和邮件池位置。

```
user peter
+OK
pass rabbit
+OK
data
```

检查文件中的答案，并查找该用户的邮箱所在地。如果有新消息，它将它们转发给客户端。某些 POP 系统可以配置为保存转发给客户端的每条消息的副本，但大多数系统是转发后即忘记。用户可以花任何需要的时间离线阅读和回复消息，然后连接到 SMTP 服务器发送回复。

# 500 第三部分 高级技术

流行的 POP 服务器包括：

- Qualcomm Qpopper `http://www.eudora.com/qpopper/index.html`
- qmail-pop3d `http://www.qmail.org`

此外，大多数名声户外的 IMAP 服务器也实现了 POP3 协议。PHP 的 IMAP 函数也可以作为 POP 函数工作。

IMAP 是一种更现代、更强大的邮件取回协议。IMAP 不是转发后即忘记，而是允许模拟本地客户端/服务器的体验。潜在的劣势是，与相对快速的 POP3 数据转储不同，只要用户在阅读和回复电子邮件，客户端必须保持与 IMAP 服务器的连接——因此该过程非常消耗资源。IMAP 服务器的学习、安装、配置和维护要困难得多。

最流行的 IMAP 服务器是：

- Washington IMAP `http://www.washington.edu/imap`
- Cyrus `http://asg.web.cmu.edu/cyrus`

还有一类被称为邮件取回工具的程序。其中最著名的是 Eric Raymond 的 Fetchmail (`http://www.tux.org/~esr/fetchmail`)，它对于拨号连接特别有用。它实现了 POP、IMAP 以及其他协议。

## 邮件列表管理器 (Mailing List Manager)

最后，一个邮件服务器没有列表管理器是不完整的。这是一种帮助自动发送大量邮件的软件包。将这个程序视为邮件大厦的秘书：她的工作是处理所有的回复。

常见的 MLM 有：

- Majordomo `http://www.greatcircle.com/majordomo`
- Ezmlm 对于 qmail，`http://www.ezmlm.org`

所以你有了模型服务器。现在，定义大部分术语后，我们可以继续本章的其余部分。

## 使用 PHP 接收电子邮件 (Receiving E-Mail with PHP)

基于 Web 的客户端——从 POP/IMAP 服务器下载邮件并通过 SMTP 转发邮件——正在占据越来越大的市场。PHP 是开发这些实用应用程序的工具之一。

然而，我们无法想象从零开始编写这个项目——任何能这样做的人都不会。因此，我们对邮件客户端的讨论将集中在如何（正如永恒的 Tina Turner 所说）轻松地完成。

## 拒绝开发 (Development by denial)

用 PHP 获取一个良好的 POP3 客户端的唯一简单方法就是放弃它。除非你有大量的空闲时间，否则仔细考虑你是否真的需要自己的自定义 POP 客户端。全世界的免费邮件服务几乎是在付给你使用它们的服务，你可以使用它们连接到任何 POP 服务器。极其安全的 Web 应用（如 Hushmail）也开始出现在市场上，消费者无需付费。我们个人乐意让大型门户网站的工程师为我们处理个人邮件。

## 引导开发 (Development by direction)

如果你由于特殊且紧迫的原因确实需要用 PHP 编写自己的 POP3 专用客户端，请通过 Manuel Lemos 的邮件类来让自己减轻负担。一位著名的 PHP 社区成员提供了一个用于 POP3 的类、一个用于 SMTP 的类以及一个用于编写 MIME 消息的类。但在此基础上的一些已经完成了一半。你可以在这里找到它们：

```
http://phpclasses.upperdesign.com/browse.html/class/2
```

更棒的是，一个功能极其强大、时尚且支持良好的 IMP 客户端名为 IMP，根据 GPL 协议从那些运行的系统中提供：

```
http://www.horde.org/imp
```
