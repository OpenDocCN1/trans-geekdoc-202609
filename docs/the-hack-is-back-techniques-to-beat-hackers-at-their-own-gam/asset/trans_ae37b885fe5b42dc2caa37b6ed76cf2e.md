
这里有趣的是，我不确定那个 DefaultAccount 是我创建的东西，还是本来就应该存在那里。通过简单的 Google 搜索，我得知 DefaultAccount 或默认系统托管账户（DSMA）是 Windows 10 版本 1607 和 Windows Server 2016 中引入的内置账户。所以，该账户应该存在于这个 Windows 操作系统版本中，但并非所有 Windows 版本都有。它会因版本而异，所以可能相当棘手，正如下一个示例所示，即使是经验丰富的管理员也可能需要研究才能找到账户列表。

在这个较旧版本的 Windows 中，有一堆默认账户本来就应该存在。根据所安装和配置的内容，你可能会在现代版本的 Windows 中看到一些类似的账户。HelpAssistant 和 Support 账户是此 Windows 版本附带的合法账户。IWAM 和 IUSR 账户是在用户安装 Internet Information Services 时创建的，因此这些账户也应该存在。在较新版本的 Windows 中，我还见过一个与 Windows Defender 相关的 WDAUtilityAccount。我创建的假账户是 HelperAssistant。注意，我试图让大小写与 HelpAssistant 账户保持相似。

![](img/181571ad74cba0e6a2f38fcd2658651e_286_0.png)

**图 9.21** 哪些账户是合法的？

管理员和来宾账户如果未被使用，攻击者也可以将其启用并使用。从 Windows Vista 开始，客户端操作系统版本（Windows NT 客户端列表包括 NT Workstation、2000 Pro、XP、Vista、8.1、10 和 11）中的 Administrator 和 Guest 账户默认被禁用。在 Windows Server 版本（NT Server、2000 Server、2003、2008、2012、2016、2019 和 2022）中，Administrator 账户处于启用状态，而 Guest 账户处于禁用状态。谈到 Windows Server，在域控制器上可能有几十、几百甚至几千个账户，这使得跟踪用户账户变得更加复杂，也更难发现未授权账户。一个有助于发现未授权账户的建议是查看系统上具有管理权限的账户。当我在 Windows 服务器上执行此操作时，只找到了两个账户。标准账户以及备份操作员等组的成员账户仍然可能对系统造成损害，但在大多数情况下，攻击者执行任务需要管理员权限。

我用来查看管理员账户的命令是：**net localgroup administrators**

![](img/181571ad74cba0e6a2f38fcd2658651e_286_1.png)

**图 9.22** 我可以和管理员谈谈吗？

我们查看了连接和进程，以确定是否有攻击者可能连接到你的系统。然后，我们检查了系统上的用户账户，以查找任何未授权用户。接下来，我们还将确保“前门”没有敞开。系统上没有必要开放那些可能被攻击者利用的服务。即使你位于防火墙后面，也要记住，网络中的其他系统或你通过笔记本电脑连接的无线网络可能绕过这些过滤器。家庭和工作场所中联网设备无处不在，使得这一威胁更加严重。例如，Check Point 的一名研究人员能够演示攻击者如何利用被入侵的 Peloton 在网络中进行横向移动。

接下来，我们将检查哪些端口处于开放状态，如果认为服务不需要，就关闭相应端口。我们可以在 Windows 上使用 nmap（你可以从此处下载：https://nmap.org/download），也可以直接使用内置的 netstat。

运行以下命令，查看 Windows 系统上打开了哪些端口：

```
nmap 127.0.0.1 -p 0-65535   -> checks to see what Transmission Control Protocol (TCP) ports are open
netstat -tan | find "LISTENING" -> shows a list of open ports with the built-in netstat command
```

![](img/181571ad74cba0e6a2f38fcd2658651e_287_0.png)

**图 9.23** Windows 系统上的开放端口。

1. 使用服务器管理器卸载 IIS，如果 FTP 和 HTTP 服务器未被使用，这将一并移除它们。
2. 如果你在网络中没有使用文件和打印机共享，请将其删除。你可以在这里进行此操作：控制面板\网络和 Internet\网络和共享中心\高级共享设置。

你主要应该关注的是删除用于远程连接的安全外壳（SSH）服务器和远程桌面协议（RDP）服务器。SSH 使用 22 端口进行远程命令行管理，RDP 使用 3389 端口进行基于 GUI 的远程管理。没错，微软已经开始在其服务器版本中包含 OpenSSH 服务器，并且值得庆幸的是，已停止包含 Telnet 服务器。你可以通过“设置”应用、“应用”、“可选功能”卸载 OpenSSH 服务器。如果不需要 RDP，请右键单击“开始”按钮，转到“系统”，然后选择“远程桌面”。将其关闭，然后确认你的选择。使用 nmap 再次扫描 localhost，以验证该端口已关闭。

![](img/181571ad74cba0e6a2f38fcd2658651e_288_0.png)

**图 9.24** 关闭 RDP。

关于 Windows 设备上 Administrator 账户的安全性，还有最后一点可能不太明显。内置的 Administrator 账户无法被锁定，原因显而易见，比如避免永久失去对系统的访问能力。在 Windows 10 和 11 等客户端系统中，此账户默认处于禁用状态。但在 Server 2019 和 Server 2022 等服务器操作系统中，此账户处于活动状态且可能被利用，因为它会接受成百上千次错误登录，并且仍允许你继续尝试。在下面的示例中，我尝试了 182,899 个不同的密码，最终成功获取了管理员密码 P@ssw0rd。重命名内置 Administrator 账户肯定有助于解决该账户的这个漏洞。

![](img/181571ad74cba0e6a2f38fcd2658651e_288_1.png)

**图 9.25** Administrator 账户的缺点。

在账户方面，我们还需要检查 Linux。在我看来，两种操作系统（Windows 和 Linux）各有优缺点，从安全角度看也各有优缺点。请不要到处宣扬 Linux 比 Windows 更安全（或更稳定），因为这取决于许多因素，比如你使用的操作系统版本、使用的应用程序以及配置的安全设置。一个有漏洞的 Linux 系统并不比 Windows 系统更安全。黑客更常攻击 Windows 系统，因为 Windows 在消费市场中使用更为广泛。在互联网变得更为主流之前，Windows 在 90 年代的安全防护非常松懈（而且相当不稳定）。早期版本的 Windows 包含不安全的文件系统、默认安装和运行的不必要应用程序，并且没有防火墙。但即使 Windows 开始加强安全，Java、Adobe（以及 Office）等应用程序也为黑客提供了进入系统的便捷入口。2024 年的 Windows 比 30 多年前发布时更加安全稳定。许多人都知道的常见 Linux 权限提升攻击（如 Shellshock 等）也证明 Linux 对安全问题并非免疫。

在 Linux 中，我们可以通过查看 /etc/shadow 文件来检查账户。特别是，我们要查找 UID 可能为 0 的账户。Linux 中可能有许多没有登录名或密码的账户，因此我们可以使用 grep 查找 $ 符号来筛选出有密码的账户。Linux 密码哈希中包含美元符号（$），因为它们是（$）加盐的。加盐是哈希过程中的一个额外步骤，可以防止攻击者使用彩虹表。彩虹表是大量哈希及其对应密码的集合。彩虹表对 Windows NTLM 和 LAN Manager 哈希有效，但对 Linux、Cisco（或 Mac）设备上的密码哈希无效。用通俗的话说，**如果两个用户拥有完全相同的密码，他们在 Linux 中的密码哈希会不同，但在 Windows 中的密码哈希则相同。** 在 Linux 中，我们可以使用 grep 查找 x:0 来寻找 UID 为 0（root 级权限）的账户。

运行以下命令来查找有密码的账户和 UID 为 0 的账户：

```
cat /etc/shadow | grep -F "$"          -> finds accounts with Passwords
cat /etc/passwd| grep x:0              -> finds accounts with a UID of 0
```

![](img/181571ad74cba0e6a2f38fcd2658651e_289_0.png)

**图 9.26** 有密码和根级访问权限（UID=0）的用户账户。

您还可以而且应该通过键入命令 cat /etc/group 并查看 sudo 组中的账户来检查 sudo 组。在大多数较新版本的 Linux 中，root 账户甚至可能被禁用，第一个用户账户在运行 sudo 命令时将拥有 root 级权限。这与微软在其客户端版本操作系统上的做法大体相同：禁用内置管理员，并在用户点击用户账户控制的允许按钮时，将管理权限授予第一个创建的账户（这始于 Windows Vista）。Windows 试图避免最终用户使用 Administrator 账户（在客户端上），而 Linux 试图避免最终用户使用 root 账户。为什么？因为这些管理权限可能允许你通过安装恶意软件来损害自己的系统。
