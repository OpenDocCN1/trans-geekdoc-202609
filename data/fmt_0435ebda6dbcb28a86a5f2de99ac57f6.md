
*   输入 `5` 选择 Web Jacking Attack Method

![](img/bapp01g013.jpg)

9. 点击桌面左上角的 **Applications**。选择 **Internet** 并打开 **IceWeasel** Web 浏览器，以验证你在 Kali 环境中是否有 Internet 连接。

10. 浏览到你的网站或另一个你有书面授权复制的网站。

11. 返回终端窗口中的 SET，输入 `2` 选择 Site Cloner。这个强大的工具允许你制作任何网站的精确副本。如果你能通过网络钓鱼攻击诱使用户登录到你的网站，这个虚假网站就能窃取密码。要检测和防止网站被克隆很难，但有一系列可行的步骤可降低发生的可能性。网络搜索将显示一些当前可用的技术解决方案，因为这种威胁在不断演变。

12. 克隆过程需要提供你的 IP 地址。程序会为你设置一个 Web 服务器，允许用户登录到虚假网站。要查找 IP，打开命令提示符（Applications 右侧的 `>_`），输入 `ifconfig`。IP 地址在 Linux 中显示为 `inet addr:`。

13. 在浏览器中输入你的网站 URL 或你有书面授权克隆的网站 URL。

14. 按 Enter 键，等待网站克隆完成。

15. 输入 `Y` 启动 Apache Web 服务器，按 Return 键继续。

16. 返回 IceWeasel Web 浏览器，输入 `http://` 后跟 `ifconfig` 显示的 IP 地址。你将看到一个带有链接的重定向页面。

17. 点击该链接，你将被转发到之前选择的 Web 地址。它看起来像你的示例网站，但实际上是一个克隆（虚假）副本，可用于窃取凭证。你的最终用户会不会轻易被骗，在这样的网站上输入登录凭证？你该如何防止这种情况发生？

18. 如果该网站允许输入凭证登录，请输入一些虚假凭证并点击 **Log In** 按钮。

19. 要退出 Kali 并返回 Windows 环境，点击窗口右上角的 **root**，选择 **Shut Down**。

---

## 实验 A16：下载、验证和安装虚拟环境

我们正准备建立一个虚拟化网络，将在后续实验中使用。在本练习中，你将下载 Microsoft 文件校验和完整性验证器 (`FCIV`)、`VMware Player` 和 `NETinVM` 虚拟机。如有必要，还将下载 `7-Zip` 文件归档工具。

你将验证 `VMware Player` 和 `NETinVM` 的 MD5 校验和，并安装虚拟环境。本实验旨在演示文件完整性和虚拟化，同时为你提供一个可执行更高级虚拟环境实验的环境。

以下是下载必要软件的地址：

*   Microsoft FCIV：`http://support.microsoft.com/kb/841290`
*   VMware Player：`www.vmware.com/try-vmware/`
*   NETinVM：`www.netinvm.org`
*   7-Zip：`www.7-zip.org/`

1.  下载 NETinVM 2013-1-28 版本（约 3.3 GB，即使在高速连接下也可能需要五个多小时下载）以及适合你 PC 的 `VMware Player` 版本。使用 `7-Zip` 文件归档工具（或你喜欢的任何归档工具）解压 NETinVM 压缩包的内容。记下其官网引用的 MD5 校验和。

2.  使用前面列出的 Microsoft 知识库 (KB) 文章中的说明下载并安装 `FCIV` 实用程序。此步骤仅适用于基于 Windows 的机器。

3.  验证 `VMware Player` 和 `NETinVM` 的校验和完整性。首先，打开 Windows 命令行外壳并运行 `FCIV` 工具，使用以下语法：

    ```
    fciv.exe filename
    ```

    你必须在 `FCIV` 工具所在的目录中发出此命令，或者将该工具添加到系统路径中，如果你希望从任何目录发出 `FCIV` 命令。

4.  确保文件校验和与其官网上针对你特定下载文件引用的校验和匹配。如果匹配，你就可以开始安装了。如果不匹配，请停止并重新下载这些文件，包括 `FCIV`。验证下载无误后继续。

5.  通过双击下载的文件并按照说明安装 `VMware Player`。如果遇到任何问题，请访问 VMware 常见问题解答页面。常见问题的答案、文档参考和用户论坛可在此处找到：

    `www.vmware.com/products/player/faqs.html`

6.  打开 `VMware Player` 并点击 **Open A Virtual Machine**。

## 实验 A17：探索您的虚拟网络

在本实验中，您将熟悉在上一课中安装的 NETinVM 网络环境的固有设计。本练习不需要额外的软件。

您将加载 NETinVM 虚拟环境，包括网络拓扑的用户界面、各个系统、网络接口，以及该环境中使用的 IP 寻址方案。

### 设置与初始配置

1.  启动 VMware Player 并加载 NETinVM。

    ![](img/bapp01g014.jpg)

2.  您现在看到的是基础系统的 KDE 界面，这将是您的主要工作环境。这是 `base.example.net` OpenSUSE Linux 系统。点击桌面上的 **Run All（全部运行）**，以启动 `exta`、`dmza`、`dmzb`、`fw` 和 `inta` 系统。

    ![](img/bapp01g015.jpg)

3.  在 VMware Player 中右键点击网络适配器图标（上图中红色 X 上方的图标），然后点击 **Disconnect（断开连接）**。每次启动 VMware Player 时都应执行此操作，因为您仅在从互联网下载软件包时才需要此连接。

    ![](img/bapp01g016.jpg)

4.  一切加载完成后，从任务栏选择 **Window List（窗口列表）**（根据 Linux 发行版的不同，通常称为图标栏或菜单栏），熟悉各个系统，并记下它们所在的桌面。

5.  选择 **inta – Terminal 1**，并以系统管理员身份登录此终端（用户名：`root`，口令：`You should change this passphrase`）。

6.  输入 `ifconfig`。请注意，系统正在使用 `eth0` 接口进行网络连接，并已配置 IP 地址 `10.5.2.10`。

7.  现在让我们看看网络的其余部分，从 `base.example.net` 开始。输入 `ping base.example.net`。您现在正从内部网络向内部网络中的另一台机器（IP 地址为 `10.5.0.1` 的 OpenSUSE 系统）发送 ping 命令。按 `Ctrl+C` 停止 ping 序列。

8.  现在分别 ping DMZ 中的 Web 和 FTP 服务器，即 `www.example.net` 和 `ftp.example.net`。请注意，您从内部 LAN 可以连接到 DMZ 中的这两台服务器。记下它们的 IP 地址。

9.  现在 ping `10.5.0.10`；这是外部网络中的 `exta` 系统。您已确认能够从内部 LAN 访问所有系统。

10. 在 Window list（窗口列表）旁边是您的虚拟桌面。选择 **Desktop 1（桌面 1）**。这将带您回到 OpenSUSE `base.example.net` 系统。

11. 通过点击任务栏中的终端图标打开 KDE Konsole 终端。

12. 输入 `su` 并按回车键登录此系统，然后输入您在 Debian 机器上使用的相同口令。

13. 输入 `ifconfig`，记下 `eth0`、`tap0`、`tap1` 和 `tap2` 接口。

    ![](img/bapp01g017.jpg)

14. 输入两次 `exit`。

15. 从任务栏选择 Window list（窗口列表），然后选择 **exta Terminal 1**。

16. 使用用户 `root` 登录，并在提示时输入 root 口令。

17. 输入 `man nmap`。使用空格键翻页，按 `Q` 退出。请注意，您的外部机器上已经安装了功能齐全的 Nmap 端口扫描器。

18. 通过输入 `nmap -sS base.example.net` 执行基本的 TCP SYN 扫描。请注意，Nmap 足够智能，能够注意到所有三个 tap 接口，并默认使用 `tap0` 进行扫描，因为它位于同一子网中。

    ![](img/bapp01g018.jpg)

19. 返回 `exta` 系统，输入 `nmap -sL 10.5.0.0/24 | less`，密切关注结果。按空格键向下滚动。

20. 在您的 DMZ 上执行之前的列表扫描：`nmap -sL 10.5.1.0/24`，以及在您的内部 LAN 上执行：`nmap -sL 10.5.2.0/24`。

## 实验 A18：端口扫描

在本实验中，您将使用 Nmap 安全扫描器深入探究端口扫描。本实验演示了使用 Nmap 等工具，您可以确定关于网络的大量信息中的一小部分。

本实验不需要额外的软件，因为 Nmap 已安装在您的基础 OpenSUSE 系统以及各个 Debian 系统上。

### 步骤

1.  打开 VMware Player，加载 NETinVM，并 **Run All（全部运行）** 虚拟机。

2.  连接 VMware 网络适配器。这将为您提供临时的互联网访问权限。

3.  从基础系统打开 Firefox 网页浏览器；图标位于桌面上。

4.  在地址栏中输入以下 URL：

    ```
    nmap.org/data/nmap.usage.txt
    ```

5.  选择 **File ⇨ Save Page As（文件 ⇨ 另存为）**，并确保您将其保存为文本文件。

6.  将文件命名为 `nmapUse.txt` 并保存到桌面。

    ![](img/bapp01g019.jpg)

7.  您现在在桌面上拥有一个参考指南，位于您的 `password.txt` 文件旁边。打开 `nmapUse.txt`。

8.  断开 VMware Player 网络适配器的连接。

9.  从您的基础机器打开一个 `dmza` 终端；图标在任务栏中。使用您在早期实验中使用的相同凭据登录。

10. 从您的基础机器对外部网络执行列表扫描。输入 `nmap -sL 10.5.0.0/24`。您将看到 `10.5.0.1`、`10.5.0.10-15` 和 `10.5.0.254`。

    ![](img/bapp01g020.jpg)

11. 您可以执行相同的列表扫描，但排除您不想列出的机器。通过输入 `nmap -sL 10.5.0.0/24 --exclude 10.5.0.1` 排除基础机器。

12. 您也可以仅列出您希望的机器。为此，输入 `nmap -sL 10.5.0.10-15`。

13. Nmap 配备了强大的脚本功能，使用各种 Lua 脚本。让我们看看在主机上运行默认脚本扫描会发生什么。输入 `nmap -sC 10.5.0.10` 并观察输出。您可能会感到惊讶。

14. 现在让我们运行另一个扫描，它将提供相同的 SSH 信息，外加一些操作系统指纹识别。输入 `nmap -A -T4 exta.example.net`。

15. 选择 Window list（窗口列表）并登录 **exta Terminal 1**。

16. 您知道这是一台 Debian 机器，但让我们看看 Nmap 确定版本信息的准确性如何。从 shell 中输入 `cat /etc/debian_version`。正如您所见，Nmap 正确识别出了 Debian 6.0.5。

17. 让我们也看看哪些端口正在监听。输入 `netstat -l` 并查看结果。正如您所见，SSH 绝对正在运行。

18. 现在让我们看看那台 FTP 服务器。尝试 `nmap -sS --traceroute ftp.example.net` 并观察结果。您将看到这确实是一台 FTP 服务器，ftp-data 端口 20 已关闭，而 FTP 端口 21 已打开。另请注意，正如您附加的 traceroute 所确定的那样，您必须通过防火墙才能访问此服务器。

19. 现在看看这台 Debian 机器在被扫描时发生了什么。您将使用 `tcpdump` 应用程序来实现这一点。输入 `tcpdump -nnvvS -c15`。它将默认使用 `eth0` 接口，因为它是该特定系统上唯一的非回环接口。

## 实验 A19：Metasploit 框架简介

在本实验中，您将在 NETinVM 实验环境中下载并安装 Metasploit 框架，并对您的 Debian 机器执行简单的利用。您将在 NETinVM 环境中对您的 Debian 5 Apache 服务器执行扫描和轻度利用，同时学习 Metasploit 框架控制台的语法。了解 Apache 服务器如何被利用将有助于您保护服务器免受攻击。

要下载必要的软件，请访问：

`www.metasploit.com/download/`

1.  运行 VMware Player 并加载 NETinVM 环境。

2.  在 NETinVM 中点击**全部运行**。

3.  从 OpenSUSE 机器打开 Firefox 网页浏览器。

4.  访问 Metasploit 网站并下载完整的 32 位 Linux 二进制文件。

5.  从 OpenSUSE 机器打开一个终端。

6.  输入 `su`，并输入口令。

7.  导航到下载目录；输入 `cd Downloads`。

8.  输入 `chmod +x framework-4.0.0-linux-full.run`。您可能需要根据您下载的框架版本修改此命令。

9.  输入 `./framework-4.0.0-linux-full.run`。

10. 您将看到 Metasploit 安装程序；除自动更新外，请使用默认设置。

11. 输入 `msfupdate` 以手动更新 Metasploit。

12. 从 OpenSUSE root shell 输入 `msfconsole` 以进入 Metasploit 框架控制台。

13. 请注意，您拥有一个功能齐全的控制台会话。输入 `ifconfig` 以查看系统网络接口。

14. 输入 `ping -c 2 10.5.0.10` 向 exta Debian 5 机器发送两个数据包进行 ping 测试。

15. 在 MSF 控制台中输入 `help`。

16. 在 Metasploit 框架控制台中，输入 `db_database postgresql`。

17. 输入 `db_nmap 10.5.1.10` 从 Metasploit 框架控制台内扫描 Debian 5 Apache Web 服务器。请注意 Nmap 现已集成到 Metasploit 中。

18. 观察结果；注意 Apache Web 服务器确实在端口 80 上监听。

19. 输入以下内容：

    ```
    use auxiliary/scanner/http/mod_negotiation_scanner
    ```

20. 输入 `set rhosts 10.5.1.0/24`。

21. 输入 `run`。

现在您已经找到一个启用了 `mod_negotiation` 的 Web 服务器，尝试通过暴力攻击利用该功能。输入以下内容：

```
use auxiliary/scanner/http/mod_negotiation_brute
```

22. 输入 `set rhosts 10.5.1.10/32`。

23. 输入 `run`。

这个简单而有效的方法允许您查看启用了 `mod_negotiation` 的 Apache Web 服务器上位于的所有文件。在本场景中只有 `index.html` 文件；然而，在真实场景中，此信息可能导致进一步的利用和潜在敏感数据的渗出。此类工具用于指纹识别服务器并利用已知漏洞。

Metasploit 框架有许多资源，包括 Metasploit Unleashed 网站。`Metasploit.com` 网站和 `exploit-db.com` 网站都提供信息和额外漏洞利用代码的下载，可协助定制您的渗透测试：

- `www.metasploit.com/modules/`
- `www.exploit-db.com/`
- `www.offensive-security.com/metasploit-unleashed/Metasploit_Unleashed_Information_Security_Training`
- `www.amazon.com/Metasploit-The-Penetration-Testers-Guide/dp/159327288X`

## 实验 A20：使用 Wireshark 嗅探 NETinVM 流量

您早在实验 A2 中就在宿主系统上安装了 Wireshark。要从虚拟网络捕获流量，您需要在宿主机器上安装 Microsoft 回环适配器。

在 Windows Vista 和 7 中，此功能可在控制面板中启用。请执行以下步骤，使用“添加硬件向导”在 Windows 7 或 Vista 中启用回环网络适配器：

1.  点击开始，输入 `hdwwiz`，然后点击下一步。

2.  从出现的列表中选择**手动安装硬件**，然后点击下一步。

3.  选择**网络适配器**并点击下一步。

4.  选择 **Microsoft** 和 **Microsoft 回环适配器**，点击两次下一步，然后选择完成。

请注意，在通过 Windows 防火墙执行需要宿主和客户机系统间通信的练习时，需要启用网络发现和文件共享。在 Windows Vista 和 7 下执行此操作的说明位于此处：

- `http://windows.microsoft.com/en-US/windows-vista/Enable-or-disable-network-discovery`
