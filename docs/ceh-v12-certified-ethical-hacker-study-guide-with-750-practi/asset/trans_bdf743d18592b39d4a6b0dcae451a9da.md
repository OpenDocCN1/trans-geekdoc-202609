
-   [ARP]的缩写是 **Address Resolution Protocol**，它用于在本地网络中将 **IP 地址** 映射到 **MAC 地址**。

3. [DNS]的缩写是 **Domain Name System**，它负责在因特网上将 **域名** 转换为 **IP 地址**。

4. [RARP]的缩写是 **Reverse Address Resolution Protocol**，它用于将 **MAC 地址** 解析为 **IP 地址**。

5. 将包含 **AAAAAAAAAAAAAAAA**（共 16 个字符）的字符串写入只分配了 **8 字节** 内存空间会导致 **缓冲区溢出（Buffer overflow）**，因为数据超出了分配的存储空间，可能覆盖相邻的内存。

1. [Heap spraying]是一种通过大量分配内存来填充堆区的技术，常用于绕过防护机制。

2. [SQL injection]是通过在输入中注入恶意的 SQL 语句，以此操控数据库后端的攻击手段。

3. [Buffer overflow]是指向量超出其预期的长度，导致内存被破坏或执行任意代码的漏洞。

4. [Slowloris attack]是一种通过长时间打开少量连接，占用服务器资源从而导致服务不可用的拒绝服务攻击。

6. 子网掩码 **255.255.248.0** 对应的 CIDR 前缀是 **/21**。

1. [/23]是错误的，因为它只覆盖了 23 位，掩码长度不匹配。

2. [/22]是错误的，掩码长度为 22 位，范围不匹配。

3. [/21]是正确的，掩码长度为 21 位，正好对应 255.255.248.0。

4. [/20]是错误的，掩码长度为 20 位，范围不匹配。

7. 蠕虫（worm）与病毒（virus）的主要区别在于 **蠕虫可以自行传播**，而病毒通常需要宿主文件或程序作为载体。

1. [A worm uses polymorphic code]是错误的，蠕虫不一定使用多态代码。

2. [A virus uses polymorphic code]是错误的，虽然病毒可能使用多态代码，但这并不是两者的根本区别。

3. [A worm can self‑propagate]是正确的，蠕虫能够自行在网络中传播。

4. [A virus can self‑propagate]是错误的，病毒需要借助其他程序或文件传播。

8. 计算风险的常用公式是 **Probability × Loss**（即概率乘以潜在损失）。

1. [Probability * loss]是正确的。

2. [Probability * mitigation factor]是错误的，因为它引入了缓解因子，而不是直接的损失。

3. [(Loss + mitigation factor) * (loss/probability)]是错误的，公式不合逻辑。

4. [Loss * mitigation factor]是错误的，缺少概率因子。

9. 恶意双子（evil twin）攻击的工作方式是 **冒充合法的无线接入点（AP）**，诱骗用户连接到攻击者控制的 AP，从而可以拦截或篡改流量。

1. [Phishing users for credentials]是错误的，这是钓鱼攻击，不是双子攻击。

2. [Spoofing an SSID]是正确的，攻击者伪装 AP 的 SSID 以误导用户。

3. [Changing an SSID]是错误的，单纯更改 SSID 并不能实现双子攻击。

4. [Injecting four‑way handshakes]是错误的，这与攻击的核心机制无关。

10. 在端点之前、网络层面清除恶意软件的常用手段是 **统一威胁管理（Unified threat management）设备**。

1. [Antivirus]是错误的，它主要在终端层面工作。

2. [Application layer gateway]是错误的，它主要处理应用层流量，而非网络层恶意软件清除。

3. [Unified threat management appliance]是正确的，它集成了防火墙、入侵防御等功能，可在网络层面阻断恶意软件。

4. [Stateful firewall]是错误的，它只能基于连接状态过滤流量，无法主动清除恶意软件。

11. 安全策略的主要目的是 **为安全提供高层次的指导**，帮助组织制定整体的安全方针和原则。

1. [Providing high‑level guidance on the role of security]是正确的。

2. [Providing specific direction to security workers]是错误的，这是详细操作指南，而非策略的主要目的。

3. [Increasing the bottom line of a company]是错误的，安全策略的核心不是财务增长。

4. [Aligning standards and practices]是错误的，虽然对齐很重要，但不是策略的首要目的。

12. 给定的字符串 **%3Cscript%3Ealert('wubble');%3C/script%3E** 是 **URL 编码**（percent‑encoding）后的形式，其中 `%3C` 代表 `<`，`%3E` 代表 `>`，`%3E` 后面的部分是被编码的脚本代码。

1. [Base64 encoding]是错误的，Base64 使用 64 个字符的字母数字和符号集合。

2. [URL encoding]是正确的，这是典型的百分比编码形式。

3. [Encryption]是错误的，加密会产生不可读的二进制或 Base64 形式，而非 `%` 形式。

4. [Cryptographic hashing]是错误的，哈希值是固定长度的二进制或十六进制字符串，不会出现 `%` 编码。

13. 运行 `dig ns domain.com` 会查询 **域名系统（DNS）名称服务器（NS）记录**，返回该域名的 **名称服务器（Name server）记录**。

1. [Mail exchanger records for domain.com]是错误的，那是 MX 记录。

2. [Name server records for domain.com]是正确的，dig ns 会返回 NS 记录。

3. [Caching name server for domain.com]是错误的，dig 本身不返回缓存信息。

4. [IP address for the hostname ns]是错误的，dig ns 返回的是域名对应的名称服务器，而不是 IP。

14. 理想情况下用于获取域名所有主机名的技术是 **区域传输（Zone transfer）**，即从主 DNS 服务器将整个区域的记录复制到从属服务器。

1. [DNS query]是错误的，普通查询只能获取单个主机名。

2. [Zone copy]是错误的，这通常指手动复制区域文件，而不是自动传输。

3. [Zone transfer]是正确的，它允许获取完整的区域记录。

4. [Recursive request]是错误的，普通递归查询只返回域名对应的记录，而非全部主机名。

15. 在数据包捕获中看到 **操作系统命令** 包含在 DNS 查询中，最可能的情况是 **隧道攻击（Tunneling attack）**，攻击者将非 DNS 的二进制数据封装在 DNS 报文中进行传输。

1. [Tunneling attack]是正确的。

2. [DNS amplification]是错误的，它是指利用 DNS 服务器放大流量的攻击。

3. [DNS recursion]是错误的，它是 DNS 服务器内部的查询机制。

4. [XML entity injection]是错误的，它针对 XML 解析器，与 DNS 无关。

16. 运行 **ping sweep**（ICMP echo sweep）的目的是 **在不进行端口扫描的情况下识别哪些主机是响应的**。

1. [You want to identify responsive hosts without a port scan]是正确的。

2. [You want to use something that is light on network traffic]是错误的，ping sweep 本身会产生大量 ICMP 包。

3. [You want to use a protocol that may be allowed through the firewall]是错误的，ICMP 通常被防火墙阻断或受限。

4. [All of the above]是错误的，因为只有第一项是正确的。

17. 根据 NIST 网络安全框架（NIST Cybersecurity Framework），其核心功能（Framework Functions）包括 **Identify、Protect、Detect、Respond、Recover**，共 **5** 个功能。

1. [0]是错误的。

2. [3]是错误的。

3. [5]是正确的。

4. [4]是错误的。

18. 不写恶意软件的一个原因是 **Python 解释器可能不存在于目标系统上**。

1. [The Python interpreter is slow]是错误的，Python 解释器的性能不是主要考虑因素。

2. [The Python interpreter may not be available]是正确的。

3. [There is inadequate library support]是错误的，Python 拥有丰富的第三方库。

4. [Python is a hard language to learn]是错误的，Python 以易学著称。

19. 命令 `tcpdump -i eth2 host 192.168.10.5` 捕获的是 **仅来自 192.168.10.5 的流量**（即源地址为该 IP 的包）。

1. [Traffic just from 192.168.10.5]是正确的。

2. [Traffic to and from 192.168.10.5]是错误的，因为只限定了源地址。

3. [Traffic just to 192.168.10.5]是错误的，因为只限定了目的地址。

4. [All traffic other than from 192.168.10.5]是错误的，与捕获条件相反。

20. Diffie‑Hellman 协议主要用于 **密钥交换（Key exchange）**，使两方安全地协商共享密钥。

1. [Key management]是错误的，它涉及密钥的生成、分发、存储和撤销，而非交换。

2. [Key isolation]是错误的，与密钥交换无关。

3. [Key exchange]是正确的。

4. [Key revocation]是错误的，撤销是后续管理步骤。

21. 社会工程学中的 **权威（Authority）** 原则可以让假扮帮助台的电话更容易被接受。

1. [Social proof]是错误的，它基于他人行为的认可。

2. [Imitation]是错误的，它强调模仿而非权威。

3. [Scarcity]是错误的，它基于稀缺性。

4. [Authority]是正确的。

22. SNMPv1 使用 **公共字符串（Community string）** 进行身份验证。

1. [Username/password]是错误的，SNMPv1 不支持用户名和密码。

2. [Hash]是错误的，SNMPv1 没有哈希验证。

3. [Public string]是错误的，虽然有时会被误称为 “public string”，但标准术语是 “community string”。

4. [Community string]是正确的。

23. Java 程序在网络中共享过程时，使用 **RMI 注册表（RMI registry）** 来注册和查找远程对象。

1. [RMI registry]是正确的。

2. [RMI mapper]是错误的，不存在此术语。

3. [RMI database]是错误的，没有此概念。

4. [RMI process]是错误的，RMI 与进程无直接关系。

24. 一个 **没有对应的 ARP 请求** 的 ARP 响应称为 ** gratuitous ARP**（ gratuitous response）。

1. [Is‑at response]是错误的。

2. [Who‑has ARP]是错误的。

3. [Gratuitous ARP]是正确的。

4. [IP response]是错误的。

25. 文件元数据中通常存储的三个时间点是 **修改时间（Modified）**、**访问时间（Accessed）**、**创建时间（Created）**。

1. [Moves, adds, changes]是错误的。

2. [Modified, accessed, deleted]是错误的，缺少创建时间且包含删除时间。

3. [Moved, accessed, changed]是错误的。

4. [Modified, accessed, created]是正确的。

26. 使用本地漏洞的 **特权提升（Privilege escalation）** 是最常见的原因。

1. [Pivoting]是错误的，它是利用已获取的权限进行进一步攻击。

2. [Log manipulation]是错误的，与特权提升无关。

3. [Privilege escalation]是正确的。

4. [Password collection]是错误的，与特权提升无直接关联。

27. 为了证明 **签名消息** 确实来自拥有私钥的所有者，使用 **非否认性（Nonrepudiation）** 原则。

1. [Nonrepudiation]是正确的。

2. [Nonverifiability]是错误的，这是一个不常用的术语。

3. [Integrity]是错误的，它只保证数据未被篡改，而不保证签名来源。

4. [Authority]是错误的，与签名验证无关。

28. 防御 **尾随（tailgating）** 的可行做法是 **人防（Man traps）**，即在入口处设置物理阻挡，只有持有有效凭证的人才能进入。

1. [Biometrics]是错误的，它用于身份验证，但不能阻止尾随。

2. [Badge access]是错误的，它本身不防止尾随。

3. [Phone verification]是错误的，与物理访问控制无关。

4. [Man traps]是正确的。

29. **蓝牙窃听（bluesnarfing）** 比 **蓝牙推送（bluejacking）** 更危险，因为 **蓝牙窃听会接收（接收）数据**，而蓝牙推送只会发送（发送）数据。

1. [Bluejacking sends, while bluesnarfing receives.]是正确的。

2. [Bluejacking receives, while bluesnarfing sends.]是错误的。

3. [Bluejacking installs keyloggers.]是错误的。

4. [Bluesnarfing installs keyloggers.]是错误的。

30. **Biba 安全模型** 关注的是 **完整性（Integrity）**，防止未经授权的提升或降低完整性的操作。

1. [Confidentiality]是错误的。

2. [Integrity]是正确的。

3. [Availability]是错误的。

4. [All of them]是错误的。

**Assessment Test Answers**

1. **B** The destination address is used as the address to send messages to. The don't fragment bit is used to tell network devices not to fragment the packet. The Type of Service (ToS) field can be used to perform quality of service. The IP identification field is used to identify fragments of the same packet, as they would all have the same IP identification number.

2. **C** A SQL injection attack makes use of SQL queries, which can include logic that may alter the flow of the application. In the example provided, the intent is to force the result of the SQL query to always return a true. It is quoted the way it is to escape the existing query already in place in the application. None of the other attacks uses a syntax that looks like the example.

3. **C** The Apple App Store and the Google Play Store are controlled by Apple and Google. It's not impossible to get malware onto mobile devices that way, but it's very difficult because apps get run through a vetting process. While some Android devices will support external storage, it's not an effective way to get malware onto a smartphone or other mobile device. Jailbreaking can lead to malware being installed, but it's not the means to get malware onto a mobile device. Third‑party app stores can be a good means to get malware onto mobile devices because some third‑party app stores don't vet apps that are submitted.

4. **B** DHCP is used to get IP configuration to endpoints. DNS is used to resolve a hostname to an IP address and vice versa. RARP is the reverse address protocol used to take a MAC address and resolve it to an IP address. ARP is used to resolve an IP address to a MAC address. Communication on a local network requires the use of a MAC address. The IP address is used to get to systems off the local network.
