
## net users

**net users** 命令列出用户。你可以在图 6-4 中看到它。

![](img/fa54c6d61c14db5421f8f63e6d594bb5_162_0.png)

图 6-4 **net users** 命令。

## net view

**net view** 命令是我个人最喜欢的之一。它显示此计算机可以通信的网络项目。如果您已获得一台机器的访问权限，此命令在枚举网络时非常宝贵。您可以在图 6-5 中看到 **net view**。

![](img/fa54c6d61c14db5421f8f63e6d594bb5_162_1.png)

图 6-5 **net view** 命令。

## net share

**net share** 是另一个不错的枚举工具。它会显示此计算机可以访问的所有网络共享。您可以在图 6-6 中看到这一点。

注意共享的打印机 Workforce845。这可能为你对该网络的渗透测试提供下一步。

![](img/fa54c6d61c14db5421f8f63e6d594bb5_163_0.png)

图 6-6 net share 命令。

## net service

net 命令可用于启动或停止服务。例如：

```
net start service
net stop service
```

常见服务包括：
- browser
- alerter
- messenger
- "routing and remote access"
- schedule
- spooler

## netshell

netshell，或 netsh，提供许多有趣的命令。在阅读这些内容时，请思考如何将它们与第 5 章中介绍的脚本病毒结合起来。我想你会看到一些有趣的可能性。

让我们首先以 netsh 作为在防火墙上打开端口的方式来检查它：

```
netsh firewall set portopening tcp 445 smb enable
```

它会起作用，但你会收到通知称 netsh firewall 已被弃用。用新的命令（netsh advfirewall firewall）和不同的端口重复实验。你可以在图 6-7 中看到这一点。

![](img/fa54c6d61c14db5421f8f63e6d594bb5_164_0.png)

图 6-7 netsh advfirewall firewall。

还有其他几个选项，例如：
- netsh wlan show networks
- netsh interface ip show config

你甚至可以尝试连接到该网络上的另一台计算机，这与之前检查过的 net view 命令配合得很好：

```
netsh set machine remotecomputer
```

这并不总是成功，但非常值得尝试。

## Windows Password Cracking

密码破解是破解 Windows 的最基本方面之一。渗透测试人员尝试破解 Windows 密码非常重要。如果你可以破解它们，攻击者也可以。我们将在本节中检查几种工具。其中一些我们在第 3 章密码学中检查过，但在这里再次给出，以便将它们置于 Windows 密码破解的背景中。

### Offline NT Registry Editor

此工具只是清除目标机器的密码。它通常非常快且非常有效。它也是 https://www.lifewire.com/offline-nt-password-and-registry-editor-review-2626147 的免费下载。然而，从攻击者的角度来看，很明显本地密码已被清空。

### LCP

LCP 是一款老旧但有效的 Windows 密码破解器。你可以从 http://www.tucows.com/preview/391886/LCP 下载它。此工具允许你从各种位置导入哈希，包括同一网络上的另一台机器（Import > Import From Remote Computer），如图 6-8 所示。

![](img/fa54c6d61c14db5421f8f63e6d594bb5_165_0.png)

图 6-8 LCP。

### pwdump

pwdump 是攻击者常用的工具，因此对安全专业人员来说也是一个好东西。许多密码破解工具的第一步是从 Windows 安全账户管理器（SAM）文件中获取本地密码哈希的副本，Windows 在其中存储密码的哈希。程序 pwdump 将从 SAM 文件中提取密码哈希。它是 http://www.openwall.com/passwords/windows-pwdump 的免费下载。

图 6-9 是 pwdump7 输出的图像。由于这是在一台实时机器上运行的，因此实际哈希已被涂黑。

![](img/fa54c6d61c14db5421f8f63e6d594bb5_165_1.png)

图 6-9 pwdump。

通常，你希望将哈希转储到外部文件，以便将其导入彩虹表工具。彩虹表在第 3 章中有详细解释，但现在只需记住它们是用于猜测密码的预计算哈希表。这可以通过简单地将 pwdump 的输出通过管道传输到测试文件来轻松完成。例如：

```
pwdump > passwordhashes.txt
```

一旦你拥有了密码哈希，你就可以使用任何彩虹表工具来检查密码是否可以恢复。这是验证组织密码强度的一种方法。

### ophcrack

ophcrack 是最广泛使用的密码破解工具之一。ophcrack 很重要，因为它可以安装在可启动 CD 上。如果以这种方式使用，你将系统启动到 CD，从而绕过 Windows 安全，然后尝试破解密码。ophcrack 提供一个免费的小型彩虹表；必须购买更大的彩虹表。你可以从 http://ophcrack.sourceforge.net/ 下载 ophcrack。它也不需要单独的过程来转储 Windows SAM 文件。相反，它会为你从 SAM 文件中获取数据。图 6-10 显示了 ophcrack 的输出。实际哈希和密码已被涂黑。

![](img/fa54c6d61c14db5421f8f63e6d594bb5_166_0.png)

图 6-10 ophcrack。

无论你使用哪种特定的密码破解工具，此类工具对于验证密码的安全性都非常重要。从本质上讲，你尝试破解密码，如果成功，则表明你的密码不够强。

### John the Ripper

John the Ripper 可能是最古老且最广为人知的密码破解工具。它也不再仅限于 Windows。也有 Linux 和 Macintosh 版本。你可以从 http://www.openwall.com/john/ 下载 John the Ripper。

John the Ripper 是一个命令行工具。但是，有完整的教程位于 http://openwall.info/wiki/john/tutorials。

## Detecting Malware in Windows

请记住，渗透测试人员的目标与攻击者不同。你的目标是提高安全性。并且经常会将渗透测试与审计/事件响应/漏洞扫描结合进行。因此，了解如何在 Windows 计算机上检测恶意软件的基本知识非常重要。并非总是可以通过防病毒软件检测到恶意软件。例如，零日利用很难检测，因为还没有签名。零日利用最好用以下引文描述：

> > Zero-day 指的是“好人”知道软件中存在安全问题的时间长短。有两种类型的零日。零日漏洞是软件安全性的一个漏洞，可能存在于浏览器或应用程序中。另一方面，零日利用是一种数字攻击，利用零日漏洞在设备上安装恶意软件。
> >
> > —Avast, https://www.avast.com/c-zero-day

那么，当你进行渗透测试或安全审计时，如何确定此类恶意软件是否存在？对于 Windows 计算机来说，至少，这比你想象的要容易得多。有工具可用于查找计算机上的异常。Windows Sysinternals 是一套由 Mark Russinovich 创建并可从 Microsoft 在 https://docs.microsoft.com/en-us/sysinternals/ 获取的工具。此工具套件可以检查系统的许多方面。

Process Explorer 将显示正在运行的进程以及启动这些进程的进程，如图 6-11 所示。

![](img/fa54c6d61c14db5421f8f63e6d594bb5_168_0.png)

图 6-11 Process Explorer。

如 图 6-12 所示，Autoruns 工具将显示设置为自动运行的程序，这通常是恶意软件的标志。

![](img/fa54c6d61c14db5421f8f63e6d594bb5_168_1.png)

图 6-12 Autoruns。

Windows 本身包含 sigverif，这是一个程序，将检查系统文件的数字签名并确保其合法。你可以在图 6-13 中看到这一点。

![](img/fa54c6d61c14db5421f8f63e6d594bb5_169_0.png)

图 6-13 Sigverif。

这些工具实际上并不是渗透测试工具。它们更像是安全审计工具，有时也用于取证。但请记住本书贯穿始终的一个主题：渗透测试人员不是黑客。他或她会使用黑客技术，但最终目标是提高系统安全性。因此，在本书中，我有时会向你展示一些对安全有用但严格来说不是渗透测试的工具和技术。许多书籍声称是渗透测试书籍，但实际上只是教你黑客技术并希望你以道德方式使用技能。在本书中，我教你的是渗透测试。这意味着你对安全测试感兴趣，可能不特指“黑客”。

### Cain and Abel

这是一款老旧但可靠的工具，有助于提取大量信息。它是 http://www.oxid.it/cain.html 的免费下载。此工具具有许多有趣的功能。

最明显的功能之一是 Cain and Abel 可以读取 Windows 注册表并获取 Wi-Fi 密码。你可以在图 6-14 中看到这一点（SSID 和密码已被涂黑）。
