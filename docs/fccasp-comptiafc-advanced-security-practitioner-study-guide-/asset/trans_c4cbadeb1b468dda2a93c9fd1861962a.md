

## 实验 A19：Metasploit 框架简介

在本实验中，您将在 NETinVM 实验环境中下载并安装 Metasploit 框架，并对您的 Debian 机器执行简单的利用。您将在 NETinVM 环境中对您的 Debian 5 Apache 服务器执行扫描和轻度利用，同时学习 Metasploit 框架控制台的语法。了解 Apache 服务器如何被利用将有助于您保护服务器免受攻击。

要下载必要的软件，请访问：

`www.metasploit.com/download/`

1. 运行 VMware Player 并加载 NETinVM 环境。
2. 在 NETinVM 中点击**全部运行**。
3. 从 OpenSUSE 机器打开 Firefox 网页浏览器。
4. 访问 Metasploit 网站并下载完整的 32 位 Linux 二进制文件。
5. 从 OpenSUSE 机器打开一个终端。
6. 输入 `su`，并输入口令。
7. 导航到下载目录；输入 `cd Downloads`。
8. 输入 `chmod +x framework-4.0.0-linux-full.run`。您可能需要根据您下载的框架版本修改此命令。
9. 输入 `./framework-4.0.0-linux-full.run`。
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

1. 点击开始，输入 `hdwwiz`，然后点击下一步。
2. 从出现的列表中选择**手动安装硬件**，然后点击下一步。
3. 选择**网络适配器**并点击下一步。
4. 选择 **Microsoft** 和 **Microsoft 回环适配器**，点击两次下一步，然后选择完成。

请注意，在通过 Windows 防火墙执行需要宿主和客户机系统间通信的练习时，需要启用网络发现和文件共享。在 Windows Vista 和 7 下执行此操作的说明位于此处：

- `http://windows.microsoft.com/en-US/windows-vista/Enable-or-disable-network-discovery`
- `http://windows.microsoft.com/en-US/windows7/Enable-or-disable-network-discovery`

现在您已准备好尝试使用 Wireshark 嗅探虚拟网络流量：

1. 打开 VMware Player，加载 NETinVM，然后点击**全部运行**。
2. 从基础系统打开一个终端。
3. 输入 `su`，输入口令，并输入 `ifconfig`。观察 `eth0` 接口未分配 IP 地址。(`su` 指 SuperUser，即 Unix 管理员。)
4. 在宿主 Windows 操作系统的网络和共享下启用网络发现和文件共享。
5. 连接到 VMware Player 网络适配器。
6. 从基础系统再次执行 `ifconfig`，注意 `eth0` 现在有了 IP 地址。记下分配给 `eth0` 的 IP 地址。
7. 从 Windows 宿主打开一个终端并输入 `ipconfig /all`。记下与您的基础系统 `eth0` 接口位于同一子网内的 VMNet 接口。在我的实验中，这是 `VMnet8`，分配的 IP 地址为 `192.168.184.1`。基础系统的 `eth0` 接口被分配了 IP 地址 `192.168.184.128`。
8. 验证两者之间的连通性；从您的 Windows 宿主输入 `ping 192.168.184.128`。
9. 测试从您的 Windows 宿主到基础系统的路径。输入 `tracert 192.168.184.128`。观察您现在拥有直接连接。这就像一个虚拟交换机一样运作。
10. 从基础系统验证到 Windows 宿主的连通性；输入 `ping 192.168.184.1`。
11. 既然您已验证连通性，就可以捕获一些实时流量。在 Windows 宿主上打开 Wireshark。
12. 选择适当的 VMware 适配器（可能是列表中的最后一个），然后点击**捕获**。
13. 从您的基础系统输入 `ping 192.168.184.1` 以生成一些 ICMP 流量；然后用 `Ctrl+C` 停止 ping。
14. 通过点击主工具栏上的**停止正在运行的实时捕获**图标来停止捕获，并简要浏览结果。
15. 在数据包列表窗格中，高亮显示第一个 ICMP ping 请求。
16. 在数据包详情窗格中，展开所有内容。
17. 双击**响应帧：**。您现在正在查看对初始请求的回显应答。
18. 在数据包详情窗格的标题校验和下，选择源 IP 地址。
19. 在 NETinVM 的基础系统下启动 Wireshark。
20. 在 `tap0` 接口上捕获流量；回想这是外部网络。
21. 以 root 身份登录 exta 并尝试使用 netcat 通过端口 31337 与基础系统建立连接。输入 `nc 10.5.0.1 31337`。此连接将被拒绝。
22. 返回基础系统并停止实时捕获。
23. 观察结果。
24. 现在您将尝试一些简单的 Wireshark 显示过滤器。我还提供了 Wireshark 捕获过滤器的 URL，我们稍后将讨论。
25. - `http://wiki.wireshark.org/DisplayFilters`
    - `http://wiki.wireshark.org/CaptureFilters`
26. 在过滤器工具栏中输入 `http` 并点击**应用**。这是 Wireshark 也许是最强大功能的一个基本示例。它因过滤能力而闻名。
27. 点击**清除**。

