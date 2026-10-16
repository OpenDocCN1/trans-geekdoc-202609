
如果需要快速识别正在运行的 Windows 版本，可以使用 Nmap (`https://nmap.org/download.html`) 并加 `-O` 选项，如 [Figure 12-3](#c12.xhtml#c12-fig-0003) 所示。

![tip](images/tip.png)其他操作系统指纹识别工具可用，但我发现 Nmap 以及商业扫描器如 Nexpose 是最准确的。

3. **确定潜在的安全漏洞。**

漏洞分析可能是主观的，且因系统而异，但请寻找有趣的服务和应用，并从该点开始。

![ FIGURE 12-1:  使用 NetScanTools Pro 对 Windows 10 系统进行端口扫描。](images/9781119485476-fg1201.png)

[FIGURE 12-1:](#c12.xhtml#rc12-fig-0001)  使用 NetScanTools Pro 对 Windows 10 系统进行端口扫描。

![ FIGURE 12-2:  使用 NetScanTools SMB Scanner 收集 SMB 版本。](images/9781119485476-fg1202.png)

[FIGURE 12-2:](#c12.xhtml#rc12-fig-0002)  使用 NetScanTools SMB Scanner 收集 SMB 版本。

![ FIGURE 12-3:  使用 Nmap 确定 Windows 版本。](images/9781119485476-fg1203.png)

[FIGURE 12-3:](#c12.xhtml#rc12-fig-0003)  使用 Nmap 确定 Windows 版本。

#### 防御系统扫描

通过在网络和 Windows 主机上实施适当的安全设置，您可以防止外部攻击者或恶意内部用户收集有关 Windows 系统的特定信息。您有以下选项：

*   对运行 Internet Information Services (IIS) 的系统使用网络防火墙或 Web 应用防火墙。

*   在每个系统上使用 Windows 防火墙或其他个人防火墙软件。您可能需要专门阻止 Windows 网络端口，如 RPC（端口 135）和 NetBIOS（端口 137–139 和 445）。请注意，此操作可能会破坏 Windows 网络通信，尤其是在服务器上。

*   禁用不必要的服务，以免在建立连接时显现。

#### NetBIOS

您可以通过 NetBIOS（Network Basic Input/Output System）功能和程序来收集 Windows 信息。NetBIOS 允许应用程序进行网络调用并与局域网内的其他主机通信。

![warning](images/warning.png)如果未正确保护，以下 Windows NetBIOS 端口可能会被 compromise：

*   用于网络浏览的 UDP 端口：

    *   端口 137（NetBIOS 名称服务，也称为 WINS）

    *   端口 138（NetBIOS 数据报服务）

*   用于 Server Message Block (SMB) 的 TCP 端口：

    *   端口 139（NetBIOS 会话服务，也称为 CIFS）

    *   端口 445（在 TCP/IP 上运行 SMB，无需 NetBIOS）

#### 默认

下文两节描述的默认操作可以在未受保护的运行 NetBIOS 的系统上执行。

#### UNAUTHENTICATED ENUMERATION

在执行未经验证的枚举测试时，您可以通过以下两种方式收集本地或远程系统的配置信息：

*   使用全能扫描器，如 LanGuard 或 Nexpose。

*   使用内置于 Windows 的 nbtstat 程序。（nbtstat 代表 NetBIOS over TCP/IP Statistics。）

[Figure 12-4](#c12.xhtml#c12-fig-0004) 展示了使用简单 nbtstat 查询在 Windows 7 系统上可以收集的信息。

![ FIGURE 12-4:  使用 nbtstat 在 Windows 7 系统上收集信息。](images/9781119485476-fg1204.png)

[FIGURE 12-4:](#c12.xhtml#rc12-fig-0004)  使用 nbtstat 在 Windows 7 系统上收集信息。

nbtstat 显示远程计算机的 NetBIOS 名称表，该表通过 `nbtstat -A` 命令获取。该命令显示计算机名称、域名称以及媒体访问控制（MAC）地址。

![tip](images/tip.png)不需要像 Nexpose 这样的高级程序即可从 Windows 系统中收集这些基础信息。商业软件（如 Nexpose）提供的图形界面虽然美观且易用，但您可以使用单一工具即可获取所需信息。

#### SHARES

Windows 使用网络共享来共享系统中的特定文件夹或驱动器，以便其他用户在网络中访问。共享易于设置，且能够在不涉及服务器的情况下与网络中的其他用户共享文件。然而，共享经常配置不当，导致用户、恶意软件以及已进入网络的外部攻击者能够访问他们不应获得的信息。您可以使用 LanGuard 内置的 Share Finder 工具扫描整个 IP 地址范围，以查找 Windows 共享，如 [Figure 12-5](#c12.xhtml#c12-fig-0005) 所示。

![ FIGURE 12-5:  使用 LanGuard 扫描网络以查找 Windows 共享。](images/9781119485476-fg1205.png)

[FIGURE 12-5:](#c12.xhtml#rc12-fig-0005)  使用 LanGuard 扫描网络以查找 Windows 共享。

Everyone 组对 THINKPAD 主机上的 LifeandHealth 共享拥有完全共享和文件访问权限。我经常看到类似情况：有人共享本地驱动器以便他人访问。问题在于，此人往往忘记撤销权限，留下一个安全漏洞。

[Figure 12-5] 中显示的共享正是恶意内部人员所寻找的，因为共享名称暗示了如果攻击者连接到共享，可能访问的文件类型。发现这些共享后，攻击者通常会进一步探查，看是否能浏览并访问共享内的文件。本章后期以及 [第 16 章](#c16.xhtml) 将讨论共享和敏感信息。

#### 防御 NetBIOS 攻击

您可以实施以下安全措施，以最大程度降低 Windows 系统上 NetBIOS 和 NetBIOS over TCP/IP 的攻击风险：

*   使用网络防火墙。

*   在每个系统上使用 Windows 防火墙或其他个人防火墙软件。

*   禁用 Windows 文件和打印共享（该设置位于 Windows 控制面板）。在 Windows 8.1 和 Windows 10 中，路径为控制面板 > 网络和 Internet > 网络和共享中心 > 更改高级共享设置。

*   教育用户了解启用不当安全访问控制的文件共享的风险。这些风险在本章以及 [第 16 章](#c16.xhtml) 中也有讨论。共享无疑是当今网络中最大的风险之一。

![warning](images/warning.png)隐藏共享 —  — 在共享名称末尾添加美元符号 ($) —  — 实际上并不能隐藏共享名称。我提到的所有工具都能轻易看透这种“安全隐蔽”手段。事实上，如果您发现此类共享，应更 closely 观察，因为用户可能在隐藏某些内容，或知道共享上的信息敏感，不希望引起注意。

#### 检测 Null Sessions

一个众所周知的 Windows 漏洞允许将匿名连接（即 *null session*）映射到隐藏的 IPC$ 共享（即 *interprocess communication*）。此攻击方法可用于收集 Windows 主机配置信息，如用户标识和共享名称，或编辑远程计算机注册表的部分内容。

尽管 Windows Server 2008 及以后版本，以及 Windows 7、Windows 8 和 Windows 10 默认不允许 null-session 连接，但我常发现因禁用 Windows 防火墙而配置了此漏洞的系统。此漏洞可能对您的网络造成问题。

