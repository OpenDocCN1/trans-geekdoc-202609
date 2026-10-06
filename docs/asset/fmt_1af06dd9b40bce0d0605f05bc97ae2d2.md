
| 命令 | 说明 |
|---|---|
| `cd -` | 返回上级目录 |
| `ls` | 列出文件 |
| `ls -h` | 显示文件大小 |
| `cp` | 复制文件 |
| `cp -r` | 复制包含所有文件的文件夹 |
| `mv` | 移动文件 |
| `mkdir` | 创建目录 |
| `rm` | 删除文件 |

按下 `Ctrl+D` 会话将终止。

> **注意** 当你第一次连接服务器时，可能会提示接受服务器密钥或证书。可能会出现类似“服务器密钥未在注册表中”的字样。这是正常的。当你点击 Yes 时，你正在主机之间建立信任。

![](img/e8e965b6c3537819be0d570febb3fc1d_31.png)

图 1.11: PuTTY 安全警告

我真心希望为你提供了一个可以建立的基础，并且你将这些工具添加到了你的工具箱中。这些工具有些对你来说只是复习，而有些是全新的。这些工具不仅有助于你排除故障，还有助于你进行安全防护。

# 第 2 章 排除 Windows 故障

在本章中你将学习：

- RELI
- PSR
- PathPing
- MTR
- Sysinternals
- GodMode

2012 年，我离开了大路斯安那州前往科罗拉多州，在福特卡森的美国陆军通信电子司令（CECOM）担任了一个职位。我的工作是培训士兵进行信息安全（IA）。国防部要求任何具有特权访问权限的全职或兼职现役人员或承包商必须拥有某些计算机认证。这被称为 DoD 8570。

## RELI

我将其称为 RELI，因为当你在任务栏的 Windows 搜索框中输入这四个字母时，除了“可靠性记录/监控器”（Reliability History/Monitor）之外通常没有其他选项。RELI 的起源可以溯到 Windows Vista。它允许你在时间轴上查看机器的稳定性。当你开始在开始菜单输入时，你会发现工具的名称显示为“可靠性记录”（Reliability History）。当你打开工具时，它会重命名为“可靠性监控器”（Reliability Monitor）。（感谢微软）

可靠性监控器将为你创建一个图，显示重要事件、应用程序和 Windows 故障、更新以及可能重要的信息。图 2.1 显示了由应用程序、Windows 和杂项故障生成的图形。在实验 2.1 中你将使用 RELI。

![](img/e8e965b6c3537819be0d570febb3fc1d_33_0.png)

图 2.1：可靠性监控器图形

## 实验 2.1: RELI

1. 要打开此工具，打开开始菜单并开始输入 `reli`。
2. 当你在开始菜单的“可靠性记录”旁边看到蓝色旗帜图标时，按回车键。等待它生成你的图形时间轴。
3. 注意左上角图表上方，你可以将时间轴视图从“天”（Days）切换到“周”（Weeks）。
   - 图表右侧指示的前三行是该系统经历的应用程序和杂项故障。这些可能包括程序停止运行或 Windows 未正常关闭的情况。这是蓝屏/黑屏（BSOD）的极佳指示器。它将显示为带有白色 X 的红色圆圈。
   - 在故障下方，带有感叹号的黄色三角形表示警告。这些三角形被称为“喷点”（splats）。它们可能表示软件未正确更新，或者发生了错误但没有完全失败。
   - 底部的蓝色圆圈是信息性的。它们将告诉你软件更新是否成功或驱动程序是否正确安装。
4. 在可靠性监控器的左下角，点击“保存可靠性记录”链接以将此时间轴保存为 XML 文件。此文件可以被其他报告应用程序导出和分析。
5. 点击右下角“保存可靠性记录”链接旁边的“查看所有问题报告”链接。这将打开一个新页面，包含此设备经历的所有问题，并可以直接报告给微软。当有解决方案时，它将出现在“安全维护”（Security Maintenance）中。

## 使用 RELI

假设你是一个系统管理员。大多数系统管理员为其组织安装、升级和监控软件及硬件。你的数据中心有一台可能运行异常的服务器。你尝试排除故障，但无法复制报告给你的问题。相反，你遇到了臭名昭著的蓝屏（BSOD）。

你会发现当客户报告问题时，你问的第一句话是：“你试过关掉再重启吗？”如果你不幸遇到了 BSOD，你唯一的选择就是关机并重启设备。检查可靠性以确定导致崩溃的原因。

根据我的经验，BSOD 是由坏的驱动程序、过热或有人安装了与硬件或操作系统不兼容的新软件引起的。使用可靠性就是你弄清到底发生了什么的方法。

没有人承认下载并玩过《毁灭战士：永恒》（Duke Nukem Forever）。

## PSR

你是组织中负责持续或文档记录的人吗？你必须培训他人如何工作，或者你被要求培训某人做你的工作？你是否经常需要对系统的环境问题进行故障排除，或者在最后一分钟进行演示？

问题步骤记录器（Problem Steps Recorder，简称 PSR）允许你记录故障排除问题的步骤。它记录你的操作步骤。

## PathPing

以及目标地。当涉及公共设备时，你不能完全依赖 ICMP。它们是公共设备。在互联网上，你偶尔会遇到这样的情况：对一个节点的 ICMP ping 失败率为 50%，而下一跳的成功率则是 100%。

图 2.3 往 Google 公共 DNS 服务器 8.8.8.8 的路由追踪。从我的桌面到服务器需要经过 11 次跳跃。然后，PathPing 将计算往返时间 (RTT) 的统计数据，即在两个 IP 地址之间丢弃的数据包的百分比。当你看到丢包率时，可能表明这些路由器负载过载。

```
Microsoft Windows (Version 10.0.19043)
(c) 2017 Microsoft Corporation. All rights reserved.
C:\Users\admin>ping 8.8.8.8
Tracing route to google-public-dns-a.com [8.8.8.8]
over a maximum of 30 hops:
1    1ms    1ms    1ms    0%    router-0 [192.168.1.1]
2    2ms    2ms    2ms    0%    router-1.louisville.co.denver.com.net
3    3ms    3ms    3ms    0%    router-2.louisville.co.denver.com.net
4    4ms    4ms    4ms    0%    ae-301-run1.louisville.co.denver.com.net
5    5ms    5ms    5ms    0%    ae-301-run2.louisville.co.denver.com.net
6    6ms    6ms    6ms    0%    be-36652-cr02.160misle.hl.ibone.com
7    7ms    7ms    7ms    0%    be-36653-cr01.160misle.hl.ibone.com
8    8ms    8ms    8ms    0%    ae-8339-pop2.ashurn.va.ibone.com
9    9ms    9ms    9ms    0%    google-public-dns-a.com [8.8.8.8]
10   10ms   10ms   10ms   0%    google-public-dns-a.com [8.8.8.8]

Computing statistics for 27 seconds...
Source to: This Node/Link               Address
RTT  Sent/Lost  Pct  Last/Sent  Pct  DESKTOP-AUB7VK.HomeRT
1    1ms     0/0    0%    1ms        0/0    0%    router-0 [192.168.1.1]
2    2ms     0/0    0%    2ms        0/0    0%    cm-1-arc.louisville.co.denver.com.net [162.151.15.41]
3    3ms     0/0    0%    3ms        0/0    0%    ae-103-run1.louisville.co.denver.com.net
4    4ms     0/0    0%    4ms        0/0    0%    ae-2-run2.louisville.co.denver.com.net [162.151.15.41]
5    5ms     0/0    0%    5ms        0/0    0%    ae-15-run1.denver.co.denver.com.net
6    6ms     0/0    0%    6ms        0/0    0%    be-36052-cr02.160misle.hl.ibone.com [60.86.02.121]
7    7ms     0/0    0%    7ms        0/0    0%    be-9216-pep9.01fifteenth.co.ibone.com, [60.86.03.94]
8    8ms     0/0    0%    8ms        0/0    0%    ae-1298-pop1.ashurn.va.ibone.com [75.149.228.174]
9    9ms     0/0    0%    9ms        0/0    0%    108.170.254.81
10   10ms    0/0    100%   10ms       0/0    100%   64.233.179.43
11   11ms    0/0    0%    11ms       0/0    0%    google-public-dns-a.com [8.8.8.8]
```

**图 2.3:** 结合了路由追踪和跳跃统计的 PathPing

在处理网络延迟时，PathPing 是一个比单纯关注延迟更好的诊断工具。对 PathPing 数据的解读可以给出更稳健的假设。如果你在第 6 跳跃的数据中看到异常或峰值和谷值，并不一定意味着第 6 跳跃有问题。可能是第 6 跳跃恰好面临巨大的压力，或者处理器具有除你的 PathPing 之外的优先级。

## Sysinternals 工具套件

### Process Explorer

| 进程 | CPU | 线程 | 工作集 | PID | 描述 | 公司名称 |
|---|---|---|---|---|---|---|
| Explorer | | 1.64 K | 13.6 K | 144 | | |
| System Process | 95.94 | | 5.700 | 4 | | |
| System | | 200 K | 1.140 | n/a | 硬件中断和 DPC | |
| Interrupts | 0.96 | 504 | 132 | 668 | | |
| Memory Compression | | 160 | 13.820 K | 1064 | | |
| winrss.exe | 0.01 | 536 | 6.438 K | 798 | | |
| services.exe | | 6.18 | 8.112 K | 712 | | |
| svchost.exe | 0.00 | 334 | 32.76 K | 906 | Windows 进程主机 | 微软公司 |
| WinExplorer.exe | 0.08 | 16 | 30.036 K | 624 | | |
| WinPrvSE.exe | 1.56 | 15.488 | 10.265 K | 3932 | Windows 外壳扩展 | 微软公司 |
| RuntimeBroker.exe | 5.96 | 15.488 | 25.188 K | 4994 | 运行时代理 | |
| Svchost.exe | 10.76 | 21 | 27.172 K | 4568 | Windows 服务主机 | 微软公司 |
| Spoolsv.exe | 0.00 | 192 | 25.112 K | 2500 | 打印后台程序 | 微软公司 |
| TypeHelper.exe | 6.96 | 11 | 31.256 K | 10728 | 任务代理 | |
| TaskHost.exe | 8.12 | 5 | 5.164 | 19312 | Office 任务主机 | |
| RemoteService.exe | 2.56 | 154 | 14.388 K | 11972 | 远程服务 | |
| Csrss.exe | 0.00 | 30 | 29.716 K | 4627 | Windows 用户进程 | |
| WMIPrvSE.exe | 0.31 | 1 | 20.964 K | 1180 | WMI 提供程序主机 | 微软公司 |
| CCcheck.exe | 0.74 | 6 | 34.789 K | 9876 | | |
| GoogleUpdate.exe | 0.00 | 12 | 11.881 K | 15000 | Google 更新服务 | 微软公司 |
| Search.exe | 4.92 | 5 | 15.440 K | 13376 | 后台任务主机 | |
| BackgroundHost.exe | 0.00 | 8 | 12.518 K | 7544 | Windows 应用程序框架主机 | |
| SupportAppWs.exe | < 0.01 | | 28.361 K | 16352 | SupportAppWs.exe | 微软公司 |

CPU 使用率: 4.06% 提交更改: 41.03% 进程: 220 物理使用率: 31.05%

图 2.7: Sysinternals Process Explorer

### 其他核心工具

- **Autoruns**：这是你 IT 生活的噩梦。它可能非常隐蔽并入侵启动文件夹。这是你尝试清理的最困难的事情之一。Autoruns 可以通过查看所有列出自动启动应用程序的可能位置来提供帮助。这样你就会发现需要启动的良好项目并没有列在其中，你可以专注于处理那些入侵系统的项目。
- **Zoom**：此工具用于放大屏幕区域。在进行演示时，你可以将某些功能与缩放、绘图集成，并在通话期间配置你需要的内容。
- **PsLoggedOn**：此工具显示登录到系统的用户。PsLoggedOn 使用注册表 `HKEY_USERS` 键来查看加载了哪些配置文件。当你需要知道在 PC 上建立了会话时，这可能非常有用。
- **SDelete**：这是一个你不应该经常使用但在关键时刻派上用场的工具。如果你需要永久删除某些内容，使得即使是最好的恢复工具也无法检索数据，SDelete 将擦除所在的扇区。
- **PsExec**：如果你需要在远程系统上执行程序，PsExec 将非常有用。

# 第 3 章 Nmap—网络映射器
