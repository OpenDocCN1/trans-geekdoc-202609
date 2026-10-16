
### 3. Zone transfer
[Zone transfer]是正确的，它允许获取完整的区域记录。

### 4. Recursive request
[Recursive request]是错误的，普通递归查询只返回域名对应的记录，而非全部主机名。

### 15. 隧道攻击
在数据包捕获中看到 `操作系统命令` 包含在 DNS 查询中，最可能的情况是 `隧道攻击（Tunneling attack）`，攻击者将非 DNS 的二进制数据封装在 DNS 报文中进行传输。

1. [Tunneling attack]是正确的。
2. [DNS amplification]是错误的，它是指利用 DNS 服务器放大流量的攻击。
3. [DNS recursion]是错误的，它是 DNS 服务器内部的查询机制。
4. [XML entity injection]是错误的，它针对 XML 解析器，与 DNS 无关。

### 16. Ping sweep 目的
运行 `ping sweep`（ICMP echo sweep）的目的是 `在不进行端口扫描的情况下识别哪些主机是响应的`。

1. [You want to identify responsive hosts without a port scan]是正确的。
2. [You want to use something that is light on network traffic]是错误的，ping sweep 本身会产生大量 ICMP 包。
3. [You want to use a protocol that may be allowed through the firewall]是错误的，ICMP 通常被防火墙阻断或受限。
4. [All of the above]是错误的，因为只有第一项是正确的。

### 17. NIST 网络安全框架
根据 NIST 网络安全框架（NIST Cybersecurity Framework），其核心功能（Framework Functions）包括 `Identify`、`Protect`、`Detect`、`Respond`、`Recover`，共 `5` 个功能。

1. [0]是错误的。
2. [3]是错误的。
3. [5]是正确的。
4. [4]是错误的。

### 18. 不写恶意软件的原因
不写恶意软件的一个原因是 `Python 解释器可能不存在于目标系统上`。

1. [The Python interpreter is slow]是错误的，Python 解释器的性能不是主要考虑因素。
2. [The Python interpreter may not be available]是正确的。
3. [There is inadequate library support]是错误的，Python 拥有丰富的第三方库。
4. [Python is a hard language to learn]是错误的，Python 以易学著称。

### 19. tcpdump 命令
命令 `tcpdump -i eth2 host 192.168.10.5` 捕获的是 `仅来自 192.168.10.5 的流量`（即源地址为该 IP 的包）。

1. [Traffic just from 192.168.10.5]是正确的。
2. [Traffic to and from 192.168.10.5]是错误的，因为只限定了源地址。
3. [Traffic just to 192.168.10.5]是错误的，因为只限定了目的地址。
4. [All traffic other than from 192.168.10.5]是错误的，与捕获条件相反。

### 20. Diffie-Hellman 协议
Diffie‑Hellman 协议主要用于 `密钥交换（Key exchange）`，使两方安全地协商共享密钥。

1. [Key management]是错误的，它涉及密钥的生成、分发、存储和撤销，而非交换。
2. [Key isolation]是错误的，与密钥交换无关。
3. [Key exchange]是正确的。
4. [Key revocation]是错误的，撤销是后续管理步骤。

### 21. 社会工程学权威原则
社会工程学中的 `权威（Authority）` 原则可以让假扮帮助台的电话更容易被接受。

1. [Social proof]是错误的，它基于他人行为的认可。
2. [Imitation]是错误的，它强调模仿而非权威。
3. [Scarcity]是错误的，它基于稀缺性。
4. [Authority]是正确的。

### 22. SNMPv1 身份验证
SNMPv1 使用 `公共字符串（Community string）` 进行身份验证。

1. [Username/password]是错误的，SNMPv1 不支持用户名和密码。
2. [Hash]是错误的，SNMPv1 没有哈希验证。
3. [Public string]是错误的，虽然有时会被误称为 `public string`，但标准术语是 `community string`。
4. [Community string]是正确的。

### 23. Java RMI 注册表
Java 程序在网络中共享过程时，使用 `RMI 注册表（RMI registry）` 来注册和查找远程对象。

1. [RMI registry]是正确的。
2. [RMI mapper]是错误的，不存在此术语。
3. [RMI database]是错误的，没有此概念。
4. [RMI process]是错误的，RMI 与进程无直接关系。

### 24. Gratuitous ARP
一个 `没有对应的 ARP 请求` 的 ARP 响应称为 `gratuitous ARP`（gratuitous response）。

1. [Is‑at response]是错误的。
2. [Who‑has ARP]是错误的。
3. [Gratuitous ARP]是正确的。
4. [IP response]是错误的。

### 25. 文件元数据时间点
文件元数据中通常存储的三个时间点是 `修改时间（Modified）`、`访问时间（Accessed）`、`创建时间（Created）`。

1. [Moves, adds, changes]是错误的。
2. [Modified, accessed, deleted]是错误的，缺少创建时间且包含删除时间。
3. [Moved, accessed, changed]是错误的。
4. [Modified, accessed, created]是正确的。

### 26. 特权提升
使用本地漏洞的 `特权提升（Privilege escalation）` 是最常见的原因。

1. [Pivoting]是错误的，它是利用已获取的权限进行进一步攻击。
2. [Log manipulation]是错误的，与特权提升无关。
3. [Privilege escalation]是正确的。
4. [Password collection]是错误的，与特权提升无直接关联。

### 27. 非否认性原则
为了证明 `签名消息` 确实来自拥有私钥的所有者，使用 `非否认性（Nonrepudiation）` 原则。

1. [Nonrepudiation]是正确的。
2. [Nonverifiability]是错误的，这是一个不常用的术语。
3. [Integrity]是错误的，它只保证数据未被篡改，而不保证签名来源。
4. [Authority]是错误的，与签名验证无关。

### 28. 防御尾随
防御 `尾随（tailgating）` 的可行做法是 `人防（Man traps）`，即在入口处设置物理阻挡，只有持有有效凭证的人才能进入。

1. [Biometrics]是错误的，它用于身份验证，但不能阻止尾随。
2. [Badge access]是错误的，它本身不防止尾随。
3. [Phone verification]是错误的，与物理访问控制无关。
4. [Man traps]是正确的。

### 29. 蓝牙窃听与蓝牙推送
`蓝牙窃听（bluesnarfing）` 比 `蓝牙推送（bluejacking）` 更危险，因为 `蓝牙窃听会接收数据`，而蓝牙推送只会发送数据。

1. [Bluejacking sends, while bluesnarfing receives.]是正确的。
2. [Bluejacking receives, while bluesnarfing sends.]是错误的。
3. [Bluejacking installs keyloggers.]是错误的。
4. [Bluesnarfing installs keyloggers.]是错误的。

### 30. Biba 安全模型
`Biba 安全模型` 关注的是 `完整性（Integrity）`，防止未经授权的提升或降低完整性的操作。

1. [Confidentiality]是错误的。
2. [Integrity]是正确的。
3. [Availability]是错误的。
4. [All of them]是错误的。

## Assessment Test Answers

### 1. B
The destination address is used as the address to send messages to. The don't fragment bit is used to tell network devices not to fragment the packet. The Type of Service (ToS) field can be used to perform quality of service. The IP identification field is used to identify fragments of the same packet, as they would all have the same IP identification number.

### 2. C
A SQL injection attack makes use of SQL queries, which can include logic that may alter the flow of the application. In the example provided, the intent is to force the result of the SQL query to always return a true. It is quoted the way it is to escape the existing query already in place in the application. None of the other attacks uses a syntax that looks like the example.

### 3. C
The Apple App Store and the Google Play Store are controlled by Apple and Google. It's not impossible to get malware onto mobile devices that way, but it's very difficult because apps get run through a vetting process. While some Android devices will support external storage, it's not an effective way to get malware onto a smartphone or other mobile device. Jailbreaking can lead to malware being installed, but it's not the means to get malware onto a mobile device. Third‑party app stores can be a good means to get malware onto mobile devices because some third‑party app stores don't vet apps that are submitted.

### 4. B
DHCP is used to get IP configuration to endpoints. DNS is used to resolve a hostname to an IP address and vice versa. RARP is the reverse address protocol used to take a MAC address and resolve it to an IP address. ARP is used to resolve an IP address to a MAC address. Communication on a local network requires the use of a MAC address. The IP address is used to get to systems off the local network.

### 7. C
既 `worms` 也 `viruses` 都可以编写使用多态代码，这意味着它们在传播时可以改变外观。`worm` 可以自行传播，这是 `worms` 与 `viruses` 的唯一区别。`viruses` 需要用户进行干预才能传播和执行。

### 8. A
风险是事件发生的概率乘以损失的金额。没有可量化的缓解因素，因此不能用于风险计算。

### 9. B
恶意双子攻击使用伪装的接入点，冒充合法的无线网络的连接点。终端尝试连接到该伪装的接入点。虽然可以在恶意双子攻击中钓鱼获取凭据，但凭据钓鱼并不是此类攻击的实现方式。SSID 不会在恶意双子攻击中被修改，这意味着已存在的任何 SSID 都不会变成另一个 SSID。注入四次握手并没有多大作用，因为四次握手假设双方都在通信，注入的完整通信流会被忽略。

### 10. C
防病毒解决方案用于终端或可能用于邮件服务器。状态防火墙能够考虑连接的状态——新建、相关、已建立。应用层网关了解应用层协议。统一威胁管理设备在防火墙功能之上增加了包括防病毒在内的能力。

### 11. A
标准和实践应来源于安全策略，这是对组织内安全角色的高层指导。安全通常不会直接提升公司的底线。策略并非提供具体指示，那是程序的作用。

### 12. B
Base64 编码将不可打印字符编码为可在文本中显示的形式。加密通常会使文本对人类不可读。加密散列是生成固定长度值以标识某值的方式。URL 编码使用十六进制表示字符，将文本转换为十六进制以便在 URL 中使用。

### 13. B
邮件交换记录以 `MX` 记录标识。名称服务器记录以 `ns` 标记。企业可能拥有一个或多个缓存名称服务器，但缓存名称服务器不属于该域，因为它没有任何与域相关的标识。

### 14. C
DNS 查询可以根据主机名或 IP 地址相互查找。你可以使用暴力强行技术尝试识别主机名，但该方法可能无法得到全部结果。递归请求通常由缓存服务器向权威服务器发起，以获取完整响应。完整区域内容的术语是区域传输（zone transfer）。

### 15. A
隧道攻击可以用于在一个协议内隐藏另一个协议。这可能用于通过隧道系统发送操作系统命令。DNS 放大攻击是指一次小的 DNS 请求导致 mucho 更大的响应发送到目标。DNS 递归用于从 DNS 服务器查找信息。XML 实体注入是基于 Web 的攻击，不会出现在 DNS 请求中。

### 16. D
进行 ping 掃描可能有多种原因。你可能想识别网络段中可响应的主机。但你可能不想使用完整的端口扫描。ICMP 是轻量级协议，且有可能通过防火墙，因为它用于故障排除和诊断。

### 17. C
NIST 网络安全框架规定了五个功能：识别、保护、检测、响应、恢复。

### 18. B
Python 解释器的执行速度可能低于编译程序，但差异微乎其微，通常在恶意软件中执行速度不是主要考量。Python 并不难学习，且有大量社区库。一个挑战是你可能需要 Python 解释器，除非你使用 Python 编译器将脚本编译。

### 19. B
表达式 `host 192.168.10.5` 在 BPF 中表示 `tcpdump` 只捕获到或来自 192.168.10.5 的数据包。如果你只想捕获到或自该 IP 的流量，需要将 `host` 替换为 `src` 或 `dest`。

### 20. C
证书可以撤销，但这并不是 Diffie‑Hellman 的用途。密钥管理是一个更广泛的主题，而 Diffie‑Hellman 仅用于密钥交换。它允许通信双方在拥有相同的基值的前提下共同派生相同的密钥。

### 21. D
虽然你可能在模仿他人，但模仿并不是社会工程学的原则。也不存在社会证明或稀缺性。如果你是帮助台的电话，你可能被视为拥有权威地位。

### 22. D
SNMPv3 实现了用户名和密码认证。在版本 1 中，使用明文的 `community` 字符串。SNMP 不使用哈希，虽然常把 `public` 当作 `community` 字符串，但这并不是 SNMPv1 的认证方式。

### 23. A
跨系统的进程间通信称为远程方法调用（RMI）。程序需要与之通信以获取动态端口分配的进程是 `RMI 注册表`。你查询该注册表以识别已在实现 RMI 的系统上可用的服务。

### 24. C
当没有对应的 ARP 请求时发送 ARP 响应，属于意外或不必要的消息，即 `gratuitous ARP`。

### 25. D
文件元数据常用三个日期时间戳。创建时记录创建瞬间，访问时记录访问瞬间，修改时记录修改瞬间。访问时间不等同于修改时间，因为访问可能是只读的。即使你打开文件但未实际修改，访问时间仍会更新。搬动、添加或更改文件有时称为 MAC（修改、访问、创建），但这些并非与文件时间相关的任务。

### 26. C
本地漏洞针对的不是网络上监听的应用。这意味着你必须是本地登录的机器用户，而非远程。换句话说，你需要以某种方式登录系统。本地漏洞不需要用于收集密码，因为不需要利用漏洞即可完成此类操作。同样，操纵日志或横向移动也不需要利用漏洞，通常需要提升权限。本地漏洞可以被利用以获取提升权限的优势。

### 27. A
完整性是 CIA 三要素之一，但它并不是将已签名消息与签名证书的主体关联的原则。不可验证性是无意义的，权威性在此不相关。相反，不可否认性（nonrepudiation）意味着签名者不能否认自己发送了该消息，前提是其密钥在其持有且受密码保护。

### 28. D
生物特征和徽章访问属于物理访问控制。电话验证可能用于验证身份，但不能防止尾随。而 `人阱（man trap）` 能防止尾随，因为它一次只允许一个人进入。
