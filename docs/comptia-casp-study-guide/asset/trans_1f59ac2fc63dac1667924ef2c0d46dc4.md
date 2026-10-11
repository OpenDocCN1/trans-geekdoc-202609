
这些类型的工具通过将主机系统的网卡置于`promiscuous mode`（混杂模式）来工作。处于混杂模式的网卡可以接收其能看到的所有数据，而不仅仅是发往它的数据包。它们在开放系统互连（OSI）模型的数据链路层运行，但显示从不同网络介质捕获的数据包详细信息，将 OSI 模型分解为数据链路层、网络层、传输层和应用层。嗅探器可以捕获“线上”的所有内容并将其记录下来以供后续审查。它们允许用户查看数据包中包含的所有数据，甚至包括一些人可能想要保密的信息。许多旧协议（如 FTP 和 Telnet）以明文形式发送用户名和密码。任何拥有嗅探器的人都可以拦截这些数据并轻松重用。

如果嗅探器连接到集线器，则可以执行`passive sniffing`（被动嗅探）。当在交换网络上执行嗅探时，称为`active sniffing`（主动嗅探），因为交换机会分割流量，并知道将流量发送到哪个特定端口，同时阻止其发往所有其他端口。交换机给任何想要出于合法或非法原因嗅探流量的人都设置了障碍。

由于交换机分割流量，因此不再可能通过将混杂模式设备连接到单个端口来监控所有流量。为了绕过这一限制，交换机制造商开发了称为端口镜像、交换机镜像的解决方案，或者在思科交换机上称为`switched port analyzers (SPANs)`（交换端口分析器）。跨接端口允许用户不仅查看发往其特定端口的流量，还能查看交换机转发的所有流量。此功能使交换机能够配置为：当数据被转发到交换机上的任意端口时，也会被转发到 SPAN 端口。在使用嗅探器以及 Snort 等入侵检测系统（IDS）等设备时，此功能非常有用。

### 易受攻击的 Web 应用程序

一种很好的学习方法是探索和利用预构建的、旨在故意被利用的应用程序。有些可作为虚拟机获得，有些则是包含工具集和虚拟机的完整独立环境。绝大多数都是免费的，因此几乎没有理由不准备一些，即使不运行它们。

一些易受攻击的 Web 应用程序遵循一个“主题”，例如商店或赌场，而其他完整环境则只是拥有丰富多彩的名称。

以下是一些易受攻击的 Web 应用程序或虚拟机的列表：

*   `BadStore`：`www.vulnhub.com/entry/badstore-123,41`
*   `WebSecurity Dojo`，一个包含多个虚拟机的学习环境：`sourceforge.net/projects/websecuritydojo`
*   `Metasploitable 2`：`information.rapid7.com/download-metasploitable-2017.html`
*   `DVWA`：`github.com/ethicalhack3r/DVWA`

### Microsoft Windows

CASP+ 不仅应具备与安全相关工具的良好实操知识，还应了解常见操作系统，如 Microsoft Windows 8x、Windows 10、Windows Server 2008、Windows Server 2012 和 Windows Server 2016。您目前可以在 `www.microsoft.com/en-us/windows-server/trial` 下载 Windows Server 2019 或云中的 Windows Server 的 180 天免费试用版。

可以在此处评估最新版本的 Windows Server：`www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2022`。

如果您必须使用 Windows 11，可以在此处下载：`www.microsoft.com/software-download/windows11`。

### Linux

Linux 系统被大多数大型组织使用。CASP+ 应对这些系统及其配置和安全加固方式有良好的基本了解。获取一些技能的一种方法是查看 Fedora Linux Security Lab（一个实时操作系统），网址为 `labs.fedoraproject.org/en/security`。

### 虚拟化工具

`Virtualization`（虚拟化）已成为一种广泛接受的手段，可在无需购买更多物理硬件的情况下增加基础设施。CASP+ 应了解基本的虚拟化产品，如 VMware Player、QEMU 和 VirtualBox。您可以在 `www.vmware.com/products/workstation-player.html` 下载 VMware Player，在 `www.qemu.org` 下载 QEMU，在 `www.virtualbox.org/wiki/Downloads` 下载 VirtualBox。

### 可视化工具

不要将其与虚拟化混淆，`data visualization`（数据可视化）是以图表或图形格式呈现数据。数据可视化让决策者以可视化方式查看分析数据，从而掌握困难的概念或识别新模式。通过交互式可视化，您可以利用技术深入钻取图表和图形以获取更多细节，从而将概念推进一步，交互式地更改所见数据及其处理方式。一些最流行的数据可视化工具包括 Tableau、Qlikview、FusionCharts、Highcharts、Datawrapper、Plotly 和 Sisense。

### 漏洞评估工具

`Vulnerability scanners`（漏洞扫描器）用于扫描内部或外部计算机的漏洞。一些漏洞评估工具是开源的，而另一些是商业的，可能需要年度订阅或许可费。这些工具可分为三大类：

#### 源代码扫描器

`Source code scanners`（源代码扫描器）可用于协助代码审查。如果您在软件产品开发期间有权访问代码，这些工具提供了查找常见问题和缺陷的能力。RATS 和 Flawfinder 就是此类工具。源代码扫描器可以检测缓冲区溢出、竞争条件、权限提升和输入污染等问题。虽然它们很有帮助，但这些工具可能会产生大量误报。这些工具擅长查找未执行适当边界检查的特定函数。C 语言中的某些函数不检查缓冲区大小，例如 `scanf()`、`strcpy()`、`bcopy()`、`vsprintf()` 和 `gets()`。

#### 应用程序扫描器

在某些情况下，您可能无法访问代码。例如，假设您刚购买了 Microsoft 最新的 Web 服务器产品；Microsoft 很可能不会授予您访问其代码的权限。这就是应用程序扫描器派上用场的情况。`Application scanners`（应用程序扫描器）可以测试已完成的应用程序，而非源代码。它们查找运行时可能发生的漏洞和其他问题。应用程序扫描器还可以进行输入和边界测试。

#### 系统扫描器

最后一类扫描器是`system scanners`（系统扫描器）。既然有工具可用于探测整个网络及所有连接到它的系统，为什么只检查单个应用程序呢？系统扫描器可以针对单个地址或一系列地址运行。系统级扫描器的主要优势在于，它们可以探测整个本地或远程系统或网络的各种漏洞。Nessus、SAINT 和 Retina 都是系统扫描器的示例。

使用漏洞扫描器时，您需要决定哪种方法最适合。例如，您可能从网络外部运行工具以查看攻击者可以访问什么内容，从网络内部在没有特定系统用户名和密码的情况下运行，或从网络内部使用带有用户名和密码的凭证扫描运行。每种方法将产生不同的结果。在网络安全边界外运行具有从外部人员视角查看网络的优势。只需记住，这无法告知用户关于用户权限的任何信息，甚至无法告知什么需要修补或更新。有许多漏洞扫描工具可用。此处列出其中几个：

*   **Open Vulnerability Assessment System** `Open Vulnerability Assessment System (OpenVAS)` 是一个用于漏洞扫描的漏洞评估框架。OpenVAS 提供当前漏洞的每日更新。
*   **Nessus** 这是一款成熟的漏洞扫描器，可以扫描各种系统，如 Unix、Linux 和 Windows 计算机。
*   **SAINT** SAINT 是一款商业漏洞扫描和识别工具。

