

存在一种名为 MMDF 的 mbox 格式变体，其中每条消息都被包含四个 ctrl-A (^^A^^A^^A) 的行所围绕，且各消息之间没有空行分隔。

随着存储在邮箱中的电子邮件数量增长，单一文本文件模型在访问和管理方面变得极其低效。此外，两个客户端无法同时访问同一个邮箱：当另一个客户端尝试访问时，一个客户端可能会失去对邮箱的锁定。为避免此文件锁定问题，每封电子邮件都需要存储为单独的文件。MH 邮箱格式由目录组成，每条消息均存储在单独的文件中。大多数 NNTP 服务器使用与 MH 类似的格式来管理新闻文章。

IMAP 允许你以与操作文件目录几乎相同的方式创建多个邮箱的层次结构。邮箱层次结构的格式因服务器实现而异，但最简单的形式是邮件文件系统格式。在这种格式中，每个邮箱都可以映射到一个目录或文件。INBOX 始终是一个目录。

请注意，UW-IMAP 服务器最终会将消息追加到单个 mbox 格式邮箱中，而 Cyrus 服务器则将每条消息作为邮箱目录中的单独文件维护。Courier-IMAP 服务器的独特之处在于它支持 Qmail 的 Maildir 邮箱格式。在 UW-IMAP 中，两个客户端无法同时访问同一个邮箱：也就是说，如果另一个客户端同时尝试访问，一个客户端可能会失去对邮箱的锁定。Cyrus 和 Courier-IMAP 服务器不受此文件锁定问题的影响。

## IMAP 会话示例

IMAP 会话包含四个不同的状态。由于它支持多个邮箱，您需要先选择一个邮箱才能访问其中的消息：

- 未认证状态：客户端已连接到服务器
- 已认证状态：客户端已成功认证
- 已选择状态：邮箱已成功选择
- 退出状态：客户端发出了 LOGOUT 命令或服务器关闭了连接

现在让我们 telnet 到运行 IMAP 服务器的 localhost：

```
# telnet localhost imap
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
* OK [CAPABILITY IMAP4 IMAP4REV1 LOGIN-REFERRALS AUTH=LOGIN] localhost IMAP4rev1
2000.287 at Tue, 30 Jan 2001 16:15:07 +0900 (KST)
```

服务器用未加标记的响应向您问好（注意响应开头的星号）。

如果您想与服务器进行任何有意义的交互，需要先登录。LOGIN 命令使用两个参数：您的帐户名（也即邮箱名）和密码。请记住，您需要在每条命令前加上标记字符串：

```
WCK001 LOGIN wankyu 12345
* CAPABILITY IMAP4 IMAP4REV1 NAMESPACE IDLE MAILBOX-REFERRALS SCAN SORT THREAD=REFERENCES THREAD=ORDEREDSUBJECT MULTIAPPEND
WCK001 OK LOGIN completed
```

请注意，服务器对您的 `LOGIN` 命令返回了加标记的响应："WCK001 OK LOGIN completed"。您尚未准备好列出或读取消息。您应先选择一个要使用的邮箱。一个名为 `INBOX` 的特殊邮箱用于接收和存储所有传入消息。对于用户 wankyu，他的 `INBOX` 通常是其主目录下的一个目录，例如 `/home/wankyu/Mail/`。使用 IMAP，您可以创建、删除或重命名邮箱。但是，`INBOX` 是您无法随意操作的唯一邮箱。

让我们使用 `SELECT` 命令选择 `INBOX`，并查看服务器如何响应：

```
WCK002 SELECT INBOX
* 10 EXISTS
* 6 RECENT
* OK [UIDVALIDITY 980691555] UID validity status
* OK [UIDNEXT 11] Predicted next UID
* FLAGS (\\Answered \\Flagged \\Deleted \\Draft \\Seen)
* OK [PERMANENTFLAGS (\\* \\Answered \\Flagged \\Deleted \\Draft \\Seen)] Permanent flags
WCK002 OK [READ-WRITE] SELECT completed
```

服务器报告 wankyu 的 `INBOX` 中有 10 条消息，其中 6 条是最近且未读的。

IMAP 邮箱中的消息可以通过其唯一标识符 (UID) 或序列号来引用。消息序列号是从 1 到邮箱中消息总数的相对位置。每添加一条新消息，就会分配一个消息序列号，其值比添加前邮箱中的消息数多 1。出于多种原因，消息序列号可在会话期间重新分配，例如，当消息从邮箱中永久删除时。因此，它们在会话之间使用并不十分可靠。

另一方面，UID 在会话间持久存在，但与消息序列号不同，它们不一定是连续的，尽管 UID 对于保持前一会话的状态特别有用。一个唯一标识符有效性值（本例中为 980691555）与每个邮箱关联以验证 UID，并在邮箱选择时通过 `UIDVALIDITY` 响应码发送。

最近消息是指自上次会话以来送达您邮箱的消息，而“未读”消息是指出现在邮箱中后您尚未阅读的消息。服务器响应包含一条 `FLAGS` 行，用于标记电子邮件的状态，指示服务器支持哪些标志。标志就像文件属性一样，保存有关相关消息的状态信息。各标志在下表中解释：

| 标志 | 说明 |
| :--- | :--- |
| `\\Answered` | 该消息已读并已回复。 |
| `\\Flagged` | 该消息已为某些目的加标记：重要、紧急，或仅表示有待处理事项的便笺。 |
| `\\Deleted` | 该消息已标记为待删除。实际删除发生在客户端退出或发出 `EXPUNGE` 命令时。 |
| `\\Draft` | 该消息不完整，是一份草稿。完成后将稍后发送。 |
| `\\Seen` | 该消息已读。 |

您使用 FETCH 命令读取消息。让我们使用 FETCH 命令读取 INBOX 中的第五条消息。它接受多个参数，第一个参数是消息编号。其余参数可能因您想通过该命令执行的操作而异：

```
WCK003 FETCH 5 BODY[1]
* 5 FETCH (BODY[1] {61}
Don't forget to bring your notebook tomorrow.
Sleep tight.
)
WCK003 OK FETCH completed
```

通过 BODY 参数，您可以指定要检索的消息部分：例如，BODY[0] 用于标头，BODY[1] 用于消息正文。让我们看看这条消息的标头是什么样子：

```
WCK004 FETCH 5 BODY[0]
* 5 FETCH (BODY[0] {452}
Return-Path: <wankyu@whatever.com>
Received: from whatever.com (IDENT:wankyu@whatever.com[192.168.0.2])
    by mail.somewhere.com (8.9.3/8.9.3) with SMTP id WAA29446
    for yonsuk; Sun, 28 Jan 2001 23:18:09 +0900
Date: Sun, 28 Jan 2001 23:18:09 +0900
From: Wankyu Choi <wankyu@whatever.com>
To: yonsuk@whoelse.com
Message-Id: < F890755DE93ED411@ whatever.com>
Subject: Just a Note
)
WCK004 OK FETCH completed
```

您甚至可以使用 BODYSTRUCTURE 参数获取消息结构摘要：

```
WCK005 FETCH 5 BODYSTRUCTURE
* 5 FETCH (BODYSTRUCTURE ("TEXT" "PLAIN" ("CHARSET" "US-ASCII") NIL NIL "7BIT" 61
2 NIL NIL NIL))
WCK005 OK FETCH completed
```

检索标志的方式大致相同：

```
WCK006 FETCH 5 FLAGS
* 5 FETCH (FLAGS (\Seen))
WCK006 OK FETCH completed
```

现在您知道第五条消息已读 (\Seen)。您可以通过将参数用括号括起来将这些组合为单个命令：

```
WCK007 FETCH 5 (BODYSTRUCTURE FLAGS)
* 5 FETCH (BODYSTRUCTURE ("TEXT" "PLAIN" ("CHARSET" "US-ASCII") NIL NIL "7BIT" 61
2 NIL NIL NIL) FLAGS (\Seen))
WCK007 OK FETCH completed
```

让我们看看如何创建邮箱。使用 UW-IMAP 服务器时，用户 wankyu 的邮箱位于其主目录下的名为 Mail 的子目录中：

```
/home/wankyu/Mail/
```

如果他创建另一个名为 work 的邮箱，其主目录中将有一个同名文件：

```
/home/wankyu/work/
```

请注意，要创建邮箱容器（即包含其他邮箱的邮箱目录），需要追加一个尾随的邮箱层次结构分隔符。一些服务器（包括 UW-IMAP）使用正斜杠 "/"，而其他服务器（Cyrus 和 Courier-IMAP）则使用单个点 "."。例如，使用 UW-IMAP，您可以通过以下命令创建邮箱容器：

```
WCK008 CREATE work/
WCK008 OK CREATE completed
```

上述 IMAP 命令创建名为 work 的邮箱容器，它是用户主目录中的一个子目录。另一方面，以下命令创建名为 work 的邮箱文本文件：

```
WCK008 CREATE work
WCK008 OK CREATE completed
```

如果在 work 邮箱容器下创建新邮箱，则会在 work 子目录下生成同名的邮箱文件：

```
/home/wankyu/work/Jan
```

如果从用户主目录开始遍历路径，您将得到邮箱名 work/Jan。

现在通过发出 LOGOUT 命令结束会话：

```
WCK009 LOGOUT
* BYE whatever.com IMAP4rev1 server terminating connection
WCK009 OK LOGOUT completed
Connection closed by foreign host.
#
```

## POP 与 IMAP

上述示例会话仅使用了 IMAP 提供的命令子集。即使是单个 FETCH 命令，也可使用不同的参数集采用多种形式。不过，鉴于其丰富的功能，IMAP 在电子邮件社区中正日益普及。其中一些功能包括：

- IMAP 将您所有的电子邮件消息存储在服务器上，因此您可以随时随地从任何联网计算机访问它们。

