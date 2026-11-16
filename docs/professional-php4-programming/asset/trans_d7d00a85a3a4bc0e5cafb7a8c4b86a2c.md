

| Command | Description | Equivalent PHP Function |
| :--- | :--- | :--- |
| RSTATUS | 显示远程机器或远程文件的状态 | |
| RUNIQUE | 切换本地唯一文件命名的开关 | |
| SEND | PUT 的别名 | |
| SENDPORT | 切换使用 PORT 命令的开关 | |
| SITE | 向远程服务器发送 SITE 命令 | ftp_site() |
| SIZE | 显示远程文件的大小 | ftp_size() |
| STATUS | 显示当前状态信息 | |
| STRUCT | 设置文件传输结构类型 | |
| SUNIQUE | 切换远程机器上存储唯一文件的开关 | |
| SYSTEM | 显示远程系统类型 | ftp_systype() |
| TENEX | 将传输类型设置为 TENEX，实际上已过时 | |
| TRACE | 切换数据包跟踪的开关 | |
| TYPE | 设置文件传输类型 | 通过 ftp_fget()、ftp_fput()、ftp_get() 和 ftp_put() 的调用，按每次调用设置 |
| UMASK | 在远程服务器上设置默认 umask | |
| USER | 向远程系统发送用户名和密码 | ftp_login() |
| VERBOSE | 切换详细模式的开关 | |

## Summary

FTP 非常有用，对于某些任务不可或缺，但也存在某些安全局限性。其中之一是 FTP 以明文形式传输密码。

例如，本章的主要示例提供了通过 Web 访问 FTP 的功能；此功能常用于让用户轻松访问其远程账户上的文件。如果 Web 服务器可以访问用户账户，那么让 Web 服务器将 FTP 连接到自身会更安全，这样密码不会通过 Internet 传输。如果用户账户无法被 Web 服务器的主机访问，但可以被与 Web 服务器主机同处一地的主机访问，那么明智地使用防火墙和虚拟专用网络可以帮助保护 FTP 服务器和用户的密码。

本章涵盖：

- 向 PHP 添加 FTP 支持
- PHP FTP 扩展的基本用法
- 实际示例：
  - 构建 FTP 便捷包装器
  - 构建基于 Web 的 FTP 客户端
- 使用不同的函数
- 按字母顺序排列的函数参考

## 11 E-Mail and News

电子邮件已成为我们生活的一部分，但你是否曾想过电子邮件是如何从你的个人电脑传送到地球另一端的某个人手中的？你的电子邮件客户端程序会要求你指定 POP 或 IMAP 服务器，以及 SMTP 服务器。它们是什么？它们如何协同工作来发送、保存并让你阅读电子邮件？你可能认为互联网电子邮件系统对你来说过于复杂，难以理解，但事实证明，它的核心是一个极其简单的系统。好消息是，使用 PHP，创建可以发送或接收电子邮件和新闻的应用程序出人意料地简单。

Did we say news? Yes, but it's a different kind of news: Usenet. Usenet 是最古老的互联网功能之一，用于大规模信息分发，并提供论坛供人们聚集讨论共同兴趣。Usenet 由成千上万个按主题组织的互联网讨论组（称为 newsgroups）组成。即使 PHP 也有自己的一组 newsgroups，PHP 开发人员、新手和专业人士都在那里分享知识，获取 PHP 社区的最新新闻。在 PHP 中处理 Usenet 新闻与处理电子邮件并无不同。甚至一篇新闻文章与电子邮件也非常相似。

Over the next two chapters, we'll take an in-depth look at e-mail and news, and how you can incorporate related features into your PHP applications.

在接下来的两章中，我们将深入探讨电子邮件和新闻，以及如何将相关功能融入到你的 PHP 应用程序中。

We begin by walking you through the basics of the e-mail system in this chapter. Let's get a sneak preview:

我们将从本章中电子邮件系统的基础知识开始。让我们先睹为快：

- Basics of the e-mail system
- Simple Mail Transfer Protocol (SMTP)
- Sending e-mail in PHP using the `mail()` function
- Sending e-mail in PHP using a remote SMTP server
- [ ] Multipurpose Internet Message Extensions (MIME)
- [ ] Sending MIME e-mail in PHP using the `mail()` function
- [ ] Sending MIME e-mail in PHP using a remote SMTP server
- [ ] Basics of Usenet
- [ ] Posting articles to newsgroups

- 电子邮件系统基础
- 简单邮件传输协议 (SMTP)
- 在 PHP 中使用 `mail()` 函数发送电子邮件
- 在 PHP 中使用远程 SMTP 服务器发送电子邮件
- [ ] 多用途互联网邮件扩展 (MIME)
- [ ] 在 PHP 中使用 `mail()` 函数发送 MIME 电子邮件
- [ ] 在 PHP 中使用远程 SMTP 服务器发送 MIME 电子邮件
- [ ] Usenet 基础
- [ ] 将文章发布到 newsgroups

We'll wrap up this chapter by creating an application with which you can send e-mail or post news articles. The classes we'll be creating in this chapter lay a foundation for a web-based e-mail system presented in the next chapter.

我们将通过创建一个可以发送电子邮件或发布新闻文章的应用程序来结束本章。本章中我们将创建的类为下一章中展示的基于 Web 的电子邮件系统奠定了基础。

### How E-Mail Works

### 电子邮件的工作原理

The e-mail system is nothing but an electronic representation of the real-life postal system. When you want to mail a letter, you write one on paper, enclose it in an envelope, and put it into a nearby mailbox. A mailman doing his next round collects your letter, and gets it to the post office. The post office determines whether the letter can be delivered locally (the recipient lives in the same district) or it should be tossed over to a remote post office (the recipient lives hundreds or thousands of miles away). The post office at the receiving end tasks another mailman to deliver the letter to its recipient.

电子邮件系统只不过是现实生活中邮政系统的电子化体现。当你想寄信时，你在纸上写一封信，把它放进信封，投进附近的邮箱。邮递员下次送邮件时会收走你的信，并将其送到邮局。邮局会判断信件是否可以本地投递（收件人住在同一个地区），或者应该转交给远程邮局（收件人住在成百上千英里之外）。接收端的邮局会派遣另一名邮递员将信件送达收件人。

To send or receive e-mail, all you need to have is an e-mail address of the recipient. Your e-mail account is safeguarded by the password of your choice. You can create e-mail accounts in various ways. If you have an account with an Internet service provider, you may already have a POP (Post Office Protocol) account. You don't even have to spend a dime to get a web-based e-mail account with free e-mail service providers like Hotmail and Yahoo. Web-based e-mail is usually implemented upon what is called IMAP. You can have as many e-mail addresses as your memory goes, that is, if you can memorize all those address and password combinations.

要发送或接收电子邮件，你只需要知道收件人的电子邮件地址。你的电子邮件账户由你选择的密码保护。你可以通过各种方式创建电子邮件账户。如果你有一个互联网服务提供商的账户，你可能已经拥有一个 POP（邮局协议）账户。你甚至不需要花一分钱就能从 Hotmail 和 Yahoo 等免费电子邮件服务提供商那里获得一个基于 Web 的电子邮件账户。基于 Web 的电子邮件通常建立在所谓的 IMAP 之上。你可以拥有任意多的电子邮件地址，只要你的记忆力足够，也就是说，如果你能记住所有这些地址和密码组合。

When you send an e-mail message, it travels upon SMTP, Simple Mail Transfer Protocol. It's a language your computer speaks when talking to another machine to send e-mail messages. You need a basic understanding of what SMTP is and how it works in order to create advanced e-mail applications in any computer language.

当你发送一封电子邮件时，它通过 SMTP（简单邮件传输协议）传输。这是你的计算机在与另一台机器通信以发送电子邮件时所使用的语言。你需要了解 SMTP 是什么以及它如何工作，才能在任何计算机语言中创建高级电子邮件应用程序。

When receiving e-mail, your e-mail clients speak POP or Internet Message Access Protocol (IMAP), depending on the server you get your e-mail from.

接收电子邮件时，你的电子邮件客户端使用 POP 或 Internet Message Access Protocol（IMAP），具体取决于你从哪个服务器获取电子邮件。

First, let's take a look at how your e-mail message find its way to your friend, tens of thousands of miles away.

首先，让我们看看你的电子邮件是如何传送到成千上万英里外的朋友那里的。

### Not-So-Secret Agents

### 不那么秘密的代理

The Internet e-mail system is basically the combination of a client-to-server and server-to-server system with a bunch of agents toiling behind the scene. You compose an e-mail message in a client program such as Microsoft Outlook or Pine. The hardworking mailman delivers it to the designated post office, that is, the outgoing mail server of your choice. The server may have to talk to another mail server, if the recipient is unreachable within the network it is responsible for. Upon getting the e-mail message, the mail server at the receiving end asks another server-side program to put it into the recipient's mailbox. It is the recipient's e-mail client that actually fetches the e-mail message from his mailbox on his incoming mail server.

互联网电子邮件系统基本上是客户端到服务器和服务器到服务器系统的结合，后面有一大群代理在默默工作。你在 Microsoft Outlook 或 Pine 等客户端程序中撰写一封电子邮件。勤劳的邮递员将其送到指定的邮局，也就是你选择的发送邮件服务器。如果收件人在服务器负责的网络范围内无法联系到，该服务器可能需要与另一台邮件服务器通信。收到电子邮件后，接收端的邮件服务器会请求另一台服务器端程序将其放入收件人的邮箱。实际从收件人接收邮件服务器上的邮箱中获取电子邮件的是收件人的电子邮件客户端。

Your e-mail client program is called a Mail User Agent (MUA) and the mail server is called a Mail Transfer Agent (MTA). An MUA not only delivers e-mail messages but also receives them. As we already mentioned, it is not the MTA that actually puts e-mail messages into the recipient's mailbox. Another small program, called a Mail Delivery Agent (MDA), is the grunt of the e-mail system that does the job.

你的电子邮件客户端程序称为邮件用户代理（MUA），邮件服务器称为邮件传输代理（MTA）。MUA 不仅发送电子邮件，还接收电子邮件。如我们之前提到的，并不是 MTA 实际将电子邮件放入收件人邮箱的。另一个名为邮件投递代理（MDA）的小程序，才是电子邮件系统中干活的家伙，它负责这项工作。

You may have heard another acronym, **MRA**, short for Mail Retrieval Agent. It's not a standard term, but widely used for referring to a program or service that fetches e-mail from a mailbox on a remote server and passes it to an MUA using one of the two protocols: POP or IMAP. We'll be looking at details of these protocols in the next chapter.

你可能还听过另一个缩写，**MRA**，即邮件检索代理。它不是标准术语，但广泛用于指代从远程服务器邮箱中获取电子邮件，并通过 POP 或 IMAP 两种协议之一将其传递给 MUA 的程序或服务。我们将在下一章详细介绍这些协议。

As you can see, different software agents are involved in handling e-mail. As with us human beings, they need to speak a common language to get the job done: a protocol.

由此可见，处理电子邮件涉及多种不同的软件代理。就像我们人类一样，它们需要说一种共同的语言才能完成工作：一种协议。

### SMTP

### SMTP

When an MUA delivers an e-mail message to an MTA, they speak the same language called Simple Mail Transfer Protocol (SMTP). As its name implies, SMTP is very easy to understand. Let's see SMTP in action. If you telnet to port 25 of your outgoing mail server, you can talk to your MTA directly. Unless configured otherwise, MTAs are expected to listen on port 25. Words in bold typeface are the SMTP commands that a client, you in this case, types in:

当 MUA 将电子邮件发送到 MTA 时，它们使用一种名为简单邮件传输协议（SMTP）的通用语言。顾名思义，SMTP 非常容易理解。让我们看看 SMTP 的实际运作。如果你 telnet 到发送邮件服务器的 25 端口，就可以直接与你的 MTA 对话。除非另有配置，MTA 应监听 25 端口。粗体字表示客户端（即你）输入的 SMTP 命令：

```
# telnet somewhere.com 25
Trying 192.168.0.1...
Connected to somewhere.com
Escape character is '^]'.
220 somewhere.com ESMTP Sendmail 8.9.3/8.9.3; Sun, 28 Jan 2001 22:30:55 +0900
**HELO** whatever.com
250 whatever.com Hello IDENT:wankyu@whatever.com [192.168.0.2], Pleased to meet you
**MAIL FROM**: wankyu@whatever.com
250 wankyu@whatever.com... Sender ok
**RCPT TO**: yonsuk@whoelse.com
250 yonsuk@whoelse.com... Recipient ok
**DATA**
354 Enter mail, end with "." on a line by itself
Subject: Just a Note

Don't forget to bring your notebook tomorrow.
Have a nice read.
.
250 WAA29446 Message accepted for delivery
**QUIT**
221 whatever.com closing connection
Connection closed by foreign host.
#
```

SMTP is a line-oriented protocol. Both the client and the server transmit commands and responses in the form of character strings terminated by a carriage return/line feed (CR/LF) pair. Line-oriented protocols are easy to learn and understand. Parsing a server response, for example, is just a matter of throwing in a regular expression.

SMTP 是一种面向行的协议。客户端和服务器都以以回车/换行（CR/LF）对结束的字符串形式传输命令和响应。面向行的协议易于学习和理解。例如，解析服务器响应只是使用正则表达式的问题。

