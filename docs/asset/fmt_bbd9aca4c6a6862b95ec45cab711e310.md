
32.Zonith. (2018). `Safety and Security Solutions` \[Online\]. Available at: [`zonith.com/`](https://zonith.com/) (Accessed 26 April 2018).

# Chapter 5 Ransomware

Usman Javed Butt\* and Arvind Kumar^†

\**Brunel University, London, UK  
usman.butt@brunel.ac.uk*

^†*Northumbria University, London, UK  
arvind.kumar@northumbria.ac.uk*

## ABSTRACT

In this modern era, malware has emerged as a malicious cyber threat to critical information and communication infrastructure. Ransomware is a type of malware which holds the victim’s computer hostage by encrypting the data available on it, which makes the data unusable and inaccessible to its legitimate user. The attacker demands that the user pay before the decryption key is released to reverse the attack. This chapter explains about ransomware and its classification, how it impacts different platforms, the severity of ransomware, the methodology used by ransomware to penetrate target machines, the attack vectors used, the latest ransomware attacks, the most common targets of ransomware attacks, how to prevent ransomware attacks, and ways to recover.

*Keywords* : malware, ransomware, botnets, cryptography, bitcoins, crypto-lockers, attack vectors, exploit kits, RSA public key, MD5 algorithm, AES, symmetric key, WannaCry, Petya, SimpleLocker, TeslaCrypt, NotPetya, IoT

## 5.1 Introduction

根据 Kapersky 的说法，随着计算机从软盘启动机器发展为更高级的工作站设备，如笔记本电脑和智能手机，恶意软件技术（malware）也随之演变（Kaspersky, 2018a）。Kaspersky 还建议恶意软件自信息技术诞生之初就已存在，但只有在个人电脑普及后，其使用才真正兴起。第一个恶意软件被称为“Elk Cloner Virus”（Tasril *et al*., 2017）。审视 Elk Cloner Virus 的特征可知，这类恶意技术曾采用简单的图案和技术，如今已变得更加复杂，并对计算机设备造成更严重的损害。Elk Cloner Virus 最初是一种“玩笑”，危害不大。其自传播功能依赖于社交工程技术，如软盘插入（Touchette, 2016）。网络罪犯在此基础上发展，形成了当今存在的网络犯罪产业。

网络犯罪给各行业造成约 1000 亿美元的损失，根据所产生的恶意软件类型进行分类。Kaspersky 的研究在 Fig. 5.1 中绘制了“恶意软件分类树”图（Kaspersky, 2018b）。

根据同一报告，分类后的恶意软件被视为“特定功能”恶意软件，意味着这些恶意软件仅能造成特定损害，不会对设备产生复杂效应。相反，网络罪犯设计了多维度、多功能的恶意软件。65.32%为`botnets`，影响全球设备；34.68%为木马与蠕虫的组合，如 Fig. 5.2 所示（Soni, 2018）。

![image](img/fig5.1.jpg)

**Fig. 5.1.**`Malware classification tree`.

![image](img/fig5.2.jpg)

**Fig. 5.2.**`Pie chart of multi-functional malware vs. single-function malware (Trojans)`。

Cisco 将这些多功能恶意软件归类为“高级恶意软件”，并指出最显著的高级恶意软件包括：风险软件（riskware）、间谍软件（spyware）、广告软件（adware）和勒索软件（ransomware），其中勒索软件因其能力最为致命（Cisco, 2018）。Esset 将风险软件定义为一种利用加密技术识别用户操作并将其转为数字交易（如信用卡支付）而未经用户授权的恶意软件（Esset, 2018）。间谍软件会收集设备数据、加密信息并将数据发送回恶意软件源头，这些数据被非法用于勒索数据提供者（Stavrou *et al*., 2010）。阿瓦斯（Avast）指出，间谍软件通常伴随广告软件，后者会向用户显示不雅和不想要的弹窗或广告，对设备造成危害（Avast, 2018）。最终，当这些功能结合并针对更大目的定制时，产生了`勒索软件`。

可以观察到，大多数高级恶意软件的增强源于加密技术的发展及新的文本加密方式。当研究人员意识到这些加密技术可用于开发恶意软件时，`cryptovirology` 这一领域被创立（Young, 2017）。

## 5.2 Ransomware and Its Impact on Different Platforms

勒索软件已导致全球多家公司被迫支付巨额赎金却未获得任何实质性回报。例如，苏格兰酿酒公司 Arran Brewery 最近向匿名黑客支付 2 枚比特币（约 9600 英镑）以恢复系统，该公司所有电脑均被锁定（BBC, 2018）。类似事件也发生在美国政府：宾夕法尼亚州参议院民主党议员会在 2017 年 3 月 3 日遭入侵后，向 Microsoft 支付费用以重建议会的 IT 框架（Cimpanu, 2019）。该报告称，黑客要求支付 28 枚比特币（约 3 万美元），但政府选择花费 70 万美元重建，以此抑制对政府办公室的未来攻击。随着此类事件增多，攻击手段 reportedly 正在恶化。

**Ransomware** 是一种高级恶意软件，受害者需为感染的文件或文档支付赎金才能获得解锁。除非向攻击者支付赎金，否则文件将不被提供给受害者，攻击者收到赎金后会移除恶意软件（Young, 2017）。2017 年，勒索软件被认为是最有效的恶意软件之一，全年感染样本超过 1200 万。2017 年第四季度，恶意样本数量增长了 36%（McAfee, 2017）。2017 年勒索软件导致全球超过 50 亿美元损失， Europol 因此在其“Internet Organised Crime Threat Assessment (IOCTA) 2018”会议上宣布，勒索软件是最危险的恶意软件威胁（Walker, 2018）。

随着勒索软件成为繁荣的商业模式，勒索软件作者开发了两种类型：`locker ransomware` 和 `crypto ransomware`（Deloitte, 2016）。

**Locker ransomwares** 危害较小，因为它们不加密受害者的文件。此类勒索软件通过要求受害者支付“因滥用互联网（如观看色情内容或下载非法 torrents 程序）而收取的罚款”来恐吓受害者。攻击者常在赎金通知中加入受害者的敏感信息（如 IP 地址和最近访问的恶意网站），以增强通知的可信度（Deloitte, 2016）。

**Crypto ransomwares (crypto-locker ransomwares)** 危害更大，对受害者的设备和财务稳定性造成严重打击。加密锁定器是一种会感染设备并`加密`受害者文件直至赎金支付的勒索软件。部分加密锁定器甚至会删除系统备份，使得恢复受害者文件更加困难（Richet, 2016）。

## 5.3 Methodology of Ransomware

“Ransomware”一词由“ransom”（赎金）和“malware”组成。可以将“ransom”定义为为释放人质或被劫持物而支付的款项或屈从（Merriam-Webster, 2018）。因此，理解能够将虚拟平台劫持并进行勒索的恶意软件的关键性以及其操作流程至关重要。

大量关于勒索软件的研究指出，不同勒索软件的传播方式各异，但所有勒索软件均遵循一个包含五个阶段的传播模式，从受害者系统被 compromises 的那一刻开始。这五个阶段如下（Brewer, 2016）：

1.***First Phase: Acquisition, Utilisation and Infection***

获取勒索软件的过程类似于获取其他类型恶意软件（Ali, 2017）。Norton 由 Symantec 建议，勒索软件及其他恶意软件可根据获取方式分为五类，具体如下（Norton, 2018）：

•Software-integrated malwares: 当用户下载标记为“免费”的软件，但实际上会将系统感染于恶意软件。

•点对点虚拟共享：这是指用户通过 BitTorrent、uTorrent 等工具电子方式共享文件。这不仅指熟悉的伙伴之间的文件共享，也包括通过匿名上传下载非法应用程序的行为。

•可移动介质：这是恶意软件最常见的获取途径。恶意软件通过 USB、CD、外置硬盘等电子设备传输给受害者。

•网络获取：当联网设备访问包含恶意 Cookie 或弹窗的网站时，受害者会因点击这些数字平台中的链接而陷入陷阱。

•普遍缺乏防护：当设备未使用能够防护恶意软件的软件时，就会出现此情况。

**勒索软件的攻击向量**

尽管被恶意软件感染的方式有很多，研究人员发现 `幸运的是`，获取勒索软件的方式只有少数几种。这些向量可分为虚拟方式和物理方式。

*虚拟方式的勒索软件获取*：

a)**电子邮件** 是勒索软件攻击的主要来源。统计显示，全球每天约发送 3545 亿封邮件，其中 85.35% 为垃圾邮件，仅 14.64% 为合法邮件（Cisco Talos, 2018）。IBM 估计从 2015 年 1 月到 2016 年 12 月，垃圾邮件量激增了 350%，而且尽管并非所有垃圾邮件都包含恶意软件，垃圾邮件中恶意软件的比例正在上升。2015 年 1 月，包含恶意软件的垃圾邮件占所有垃圾邮件的约 10%；到 2016 年，垃圾邮件增长了 450%，且包含恶意软件的垃圾邮件占比达 210%（IBM, 2016），如图 Fig. 5.3 所示。

Symantec 认为这些恶意软件主要是通过名为 Necrus 的僵尸网络传播，该僵尸网络专门用于全球发送垃圾邮件（O'Brien, 2017）。Symantec 还指出，如果通过电子邮件获取勒索软件，可通过以下步骤激活：

•打开恶意附件  

•恶意附件触发第三方 JavaScript 或 PowerShell 命令  

•恶意附件触发 `exploit kits` 下载  

![image](img/fig5.3.jpg)

**Fig. 5.3.**恶意与非恶意垃圾邮件的体积。

b)**Exploit Kits**（利用工具包）本质上是利用计算机漏洞。Exploit Kits 用于通过 Web 浏览器、程序或操作系统的弱点来获取优势。大多数 Exploit Kits 嵌入网站，用户访问特定网站时即触发工具包，随后扫描设备漏洞并将恶意软件安装到设备上。被感染的网站不一定是恶意网站，像 BBC 或 Yahoo 这类合法网站也可能通过广告被感染（Monrose *et al*., 2015）。Malwarebytes 的研究表明，如图 Fig. 5.4，61% 的所有 Exploit Kits 包含用于勒索软件的 payload（Malwarebytes Labs, 2016）。

*物理方式的勒索软件获取*

**社交工程** 是一种确定但风险较高的传播恶意软件的手段。社交工程是操纵人类心理，诱使个人执行可能对其本人、他人或群体产生毁灭性影响的行为。研究者称其为“黑客化”人以达成目的（Mann, 2008）。

![image](img/fig5.4.jpg)

**Fig. 5.4.**利用载荷摘要。

*Kevin Mitnick 所提社交工程方法论*（Gallegos-Segovia, 2017）：

•信息收集：攻击者在此阶段收集受害者的相关信息。

•信任：攻击者在此阶段与受害者建立更深层次的连接，从而识别合适的攻击向量。

•利用：攻击者在此阶段执行计划，勒索软件感染设备。

•达成：系统最终被妥协，此时攻击者通常与受害者无联系。

2015 年 12 月的 **乌克兰电力网络攻击** 是这些方法被使用的例证。众多报告指出，该事件是对乌克兰电力公司 Ukrenergo 进行精心策划的攻击（BBC, 2017）。调查人员对信息收集和信任建立的精确程度惊讶，并指责俄罗斯人在入侵乌克兰的 SCADA 系统后，通过 USB 介质植入恶意软件进行系统操控（Zetter, 2016）。

上述社交工程方法可用于识别多种攻击类型（Gallegos-Segovia, 2017）：

•Ego 攻击：攻击者通过提供帮助、证明自身智慧的可靠性，试图与受害者建立个人联系。一旦受害者被透明的操纵所欺骗，攻击者即执行勒索软件。

•Sympathy 攻击：攻击者利用情感营造联系，当受害者开始信任攻击者时，便执行勒索软件。

•Bullying 攻击：攻击者使用力量、支配或勒索，以获取信息。这是最常见且最有效的社交工程攻击类型。

2.***第二阶段：交付与实施***

下一步是将恶意软件安装到系统中，加密勒索软件程序，并为即将到来的 **command and control 网络** 建立安全平台。

勒索软件使用简单的非对称 RSA 公钥（Emsisoft, 2018），在某个时点会发起 `GET` 或 `POST` 请求（Securonix, 2018）。`GET` 或 `POST` 请求包含以下参数（Emsisoft, 2018; Securonix, 2018）：

• 计算机名称  

• 处理器信息  

• 卷序号  

• 操作系统  

• 活动驱动器  

• 公共 IP，格式为：`{ ipv4bot[.]whatismyipaddress[.] com}`  

• 磁盘空间  

研究者（Emsisoft, 2018）指出勒索软件开发者使用 RSA 公钥的原因包括：

•占用较少内存，易于传输。  

•网络监测者或恶意软件分析员仅能看到明文和加密的网络流量，看不到实际内容。  

•攻击者可在与部署勒索软件的设备通信时使用自有服务器。

在通过唯一的 MD5 哈希身份识别受害者后，勒索软件会检查是否以 `root` 或 `admin` 权限运行（Rajpal and Kotov, 2014）。若以 root 或 admin 权限运行，则通过以下步骤继续安装勒索软件（Rajpal and Kotov, 2014）：

如流程图所示，勒索软件会将自身解压到设备内存或硬盘，随后自行执行。随后创建多个“stage dropper”副本并将 payload 注入 `explorer.exe` 与 `svchost.exe`。后续阶段，勒索软件还会删除所有阴影副本和备份文件，最终禁用系统恢复功能。

![image](img/fig5.5.jpg)

**Fig. 5.5.**勒索软件安装流程。  

进入`/path/to/xxx`目录，找到`xxx.json`。

在表达式`cvar = avar + bvar`中，加法运算符（`+`）将`avar`与`bvar`相加，得到它们的和`cvar`

在`List.of(arg0, arg1, arg2)`中，`List`接口的工厂方法`of()`接受一系列的元素，返回包含它们的只读列表。

之后我们这样调用`cmd`命令：`cmd arg0 arg1 arg2`。

```
if (condVar > someVal) {console.log("xxx")}
```

3.`SimpleLocker`: 一种在 Android 平台上有效的勒索软件，能够收集 IMEI、型号和制造商信息用于命令与控制中心。加密采用 AES 加密方法，勒索软件还会访问摄像头拍摄受害者的照片，这张照片随后用于进一步威胁受害者支付赎金（NJCCIC，2016）。

4.`WannaCry`: 被认为是历史上最致命的勒索软件之一。该勒索软件导致英国和乌克兰的多家医院瘫痪。WannaCry 的开发者能够发现由美国国家安全局首次揭示的 Windows 漏洞。Symantec 随后怀疑其开发者来自一个与北韩有关的名为 Lazarus 的团体（Fruhlinger，2017）。该勒索软件也是近期出现的。2017 年 WannaCry 在 NHS 运营期间导致 6,912 次预约取消，影响 19,000 人。尽管 Kingsley Manning 认为其“并不高明”，但该攻击之所以能取得成功，是因为不同 NHS 办公室之间“交织在一起”，从而加速了勒索软件的传播（BBC，2017）。

5.`Petya` 和 `NotPetya`: 在 WannaCry 爆发一周后推出，这表明勒索软件进入了一个新时代（Fruhlinger，2017）。`Petya` 或 `NotPetya` 是由发送工作申请文档的 PDF 文件进行传播的，当公司打开该 PDF 时，勒索软件便被激活。`NotPetya` 是首个无需发送垃圾邮件或进行社会工程就能感染并获得管理员权限的勒索软件。只要两台设备之间存在网络连接，`Petya` 或 `NotPetya` 就可以在它们之间传播（Fruhlinger，2017）。
