
在本测试中，我从无线接入点中获取了大量信息，包括型号、固件版本和系统运行时间。这些信息如果攻击者想利用该系统中已知的漏洞，就可以用于针对主机进行攻击。通过进一步挖掘，我发现了该接入点上的多个管理界面用户名，如图 9-5 所示。你绝对不想把这些信息公开。

![ FIGURE 9-5:  Management interface user IDs gleaned via Getif’s SNMP browsing function.](images/9781119485476-fg0905.png)

[FIGURE 9-5:](#c09.xhtml#rc09-fig-0005) Management interface user IDs gleaned via Getif’s SNMP browsing function.

#### Countermeasures against SNMP attacks

![remember](images/remember.png)防止 SNMP 攻击可以很简单，ABC：

*   **A**lways disable SNMP on hosts if you’re not using it — period.

*   **B**lock the SNMP ports (UDP ports 161 and 162) at the network perimeter.

*   **C**hange the default SNMP community read string from `public` and the default community write string from `private` to another long, complex value that’s virtually impossible to guess.

技术上，U 是解决方案的一部分：升级。将系统（至少是你可以升级的系统）升级到 SNMP 版本 3，可以解决许多已知的 SNMP 安全弱点。

### 抓取横幅

*Banners* 是网络主机欢迎屏幕，显示软件版本号和其他系统信息。这些横幅信息可能识别操作系统、版本号以及特定服务包，为攻击者提供攻击网络的优势。你可以使用传统的 Telnet 或我提到的工具（如 Nmap 和 SoftPerfect Network Scanner）来抓取横幅。

#### Telnet

你可以通过默认 Telnet 端口（TCP 端口 23） Telnet 到主机上，看看是否会出现登录提示或其他信息。只需在 Windows 或 Unix 的命令行中输入以下命令：

`telnet ip_address`

你可以通过以下命令 Telnet 到其他常用端口：

*   **SMTP:**  `telnet ip_address 25` 

*   **HTTP:**  `telnet ip_address 80` 

*   **POP3:**  `telnet ip_address 110` 

[Figure 9-6](#c09.xhtml#c09-fig-0006) 展示了我通过 Telnet 连接到 25 端口的 IceWarp 邮件服务器时获取的具体版本信息。关于 Telnet 的帮助，输入 `telnet /?` 或 `telnet help` 可获得程序的具体使用指南。

![ FIGURE 9-6:  Information gathered about an email server via Telnet.](images/9781119485476-fg0906.png)

[FIGURE 9-6:](#c09.xhtml#rc09-fig-0006)  Information gathered about an email server via Telnet.

#### Countermeasures against banner-grabbing attacks

以下步骤可降低横幅抓取攻击的风险：

*   如果没有业务需求的服务会泄露横幅信息，请在网络主机上禁用这些未使用的服务。

*   如果没有业务需求的默认横幅，或可以自定义横幅，请配置网络主机的应用程序或操作系统以禁用横幅或从横幅中去除攻击者可能利用的信息。请参考特定厂商的说明。Linux 的 TCP Wrappers 也是一种解决方案。

![tip](images/tip.png)如果你可以自定义横幅，请咨询律师是否在横幅上添加警告。此类警告横幅不能阻止横幅抓取，但会向潜在入侵者表明系统是私有且受监控（假设真的如此）。警告横幅在安全事件发生时，也可能帮助降低公司责任。示例如下：

> *Warning! This is a private system. All use is monitored and recorded. Any unauthorized use of this system may result in civil and/or criminal prosecution to the fullest extent of the law.*

### 测试防火墙规则

在安全测试中，你可以检查防火墙规则，确保它们按预期工作。

#### 测试

几项测试可验证防火墙实际执行的功能。你可以通过防火墙连接开放的端口，但对于那些可能开放但本不该开放的端口呢？

#### NETCAT

你可以使用 Netcat（[`http://netcat.sourceforge.net`](http://netcat.sourceforge.net)）在不直接测试生产系统的情况下测试特定防火墙规则。例如，你可以检查防火墙是否允许 Telnet（端口 23）通过。按照以下步骤查看是否可以通过端口 23 建立连接：

1.  **在网络内部的客户机上加载 Netcat。**

    此步骤设置出站连接。

2.  **在防火墙外部的测试机上加载 Netcat。**

    此步骤允许从外部向内部进行测试。

3.  **在客户机（内部）机器上输入 Netcat 监听命令，并指定要测试的端口号。**

    如果你在测试端口 23，输入以下命令：

    `nc –l –p 23 cmd.exe`

4.  **在测试（外部）机器上输入 Netcat 命令以发起入站会话。**

    必须包含以下信息：

    *   你正在测试的内部机器的 IP 地址。

    *   你正在测试的端口号。

    如果内部（客户）机器的 IP 地址是 10.11.12.2，端口是 23，输入以下命令：

    `nc –v 10.11.12.2 23`

如果 Netcat 在外部机器上显示新的命令提示符（Step 3 中的 `cmd.exe` 用途），则说明已建立连接，你可以在内部机器上执行命令！这可以用于多种目的，包括测试防火墙规则、网络地址转换（NAT）、端口转发，以及——呃，执行远程系统上的命令！

#### RULEBASE ANALYZERS

你可以找到多种防火墙规则分析工具，例如 SolarWinds Network Configuration Manager（[`https://www.solarwinds.com/network-configuration-manager`](https://www.solarwinds.com/network-configuration-manager)）和 Firemon Risk Analyzer（[`https://www.firemon.com/products/risk-analyzer`](https://www.firemon.com/products/risk-analyzer)）。这些工具允许你对所有主要厂商的防火墙规则库进行深入分析，以发现传统漏洞扫描和渗透测试可能无法发现的安全缺陷和低效之处。防火墙规则库分析类似于软件源代码分析，因为它能在源码层面找到人眼在进行深入安全测试时（从 Internet 和内部网络）很少能看到的缺陷。如果你从未进行过防火墙规则库分析，强烈推荐你进行一次！

#### 防火墙规则库漏洞的防范措施

以下防范措施可防止黑客测试你的防火墙：

*   **执行防火墙规则库审计。** 我总是说，你不能保护你不认识的东西，防火墙规则库就是最好的例子。无论规则库看起来多么简单，使用自动化工具验证工作从未有害。

*   **仅允许必要的流量。** 在防火墙（如有需要，也在路由器）上设置规则，仅允许必须通过的流量。你可能已经有规则允许内部 web 服务器的入站 HTTP 流量、内部 email 服务器的入站 SMTP 流量，以及外部网络访问的出站 HTTP 流量。

    ![remember](images/remember.png)这些规则是防御试图探测你防火墙的最佳手段。

*   **阻止 ICMP。**

    这有助于防止外部攻击者探测网络，看哪些主机是存活的。

*   **在防火墙上启用状态包检查。**

    这将阻止未经请求的网络请求。

### 分析网络数据

