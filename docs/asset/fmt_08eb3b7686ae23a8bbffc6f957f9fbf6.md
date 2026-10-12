
### S

*   **Snort_inline**，170
*   **防火墙**，126
*   **受限**，116
*   **用于保护网络免受恶意软件侵害**，68–69
*   **传感器**，147
*   **SIEM**，132–133
*   **虚拟化**，114–115，117–119
*   **VMware**，118–120
*   **蠕虫**，71–72

*   **Solaris 蜜罐**，93，109
*   **源头/起源**，2
*   **Specter 蜜罐**，112
*   **SQL Slammer 蠕虫**，74
*   **有状态协议分析方法**，137–139
    *   缺点，138–139
    *   专有，138
    *   协议模型，138–139
    *   状态跟踪特性，138
*   **静态概况**，异常，136
*   **隐身模式**，143
*   **Stoll, Clifford**，87–88
*   **Sub7 特洛伊木马**，92
*   **子进程控制服务**，93
*   **Sun Solaris 系统**，73
*   **系统调用监控技术**，156

### T

*   **机会主义攻击者**，104
*   **TCP/IP**
    *   实现，62–63
    *   按操作系统划分的参数，63t
    *   不使用 TCP/IP 的 Sebek，169
    *   协议族，15，18
*   **TCP 扫描**，48–54
    *   ACK 扫描，51
    *   连接/全打开扫描，49
    *   连接握手，49f
    *   FIN 扫描，50
    *   分片扫描，51
    *   FTP 反弹攻击，53，54f
    *   半打开/SYN 扫描，50
    *   空闲/哑扫描，51–52，53f
    *   反向标志扫描，51
    *   IP 欺骗，53
    *   空扫描，50–51
    *   会话劫持，52
    *   慢速扫描，49–50
    *   Xmas/Xmas-tree 扫描，50，50f
*   **威胁**
    *   信息系统，41–42
    *   蜜罐类型，95–99
        *   高级黑客攻击，97–98
        *   攻击者动机，98–99
        *   脚本小子攻击，95–97
*   **三次握手过程**，22，23f
*   **训练期**，136
*   **传输控制协议 (TCP)**，18，21–22
    *   连接建立，22
    *   段结构，21，22f
*   **隧道技术**，HTTP，47–48，48f
*   **双绞线电缆**，5–6

### U

*   **UNIX/Linux 平台**，65
*   **用户数据报协议 (UDP)**，18，74
    *   扫描，57

### V

*   **Vanilla scan（标准扫描）**，49
*   **Virtual honeynet（虚拟蜜网）**，114–115
    *   advantages of（优势），114–115
    *   hybrid virtual（混合虚拟），116–117
    *   self-contained（自包含），115–116
    *   virtualization software（虚拟化软件），117–118
*   **VMware ground storm X (GSX)**，119–121
*   **VMware workstation**，117–119, 170
    *   advantages（优势），117–118
    *   disadvantages（劣势），118

### W

*   **Walleye Web interface（Walleye Web 界面）**，168
*   **Weak security methods（弱安全方法）**，150
*   **Wide area network (WAN)（广域网）**，7
*   **Wildcard bytes（通配符字节）**，77
*   **Windows Local Security Authority Service Server (LSASS)（Windows 本地安全机构服务服务器）**，75
*   **Wired networks（有线网络）**，5–6
*   **Wireless IDPS（无线 IDPS）**，130, 132, 146–151, 162*t*
    *   advantages of（优势），148
    *   intrusion prevention capabilities（入侵防御能力），149
    *   security capabilities（安全能力），148–150
    *   weak security methods（弱安全方法），150
*   **Wireless LANs (WLANs)（无线局域网）**，58, 147–148
*   **Wireless networks（无线网络）**，6
*   **World Wide Web（万维网）**，46
*   **Worms, computer（计算机蠕虫）**，70–72
    *   architecture（架构），71–72
    *   attack（攻击），70
    *   examples（示例），72–75
        *   Allaple，75
        *   Blaster（冲击波），74–75
        *   Code Red and Code Red II（红色代码和红色代码 II），73–74
        *   Conficker（震网/Conficker），75
        *   Melissa（梅丽莎），73
        *   Morris（莫里斯），72–73
        *   Nimda or W32/Nimda（尼姆达或 W32/Nimda），74
        *   Sadmind，73
        *   Sasser（震荡波），75
        *   SQL slammer（SQL 冲击波），74
    *   polymorphic（多态性），75–78
        *   analysis（分析），76–77
        *   signature generation for（特征码生成），77
        *   structure（结构），76
        *   techniques（技术），77–78
    *   prevention and detection（预防与检测），78–80
        *   of exploits（针对漏洞利用），79–80
        *   of vulnerabilities（针对漏洞），79
    *   spread of（传播），70–71

### X

*   **Xmas/Xmas-tree scan（Xmas/Xmas 树扫描）**，50, 50*f*

### Z

*   **Zero-day attacks（零日攻击）**，84, 107
*   **Zero-day exploits（零日漏洞利用）**，110

---

1.  设备中上层 OSI 功能的存在要求其也应执行所有下层的任务，即它应实现到该层级的所有层。因此，如果我们说一个设备是第 3 层设备或属于第 3 层，这意味着它实现（或执行与之相关的动作）了从第 1 层到第 3 层的所有层。↩

2.  此处术语 `device`（设备）在技术上是指 `interface of a device`（设备接口）。由于一个设备可以拥有多个网络接口，这些接口中的每一个都将拥有自己的 MAC 地址。然而，在上层，所有这些独立的数据流可能会为了单一通信目的而合并。例如，路由器通常有多个接口，转发工作是通过将数据包——在其中一个接口上接收——中继到一个合适的接口来执行的。↩

3.  以太网和 802.3 如今通常被视为同一标准。然而，它们在原始设计上存在细微的技术差异。↩

4.  尽管图中未显示，网桥（如果需要）也支持 IEEE 无线 PHY/MAC 标准。↩

5.  由于一个十六进制数字等于四个二进制数字，每个数字将有四个十六进制数字。↩

6.  存在 DHCP offer（提供）不进行广播的情况，例如，当客户端已拥有 IP 地址并仅请求延长租约时。↩

7.  在计算机安全语境下有多个方面，如硬件和软件；然而，本书的重点是利用计算机通过计算机网络进行的通信。↩

8.  CIA 一词最熟悉的用法是指中央情报局；因此，在文献中一些作者也使用 `AIC triad`（AIC 三要素）一词以避免混淆。↩

9.  在黑客攻击中，侦察技术进一步分为足迹、枚举或扫描等组。文中所述的横幅抓取攻击无法精确归入这些子类中的任何一个，因为它实现了多种目的。↩

10.  在黑客攻击中，侦察技术进一步分为足迹、枚举或扫描等组。文中所述的横幅抓取攻击无法精确归入这些子类中的任何一个，因为它实现了多种目的。↩

11.  并非 HTTP 报文从不受限。然而，限制 HTTP 流量的通常场景是限制针对某些已知统一资源定位符（URL）的 HTTP 请求，而此处并非这种情况。↩

12.  我们此处刻意避免使用 `攻击者` 一词，因为并非所有 HTTP 隧道的用途都被一致认为是恶意的。↩

13.  `ACK` 标志通常会在握手过程的前两个步骤之后的所有段中被置位，因为它们都是确认段。↩

14.  如果两个或多个主机的帧在同时传输时可能发生碰撞，则认为它们处于同一冲突域中。↩
