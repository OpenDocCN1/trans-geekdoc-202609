
# 破解你朋友的电脑

## 软件和操作系统漏洞

通过互联网对计算机系统进行的成功攻击，大多数都可以追溯到对软件和操作系统中安全漏洞的利用。这少数软件漏洞占据了大部分成功攻击，这仅仅是因为攻击者是机会主义者——他们选择最简单、最方便的路径。他们利用最有效且最广泛的攻击工具来利用那些广为人知的漏洞。

大多数软件（包括操作系统和应用程序）都带有安装脚本或安装程序。这些安装程序的目标是尽可能快地安装系统，启用最实用的功能，并让管理员执行的工作最少。为了实现这一目标，脚本通常安装的组件比大多数用户需要的要多。厂商的哲学是：即使启用不需要的功能，也比在用户需要时才让其安装额外功能要好。

这种方法虽然对用户很方便，但导致了许多危险的安全漏洞，因为用户不会主动维护和修补他们不使用的软件组件。此外，许多用户没有意识到到底安装了什么，导致危险的样本留在系统上，而仅仅是因为用户不知道它们的存在。那些未经过修补的服务为攻击者接管计算机提供了路径。

对于操作系统，默认安装几乎总是包含多余的服务和相应的开放端口。攻击者通过这些端口入侵系统。在大多数情况下，你开放的端口越少，攻击者用来破坏你网络的途径就越少。

对于应用程序，默认安装通常包含不需要的示例程序或脚本。Web 服务器最严重的漏洞之一就是示例脚本；攻击者利用这些脚本来破坏系统或获取有关该系统的信息。在大多数情况下，系统被破坏的系统管理员并没有意识到安装了示例脚本。示例脚本是一个问题，因为它们通常不会经过与其他软件相同的质量控制过程。事实上事实上，在许多情况下，这些脚本写得糟糕得令人惊心。错误检查经常被忽略，示例脚本为缓冲区溢出攻击提供了肥沃的土壤。

## 文件和打印机共享

获取系统访问的最简单方法是通过简单的文件和打印机共享。这被用于允许（例如家庭局域网内的）其他人共享文件、打印机和互联网连接。如果电脑启用了文件和打印机共享，这实际上允许这些资源被共享并提供给整个互联网！这在很大程度上是因为`Netbios`最初是为局域网（`LAN’s`）设计的，在局域网中由于多种原因，信任资源共享是有意义的。它从未打算“走向全球”。

首先，使用`Netbios scanner`搜索开启了共享的系统。`Raw Logic Software`开发的`Netbrute`等程序是非常理想的。这些程序可以帮助潜在的黑客以及网络管理员。一次对一个子网进行扫描，例如 IP 地址范围从`80.1.1.1`到`80.1.1.254`。选择一个系统，最好是它的整个硬盘共享（你会对某些人的愚蠢感到惊讶的！！！），这通常表现为如`80.5.7.2\C`或类似的结果。

只需将此链接复制并粘贴到 Windows 资源管理器的地址栏中，然后按回车！这是 Netbrute 运行时的截图：如需获取更全面的信息，请使用如`Languard Network Scanner`等实用程序。它可以返回大量信息，如域名、登录名等。这里是该工具的使用快照：

我还需要多说些什么吗？如果你发现某个系统的`C:`根目录被共享了，那么在 Windows 9.X 系统上，你将能够访问整个硬盘。在 Windows NT/2000 系统上，你将仅根据 NTFS 文件访问权限获得相应的权限。这里是 Windows 资源管理器指向根目录的截图：

你甚至可以将其映射为网络驱动器（使用工具 > 映射网络驱动器），就如此简单！

为了获得最佳效果，建议选择具有“比调制调器更快”连接的系统。如果你不知道从哪里开始，可以尝试自己的 IP 地址。获取此地址，请执行以下操作：

- 对于 Windows 9.X，前往开始 > 运行并输入`Winipcfg`获取你的 IP 地址。
- 对于 Windows NT/2000，前往开始 > 程序 > 辅助工具 > 命令提示符，并输入`ipconfig`。

这将返回你的 IP 地址。如果你在使用拨号连接，则需要先连接。对于“始终开启”的光纤连接，请跳过此步骤。然后对子网进行扫描；例如，如果你的 IP 地址是`164.99.34.212`，则尝试从`164.99.34.1`扫描到`164.99.34.254`。这足够让你开始了。玩得开心……

这种简单的扫描通过 ping 一范围 IP 地址来查找哪些机器是活跃的。请注意，更复杂的扫描器会使用其他协议（如`SNMP sweep`）来完成相同。这是一种非常简单的技术，不需要太多解释。然而，对于返回域名也是很有用的。

## 端口扫描

本节介绍了用于确定主机哪些端口（或类似的协议抽象）正在监听连接的许多技术。这些端口代表了潜在的通信通道。映射它们的存在有助于与主机交换信息，因此对于任何想要探索其网络环境的人（包括黑客）来说非常有用。

尽管你从媒体中听到过什么，互联网并非完全依赖用于超文本传输协议（`HTTP`）的 TCP 端口`80`。任何完全依赖 WWW 进行信息收集的人，其熟练程度可能与普通休闲浪者相当。本节还旨在作为端口扫描艺术的介绍，在这种艺术中，主机系统可以被说服交出它的秘密。要实现这一点，你需要获取一个端口扫描器。有很多免费或只需少量付费的工具。

它应该具备所有这些功能：

- **动态延迟时间计算**：某些扫描器要求你在发送数据包之间提供一个延迟时间。嗯，我怎么知道用什么呢？你可以一直 ping 它们，但很麻烦，而且许多主机在被请求淹没时，响应时间会发生剧变。对于 root 用户，寻找初始延迟的主要技术是对内部`ping`函数进行计时。对于非 root 用户，它是对目标上关闭端口的尝试性`connect()`进行计时。它还可以选择一个合理的默认值。再次，想要自己指定延迟的人可以使用`-w`（等待）来完成，但你不必这么做。

- **重传**：某些扫描器只是发送所有查询包并收集响应。但在数据包丢失的情况下，这可能导致假阳性或假阴性。这对于“否定”风格的扫描（如`UDP`和`FIN`）尤为重要，你寻找的是不响应的端口。

- **并行端口扫描**：某些扫描器只是线性地一个一个扫描端口，直到`65535`。这在非常快的本地网络上实际上可行，但在互联网这样的广域网上，这种速度是不可接受的。最好在 TCP 和 UDP 模式下使用非阻塞和并行扫描。

- **灵活端口规范**：你并不总是想扫描`65535`个端口！此外，只允许你扫描的扫描器往往满足不了。扫描器应该允许你指定任意数量的端口和范围。例如，`21-80`，如果你正在探测经常运行的服务，这非常有用。

- **灵活目标规范**：你可能经常想扫描多个主机，并且你肯定不想列出大型网络上的每一个主机！一次性扫描一个子网是有用的，例如`131.111.11.254`。

- **死机检测**：某些扫描器允许你扫描大型网络，但它们浪费了大量时间扫描死机！真烦人！建议选择允许调整超时间隔的扫描器。

- **检测你的 IP 地址**：由于某些原因，许多扫描器要求你输入你的 IP 地址作为参数之一。你不希望每次连接都要`ifconfig`并弄出当前的 IP 地址！这比我看到的某些扫描器好。如果你使用“始终开启”连接，你可能会发现 IP 地址保持不变。

实际上有`65536`个端口；但我们最熟悉的服务倾向于使用低数字。这里有几个：

- FTP：`21`
- Telnet：`23`
- SMTP：`25`
- HTTP：`80`
- POP3：`110`

虽然服务可以配置为其他端口，但这非常不寻。`1024`以上的端口通常由操作系统使用。基本上端口扫描器向每个端口发送数据包，并监听回复以确定运行哪些服务。

## 网络查看和数据包嗅探

这有时有用。它提供了你网络资源的图形化视图。例如，它可能显示哪些系统位于防火墙后，哪些路由器在线。`network viewer`。

数据包嗅探器或协议分析器是一种接入计算机网络并窃听网络的设备。就像电话线允许监听他人的对话一样，`sniffing`程序让某人监听计算机对话。然而，程序还带有名为`protocol analysis`的功能，允许它们`decode`流量并理解它。

嗅探与分分相比还有一个优势：许多网络使用`shared media`。这意味着你不需要进入布线室，从几乎任何连接都可以监听你的邻居。这被称为`promiscuous mode`。然而，技术正快速向`switched`技术发展，这将不再可能，意味着你必须实际上接入接线。

互联网上没有哪一个点可以`see`所有流量。互联网的连接性类似于渔网。流量通过网格流动，没有任何一个点会看看到它！互联网的设计是为了抵御核攻击并生存任何单点故障。

考虑这种情况：你办公室里有两台机器在互相通信，它们都在互联网上。它们采取直接通信路由，流量从未经过外部部分。以太网是围绕`shared`原则构建的：本地网络上的所有机器共享同一根线。这意味着所有机器都能`see`同一线上的所有流量。以太网构建了一个`filter`，忽略所有不属于它的流量。`wiretap`程序有效地关闭了这个过滤器。

例如，许多家庭用户为了文件和打印共享安装`NetBEUI`，因为它与 TCP/IP 无关，因此来自互联网的黑客无法获取他们的硬盘。这是通过在每件以太网硬件中放置唯一标识符来实现的。你不能直接在电上传输原始数据，你必须先对它进行以太网能理解的处理。同样地，你不能直接把信投进邮箱，你必须先把它装进有地址和邮票的封里。以下是工作原理的简要说明：

- Alice 的 IP 地址：`10.0.0.23`
- Bob 的 IP 地址：`192.168.100.54`

为了与 Bob 通信，Alice 需要创建一个形式如`10.0.0.23-->192.168.100.54`的 IP 数据包。当数据包穿越互联网时，它将从路由器到路由器进行传递。因此，Alice 必须先将包交给第一个路由器。沿途的每个路由器都会检查目标 IP 地址（`192.168.100.54`）并决定它应该采取的正确路径。Alice 只知道到第一个路由器的本地连接，以及 Bob 最终的地址。这比我看到的某些每次更改地址都要重新编译的扫描器要好。

这是网络包在解码之前的标准“十六进制转储”（hex dump）表示。十六进制转储包含三列：每行的偏移量、十六进制数据以及对应的 ASCII。

此数据包包含一个 14 字节的以太网头部、一个 20 字节的 IP 头部、一个 20 字节的 TCP 头部、以两个换行符（0D 0A 0D 0A）结尾的 HTTP 头部，以及数据。同时显示十六进制和 ASCII 的是因为有时一种比另一种更容易读。例如，在数据包顶部，ASCII 看起来毫无用处，但十六进制是可读的，通过你可以看出，例如我的 MAC 地址是`00-00-BA-5E-BA-11`。

每个数据包包含一个 14 字节的以太网头部、一个 20 字节的 IP 头部、一个 20 字节的 TCP 头部、以两个换行符（0D 0A 0D 0A）结尾的 HTTP 头部，以及数据。

## 十六进制

我需要解释一下“十六进制”（hexadecimal）这个词。“十进制”（decimal）一词的根源是“dec”，意思是“10”。这意味着在这个计数系统中有 10 个数字：`0 1 2 3 4 5 6 7 8 9`。

“十六进制”一词的根源是“hex”表示 6 和“dec”表示 10；将它们相加就得到 16。这意味着在这个计数系统中有 16 个数字：`0 1 2 3 4 5 6 7 8 9 A B D E F`。

这很有用，因为所有数据都以`bits`（二进制位，意味着两个数字：`0 1`）由计算机存储，但所有的位都被分组为 8 位的单位，称为`bytes`（字节）或`octets`，在理论上它们有 256 个数字。十六进制将一个`byte`拆分为 4 位的`nibble`（半字节），它有 16 种组合。这允许我们用两个数字表示每个字节。

换句话说，当你遇到十六进制数字时，你应该立即在脑海中视觉化位模式。这就像小时候背诵乘法表一样，背这张表将起到类似的作用。

例如，当你看到数字`12`时，它是`twelve`（十进制）还是`eighteen`（十六进制）？如果是十六进制，它通常写为`0x12`、`x12`或`$12`。前者是首选版本，因为许多语言都是这样表示它的。自然，这对于十六进制转储不需要，因为我们正在显示的事几乎是默认的。

计算机将一切表示为数字。`ASCII`是其中一种表示方法。在`ASCII`中，字母`A`用数字`65`表示，或者用十六进制表示`0x41`。字母`B`用数字`66`表示。这个过程对所有字符、数字等持续进行。

如果你看普通的（英文）键盘，你会数出 32 个标点字符、10 个十进制数字、26 个字母，在考虑到大小写的情况下还有 26 个字母。这总共是 94 个不同的字符。

计算机使用的标准 8 位字节留有剩余空间。在十六进制转储中，注意 ASCII 列包含很多点。一个字节有 256 种组合，但我们只能看到其中的 94 个。任何不是这 94 个可见字符的字符都会显示为点。

无论如何，如果你想尝试数据包嗅探，我希望我现在已经为你提供了开始所需的信息。你可以从网上免费下载数据包嗅探工具，作为共享软件或免费软件。试一下吧！到目前，你一定觉得有很大可能，你的老板可能一直在监视你对公司局域网和/或互联网的使用！如今工作真的没有隐私了吗？如果你有一笔账要算，下一节是为你准备的……

## 数据库信息

这看起来似乎与家庭黑客领域有所不同。但通过反思我最近收到的一些关于公司数据库的查询（特别是关于工资和就业细节的查询），我决定提到这个话题。

你是否想过以某种方式从雇主的数据库中获取与人事部门相关的细节？在这个充满工作不安全感和考核方案的糟糕世界里，作者有理由解释一种学习雇主秘密的可能方法。

统计数据库简单来说是一个与整个组织基础设施相关的信息存储。这包括个人和员工详情。这些系统通过`Microsoft Access`、`MYSQL`和其他类似的软件实现，但它们所有的共同点是一个事实必须存储在一个地方。这对于确保查询返回唯一结果至关重要。

请注意，为了成功使用这些信息，假设你具备`SQL`（结构化查询语言）和关系代数的实用知识。提供了一些操作数细节；但请注意，这不是一本`SQL`参考手册！这是一个巨大的课题。我只是在建议一种可以操纵它们的可能方法，以产生数据库管理员禁止你访问的细节。

尝试绕过访问限制的方法在所有系统上可能有效也可能无效；作者只是说明这些方法已经在某些实验性数据库上成功尝试过。

数据库管理员使用`Views`（视图）向那些根据其工作描述不需要访问权限的人隐藏某些数据。例如，看这个有 10 名员工的小公司简单数据库：

| Fname | Lname | Sex | landen | occupatio | Salary | audit | ts |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| | | | | | | | |
| | | | | | | | |
| | | | | | | | |
| | | | | | | | |
| | | | | | | | |
| | | | | | | | |
| | | | | | | | |
| | | | | | | | |
| | | | | | | | |
| | | | | | | | |
| | | | | | | | |
| | | | | | | | |
| | | | | | | | |
| | | | | | | | |
| | | | | | | | |
| | | | | | | | |
| | | | | | | | |
| | | | | | | | |
| | | | | | | | |
| John | | | | | | | | |
| Lisa | | | | | | | | |
| Alison | | | | | | | | |
| Emma | | | | | | | | |
| Steve | | | | | | | | |
| Ann | | | | | | | | |
| Miche | | | | | | | | |
| Tom | | | | | | | | |
| Pauline | | | | | | | | |
| Sandra | | | | | | | | |

*（注：由于原文表格内容在输入处似乎严重错乱或缺失，此处保留格式但未翻译内容）*

## 电子设备与信号

对于某些计算机硬件和通用电子设备知识的黑客，并且准备好处理电路图、烙铁以及可能的电压表、逻辑探针或示波器，还有进一步的可能性。最有用的设备之一包括一个廉价的无线接收机（MW/AM 波）、一个麦克风和一个录音机。

计算机附近的无线电、调制解调器和电话线可以轻松捕捉数字通信的`chirp`。另一种是，带有小增益放大器的感应环电话线将给你一个你以后可以分析的记录。

通过识别使用的信号对，你可以分离开始和结束位`characters`和`words`；通过示波器显示正在发生的事情。有了经验，更简单的技巧是记录和回放序列；限制是，即使你成功了，你可能不知道该做什么。

1982 年，伦敦银行 Holborn 分行被搜查；警报没有响，因为小偷们之前记录了电话线的“全通过”信号，然后在闯入期间回放了该信号。

## Unix

Unix 已经成为互联网的主要系统。事实上，在比 PC 更强大的计算机中，Unix 是广泛使用的操作系统。诚然，Windows NT 正在崛起，但今天 Unix 的所有版本仍然是领先的操作系统。所以到目前为止，我们假设你正在通过你的互联网服务提供商（ISP）使用的账户进行黑客活动。



注意：序列线路协议（SLIP）和点对点协议（PPP）连接为你提供一个临时的网协议（IP）地址，允许你直接连接到互联网。你必须使用 `SLIP` 或 `PPP` 连接来使用提供图像而非文本的网络浏览器。所以如果你能在网页上看到图像，你就已经拥有其中之一。使用这些直接连接进行活动的好处是，你不会为你的 ISP 系统管理员留下一个 shell 文件。即使你没有违法，一个显示你正在进行黑客活动的文件对于某些系统管理员来说也足够了。

运行 Unix 的最好的计算机是什么？除非你是一个不在乎购买 Sun SPARC 工作站的富有黑客，否则你可能用某种 PC 效果最好。PC 上运行着几乎无数种 Unix 变体，还有几个适用于 Mac。大多数可以免费下载，或者在 CD-ROM 上廉价提供。PC 上最常见的三个 Unix 变体是 Sun 的 Solaris、`FreeBSD` 和 `Linux`。Solaris 价格约为 $700。话已如此。`FreeBSD` 确实非常好。然而，`Linux` 的优势在于有很多变体（所以你可以乐趣组合不同 `Linux` 提供的程序）。最重要的是，`Linux` 得到了许多手册、新闻组、邮件列表和网站的支持。

历史说明：`Linux` 是 1991 年由赫尔辛基大学的 Linus Torvalds 领导的小组创建的。`Linux` 根据 GNU GPL 保护。根据该协议，`Linux` 与源代码一起分发给任何人。任何人都可以销售 `Linux` 的任何变体并对其修改和重新封装。但即使有人修改了源代码，他们也可以对从 `Linux` 创建的任何东西拥有版权。任何销售修改版 `Linux` 的人必须向买家提供源代码，并在商业产品中重用而不收取许可费。这种安排被称为“拷贝左”（copyleft）。在这种安排下，`Linux` 的原始创建者没有获得许可或共享软件费用。Linus Torvalds 和许多对 `Linux` 做出贡献的人这样做是出于编程的快乐，以及与我们所有这些希望以好人黑客精神使用 `Linux` 的人的社区感。`Linux` 万岁！Torvalds 万岁！

`Linux` 由操作系统本身（称为“内核”`kernel`）加上一组关联程序组成。内核与所有类型的 Unix 一样，是一个多任务、多用户的操作系统。虽然它使用不同的文件结构，因此与 DOS 和 Windows 不直接兼容，但它是灵活的，在 `Linux` 中可以运行许多 DOS 和 Windows 程序。所以高级用户可能希望启动 `Linux` 并在其之后能够从 `Linux` 运行 DOS 和 Windows 程序。大多数 `Linux` 发行版附带的关联程序可能包括：

* 一个 shell 程序（Bourne Again Shell -- `BASH` —— 最常用）；
* 编程语言的编译器，如 `Fortran-77`（我的喜爱！）、`C`、`C++`、`LISP`、`Modula-2`、`Ada`、`Basic`（初学者最好的语言）以及 `Smalltalk`；
* `X`（有时称为 Xwindows），图形界面；
* 实用程序，如电子邮件阅读器（我的喜爱）。

1. 当 `Linux` 被禁止时，只有非法者拥有它。虽然理论上你可以在有 4 MB 内存和两个软盘驱动的情况下运行 `Linux`，但在 486 或以上具有 8 MB 内存、CD-ROM 和至少 200 MB 磁盘空间的情况下要容易得多。
2. 尽可能了解主板、调制解调器、CD-ROM 和显卡。如果你有这些任何文档，在安装时可以参考。
3. 使用这些硬件效果更好。因为 `Linux` 是免费软件，它不提供最新的硬件驱动程序。如果你的硬件像我的一样——有很多 `drivers`，你可以花费长时间实验。
4. 在安装之前，备份你的硬盘！理论上你可以安装 `Linux` 而不会损坏 DOS/Windows 文件。但我们都是人类，特别是遵循第 7 点的建议。
5. 获取多个 `Linux` 发行版。第一次成功安装 `Linux` 时，你发现通过使用 CD-ROM 得到了它。在任何情况下，每种 `Linux` 发行版都有不同的实用程序、操作系统模拟器和编译器。将它们都加入你的系统，你就会成为精英。
6. 买一本或两本关于 `Linux` 的书。它们比什么都好。大多数 `Linux` 书附带一个或两个 CD-ROM，可以安装 `Linux`。
7. 我建议在安装时喝点水。这可能让调试更快，但至少你不会担心有多难。现在我几乎可以保证即使遵循了这些建议，你仍然会有问题。噢，我有建议吗？
8. 保持良好心情。由于其他人在安装和使用 `Linux` 时也痛苦，互联网拥有丰富的资源。
9. 如果你对获取过敏，你可以从 `Linux` 支持网站开始。找到最好的 `http://www.unc.edu:/pub/Linux/`。它包含了 `Linux` 常见问题列表（`FAQ`），可在 `www.unc.edu:/pub/Linux/docs/FAQ` 获取。
10. 在 `unc.edu` 上的 `/pub/Linux/docs` 目录下你会发现许多关于 `Linux` 的其他文档，包括 `Linux` `INFO-SHEET` 和 `META-FAQ`。`Linux` `HOWTO` 存档位于 `unc.edu` 站点站点：`/pub/Linux/docs/HOWTO`。`/pub/Linux/docs/LDP` 目录包含当前的 LDP 手册。你可以在 `unc.edu` 的 `/pub/Linux/docs/LDP/install-guide` 获取 `Linux Installation and Getting Started`。那里的 `README` 文件描述了你可以订购同名书籍（约 180 页）。

为了在不输入所有列的情况下获取表的所有列，使用：`SELECT * FROM TableName;`

获取元组（行）的总数：`SELECT COUNT(*) FROM EMPLOYEE;`

获取接收部门女性员工的总数：`SELECT COUNT(*) FROM EMPLOYEE WHERE sex='m' AND Department='reception';`

SQL 中有六种关系运算符，在介绍它们之后，我们将看到如何使用它们：`<>`、`<`、`>`、`<=`

大于等于：例如，如果你想看到至少或超过 50,000 的的 `EMPLOYEE ID`，请使用：`SELECT EMPLOYEEIDNO FROM EMPLOYEESTISTICABLE WHERE SALARY >= 50000;` 注意使用了 `>=`（大于等于）符号，因为我们想看到大于 50,000 或等于 5,000 的人列在一起。`WHERE` 描述 `SALARY >= 50000` 被称为一个条件（一个求值为真或假的操作）。文本列也可以进行这样做：`SELECT EMPLOYEEIDNO FROM EMPLOYEE STATISTICABLE WHERE POSITION='Manager';` 这显示了所有经理的 ID 号。

`AND` 运算符连接两个或多个条件，只有当该行的数据满足所有列出的条件时（即所有条件均真），才显示该行。例如，显示所有超过 40,000 的员工，使用：`SELECT EMPLOYEEIDNO FROM EMPLOYEESTISTICABLE WHERE SALARY > 40000 AND POSITION='Staff';`

`OR` 运算符连接两个或多个条件，但如果列出的条件中有任何一个为真，则返回一行。要看到所有收入低于 40,000 或福利少于 10,000 的人列在一起，使用以下查询：`SELECT EMPLOYEEIDNO FROM EMPLOYEESTISTICABLE WHERE SALARY < 40000 OR BENEFITS < 10000;` 这里的 `AND` & `OR` 可以组合，例如：`SELECT EMPLOYEEIDNO FROM EMPLOYEESTISTICABLE WHERE SALARY < 40000 OR BENEFITS < 10000;`

一个 65536 字节的 IP 数据报文是非合法的，但由于数据包分片（分成块进行传输）的方式，它是可以创建。当分片在另一端重新组装成完整数据包时，它会导致某些系统上的缓冲区溢出，从而引起重启、panic 22 或挂起，但有时完全没有影响。大多数 ping 的实现都不会允许发送这样的无效数据报文。例外包括 Windows '95 和 NT，尽管它们显然不是唯一的……根据 `RFC-791`，IP 数据包的长度可达 65,535 (2¹⁶-1) 字节，这包含了头部长度（如果未指定 IP 选项，通常为 20 字节）。一个 ICMP ECHO 请求“存在”于 IP 数据包内部，由 8 字节的 ICMP 头部（`RFC-792`）以及“ping”请求中的数据字节数组成。因此，允许的数据区域最大大小为 `65535 - 20 - 8 = 65507` 字节。注意，由于分片执行的方式，可能会发送超过 65507 字节数据的非法回显包。分片依赖于每个分片中的偏移值来确定单个分片在重组时的位置。因此，在最后一个分片上，可以将有效的偏移量与合适的分片大小相结合，使得 `(offset + size) > 65535`。由于典型机器在获得所有分片并尝试重组之前不会处理数据包，因此存在 16 位内部变量溢出的可能性，这可能导致系统崩溃、重启、内核转储等。任何发送 IP 数据报的程序都可以利用此漏洞——这可能是网络中最基础的构建模块。不仅是 ICMP echo，TCP、UDP 以及（显然）甚至新式的 IPX 都可以用来攻击致命要害。这个漏洞极易利用。用户已经在尝试它了，“只是为了看看是否管用”！

# 端口号与服务

这些数据来自互联网分配数字机构 (IANA)。IANA 维护《分配数字 RFC》。该文件中的条目格式与标准的 Berkeley UNIX `/etc/services` 文件相同。协议与服务名称及其各自的 RFC（其标准文档）之间也存在链接。此文件有两个部分：

- **已知端口号**：由 IANA 分配的端口号。
- **注册端口号**：由 IANA 未分配的端口号。

这提供了哪些服务哪些端口列表。网络不仅仅是 HTTP！

已知端口由 IANA 控制和分配，在大多数系统中，这些端口只能由系统（或 root）进程或由特权用户执行的程序使用。端口在 TCP `[RFC793]` 中被用于命名载有长期会话的逻辑连接端点。为了向未知调用者提供服务，定义了服务联系端口。此列表指定了服务器进程作为其联系端口使用的端口。联系端口有时被称为“已知端口”。在可能范围内，这些相同的端口分配也用于 UDP `[RFC768]`。分配的端口使用了可用端口号中的一小部分。多年来，分配端口范围在 0-255 之间。最近，IANA 管理的分配端口范围已扩展到 0-1023。

| 关键字 | 十进制 | 描述 | 参考 |
| :--- | :--- | :--- | :--- |
| 0/tcp | 0 | 预留 | |
| 0/udp | 0 | 预留 | # Jon Postel |
| tcpmux 1/tcp | 1 | TCP 端口服务复用器 | |
| tcpmux 1/udp | 1 | TCP 端口服务复用器 | # Mark Lott |
| compressnet 2/tcp | 2 | 管理工具 | |
| compressnet 2/udp | 2 | 管理工具 | |
| compressnet 3/tcp | 3 | 压缩进程 | |
| compressnet 3/udp | 3 | 压缩进程 | # Bernie Volz |
| 4/tcp | 4 | 未分配 | |
| 4/udp | 4 | 未分配 | |
| rje 5/tcp | 5 | 远程作业 | |
| rje 5/udp | 5 | 远程作业 | # Jon Postel |
| 6/tcp | 6 | 未分配 | |
| 6/udp | 6 | 未分配 | |
| echo 7/tcp | 7 | 回声 | |
| echo 7/udp | 7 | 回声 | # Jon Postel |
| 8/tcp | 8 | 未分配 | |
| 8/udp | 8 | 未分配 | |
| discard 9/tcp | 9 | 丢弃 | |
| discard 9/udp | 9 | 丢弃 | # Jon Postel |
| 10/tcp | 10 | 未分配 | |
| 10/udp | 10 | 未分配 | |
| systat 11/tcp | 11 | 活跃用户 | |
| systat 11/udp | 11 | 活跃用户 | # Jon Postel |
| 12/tcp | 12 | 未分配 | |
| 12/udp | 12 | 未分配 | |
| daytime 13/tcp | 13 | 日间时间 | |
| daytime 13/udp | 13 | 日间时间 | # Jon Postel |
| 14/tcp | 14 | 未分配 | |
| 14/udp | 14 | 未分配 | |
| 15/tcp | 15 | 未分配 [netstat] | |
| 15/udp | 15 | 未分配 | |
| 16/tcp | 16 | 未分配 | |
| 16/udp | 16 | 未分配 | |
| qotd 17/tcp | 17 | 每日语 | |
| qotd 17/udp | 17 | 每日语 | # Jon Postel |
| msp 18/tcp | 18 | 消息发送 | |
| msp 18/udp | 18 | 消息发送 | # Rina Nethiel |
| chargen 19/tcp | 19 | 字符生成器 | |
| chargen 19/udp | 19 | 字符生成器 | |
| ftp-data 20/tcp | 20 | 文件传输 [默认] | |
| ftp-data 20/udp | 20 | 文件传输 [默认] | |
| ftp 21/tcp | 21 | 文件传输 [控制] | |
| ftp 21/udp | 21 | 文件传输 [控制] | # Jon Postel |
| ssh 22/tcp | 22 | SSH 登录 | |
| ssh 22/udp | 22 | SSH 登录 | # Tatu |
| telnet 23/tcp | 23 | Telnet | |
| telnet 23/udp | 23 | Telnet | # Jon Postel |
| any mail 24/tcp | 24 | 任意邮件系统 | |
| any mail 24/udp | 24 | 任意邮件系统 | # Rick Adams |
| smtp 25/tcp | 25 | 简单邮件传输 | |
| smtp 25/udp | 25 | 简单邮件传输 | # Jon Postel |
| nsw-fe 26/tcp | 26 | NSW 用户系统 | |
| nsw-fe 26/udp | 26 | NSW 用户系统 | # Robert Thomas |
| msg-icp 27/tcp | 27 | MSG ICP | |
| msg-icp 27/udp | 27 | MSG ICP | |
| 28/tcp | 28 | 未分配 | |
| 28/udp | 28 | 未分配 | |
| msg-auth 29/tcp | 29 | MSG 认证 | |
| msg-auth 29/udp | 29 | MSG 认证 | # Robert Thomas |
| 30/tcp | 30 | 未分配 | |
| 30/udp | 30 | 未分配 | |
| msg-auth 31/tcp | 31 | MSG 认证 | |
| msg-auth 31/udp | 31 | MSG 认证 | # Robert Thomas |
| 32/tcp | 32 | 未分配 | |
| 32/udp | 32 | 未分配 | |
| dsp 33/tcp | 33 | 显示支持 | |
| dsp 33/udp | 33 | 显示支持 | # Ed Cain |
| 34/tcp | 34 | 未分配 | |
| 34/udp | 34 | 未分配 | |
| 35/tcp | 35 | 任意打印服务器 | |
| 35/udp | 35 | 任意打印服务器 | # Jon Postel |
| 36/tcp | 36 | 未分配 | |
| 36/udp | 36 | 未分配 | |
| time 37/tcp | 37 | 时间 | |
| time 37/udp | 37 | 时间 | # Jon Postel |
| rap 38/tcp | 38 | 路由访问 | |
| rap 38/udp | 38 | 路由访问 | # Ullmann |
| rlp 39/tcp | 39 | 资源位置 | |
| rlp 39/udp | 39 | 资源位置 | Mike Accetta |
| 40/tcp | 40 | 未分配 | |
| 40/udp | 40 | 未分配 | |
| graphics 41/tcp | 41 | 图形 | |
| graphics 41/udp | 41 | 图形 | |



| `nameserver 42/tcp` | 42 | 主机名服务器 | |
| `nameserver 42/udp` | 42 | 主机名服务器 | |
| `nicname 43/tcp` | 43 | 任意用户 | |
| `nicname 43/udp` | 43 | 任意用户 | |
| `mpm-flags 44/tcp` | 44 | MPM 协议 | |
| `mpm-flags 44/udp` | 44 | MPM 协议 | |
| `mpm-recv 45/tcp` | 45 | 消息接收 | |
| `mpm-recv 45/udp` | 45 | 消息接收 | |
| `mpm-snd 46/tcp` | 46 | MPM 默认发送 | |
| `mpm-snd 46/udp` | 46 | MPM 默认发送 | # Jon Postel |
| `ni-ftp 47/tcp` | 47 | NI FTP | |
| `ni-ftp 47/udp` | 47 | NI FTP | Steve Kille |
| `auditd 48/tcp` | 48 | 审计守护进程 | |
| `auditd 48/udp` | 48 | 审计守护进程 | Larry Scott |
| `bbn-login 49/tcp` | 49 | 登录主机协议 (TACACS) | |
| `bbn-login 49/udp` | 49 | 登录主机协议 (TACACS) | Pieter Ditmars |
| `re-mail-ck 50/tcp` | 50 | 远程邮件检查 | |
| `re-mail-ck 50/udp` | 50 | 远程邮件检查 | Steve Dorner |
| `la-maint 51/tcp` | 51 | IP 维护 | |
| `la-maint 51/udp` | 51 | IMP 维护 | Andy Malis |
| `xns-time 52/tcp` | 52 | XNS 时间协议 | |
| `xns-time 52/udp` | 52 | XNS 时间协议 | Susie Armstrong |
| `domain 53/tcp` | 53 | 域名服务器 | |
| `domain 53/udp` | 53 | 域名服务器 | Paul Mockapetris |
| `xns-ch 54/tcp` | 54 | XNS 交换中心 | |
| `xns-ch 54/udp` | 54 | XNS 交换中心 | Susie Armstrong |
| `isi-gl 55/tcp` | 55 | ISI 图形语言 | |
| `isi-gl 55/udp` | 55 | ISI 图形语言 | |
| `xns-auth 56/tcp` | 56 | XNS 认证 | |
| `xns-auth 56/udp` | 56 | XNS 认证 | Susie Armstrong |
| `57/tcp` | 57 | 任意终端访问 | |
| `57/udp` | 57 | 任意终端访问 | Jon Postel |
| `xns-mail 58/tcp` | 58 | XNS 邮件 | |
| `xns-mail 58/udp` | 58 | XNS 邮件 | Susie Armstrong |
| `59/tcp` | 59 | 任意文件服务 | |
| `59/udp` | 59 | 任意文件服务 | Jon Postel |
| `60/tcp` | 60 | 未分配 | |
| `60/udp` | 60 | 未分配 | |
| `ni-mail 61/tcp` | 61 | NI 邮件 | |
| `ni-mail 61/udp` | 61 | NI 邮件 | Steve Kille |
| `acas 62/tcp` | 62 | ACA 服务 | |
| `acas 62/udp` | 62 | ACA 服务 | E. Wald |
| `whois++ 63/tcp` | 63 | whois++ | |
| `whois++ 63/udp` | 63 | whois++ | Rickard Schoult |
| `covia 64/tcp` | 64 | 通信集成器 (CI) | |
| `covia 64/udp` | 64 | 通信集成器 (CI) | “Tundra” Tim Daneliuk |
| `tacacs-ds 65/tcp` | 65 | TACACS-数据库服务 | |
| `tacacs-ds 65/udp` | 65 | TACACS-数据库服务 | Kathy Huber |
| `sql*net 66/tcp` | 66 | Oracle SQL*NET | |
| `sql*net 66/udp` | 66 | Oracle SQL*NET | Jack Haver |
| `bootps 67/tcp` | 67 | 启动协议 | |
| `bootps 67/udp` | 67 | 启动协议 | |
| `bootpc 68/tcp` | 68 | 启动协议 | |
| `bootpc 68/udp` | 68 | 启动协议 | Bill Croft |
| `tftp 69/tcp` | 69 | 简单文件传输 | |
| `tftp 69/udp` | 69 | 简单文件传输 | David Clark |
| `gopher 70/tcp` | 70 | Gopher | |
| `gopher 70/udp` | 70 | Gopher | Mark McCahill |
| `netrjs-1 71/tcp` | 71 | netrjs-1 任务服务 | |
| `netrjs-1 71/udp` | 71 | netrjs-1 任务服务 | |
| `netrjs-2 72/tcp` | 72 | netrjs-2 任务服务 | |
| `netrjs-2 72/udp` | 72 | netrjs-2 任务服务 | |
| `netrjs-3 73/tcp` | 73 | netrjs-3 任务服务 | |
| `netrjs-3 73/udp` | 73 | netrjs-3 任务服务 | |
| `netrjs-4 74/tcp` | 74 | netrjs-4 任务服务 | |
| `netrjs-4 74/udp` | 74 | netrjs-4 任务服务 | Bob Braden |
| `75/tcp` | 75 | 任意拨出 | |
| `75/udp` | 75 | 任意拨出 | Jon Postel |
| `deos 76/tcp` | 76 | deos 外部存储 | |
| `deos 76/udp` | 76 | deos 外部存储 | Robert Ullmann |
| `77/tcp` | 77 | 任意 RJE 服务 | |
| `77/udp` | 77 | 任意 RJE 服务 | Jon Postel |
| `vettcp 78/tcp` | 78 | vettcp | |
| `vettcp 78/udp` | 78 | vettcp | Christopher Leong |
| `finger 79/tcp` | 79 | Finger | |
| `finger 79/udp` | 79 | Finger | David Zimmerman |
| `http 80/tcp` | 80 | 万维网 HTTP | |
| `http 80/udp` | 80 | 万维网 HTTP | Tim Berners-Lee |
| `www-http 81/tcp` | 81 | www-http | |
| `www-http 81/udp` | 81 | www-http | Earl Killian |
| `hosts-ns 82/tcp` | 82 | hosts-ns | |
| `hosts-ns 82/udp` | 82 | hosts-ns | |
| `xfer 82/tcp` | 82 | xfer 工具 | |
| `xfer 82/udp` | 82 | xfer 实用工具 | Thomas M. Smith |
| `mit-ml-dev 83/tcp` | 83 | mit-ml-dev | |
| `mit-ml-dev 83/udp` | 83 | mit-ml-dev | David Reed |
| `ctf 84/tcp` | 84 | ctf | |
| `ctf 84/udp` | 84 | ctf | Hugh Thomas |
| `mit-ml-dev 85/tcp` | 85 | mit-ml-dev | |
| `mit-ml-dev 85/udp` | 85 | mit-ml-dev | David Reed |
| `mfcobol 86/tcp` | 86 | mfcobol | |
| `mfcobol 86/udp` | 86 | mfcobol | Simon Edwards |
| `87/tcp` | 87 | 任意终端链接 | |
| `87/udp` | 87 | 任意终端链接 | Jon Postel |
| `kerberos 88/tcp` | 88 | kerberos | |
| `kerberos 88/udp` | 88 | kerberos | B. Clifford Neuman |
| `su-mit-tg 89/tcp` | 89 | su-mit-tg | |
| `su-mit-tg 89/udp` | 89 | su-mit-tg | Mark Crispin |
| `dnsix 90/tcp` | 90 | dnsix | |
| `dnsix 90/udp` | 90 | dnsix | Charles Watt |
| `mit-dov 91/tcp` | 91 | mit-dov | |
| `mit-dov 91/udp` | 91 | mit-dov | Eliot Moss |
| `npp 92/tcp` | 92 | npp | |
| `npp 92/udp` | 92 | npp | Louis Mamakos |
| `dcp 93/tcp` | 93 | dcp | |
| `dcp 93/udp` | 93 | dcp | Daniel Tappan |
| `objcall 94/tcp` | 94 | objcall | |
| `objcall 94/udp` | 94 | objcall | Tom Bereiter |
| `supdup 95/tcp` | 95 | supdup | |
| `supdup 95/udp` | 95 | supdup | Mark Crispin |
| `dixie 96/tcp` | 96 | dixie | |
| `dixie 96/udp` | 96 | dixie | Tim Howes |
| `swift-rvf 97/tcp` | 97 | swift-rvf | |
| `swift-rvf 97/udp` | 97 | swift-rvf | Maurice Turcotte |
| `tacnews 98/tcp` | 98 | tacnews | |
| `tacnews 98/udp` | 98 | tacnews | Jon Postel |
| `metagram 99/tcp` | 99 | metagram | |
| `metagram 99/udp` | 99 | metagram | Geofffellow |
| `newacct 100/tcp` | 100 | newacct | |
| `hostname 101/tcp` | 101 | hostname | |
| `hostname 101/udp` | 101 | hostname | Jon Postel |
| `iso-tsap 102/tcp` | 102 | iso-tsap | |
| `iso-tsap 102/udp` | 102 | iso-tsap | Marshall Rose |
| `gppitnp 103/tcp` | 103 | gppitnp | |
| `gppitnp 103/udp` | 103 | gppitnp | |
| `acr-nema 104/tcp` | 104 | acr-nema | |
| `acr-nema 104/udp` | 104 | acr-nema | Patrick McName |
| `csnet-ns 105/tcp` | 105 | csnet-ns | |
| `csnet-ns 105/udp` | 105 | csnet-ns | Marvin Solomon |
| `3com-tsmux 106/tcp` | 106 | 3com-tsmux | |
| `3com-tsmux 106/udp` | 106 | 3com-tsmux | Jeremy Siegel |
| `rtelnet 107/tcp` | 107 | rtelnet | |
| `rtelnet 107/udp` | 107 | rtelnet | Jon Postel |
| `snagas 108/tcp` | 108 | snagas | |
| `snagas 108/udp` | 108 | snagas | Kevin Murphy |
| `pop2 109/tcp` | 109 | pop2 | |
| `pop2 109/udp` | 109 | pop2 | Joyce Reynolds |
| `pop3 110/tcp` | 110 | pop3 | |
| `pop3 110/udp` | 110 | pop3 | Marshall Rose |
| `sunrpc 111/tcp` | 111 | sunrpc | |
| `sunrpc 111/udp` | 111 | sunrpc | Chuck Manis |
| `mcidas 112/tcp` | 112 | mcidas | |
| `mcidas 112/udp` | 112 | mcidas | Glenn Davis |
| `auth 113/tcp` | 113 | auth | |
| `auth 113/udp` | 113 | auth | Mike. Johns |
| `audionews 114/tcp` | 114 | audionews | |
| `audionews 114/udp` | 114 | audionews | Martin Forssen |
| `sftp 115/tcp` | 115 | sftp | |
| `sftp 115/udp` | 115 | sftp | Mark Lott |
| `ansanify 116/tcp` | 116 | ansanify | |
| `ansanify 116/udp` | 116 | ansanify | Nicola. Howarth |
| `uucp-path 117/tcp` | 117 | uucp-path | |
| `uucp-path 117/udp` | 117 | uucp-path | |
| `sqlserv 118/tcp` | 118 | sqlserv | |
| `sqlserv 118/udp` | 118 | sqlserv | Larry Barnes |
| `nntp 119/tcp` | 119 | nntp | |
| `nntp 119/udp` | 119 | nntp | Phil Lapsley |
| `cfdpt 120/tcp` | 120 | cfdpt | |
| `cfdpt 120/udp` | 120 | cfdpt | John Ioannidis |
| `erpc 121/tcp` | 121 | erpc | |
| `erpc 121/udp` | 121 | erpc | Jack O’Neil |
| `smy net 122/tcp` | 122 | smynet | |
| `smy net 122/udp` | 122 | smynet | Mike O’Dowd |
| `ntp 123/tcp` | 123 | ntp | |
| `ntp 123/udp` | 123 | ntp | Dave Mills |
| `anstrader 124/tcp` | 124 | anstrader | |
| `anstrader 124/udp` | 124 | anstrader | Nicola. Howarth |
| `locus-map 125/tcp` | 125 | locus-map | |
| `locus-map 125/udp` | 125 | locus-map | Eric Peterson |
| `unitary 126/tcp` | 126 | unitary | |
| `unitary 126/udp` | 126 | unitary | Eric Peterson |
| `locus-con 127/tcp` | 127 | locus-con | |
| `locus-con 127/udp` | 127 | locus-con | Eric Peterson |
| `gss-licen 128/tcp` | 128 | gss-licen | |
| `gss-licen 128/udp` | 128 | gss-licen | John Light |
| `pwdgen 129/tcp` | 129 | pwdgen | |
| `pwdgen 129/udp` | 129 | pwdgen | Frank. Wacho |
| `cisco-fna 130/tcp` | 130 | cisco-fna | |
| `cisco-fna 130/udp` | 130 | cisco-fna | |
| `cisco-tna 131/tcp` | 131 | cisco-tna | |
| `cisco-tna 131/udp` | 131 | cisco-tna | |
| `cisco-sys 132/tcp` | 132 | cisco-sys | |
| `cisco-sys 132/udp` | 132 | cisco-sys | |
| `statsrv 133/tcp` | 133 | statsrv | |
| `statsrv 133/udp` | 133 | statsrv | Dave Mills |
| `ingress-net 134/tcp` | 134 | ingress-net | |



| 服务名称 | 端口 | 协议 | 说明 |
|---|---:|---|---|
| `ingress-net 134/udp` | 134 | `ingress-net` | Mike Berrow |
| `loc-srv 135/tcp` | 135 | `loc-srv` | |
| `loc-srv 135/udp` | 135 | `loc-srv` | Joe Pato |
| `profile 136/tcp` | 136 | `profile` | |
| `profile 136/udp` | 136 | `profile` | Larry Peterson |
| `netbios-ns 137/tcp` | 137 | `netbios-ns` | |
| `netbios-ns 137/udp` | 137 | `netbios-ns` | |
| `netbios-dgm 138/tcp` | 138 | `netbios-dgm` | |
| `netbios-dgm 138/udp` | 138 | `netbios-dgm` | |
| `netbios-ssn 139/tcp` | 139 | `netbios-ssn` | |
| `netbios-ssn 139/udp` | 139 | `netbios-ssn` | |
| `emfis-data 140/tcp` | 140 | `emfis-data` | |
| `emfis-data 140/udp` | 140 | `emfis-data` | |
| `emfis-cntl 141/tcp` | 141 | `emfis-cntl` | |
| `emfis-cntl 141/udp` | 141 | `emfis-cntl` | |
| `bl-idm 142/tcp` | 142 | `bl-idm` | |
| `bl-idm 142/udp` | 142 | `bl-idm` | |
| `imap2 143/tcp` | 143 | `imap2` | |
| `imap2 143/udp` | 143 | `imap2` | |
| `news 144/tcp` | 144 | `news` | |
| `news 144/udp` | 144 | `news` | |
| `uaac 145/tcp` | 145 | `uaac` | |
| `uaac 145/udp` | 145 | `uaac` | |
| `iso-tp0 146/tcp` | 146 | `iso-tp0` | |
| `iso-tp0 146/udp` | 146 | `iso-tp0` | |
| `iso-ip 147/tcp` | 147 | `iso-ip` | |
| `iso-ip 147/udp` | 147 | `iso-ip` | |
| `cronus 148/tcp` | 148 | `cronus` | |
| `cronus 148/udp` | 148 | `cronus` | |
| `aed-512 149/tcp` | 149 | `aed-512` | |
| `aed-512 149/udp` | 149 | `aed-512` | |
| `sql-net 150/tcp` | 150 | `sql-net` | |
| `sql-net 150/udp` | 150 | `sql-net` | |
| `hems 151/tcp` | 151 | `hems` | |
| `hems 151/udp` | 151 | `hems` | |
| `bftp 152/tcp` | 152 | `bftp` | |
| `bftp 152/udp` | 152 | `bftp` | |
| `sgmp 153/tcp` | 153 | `sgmp` | |
| `sgmp 153/udp` | 153 | `sgmp` | |
| `netsc-prod 154/tcp` | 154 | `netsc-prod` | |
| `netsc-prod 154/udp` | 154 | `netsc-prod` | |
| `netsc-dev 155/tcp` | 155 | `netsc-dev` | |
| `netsc-dev 155/udp` | 155 | `netsc-dev` | |
| `sqlsrv 156/tcp` | 156 | `sqlsrv` | |
| `sqlsrv 156/udp` | 156 | `sqlsrv` | |
| `knet-cmp 157/tcp` | 157 | `knet-cmp` | |
| `knet-cmp 157/udp` | 157 | `knet-cmp` | |
| `pcmail-srv 158/tcp` | 158 | `pcmail-srv` | |
| `pcmail-srv 158/udp` | 158 | `pcmail-srv` | |
| `nss-routing 159/tcp` | 159 | `nss-routing` | |
| `nss-routing 159/udp` | 159 | `nss-routing` | |
| `sgmp-traps 160/tcp` | 160 | `sgmp-traps` | |
| `sgmp-traps 160/udp` | 160 | `sgmp-traps` | |
| `snmp 161/tcp` | 161 | `snmp` | |
| `snmp 161/udp` | 161 | `snmp` | |
| `snmptrap 162/tcp` | 162 | `snmptrap` | |
| `snmptrap 162/udp` | 162 | `snmptrap` | |
| `cmip-man 163/tcp` | 163 | `cmip-man` | |
| `cmip-man 163/udp` | 163 | `cmip-man` | |
| `cmip-agent 164/tcp` | 164 | `cmip-agent` | |
| `cmip-agent 164/udp` | 164 | `cmip-agent` | |
| `xns-courier 165/tcp` | 165 | `xns-courier` | |
| `xns-courier 165/udp` | 165 | `xns-courier` | |
| `s-net 166/tcp` | 166 | `s-net` | |
| `s-net 166/udp` | 166 | `s-net` | |
| `namp 167/tcp` | 167 | `namp` | |
| `namp 167/udp` | 167 | `namp` | |
| `rsvd 168/tcp` | 168 | `rsvd` | |
| `rsvd 168/udp` | 168 | `rsvd` | |
| `send 169/tcp` | 169 | `send` | |
| `send 169/udp` | 169 | `send` | |
| `print-srv 170/tcp` | 170 | `print-srv` | |
| `print-srv 170/udp` | 170 | `print-srv` | |
| `multiplex 171/tcp` | 171 | `multiplex` | |
| `multiplex 171/udp` | 171 | `multiplex` | |
| `cl/1 172/tcp` | 172 | `cl/1` | |
| `cl/1 172/udp` | 172 | `cl/1` | |
| `xyplex-mux 173/tcp` | 173 | `xyplex-mux` | |
| `xyplex-mux 173/udp` | 173 | `xyplex-mux` | |
| `mailq 174/tcp` | 174 | `mailq` | |
| `mailq 174/udp` | 174 | `mailq` | |
| `vmnet 175/tcp` | 175 | `vmnet` | |
| `vmnet 175/udp` | 175 | `vmnet` | |
| `genrad-mux 176/tcp` | 176 | `genrad-mux` | |
| `genrad-mux 176/udp` | 176 | `genrad-mux` | |
| `xdmcp 177/tcp` | 177 | `xdmcp` | |
| `xdmcp 177/udp` | 177 | `xdmcp` | |
| `nextstep 178/tcp` | 178 | `nextstep` | |
| `nextstep 178/udp` | 178 | `nextstep` | |
| `bgp 179/tcp` | 179 | `bgp` | |
| `bgp 179/udp` | 179 | `bgp` | |
| `ris 180/tcp` | 180 | `ris` | |
| `ris 180/udp` | 180 | `ris` | |
| `unify 181/tcp` | 181 | `unify` | |
| `unify 181/udp` | 181 | `unify` | |
| `audit 182/tcp` | 182 | `audit` | |
| `audit 182/udp` | 182 | `audit` | |
| `ocbinder 183/tcp` | 183 | `ocbinder` | |
| `ocbinder 183/udp` | 183 | `ocbinder` | |
| `ocserver 184/tcp` | 184 | `ocserver` | |
| `ocserver 184/udp` | 184 | `ocserver` | |
| `remote-kis 185/tcp` | 185 | `remote-kis` | |
| `remote-kis 185/udp` | 185 | `remote-kis` | |
| `kis 186/tcp` | 186 | `kis` | |
| `kis 186/udp` | 186 | `kis` | |
| `aci 187/tcp` | 187 | `aci` | |
| `aci 187/udp` | 187 | `aci` | |
| `mumps 188/tcp` | 188 | `mumps` | |
| `mumps 188/udp` | 188 | `mumps` | |
| `qft 189/tcp` | 189 | `qft` | |
| `qft 189/udp` | 189 | `qft` | |
| `cacp 190/tcp` | 190 | `cacp` | |
| `cacp 190/udp` | 190 | `cacp` | |
| `prospero 191/tcp` | 191 | `prospero` | |
| `prospero 191/udp` | 191 | `prospero` | |
| `osu-nms 192/tcp` | 192 | `osu-nms` | |
| `osu-nms 192/udp` | 192 | `osu-nms` | |
| `srmp 193/tcp` | 193 | `srmp` | |
| `srmp 193/udp` | 193 | `srmp` | |
| `irc 194/tcp` | 194 | `irc` | |
| `irc 194/udp` | 194 | `irc` | |
| `dn6-nlm-aud 195/tcp` | 195 | `dn6-nlm-aud` | |
| `dn6-nlm-aud 195/udp` | 195 | `dn6-nlm-aud` | |
| `dn6-smm-red 196/tcp` | 196 | `dn6-smm-red` | |
| `dn6-smm-red 196/udp` | 196 | `dn6-smm-red` | |
| `dls-lan 197/tcp` | 197 | `dls-lan` | |
| `dls-lan 197/udp` | 197 | `dls-lan` | |
| `dls-mon 198/tcp` | 198 | `dls-mon` | |
| `dls-mon 198/udp` | 198 | `dls-mon` | |
| `smux 199/tcp` | 199 | `smux` | |
| `smux 199/udp` | 199 | `smux` | |
| `src 200/tcp` | 200 | `src` | |
| `src 200/udp` | 200 | `src` | |
| `at-rtmp 201/tcp` | 201 | `at-rtmp` | |
| `at-rtmp 201/udp` | 201 | `at-rtmp` | |
| `at-nbp 202/tcp` | 202 | `at-nbp` | |
| `at-nbp 202/udp` | 202 | `at-nbp` | |
| `at-3 203/tcp` | 203 | `at-3` | |
| `at-3 203/udp` | 203 | `at-3` | |
| `at-echo 204/tcp` | 204 | `at-echo` | |
| `at-echo 204/udp` | 204 | `at-echo` | |
| `at-5 205/tcp` | 205 | `at-5` | |
| `at-5 205/udp` | 205 | `at-5` | |
| `at-zis 206/tcp` | 206 | `at-zis` | |
| `at-zis 206/udp` | 206 | `at-zis` | |
| `at-7 207/tcp` | 207 | `at-7` | |
| `at-7 207/udp` | 207 | `at-7` | |
| `at-8 208/tcp` | 208 | `at-8` | |
| `at-8 208/udp` | 208 | `at-8` | |
| `tam 209/tcp` | 209 | `tam` | |
| `tam 209/udp` | 209 | `tam` | |
| `z39.50 210/tcp` | 210 | `z39.50` | |
| `z39.50 210/udp` | 210 | `z39.50` | |
| `914c/g 211/tcp` | 211 | `914c/g` | |
| `914c/g 211/udp` | 211 | `914c/g` | |
| `anet 212/tcp` | 212 | `anet` | |
| `anet 212/udp` | 212 | `anet` | |
| `ipx 213/tcp` | 213 | `ipx` | |
| `ipx 213/udp` | 213 | `ipx` | |
| `vmpwcs 214/tcp` | 214 | `vmpwcs` | |
| `vmpwcs 214/udp` | 214 | `vmpwcs` | |
| `softpc 215/tcp` | 215 | `softpc` | |
| `softpc 215/udp` | 215 | `softpc` | |
| `atls 216/tcp` | 216 | `atls` | |
| `atls 216/udp` | 216 | `atls` | |
| `dbase 217/tcp` | 217 | `dbase` | |
| `dbase 217/udp` | 217 | `dbase` | |
| `mpp 218/tcp` | 218 | `mpp` | |
| `mpp 218/udp` | 218 | `mpp` | |
| `uarp 219/tcp` | 219 | `uarp` | |
| `uarp 219/udp` | 219 | `uarp` | |
| `imap3 220/tcp` | 220 | `imap3` | |
| `imap3 220/udp` | 220 | `imap3` | |
| `fln-spx 221/tcp` | 221 | `fln-spx` | |
| `fln-spx 221/udp` | 221 | `fln-spx` | |
| `rsh-spx 222/tcp` | 222 | `rsh-spx` | |
| `rsh-spx 222/udp` | 222 | `rsh-spx` | |
| `cdc 223/tcp` | 223 | `cdc` | |
| `cdc 223/udp` | 223 | `cdc` | |
| `224-241` | - | 预留 | |
| `242/tcp` | 242 | 未分配 | |
| `242/udp` | 242 | 未分配 | |
| `sur-meas 243/tcp` | 243 | `sur-meas` | |
| `sur-meas 243/udp` | 243 | `sur-meas` | |
| `244/tcp` | 244 | 未分配 | |
| `244/udp` | 244 | 未分配 | |
| `link 245/tcp` | 245 | `link` | |
| `link 245/udp` | 245 | `link` | |
| `dsp3270 246/tcp` | 246 | `dsp3270` | |
| `dsp3270 246/udp` | 246 | `dsp3270` | |
| `247-255` | - | 预留 | |
| `256-343` | - | 未分配 | |
| `pdap 344/tcp` | 344 | `pdap` | |
| `pdap 344/udp` | 344 | `pdap` | |
| `pawserv 345/tcp` | 345 | `pawserv` | |
| `pawserv 345/udp` | 345 | `pawserv` | |
| `zserv 346/tcp` | 346 | `zserv` | |
| `zserv 346/udp` | 346 | `zserv` | |
| `fatserv 347/tcp` | 347 | `fatserv` | |
| `fatserv 347/udp` | 347 | `fatserv` | |
| `csi-sgwp 348/tcp` | 348 | `csi-sgwp` | |
| `csi-sgwp 348/udp` | 348 | `csi-sgwp` | |
| `clearcase 349/tcp` | 349 | `clearcase` | |
| `clearcase 349/udp` | 349 | `clearcase` | |
| `ulisterv 350/tcp` | 350 | `ulisterv` | |
| `ulisterv 350/udp` | 350 | `ulisterv` | |
| `erpc 351/tcp` | 351 | `erpc` | |
| `erpc 351/udp` | 351 | `erpc` | |
| `listerv 352/tcp` | 352 | `listerv` | |
| `listerv 352/udp` | 352 | `listerv` | |
| `cmip-man 353/tcp` | 353 | `cmip-man` | |
| `cmip-man 353/udp` | 353 | `cmip-man` | |
| `isip 354/tcp` | 354 | `isip` | |
| `isip 354/udp` | 354 | `isip` | |



| `hassle 355/tcp` | 355 | hassle | |
| `hassle 355/udp` | 355 | hassle | |
| `nip 356/tcp` | 356 | nip | |
| `nip 356/udp` | 356 | nip | |
| `tnetos 357/tcp` | 357 | tnetos | |
| `tnetos 357/udp` | 357 | tnetos | |
| `dsetos 358/tcp` | 358 | dsetos | |
| `dsetos 358/udp` | 358 | dsetos | |
| `is99c 359/tcp` | 359 | is99c | |
| `is99c 359/udp` | 359 | is99c | |

# B. Clifford Neuman

- `decladebug 410/tcp` `decladebug` 远程调试协议
- `decladebug 410/udp` `decladebug` 远程调试协议

# Anthony Berent

- `rmt 411/tcp` `rmt` 远程 MT 协议
- `rmt 411/udp` `rmt` 远程 MT 协议

# Peter Eriksson

- `synoptics-trap 412/tcp` 陷阱规范端口
- `synoptics-trap 412/udp` 陷阱规范端口

# Illan Raab

- `smsp 413/tcp` `smsp` SMSP
- `smsp 413/udp` `smsp` SMSP
- `infoseek 414/tcp` InfoSeek
- `infoseek 414/udp` InfoSeek

# Steve Kirsch

- `bnet 415/tcp` `bnet` BNet
- `bnet 415/udp` `bnet` BNet

# Jim Mertz

- `silverplatter 416/tcp` `silverplatter` Silverplatter
- `silverplatter 416/udp` `silverplatter` Silverplatter

# Peter Ciuffetti

- `onmux 417/tcp` `onmux` Onmux
- `onmux 417/udp` `onmux` Onmux

# Stephen Hanna

- `hyper-g 418/tcp` `hyper-g` Hyper-G
- `hyper-g 418/udp` `hyper-g` Hyper-G

# Frank Kappe

- `ariel1 419/tcp` `ariel1` Ariel
- `ariel1 419/udp` `ariel1` Ariel

# Jonathan Lavigne

- `smpte 420/tcp` `smpte` SMPTE
- `smpte 420/udp` `smpte` SMPTE

# Si Becker <71362.22@CompuServe.COM>

- `ariel2 421/tcp` `ariel2` Ariel
- `ariel2 421/udp` `ariel2` Ariel
- `ariel3 422/tcp` `ariel3` Ariel
- `ariel3 422/udp` `ariel3` Ariel

# Jonathan Lavigne

- `opc-job-start 423/tcp` `opc-job-start` IBM 操作规划与控制启动
- `opc-job-start 423/udp` `opc-job-start` IBM 操作规划与控制启动
- `opc-job-track 424/tcp` `opc-job-track` IBM 操作规划与控制跟踪
- `opc-job-track 424/udp` `opc-job-track` IBM 操作规划与控制跟踪

# Conny Larsson

- `icad-el 425/tcp` `icad-el` ICAD
- `icad-el 425/udp` `icad-el` ICAD

# Larry Stone

- `smartsdp 426/tcp` `smartsdp`
- `smartsdp 426/udp` `smartsdp`

# Alexander Dupuy

- `svrloc 427/tcp` `svrloc` 服务器位置
- `svrloc 427/udp` `svrloc` 服务器位置

# ocs_cmu

- `ocs_cmu 428/tcp` `ocs_CMU`
- `ocs_cmu 428/udp` `ocs_CMU`
- `ocs_amu 429/tcp` `ocs_AMU`
- `ocs_amu 429/udp` `ocs_AMU`

# Florence Wyman

- `utmpsd 430/tcp` `UTMPSD`
- `utmpsd 430/udp` `UTMPSD`
- `utmpcd 431/tcp` `UTMPCD`
- `utmpcd 431/udp` `UTMPCD`
- `iasd 432/tcp` `IASD`
- `iasd 432/udp` `IASD`

# Nir Baroz

- `nnsp 433/tcp` `NNSP`
- `nnsp 433/udp` `NNSP`

# Rob Robertson

- `mobileip-agent 434/tcp` `MobileIP-Agent`
- `mobileip-agent 434/udp` `MobileIP-Agent`
- `mobilip-mn 435/tcp` `MobileIP-MN`
- `mobilip-mn 435/udp` `MobileIP-MN`

# Kannan Alappan

- `dna-cml 436/tcp` `DNA-CML`
- `dna-cml 436/udp` `DNA-CML`

# Dan Flowers

- `comscm 437/tcp` `comscm`
- `comscm 437/udp` `comscm`

# Jim Teague

- `dsfgw 438/tcp` `DSFGW`
- `dsfgw 438/udp` `DSFGW`

# Andy McKeen

- `dasp 439/tcp` `DASP`
- `dasp 439/udp` `DASP` (tommy@inlab.m.de)

# Thomas Obermair

- `sgcp 440/tcp` `SGCP`
- `sgcp 440/udp` `SGCP`

# Marshall Rose

- `decvms-sysgt 441/tcp` `DECVMS-SYSGT`
- `decvms-sysgt 441/udp` `DECVMS-SYSGT`

# Lee Barton

- `cvc_host 442/tcp` `CVC_HOST`
- `cvc_host 442/udp` `CVC_HOST`

# Bill Davidson

- `https 443/tcp` `HTTPS`
- `https 443/udp` `HTTPS`

# Kipp E. Hickman

- `snpp 444/tcp` `SNPP` 网络分页呼叫
- `snpp 444/udp` `SNPP` 网络分页呼叫 (`RFC1568`)

# Arnold Miller

- `microsoft-ds 445/tcp` `microsoft-DS`
- `microsoft-ds 445/udp` `microsoft-DS`
- `ddm-rdb 446/tcp` `DDM-RDB`
- `ddm-rdb 446/udp` `DDM-RDB`
- `ddm-dfm 447/tcp` `DDM-DFM`
- `ddm-dfm 447/udp` `DDM-DFM`
- `ddm-byte 448/tcp` `DDM-BYTE`
- `ddm-byte 448/udp` `DDM-BYTE`

# Jan David Fisher

- `as-server 449/tcp` `AS-SERVER` 服务器映射
- `as-server 449/udp` `AS-SERVER` 服务器映射

# Barbara Foss

- `tserver 450/tcp` `TSERVER`
- `tserver 450/udp` `TSERVER`

# Harvey S. Schultz

- `sfs-smp-net 451/tcp` `SFS-SMP-NET` Cray 网络信号
- `sfs-smp-net 451/udp` `SFS-SMP-NET` Cray 网络信号
- `sfs-config 452/tcp` `SFS-CONFIG` Cray SFS 服务器
- `sfs-config 452/udp` `SFS-CONFIG` Cray SFS 服务器

# Walter Poxon

- `creativeserver 453/tcp` `CREATIVESERVER`
- `creativeserver 453/udp` `CREATIVESERVER`
- `contentserver 454/tcp` `CONTENTSERVER`
- `contentserver 454/udp` `CONTENTSERVER`
- `creativepartnr 455/tcp` `CREATIVEPARTNR`
- `creativepartnr 455/udp` `CREATIVEPARTNR`

# Jesus Ortiz

- `macon-tcp 456/tcp` `MACON-TCP`
- `macon-udp 456/udp` `MACON-UDP`

# Yoshinobu Inoue

- `scohelp 457/tcp` `SCOHELP`
- `scohelp 457/udp` `SCOHELP`

# Faith Zack

- `appleqtc 458/tcp` `APPLEQTC` QuickTime
- `appleqtc 458/udp` `APPLEQTC` QuickTime

# Murali Ranganathan

- `ampr-rcmd 459/tcp` `AMPR-RCMD`
- `ampr-rcmd 459/udp` `AMPR-RCMD`

# Rob Janssen

- `skronk 460/tcp` `SKRONK`
- `skronk 460/udp` `SKRONK`

# Henry Strickland

- `datasurfsrv 461/tcp` `DATURFSRV` DataSurv
- `datasurfsrv 461/udp` `DATURFSRV` DataSurv
- `datasurfssec 462/tcp` `DATURFSSEC` DataSurf
- `datasurfssec 462/udp` `DATURFSSEC` DataSurf

# Larry Barnes

- `alpes 463/tcp` `ALPES`
- `alpes 463/udp` `ALPES`

# Alain Durand

- `kpasswd 464/tcp` `KPASSWORD`
- `kpasswd 464/udp` `KPASSWORD`

# Theodore Ts’o

- `ssmtp 465/tcp` `SSMPTP`
- `ssmtp 465/udp` `SSMPTP`

# John Hemming

- `digital-vrc 466/tcp` `DIGITAL-VRC`
- `digital-vrc 466/udp` `DIGITAL-VRC`

# Dave Forster

- `mylex-mapd 467/tcp` `MYLEX-MAPD`
- `mylex-mapd 467/udp` `MYLEX-MAPD`

# Gary Lewis

- `photuris 468/tcp` `PHOTURIS`
- `photuris 468/udp` `PHOTURIS`

# Bill Simpson

- `rcp 469/tcp` `RCP` Radio 控制协议
- `rcp 469/udp` `RCP` Radio 控制协议

# Jim Jennings

- `scx-proxy 470/tcp` `SCX-PROXY`
- `scx-proxy 470/udp` `SCX-PROXY`

# Walter Poxon

- `mondex 471/tcp` `MONDEX`
- `mondex 471/udp` `MONDEX`

# Bill Reding

- `ljk-login 472/tcp` `LJK-LOGIN`
- `ljk-login 472/udp` `LJK-LOGIN`

# LJK Software, Cambridge, Massachusetts

- `hybrid-pop 473/tcp` `HYBRID-POP`
- `hybrid-pop 473/udp` `HYBRID-POP`

# Rami Rubin

- `tn-tl-w1 474/tcp` `TN-TL-W1`
- `tn-tl-w2 474/udp` `TN-TL-W2`

# Ed Kress

- `tcpnethaspsrv 475/tcp` `TCPNETHASPRV`
- `tcpnethaspsrv 475/udp` `TCPNETHASPRV`

# Charlie Hava

- `exec 512/tcp` `EXEC` 远程进程执行
- `biff 512/udp` `BIFF` 用于邮件系统
- `login 513/tcp` `LOGIN` 远程登录 telnet
- `who 513/udp` `WHO` 维护数据库
- `cmd 514/tcp` `CMD` 类似 exec
- `syslog 514/udp` `SYSLOG`
- `printer 515/tcp` `PRINTER` 打印后台程序
- `printer 515/udp` `PRINTER` 打印后台程序
- `talk 517/tcp` `TALK` tenex 链接
- `talk 517/udp` `TALK` tenex 链接
- `ntalk 518/tcp` `NTALK`
- `ntalk 518/udp` `NTALK`
- `utime 519/tcp` `UTIME`
- `utime 519/udp` `UTIME`
- `efs 520/tcp` `EFS` 扩展文件名服务器
- `router 520/udp` `ROUTER` 本地路由进程

注册端口不受 IANA 控制，在大多数系统中可以由普通用户进程或普通用户执行的程序使用。端口在 TCP `RFC793` 中用于命名传输长时间的逻辑连接。为了向未知调用者提供服务，定义了服务联系端口。此列表指定了服务器进程作为其联系端口使用的。虽然 IANA 可以控制这些端口的使用，但为了方便社区，注册或列出了这些端口的使用。在可能的情况下，这些端口分配也用于 UDP `RFC768`。注册端口范围为 1024-65535。

| 关键字 | 十进制 | 描述 | 引用 |
| :--- | :--- | :--- | :--- |
| `1024/tcp` | | 预留 | IANA |
| `1024/udp` | | 预留 | IANA |
| `blackjack 1025/tcp` | 1025 | 网络黑杰 | |
| `blackjack 1025/udp` | 1025 | 网络黑杰 | |
| `iad1 1030/tcp` | 1030 | BBN IAD | |
| `iad1 1030/udp` | 1030 | BBN IAD | |
| `iad2 1031/tcp` | 1031 | BBN IAD | |
| `iad2 1031/udp` | 1031 | BBN IAD | |
| `iad3 1032/tcp` | 1032 | BBN IAD | |
| `iad3 1032/udp` | 1032 | BBN IAD | |
| `nim 1058/tcp` | 1058 | nim | |
| `nim 1058/udp` | 1058 | nim | |
| `nimreg 1059/tcp` | 1059 | nimreg | |
| `nimreg 1059/udp` | 1059 | nimreg | |
| `instl_boots 1067/tcp` | 1067 | 安装引导程序. | |
| `instl_boots 1067/udp` | 1067 | 安装引导程序. | |
| `instl_bootc 1068/tcp` | 1068 | 安装引导程序. | |
| `instl_bootc 1068/udp` | 1068 | 安装引导程序. | |
| `socks 1080/tcp` | 1080 | Socks | |
| `socks 1080/udp` | 1080 | Socks | |
| `ansoft-lm-1 1083/tcp` | 1083 | Anasoft 许可管理器 | |
| `ansoft-lm-1 1083/udp` | 1083 | Anasoft 许可管理器 | |
| `ansoft-lm-2 1084/tcp` | 1084 | Anasoft 许可管理器 | |
| `ansoft-lm-2 1084/udp` | 1084 | Anasoft 许可管理器 | |
| `nfsd-status 1110/tcp` | 1110 | 集群状态 | |
| `nfsd-keepalive 1110/udp` | 1110 | 集群状态 | |
| `nfa 1155/tcp` | 1155 | 网络文件访问 | |
| `nfa 1155/udp` | 1155 | 网络文件访问 | |
| `lupa 1212/tcp` | 1212 | lupa | |
| `lupa 1212/udp` | 1212 | lupa | |
| `nerv 1222/tcp` | 1222 | SNI 网络 | |
| `nerv 1222/udp` | 1222 | SNI 网络 | |
| `alta-ana-lm 1346/tcp` | 1346 | Alta-ana-lm 许可管理器 | |
| `alta-ana-lm 1346/udp` | 1346 | Alta-ana-lm 许可管理器 | |
| `bbn-mmc 1347/tcp` | 1347 | bbn 多媒体 | |



# 端口服务列表

- `bbn-mmc` `1347/udp` `bbn 多媒体`
- `bbn-mmx` `1348/tcp` `bbn 多媒体`
- `bbn-mmx` `1348/udp` `bbn 多媒体`

- `csdmbase` `1467/udp` `CSDM`
- `csdm` `1468/tcp` `CSDM`
- `csdm` `1468/udp` `CSDM`
- # Robert Stabl `58`
- `aal-lm` `1469/tcp` `Active Analysis Limited License Manager`
- `aal-lm` `1469/udp` `Active Analysis Limited License Manager`
- # David Snocken +44 (71)437-7009
- `uaiact` `1470/tcp` `Universal Analytics`
- `uaiact` `1470/udp` `Universal Analytics`
- # Mark R. Ludwig
- `csdmbase` `1471/tcp` `csdmbase`
- `csdmbase` `1471/udp` `csdmbase`
- `csdm` `1472/tcp` `csdm`
- `csdm` `1472/udp` `csdm`
- # Robert Stabl
- `openmath` `1473/tcp` `OpenMath`
- `openmath` `1473/udp` `OpenMath`
- # Garth Mayville
- `telefinder` `1474/tcp` `Telefinder`
- `telefinder` `1474/udp` `Telefinder`
- # Jim White
- `taligent-lm` `1475/tcp` `Taligent License Manager`
- `taligent-lm` `1475/udp` `Taligent License Manager`
- # Mark Sapsford
- `clvm-cfg` `1476/tcp` `clvm-cfg`
- `clvm-cfg` `1476/udp` `clvm-cfg`
- # Eric Soderberg
- `ms-sna-server` `1477/tcp` `ms-sna-server`
- `ms-sna-server` `1477/udp` `ms-sna-server`
- `ms-sna-base` `1478/tcp` `ms-sna-base`
- `ms-sna-base` `1478/udp` `ms-sna-base`
- # Gordon Mangione
- `dberegister` `1479/tcp` `dberegister`
- `dberegister` `1479/udp` `dberegister`
- # Brian Griswold
- `pacerforum` `1480/tcp` `PacerForum`
- `pacerforum` `1480/udp` `PacerForum`
- # Peter Caswell
- `airs` `1481/tcp` `AIRS`
- `airs` `1481/udp` `AIRS`
- # Bruce Wilson, 905-771-6161
- `miteksys-lm` `1482/tcp` `Miteksys License Manager`
- `miteksys-lm` `1482/udp` `Miteksys License Manager`
- # Shane McRoberts
- `afs` `1483/tcp` `AFS License Manager`
- `afs` `1483/udp` `AFS License Manager`
- # Michael R. Pizolato
- `confluent` `1484/tcp` `Confluent License Manager`
- `confluent` `1484/udp` `Confluent License Manager`
- # James Greenfiel
- `lansource` `1485/tcp` `LANSource`
- `lansource` `1485/udp` `LANSource`
- # Doug Scott
- `nms_topo_serv` `1486/tcp` `nms_topo_serv`
- `nms_topo_serv` `1486/udp` `nms_topo_serv` `59`
- # Sylvia Siu
- `localinfosrvr` `1487/tcp` `LocalInfoSrvr`
- `localinfosrvr` `1487/udp` `LocalInfoSrvr`
- # Brian Matthews
- `docstor` `1488/tcp` `DocStor`
- `docstor` `1488/udp` `DocStor`
- # Brian Spears
- `dmdocbroker` `1489/tcp` `dmdocbroker`
- `dmdocbroker` `1489/udp` `dmdocbroker`
- # Razmiknous
- `insitu-conf` `1490/tcp` `insitu-conf`
- `insitu-conf` `1490/udp` `insitu-conf`
- # Paul Blacknell
- `anynetgateway` `1491/tcp` `anynetgateway`
- `anynetgateway` `1491/udp` `anynetgateway`
- # Dan Poirier
- `stone-design-1` `1492/tcp` `stone-design-1`
- `stone-design-1` `1492/udp` `stone-design-1`
- # Andrew Stone
- `netmap_lm` `1493/tcp` `netmap_lm`
- `netmap_lm` `1493/udp` `netmap_lm`
- # Phillip Magson
- `ica` `1494/tcp` `ica`
- `ica` `1494/udp` `ica`
- # John Richardson
- `cvc` `1495/tcp` `cvc`
- `cvc` `1495/udp` `cvc`
- # Bill Davidson
- `liberty-lm` `1496/tcp` `liberty-lm`
- `liberty-lm` `1496/udp` `liberty-lm`
- # Jim Rogers
- `rfx-lm` `1497/tcp` `rfx-lm`
- `rfx-lm` `1497/udp` `rfx-lm`
- # Bill Bishop
- `watcom-sql` `1498/tcp` `watcom-sql`
- `watcom-sql` `1498/udp` `watcom-sql`
- # Rog Skowius
- `fhc` `1499/tcp` `fhc`
- `fhc` `1499/udp` `fhc`
- # Federico Heinz
- `vlsi-lm` `1500/tcp` `vlsi-lm`
- `vlsi-lm` `1500/udp` `vlsi-lm`
- # Shue-Lin Kuo
- `sas-3` `1501/tcp` `sas-3`
- `sas-3` `1501/udp` `sas-3`
- # Bill Taylor
- `shivadiscovery` `1502/tcp` `shivadiscovery`
- `shivadiscovery` `1502/udp` `shivadiscovery`
- # Jonathan Wenocur `60`
- `imtc-mcs` `1503/tcp` `imtc-mcs`
- `imtc-mcs` `1503/udp` `imtc-mcs`
- # Jim Johnstone
- `evb-elm` `1504/tcp` `evb-elm`
- `evb-elm` `1504/udp` `evb-elm`
- # B.G. Mahesh
- `funkproxy` `1505/tcp` `funkproxy`
- `funkproxy` `1505/udp` `funkproxy`
- # Robert D. Vincent
- `utcd` `1506/tcp` `utcd`
- `utcd` `1506/udp` `utcd`
- # Walter Poxon
- `symplex` `1507/tcp` `symplex`
- `symplex` `1507/udp` `symplex`
- # Mike Turley
- `diagmond` `1508/tcp` `diagmond`
- `diagmond` `1508/udp` `diagmond`
- # Pete Moscatelli
- `robcad-lm` `1509/tcp` `robcad-lm`
- `robcad-lm` `1509/udp` `robcad-lm`
- # Hindin Joseph
- `mvx-lm` `1510/tcp` `mvx-lm`
- `mvx-lm` `1510/udp` `mvx-lm`
- # Charles X. Chen
- `3l-l1` `1511/tcp` `3l-l1`
- `3l-l1` `1511/udp` `3l-l1`
- # Ian A. Young
- `wins` `1512/tcp` `wins`
- `wins` `1512/udp` `wins`
- # Pradeep Bahl
- `fujitsu-dtc` `1513/tcp` `fujitsu-dtc`
- `fujitsu-dtc` `1513/udp` `fujitsu-dtc`
- `fujitsu-dtcs` `1514/tcp` `fujitsu-dtcs`
- `fujitsu-dtcs` `1514/udp` `fujitsu-dtcs`
- # Charles A. Higgins
- `ifor-protocol` `1515/tcp` `ifor-protocol`
- `ifor-protocol` `1515/udp` `ifor-protocol`
- # Dr. R.P. Alston
- `vpad` `1516/tcp` `vpad`
- `vpad` `1516/udp` `vpad` `61`
- `vpac` `1517/tcp` `vpac`
- `vpac` `1517/udp` `vpac`
- `vpvd` `1518/tcp` `vpvd`
- `vpvd` `1518/udp` `vpvd`
- `vpvc` `1519/tcp` `vpvc`
- `vpvc` `1519/udp` `vpvc`
- # Ehud Shapiro
- `atm-zip-office` `1520/tcp` `atm-zip-office`
- `atm-zip-office` `1520/udp` `atm-zip-office`
- # Wilson Kwan
- `ncube-lm` `1521/tcp` `ncube-lm`
- `ncube-lm` `1521/udp` `ncube-lm`
- # Maxine Yuen
- `rna-lm` `1522/tcp` `rna-lm`
- `rna-lm` `1522/udp` `rna-lm`
- # MFlemming@aol.com
- `cichild-lm` `1523/tcp` `cichild-lm`
- `cichild-lm` `1523/udp` `cichild-lm`
- # Andy Burgess
- `ingreslock` `1524/tcp` `ingreslock`
- `ingreslock` `1524/udp` `ingreslock`
- `orasrv` `1525/tcp` `orasrv`
- `orasrv` `1525/udp` `orasrv`
- `prospero-np` `1526/tcp` `prospero-np`
- `prospero-np` `1526/udp` `prospero-np`
- `pdap-np` `1527/tcp` `pdap-np`
- `pdap-np` `1527/udp` `pdap-np`
- # B. Clifford Neuman
- `tlisrv` `1528/tcp` `tlisrv`
- `tlisrv` `1528/udp` `tlisrv`
- # John Klensin
- `coauthor` `1529/tcp` `coauthor`
- `coauthor` `1529/udp` `coauthor`
- `rap-service` `1530/tcp` `rap-service`
- `rap-service` `1530/udp` `rap-service`
- # Phil Servita
- `rap-listen` `1531/tcp` `rap-listen`
- `rap-listen` `1531/udp` `rap-listen`
- # Michael Fischer
- `miroconnect` `1532/tcp` `miroconnect`
- `miroconnect` `1532/udp` `miroconnect` `49`
- `virtual-places` `1533/tcp` `virtual-places`
- `virtual-places` `1533/udp` `virtual-places`
- # Ehud Shapiro
- `micromuse-lm` `1534/tcp` `micromuse-lm`
- `micromuse-lm` `1534/udp` `micromuse-lm`
- # Adam Kerrison
- `ampr-info` `1535/tcp` `ampr-info`
- `ampr-info` `1535/udp` `ampr-info`
- `ampr-inter` `1536/tcp` `ampr-inter`
- `ampr-inter` `1536/udp` `ampr-inter`
- # Rob Janssen
- `sdsc-lm` `1537/tcp` `sdsc-lm`
- `sdsc-lm` `1537/udp` `sdsc-lm`
- # Len Wanger
- `3ds-lm` `1538/tcp` `3ds-lm`
- `3ds-lm` `1538/udp` `3ds-lm`
- # Keith Trummel
- `intellistor-lm` `1539/tcp` `intellistor-lm`
- `intellistor-lm` `1539/udp` `intellistor-lm`
- # Ron Vaughn
- `rds` `1540/tcp` `rds`
- `rds` `1540/udp` `rds`
- `rds2` `1541/tcp` `rds2`
- `rds2` `1541/udp` `rds2`
- # Sudhakar Rajamannar
- `gridgen-elmd` `1542/tcp` `gridgen-elmd`
- `gridgen-elmd` `1542/udp` `gridgen-elmd`
- # John R. Chawner `817`
- `simba-cs` `1543/tcp` `simba-cs`
- `simba-cs` `1543/udp` `simba-cs`
- # Betsy Alexander `604`
- `aspeclmd` `1544/tcp` `aspeclmd`
- `aspeclmd` `1544/udp` `aspeclmd`
- # V. Balaji
- `vistium-share` `1545/tcp` `vistium-share`
- `vistium-share` `1545/udp` `vistium-share`
- # Allison Carleton
- `abbaccuray` `1546/tcp` `abbaccuray`
- `abbaccuray` `1546/udp` `abbaccuray`
- # John Wendt `614`
- `laplink` `1547/tcp` `laplink`
- `laplink` `1547/udp` `laplink`
- # Michael Crawford
- `axon-lm` `1548/tcp` `axon-lm`
- `axon-lm` `1548/udp` `axon-lm`
- # Mark Pearce
- `shivahose` `1549/tcp` `shivahose`
- `shivasound` `1549/udp` `shivasound`
- # Kin Chan
- `3m-image-lm` `1550/tcp` `3m-image-lm`
- `3m-image-lm` `1550/udp` `3m-image-lm`
- # J. C. Canessa
- `hecmtl-db` `1551/tcp` `hecmtl-db`
- `hecmtl-db` `1551/udp` `hecmtl-db`
- # Maxime Belanger



- `pciarray` `1552/tcp` `pciarray` `63`
- `pciarray` `1552/udp` `pciarray`

## Ron Folk

- `sna-cs` `1553/tcp` `sna-cs`
- `sna-cs` `1553/udp` `sna-cs`

## Tony Sowter

- `caci-lm` `1554/tcp` `caci-lm`
- `caci-lm` `1554/udp` `caci-lm`

## Erik Blume

- `livelan` `1555/tcp` `livelan`
- `livelan` `1555/udp` `livelan`

## khedayat

- `ashwin` `1556/tcp` `ashwin`
- `ashwin` `1556/udp` `ashwin`

## Dave Neal

- `arbortext-lm` `1557/tcp` `arbortext-lm`
- `arbortext-lm` `1557/udp` `arbortext-lm`

## David J. Wilson

- `xingmpeg` `1558/tcp` `xingmpeg`
- `xingmpeg` `1558/udp` `xingmpeg`

## Howard Gordon

- `web2host` `1559/tcp` `web2host`
- `web2host` `1559/udp` `web2host`

## Stephen Johnson

- `asci-val` `1560/tcp` `asci-val`
- `asci-val` `1560/udp` `asci-val`

## Brian Schenken

- `facilityview` `1561/tcp` `facilityview`
- `facilityview` `1561/udp` `facilityview`

## Carsteinberg

- `orbixd` `1570/tcp` `orbixd`
- `orbixd` `1570/udp` `orbixd`

## Bridget Walsh

- `rdb-bs-disp` `1571/tcp` `rdb-bs-disp`
- `rdb-bs-disp` `1571/udp` `rdb-bs-disp`

## Jerryowitz

- `chip-lm` `1572/tcp` `chip-lm`
- `chip-lm` `1572/udp` `chip-lm`

## Natowitz

- `itscomm-ns` `1573/tcp` `itscomm-ns`
- `itscomm-ns` `1573/udp` `itscomm-ns`

## Rich Thompson

- `mvel-lm` `1574/tcp` `mvel-lm`
- `mvel-lm` `1574/udp` `mvel-lm`

## David Bisset

- `oraclenames` `1575/tcp` `oraclenames`
- `oraclenames` `1575/udp` `oraclenames`

## P.V. Shivkumar

- `moldflow-lm` `1576/tcp` `moldflow-lm`
- `moldflow-lm` `1576/udp` `moldflow-lm`

## Paul Browne

- `hypercube-lm` `1577/tcp` `hypercube-lm`
- `hypercube-lm` `1577/udp` `hypercube-lm`

## Michael Moller

- `jacobus-lm` `1578/tcp` `jacobus-lm`
- `jacobus-lm` `1578/udp` `jacobus-lm`

## Tony Cleveland

- `ioc-sea-lm` `1579/tcp` `ioc-sea-lm`
- `ioc-sea-lm` `1579/udp` `ioc-sea-lm`

## Paul Nelson

- `tn-tl-r1` `1580/tcp` `tn-tl-r1`
- `tn-tl-r2` `1580/udp` `tn-tl-r2`

## Ed Kress

- `vmf-msg-port` `1581/tcp` `vmf-msg-port`
- `vmf-msg-port` `1581/udp` `vmf-msg-port`

## Eric Whitehill

- `tams-lm` `1582/tcp` `tams-lm`
- `tams-lm` `1582/udp` `tams-lm`

## Philip Scott

- `simbaexpress` `1583/tcp` `simbaexpress`
- `simbaexpress` `1583/udp` `simbaexpress`

## Betsy Alexander `604`

## 1584-1599 未分配

- `issd` `1600/tcp` `issd`
- `issd` `1600/udp` `issd`

## 1601-1641 未分配

- `isis-am` `1642/tcp` `isis-am`
- `isis-am` `1642/udp` `isis-am`
- `isis-ambc` `1643/tcp` `isis-ambc`
- `isis-ambc` `1643/udp` `isis-ambc`

## Ken Chapman

- `nkd` `1650/tcp` `nkd`
- `nkd` `1650/udp` `nkd`
- `shiva-confsvr` `1651/tcp` `shiva-confsvr`
- `shiva-confsvr` `1651/udp` `shiva-confsvr`

## Mike Horowitz

- `xnmp` `1652/tcp` `xnmp`
- `xnmp` `1552/udp` `xnmp`

## Ali Saleh

- `netview-aix-1` `1661/tcp` `netview-aix-1`
- `netview-aix-1` `1661/udp` `netview-aix-1`
- `netview-aix-2` `1662/tcp` `netview-aix-2`
- `netview-aix-2` `1662/udp` `netview-aix-2`
- `netview-aix-3` `1663/tcp` `netview-aix-3`
- `netview-aix-3` `1663/udp` `netview-aix-3`
- `netview-aix-4` `1664/tcp` `netview-aix-4`
- `netview-aix-4` `1664/udp` `netview-aix-4`
- `netview-aix-5` `1665/tcp` `netview-aix-5`
- `netview-aix-5` `1665/udp` `netview-aix-5`
- `netview-aix-6` `1666/tcp` `netview-aix-6`
- `netview-aix-6` `1666/udp` `netview-aix-6`
- `netview-aix-7` `1667/tcp` `netview-aix-7`
- `netview-aix-7` `1667/udp` `netview-aix-7`
- `netview-aix-8` `1668/tcp` `netview-aix-8`
- `netview-aix-8` `1668/udp` `netview-aix-8`
- `netview-aix-9` `1669/tcp` `netview-aix-9`
- `netview-aix-9` `1669/udp` `netview-aix-9`
- `netview-aix-10` `1670/tcp` `netview-aix-10`
- `netview-aix-10` `1670/udp` `netview-aix-10`
- `netview-aix-11` `1671/tcp` `netview-aix-11`
- `netview-aix-11` `1671/udp` `netview-aix-11`
- `netview-aix-12` `1672/tcp` `netview-aix-12`
- `netview-aix-12` `1672/udp` `netview-aix-12`

## Martha Crisson

## 1673-1987 未分配

- `licensedaemon` `1686/tcp` `licensedaemon`
- `licensedaemon` `1686/udp` `licensedaemon`
- `tr-rsrb-p1` `1687/tcp` `tr-rsrb-p1`
- `tr-rsrb-p1` `1687/udp` `tr-rsrb-p1`
- `tr-rsrb-p2` `1688/tcp` `tr-rsrb-p2`
- `tr-rsrb-p2` `1688/udp` `tr-rsrb-p2`
- `tr-rsrb-p3` `1689/tcp` `tr-rsrb-p3`
- `tr-rsrb-p3` `1689/udp` `tr-rsrb-p3`

## Bob Kummerfeld

- `mshnet` `1989/tcp` `mshnet`
- `mshnet` `1989/udp` `mshnet`
- `stun-p1` `1990/tcp` `stun-p1`
- `stun-p1` `1990/udp` `stun-p1`
- `stun-p2` `1991/tcp` `stun-p2`
- `stun-p2` `1991/udp` `stun-p2`
- `stun-p3` `1992/tcp` `stun-p3`
- `stun-p3` `1992/udp` `stun-p3`
- `ipsendmsg` `1992/tcp` `ipsendmsg`
- `ipsendmsg` `1992/udp` `ipsendmsg`
- `snmp-tcp-port` `1993/tcp` `snmp-tcp-port`
- `snmp-tcp-port` `1993/udp` `snmp-tcp-port`
- `stun-port` `1994/tcp` `stun-port`
- `stun-port` `1994/udp` `stun-port`
- `perf-port` `1995/tcp` `perf-port`
- `perf-port` `1995/udp` `perf-port`
- `tr-rsrb-port` `1996/tcp` `tr-rsrb-port`
- `tr-rsrb-port` `1996/udp` `tr-rsrb-port`
- `gdp-port` `1997/tcp` `gdp-port`
- `gdp-port` `1997/udp` `gdp-port`
- `x25-svc-port` `1998/tcp` `x25-svc-port`
- `x25-svc-port` `1998/udp` `x25-svc-port`
- `tcp-id-port` `1999/tcp` `tcp-id-port`
- `tcp-id-port` `1999/udp` `tcp-id-port`
- `callbook` `2000/tcp` `callbook`
- `callbook` `2000/udp` `callbook`
- `dc` `2001/tcp` `dc`
- `dc` `2001/udp` `dc`
- `wizard` `2002/tcp` `wizard`
- `wizard` `2002/udp` `wizard`
- `mailbox` `2004/tcp` `mailbox`
- `mailbox` `2004/udp` `mailbox`
- `emce` `2005/tcp` `emce`
- `emce` `2005/udp` `emce`
- `berknet` `2005/tcp` `berknet`
- `berknet` `2005/udp` `berknet`
- `oracle` `2005/tcp` `oracle`
- `oracle` `2005/udp` `oracle`
- `invokator` `2006/tcp` `invokator`
- `invokator` `2006/udp` `invokator`
- `raid-cc` `2006/tcp` `raid-cc`
- `raid-cc` `2006/udp` `raid-cc`
- `dectalk` `2007/tcp` `dectalk`
- `dectalk` `2007/udp` `dectalk`
- `raid-am` `2007/tcp` `raid-am`
- `raid-am` `2007/udp` `raid-am`
- `conf` `2008/tcp` `conf`
- `conf` `2008/udp` `conf`
- `terminaldb` `2008/tcp` `terminaldb`
- `terminaldb` `2008/udp` `terminaldb`
- `news` `2009/tcp` `news`
- `news` `2009/udp` `news`
- `whosockami` `2009/tcp` `whosockami`
- `whosockami` `2009/udp` `whosockami`
- `search` `2010/tcp` `search`
- `search` `2010/udp` `search`
- `pipe_server` `2010/tcp` `pipe_server`
- `pipe_server` `2010/udp` `pipe_server`
- `raid-cc` `2011/tcp` `raid-cc`
- `raid-cc` `2011/udp` `raid-cc`
- `servserv` `2011/tcp` `servserv`
- `servserv` `2011/udp` `servserv`
- `ttyinfo` `2012/tcp` `ttyinfo`
- `ttyinfo` `2012/udp` `ttyinfo`
- `raid-ac` `2012/tcp` `raid-ac`
- `raid-ac` `2012/udp` `raid-ac`
- `raid-am` `2013/tcp` `raid-am`
- `raid-am` `2013/udp` `raid-am`
- `raid-cd` `2013/tcp` `raid-cd`
- `raid-cd` `2013/udp` `raid-cd`
- `raid-sf` `2014/tcp` `raid-sf`
- `raid-sf` `2014/udp` `raid-sf`
- `troff` `2014/tcp` `troff`
- `troff` `2014/udp` `troff`
- `cypress` `2015/tcp` `cypress`
- `cypress` `2015/udp` `cypress`
- `raid-cs` `2015/tcp` `raid-cs`
- `raid-cs` `2015/udp` `raid-cs`
- `bootserver` `2016/tcp` `bootserver`
- `bootserver` `2016/udp` `bootserver`
- `cypress-stat` `2017/tcp` `cypress-stat`
- `cypress-stat` `2017/udp` `cypress-stat`
- `bootclient` `2017/tcp` `bootclient`
- `bootclient` `2017/udp` `bootclient`
- `terminaldb` `2018/tcp` `terminaldb`
- `terminaldb` `2018/udp` `terminaldb`
- `rellpack` `2018/tcp` `rellpack`
- `rellpack` `2018/udp` `rellpack`
- `whosockami` `2019/tcp` `whosockami`
- `whosockami` `2019/udp` `whosockami`
- `about` `2019/tcp` `about`
- `about` `2019/udp` `about`
- `xinupageserver` `2020/tcp` `xinupageserver`
- `xinupageserver` `2020/udp` `xinupageserver`
- `servexec` `2021/tcp` `servexec`
- `servexec` `2021/udp` `servexec`
- `xinupansion1` `2021/tcp` `xinupansion1`
- `xinupansion1` `2021/udp` `xinupansion1`
- `down` `2022/tcp` `down`
- `down` `2022/udp` `down`
- `xinupansion2` `2022/tcp` `xinupansion2`
- `xinupansion2` `2022/udp` `xinupansion2`
- `xinupansion3` `2023/tcp` `xinupansion3`



- `xinupansion3` `2023/udp` `xinupansion3`
- `xinupansion4` `2024/tcp` `xinupansion4`
- `xinupansion4` `2024/udp` `xinupansion4`
- `ellpack` `2025/tcp` `ellpack`
- `ellpack` `2025/udp` `ellpack`
- `xribs` `2025/tcp` `xribs`
- `xribs` `2025/udp` `xribs`
- `scrabble` `2026/tcp` `scrabble`
- `scrabble` `2026/udp` `scrabble`
- `shadowserver` `2027/tcp` `shadowserver`
- `shadowserver` `2027/udp` `shadowserver`
- `submitserver` `2028/tcp` `submitserver`
- `submitserver` `2028/udp` `submitserver`
- `device2` `2030/tcp` `device2`
- `device2` `2030/udp` `device2`
- `blackboard` `2032/tcp` `blackboard`
- `blackboard` `2032/udp` `blackboard`
- `glogger` `2033/tcp` `glogger`
- `glogger` `2033/udp` `glogger`
- `scoremgr` `2034/tcp` `scoremgr`
- `scoremgr` `2034/udp` `scoremgr`
- `imsldoc` `2035/tcp` `imsldoc`
- `imsldoc` `2035/udp` `imsldoc`
- `objectmanager` `2038/tcp` `objectmanager`
- `objectmanager` `2038/udp` `objectmanager`
- `lam` `2040/tcp` `lam`
- `lam` `2040/udp` `lam`
- `interbase` `2041/tcp` `interbase`
- `interbase` `2041/udp` `interbase`
- `isis` `2042/tcp` `isis`
- `isis` `2042/udp` `isis`
- `isis-bcast` `2043/tcp` `isis-bcast`
- `isis-bcast` `2043/udp` `isis-bcast`
- `ivs-video` `2032/tcp` `ivs-video`
- `ivs-video` `2032/udp` `ivs-video`
- `rimsl` `2044/tcp` `rimsl`
- `rimsl` `2044/udp` `rimsl`
- `cdfunc` `2045/tcp` `cdfunc`
- `cdfunc` `2045/udp` `cdfunc`
- `sdfunc` `2046/tcp` `sdfunc`
- `sdfunc` `2046/udp` `sdfunc`
- `dls` `2047/tcp` `dls`
- `dls` `2047/udp` `dls`
- `dls-monitor` `2048/tcp` `dls-monitor`
- `dls-monitor` `2048/udp` `dls-monitor`
- `shilp` `2049/tcp` `shilp`
- `shilp` `2049/udp` `shilp`
- `dlsrpn` `2065/tcp` `dlsrpn`
- `dlsrpn` `2065/udp` `dlsrpn`
- `dlswpn` `2067/tcp` `dlswpn`
- `dlswpn` `2067/udp` `dlswpn`
- `ats` `2201/tcp` `ats`
- `ats` `2201/udp` `ats`
- `ivs-video` `2232/tcp` `ivs-video`
- `ivs-video` `2232/udp` `ivs-video`
- `ivsd` `2241/tcp` `ivsd`
- `ivsd` `2241/udp` `ivsd`
- `pehelp` `2307/tcp` `pehelp`
- `pehelp` `2307/udp` `pehelp`
- `rtsserv` `2500/tcp` `rtsserv`
- `rtsserv` `2500/udp` `rtsserv`
- `rtsclient` `2501/tcp` `rtsclient`
- `rtsclient` `2501/udp` `rtsclient`
- `hp-3000-telnet` `2564/tcp` `hp-3000-telnet`
- `hp-3000-telnet` `2564/udp` `hp-3000-telnet`
- `www-dev` `2784/tcp` `www-dev`
- `www-dev` `2784/udp` `www-dev`
- `NSWS` `3049/tcp` `NSWS`
- `NSWS` `3049/udp` `NSWS`
- `vmodem` `3141/tcp` `vmodem`
- `vmodem` `3141/udp` `vmodem`
- `ccmail` `3264/tcp` `ccmail`
- `ccmail` `3264/udp` `ccmail`
- `dec-notes` `3333/tcp` `dec-notes`
- `dec-notes` `3333/udp` `dec-notes`
- `mapper-nodemgr` `3984/tcp` `mapper-nodemgr`
- `mapper-nodemgr` `3984/udp` `mapper-nodemgr`
- `map-ethd` `3985/tcp` `map-ethd`
- `map-ethd` `3985/udp` `map-ethd`
- `ws-ethd` `3986/tcp` `ws-ethd`
- `ws-ethd` `3986/udp` `ws-ethd`

© 2021 Magelan Cyber Security 版权所有。ISBN: 9783754300923 出版与发行: BoD - Books on Demand, Norderstedt.

![](img/image-khxfg2pf.jpg)
