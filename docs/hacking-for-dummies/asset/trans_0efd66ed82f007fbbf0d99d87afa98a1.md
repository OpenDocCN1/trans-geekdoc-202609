
![ FIGURE 9-8:  Omnipeek 可以帮助发现某人运行非法系统，例如 FTP 服务器。](images/9781119485476-fg0908.png)

[FIGURE 9-8:](#c09.xhtml#rc09-fig-0008)  Omnipeek 可以帮助发现某人运行非法系统，例如 FTP 服务器。

查看你的网络统计信息（如每秒字节数、网络利用率以及入站/出站数据包数量）是另一种确定是否有异常情况的好方法。[Figure 9-9](#c09.xhtml#c09-fig-0009) 通过强大的 CommView 网络分析器查看网络统计信息。

![ FIGURE 9-9:  CommView 的界面用于查看网络统计信息](images/9781119485476-fg0909.png)

[FIGURE 9-9:](#c09.xhtml#rc09-fig-0009)  CommView 的界面用于查看网络统计信息

TamoSoft（CommView 的开发商）还有一个名为 NetResident 的产品（[`https://www.tamos.com/products/commview`](https://www.tamos.com/products/commview)），可以跟踪常见协议的使用情况，如 HTTP、电子邮件、FTP 和 Voice over Internet Protocol（VoIP）。如 [Figure 9-10](#c09.xhtml#c09-fig-0010) 所示，你可以使用 NetResident 监控 Web 会话并回放它们。

![ FIGURE 9-10:  NetResident 可以跟踪 Internet 使用并确保安全策略得到执行。](images/9781119485476-fg0910.png)

[FIGURE 9-10:](#c09.xhtml#rc09-fig-0010)  NetResident 可以跟踪 Internet 使用并确保安全策略得到执行。

NetResident 还能通过其 PromiSwitch 工具（在工具菜单中可用）进行 ARP 中毒，这使得 NetResident 能够看到本地网络段上的所有流量。我在本章后面的“[The MAC-daddy attack](#c09.xhtml#c09-sec-0029)”中会介绍 ARP 中毒。

#### 对网络协议漏洞的防范措施

网络分析器可以用于善意或恶意。善意确保你的安全策略得到遵守，恶意则帮助对手针对你进行攻击。几种防范措施可以帮助降低有人使用未经授权网络分析器的风险。请记住，完全防止它是不可能的。

![warning](images/warning.png)如果外部攻击者或恶意用户能够物理或无线方式连接到你的网络，他可以捕获网络上的数据包，即使你使用的是以太网交换机。

#### 物理安全

确保已采取适当的物理安全措施，防止有人通过插入网线接入你的网络，具体做法包括：

*   **将坏人挡在服务器室和布线间隔之外。** 确保以太网交换机上的 Web、Telnet 和 Secure Shell（SSH）管理界面尤其安全，防止有人更改交换机端口配置并窃听所有经过的流量。

*   **确保未受监督的区域（如空置的大堂或培训室）没有活动的网络连接。**

有关物理安全的详细信息，请参见 [Chapter 7](#c07.xhtml)。

#### 网络分析器检测

你可以使用一些较旧的工具来判断是否有人在你的网络上运行未经授权的网络分析器：

*   **Sniffdet** ([`http://sniffdet.sourceforge.net`](http://sniffdet.sourceforge.net)) 用于类 Unix 系统。

*   **PromiscDetect** ([`http://ntsecurity.nu/toolbox/promiscdetect`](http://ntsecurity.nu/toolbox/promiscdetect)) 用于 Windows。

某些 IPS 也能够检测网络分析器是否在你的网络上运行。这些工具可以监控网络中处于混杂模式的以太网卡。你只需在电脑上加载这些程序，它们会在检测到网络中出现混杂行为（Sniffdet）或本地系统（PromiscDetect）时发出警报。

### The MAC-daddy attack

攻击者可以利用网络中的 ARP（地址分辨率协议）使他们的系统看起来像是你的系统或网络中另一台受信任的主机。

#### ARP spoofing

大量的 ARP 请求可能是 *ARP spoofing*（也称为 *ARP poisoning*）攻击的迹象。

运行诸如 dsniff（[`https://www.monkey.org/~dugsong/dsniff`](https://www.monkey.org/~dugsong/dsniff)）或 Cain & Abel 的客户端可以修改 ARP 表——这些表存储 IP 地址到媒体访问控制（MAC）地址的映射。修改 ARP 表会导致受害计算机在网络通信时，错误地将流量发送到攻击者的机器，而不是真正的目的主机。ARP spoofing 常用于中间人攻击。

伪造的 ARP 回复可以发送到交换机，使其回退到广播模式，基本上把交换机变成集线器。发生这种攻击时，攻击者能够截获交换机上所有经过的数据包，捕获网络上的任何内容。

![remember](images/remember.png)此安全漏洞源于 TCP/IP 通信处理方式本身的固有缺陷。

下面是一个典型的 ARP 中毒攻击示例，涉及攻击者的电脑（Hacky）和两个合法用户的电脑（Joe 和 Bob）：

1.  Hacky 使用诸如 dsniff、ettercap 或 netcat 等工具中毒化受害者 Joe 和 Bob 的 ARP 缓存。

2.  Joe 将 Hacky 的 MAC 地址与 Bob 的 IP 地址关联。

3.  Bob 将 Hacky 的 MAC 地址与 Joe 的 IP 地址关联。

4.  Joe 的流量和 Bob 的流量首先发送到 Hacky 的 IP 地址。

5.  Hacky 的网络分析器捕获 Joe 的和 Bob 的流量。

![remember](images/remember.png)如果 Hacky 配置为像路由器一样转发数据包，它会将流量转发到原始目的地。发送方和接收方毫无察觉！

#### 使用 Cain & Abel 进行 ARP 中毒

你可以在交换以太网网络上使用 Cain & Abel 进行 ARP 中毒，以测试你的 IPS 或观察交换机如何被转换为集线器并被网络分析器捕获。

![warning](images/warning.png)ARP 中毒可能对网络硬件和健康造成危害，导致停机甚至更严重的后果。请小心！

使用 Cain & Abel 进行 ARP 中毒的步骤如下：

1.  **加载 Cain & Abel，然后点击 Sniffer 标签进入网络分析器模式。** 默认会打开 Hosts 页面。

2.  **点击黄黑相间的圆形图标（Start/Stop APR）启动 ARP 中毒路由过程并启用内置嗅探器。**

3.  **如果系统提示，选择出现的窗口中的网络适配器，然后点击 OK。**

4.  **点击蓝色加号（+）图标，将要进行 ARP 中毒的主机添加进去。**

5.  **在 MAC Address Scanner 窗口中，确保选中 “All Hosts in My Subnet” 选项，然后点击 OK。**

6.  **点击 APR 标签（带有黄黑圆形图标）加载 APR 页面。**

7.  **在 “Status” 列标题下方的空白区域点击，重新启用蓝色加号。**

8.  **点击蓝色加号。** “New ARP Poison Routing” 窗口会显示步骤 4 中发现的主机。

9.  **Ctrl+单击右侧列中你想中毒的所有主机。** 右侧列会填充剩余的所有主机，如 [Figure 9-11](#c09.xhtml#c09-fig-0011) 所示。

10. **按 Ctrl+点击右侧列中想要中毒的所有主机。**

11. **点击 OK 开始 ARP 中毒过程。** 根据网络硬件和每个主机的本地 TCP/IP 栈，该过程可能需要几秒到几分钟。[Figure 9-12](#c09.xhtml#c09-fig-0012) 展示了我在测试网络上进行 ARP 中毒的结果。

12. **点击 Passwords 标签，使用内置密码功能捕获 traversing 网络的各种主机之间的密码。** 

![ FIGURE 9-11:  在 Cain & Abel 中选择要中毒的受害主机。](images/9781119485476-fg0911.png)
