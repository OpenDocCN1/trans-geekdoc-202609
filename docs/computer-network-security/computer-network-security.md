# 计算机网络安全









## 第7章. 保障本地网络安全 . . . . . . . . . . . . . . . 125

### 7.1. 引言. . . . . . . . . . . . . . . . . . . . . . . 125

### 7.2. 第二层攻击类型 . . . . . . . . . . . . . . . 126

#### 7.2.1. MAC地址泛洪攻击 . . . . . . . . . . . . . 126

#### 7.2.2. MAC欺骗攻击 . . . . . . . . . . . . . . . . . . 127

#### 7.2.3. DHCP耗尽攻击 . . . . . . . . . . . . . . . 127

#### 7.2.4. VLAN跳跃攻击. . . . . . . . . . . . . . . . . . 128

#### 7.2.5. 基于STP的攻击 . . . . . . . . . . . . . . . . . . 130

### 7.3. 保护第二层的最佳安全实践 . . . . . . 131

### 7.4. 应用练习 . . . . . . . . . . . . . . . . . 132

## 第8章. 密码学 . . . . . . . . . . . . . . . . . . . . 143

### 8.1. 密码学基本概念 . . . . . . . . . . . . . . 143

#### 8.1.1. 定义 . . . . . . . . . . . . . . . . . . . . . . . 143

#### 8.1.2. 术语. . . . . . . . . . . . . . . . . . . . . . . 144

### 8.2. 密码学的不同分类 . . . . . . . . . . . . . . 144

#### 8.2.1. 传统密码学 . . . . . . . . . . . . . . . . 145

#### 8.2.2. 现代密码学 . . . . . . . . . . . . . . . . . . 146

#### 8.2.3. 对称加密与非对称加密 . . . . . . . . . . . 147

### 8.3. 密钥管理 . . . . . . . . . . . . . . . . . . . . . . 149

#### 8.3.1. 引言 . . . . . . . . . . . . . . . . . . . . . . . 149

#### 8.3.2. Diffie-Hellman密钥交换. . . . . . . . . . . . . . . 149

### 8.4. 哈希函数 . . . . . . . . . . . . . . . . . . . . . . 151

### 8.5. HMAC代码 . . . . . . . . . . . . . . . . . . . . . . . . 151

### 8.6. 非对称密码学 . . . . . . . . . . . . . . . . . . . 151

#### 8.6.1. 引言 . . . . . . . . . . . . . . . . . . . . . . . 151

#### 8.6.2. 工作原理 . . . . . . . . . . . . . . . . . . . . . . 152

#### 8.6.3. 数字签名 . . . . . . . . . . . . . . . . . . . 153

#### 8.6.4. 公钥基础设施. . . . . . . . . . . . . . . . . . 155

### 8.7. 应用练习 . . . . . . . . . . . . . . . . . . . . 159

## 第9章. IPsec VPN . . . . . . . . . . . . . . . . . . . . . 173

### 9.1. IPsec协议. . . . . . . . . . . . . . . . . . . . . 173

#### 9.1.1. IPsec目标 . . . . . . . . . . . . . . . . . . . . 173

#### 9.1.2. 基本IPsec协议. . . . . . . . . . . . . . . . . 174

#### 9.1.3. IPsec框架. . . . . . . . . . . . . . . . . . . 174

#### 9.1.4. IPsec安全关联 . . . . . . . . . . . . . . . . . . 175

#### 9.1.5. IPsec模式 . . . . . . . . . . . . . . . . . . . . . . 175

### 9.2. IKE协议 . . . . . . . . . . . . . . . . . . . . . . . . 176

#### 9.2.1. 引言 . . . . . . . . . . . . . . . . . . . . . . 176

#### 9.2.2. IKE组件 . . . . . . . . . . . . . . . . . . . . 176

#### 9.2.3. IKE阶段 . . . . . . . . . . . . . . . . . . . . . . 176

### 9.3. 站点到站点VPN配置 . . . . . . . . . . . . . . . . . . . . . . 178

#### 9.3.1. 引言 . . . . . . . . . . . . . . . . . . . . . . . . 178

#### 9.3.2. IPsec VPN配置 . . . . . . . . . . . . . . . . . . 179

### 9.4. 应用练习 . . . . . . . . . . . . . . . . . . . . . 181

## 第10章. 研究高级防火墙 . . . . . . . . . . . . . . . . . . . . 189

### 10.1. Cisco ASA防火墙 . . . . . . . . . . . . . . . . . . . . . 189

#### 10.1.1. 引言 . . . . . . . . . . . . . . . . . . . . . . . . 189

#### 10.1.2. ASA型号 . . . . . . . . . . . . . . . . . . . . . . . . 190

#### 10.1.3. 使用ASA设备的模式. . . . . . . . . . . . . . . . 190

#### 10.1.4. ASA 5505概述 . . . . . . . . . . . . . . . . . . 191

#### 10.1.5. ASA安全级别 . . . . . . . . . . . . . . . . . . 192

#### 10.1.6. 使用CLI配置ASA . . . . . . . . . . . . . . . . . . 193

### 10.2. 应用练习 . . . . . . . . . . . . . . . . . . . . . 198

### 10.3. 使用图形工具配置Cisco元素. . . . . . . . . . . . . . 210

#### 10.3.1. CCP概述 . . . . . . . . . . . . . . . . . . . . 210

#### 10.3.2. ASDM概述 . . . . . . . . . . . . . . . . . . . 210

#### 10.3.3. 使用CCP和ASDM. . . . . . . . . . . . . . . . . . . . 210

### 10.4. TMG 2010防火墙. . . . . . . . . . . . . . . . . . . . 211

#### 10.4.1. 引言 . . . . . . . . . . . . . . . . . . . . . . . . 211

#### 10.4.2. 安装与配置. . . . . . . . . . . . . . . . . . . 211

## 参考文献 . . . . . . . . . . . . . . . . . . . . . . . . . . . . 243

## 索引 . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 245

## 前言

本书面向备考CCNA安全认证（210-260 IINS）的学生，无论他们身处专业培训中心、技术学院，还是与“思科学院”计划相关的培训中心。尽管如此，本书对任何对信息安全感兴趣的人也可能有所帮助，无论他们是在专业环境中工作，还是仅是一名IT用户。

本书涵盖上述思科考试大纲中列出的所有科目。然而，我们也整合了某些我们认为重要的实际网络工作案例。

每章首先介绍与预设安全目标相关的理论概念，然后提供保障网络组件所需的CLI命令和GUI截图。每章末尾还建议了实践任务，帮助学生应用该配置，掌握所介绍的概念。

本书在与思科培训与认证团队合作下开发，以确保内容清晰明了。本书旨在一卷之中呈现构建安全信息系统所需的前沿技术与良好实践。

我们希望本书能满足学生的期望，帮助他们获得认证，同时也让任何对该主题感兴趣的人更好地理解信息安全的不同概念。

Ali SADIQUI
2019年11月

## 简介

## CCNA安全简介

“CCNA安全”证书是一项考试，用于验证保障由思科基础设施组成的网络所需的知识和资格。

这使网络专业人员能够展示所需的技能，以开发安全基础设施、识别网络威胁和网络漏洞，并减轻这些威胁，从而维护数据和设备的完整性、机密性和可用性。

### 前提条件

1) 为了优化您从本书中获得的学习效果，强烈建议您查看以下认证所要求的目标：

- 思科CCENT；
- 思科CCNA路由与交换。

### 命令语法约定

2) 本书用于呈现命令语法的约定如下：

- 文本为**粗体**：表示命令或关键字；
- *斜体*：表示参数或用户变量；
- 竖线(|)：表示互斥的替代元素；
- 方括号([])：表示可选元素；
- 花括号({})：表示必选项；
- 方括号内的花括号([{}])：表示可选元素中的必选项。

## 网络安全基础

- 本章学习以下主题：

- 保障网络安全的主要目标；

- 信息安全术语：

  - 通用术语，
  - 黑客类型，
  - 恶意代码；

- 网络安全的类型：

  - 物理安全，
  - 逻辑安全，
  - 管理安全；

- 与网络逻辑安全相关的主要风险：

  - 不同类型的网络攻击，
  - 网络安全措施，
  - 漏洞审计措施

### 1.1. 引言

网络安全是计算机科学的一个分支，旨在保护计算机网络的所有组件，以防止未经授权的访问、数据窃取、滥用网络连接、数据修改等。其目的是



网络安全旨在提供主动防御方法和机制，以保护网络免受内部和外部威胁。

#### 1.1.1. 保障网络安全的主要目标

保障网络安全的三个主要目标是确保：

- **机密性**：这包括保护存储在计算机网络上或通过计算机网络传输的数据免受未授权人员的访问；
- **完整性**：这维护或确保数据的可靠性。接收方接收到的数据必须与发送方传输的数据相同；
- **可用性**：这确保网络数据或服务始终可供用户访问。

#### 1.1.2. 信息安全术语

##### 1.1.2.1. 一般术语

- **资源**：对组织具有价值且必须受到保护的任何对象。
- **漏洞**：系统中的弱点，可能被威胁利用。
- **威胁**：对资源或网络运行的潜在危险。
- **攻击**：这是为损害资源而采取的行动。
- **风险**：组织资源丢失、被修改、被销毁或遭受其他负面后果的可能性。风险可能源于单一威胁、多个威胁或漏洞的利用：
  $A risk = a resource + a threat + a vulnerability$
- **对策**：减轻潜在威胁或风险的保护措施。

##### 1.1.2.2. 黑客类型

信息技术领域存在不同类型的黑客：

- "**黑客**": 此群体被定义为"网络狂人"，他们只希望了解计算机系统的工作原理，同时测试自己的知识和工具；
- "白帽黑客": 这些是执行安全审计的个人，以测试组织的计算机网络是否受到良好保护；
- "黑帽黑客": 这些是经验丰富的个人，通过进行数据盗窃、黑客攻击账户、渗透系统等行为为非法目的工作；
- "灰帽黑客": 既是"白帽"又是"黑帽"黑客的个人；
- "蓝帽黑客": 这些是测试漏洞以确保应用程序平稳运行的个人；
- "脚本小子": 这些是IT安全管理技能非常基础的个人，他们试图使用他人开发的脚本和程序来渗透系统；
- "黑客活动家": 这些是主要出于意识形态动机的个人；
- "电话黑客": 这些是专门攻击电话系统的个人。通常，他们致力于免费拨打电话；
- "卡盗": 这些是专门攻击智能卡系统的个人。

##### 1.1.2.3. 恶意代码

黑客可能使用的最常见的恶意代码或恶意软件类型是：

- 病毒：这是一种将自身附加到软件上的程序，以便在计算机上执行特定的不良功能。大多数病毒需要用户激活。但是，它们也可以设置为"空闲模式"较长时间，因为它们还可以被编程为避免被检测到；
- 蠕虫：这些是独立的程序，利用已知漏洞以减慢网络速度为目的。它们不需要用户激活，并且可以自我复制并尝试感染网络中的其他主机；
- 间谍软件：这些是间谍软件，通常用于影响用户购买某些产品或服务。间谍软件通常不会自动自我传播，而是未经许可自行安装。它们被编程为：
  - 收集用户的个人信息，
  - 跟踪互联网上的浏览活动以检测用户的偏好，
  - 将HTTP请求重定向到预设的广告网站；
- 广告软件：这指的是任何未经用户许可即显示广告的软件，通常以弹出窗口的形式；
- 恐吓软件：这指的是一类用于说服用户其系统已被病毒感染并建议解决方案的软件，目的是销售软件；
- 特洛伊木马：这是一个具有两个特征的程序：
  - 对用户表面上有用的行为，
  - 隐藏的恶意行为，通常会导致访问运行该软件的机器；
- 勒索软件：勒索软件是一种旨在通过加密内容来阻止访问计算机系统的程序，直到支付一定数额的钱以恢复系统。

### 1.2. 网络安全的类型

我们识别出三类网络安全。

#### 1.2.1. 物理安全

物理安全涉及安装资源的环境的所有方面。这可能包括：

- 服务器室、网络设备等的物理安全；
- 防止事故和火灾；
- 不间断电源；
- 视频监控等。

#### 1.2.2. 逻辑安全

逻辑安全是指实施访问控制系统（使用软件）以保护资源。这可能包括：

- 为密码应用可靠的安全策略；
- 建立基于身份验证、授权和可追溯性的访问模型；
- 确保网络防火墙的正确配置；
- 部署IPS（入侵防御系统）；
- 使用VPN（虚拟专用网络）等。

#### 1.2.3. 管理安全

管理安全允许使用程序手册对组织进行内部监控。

这可能包括：

- 防止错误和欺诈；
- 确定不同参与者或操作员的职责；
- 保护公司财产和资源的完整性；
- 确保所有涉及物料处理的操作都有记录；
- 合理管理公司财产；
- 确保活动的有效高效管理。

注意：——你现在可以尝试练习1。

### 1.3. 与网络逻辑安全相关的主要风险

#### 1.3.1. 不同类型的网络攻击

##### 1.3.1.1. 侦察攻击

侦察攻击或"被动攻击"的目的是收集目标网络的信息，以检测所有漏洞。通常，此攻击使用以下基本方法：

- "ping扫描": 攻击者向一系列IP地址发送ping数据包以识别属于网络的计算机。
- 端口扫描: 攻击者进行端口分析（TCP和UDP）以发现目标计算机上运行了哪些服务；
- 数据包嗅探: "数据包嗅探"可以捕获正在通过网络传输的数据（通常是以太网帧），目的是识别目标网络中使用的MAC地址、IP地址或端口数量。这种攻击甚至可以发现用户名或密码。最常用的数据包捕获软件是wireshark和tcpdump。

##### 1.3.1.2. 密码攻击

这些攻击的目的是发现用户名和密码，以访问各种资源。这种类型的攻击中有两种常用方法：

- 字典攻击: 这种方法使用一组常用作密码的单词或短语；
- 暴力攻击: 这种方法尝试字母、数字和符号的所有可能组合以检测用户的密码。

##### 1.3.1.3. 访问攻击

这些攻击的目的是尝试恢复关于网络组件的敏感信息。执行访问攻击时通常使用以下方法：

- 钓鱼: 钓鱼是通过发送带有假URL的未请求电子邮件，试图恢复敏感信息（通常是财务信息，如信用卡详细信息、登录名、密码等）；
- "pharming": 这是另一种旨在将流量从一个网站重定向到另一个网站的网络攻击；
- "中间人"攻击: 攻击者将自己置于两个网络组件之间，以试图从交换的数据中获益。这种攻击基于，其中包括：
  - 欺骗: 这是一种从未知来源发送伪装成可靠来源的通信的做法，以便接收者认为可靠。这使得可以欺骗防火墙、TCP服务、身份验证服务器等。欺骗可能发生在多个层级：MAC地址、IP地址、TCP/UDP端口、DNS域名，
  - 劫持: 攻击者劫持主机和服务器之间的会话，以未经授权访问该服务。这种攻击依赖于欺骗；
- 混合攻击: 混合攻击结合病毒、蠕虫和其他软件的特征来收集用户信息。





##### 1.3.1.4. 针对可用性的网络攻击

– DoS 或 拒绝服务攻击 是以各种方式使服务不可用的攻击。这些攻击可以分为两大类：

- 通过饱和实施的拒绝服务：此类攻击包括向计算机发送大量虚假请求，使其无法响应真实请求；
- 通过利用漏洞实施的拒绝服务：此类攻击包括利用远程系统中的弱点使其不可用。

– DDoS 或 分布式拒绝服务攻击 是一种源自许多由黑客控制的联网计算机的 DoS 攻击，黑客从不同地理位置发起攻击。这些攻击的基本原理基于以下方法（其中包括）：

- SYN 洪水攻击：攻击者发送多个 TCP-SYN 数据包来建立 'TCP' 连接，但不发送“SYN-ACK”消息；
- ICMP 洪水攻击：攻击者向目标计算机发送多个伪造的 ICMP 数据包。

##### 1.3.1.5. 近距离攻击

近距离攻击的不寻常之处在于，攻击者与目标系统在物理上距离很近。攻击者利用自己靠近目标设备的事实，例如重置路由器，或使用 CD 启动服务器等。

##### 1.3.1.6. 针对批准关系的攻击

当控制一台网络计算机时，攻击者利用该机器与网络上各种外围设备之间的批准关系，以获得更大的控制权。

### 1.3.2. 网络安全措施

为确保公司网络的更高安全性，建议采取以下措施：

- 资源分离：组织的资源网络和各种敏感数据必须位于不同的安全区域（例如，创建 DMZ 区域）。对组织网络和数据库的访问必须通过高度监控的机制进行。
- 深度防御：网络安全设备必须在组织网络的不同位置使用；
- “最小权限”规则：每个用户只能分配执行给定任务所需的最低访问级别；
- 适当保护：保护机制必须以可靠有效的方式在网络的所有级别安装；
- 限制信息查阅：仅向特定员工提供执行特定任务所需的信息。
- 任务分离和轮岗：任务分离和轮岗有助于组织更好地实施安全政策并减少漏洞。

### 1.3.3. 漏洞审计措施

计算机网络审计必须包括以下五个类别：

- 预防措施：包括通过防火墙、物理锁和管理安全策略等手段采取的预防漏洞被利用的预防措施；
- 检测措施：包括使用系统日志、入侵防御系统 (IPS)、防欺骗技术和监控摄像头检索所有关于网络或系统入侵的信息；
- 纠正措施：包括确定安全违规的原因，然后通过更新病毒或 IPS 来减轻这些影响；
- 恢复措施：这些措施使系统在事件发生后能够恢复；
- 威慑措施：这些措施阻止试图破坏网络安全的人员。

### 1.4. 测试学习成果的练习

### ETL 1.–

- 1. 哪个安全术语指对组织有价值的属性或数据？
  - a. 风险。
  - b. 资源。
  - c. 对策。
  - d. 漏洞。

- 2. 以下哪项代表物理安全措施？
  - a. 更换安全人员的政策。
  - b. 每日验证设备事件日志。
  - c. 实施电子锁。
  - d. 建立访问控制列表。

- 3. 以下哪项是使用防火墙的原因？
  - a. 防止未经授权的入站或出站请求访问网络。
  - b. 防止计算机在火灾中受损。
  - c. 方便从网站下载数据。
  - d. 检测并清理计算机上的病毒。

- 4. 以下哪项尊重信息的机密性？
  - a. 通过电话讨论机密数据。
  - b. 仅向授权人员披露机密信息。
  - c. 在共享网站上下载机密信息。
  - d. 将机密信息发送给同事。

- 5. 将黑客类型与其描述匹配。
  | 黑客类型 | 描述 |
  |---|---|
  | 1. Carders | a. 利用计算机技能获取经济利益或损害个人或组织的个人 |
  | 2. Hacktivists | b. 他们通常有助于识别和修复系统中的安全弱点。 |
  | 3. Phreakers | c. 他们主要攻击智能卡系统以利用其漏洞。 |
  | 4. White Hat | d. 利用计算机技能带来政治或社会变革的个人。 |
  | 5. Black Hat | e. 利用电话网络免费拨打电话的人。 |

- 6. 哪种恶意程序可描述为一种将自身附加到另一个程序以执行不良功能的软件？
  - a. 病毒。
  - b. 间谍软件。
  - c. 特洛伊木马。
  - d. 广告软件。
  - e. 蠕虫。

- 7. 蠕虫的主要特征是什么？
  - a. 蠕虫可以独立运行。
  - b. 蠕虫必须由主机系统上的事件激活。
  - c. 蠕虫伪装成合法软件。
  - d. 一旦安装在主机系统上，蠕虫不会自我复制。

- 8. 将安全措施分类为物理安全、逻辑安全或管理安全。
  | 物理安全 | 逻辑安全 | 管理安全 |
  |---|---|---|
  | | | |
  
  - 定义计算机房的进出时间。
  - 安装事件防护系统。
  - 安装防火墙。
  - 定义 ACL 规则。
  - 记录与设备处理相关的所有操作。
  - 安装监控摄像头。
  - 更改 IPS 系统的位置。
  - 定义加密密钥长度。
  - 规定所有访客必须佩戴徽章。
  - 为访问设备实施“最小权限”原则。

- 9. 以下哪项描述了垃圾邮件？
  - a. 未经授权收集个人或组织的信息。
  - b. 执行未经授权的操作，例如修改或删除文件。
  - c. 通过复制文件给系统带来不必要的负载。
  - d. 批量发送不需要的大量信息。

- 10. 以下哪项描述了必须如何报告安全漏洞？
  - a. 使用电话。
  - b. 向 IT 经理发送电子邮件。
  - c. 使用任何通信方式。
  - d. 使用组织安全政策中给定的方法。

- 11. 访问网站时，地址栏中的哪个图标表示该网站是安全的？
  - a. 箭头。
  - b. 锁。
  - c. 星星。
  - d. 盾牌。

- 12. 以下哪些可能会拦截并出于自身目的使用您的消息？
  - a. 媒体。
  - b. 政府。
  - c. 广告机构。
  - d. 犯罪网络。
  - e. 以上全部。

- 13. 防御恶意软件的主要方法是什么？
  - a. 使用加密身份验证技术。
  - b. 在所有主机设备上安装防病毒软件。
  - c. 阻止 ICMP 响应。
  - d. 在整个网络中部署入侵防御系统。

- 14. 以下哪项描述了特洛伊木马？
  - a. 嵌入看似合法的可执行程序中的恶意软件。
  - b. 发送大量数据以阻止服务的恶意软件。
  - c. 用于获取网络管理员密码的电子字典。
  - d. 用于说服用户其系统已被病毒感染的软件。

### ETL 2.–

- 1. 可以使用什么简单的对策来缓解“ping sweep”攻击？
  - a. 使用加密身份验证协议。
  - b. 在主机上安装防病毒软件。





- c. 在所有网络设备上部署“反嗅探”软件。
- d. 在所有网络设备上阻止 ICMP 回送响应。

2. 可以使用哪些网络安全对策来防范 DoS 攻击？选择两个答案。

- a. 安装防病毒软件。
- b. 部署 IPS（入侵防护系统）。
- c. 安装用于对用户进行身份验证的应用程序。
- d. 安装反欺骗技术。
- e. 部署数据加密技术。

3. 如何定义“ping 扫描”？

- a. 这是一种网络扫描技术，可发现 IP 地址范围内可用的主机。
- b. 这是一款允许捕获通过局域网发送的所有网络数据包的应用程序。
- c. 这是一种检查局域网上可用端口号（TCP 或 UDP）范围的技术。
- d. 这是一种可使用帧分析发现局域网上所有可用 IP 地址的技术。

4. DoS 攻击的两个特征是什么？选择两个答案。

- a. 它们总是在访问攻击之前发生。
- b. 它们试图损害网络、主机或应用程序的可用性。
- c. 它们难以实施，且仅由高技能攻击者发起。
- d. 它们始终使用 ICMP 协议。
- e. 它们易于检测。

5. 欺骗攻击中会发生什么？

- a. 攻击者修改通过网络传输的数据以访问机密信息。
- b. 攻击者向设备发送大量网络流量，使用户无法访问。
- c. 攻击者向目标设备发送格式错误的帧，导致其故障。
- d. 攻击者发送恶意代码以窃取设备上存储的所有数据。

6. 攻击者使用未授权的接入点来捕获目标用户的网络流量，这种攻击类型是什么？

- a. 对批准关系的攻击。
- b. 缓冲区溢出攻击。
- c. “中间人”攻击。
- d. DDoS 攻击

7. 这是一种网络安全攻击类型，入侵者控制两个实体之间的通信以谋取自身利益。

- a. 网络钓鱼。
- b. 缓冲区溢出。
- c. 药房劫持。
- d. 劫持。
- e. SYN 洪水攻击。

8. 缓冲区溢出攻击中会发生什么？

- a. 攻击者将一个网站的流量重定向到另一个网站。
- b. 攻击者从不同地理区域的许多连接计算机发送多个查询，使服务不可用。
- c. 攻击者将病毒、蠕虫和其他软件的特征相结合，以收集用户信息。
- d. 攻击者尝试在设备的饱和内存中写入额外数据。

9. 在社交网站上共享过多信息的风险是什么？

- a. 网络钓鱼。
- b. 缓冲区溢出。
- c. 药房劫持。
- d. 劫持。
- e. 勒索。

10. 创建强密码必须使用多少个字符？

- a. 八个字符。
- b. 十六个字符。
- c. 尽可能多的字符。
- d. 字符数量无关紧要。

11. 强密码可能难以记住，可以做什么来避免忘记它们？

- a. 使用易于记住的首字母缩写或短语。
- b. 制定密码策略。
- c. 使用带加密的密码管理软件。
- d. 以上都是。

12. 攻击者检测一个 10 字符密码需要多长时间？

- a. 一小时以内。
- b. 一周以内。
- c. 一个月以内。
- d. 取决于许多因素。

13. 攻击者使用 *wireshark* 工具发现用户名和管理密码。这是什么类型的网络攻击？

- a. “中间人”攻击。
- b. DoS 攻击。
- c. 侦察攻击。
- d. 近场攻击。

## 保护网络设备

本章将学习以下主题：

- 网络流量的类型：
- 管理平面，
- 控制平面，
- 数据平面；
- 保护管理平面：
- 保护密码，
- 实现连接限制，
- 通过控制线、VTY 和辅助线保护访问，
- 分配管理角色：使用特权级别保护访问；
- 通过管理“视图”和“超级视图”保护访问：
- 保护配置文件和系统，
- 使用自动化安全功能；
- 保护控制平面。

### 2.1. 网络流量类型

Cisco 将不同类型的网络流量分类为不同的通信“平面”。它定义了三个这样的平面：管理平面、控制平面和数据平面。

- 管理平面：这包括网络管理员用于配置网络设备的流量。它通常由 **Telnet**、**SSH** 和 **SNMP** 等协议组成；
- 控制平面：这包括网络设备之间的流量，用于相互发现和/或自动配置网络，例如更新 **路由协议** 或 ARP 协议的流量。
- 数据平面：这是网络中最终用户的实际流量。

### 2.2. 保护管理平面

保护管理平面包括（但不限于）以下内容：

- 应用安全密码策略；
- 保护控制台、VTY 和辅助访问；
- 保护和归档配置；
- 启用日志记录以记录所有更改；
- 使用 NTP（网络时间协议）同步网络设备上的时钟。

### 2.3. 保护密码

应用密码策略时必须考虑以下事项：

- 经常更改密码；
- 密码中包含字母数字字符、大写字母、小写字母、符号和空格；
- 不要使用容易被检测到的密码；
- 加密所有密码；
- 设置密码最小长度为 10 个字符；

| 命令 | 描述 |
| --- | --- |
| Router(config)# service password-encryption | 加密所有密码。 |

| 命令 | 描述 |
| --- | --- |
| Router(config)# security passwords min-length length | 对所有新密码应用最小长度。现有密码不受影响。长度可为 1 到 16。建议使用 10 个或更多字符。 |
| Router(config)# enable algorithm-type {md5|scrypt|sha256} secret password | 使用首选模式加密密码，使用 MD5 算法。 |

### 2.4. 实现连接限制

#### 2.4.1. 配置登录横幅

横幅是 Cisco 系统中使用的一种功能，可在使用 Cisco 机器时显示文本消息。Cisco 建议在所有交互会话中显示法律通知横幅。这样做主要有两个原因：

- 横幅必须用于向入侵者和用户发出警告，告知其适用的安全政策，他们必须遵守该政策；
- 横幅必须用于快速标识正在访问的终端。

| 命令 | 描述 |
| --- | --- |
| banner exec | 每次启动 EXEC 模式时显示自定义横幅。 |
| banner login | 在输入用户名和密码之前显示自定义横幅。 |
| banner motd | 定义自定义“今日消息”横幅。 |

#### 2.4.2. 配置连接参数

| 命令 | 描述 |
| --- | --- |
| login block-for X attempts Y within Z | 在“Z”秒内发生“Y”次登录尝试后，阻止访问“X”秒。 |
| login quiet-mode access-class {acl-name|acl-number} | 当 login block-for 阻止访问时，定义 ACL 以授权连接。 |

| 命令 | 描述 |
| --- | --- |
| login delay second | 设置连续登录尝试之间的延迟。 |
| login on-failure log [every login] | 每次连接尝试失败时在事件日志中创建条目。此命令可自定义。 |
| login on-success log [every login] | 每次成功登录尝试时在事件日志中创建条目。 |

### 2.5. 通过控制台线路、VTY 和辅助线保护访问

#### 2.5.1. 通过控制台线路保护访问并禁用辅助线

| 命令 | 描述 |
| --- | --- |
| Router(config)# username name privilege level secret password | 创建本地用户数据库并加密其密码。 |
| Router(config)# line vty 0 4 Router(config-line)# login local | – |
| Router(config-line)# exec-timeout minutes seconds | 将非活动期设置为特定值。默认值为 10 分钟。 |
| Router(config-line)# line aux 0 | 进入“辅助线”模式。 |
| Router(config-line)# no exec | 禁用辅助端口。 |

#### 2.5.2. 使用 ssh 保护 VTY 访问

| 命令 | 描述 |
| --- | --- |
| Router(config)# ip ssh version [1|2] | 建议使用版本 2。 |
| Router(config)# ip ssh time-out seconds | 定义在协商阶段 SSH 客户端响应前等待的秒数。默认值设置为 120 秒。 |
| Router(config)# ip ssh authentication-retries integer | 限制登录尝试次数。默认值为 3。 |
| Router(config)# login block-for seconds attempts tries within seconds | 保护 VTY 连接。 |
| Router(config-line)# transport input ssh | 仅授权 SSH 会话。 |
| Router(config-line)# access-class ACL-number | 应用 ACL 以控制对 VTY 线路的访问。 |





### 2.6. 管理角色分配

#### 2.6.1. IOS系统的特权级别

特权级别决定用户在路由器上运行某些命令的能力。默认情况下，Cisco路由器有三个特权级别，即“零”、“用户”和“特权”：

- 零级：这只允许五个命令：_logout, enable, disable, help and exit_；
- 用户级别（级别1）：这对路由器提供非常有限的只读访问；
- 特权级别（级别15）：这对路由器提供完全控制。

为了增加灵活性，Cisco路由器还可以配置为使用16个不同的特权级别（从0到15）。

#### 2.6.2. 配置特权级别

| Command | Description |
|---|---|
| Router(config)# privilege mode { level level command \| reset command } | 允许在自定义特权级别上使用命令。 |
| Router(config)# enable secret level level password | 在自定义特权级别分配密码。 |
| Router> enable level | 访问自定义特权级别。 |

#### 命令使用示例

| Command | Description |
|---|---|
| R1(config)# privilege exec level 5 ping | 允许在特权级别5使用“ping”命令。 |
| R1(config)# privilege exec level 5 reload | 允许在特权级别5使用“reload”命令。 |
| R1(config)# enable secret level 5 tri | 启用配置Enable密码以访问级别5。 |
| R1> enable 5 Password: | 允许用户以特权5访问。除常规Level 1命令外，Level 5用户还可以使用“ping”和“reload”命令。 |
| R1# show privilege Current privilege level is 5 | 特权级别验证。 |

注意：当为特权级别定义一个命令时，语法为此命令子集的所有命令也会在此级别定义。例如，如果“show ip route”命令自动定义在级别10，那么“show”和“show ip”命令也会自动在特权级别10定义，除非这些命令分别在不同级别定义。

#### 2.6.3. 为每个用户设置特权级别

建议为每个用户配置特权级别。可以使用以下命令：

```
Router(config)#username name privilege privilege-level secret password
```

#### 示例

```
Router(config)#username user1 privilege 5 secret
Ci$co012
Router(config)#username user2 privilege 12 secret
Ci$co013
```

#### 2.6.4. 为控制台、VTY和辅助线路访问设置特权级别

默认情况下，控制台、辅助或VTY（虚拟终端线路）被分配特权级别1。要修改这些访问线路的默认特权级别，请执行以下操作：

| Command | Description |
|---|---|
| R1(config)# line console 0 | 访问控制台（或辅助）端口。 |
| R1(config-line)# privilege level 4 | 定义使用此模式的特权级别。 |
| R1(config)# line vty 0 4 | 访问VTY模式。 |
| R1(config-line)# privilege level 10 | 定义使用此模式的特权级别。 |

注意：你现在可以尝试练习1。

#### 2.6.5. 通过管理“视图”和“超级视图”保护访问

#### 2.6.5.1. 视图简介

虽然用户可以通过特权级别控制CLI访问，但这些功能并未为网络管理员提供更多选项。CLI视图提供更详细的访问控制能力，从而提高安全性。

视图还具有以下特征：

- 必须先激活“AAA”模型（参见第4章）；
- 用户帐户可能位于本地机器上或外部“AAA服务器”上；
- 分配给“视图”的访问级别优先于“特权”级别；
- 如果未向用户分配“视图”级别，则用户可以使用其特权级别；
- 每个用户只能配置一个“视图”；
- 配置“视图”时，名称和密码区分大小写。

要配置视图，请执行以下操作：

| Command | Description |
|---|---|
| R1(config)# parser view View1 | 创建名为“View1”的视图。 |
| R1(config-view)# secret cisco123 | 为“视图”分配密码。 |
| R1(config-view)# commands exec include show | 此视图可以使用EXEC模式的所有“show”命令。 |
| R1(config-view)# commands exec include ping | 此视图可以使用EXEC模式的“ping”命令。 |
| R1(config-view)# commands exec exclude telnet | 此视图不能使用EXEC模式的“telnet”命令。 |
| R1# enable view View1 Password: | 连接到视图View1以进行验证。 |

#### 2.6.5.2. 超级视图简介

“超级视图”是一个或多个“视图”的集合，允许管理员轻松定义每个用户授权的命令。

超级视图具有以下特征：

- 超级视图不能直接通过命令配置。它将构成它的视图集的配置组合在一起；
- 一个视图可以在多个超级视图之间共享；
- 连接到超级视图的用户可以访问超级视图中包含的视图中配置的所有命令；
- 删除超级视图不会删除与此视图关联的所有视图。

要配置视图，请执行以下操作：

| Command | Description |
|---|---|
| Router(config)# parser view Super-view-name Superview | 在全局配置模式下创建超级视图。 |
| Router(config-view)# secret password | 为超级视图分配密码。 |
| Router(config-view)# view view-name | 将现有视图分配给超级视图。 |
| Router# username U1 view Super-view-name | 将超级视图分配给用户。 |
| Router# enable view view-name | 连接到超级视图。 |
| R1# show parser view all | 显示超级视图列表。 |

#### 2.6.6. 保护配置文件和IOS系统

Cisco IOS系统提供创建IOS映像或配置文件副本的功能。存档以“bootset”格式存储，受删除保护。

要存档IOS映像文件或配置文件，请执行以下操作：

| Command | Description |
|---|---|
| R1(config)# secure boot-image | 通过将IOS映像隐藏在Flash内存中来保护它。这只能在ROMMON模式下看到。 |
| R1(config)# secure boot-config | 保护配置文件。 |
| R1# show secure bootset | 显示Cisco IOS映像和配置文件的存档状态。 |

要在事件发生后从受保护的存档中恢复IOS映像文件，请执行以下操作：

| Command | Description |
|---|---|
| Router# reload<br>Proceed with reload? [confirm] | 重新启动路由器。 |
| rommon 1 > dir flash: | 进入ROMMON模式并显示可用的“bootset”文件。 |
| rommon 2 > boot flash:c1841-advipservicesk9-mz.124-20.T1.bin | 使用索引映像重新启动路由器。 |
| Router(config)# secure boot-config restore flash::runcfg-20120701-090211.ar | 恢复受保护的配置。 |

#### 2.6.7. 使用自动化安全功能

#### 2.6.7.1. 简介

**Autosecure**是一个简单的安全配置脚本，它禁用非必要的系统服务，并允许您配置推荐的安全级别。**Autosecure**命令以与使用安装程序配置路由器相同的方式启动命令行向导。

#### 2.6.7.2. 配置

Router# auto secure

--- AutoSecure 配置 ---

*** AutoSecure配置增强了路由器的安全性，但它不会使路由器免受所有安全攻击 ***

作为AutoSecure一部分完成的所有配置都将在此显示。有关此配置有用的原因和方法以及任何可能副作用的更多详细信息，请参阅Cisco的AutoSecure文档。

在任何提示符处，您可以输入“？”获取帮助。

在任何提示符处，使用ctrl-c中止此会话。

正在为AutoSecure收集路由器信息。

此路由器是否已连接到互联网？[no]:y

...

### 2.7. 保护控制平面

#### 2.7.1. 简介

保护控制平面需要保护由网络设备生成或接收的数据包，这些数据包用于发现和使用网络本身，例如更新路由协议（OSPF、EIGRP、RIP等）的流量以及ICMP或ARP协议的流量。

保护此流可以避免注册错误的路由信息来执行DoS或“中间人”攻击等攻击。

必须注意的是，为这种保护提出的解决方案仅限于保护网络元素的身份验证，而不是设备之间交换的流的加密。

#### 2.7.2. MD5身份验证

有两种共享密钥身份验证方法：明文和MD5消息。由于明文身份验证使用不广泛，MD5方法通常用于执行网络设备的安全标识。

在这种方法中，密钥不会在网络上共享。相反，密钥与其他参数结合以计算一个单一值，称为哈希值，该值用于身份验证。（有关更多信息，请参见第8章。）

#### 2.7.3. 配置OSPF协议身份验证

OSPF支持两种MD5身份验证配置，即按接口或按区域：

- 要配置按接口MD5身份验证，请执行以下操作：



| 命令 | 描述 |
|---|---|
| router(config)#interface interface-type router(config-if)#ip ospf authentication message-digest | 配置每接口身份验证。 |
| router(config-if)#ip ospf message-digest-key key-id md5 key | 定义身份验证设置。 |

- 要配置每区域 MD5 身份验证，请执行以下操作：

| 命令 | 描述 |
|---|---|
| router(config-router)#area area-id authentication message-digest | 配置每区域身份验证。 |
| router(config)#interface interface-type router(config-if)#ip ospf message-digest-key key-id md5 key | 定义身份验证设置。 |

#### 2.7.4. 配置 EIGRP 协议身份验证

要为 EIGRP 配置 MD5 身份验证，必须执行以下操作：

- 配置一个密钥串；
- 在密钥串下配置一个密钥 ID；
- 为密钥 ID 指定密码；
- 为密钥指定接受时间和过期时间（可选）。

请执行以下操作：

| 命令 | 描述 |
|---|---|
| router(config)#key chain name-of-key-chain | 密钥串可用于配置多个密钥，这些密钥随后可用于执行安全身份验证。例如，这样可以为给定密钥配置有效期，或在有限时间内使用一系列轮换密钥，以降低密钥被攻破的可能性。 |

| 命令 | 描述 |
|---|---|
| router(config-keychain)#key key-id | 创建一个密钥并进入密钥配置模式。 |
| router(config-keychain-key)#key-string key-string | 配置一个密钥字符串。 |
| router(config)#interface interface-type router(config-if)#ip authentication key-chain eigrp as-number key-chain-name | 配置使用特定密钥串进行身份验证。 |
| router(config-if)#ip authentication mode eigrp as-number md5 | 配置使用 MD5 身份验证。 |

注意 - EIGRP 仅支持 MD5 身份验证。

#### 2.7.5. 配置 RIP 身份验证

要为 RIP 配置 MD5 身份验证，请执行以下操作：

| 命令 | 描述 |
|---|---|
| router(config)#key chain name-of-key-chain | 创建密钥串。 |
| router(config-keychain)#key key-id | 创建一个密钥并进入密钥配置模式。 |
| router(config-keychain-key)#key-string key-string router(config-keychain-key)#end | 配置一个密钥字符串。 |
| router(config)#interface interface-type router(config-if)#ip rip authentication key-chain key-chain-name | 配置使用特定密钥串进行身份验证。 |
| router(config-if)#ip rip authentication mode md5 | 配置使用 MD5 身份验证。 |

### 2.8. 应用练习

### 练习 1。

### 拓扑结构

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_41_0.png)

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_42_0.png)

### 寻址表

| 设备 | 接口 | IP 地址 / 子网掩码 | 操作系统 (GNS3) | 网关 |
|---|---|---|---|---|
| R1 | G0/0 | 192.168.0.1/24 | c2600-adventerprisek9-mz.124-1 | - |
| PC1 | NIC | 192.168.0.2/24 | Windows 7 | 192.168.0.1 |

### 目标

- 保护密码。
- 实施连接限制。
- 分配管理角色。

### 使用的软件

- Packet Tracer。
- 或 GNS3。

### 部分 A：建立基本设备配置

- 1.1. 按照拓扑结构中指示的内容配置主机名。
- 1.2. 根据寻址表将 IP 地址应用于设备接口。

### 部分 B：保护密码

- 1. 设置最小密码长度为 8 个字符。

```
R1(config)# security passwords min-length 8
```

- 2. 配置特权模式的密码。

  - 2.1. 为该模式定义明文密码。

```
R1(config)# enable password Ci$c0123
```

- 2.2. 能否从“show run”命令中读取此密码？

- 2.3. 为特权模式设置加密密码。

```
R1(config)# enable secret Ci$c0ena
```

- 2.4. 能否从“show run”命令中读取此密码？

- 3. 配置控制台端口、辅助端口和虚拟访问线路。

  - 3.1. 配置控制台端口密码，并将非活动间隔设置为 5 分钟。

```
R1(config)# line console 0
R1(config-line)# password Ci$c0con
R1(config-line)# exec-timeout 5 0
R1(config-line)# login
R1(config-line)# logging synchronous
```

  - 3.2. 在 VTY 线路上配置密码，并将非活动间隔设置为 2 分钟。

```
R1(config)# line vty 0 4
R1(config-line)# password Ci$c0vty
R1(config-line)# exec-timeout 2 0
R1(config-line)# login
```

  - 3.3. 禁用辅助端口。

```
R1(config)# line aux 0
R1(config-line)# no exec
```

  - 3.4. 通过 Telnet 从 PC1 访问 R1。

```
PC1> telnet 192.168.0.1
```

- 4. 加密所有密码。

  - 4.1. 使用“密码加密服务”命令加密控制台和 VTY 密码。

```
R1(config)# service password-encryption
```

- 4.2. 能否从“show run”命令中读取控制台和 VTY 密码？

### 部分 C：实施连接限制

- 1. 配置登录警告横幅。

  - 1.1. 使用“motd”命令为未授权用户配置警告。

```
R1(config)# banner motd $ Access strictly forbidden for unauthorized persons $
R1(config)# exit
```

  - 1.2. 从命令“show run”中，配置文件中字符“$”被什么替换了？

### 部分 D：保护对 VTY 线路的访问

- 1. 配置 SSH 连接。

使用以下选项配置 SSH 连接：

- 域名：tri.local；
- 用户名：sshadmin，密码：Ci$c0ssh；
- RSA 加密密钥为 1024 位；
- 使用的 SSH 版本为版本 2；
- 等待时间为 90s；
- 登录尝试次数为 3 次；
- 授权 SSH 和 Telnet 会话。

- 2. 配置连接参数。

  - 2.1. 使用“login block-for”命令配置：如果在 30 秒内两次连接尝试失败，则停止连接 60 秒。

```
R1(config)# login block-for 60 attempts 2 within 30
```

  - 2.2. 使用“Login delay”命令配置连续连接尝试之间 5 秒的延迟。

```
R1(config)# login delay 5 (GNS3)
```

  - 2.3. 每次连接尝试成功时，向事件日志添加一条条目。

```
R1(config)# login on-success log
```

或：

```
R1(config)# login on-success log every 1 (GNS3)
```

  - 3. 创建两个新用户帐户，使用秘密密码。

```
R1(config)# username user01 secret user01pass
R1(config)# username user02 secret user02pass
```

- 4. 从 Telnet 会话连接到 R1。

  - 4.1. 从 PC1 建立到 R1 的 Telnet 会话。

```
PC1> telnet 192.168.1.1
```

  - 4.2. 是否要求您输入用户帐户？为什么？

............................................................................

  - 4.3. 定义 VTY 线路使用本地定义的登录帐户。

```
R1(config)# line vty 0 4
R1(config-line)# login local
```

  - 4.4. 从 PC1 重新建立到 R1 的 Telnet 会话。

```
PC1> telnet 192.168.1.1
```

  - 4.5. 尝试使用错误的用户 ID 或密码登录两次。第二次失败尝试后，PC1 上会显示什么消息？

............................................................................

  - 4.6. 第二次不成功的连接尝试后，R1 控制台上会显示什么消息？

............................................................................

- 4.7. 从 PC1，尝试在 60 秒内建立另一个到 R1 的 Telnet 会话。Telnet 连接尝试后，PC1 上会显示什么消息？

- 4.8. Telnet 连接尝试后，R1 路由器上显示了什么消息？

- 5. 仅通过使用 SSH 协议限制到 R1 的连接。

  - 5.1. 配置 VTY 线路仅使用 SSH 协议。

```
R1(config)# line vty 0 4
R1(config-line)# transport input ssh
R1(config-line)# exit
```

  - 5.2. 从 PC1，尝试建立另一个 SSH 和 Telnet 会话到 R1。

### 部分 E：分配管理角色

- 1. 配置特权级别。

  - 1.1. 使用以下选项创建一个新用户帐户：
    - 帐户名称：“SshUser”；
    - 加密密码：‘SshUpa $$’；
    - 特权级别 10。

```
R1(config)# username SshUser privilege 10 secret SshUpa $$
```

  - 1.2. 为特权级别 10 配置密码“Priv10P $”。

```
R1(config)# enable secret level 10 Priv10P$
```

  - 1.3. 在 exec 模式下允许此特权级别使用“ping”命令。

```
R1(config)# privilege exec level 10 ping
```

  - 1.4. 在 exec 模式下允许此特权级别使用“ssh”命令。

```
R1(config)# privilege exec level 10 ssh
```





1.5. 在 exec 模式下为该特权级允许所有“show IP”命令。

```
R1(config)#privilege exec all level 10 show ip
```

1.6. 使用以下选项创建新用户帐户：

- 用户名：“TelUser”；
- 加密密码“TelUpa$$”；
- 特权级别 12。

```
R1(config)# username TelUser privilege 12 secret TelUpa$$
```

1.7. 为特权级别 12 配置密码“Priv12P$”。

```
R1(config)#enable secret level 12 Priv12P$
```

1.8. 在 exec 模式下为该特权级别允许“ping”命令。

```
R1(config)#privilege exec level 12 ping
```

1.9. 在 exec 模式下为该特权级别允许“telnet”命令。

```
R1(config)#privilege exec level 12 telnet
```

1.10. 为该特权级别允许所有配置模式命令

```
R1(config)#privilege exec all level 12 configure
```

1.11. 按照相同步骤配置特权级别 13，并赋予其以下选项：

- 密码 Priv13P$；
- 授权命令：telnet, traceroute, show (全部), configure (全部)。

1.12. 访问特权级别 10、12 和 13 并测试配置。

```
Router>enable 12
Password:
R1#?
Exec commands:
<1-99>   Session number to resume
connect  Open a terminal connection
disable  Turn off privileged commands
- disconnect Disconnect an existing network connection
- enable Turn on privileged commands
- exit Exit from the EXEC
- logout Exit from the EXEC
- no Disable debugging information
- ping Send echo messages
- resume Resume an active network connection
- telnet Open a secure shell client connection
- terminal Set terminal line parameters
```

NOTE:
- 0（零）特权级别命令会自动添加。
- 不希望特定特权级别拥有的所有命令必须单独分配给其他特权级别。
- 结果和特权级别的测试也可以通过使用 TelUser 或 sshUser 帐户通过 ssh 进行。

1.13. 显示当前特权级别。

```
R1# show privilege
```

## 练习 2

### 拓扑

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_48_0.png)

### 寻址表

| 设备 | 接口 | IP 地址 / 子网掩码 | 操作系统 | 网关 |
| :--- | :--- | :--- | :--- | :--- |
| R1 | G0/0 | 192.168.0.1/24 | c2600-adventerprisek9-mz.124-1 | – |
| PC1 | NIC | 192.168.0.2/24 | Windows 7 或更高版本 | 192.168.0.1 |

### 目标

- 保护密码。
- 设置连接限制。
- 通过管理“视图”和“超级视图”来保护访问。
- 保护配置文件和 IOS 系统。
- 使用自动化安全功能。

### 使用的软件

- GNS3。

### Part A: 建立基本设备配置

- 1.1. 按照拓扑图所示配置主机名。
- 1.2. 根据寻址表将 IP 地址应用于设备接口。

### Part B: 保护密码

- 1. 设置最小密码长度为 8 个字符。

```
R1(config)# security passwords min-length 8
```

- 2. 为特权模式配置密码。

```
R1(config)# enable secret Ci$c0ena
```

- 3. 配置控制台端口、辅助端口和虚拟访问线路。

- 3.1. 配置控制台端口密码并将非活动间隔设置为 5 分钟。

```
R1(config)# line console 0
R1(config-line)# password Ci$c0con
R1(config-line)# exec-timeout 5 0
R1(config-line)# login
R1(config-line)# logging synchronous
```

- 3.2. 在 VTY 线路上配置密码并将非活动间隔设置为 2 分钟。

```
R1(config)# line vty 0 4
R1(config-line)# password Ci$c0vty
R1(config-line)# exec-timeout 2 0
R1(config-line)# login
```

- 3.3. 禁用辅助端口。

```
R1(config)# line aux 0
R1(config-line)# no exec
```

- 3.4. 从 PC1 使用 Telnet 访问 R1 路由器。

```
PC1> telnet 192.168.0.1
```

- 4. 加密所有密码。

```
R1(config)# service password-encryption
```

### Part C: 使用 SSH 保护 VTY 线路的访问

- 1. 配置 SSH 连接。

使用以下选项配置 SSH 连接：

- 域名：tri.local；
- 用户名：sshadmin，密码：Ci$c0ssh；
- RSA 加密密钥为 1024 位；
- 使用的 SSH 版本为版本 2；
- 等待时间为 90 秒；
- 登录尝试次数为 3 次；
- 授权 SSH 和 VTY 会话。

- 2. 配置连接参数。

使用 "login block-for" 命令，如果在 _30 秒_ 内有两次连接尝试失败，则配置 _60 秒_ 的连接阻塞。

```
R1(config)#login block-for 60 attempts 2 within 30
```

### Part D: 使用“视图”管理保护访问

- 1. 使用加密密码“Us01paSS”创建新用户帐户“User01”。

```
R1(config)# username User01 secret Us01paS$
```

- 2. 在 R1 上激活“AAA”。

```
R1# config terminal
R1(config)# aaa new-model
R1(config)# exit
```

- 3. 创建“ViewRouter”视图。

```
R1#enable view
Password: (password enable)
R1#conf t
R1(config)# parser view ViewRouter
R1(config-view)#
```

- 4. 为该视图分配密码“ViewRouPs”。

```
R1(config-view)# secret ViewRouPs
```

- 5. 对于该视图，允许 exec 模式下的所有“show”命令。

```
R1(config-view)# commands exec include all show
```

- 6. 允许配置模式下的所有命令。

```
R1(config-view)# commands exec include all configure terminal
```

- 7. 允许路由器模式下的所有命令。

```
R1(config-view)# commands configure include all router
```

- 8. 按照相同步骤创建“ViewTelnet”视图，并赋予其以下选项：

- 密码 ViewTelPs；
- 授权命令：telnet, traceroute, show (全部)。

- 9. 访问 ViewRouPs 视图并测试配置。

```
R1#enable view ViewRouPs
Password:
Router#?
Exec commands:
configure Enter configuration mode
disable Turn off privileged commands
enable Turn on privileged commands
exit Exit from the EXEC
logout Exit from the EXEC
show Show running system information
```

对于 ViewTelnet 视图：

```
R1#enable view ViewTelnet
Password:
R1#?
Exec commands:
disable Turn off privileged commands
enable Turn on privileged commands
exit Exit from the EXEC
logout Exit from the EXEC
show Show running system information
telnet Open a telnet connection
traceroute Trace route to destination
```

- 10. 显示视图列表。

```
R1#show parser view all
Views/SuperViews Present in System:
ViewRouter
ViewTelnet
-----(*) represent superview------
```

- 11. 将“ViewRouter”分配给“User01”。

```
R1(config)#username User01 view ViewRouter
```

- 12. 创建带密码“$uperView1”的超级视图“SuperView1”。

```
R1#enable view
Password: (password enable)
R1(config)# parser view SuperView1 superview
R1(config-view)#secret $uperView1
```

- 13. 将“ViewRouter”和“ViewTelnet”视图分配给此超级视图。

```
R1(config-view)# view ViewRouter
R1(config-view)# view ViewTelnet
```

- 14. 显示视图列表。

```
R1#show parser view all
Views/SuperViews Present in System:
ViewRouter
ViewTelnet
SuperView1 *
-----(*) represent super-view-----
```

- 15. 将“SuperView1”分配给“User01”。

```
R1(config)#username User01 view SuperView1
```

### Part E: 保护配置文件和 IOS 系统

- 1. 显示闪存内容。

```
R1#show flash:
System flash directory:
File Length Name/status
  3  50938004 c2800nm-advipservicesk9-mz.124-15.T1.bin
  2  28282   sigdef-category.xml
  1  227537  sigdef-default.xml
[51193823 bytes used, 12822561 available, 64016384 total]
63488K bytes of processor board System flash (Read/Write
```

- 2. 通过在闪存中隐藏 IOS 映像文件来保护它。

```
R1(config)# secure boot-image
```

- 3. 保护闪存上的当前配置文件。

```
R1(config)# secure boot-config
```

- 4. 再次显示闪存内容。

```
R1#show flash:
System flash directory:
File Length Name/status
2 28282 sigdef-category.xml
1 227537 sigdef-default.xml
[51193823 bytes used, 12822561 available, 64016384 total]
63488K bytes of processor board System flash (Read/Write
```

- 5. 你能看到 IOS 映像文件吗？为什么？

............................................................................

- 6. 显示 Cisco IOS 映像和配置文件的存档状态。

```
R1# show secure bootset
IOS image resilience version 12.4 activated at 00:01:50 UTC mon. march 1 1993
Secure archive flash:/c2800nm-advipservicesk9-mz.124-15.T1.bin type is image (elf) file size is 50938004 bytes, run size is 50938004 bytes
Runnable image, entry point 0x8000F000, run from ram
IOS configuration resilience version 12.4 activated at 00:02:03 UTC mon. march 1 1993
Secure archive flash:/runcfg-19930301-000203.ar type is config configuration archive size 551 bytes
```

- 7. 配置从 ROMMON 启动并重新启动路由器。

```
R1(config)#config-register 0x2100
R1(config)#exit
R1#reload
Proceed with reload? [confirm]
```

- 8. 显示 ROMMON 模式下可用的安全文件。

```
rommon 1 > dir flash:
```





## 部分 F：使用自动化安全功能

| 文件大小 | 校验和 | 文件名 |
|---|---|---|
| 551 bytes (0x227) | 0x0227 | . runcfg-19930301-000203.ar |
| 50938004 bytes (0x3094094) | 0x439d | c2800nm-advipservicesk9-mz.124-15.T1.bin |
| 28282 bytes (0x6e7a) | 0x6e7a | sigdef-category.xml |
| 227537 bytes (0x378d1) | 0x78d4 | sigdef-default.xml |

- 9. 使用索引映像启动路由器。

```
rommon 2 > boot c2800nm-advipservicesk9-mz.124-15.T1.bin
```

- 10. 将受保护的配置还原到 Flash 中找到的归档文件。

```
R1(config)#secure boot-config restore flash: runcfg-19930301-000203.ar
```

- 1. 审查“Autosecure”脚本的使用。

..........................................................................

- 2. 启动“autosecure”脚本并按照说明操作。

```
R1#auto secure
```

## 监控计算机网络

本章将重点介绍以下主题：

- 实现网络时间协议 (NTP)：
  - 介绍，
  - 工作原理，
  - NTP 配置；
- 实现 Syslog 协议：
  - 介绍，
  - 工作原理，
  - Syslog 协议配置；
- 实现简单网络管理协议 (SNMP)：
  - 介绍，
  - 工作原理，
  - SNMP 配置。

### 3.1. 简介

管理平面包括网络监控协议的流量，在本例中为 Syslog 和 SNMP 协议。NTP 使同步网络元素上的时间成为可能，从而保证被监督元素数据的可靠性。

### 3.2. 实现 NTP 服务器

#### 3.2.1. NTP 简介

网络时间协议（NTP）使计算机网络中组件的本地时钟与参考服务器（互联网上的公共时间服务器或内部时间源）的时钟同步成为可能。

#### 3.2.2. NTP 的工作原理

##### 3.2.2.1. 不同的 NTP 层级

存在不同层级（或称为层）的 NTP 服务器，分别对应不同的规范。原子钟构成第 0 层（Stratum 0），并直接连接到第 1 层（Stratum 1）的服务器；这些服务器仅可被第 2 层或第 3 层的服务器访问。此外，其中一些服务器可自由访问。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_57_0.png)

图 3.1. 不同的 NTP 层级

##### 3.2.2.2. NTP 的通信模式

客户端可以使用多种模式来同步时钟：

- 客户端/服务器模式：客户端与服务器时间同步；
- 对称模式：优先级授予同步距离最短的站点。
- 多播模式：这使客户端能够从多个服务器获得响应。

#### 3.2.3. NTP 配置

##### 3.2.3.1. 配置 NTP 主服务器

要将路由器配置为 NTP 主路由器，请按以下步骤操作：

| 命令 | 描述 |
| :--- | :--- |
| Router(config)# ntp master stratum | 将路由器配置为 NTP 主服务器。层级数量为可选项。 |
| Router(config)# ntp authenticate | 激活 NTP 身份验证。 |
| Router(config)# ntp authentication-key key-number md5 key-value | 定义密钥 ID 和 NTP 密码，并使用 MD5 对其进行加密。 |
| Router(config)# ntp trusted-key key-number | 标识主服务器上的密钥。为了同步，NTP 客户端必须提供适当的密钥 ID 和密码。 |

##### 3.2.3.2. 配置 NTP 客户端

要将路由器配置为 NTP 客户端，请按以下步骤操作：

| 命令 | 描述 |
| :--- | :--- |
| Client(config)# ntp server ntp-server-address | 定义客户端将与之同步的 NTP 主路由器。 |
| Client(config)# ntp authentication-key key-number md5 key-value | 定义密钥 ID 和 NTP 密码，并使用 MD5 对其进行加密。 |
| Client(config)# ntp trusted-key key-number | 标识受信任密钥。 |

注意。—— 现在你可以尝试练习 3。

### 3.3. 实现 Syslog 服务器

#### 3.3.1. Syslog 简介

- Syslog 协议用于收集设备或应用程序生成的日志消息。这些消息有时可能是澄清某些设备故障原因的唯一方式。
- Syslog 消息通常发送到：
  - 控制台行；
  - 终端行；
  - Syslog 服务器。
- Syslog 服务器可用于执行以下任务：
  - 集中管理不同网络设备（路由器、交换机、服务器等）的所有日志文件；
  - 在安全位置存档日志，以便进行处理；
  - 对日志进行搜索和排序，以便于分析。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_59_0.png)

图 3.2. 在 Syslog 服务器上集中日志文件

#### 3.3.2. Syslog 的工作原理

##### 3.3.2.1. Syslog 严重性级别

严重性级别表示错误消息的性质。共有八个严重性级别，从 0 到 7，其中 0（零）为最严重，7 为最不严重。这些级别如下所述：

| 代码 | 严重性 | 描述 |
|---|---|---|
| 0 | 紧急 | 系统无法操作。 |
| 1 | 警报 | 需要立即干预。 |
| 2 | 严重 | 关键系统错误。 |
| 3 | 错误 | 操作错误。 |
| 4 | 警告 | 警告（如果不采取措施，可能会发生错误）。 |
| 5 | 通知 | 必须报告的正常事件。 |
| 6 | 信息 | 用于信息。 |
| 7 | 调试 | 调试消息。 |

##### 3.3.2.2. Syslog 消息的格式

- Syslog 格式的日志按顺序提供以下信息：Seq num:timestamp%FACILITY-SEVERITY-MNEMONIC: message：
- Seq num：表示事件的序列号。仅在执行了 service sequence-numbers 命令时，此信息才会出现。
- timestamp：表示事件发生的日期和时间。仅在运行了 service timestamps 命令时，此信息才会出现。必须注意的是，该命令默认处于激活状态；
- FACILITY：表示生成消息的组件、协议或进程。例如，SYS 表示操作系统，IF 表示接口，等等；
- SEVERITY：一个介于 0 和 7 之间的数字，表示所报告事件的严重程度；
- MNEMONIC：一个标识 Syslog 消息的代码；
- message：触发 Syslog 消息的事件的描述。
- 示例：待分析的 Syslog 消息如下。

```
39345: May 22 13:56:35.811: %LINEPROTO-5-UPDOWN: Line protocol on Interface Serial0/0/1, changed state to down
```

- Seq num：39345；
- Timestamp：May 22 13:56:35.811；
- FACILITY：LINEPROTO；
- SEVERITY 级别：5 (notification)；
- MNEMONIC：UPDOWN；
- 消息文本：Line protocol on Interface Serial0/0/1, changed state to down。

#### 3.3.3. 配置 Syslog 客户端

要将路由器配置为 Syslog 客户端，请按以下步骤操作：

| 命令 | 描述 |
|---|---|
| Router(config)# service timestamps log datetime msec | 在调试和日志消息上激活时间戳。 |
| Router(config)# logging host [ ip-address \| hostname ] | 标识 Syslog 服务器的地址或其主机名。 |
| Router(config)# logging trap level | 根据所需的严重级别限制发送到 Syslog 功能的消息。默认值为 6 (0 到 6)。 |
| Router(config)# logging on | 激活要记录的消息的发送。默认值为“on”。 |
| Router# show logging | 显示日志状态。 |

### 3.4. 实现简单网络管理协议 (SNMP)

#### 3.4.1. SNMP 简介

- 简单网络管理协议 (SNMP) 允许您远程监控、诊断和管理网络设备。
- SNMP 的目标可总结如下：
  - 监控网络性能并了解设备的总体状态（活动、非活动、部分运行、运行、网络拥塞等）；
  - 检测网络问题并管理异常事件（网络链路丢失、设备突然停止工作等）；
  - 配置设备。
- SNMP 在 OSI 模型的应用层工作，并使用端口 162 上的 UDP 协议。
- 许多软件包使用 SNMP 生成图表，以描绘网络流量或计算机系统的变化（Centreon、NetCrunch 5、MRTG 等）。

#### 3.4.2. SNMP 的工作原理

##### 3.4.2.1. SNMP 系统的组件

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_62_0.png)

图 3.3. SNMP 系统的组件

SNMP 系统由三个组件组成：

- SNMP 管理器：运行 SNMP 管理软件的主机。在大多数情况下，这是用于监控网络的计算机；
- SNMP 代理：运行在网络设备（路由器、交换机、服务器等）上的软件，使其能够被监控；
- 管理信息基 (MIB)：由 SNMP 代理管理的一组对象集合。每个集合包含一定数量的变量，可由 SNMP 管理器查询或修改。





##### 3.4.2.2. 管理信息库的结构

MIB 具有层次结构。每个对象都有一个标识符（OID），即一系列由点分隔的数字。这样可以为其分配唯一标识符。例如，1.3.6.1.2.1.2.2.1.2 是 ifDescr 的 OID。此值可用于描述网络接口（例如，思科路由器上的 FastEthernet0/0）。

最著名的 MIB 之一是 MIB-II，在 RFC 1213 中有描述。图 3.4 描绘了 MIB-II 的 OID 树的一部分。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_63_0.png)

**图 3.4.** MIB-II 的结构。有关本图的彩色版本，请参见 www.iste.co.uk/sadiqul/computer.zip

##### 3.4.2.3. SNMP 的不同版本

SNMP 有三个主要版本：SNMP 版本 1、SNMP 版本 2c 和 SNMP 版本 3。

- SNMPv1：这是原始版本，不建议在网络中使用，因为它存在安全漏洞。
- SNMPv2c：这是初始协议的更新版本，提供了某些改进。但是，它提供的安全性仅基于社区字符串，后者本质上是一个明文密码（未加密），容易受到黑客攻击。SNMPv2c 有两种社区字符串类型：
  - 只读 (RO)：此选项提供对 MIB 对象的只读访问。这是安全配置的推荐选项。
  - 读写 (RW)：此选项授予对 MIB 对象的读写权限。此方法提供修改网络元素配置的能力。
- SNMPv3：此版本有重大改进，旨在解决早期版本中存在的安全漏洞。社区字符串的概念已被新的安全功能取代。但是，尽管此版本提供了更好的安全性，SNMPv2c 仍然是使用最频繁的版本。

##### 3.4.2.4. SNMP 消息

SNMP 消息可用于执行以下操作：

- 搜索与 SNMP 代理相关的数据：SNMP 可使用以下消息搜索与代理链接的数据：
  - GET：此操作可从 MIB 元素提取值；
  - GetNext：可检索 MIB 元素的下一个值；
  - GetBulk：（SNMPv2c 及更高版本）SNMP 管理器使用此操作从 SNMP 代理高效检索大量数据；
- 修改与 SNMP 代理连接的数据：SNMP 可使用以下消息修改与代理连接的数据：
  - SET：此操作可为 MIB 元素定义值；
- 发送警报和通知：SNMP 还提供不同的通知（重定向）操作，SNMP 可使用这些操作向 SNMP 管理器发出重要事件警告：
  - Trap：当满足预设条件时，此通知用于向 SNMP 管理器 (NMS) 发送无需 SNMP 代理回执的消息；
  - Inform：用于向 SNMP 管理器发送带回执的消息。此功能在 SNMPv2c 中引入，以解决使用 Trap 时的回执问题。

#### 3.4.3. SNMP 配置

要配置路由器以使用 SNMP，请执行以下操作：

| Command | Description |
|---|---|
| Router(config)# snmp-server community name_community [ro|rw] | 配置“community”标识符及其访问级别（只读或读/写）。 |
| Router(config)# snmp-server enable traps name_traps | 激活 SNMP“trap”。 |
| Router(config)# snmp-server host IP address of agent name_community | 监督设备。 |
| Router# show snmp | 验证 SNMP 配置。 |

#### 3.5. 应用练习

### 练习 3。

### 拓扑

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_65_0.png)

有关本图的彩色版本，请参见 www.iste.co.uk/sadiqui/computer.zip

### 寻址表

| Device | Interface | IP address | Subnet Mask | Gateway |
|---|---|---|---|---|
| R1 | G0/0 | 192.168.0.1 | /24 | - |
| | S0/0 | 192.168.2.1 | /30 | - |
| R2 | G0/0 | 192.168.1.1 | /24 | - |
| | S0/0 | 192.168.2.2 | /30 | - |
| PC1 | NIC | 192.168.0.2 | /24 | 192.168.0.1 |
| NTP_syslog Server | NIC | 192.168.0.3 | /24 | 192.168.0.1 |
| PC2 | NIC | 192.168.1.2 | /24 | 192.168.1.1 |

### 目标

- 保护密码；
- 设置连接限制；
- 保护控制平面；
- 配置 NTP；
- 配置 syslog 协议。

### 使用的软件

- Packet Tracer。

### 部分 A：设置基本设备配置

- 1. 配置基本设备设置。
  - 1.1. 按拓扑图所示配置主机名。
  - 1.2. 根据寻址表将 IP 地址应用于设备接口。
  - 1.3. 将串行接口的时钟值设置为 128 000。

- 2. 使用 OSPF 协议配置路由。
  - 2.1. 在两台路由器上使用进程 ID 1 启用 OSPF。
  - 2.2. 将 R1 的 RID 值设置为 1.1.1.1，R2 的 RID 值设置为 2.2.2.2。
  - 2.3. 将所有网络添加到区域 0。
  - 2.4. 检查 PC1 和 PC2 之间的连通性。
  - 2.5. 使用“show ip ospf interface”命令显示为 s0/0 接口配置的身份验证类型。

```
R1# show ip ospf interface s0/0
Serial0 is up, line protocol is up
Internet Address 192.168.2.1/24, Area 0
...
...
Suppress hello for 0 neighbor(s)
Simple password authentication enabled
```

- 2.6. 解释下划线行的含义：

### 部分 B：保护密码

- 1. 设置最小密码长度为 8 个字符。

```
R1(config)# security passwords min-length 8
```

- 2. 配置特权模式密码。

```
R1(config)# enable secret Ci$c0ena
```

- 3. 配置控制台、辅助端口和虚拟访问线路。
  - 3.1. 为控制台端口设置密码，并将非活动间隔设置为 5 分钟。

```
R1(config)# line console 0
R1(config-line)# password Ci$c0con
R1(config-line)# exec-timeout 5 0
R1(config-line)# login
R1(config-line)# logging synchronous
```

  - 3.2. 在 VTY 线路上设置密码，并将非活动间隔设置为 2 分钟。

```
R1(config)# line vty 0 4
R1(config-line)# password Ci$c0vty
R1(config-line)# exec-timeout 2 0
R1(config-line)# login
```

  - 3.3. 禁用辅助端口。

```
R1(config)# line aux 0
R1(config-line)# no exec
```

- 4. 加密所有密码。

```
R1(config)# service password-encryption
```

### 部分 C：使用 SSH 保护对 VTY 线路的访问

- 1. 配置 SSH 连接。

使用以下选项配置 SSH 连接：

- 域名：tri.local；
- 用户名：sshadmin，密码：Ci$c0ssh；
- RSA 加密密钥为 1024 位；
- 使用的 SSH 版本为版本 2；
- 等待时间为 90 秒；
- 登录尝试次数为 3 次；
- 允许 SSH 和 VTY 会话。

- 2. 配置连接参数。

使用“login block-for”命令，如果在 30 秒内两次连接尝试失败，则阻止连接 60 秒。

```
R1(config)# login block-for 60 attempts 2 within 30
```

### 部分 D：保护控制平面

- 1. 复习控制平面的定义。

- 2. 为 OSPF 协议配置 MD5 身份验证。

  - 2.1. 在 R1 上激活 MD5 身份验证。

```
R1(config)# interface S0/0
R1(config-if)# ip ospf message-digest-key 1 md5 Ci$c0ospf
R1(config-if)# exit
R1(config)# router ospf 1
R1(config-router)# area 0 authentication message-digest
```

  - 2.2. 在 R2 上重复相同的配置。

- 2.3. 重复使用“show ip ospf interface”命令显示为 s0/0 接口配置的身份验证类型。

```
R1# show ip ospf interface s0/0
Serial0 is up, line protocol is up
Internet Address 192.168.2.1/24, Area 0
....
....
Suppress hello for 0 neighbor(s)
Message digest authentication enabled
Youngest key id is 1
```

- 2.4. 解释下划线行的含义：

### 部分 E：配置 NTP

- 1. 复习 NTP 的作用。

- 2. 配置 NTP 服务器。

在 NTP_Syslog 服务器上激活 NTP 服务。

- 3. 显示系统日期。

  - 3.1. 在 R1 上显示系统日期。

```
R1# show clock detail
```

  - 3.2. 根据上一命令的输出，填写以下表格：

| 日期 | |
|---|---|
| 时间 | |
| 时区 | |
| 时间源 | |

- 4. 将 R1 和 R2 配置为 NTP_Syslog 服务器的 NTP 客户端。

```
R1(config)# ntp server 192.168.0.3
R1(config)# ntp update-calendar
```





## 5. 验证 R1 上的 NTP 配置。

### 5.1. 显示 R1 上的系统日期。

```
R1# show clock detail
19:50:47.118 UTC Fri Jul 6 2018
Time source is NTP
```

### 5.2. 显示 NTP 配置设置。

```
R1#show ntp status
Clock is synchronized, stratum 2, reference is 192.168.0.3
nominal freq is 250.0000 Hz, actual freq is 249.9990 Hz, precision is 2**19
reference time is DEBF99EF.000001B3 (10:58:55.435 UTC Wed Jul 4 2018)
clock offset is 0.00 msec, root delay is 0.00 msec (millisecond)
root dispersion is 0.02 msec, peer dispersion is 0.02 msec.
```

## 6. 在 NTP 服务器上配置身份验证。

在 NTP Syslog 服务器上使用以下设置启用身份验证：

- 密钥：1；
- 密码：NTPpa00。

## 7. 在 R1 和 R2 上配置身份验证。

```
R1(config)# ntp authenticate
R1(config)# ntp trusted-key 1
R1(config)# ntp authentication-key 1 md5 NTPpa00
```

## 部分 F：配置 Syslog 协议

### 1. 重新定义 syslog 协议的角色。

### 2. 在调试和日志消息上启用时间戳。

```
R1(config)# service timestamps log datetime msec
```

### 3. 识别 Syslog 服务器的地址或其主机名。

```
R1# logging host 192.168.0.3
```

### 4. 激活要记录的消息的发送。

```
R1(config)# logging on
```

### 5. 将发送到 syslog 服务器的消息严重级别设置为值 7（调试）。

```
R1(config)# logging trap debugging
```

### 6. 显示日志状态。

```
R1# show logging
```

### 7. 检查消息是否已正确保存在 Syslog 服务器上。

| | 时间 | 主机名 | 消息 |
|---|---|---|---|
| 1 | jul. 04 18:58:56.182 | 192.168.0.100 | %SYS-5-CONFIG_I: Configured from console by c... |
| 2 | jul. 04 18:58:56.182 | 192.168.0.100 | *Jul, 04, 18:58:56.588: %SYS-6-LOGGINGHOST... |

### 8. 分析在 NTP Syslog 服务器上显示的消息。

根据以下消息填写表格：

```
<189>*Mar 1 00:18:20: %LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/1, changed state to up 192.168.100.1 04/07 22:27:59:280
```

| 序列号 | |
|---|---|
| 时间戳 | |
| 设施 | |
| 严重级别 | |
| 助记符 | |
| 消息 | |

## 练习 4。

### 拓扑

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_72_0.png)

此图的彩色版本，请参见 www.iste.co.uk/sadiqui/computer.zip

### 寻址表

| 设备 | 接口 | IP 地址 / 子网掩码 | 操作系统 | 网关 |
|---|---|---|---|---|
| R1 | G0/0 | 192.168.0.1/24 | c2600-adventerprisek9-mz.124-1 | - |
| | S0/0 | 192.168.2.1/30 | | - |
| R2 | S0/0 | 192.168.2.2/30 | c2600-adventerprisek9-mz.124-1 | - |
| PC1 | NIC | 192.168.0.2/24 | Windows 7 或更高版本 | 192.168.0.1 |

### 目标

- 保护密码；
- 实施连接限制；
- 保护控制平面；
- 配置 NTP；
- 配置 syslog 协议；
- 配置 SNMP。

### 使用的软件

- GNS3。

## 部分 A：设置基本设备配置。

### 1. 在设备上配置基本设置。

- 1.1. 按拓扑所示配置主机名。
- 1.2. 根据寻址表将 IP 地址应用到设备接口。
- 1.3. 将串行接口的时钟值设置为 128 000。

### 2. 使用 EIGRP 配置路由。

- 2.1. 在两台路由器上使用值 1 作为 AS ID 启用 EIGRP。
- 2.2. 将 R1 的 RID 值设置为 1.1.1.1，R2 设置为 2.2.2.2。
- 2.3. 将所有网络添加到 EIGRP。
- 2.4. 测试所有网络元素之间的连通性。

## 部分 B：保护密码

### 1. 设置最小密码长度为 8 个字符。

### 2. 为特权模式设置密码“Ci$c0ena”。

### 3. 配置控制台、辅助端口和虚拟访问线路。

- 3.1. 将“Ci$c0con”设置为控制台端口密码，并将非活动间隔设置为 5 分钟。
- 3.2. 将“C$c0vty”设置为 VTY 线路上的密码，并将非活动间隔设置为 2 分钟。
- 3.3. 禁用辅助端口。

### 4. 加密所有密码。

```
R1(config)# service password-encryption
```

## 部分 C：使用 SSH 保护对 VTY 线路的访问

### 1. 配置 SSH 连接。

使用以下选项配置 SSH 连接：

- 域名：tri.local；
- 用户名：sshadmin，密码：Ci$c0ssh；
- RSA 加密密钥为 1024 位；
- 使用的 SSH 版本为版本 2；
- 等待时间为 90 秒；
- 登录尝试次数为 3 次；
- 允许 SSH 和 Telnet 会话。

### 2. 配置连接参数。

使用“login block-for”命令配置连接，如果在 30 秒内有两次连接尝试失败，则连接将停止 60 秒。

## 部分 D：保护控制平面

### 1. 为 EIGRP 配置 MD5 身份验证。

- 1.1. 在 R1 上设置 EIGRP 密钥。

```
R1(config)#key chain EIGRP-SECRET
R1(config-keychain)# key 1
R1(config-keychain-key)# key-string Ci$eigrp
```

- 1.2. 在 R2 上重复相同的配置。

- 1.3. 设置 EIGRP 身份验证。

```
R1(config)#interface s0/0
R1(config-if)# ip authentication mode eigrp 1 md5
R1(config-if)# ip authentication key-chain eigrp 1 EIGRP-SECRET
```

- 1.4. 在 R2 上重复相同的配置。

- 1.5. 检查 R1 和 R2 之间是否建立了 EIGRP 邻居链路。

```
R1#show ip eigrp neighbors
EIGRP-IPv4 Neighbors for AS(1)
H Address Interface Hold Uptime SRTT RTO Q Seq
(sec) (ms) Cnt Num
0 192.168.2.2 s0/0 12 00:01:10 2000 5000 0 2
```

- 1.6. 确保已使用 MD5 加密建立身份验证：

```
R1#debug eigrp packets
*Mar 2 13:06:02.998: EIGRP: received packet with MD5 authentication, key id = 1
```

## 部分 E：配置 NTP

### 1. 设置 R1 路由器系统时间。

```
R1# clock set the_current_date
```

### 2. 将 R1 配置为 NTP 服务器。

```
R1(config)# ntp master 5
```

注：数字 5（层数）表示远离权威时间源的 NTP 区段数量。

### 3. 将 R2 配置为 NTP 客户端。

```
R2(config)# ntp server 192.168.2.1
R2(config)# ntp update-calendar
```

### 4. 检查 NTP 配置。

### 4.1. 显示 R2 上的系统日期。

```
R2# show clock detail
```

### 4.2. 检查 NTP 关联。

```
R2# show ntp associations
```

| 地址 | ref | clock | st | when | poll | reach | delay | offset | disp |
|---|---|---|---|---|---|---|---|---|---|
| *~192.168.2.1 | 127.127.1.1 | 5 | 11 | 64 | 177 | | 11.312 | -0.018 | 4.298 |

* sys.peer，# 选中，+ 候选，- 外围点，x 伪时钟，~ 已配置

## 部分 F：配置 Syslog 协议

### 1. 安装 Syslog 服务器。

下载并安装 tftpd32 服务器。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_76_0.png)

### 2. 在调试和日志消息上启用时间戳。

```
R1(config)# service timestamps log datetime msec
```

### 3. 配置 syslog 服务器的 IP 地址。

```
R1# logging host 192.168.0.1
```

### 4. 激活要记录的消息的发送。

```
R1(config)# logging on
```

### 5. 显示日志状态。

```
R1# show logging
```

```
...
No active filter modules.
Trap logging: level informational, 49 message lines logged
Logging to 192.168.0.1 (udp port 514, audit disabled,
link up),
6 message lines logged,
0 message lines rate-limited,
0 message lines dropped-by-MD,
...
```

### 6. 分析日志状态。

根据前一个命令的输出，填写下表：

| Syslog 服务器的 IP 地址 | |
|---|---|
| 配置的严重级别 | |
| Syslog 服务使用的端口 | |

### 7. 显示可用的不同严重级别。

```
R1(config)#logging trap?
<0-7> Logging severity level
alerts Immediate action needed (severity=1)
critical Critical conditions (severity=2)
debugging Debugging messages (severity=7)
emergencies System is unusable (severity=0)
errors Error conditions (severity=3)
informational Informational messages (severity=6)
notifications Normal but significant conditions (severity=5)
warnings Warning conditions (severity=4)
```





- 8. 复习将消息发送到 Syslog 服务器时配置的优缺点，严重性级别为 7（logging trap 7）。

- 9. 将严重性级别设置为 4（warnings）。

  R1(config)# logging trap warnings

- 10. 禁用并重新激活 S0/0 接口。

  R1(config-if)#shutdown
  R1(config-if)#no shutdown

- 11. 验证消息是否已正确记录在 Syslog 服务器上。

  <187>68: *3月 1 00:13:28.837: %LINK-3-UPDOWN: 接口 Serial0/0，
  状态更改为 up 192.168.0.1 07/07 22:35:33.869

基于此消息，填写以下信息：

| 序列号 | |
|---|---|
| 时间戳 | |
| 设备 | |
| 严重性 | |
| 助记符 | |
| 消息 | |

## G 部分：配置 SNMP

- 1. 复习 SNMP 的作用。

- 2. 复习 SNMP 系统的组件。

- 3. 配置 SNMP 管理器和 SNMP 代理。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_79_0.png)

此图的彩色版本，请参见 www.iste.co.uk/sadiqui/computer.zip

### 3.1. 安装 SNMP 管理器程序。

下载并安装 PowerSNMP 软件²。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_79_1.png)

### 3.2. 在 R1 上配置 SNMP 参数。

```
R1(config)#snmp-server community tri rw
R1(config)#snmp-server host 192.168.0.2 tri
R1(config)# snmp-server host 192.168.0.2 version 2c tri
```

### 3.3. 显示可用的“陷阱”列表。

```
R1(config)#snmp-server enable traps?
atm                  Enable SNMP atm traps
bgp                  Enable BGP traps
bstun                Enable SNMP BSTUN traps
bulkstat             Enable Data-Collection-MIB Collection notifications
cndp                 Enable NBAR Protocol Discovery traps
config               Enable SNMP config traps
config-copy          Enable SNMP config-copy traps
cpu                  Allow cpu related traps
dial                 Enable SNMP dial control traps
...
```

### 3.4. 在 SNMP 代理上启用所有“陷阱”。

```
R1(config)#snmp-server enable traps
```

### 3.5. 将 SNMP 管理器链接到 SNMP 代理。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_80_0.png)

### 3.6. 复习以下三种 SNMP 消息的定义：

- – 设置: ........................................................
- – 获取: ........................................................
- – 陷阱: .......................................................

### 3.7. 向 SNMP 代理发送“GET”请求以接收“sysName”值。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_81_0.png)

### 3.8. 为此 SNMP 请求填写以下元素：

- 此请求的 OID 值：........................................
- 访问类型：..................................................
- 此 SNMP 请求的值：....................................

> 注意.— 默认安装的基本 MIB 版本中，并非所有元素都可通过“get”命令访问。

### 3.9. 显示与记录的陷阱相关的信息。

## 使用 AAA 保护访问

本章将重点介绍以下主题：

- AAA 安全策略：
  - 身份验证，
  - 授权，
  - 可追溯性；
- AAA 身份验证类型：
  - 本地 AAA 身份验证，
  - 基于服务器的 AAA 身份验证；
- AAA 授权：
  - 简介，
  - 配置 AAA 授权；
- AAA 可追溯性：
  - 简介，
  - AAA 可追溯性的配置。

### 4.1. 简介

AAA（身份验证、授权、计费）是某些 Cisco 路由器中实施的安全策略，执行三个功能：身份验证、授权和可追溯性。具体如下：
- 身份验证：即验证用户或机器的身份；
- 授权：即确定用户对不同资源的权限；
- 可追溯性：即保留用户对资源使用情况的信息。

AAA 用户可以在路由器或交换机的本地主机上创建，也可以在外部服务器上创建（后者的额外优势是集中化访问配置）。

### 4.2. AAA 身份验证

#### 4.2.1. 本地 AAA 身份验证

本地身份验证可实现用户账户的简单快速管理。但是，当用户数量庞大时，此方法效率较低。

本地身份验证过程可总结如下：
- 1) 用户与路由器建立连接；
- 2) 路由器提示用户输入用户名和密码。随后从本地数据库验证用户身份。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_83_0.png)

图 4.1. 本地 AAA 身份验证过程

要将路由器配置为使用本地 AAA 身份验证，请执行以下操作：

| Command | Description |
|---|---|
| Router(config)# username username privilege level secret password | 在本地数据库中创建用户并为用户分配密码。 |
| Router(config)# aaa new-model | 创建新的 AAA 模型。 |
| Router(config)# aaa authentication login { default \| list-name } { method1 [ method2 ...]} | 定义访问控制台、VTY 或 AUX 线路时使用的身份验证方法。身份验证方法包括 local、local-case 和 Enable。 |
| Router(config)# aaa authentication username-prompt text-string | 将“用户名”消息替换为另一条消息。如果该消息包含空格，必须用双引号括起来。 |
| Router(config)# aaa authentication password-prompt text-string | 将“密码”消息替换为其他文本。 |
| Router(config)# aaa local authentication attempts max-fail number | 通过锁定超过预定义最大失败次数的账户来保护 AAA 账户。账户将保持锁定状态，直到管理员使用命令 clear aaa local user lockout 将其激活。 |

#### 4.2.2. 基于服务器的 AAA 身份验证

AAA 用户可以位于外部服务器上。可以基于 RADIUS 或 TACACS+ 协议使用两种类型的服务器：
- RADIUS 协议：基于 UDP 的开放协议；
- TACACS+ 协议：基于 TCP 的专有协议。

两种协议之间的区别包括：

| | Tacacs+ | Radius |
|---|---|---|
| 协议 | 端口 49 上的 TCP | UDP 端口：– 1812 或 1645 用于身份验证和授权；– 1813 或 1646 用于可追溯性 |
| 加密 | 加密所有信息 | 仅加密密码 |
| AAA 架构 | AAA 策略独立 | 结合身份验证和可追溯性 |
| 质询/响应 | 双向 | 单向 |
| 所有者 | Cisco 系统 | 开源 |

AAA 策略允许将用户集成到“Active directory”数据库中，以便受益于集中式管理。

使用服务器进行身份验证可总结如下：
- 1) 用户通过用户名和密码与路由器建立连接；
- 2) 路由器将用户标识符转发给外部 AAA 服务器；
- 3) AAA 服务器验证数据；
- 4) 路由器发送回连接结果并验证数据。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_85_0.png)

图 4.2. 基于服务器的身份验证

要将路由器配置为在服务器上使用 AAA 身份验证，请执行以下操作：

| Command | Description |
|---|---|
| R1(config)# tacacs-server host { hostname \| host-ip-address } [ key string ] [ port [ integer ] ] [ single-connection ] [ timeout [ seconds ] ] | 配置 TACACS+ 服务器的 IP 地址（或主机名）。其他参数为可选项。 |
| R1(config)# radius-server host { hostname \| host-ip-address } [ auth-port port-number ] [ acct-port port-number ] [ key password ] | 配置 RADIUS 服务器的 IP 地址（或主机名）。其他参数为可选项。 |

可选地，可以将服务器分组，以加速用户身份验证过程或确保负载冗余或平衡。





| 命令 | 描述 |
|---|---|
| Router(config)# aaa group server radius group-name | 对现有 RADIUS 主机服务器进行分组并使用它们。 |
| Router(config-sg-radius)# server ip-address [ auth-port port-number ] [ acct-port port-number ] | 为组服务器配置 RADIUS 服务器的 IP 地址。 |
| Router(config)# aaa group server tacacs+ group-name | 将现有 TACACS+ 主机服务器分组在一起。 |
| Router(config-sg-tacacs+)# server server-ip | 为组服务器配置 TACACS+ 服务器的 IP 地址。 |

### 4.3. AAA 授权

AAA 授权策略定义了用户在路由器或网络上的访问参数。

| 命令 | 描述 |
|---|---|
| Router(config)# aaa authorization { exec | network | commands level } { default list-name } { method1 [ method2 ...]} | 定义在访问以下模式时使用的授权策略：- exec，允许用户在此模式下运行命令；- network，设置与网络相关的授权访问请求，例如 PPP；- commands，为特定特权级别设置授权命令。 |

### 4.4. AAA 可追溯性

AAA 可追溯性使得可以在事件日志中记录用户执行的所有操作。通过这样做，可以查询日志以验证用户操作或识别给定操作的作者，以便在出现问题时迅速介入。AAA 支持六种不同的可追溯性类型：系统、网络、exec、commands、连接和资源。

### 4.5. 应用练习

练习 5.–

### 拓扑

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_87_0.png)

要查看此图的彩色版本，请参阅 www.iste.co.uk/sadiqui/computer.zip

### 寻址表

| 设备 | 接口 | IP 地址 | 子网掩码 | 网关 |
| :--- | :--- | :--- | :--- | :--- |
| R1 | G0/0 | 192.168.0.1 | /24 | – |
| | S0/0 | 192.168.2.1 | /30 | – |
| R2 | S0/0 | 192.168.2.2 | /30 | – |
| PC1 | NIC | 192.168.0.2 | /24 | 192.168.0.1 |
| AAA 服务器 | NIC | 192.168.0.3 | /24 | 192.168.0.1 |

### 目标

- 保护密码；
- 保护控制平面；
- 使用 AAA 保护管理访问。

### 使用的软件

Packet Tracer。

### 部分 A：配置基本设备设置。

### 1. 配置基本设备设置。

- 1.1. 按拓扑图所示配置主机名。
- 1.2. 根据寻址表将 IP 地址应用到设备接口。
- 1.3. 为串行接口设置时钟值为 128 000。

### 2. 使用 EIGRP 配置路由。

- 2.1. 在两台路由器上启用 EIGRP，SA ID 使用值 1。
- 2.2. 为 R1 设置 RID 值为 1.1.1.1，为 R2 设置 RID 值为 2.2.2.2。
- 2.3. 将所有网络添加到 EIGRP。
- 2.4. 测试所有网络元素之间的连通性。

### 部分 B：保护密码

- 1. 设置最小密码长度为 8 个字符。
- 2. 为特权模式设置密码“Ci$c0ena”。
- 3. 配置控制台、辅助端口和虚拟访问线路。
- 3.1. 将“Ci$c0con”设置为控制台端口密码，并将非活动间隔设置为 5 分钟。
- 3.2. 在 VTY 线路上设置密码“Ci$c0vty”，并将非活动间隔设置为 2 分钟。
- 3.3. 禁用辅助端口。
- 4. 加密所有密码。

```
R1(config)# service password-encryption
```

### 部分 C：保护控制平面

为 EIGRP 配置 MD5 身份验证。

- 1. 在 R1 上配置 EIGRP 密钥。

```
R1(config)#key chain EIGRP-SECRET
R1(config-keychain)# key 1
R1(config-keychain-key)# key-string Ci$eigrp
```

- 2. 在 R2 上重复相同的配置。
- 3. 实施 EIGRP 身份验证。

```
R1(config)#interface s0/0
R1(config-if)# ip authentication mode eigrp 1 md5
R1(config-if)# ip authentication key-chain eigrp 1 EIGRP-SECRET
```

- 4. 在 R2 上重复相同的配置。

### 5. 验证 R1 和 R2 之间是否已建立 EIGRP 邻居链路。

```
R1#show ip eigrp neighbors
EIGRP-IPv4 Neighbors for AS(1)
H Address Interface Hold Uptime SRTT RTO Q
Seq
(sec) (ms) Cnt Num
0 192.168.2.2 s0/0 12 00:01:10 2000 5000 0 2
```

### 6. 验证身份验证是否已使用 MD5 加密执行。

```
R1#debug eigrp packets
*Mar 2 13:06:02.998: EIGRP: received packet with MD5 authentication, key id = 1
```

### 部分 D：使用 AAA 保护管理访问

### 1. 回顾使用 AAA 管理访问的优势。

### 2. 使用本地数据库为访问控制台配置本地 AAA 身份验证。

### 2.1. 激活 AAA 服务。

```
R1(config)# aaa new-model
```

### 2.2. 配置身份验证方法，仅使用本地数据库。

```
R1(config)# aaa authentication login default local none
```

### 2.3. 创建密码为“@dmin012”的 Admin 用户。

```
R1(config)#username Admin privilege 15 secret @dmin012
R1(config)#exit
R1#exit
```

### 2.4. 通过 Telnet 连接到 Admin 账户。

### 3. 使用本地数据库为 Telnet 创建 AAA 身份验证配置文件。

3.1. 删除旧身份验证模式的配置。

```
R1(config)# no aaa authentication login default local none
```

3.2. 为路由器 Telnet 访问创建身份验证名称。

```
R1(config)# aaa authentication login TELNET_CON local
```

注.— “local” 参数用于在与“AAA”服务器连接失败时使用本地数据库。

3.3. 定义 Telnet 访问的身份验证名称。

```
R1(config)# line vty 0 4
```

```
R1(config-line)# login authentication TELNET_CON
```

3.4. 通过控制台连接到 Admin 账户。

```
PC1> telnet 192.168.0.1
```

3.5. 如何仍然可以连接到 R1？

### 4. 使用本地 AAA 服务器配置身份验证。

4.1. 在 AAA 服务器上：

- 激活 AAA 服务；
- 创建客户端“R1”，密码为“R@duis00”；
- 创建客户端“R2”，密码为“R@duis01”；
- 为客户端 R1 定义 IP 地址 192.168.0.1，为客户端 R2 定义 IP 地址 192.168.2.2；
- 将 AAA 服务器类型设置为 RADIUS；
- 创建两个用户：u1，密码为“P@ssuser1”；u2，密码为“P@ssuser2”。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_92_0.png)

### 4.2. 配置路由器以使用 AAA 服务器。

```
R1(config)# radius-server host 192.168.0.3 key R@duis00
R1(config)# aaa authentication login TELNET_CON group radius
local
```

### 4.3. 使用 Admin 账户通过 Telnet 连接到 R1。

```
PC1> telnet 192.168.0.1
```

### 4.4. 为什么现在无法再连接到 R1？

### 4.5. 使用 u1 账户通过 Telnet 连接到 R1。

### 4.6. 配置 R2 以使用 AAA 身份验证。

```
R2(config)# radius-server host 192.168.0.3 key R@duis01
R2(config)# aaa authentication login TELNET_CON group radius
local
R2(config)# line vty 0 4
R2(config-line)# login authentication TELNET_CON
```

### 4.7. 使用相同的 u1 账户通过 Telnet 连接到 R2。

```
PC1> telnet 192.168.2.2
```

### 4.8. 使用 AAA 服务器的优势是什么？

................................................................................................................

注.— 在本练习中，我们仅限于 AAA 身份验证。但是，读者可以通过添加与 AAA 授权和 AAA 可追溯性相关的部分来了解更多信息，例如使用 Cisco Secure ACS 服务器。




## 使用防火墙

本章将重点介绍以下主题：

- 防火墙的作用；
- 防火墙的类型：
  - NAT 防火墙，
  - 包过滤防火墙，
  - 有状态防火墙，
  - 应用防火墙；
- 配置防火墙；
- 不同的防火墙策略；
- 基于 ACL 的防火墙：
  - IPv4 ACL，
  - IPv6 ACL；
- 基于区域的防火墙：
  - 网络中的安全区域类型，
  - 应用于区域间流量的规则，
  - 配置 ZFW。

### 5.1 防火墙简介

防火墙是部署在可靠网络和不可靠网络之间的软件或硬件系统。部署防火墙的主要目的是过滤并阻止不需要的流量跨越防火墙屏障。为此，防火墙必须遵守以下建议：

- 它必须能抵御攻击；
- 它必须是两个网络之间唯一的中转点；
- 它必须确保组织的访问控制策略得到应用。

### 5.2 防火墙类型

有不同种类的防火墙。其中包括：

- NAT 防火墙：通过将私有 IP 地址转换为公共 IP 地址来隐藏它；
- 包过滤防火墙：可以过滤 OSI 模型第 3 层或第 4 层的数据包。此类防火墙配置简单，但也容易受到身份盗用攻击；
- 有状态防火墙：其功能与包过滤防火墙相同，同时跟踪网络连接状态（即 TCP 和 UDP 序列号），从而使其更安全；
- 应用防火墙（代理防火墙）：通常是一台服务器，用于对第 3、4、5 和 7 层中的信息进行此类过滤。

### 5.3 配置防火墙

配置防火墙的最佳实践包括：

- 将防火墙部署在安全边界以分隔不同的通信域；
- 仅允许必要服务的流量；
- 监控防火墙日志；
- 部署多种防火墙技术以提供全面的多层访问控制；
- 不要仅依赖单个防火墙来保障安全；
- 确保对防火墙的物理访问受到监控；
- 对防火墙配置实施变更管理。

### 5.4 不同的防火墙策略

通常，访问规则使用 ACL 实现。定义访问规则时，可以使用多个条件作为起点：

- 基于服务的规则：这些规则决定入站或出站流量可访问的服务类型。防火墙可根据 IP 地址和 TCP 端口号过滤流量。
- 基于方向的规则：这些规则决定对特定服务的请求可发起和授权的方向。
- 基于行为的规则：这些规则控制特定服务的使用方式。例如，防火墙可过滤电子邮件以消除垃圾邮件。

### 5.5 基于 ACL 的防火墙

#### 5.5.1 简介

访问控制列表是一组应用于地址或高层协议的授权或拒绝指令的有序集合。ACL 可以控制网络中的入站或出站流量。

#### 5.5.2 ACL 的位置

ACL 可以在两个方向上应用：

- 入站 ACL：路由器在将数据包发送到输出接口之前处理入站数据包。
- 出站 ACL：路由器将入站数据包定向到输出接口，然后通过应用出站 ACL 对其进行处理。

#### 5.5.3 IPv4 ACL

路由器支持两种类型的 IPv4 ACL。

标准 ACL：

- 仅根据源 IP 地址过滤 IP 数据包；
- 可以编号或命名；
- 有效编号范围为 1–99 和 1300–1999。

扩展 ACL：

- 根据源和目的 IP 地址、源和目的 UDP 和 TCP 端口以及 ICMP 消息类型等过滤 IP 数据包；
- 可以编号或命名；
- 有效编号范围包括 100–199 和 2000–2699。

配置标准 ACL，请按以下步骤操作：

| 命令 | 描述 |
|---|---|
| R1(config)# access-list number [deny\|permit] source [generic mask] | 创建编号的标准 ACL。 |
| R1(config)# ip access-list standard name_ACL | 创建命名的标准 ACL。 |
| R1(config-if)# ip access-group [ number \| name [ in \| out ] ] | 在接口上激活 ACL。 |

配置扩展 ACL，请按以下步骤操作：

| 命令 | 描述 |
|---|---|
| R1(config)# access-list number { deny \| permit } protocol source [generic mask] destination [generic mask] | 创建编号的扩展 ACL。 |
| R1(config)# ip access-list extended name_ACL | 创建命名的扩展 ACL。 |
| R1(config-if)# ip access-group {number\|name} {in\|out} | 在接口上激活 ACL。 |

#### 5.5.4 IPv6 ACL

IPv6 访问控制列表与 IPv4 访问控制列表类似，以下列出了一些特定功能：

| IPv4 访问控制列表 | IPv6 访问控制列表 |
|---|---|
| 标准<br>编号<br>命名<br>扩展<br>编号<br>命名 | 仅命名<br>作为 IPv4 扩展 ACL 访问控制列表。 |
| 使用通配符掩码 | 没有通配符掩码。 |
| IP access-group 命令可将 IPv4 访问控制列表应用到 IPv4 接口 | IPv6 使用 ipv6 traffic-filter 命令在 IPv6 接口上执行相同任务。 |
| 存在隐式 deny any 或 deny any 指令 | permit icmp any any nd-na<br>permit icmp any any nd-ns |

配置 IPv6 ACL，请按以下步骤操作：

| 命令 | 描述 |
|---|---|
| R1(config)# ipv6 access-list name | 创建 IPv6 ACL。 |
| R1(config-ipv6-acl) # {deny\|permit} protocol ipv6-source/CIDR [{eq\|neq\|gt\|lt\|range} port] ipv6-destination/CIDR [{eq\|neq\|gt\|lt\|range} port] | 配置 IPv6 ACL。 |
| R1(config)#interface type number<br>R1(config-if)#ipv6 traffic-filter name_ACL {in\|out} | 在接口上激活 IPv6 ACL。 |

#### 5.5.5 ACL 建议

实施 ACL 时，需要考虑以下要点：

- ACL 中的指令按顺序处理，同时考虑其顺序；
- 最具体的指令必须放在 ACL 的前几行；
- 默认情况下，现有 ACL 中的新指令将添加到最后几行；
- 必须确保最后一条指令是拒绝任何其他未指定的流量；
- 每个接口、每个协议或每个方向仅授权一个 ACL；
- 路由器生成的数据包不由出站 ACL 处理；
- 标准 ACL 必须放置在尽可能靠近目的地的位置；
- 扩展 ACL 必须放置在尽可能靠近源的位置。

注意：现在可以尝试练习 6。

### 5.6 基于区域的防火墙

#### 5.6.1 简介

基于策略的区域防火墙（ZFW）是基于 IOS 路由器的防火墙解决方案。这允许将不同类型的网络分隔到不同区域，从而保护网络免受外部威胁，并能够指定哪些流量可以从一个区域传递到另一个区域。该解决方案的主要优势之一是定义访问策略的简单性。

#### 5.6.2 网络中的安全区域类型

通常，组织网络中可应用三种安全区域：

- 内部区域：这是组织的生产网络。这是一个访问必须严格控制的区域。不得允许来自其他区域的直接、不受控制的访问；
- 外部区域：通常情况下，这对应于 Internet。这是一个不安全的区域，对组织的内部网络构成持续威胁；
- DMZ（非军事化）区域：这是一个用于实现对某些服务器（Web 消息传递服务等）的基于 Internet 的访问，同时避免与内部网络任何直接连接的区域。此区域存在多种安全漏洞风险，并要求对以下流量实施严格访问控制：
  - 来自 Internet 到 DMZ 区域主机的入站流量；
  - 来自 DMZ 区域主机到 Internet 的出站流量；
  - 来自内部网络到 DMZ 区域主机的入站流量；
  - 来自 DMZ 区域主机到内部网络的出站流量。



![](img/6cc1cc8bbb23ba3014958aee841c4ff5_100_0.png)

## 图 5.1. 不同类型网络划分至独立区域

#### 5.6.3. 应用于区域间流量的规则

路由流量时，会对 ZFW 应用以下规则：

- 必须先创建安全区域，然后才能为其分配接口；
- 一个接口可以分配给单个安全区域；
- 默认情况下，属于同一区域的接口之间允许流量；

必须预先配置安全策略，才能授权流量在两个区域之间传递。可采取三种操作：

- **放行**：允许流量从一个区域 transite 到另一个区域；
- **检查**：允许流量并检查返回流量；
- **丢弃**：删除流量；

除非明确禁止，否则任何指向路由器接口（“自身区域”）的流量均获授权。

#### 5.6.4. 术语

ZFW 的访问策略需要三个基本组件：

- 类映射：允许根据某些条件识别流量；
- 策略映射：允许应用先前创建的“类映射”策略；
- 服务策略：允许定义应用先前创建的策略映射的位置。

#### 5.6.5. 配置 ZFW

可按以下步骤依次配置 ZFW：

- 1) 创建区域；
- 2) 创建类映射以识别授权流量；
- 3) 创建策略映射以应用类映射；
- 4) 定义区域对；
- 5) 将策略映射应用到区域对；
- 6) 将接口分配给区域。

### 5.7. 创建区域

| Command | Description |
|---|---|
| Router(config)# zone security zone-name | 创建安全区域。 |

### 5.8. 创建类映射

| Command | Description |
|---|---|
| Router(config)# class-map type inspect { match-any | match-all } class-map-name | 创建类映射并定义这些选项。match-any：数据包必须满足其中一条匹配条件。match-all：数据包必须满足所有匹配条件。 |
| Router(config-cmap)# match protocol protocol | 根据协议定义匹配条件。 |

### 5.9. 创建应用类映射的策略映射

| Command | Description |
|---|---|
| Router(config)# policy-map type inspect policy-map-name | 创建策略映射并定义这些选项。 |
| Router(config-pmap)# class type inspect class-map-name | 将其与一个（或多个）类映射关联。 |
| Router(config-pmap-c)# {drop | inspect | pass } | 定义要执行的操作。 |

### 5.10. 定义区域对

| Command | Description |
|---|---|
| Router(config)# zone-pair security zone-pair-name source { source-zonename | self | default } destination { destination-zone-name | self | default } | 创建区域对，允许在两个区域之间应用单向“策略映射”。 |

### 5.11. 将策略映射应用到区域对

| Command | Description |
|---|---|
| Router(config-sec-zone-pair)# service-policy type inspect policymap-name | 将策略映射策略应用到区域对。 |

### 5.12. 将接口分配给区域

| Command | Description |
|---|---|
| Router(config)# interface type number<br>Router(config-if)# zone-member security zone-name | 将接口与特定安全区域关联。 |

### 5.13. 应用练习

练习 6.

### 拓扑

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_103_0.png)

有关此图的彩色版本，请参见 www.iste.co.uk/sadiqui/computer.zip

### 寻址表

| 设备 | 接口 | IP 地址 | 子网掩码 | 网关 |
|---|---|---|---|---|
| R1 | G0/0 | 192.168.0.1 | /24 | – |
| | S0/0 | 192.168.100.1 | /30 | – |
| R2 | G0/0 | 192.168.1.1 | /24 | – |
| | S0/0 | 192.168.100.2 | /30 | – |
| | S0/1 | 192.168.200.1 | /30 | – |
| R3 | G0/0 | 192.168.2.1 | /24 | – |
| | S0/0 | 192.168.200.2 | /30 | – |
| PC1 | NIC | 192.168.0.2 | /25 | 192.168.0.1 |
| PC2 | NIC | 192.168.1.2 | /26 | 192.168.1.1 |
| PC3 | NIC | 192.168.2.4 | /24 | 192.168.2.1 |
| PC4 | NIC | 192.168.2.5 | /24 | 192.168.2.1 |
| ftp_server | NIC | 192.168.2.2 | /24 | 192.168.2.1 |
| http-server | NIC | 192.168.2.3 | /24 | 192.168.2.1 |

## 目标

- 保护密码；
- 配置 IPv4 ACL；
- 配置 IPv6 ACL。

## 要使用的软件

Packet Tracer.

## A 部分：建立基本设备配置。

### 1. 配置基本设备设置。

- 1.1. 按拓扑配置主机名。
- 1.2. 根据寻址表将 IP 地址应用到设备接口。
- 1.3. 将串行接口的时钟值设置为 128 000。

### 2. 使用 OSPF 协议配置路由。

- 2.1. 在两台路由器上启用 OSPF，进程 ID 使用值 1。
- 2.2. 将 RID 值设置为 R1 的 1.1.1.1、R2 的 2.2.2.2 和 R3 的 3.3.3.3。
- 2.3. 将所有网络添加到 OSPF 协议。
- 2.4. 测试所有网络元素之间的连通性。

## B 部分：保护密码

- 1. 设置最小密码长度为 8 个字符。
- 2. 为特权模式设置密码“Ci$c0ena”。
- 3. 配置控制台、辅助端口和虚拟访问线路。
- 3.1. 将“Ci$c0con”设置为控制台端口密码，并将非活动间隔设置为 5 分钟。
- 3.2. 将“Cis$c0vty”设置为 VTY 线路的密码，并将非活动间隔设置为 2 分钟。
- 3.3. 禁用辅助端口。
- 4. 加密所有密码；

```
R1(config)# service password-encryption
```

## C 部分：配置 IPv4 ACL

- 1. 审查编号扩展 ACL 的有效编号范围。
- 2. 在 R3 上，创建一个编号扩展 ACL，以授权来自 PC1 站对 http-server 的访问。为此，使用以下选项创建 ACL：
  - 扩展列表编号为 100
  - 要定义的操作为 permit；
  - 要使用的协议为 TCP；
  - 源为 IP 地址为 192.168.0.2 的主机（PC1）；
  - 目标为 IP 地址为 192.168.2.2 的主机（http-server）；
  - 要使用的端口为 80。

编写要使用的 ACL：

- 3. 向已创建的扩展 ACL 添加一条规则，以拒绝来自“站点 2”网络对 http-server 的访问。为此，按以下选项配置 ACL 100：
  - 要定义的操作为 deny；
  - 要使用的协议为 TCP；
  - 源为网络地址为 192.168.1.0 / 26 的网络（站点 2）；
  - 通配符掩码通过从网络掩码中减去掩码 255.255.255.255 获得：
  255.255.255.255 – 255.255.255.192 = 0.0.0.63
  - 目标为 IP 地址为 192.168.2.3 的主机（http-server）；
  - 要使用的端口为 80。

编写要使用的命令：

- 4. 向之前的 ACL 添加一条规则，允许与 http-server 的所有 IP 流量。为此，按以下选项配置 ACL 100：
  - 要定义的操作为 permit；
  - 要使用的协议为 IP；
  - 要使用的源为 any；
  - 目标为 IP 地址为 192.168.2.3 的主机（http-server）。

编写要使用的命令：

- 5. 向之前的 ACL 添加一条规则，允许拒绝 PC1 和 PC4 之间的 ICMP 流量。为此，按以下选项配置 ACL 100：
  - 要定义的操作为 permit；
  - 要使用的协议为 ICMP；
  - 要使用的源为 IP 地址为 192.168.0.2 的主机（PC1）；
  - 目标为 IP 地址为 192.168.2.4 的主机（PC4）。

编写要使用的命令：

- 6. 将访问控制列表 100 应用到 G0/0 接口。

编写要使用的命令：

注释。—— 通常，扩展 ACL 应放置在源附近。但是，由于 ACL 100 影响来自两个网络“站点 1”和“站点 2”的流量，最佳位置应为接口 G0/0 的输出方向。

- 7. 测试先前创建的 ACL。
  - 检查是否可以从 PC1 访问 http 服务。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_107_0.png)
  - 检查是否无法从 PC2 访问 http 服务。
  - 检查是否可以从 PC2 向 http-server 发送 ping 请求。
  - 检查是否无法从 PC1 向 PC3 发送 ping 请求。
  - 检查是否可以从 PC1 向 PC4 发送 ping 请求。

- 8. 删除创建的 ACL。

```
R3(config)# no access-list 100
```

- 9. 在 R3 上，创建并测试名为“ACL_HTTP”的扩展 ACL，以满足先前所述的安全要求。

- 9.1. 创建扩展 ACL。

```
R3(config)# ip access-list extended ACL_HTTP
R3(config-ext-nacl)#
```

- 9.2. 允许从 PC1 到 http-server 的 http 访问

```
R3(config-ext-nacl)# permit tcp host 192.168.0.2 host 192.168.2.3 eq www
```




### 9.3. 禁止来自网络“site 2”到 http-server 的 HTTP 流量。

```
R3(config-ext-nacl)# deny tcp 192.168.1.0 0.0.0.63 host 192.168.2.3 eq www
```

### 9.4. 允许与 http-server 的所有 IP 流量。

```
R3(config-ext-nacl)#permit ip any host 192.168.2.3
```

### 9.5. 显示 ACL_HTTP ACL 规则。

```
R3#sh IP access-lists ACL_HTTP
```

### 9.6. 将 ACL_HTTP ACL 应用到 G0/0/0 接口。

```
R3(config-if)# ip access-group ACL_HTTP out
```

### 9.7. 测试 ACL_HTTP ACL 的效果。

### 10. 在 R3 上，创建一个名为“ACL_FTP”的扩展 ACL，以满足以下安全要求：

- 允许从 PC2 到 ftp_server 的 FTP 访问；
- 阻止来自“site 1”网络到 ftp_server_http 的 FTP 流量；
- 允许与 ftp_server 的所有 IP 流量。

### 10.1. 显示 ACL_FTP ACL 规则。

### 10.2. 将 ACL_FTP ACL 应用到 G0/0 接口。

### 10.3. 测试 ACL_FTP ACL 的效果。

```
PC2:\>ftp 192.168.2.3
Trying to connect... 192.168.2.3
Connected to 192.168.2.3
220- Welcome to PT Ftp server
Username: cisco
331- Username ok, need password
Password: **** (cisco)
230- Logged in
(passive mode On)
ftp>
```

## 部分 D：配置 IPv6 ACL

### IPv6 寻址表

| 设备 | 接口 | IP 地址 | 网关 |
|---|---|---|---|
| R1 | G0/0 | 2001:DB8:AAAA:A::1/64 | – |
| | S0/0 | 2001:DB8:AAAA:D::1/64 | – |
| R2 | G0/0 | 2001:DB8:AAAA:B::1/64 | – |
| | S0/0 | 2001:DB8:AAAA:D::2/64 | – |
| | S0/1 | 2001:DB8:AAAA:E::1/64 | – |
| R3 | G0/0 | 2001:DB8:AAAA:C::1/64 | – |
| | S0/0 | 2001:DB8:AAAA:E::2/64 | – |
| PC1 | NIC | 2001:DB8:AAAA:A::2/64 | FE80::1 |
| PC2 | NIC | 2001:DB8:AAAA:B::2/64 | FE80::1 |
| PC3 | NIC | 2001:DB8:AAAA:C::4/64 | FE80::1 |
| PC4 | NIC | 2001:DB8:AAAA:C::5/64 | FE80::1 |
| ftp_server | NIC | 2001:DB8:AAAA:C::2/64 | FE80::1 |
| http-server | NIC | 2001:DB8:AAAA:C::3/64 | FE80::1 |

- 1. 创建一个与之前练习中相同拓扑的新模板

- 2. 在 R1、R2 和 R3 上配置基本参数。

- 2.1. 按拓扑图所示配置主机名。

- 2.2. 根据寻址表将 IP 地址应用到路由器接口。

注意：路由器的本地链路地址将设置为 FE80::1/64。

- 2.3. 将串行接口的时钟值设置为 128000。

- 3. 使用 OSPF 协议配置路由。

- 3.1. 在两台路由器上使用进程 ID 1 启用 OSPF。

- 3.2. 为 R1 设置 RID 为 1.1.1.1，为 R2 设置为 2.2.2.2，为 R3 设置为 3.3.3.3。

- 3.3. 将所有网络添加到 OSPF 协议。

- 3.4. 测试所有网络元素之间的连通性。

- 4. 在 R3 上，创建并激活一个名为“ACL_HTTP”的扩展 ACL，以满足第 1 部分中定义的所有安全要求。

写出要使用的命令：
......................................................................................
......................................................................................
......................................................................................

- 5. 在 R3 上，创建一个名为“ACL_FTP”的扩展 ACL，以满足第 1 部分中定义的安全要求。
......................................................................................
......................................................................................
......................................................................................

- 6. 测试所创建 ACL 的效果。

## 练习 7.

### 拓扑

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_110_0.png)

### 寻址表

| 设备 | 接口 | IP 地址 | 子网掩码 | 网关 |
|---|---|---|---|---|
| R1 | G0/0 | 192.168.0.1 | /24 | – |
| | G0/1 | 192.168.1.1 | /24 | – |
| | S0/0 | 192.168.100.1 | /30 | – |
| | S0/1 | 192.168.200.1 | /30 | – |
| R2 | G0/0 | 192.168.10.1 | /24 | – |
| | S0/0 | 192.168.100.2 | /30 | – |
| R3 | G0/0 | 192.168.20.1 | /24 | – |
| | S0/0 | 192.168.200.2 | /30 | – |
| PC1 | NIC | 192.168.0.2 | /24 | 192.168.0.1 |
| PC2 | NIC | 192.168.10.2 | /24 | 192.168.10.1 |
| ftp_server | NIC | 192.168.1.2 | /24 | 192.168.1.1 |
| http-server | NIC | 192.168.1.3 | /24 | 192.168.1.1 |
| http2-server | NIC | 192.168.20.2 | /24 | 192.168.20.1 |

### 目标

配置基于区域的防火墙。

### 使用的软件

Packet tracer.

### 部分 A：建立基本设备配置。

- 1. 配置基本设备设置。

- 1.1. 按拓扑图所示配置主机名。

- 1.2. 根据寻址表将 IP 地址应用到设备接口。

- 1.3. 将串行接口的时钟值设置为 128000。

- 2. 使用 OSPF 协议配置路由。

- 2.1. 在路由器上使用进程 ID 1 启用 OSPF。

- 2.2. 为 R1 设置 RID 值为 1.1.1.1，为 R2 设置为 2.2.2.2，为 R3 设置为 3.3.3.3。

- 2.3. 将所有网络添加到 OSPF 协议。

- 2.4. 测试所有网络元素之间的连通性。

### 部分 B：配置基于区域的防火墙

- 1. 回顾 DMZ 区域的定义。

- 2. 在 R1 上创建安全区域。

- 2.1. 创建名为 IN-ZONE 的内部区域。

```
R1(config)# zone security IN-ZONE
R1(config-sec-zone)# exit
```

- 2.2. 创建名为 DMZ-ZONE 的 DMZ 区域。

```
R1(config)# zone security DMZ-ZONE
R1(config-sec-zone)# exit
```

- 2.3. 创建名为 OUT-ZONE 的外部区域。

```
R1(config)# zone security OUT-ZONE
R1(config-sec-zone)# exit
```

- 2.4. 创建名为 HEAD-ZONE 的外部区域。

```
R1(config)# zone security HEAD-ZONE
R1(config-sec-zone)# exit
```

- 3. 创建 Class-Maps 以识别授权流量。

- 3.1. 创建 CMAP-IN-TO-DMZ Class-Map。

```
R1(config)# class-map type inspect match-any CMAP-IN-TO-DMZ
```

- 3.2. 允许 http、ftp 和 icmp 协议。

```
R1(config-cmap)# match protocol http
R1(config-cmap)# match protocol ftp
R1(config-cmap)# match protocol icmp
R1(config-cmap)# exit
R1(config)# exit
```

- 3.3. 创建 CMAP-IN-TO-HEAD Class-Map。

```
R1(config)# class-map type inspect match-any CMAP-IN-TO-HEAD
```

- 3.4. 允许 http 和 icmp 协议。

```
R1(config-cmap)# match protocol http
R1(config-cmap)# match protocol icmp
R1(config-cmap)# exit
R1(config)# exit
```

- 3.5. 创建 CMAP-OUT-TO-DMZ Class-Map。

```
R1(config)# class-map type inspect match-any OUT-TO-DMZ
```

- 3.6. 仅允许 http 协议。

```
R1(config-cmap)# match protocol http
R1(config-cmap)# exit
R1(config)# exit
```

- 4. 创建 Policy-Maps 以将访问规则应用到 Class-Map。

- 4.1. 回顾应用于区域间流量的三条规则的定义。

- - 通过：................................................................................

- - 检查：

- - 丢弃：

- 4.2. 创建 Policy-Map 以将 Class-Map CMAP-IN-TO-DMZ 应用。

```
R1(config)# policy-map type inspect PMAP-IN-TO-DMZ
R1(config-pmap)# class type inspect CMAP-IN-TO-DMZ
R1(config-pmap-c)# pass
```

- 4.3. 同样，创建以下 Policy-Maps：

- - 针对 Class-Map CMAP-OUT-TO-DMZ 的 PMAP-OUT-TO-DMZ；
- - 针对 Class-Map CMAP-IN-TO-HEAD 的 PMAP-IN-TO-HEAD。

- 5. 定义区域对。

- 5.1. 在 IN-ZONE 和 DMZ-ZONE 之间创建一个应用 PMAP-IN-TO-DMZ 策略的区域对。

```
R1(config)# zone-pair security IN-to-DMZ source IN-ZONE destination DMZ-ZONE
R1(config-sec-zone-pair)# service-policy type inspect PMAP-IN-TO-DMZ
```

- 5.2. 同样，创建以下区域对：

- - OUT-to-DMZ，应用 PMAP-OUT-TO-DMZ 策略；
- - IN-to-HEAD，应用 PMAP-IN-TO-HEAD 策略。

- 6. 将接口分配到区域。

```
R1(config)# interface G0/0
R1(config-if)# zone-member security IN-ZONE
R1(config)# interface G0/1
R1(config-if)# zone-member security DMZ-ZONE
R1(config)# interface S0/0
R1(config-if)# zone-member security OUT-ZONE
R1(config)# interface S0/1
R1(config-if)# zone-member security HEAD-ZONE
```

- 7. 验证 R1 的配置。

使用 “show running-config” 命令，验证配置的所有参数。

- 8. 测试防火墙的配置。

- – 确保可以从 PC1 和 PC2 访问 http-server。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_115_0.png)

- – 检查是否只能从 PC1 访问 http2-server。

- – 检查是否只能从 PC1 访问 ftp-server 服务。

```
PC1> ftp 192.168.1.3
```

- – 检查是否可以从 PC1 向 http-server 发送 ping 请求。

- – 检查是否无法从 PC2 向 http-server 发送 ping 请求。

- – 检查是否可以从 PC1 向 PC2 发送 ping 请求。





## 构建入侵防御系统（IPS）

本章将重点介绍以下主题：
- 探测器的作用；
- IDS 与 IPS 的区别；
- IPS 的类型：
  - 基于主机的 IPS，
  - 基于网络的 IPS；
- 使用 IPS 的模式：
  - 混杂模式，
  - 内联模式；
- 警报的类型；
- 检测恶意流量的模式：
  - 基于签名的检测，
  - 基于策略的检测，
  - 基于异常的检测，
  - 基于声誉的检测；
- 签名的严重级别；
- 警报和警示的监控与管理；
- 攻击期间应采取的行动列表；
- IOS IPS 的配置。

### 6.1. 探测器简介

探测器是一种网络设备，它根据预定义规则分析网络流量，以将其归类为正常流量或恶意流量。

入侵检测系统（IDS）是一种探测器，可分析通过一个或多个网络连接传输的数据包，以检测可疑活动。其作用仅限于向系统管理员发出关于主机或网络上任何异常活动痕迹的警报。它不防止入侵尝试。

入侵防御系统（IPS）是一种探测器，可以检测并防止针对主机或网络的任何潜在攻击。

### 6.2. IDS 与 IPS 的区别

下表列出了两种探测器（IPS 和 IDS）的一些特性：

| | IDS | IPS |
|---|---|---|
| 处理数据包 | 仅接收原始数据包的一个副本进行处理。 | 在数据包到达网络或主机之前，系统会处理所有数据包。 |
| 对延迟的影响 | 原始流量无延迟。 | 流量发送到网络之前会有轻微延迟。 |
| 系统停止服务时造成的影响 | 无负面影响。 | 通过系统的所有流量可能会受到负面影响。 |
| 保护网络的能力 | 对恶意流量无保护。 | IPS 可以根据一套预先建立的规则保护流量。 |

注释。——第 6.3 节将重点介绍 IPS 探测器。

### 6.3. IPS 的类型

根据 IPS 在网络中的部署位置，它可以部署在主机（Host-IPS 或 HIPS）或整个网络（Network-IPS 或 NIPS）以进行保护。每种类型都有其优缺点。

| | 优点 | 缺点 |
|---|---|---|
| Host-IPS | 可以保护特定主机。可以保护操作系统和应用程序。 | 依赖于操作系统。必须在所有主机上安装。 |
| Network-IPS | 更经济的解决方案。独立于操作系统。 | 无法检查加密流量。 |

### 6.4. Cisco IP 解决方案

Cisco 提供的 IPS 解决方案设计旨在适应不同环境，并提供高可用性和高效率。

部署选项包括专用设备、交换机和路由器的 IPS 模块以及基于软件的解决方案。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_118_0.png)

图 6.1. 可集成到路由器1中的 AIP-SSM 模块（一种模块化 IPS）。有关此图的彩色版本，请参阅 www.iste.co.uk/sadiqui/computer.zip

### 6.5. 部署 IPS 的模式

IPS 可以部署在两种模式下：

- 混杂模式：IPS 仅限于分析网络流量并报告异常（即 IPS 扮演 IDS 的角色）；
- 内联模式：流量被定向到 IPS 进行分析。IPS 根据预配置的参数阻止部分流量。

¹ Cisco Networking Academy（Cisco 官方培训网站）可在以下网址找到：https://www.netacad.com。

### 6.6. 警报的类型

网络攻击可能会生成四种类型的警报，编码如下：

| 真正例 | 由已发生且被 IPS 检测到的入侵触发的警报。 |
|---|---|
| 真负例 | 未发生入侵，且 IPS 未采取任何操作。 |
| 假正例 | 正常流量或无关紧要的操作触发了警报。 |
| 假负例 | 发生入侵时未触发任何警报。 |

管理员需要确保对“假正例”警报进行调整，并对“假负例”警报进行更正。

注释。——现在你可以尝试练习 8。

### 6.7. 检测恶意流量

#### 6.7.1. 检测模式

IPS 可以使用多种方法检测恶意流量，包括基于签名的检测、基于策略的检测、基于异常的检测和基于声誉的检测。

#### 6.7.2. 基于签名的检测

##### 6.7.2.1. 签名定义

签名是配置在入侵防御系统上的一组规则，用于检测入侵。Cisco 已将具有相似特征的签名分组到各个类别中，以便于管理和分析。

##### 6.7.2.2. 签名的类型

存在两种类型的签名：

- 原子：尝试访问特定主机上的特定端口，且恶意内容包含在单个数据包中；
- 复合：在任意一段时间内分布在多个主机上的一系列操作。

##### 6.7.2.3. 此检测模式的特性

通常，基于签名的检测是 Cisco 入侵防御/检测系统中识别恶意软件最常用的方法。

优点：

- 易于配置和实现；
- 默认情况下，IPS 包含多个预安装的签名；
- 可以下载并实施其他附加签名，以缓解新类型的攻击。

缺点：

- 不检测超出预定义规则范围的攻击。
- 可能会生成“假正例”警报；
- 签名必须定期更新。

#### 6.7.3. 检测恶意流量的其他模式

##### 6.7.3.1. 基于策略的检测

根据网络安全策略在 IPS 上创建和配置策略。检测到的超出此策略的任何流量都将生成警报和/或被阻止。

优点：

- 简单、可靠且高度可定制；
- 仅允许基于网络安全策略的流量，这可能防止未知攻击。

缺点：

- 策略必须手动创建；
- 在大型网络中难以应用。

##### 6.7.3.2. 基于异常的检测

IPS 通常会查找偏离常态的网络流量。必须开发统计参考来定义网络流量的正常行为。

优点：可以检测新类型的攻击。

缺点：

- 在极大型网络上难以准确标准化流量；
- 如果有效网络流量发生显著变化，可能会引起“假正例”警报。

##### 6.7.3.3. 基于声誉的检测

Cisco 全局关联是一项功能，允许 Cisco IPS 探测器使用数据包源 IP 地址的“声誉”来过滤网络流量。

IP 地址的声誉（以及其他因素）由“Cisco SensorBase”服务根据该 IP 地址的先前行为进行计算，该服务专门从事此领域。这些信息从全球部署的超过 150 万台 Cisco IPS 探测器和防火墙等设备的流量中收集。此功能为网络提供有价值的信息，有助于检测、防止和应对最近发现的威胁。

优点：

- 利用其他现有安全系统的经验；
- 被视为早期预警系统。

缺点：需要持续更新。

### 6.8. 签名微引擎

签名微引擎是 IPS（或 IDS）探测器中支持特定签名类别的组件。来自签名微引擎的所有签名均并行扫描，这提高了数据的效率和流畅性。





签名微引擎执行以下操作：

- 为一类签名分配一组范围或可接受值；
- 使用路由器内存来编译、加载和合并签名。

思科为这些微引擎使用的几类签名定义了分类，包括：

| 签名类别 | 描述 |
|---|---|
| Atomic | 支持检查简单数据包。 |
| Service | 支持检查系统是否正在受到攻击。 |
| String | 支持检查多种协议的数据包，同时指定必须验证的表达式以触发签名。 |
| Multi-string | 支持通过指定一系列必须验证的表达式来检查数据包，以便触发签名。 |

注：还有其他类别的签名，可用于检查其他类型的流量。

### 6.9. 签名严重性级别

IPS 签名数据库中的每个签名都与一个严重性级别相关联。这使得可以根据检测到的严重性级别配置 IPS 以采取不同操作。一个签名可能与四个严重性级别相关联。

| 严重性级别 | 描述 |
|---|---|
| Information | 触发签名的活动不被视为迫在眉睫的威胁，但所提供的信息有用。 |
| Weak | 已检测到异常网络活动。这可能被视为恶意，但不太可能是迫在眉睫的威胁。 |
| Medium | 已检测到异常网络活动。这可能被视为恶意，并且迫在眉睫的威胁可能存在。 |
| High | 检测到用于访问或引发拒绝服务（DoS）攻击的攻击，且迫在眉睫的威胁极有可能存在。 |

### 6.10. 监控和管理告警与警报

IPS 生成的警报通常会发送到实时监控系统，以分析、显示和归档信息。事件的监控和管理可能托管在单个服务器上，也可能针对大型部署托管在多个独立服务器上。有多种协议可用于生成告警，特别是 SDEE（安全设备事件交换）、Syslog 服务器和 SNMP。

### 6.11. 攻击期间应采取的操作列表

当 IPS 检测器检测到恶意活动时，它可以选择以下一种操作：

| 操作 | 描述 |
|---|---|
| Deny attacker inline | 在指定时间内阻止来自攻击者 IP 地址的数据包。 |
| Deny connection inline | 阻止属于此 TCP 流的当前和未来数据包。 |
| Deny packet inline | 阻止触发警报的数据包。 |
| Log attacker packets | 开始记录包含攻击者 IP 地址的数据包。 |
| Log pair packets | 开始记录包含攻击者 IP 地址以及受害者 IP 地址的数据包。 |
| Log victim packets | 开始记录包含受害者 IP 地址的数据包。 |
| Produce alert | 开始将事件记录为警报。 |
| Produce verbose alert | 开始将事件记录为警报。但是，这还包括触发警报的数据包副本。 |
| Request block connection | 某些检测器可能依赖另一个网络元素在给定时刻阻止来自攻击者的网络流量。此设备称为“阻塞设备”，可能是使用 ACL 的 IOS 路由器、使用 VACL 的交换机等。此操作会向“阻塞设备”发送请求以阻止此连接。 |
| Request block host | 向“阻塞设备”发送请求以阻止攻击者主机。 |
| Request SNMP trap | 向事件日志发送 SNMP 通知和警报。 |
| Reset TCP connection | 重置并终止 TCP 连接。 |

### 6.12. IOS IPS 的配置

1. 要使用 CLI 命令配置基本 IPS，请按以下步骤操作：

在 Flash 存储器中创建 IPS 配置目录。

| 命令 | 描述 |
|---|---|
| Router# mkdir flash: dir-name | 创建配置目录。 |

将 IPS 签名包复制到 Flash 存储器中。

| 命令 | 描述 |
|---|---|
| Router# copy ftp://myuser:my-pass@ftp-server/IOS-Sxxx-CLI.pkg flash: dir-name idconf | 将签名包从 FTP 服务器复制到 Flash 中的目录。 |
| Router# copy tftp://tftp-server/IOS-Sxxx-CLI.pkg flash: dir-name idconf | 将签名包从 TFTP 服务器复制到 Flash 目录。 |
| Router# copy usbflash0:/IOS-Sxxx-CLI.pkg flash: dir-name idconf | 将签名包从 USB 复制到 Flash 目录。 |

创建 IPS 规则并指定 IPS 签名文件的位置。

| 命令 | 描述 |
|---|---|
| Router(config)# ip ips name ips-name [name acl] | 为 IPS 规则创建名称。注：使用 ACL 是可选的。它可用于过滤将被分析的流量。 |
| Router(config)# ip ips config location flash: dir-name | 指定 IPS 签名文件的位置。 |

### 激活 SDEE 协议和日志记录。

| 命令 | 描述 |
|---|---|
| Router(config)# ip http server | 激活 HTTP 服务器（使用 SDEE 时必需）。 |
| Router(config)# ip ips notify sdee | 激活 SDEE 事件通知。 |
| Router(config)# ip ips notify log | 激活日志记录。 |

### 修改签名类别。

按类别对签名进行参数化：

| 命令 | 描述 |
|---|---|
| Router(config)# ip ips signature-category | 进入 IPS 签名类别配置模式。 |
| Router(config-ips-category)# category { all \| ios_ips \| basic \| advanced } | 指定要修改的签名类别。 |
| Router(config-ips-category-action)# retired { false \| true } | 指示签名或签名类别是否要加载到路由器内存中。<br>- True：从内存中删除此类别中的所有签名。<br>- False：将签名类别编译到内存中并用于分析流量。 |
| Router(config-ips-category-action)# event-action action | 修改指定签名类别要采取的操作。这些操作包括以下内容：<br>- deny-attacker-inline；<br>- deny-connection-inline；<br>- deny-packet-inline；<br>- produce-alert；<br>- reset-tcp-connection。 |
| Router(config-ips-category-action)# alert-severity { high \| medium \| low \| informational } | （可选）修改签名或特定签名类别的警报严重性级别。 |

### 修改签名。

| 命令 | 描述 |
|---|---|
| R1(config)# ip ips signature-definition<br>R1(config-sigdef)# signature ID_of_signature<br>ID_of_sub-signature<br>R1(config-sigdef-sig)# status<br>...<br>R1(config-sigdef-sig)# engine<br>... | 此命令使用多个参数，特别是：<br>**签名 ID**：分配给签名的唯一数值。签名 ID 列表可在思科网站上查询。<br>**子签名 ID**：分配给子签名的唯一数值。<br>**引擎**：使可以定义签名使用的引擎以及功能特性。<br>**状态**：指示签名是处于活动状态还是已删除。 |

### 在接口上激活 IPS 规则。

将 IPS 规则应用到所需接口并指定方向：

| 命令 | 描述 |
|---|---|
| Router(config-if)# ip ips ips-name { in \| out } | 将 IPS 规则应用到接口<br>- IN：仅检查入站流量；<br>- OUT：仅检查出站流量。 |

### 6.13. 推荐实践

实施 IPS 的最佳实践包括：

- 实施 IPS 以分析发送到服务器、路由器等关键网络组件的流量；
- 在必要时重新配置 IPS，以考虑流量或拓扑的变化；
- 建议使用专用设备执行 IPS 任务，而非使用基于模块或 IOS 系统功能的 IPS；
- 使用自动化签名更新，而不是手动应用；
- 利用全局相关性来提升对潜在攻击的抵御能力；
- 组合使用多种入侵检测技术以加强安全性。





### 6.14. 应用练习

### 练习 8。

### 拓扑

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_127_0.png)

如需查看此图的彩色版本，请访问 www.iste.co.uk/sadiqui/computer.zip

### 寻址表

| 设备 | 接口 | IP 地址 | 子网掩码 | 网关 |
| :--- | :--- | :--- | :--- | :--- |
| R1 | G0/0 | 192.168.0.1 | /25 | - |
| R1 | G0/1 | 192.168.0.129 | /25 | - |
| R1 | G0/2 | 192.168.1.1 | /24 | - |
| R1 | S0/0 | 192.168.100.1 | /30 | - |
| R1 | S0/1 | 192.168.200.1 | /30 | - |
| R2 | G0/0 | 192.168.10.1 | /24 | - |
| R2 | S0/0 | 192.168.100.2 | /30 | - |
| R3 | G0/0 | 192.168.20.1 | /24 | - |
| R3 | S0/0 | 192.168.200.2 | /30 | - |
| PC1 | NIC | 192.168.0.2 | /25 | 192.168.0.1 |
| PC2 | NIC | 192.168.0.130 | /25 | 192.168.0.129 |
| PC3 | NIC | 192.168.10.2 | /24 | 192.168.10.1 |
| FTP_server | NIC | 192.168.1.2 | /24 | 192.168.1.1 |
| Server-HTTP | NIC | 192.168.1.3 | /24 | 192.168.1.1 |
| Server-HTTP2 | NIC | 192.168.20.2 | /24 | 192.168.20.1 |

### 目标

配置基于区域的防火墙。

### 使用的软件

Packet Tracer。

### 部分 A：设置基本设备配置

- 1. 配置基本设备设置。
  - 1.1. 按拓扑图所示配置主机名。
  - 1.2. 根据寻址表将 IP 地址应用于设备接口。
  - 1.3. 将串行接口的时钟值设置为 128000。
- 2. 使用 OSPF 协议配置路由。
  - 2.1. 在路由器上启用 OSPF，进程 ID 使用值 1。
  - 2.2. 将 R1 的 RID 值设置为 1.1.1.1，R2 设置为 2.2.2.2，R3 设置为 3.3.3.3。
  - 2.3. 将所有网络添加到 OSPF 协议。
  - 2.4. 测试所有网络元素之间的连通性。

### 部分 B：配置基于区域的防火墙

- 1. 在 R1 上创建安全区域。
  创建以下安全区域：

  | 安全区域名称 | 描述 |
  | :--- | :--- |
  | IN-ZONE-Z10 | 服务 1 网络 |
  | IN-ZONE-Z20 | 服务 2 网络 |
  | DMZ-ZONE | DMZ 区域网络 |
  | OUT-ZONE | 互联网网络 |
  | HEAD-ZONE | 总部网络 |

- 2. 创建定义需监控内部流量的 ACL。
  - 2.1. 创建一个编号的 ACL，授权 http、FTP 和 icmp 流。
    ```
    R1(config)# access-list 101 permit tcp 192.168.0.0 0.0.0.127 host 192.168.1.2 eq www
    R1(config)# access-list 101 permit tcp 192.168.0.0 0.0.0.127 host 192.168.1.2 eq ftp
    R1(config)# access-list 101 permit icmp 192.168.3.0 0.0.0.127 any
    ```
  - 2.2. 创建一个编号的 ACL，允许 FTP 流。
    ```
    R1(config)# access-list 102 permit tcp any host 192.168.1.2 eq ftp
    R1(config)# access-list 102 permit icmp any host 192.168.1.2
    ```
  - 2.3. 创建一个编号的 ACL，允许指向总部的 http 和 icmp 流。
    ```
    R1(config)# access-list 103 permit tcp 192.168.0.0 0.0.0.255 host 192.168.20.2 eq www
    R1(config)# access-list 103 permit icmp 192.168.0.0 0.0.0.255 host 192.168.20.2
    ```

- 3. 创建 Class-Map 以识别授权流量。
  - 3.1. 创建 CMAP-IN-TO-DMZ Class-Map 并识别授权流量。
    ```
    R1(config)# class-map type inspect match-any CMAP-IN-TO-DMZ
    R1(config-cmap)# match access-group 101
    R1(config-cmap)# exit
    ```
  - 3.2. 创建 CMAP-IN-TO-HEAD Class-Map 并识别授权流量。
    ```
    R1(config)# class-map type inspect match-any CMAP-IN-TO-HEAD
    R1(config-cmap)# match access-group 103
    R1(config-cmap)# exit
    ```
  - 3.3. 创建 CMAP-OUT-TO-DMZ Class-Map。
    ```
    R1(config)# class-map type inspect match-any OUT-TO-DMZ
    R1(config-cmap)# match access-group 102
    R1(config-cmap)# exit
    ```

- 4. 创建 Policy-Map 以应用 Class-Maps。
  - 4.1. 创建 Policy-Map 以应用 CMAP-IN-TO-DMZ Class-Map。
    ```
    R1(config)# policy-map type inspect PMAP-IN-TO-DMZ
    R1(config-pmap)# class type inspect CMAP-IN-TO-DMZ
    R1(config-pmap-c)# pass
    ```
  - 4.2. 同样，创建以下 Policy-Maps：
    - 用于 CMAP-OUT-TO-DMZ Class-Map 的 PMAP-OUT-TO-DMZ
    - 用于 CMAP-IN-TO-HEAD Class-Map 的 PMAP-IN-TO-HEAD

- 5. 定义区域对。
  创建以下区域对：

  | 区域对名称 | 源 | 目标 | 要应用的策略 |
  | :--- | :--- | :--- | :--- |
  | IN-to-DMZ | IN-ZONE-Z10 | DMZ-ZONE | PMAP-IN-TO-DMZ |
  | OUT-to-DMZ | OUT-ZONE | DMZ-ZONE | PMAP-OUT-TO-DMZ |
  | IN1-to-HEAD | IN-ZONE-Z10 | HEAD-ZONE | PMAP-IN-TO-HEAD |
  | IN2-to-HEAD | IN-ZONE-Z20 | HEAD-ZONE | PMAP-IN-TO-HEAD |

- 6. 将接口分配到区域。

  | 接口名称 | 安全区域名称 |
  | :--- | :--- |
  | G0/0 | IN-ZONE-Z20 |
  | G0/1 | IN-ZONE-Z10 |
  | G0/2 | DMZ-ZONE |
  | S0/0 | OUT-ZONE |
  | S0/1 | HEAD-ZONE |

- 7. 验证 R1 的配置。
  使用“show running-config”命令，验证配置的所有参数。

- 8. 测试防火墙的配置。
  - 检查是否可以从 PC2 和 PC3 访问 Server-HTTP。
  - 检查是否只能从 PC1 访问 Server-HTTP2。
  - 检查是否只能从 PC1 访问 Server-FTP 服务。
    ```
    PC1:> ftp 192.168.1.3
    ```
  - 检查是否可以从 PC1 向 Server-HTTP 发送 ping 请求。
  - 检查是否可以从 PC1 向 PC3 发送 ping 请求。

- 9. 修改 R1 防火墙的参数。
  添加授权并检测 IN-ZONE-Z20 与 Server-HTTP 之间流量所需的修改。

### 练习 9。

### 拓扑

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_131_1.png)

如需查看此图的彩色版本，请访问 www.iste.co.uk/sadiqui/computer.zip

### 寻址表

| 设备 | 接口 | IP 地址 | 子网掩码 | 网关 |
| :--- | :--- | :--- | :--- | :--- |
| R1 | G0/0 | 192.168.0.1 | /25 | - |
| R1 | G0/2 | 192.168.0.129 | /25 | - |
| R1 | G0/1 | 192.168.1.1 | /24 | - |
| R1 | S0/0 | 192.168.100.1 | /30 | - |
| R2 | G0/0 | 192.168.10.1 | /24 | - |
| R2 | S0/0 | 192.168.100.2 | /30 | - |
| PC1 | NIC | 192.168.0.2 | /25 | 192.168.0.1 |
| PC2 | NIC | 192.168.0.130 | /25 | 192.168.0.129 |
| FTP_server | NIC | 192.168.1.2 | /24 | 192.168.1.1 |
| Server-HTTP | NIC | 192.168.1.3 | /24 | 192.168.1.1 |
| Server-HTTP2 | NIC | 192.168.10.2 | /24 | 192.168.10.1 |
| Server-SYSLOG | NIC | 192.168.10.3 | /24 | 192.168.10.1 |

### 目标

- 配置基于区域的防火墙；
- 使用 CLI 命令配置 IPS。

### 使用的软件

Packet Tracer。

### 部分 A：建立基本设备配置。

- 1. 配置基本设备设置。
  - 1.1. 按拓扑图所示配置主机名。
  - 1.2. 根据寻址表将 IP 地址应用于设备接口。
  - 1.3. 将串行接口的时钟值设置为 128000。
  - 1.4. 设置系统日期和时间。
- 2. 使用 OSPF 协议配置路由。
  - 2.1. 在路由器上启用 OSPF，进程 ID 使用值 1。
  - 2.2. 将 R1 的 RID 值设置为 1.1.1.1，R2 设置为 2.2.2.2。
  - 2.3. 将所有网络添加到 OSPF 协议。
  - 2.4. 测试所有网络元素之间的连通性。

### 部分 B：配置基于区域的防火墙

- 1. 在 R1 上创建安全区域。
  创建以下安全区域：

  | 安全区域名称 | 描述 |
  | :--- | :--- |
  | IN-ZONE-Z10 | 服务 1 网络 |
  | IN-ZONE-Z20 | 服务 2 网络 |
  | DMZ-ZONE | DMZ 区域网络 |
  | HEAD-ZONE | 总部网络 |

- 2. 创建定义需监控内部流量的 ACL。
  - 2.1. 创建一个编号的 ACL (101)，授权 Z-10 与 DMZ 区域服务器之间的 http、FTP 和 icmp 流。
  - 2.2. 创建一个编号的 ACL (102)，允许 Z-20 与 DMZ FTP 服务器之间的 FTP 流。
  - 2.3. 创建一个编号的 ACL (103)，允许所有指向总部的 http 和 icmp 流。

- 3. 创建 Class-Map 以识别授权流量。
  - 3.1. 创建 CMAP-IN-TO-DMZ Class-Map 并识别授权流量。
  - 3.2. 创建 CMAP-IN-TO-HEAD Class-Map 并识别授权流量。
  - 3.3. 创建 CMAP-OUT-TO-DMZ Class-Map。

- 4. 创建 Policy-Map 以应用 Class-Maps。
  - 4.1. 创建 Policy-Map 以应用 CMAP-IN-TO-DMZ Class-Map。





## 4.2. 同样，创建以下策略映射：

PMAP-OUT-TO-DMZ 用于 CMAP-OUT-TO-DMZ 类映射
PMAP-IN-TO-HEAD 用于 CMAP-IN-TO-HEAD 类映射

## 5. 定义区域对。

创建以下区域对：

| 区域对名称 | 源 | 目标 | 应用的策略 |
|---|---|---|---|
| IN-to-DMZ | IN-ZONE-Z10 | DMZ-ZONE | PMAP-IN-TO-DMZ |
| IN1-to-HEAD | IN-ZONE-Z10 | HEAD-ZONE | PMAP-IN-TO-HEAD |
| IN2-to-HEAD | IN-ZONE-Z20 | HEAD-ZONE | PMAP-IN-TO-HEAD |

## 6. 将接口分配到区域。

| 接口名称 | 安全区域名称 |
|---|---|
| G0/0 | IN-ZONE-Z10 |
| G0/2 | IN-ZONE-Z20 |
| G0/1 | DMZ-ZONE |
| S0/0 | HEAD-ZONE |

## 7. 验证 R1 的配置。

使用“show running-config”命令，验证配置的所有参数。

## 8. 测试防火墙的配置。

## 部分 C：使用 CLI 命令配置 IPS

## 1. 回顾 IPS 签名的定义。

....................................................................................................
....................................................................................................

## 2. 创建配置目录。

```
R2# mkdir ipsDir
R2# config terminal
R2(config)#ip ips config location ipsDir
```

## 3. 创建 IPS 规则。

```
R2(config)#ip ips name ipsRule
```

## 4. 启用向 Syslog 服务器的日志记录。

```
R2(config)#service timestamps log datetime msec
R2(config)#logging on
R2(config)#logging 192.168.10.3
R2(config)#ip ips notify log
```

## 5. 配置 IPS 以使用签名类别。

### 5.1. 删除所有签名

```
R2(config)#ip ips signature-category
R2(config-ips-category)#category all
R2(config-ips-category-action)#retired true
R2(config-ips-category-action)#exit
```

### 5.2. 仅激活类别“ios_ips basic”中的签名。

```
R2(config-ips-category)#category ios_ips basic
R2(config-ips-category-action)#retired false
R2(config-ips-category-action)#exit
R2(config-ips-category)#exit
Do you want to accept these changes? [confirm]
```

## 6. 将 IPS 规则应用到接口。

```
R2(config)#interface S0/0
R2(config-if)#ip ips ipsRule in
```

## 7. 修改签名参数。

### 7.1. 显示与签名“ICMP Echo Request”关联的信息（IDsig：2004，IDsubsig：0）。

```
R2#show ip ips signature sigid 2004 subid 0
...
Action=(A)lert, (D)eny, (R)eset, Deny-(H)ost, Deny-(F)low
Trait=alert-traits   EC=event-count   AI=alert-interval
GST=global-summary-threshold   SI=summary-interval   SM=summary-
mode
SW=swap-attacker-victim   SFR=sig-fidelity-rating Rel=release
SigID:SubID En Cmp   Action Sev   Trait   EC   AI   GST   SI   SM   SW
SFR   Rel
--------------------------------------------------------------------------------
2004:0   N* Nr   A   INFO   0   1   0   200   30   FA   N 100   S1
sig-name: ICMP Echo Request
sig-string-info: My Sig Info
sig-comment: Sig Comment
Engine atomic-ip params:
fragment-status:
icmp-type: 8
ip-protocol: icmp
```

### 7.2. 选择签名“ICMP Echo Request”。

```
R2(config)#ip ips signature-definition
R2(config-sigdef)#signature 2004 0
```

### 7.3. 启用签名。

```
R2(config-sigdef-sig)#status
R2(config-sigdef-sig-status)#retired false
R2(config-sigdef-sig-status)#enabled true
R2(config-sigdef-sig-status)#exit
```

### 7.4. 将签名的操作更改为“produce-alert”。

```
R2(config-sigdef-sig)#engine
R2(config-sigdef-sig-engine)#event-action produce-alert
R2(config-sigdef-sig-engine)#exit
```

```
R2(config-sigdef-sig)#exit
R2(config-sigdef)#exit
Do you want to accept these changes? [confirm]
```

## 8. 检查 IPS 配置是否完成。

```
R2#show ip ips all
```

IPS Signature File Configuration Status

Configured Config Locations: ipsDir

Last signature default load time:

...

IPS Syslog and SDEE Notification Status

Event notification through syslog is enabled

IPS Signature Status

Total Active Signatures: 1

Total Inactive Signatures: 0

IPS Packet Scanning and Interface Status

IPS Rule Configuration

IPS name ipsRule

IPS fail closed is disabled

..

Interface Configuration

Interface Serial0/0

Inbound IPS rule is not set

Outgoing IPS rule is ipsRule

IPS Category CLI Configuration:

Category all

Retire: True

Category ios_ips basic

Retire: False

## 9. 检查配置是否有效。

### 9.1. 回顾 IDS 的定义。

### 9.2. 从 PC2 向 Server-http2 发送“ping”。

### 9.3. 检查以下消息是否已添加到 Server-SYSLOG：

> %IPS-4-SIGNATURE: Sig:2004 Subsig:0 Sev:25 [192.168.0.2 -> 192.168.10.2:0] RiskRating:25

### 9.4. 为什么可以将 R2 视为 IDS 而非 IPS？

### 9.5. 修改“ICMP Echo Request”签名以拒绝 ICMP 数据包。

```
R2(config)#ip ips signature-definition
R2(config-sigdef)#signature 2004 0
R2(config-sigdef-sig)#engine
R2(config-sigdef-sig-engine)#event-action produce-alert
R2(config-sigdef-sig-engine)#event-action deny-packet-inline
R2(config-sigdef-sig-engine)#exit
R2(config-sigdef-sig)#exit
R2(config-sigdef)#exit
Do you want to accept these changes? [confirm]
```

### 9.6. 从 PC2 向 Server-http2 发送“ping”。为什么该命令不成功？

### 9.7. 验证消息是否已添加到 Server-SYSLOG。

### 9.8. 为什么现在可以将 R2 视为 IPS？

## 保护本地网络

本章将重点介绍以下主题：

- 第 2 层攻击类型：
  - MAC 地址泛洪攻击；
  - MAC 地址欺骗攻击；
  - VLAN 跳跃攻击；
  - 基于 STP 的攻击；
- 保护第 2 层的最佳安全实践：
  - 配置端口安全；
  - 配置 DAI 功能；
  - 配置“portfast”功能；
  - 配置“bpdu guard”功能；
  - 配置“guard root”功能。

### 7.1. 简介

局域网（LAN）通常由一个或多个第 2 层交换机组成，可能成为基于第 2 层中可能存在的任何漏洞的多种攻击的目标。攻击者可能尝试中断、复制、重定向或破坏第 2 层数据传输，并因此可能影响上层使用的任何类型的协议。

### 7.2. 第 2 层攻击类型

在本章中，我们将研究针对 OSI 模型第 2 层的多种安全威胁，并讨论可用于防范这些风险的对策。这是保护“data plane”的一部分。

#### 7.2.1. MAC 地址泛洪攻击

#### 攻击概述

攻击者连接到交换机端口，并使用大量带有伪造源 MAC 地址的帧对其进行泛洪。一旦交换机表被填满，交换机就会充当集线器。攻击者随后可以捕获网络中的敏感数据。

#### 对策

“端口安全”功能是一种可防止 MAC 地址泛洪攻击的对策。

| Command | Description |
| :--- | :--- |
| Switch(config-if)# switchport mode access<br>Switch(config-if)# switchport port-security | 启用端口安全并将当前 MAC 地址分配到端口。<br>端口安全的默认值为：<br>– 只能分配一个 MAC 地址；<br>– 违规操作设置为禁用端口。 |
| Switch(config-if)# switchport port-security maximum value | 定义接口可能的最大安全 MAC 地址数量。 |
| Switch(config-if)# switchport port-security mac-address mac-address | 手动分配可以连接到此端口的 MAC 地址。 |
| Switch(config-if)# switchport port-security violation { protect | restrict | shutdown [shutdown vlan ] } | 配置当 MAC 地址数量超过预定义最大值时必须采取的操作。 |
| Switch(config-if)# errdisable recovery<br>interval seconds. | 配置端口禁用的时间段。 |

#### 7.2.2. MAC 欺骗攻击

#### 攻击概述

MAC 地址欺骗（ARP 欺骗）攻击包括在本地网络内发送虚假 ARP 消息，其目的是拦截并截获网络流量。

#### 对策

“DAI”（动态 ARP 检测）功能用于防止 ARP 欺骗攻击。它可以验证 IPv4 地址与 MAC 地址之间的映射。如果来自不可信端口出现任何异常，伪造的 ARP 数据包将被忽略。

| Command | Description |
|---|---|
| switch(config)#ip arp inspection vlan vlan | 在特定 VLAN 上启用动态 ARP 检测 (DAI)。 |
| switch(config)#interface g0/0<br>switch(config-if)#ip arp inspection trust | 将端口配置为可信端口。 |

### 7.2.3. DHCP 饥饿攻击

#### 攻击概述

DHCP 饥饿攻击包括广播大量带有伪造源 MAC 地址的 DHCP 请求。一旦 DHCP 服务器中可用的 IP 地址数量耗尽，攻击者可以引入其自身的 DHCP 服务器来响应网络上的新 DHCP 请求。攻击者现在可以使用中间人（MITM）攻击来捕获敏感数据。

#### 对策

“DHCP 侦听”功能通过过滤不可靠的 DHCP 消息来防止此类攻击。

| Command | Description |
|---|---|
| S1(config)#ip dhcp snooping | 在所有 VLAN 上启用“DHCP 侦听”功能。 |
| S1(config)#ip dhcp snooping vlan vlan | 在特定 VLAN 上启用“DHCP 侦听”功能。 |
| S1(config)#interface g0/0<br>S1(config-if)#ip dhcp snooping trust | 配置可信端口。 |
| S1#show ip dhcp snooping | 显示“DHCP 侦听”配置。 |





#### 7.2.4. VLAN 跳跃攻击。

VLAN 跳跃攻击包括连接到特定 VLAN 并尝试访问属于其他 VLAN 的网络流量。通过使用 VLAN 跳跃，攻击者可能会捕获另一个 VLAN 的网络流量，或将数据从一个 VLAN 发送到另一个 VLAN。

VLAN 跳跃攻击有两种类型，即：“交换机欺骗”和“双重标记”攻击。

##### 7.2.4.1. 交换机欺骗攻击

### DTP 协议概述

DTP 是用于在两台交换机之间动态创建中继（聚合链路）的协议。可以配置三种模式：“动态可取”、“动态自动”或“中继”。

### 攻击概述

该攻击包括连接到交换机接口，并从程序生成 DTP 消息，在攻击者的计算机和交换机之间创建“中继”链路。现在，攻击者可以捕获所有其他 VLAN 的数据。

该攻击还可以通过引入配置为使用 DTP 协议的“欺骗交换机”来实现。

### 防御措施

以下功能可用于防止此类攻击：

| Command | Description |
|---|---|
| S1(config)#interface range gigabitethernet 0/0 - 20 S1(config-if-range)#switchport mode access | 将连接到主机的交换机端口配置为访问端口。 |
| S1(config-if)# switchport mode trunk | 显式启用聚合链路。 |
| S1(config-if)# switchport nonegotiate | 禁用 DTP 并防止生成 DTP 消息。 |
| S1(config)#interface range gigabitethernet 0/26 - 32 S1(config-if)# switchport access vlan Vlan S1(config-if)# shutdown | 将未使用的端口分配到专用 VLAN 并禁用它们。 |

##### 7.2.4.2. 双重标记攻击

### 攻击概述

该攻击包括连接到“中继”端口上属于原生 VLAN 的接口，并在以太网帧中两次插入与 VLAN 相关的字段来发送帧。

实际上，双重标记攻击分为三个步骤：

- 1) 攻击者生成并向交换机 1 发送带有双重标记的 802.1Q 帧：
  - 第一个标记携带“中继”端口的原生 VLAN 标识符；
  - 第二个标记携带目标主机的 VLAN 标识符。

| 数据 | 原生 VLAN ID | 目标 VLAN ID |
| --- | --- | --- |

### 图 7.1. 带有两个标记的 802.1Q 帧

2) 交换机 1 将删除原生 VLAN 标记。攻击者的帧现在将仅包含目标主机的 VLAN 标记。

| 数据 | 目标 VLAN ID |
| --- | --- |

### 图 7.2. 由目标主机上的 VLAN 标记标记的 802.1Q 帧

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_144_0.png)

### 图 7.3. 双重标记攻击的步骤

— 在图 7.1、7.2 和 7.3 中，“data”字段表示与以太网帧相关的信息，此外还包含数据包中的其他信息，而不考虑它们在 802.1Q 帧中出现的顺序。

— 此类攻击是单向的，仅当黑客连接到与原生中继端口 VLAN 相同 VLAN 的端口时才有效。

### 防御措施

“原生 VLAN”功能用于防止此类攻击。

| Command | Description |
|---|---|
| Switch(config-if)# switchport trunk native vlan vlan | 为原生 VLAN 流量创建专用 VLAN，使其与用户流量分离。 |

#### 7.2.5. 基于 STP 的攻击

### STP 概述

STP 是一种网络协议，通过阻止由多台交换机组成的局域网中的某些路径，从而创建无环网络拓扑。其功能可概括如下：

- 为每个 VLAN 选择“根桥”交换机；
- 定义“根端口”，以允许“根”交换机与其他交换机之间的互连；
- 定义获准传输数据的端口；
- 阻止交换机上的某些端口。

### 攻击概述

该攻击包括引入“欺骗交换机”，该交换机将通过发送包含最小“BID”的虚假“PDU”消息，试图将自身定位为“根桥”。这将导致修改 STP 拓扑并更改端口角色。从此，攻击者可以使用先前被阻止的端口，以捕获通过网络的所有流量。

### 防御措施

“保护根”功能用于防止此类攻击：

| Command | Description |
|---|---|
| S1(config-if)# spanning-tree guard root | 防止其他交换机替换原始“根桥”。 |

注释。
- “BPDU 防护”和“保护根”功能相似，但影响不同：
- 如果在端口上激活了“PortFast”选项，则“BPDU 防护”在接收 BPDU 消息时会禁用端口。您必须手动重新激活端口或配置“禁用时间”。
- “保护根”允许 BPDU 消息跨端口传输以维护 STP 拓扑，除非另一台交换机试图成为“根桥”。当另一台交换机停止尝试时，端口将重新激活。

### 7.3. 保护第 2 层的最佳安全实践

保护第 2 层的最佳实践，针对每种攻击类型，包括：

| 攻击类型 | 描述 | 防御措施 |
|---|---|---|
| MAC 地址攻击 | – MAC 地址泛洪<br>– MAC 地址欺骗 | – 对访问端口使用端口安全功能。<br>– 配置 **DAI** 功能。 |
| STP 攻击 | – 修改 STP 拓扑 | – 配置 **端口快速** 功能。<br>– 配置 **BPDU 防护** 功能。<br>– 配置 **保护根** 功能。 |
| VLAN 跳跃攻击 | – 使用 DTP<br>– 双重标记攻击 | – 在访问端口上禁用 DTP。<br>– 显式配置“中继”端口。<br>– 始终使用专用原生 VLAN。<br>– 禁用所有未使用的端口并将其放置在未使用的 VLAN 中。<br>– 避免使用 VLAN 1。 |

### 7.4. 应用练习

练习 10.–

### 拓扑

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_147_0.png)

该图的彩色版本，请参见 www.iste.co.uk/sadiqui/computer.zip

### 寻址表

| 设备 | 接口 | IP 地址 | 子网掩码 | 网关 |
|---|---|---|---|---|
| S1 | VLAN1 | 192.168.0.2 | /24 | 192.168.0.1 |
| S2 | VLAN1 | 192.168.0.3 | /24 | 192.168.0.1 |
| S3 | VLAN1 | 192.168.0.4 | /24 | 192.168.0.1 |
| PC1 | NIC | 192.168.0.5 | /24 | 192.168.0.1 |
| PC2 | NIC | 192.168.0.6 | /24 | 192.168.0.1 |
| dhcp-server | NIC | 192.168.0.7 | /24 | 192.168.0.1 |

### 目标

- 保护密码；
- 实施连接限制；
- 保护本地网络免受第 2 层攻击。

### 使用的软件

- Packet Tracer。

### 部分 A：建立基本设备配置。

- 1. 按照拓扑中指示配置主机名称。
- 2. 根据寻址表将 IP 地址应用到设备接口。

### 部分 B：保护密码

### 在交换机 S1 上

- 1. 为特权模式设置密码“Ci$c0ena”。
- 2. 配置控制台端口和虚拟访问线路。
- 2.1. 将“Ci$c0con”设置为控制台端口的密码，并将非活动间隔设置为 5 分钟。
- 2.2. 将“Ci$c0vty”设置为 VTY 线路的密码，并将非活动间隔设置为 2 分钟。
- 3. 加密所有密码。

### 部分 C：使用 SSH 保护对 VTY 线路的访问

- 1. 配置 SSH 连接。

### 在交换机 S1 上

- 使用以下选项配置 SSH 连接：
  - 域名：tri.local；
  - 用户名：sshadmin，密码：Ci$c0ssh；
  - RSA 加密密钥为 1024 位；
  - 使用的 SSH 版本为版本 2；
  - 等待时间为 90s；
  - 登录尝试次数为 3；
  - 仅授权 SSH 会话。

- 2. 配置连接参数。

使用“login block-for”命令，如果在 **30s** 内两次连接尝试失败，则将连接阻止 **60s**。

### 部分 D：保护本地网络免受第 2 层攻击

### 在交换机 S2 上

### 1. 防御局域网免受 MAC 地址泛洪攻击。

### 1.1. 解释此类攻击。

### 1.2. 将 FastEthernet 端口 0/4 至 0/16 上的安全 MAC 地址最大数量设置为 2。

```
S2(config)# int range f0/4-16
S2(config-if)# switchport mode access
S2(config-if)# switchport port-security
S2(config-if)# switchport port-security maximum 2
```

### 1.3. 在发生访问违规时阻止在端口上接收到的帧。

```
S2(config-if)# switchport port-security violation protect
```

### 1.4. 将 Server_dhcp 的 MAC 地址手动分配给端口 f0/3。

```
S2(config)# int f0/3
S2(config-if)# switchport mode access
S2(config-if)# switchport port-security
S2(config-if)# switchport port-security mac-address mac-address_server_dhcp
```

### 1.5. 禁用未使用的 FastEthernet 端口 0/17 至 0/24。

```
S2(config)# int range f0/17-24
S2(config-if)# shutdown
```





## 1.6. 显示接口端口 f0/4 的安全性，并对粗体元素进行说明。

```
S2#show port-security interface f0/4
Port Security: Enabled
Port Status: Secure-up
Violation Mode: protect
Aging Time: 0 mins
Aging Type: Absolute
Secure Static Address Aging: Disabled
Maximum MAC Addresses: 2
Total MAC Addresses: 1
Configured MAC Addresses: 1
Sticky MAC Addresses: 0
Last Source Address: 001b.5325.256f Vlan: 1
Security Violation Count: 0
```

## 2. 防止局域网遭受 DHCP 饥饿攻击。

### 2.1. 解释此类攻击。

### 2.2. 将端口 f0/3 配置为连接可靠 DHCP 服务器的端口。

```
S2(config)# interface f0/3
S2(config-if)# ip dhcp snooping trust
```

### 2.3. 显示“dhcp snooping”参数。

```
S2#show ip dhcp snooping
```

### 2.4. 测试 DHCP 服务器的工作情况。工作站 PC1 和 PC2 在 DHCP 配置后必须能够获得动态 IP 地址。

## 3. 防止局域网遭受 VLAN 跳跃攻击

### 3.1. 解释此类攻击。

### 3.2. 禁用端口 f0/1 和 f0/2 上的 DTP 协议使用。

```
S2(config)# interface range f0/1-2
S2(config-if-range)# switchport nonegotiate
```

### 3.3. 将两个端口配置为 trunk 模式。

```
S2(config-if)# switchport mode trunk
```

### 3.4. 将无标签流量定向至原生 VLAN 99。

```
S2(config)# vlan 99
S2(config-vlan)# name 99
S2(config-vlan)# exit
S2(config)# interface range f0/0-1
S2(config-if)# switchport trunk native vlan 99
```

### 3.5. 显示接口 f0/1 的参数。

```
S2#show interfaces trunk
Port Mode Encapsulation Status Native vlan
Fa0/1 on 802.1q trunking 99
..
S2#show interface fa0/1 switchport
Name: Fa0/1
.....
Negotiation of Trunking: Off
Access Mode VLAN: 1 (default)
Trunking Native Mode VLAN: 99 (Inactive)
```

## 4. 防止局域网遭受基于 STP 的攻击。

### 4.1. 解释此类攻击。

### 4.2. 将交换机 S2 配置为“根桥”。

```
S2(config)# spanning-tree vlan 1 root primary
```

### 4.3. 保护端口 f0/1 和 f0/2 上的“根桥”替换。

```
S2(config)# interface range f0/1-2
S2(config-if-range)# spanning-tree guard root
```

### 4.4. 在 f0/3 端口上启用“portfast”选项。

```
S2(config-if)# spanning-tree portfast
```

### 4.5. 在同一端口上启用“bpduguard”选项。

```
S2(config-if)# spanning-tree bpduguard enable
```

### 4.6. 显示 f0/1 接口的 STP 参数。

```
S2#sh running-config | begin interface FastEthernet0/1
interface FastEthernet0/1
spanning-tree portfast
spanning-tree bpduguard enable
spanning-tree guard root
```

## 练习 11。

### 拓扑

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_152_0.png)

### 寻址表

| 设备 | 接口 | IP 地址 / 子网掩码 | 操作系统 | 网关 |
|---|---|---|---|---|
| S1 | VLAN1 | 172.16.0.1/24 | c3725-adventerprisek9-mz.124-15.T14 | 192.168.0.1 |
| PC1 | NIC | 172.16.0.2/24 | Windows 7 或更高版本 | 192.168.0.1 |

### 目标

- 保护密码；
- 模拟第二层攻击。

### 使用的软件

- GNS3。

### A 部分：建立基本设备配置。

- 1. 按拓扑所示配置主机名。
- 2. 根据寻址表将 IP 地址应用于设备接口。

### B 部分：保护密码（可选）

### 在交换机 S1 上

- 1. 设置最小密码长度为 8 个字符。
- 2. 为特权模式设置密码“Cisc0ena”。
- 3. 配置控制台端口和虚拟访问线路。
- 3.1. 将“Cisc0con”设置为控制台端口的密码，并将非活动间隔设置为 5 分钟。
- 3.2. 将“Cisc0vty”设置为 VTY 线路上的密码，并将非活动间隔设置为 2 分钟。
- 4. 加密所有密码。
- 5. 配置 VTY 连接。

### 在交换机 S1 上

- 使用以下选项配置 ssh 连接：
- 域名：tri.local；
- 用户名：sshadmin，密码：Ci$c0ssh；
- RSA 加密密钥为 1024 位；
- 使用的 SSH 版本为版本 2；
- 等待时间为 90 秒；
- 登录尝试次数为 3 次；
- 允许 ssh 和 telnet 会话。

### C 部分：模拟第二层攻击

下载并安装 hyenae¹ 工具。

### 1. 模拟 MAC 地址泛滥攻击。

### 目标

- 1.1. 在 S1 和 Host1 之间发送 ping。

```
S1#ping 172.16.0.2
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 172.16.0.2, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 8/20/36 ms
```

- 1.2. 显示 S1 交换机表。

```
S1#sh mac-address-table
Destination Address Address Type VLAN Destination Port
------------------------------------------------------
cc01.0d68.0000 Self 1 Vlan1
0200.4c4f.4f50 Dynamic 1 FastEthernet0/0
```

cc01.0d68.0000 是 VLAN1 的 MAC 地址。执行此练习时，此值不一定相同。

写下你的 VLAN1 地址：

### 1.3. 使用以下参数配置“ICMP-echo”攻击：

- 确保所选接口正确；

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_155_0.png)

按如下所示配置以下设置：

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_155_1.png)

注意：

- “Packet-type”参数必须设置为“ICMP-echo”攻击；
- “Fixed packet limit”必须设置为三个数据包；

按如下所示配置以下设置：

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_155_2.png)

注意：

- **目的模式** 设置必须包含你的 VLAN1 MAC 地址和 IP 地址；
- MAC 地址的两位数字必须用“:”分隔；
- “%”字符表示程序将随机生成值。

### 1.4. 通过按“Execute”按钮启动“ICMP-echo”攻击：

```
S1#sh mac-address-table
Destination Address Address Type VLAN Destination Port
-------------------------------------------------
cc01.0d68.0000 Self 1 Vlan1
cc01.0203.0411 Dynamic 1 FastEthernet0/0
cc01.0203.04dc Dynamic 1 FastEthernet0/0
cc01.0203.043a Dynamic 1 FastEthernet0/0
```

1.5. 启动“ICMP-echo”攻击，用 10 个随机 MAC 地址填充交换机表。为此，设置以下选项：

- “Fixed packet limit”参数必须设置为 10 个数据包；
- “Fixed send delay”必须设置为 100 ms。

### 1.6. 验证结果。

```
S1#sh mac-address-table
Destination Address Address Type VLAN Destination Port
-------------------------------------------------
cc01.0d68.0000 Self 1 Vlan1
cc01.0203.0411 Dynamic 1 FastEthernet0/0
cc01.0203.04dc Dynamic 1 FastEthernet0/0
cc01.0203.043a Dynamic 1 FastEthernet0/0
cc01.0203.043d Dynamic 1 FastEthernet0/0
cc01.0203.04d Dynamic 1 FastEthernet0/0
cc01.0203.0460 Dynamic 1 FastEthernet0/0
cc01.0203.04bf Dynamic 1 FastEthernet0/0
cc01.0203.0495 Dynamic 1 FastEthernet0/0
cc01.0203.04ed Dynamic 1 FastEthernet0/0
cc01.0203.041e Dynamic 1 FastEthernet0/0
0200.4c4f.4f50 Dynamic 1 FastEthernet0/0
```

### 2. 模拟“DHCP 饥饿”攻击。

### 2.1. 在 S1 交换机上配置 DHCP 服务。

```
S1(config)# ip dhcp excluded-address 172.16.0.1 172.16.0.9
S1(config)# ip dhcp pool pool1
S1(dhcp-config)# network 172.16.0.0 255.255.255.0
S1(dhcp-config)# default-router 172.16.0.1
S1(dhcp-config)# exit
```

### 2.2. 使用以下参数配置“DHCP-Discover”攻击：

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_157_0.png)

### 2.3. 按“Execute”按钮发起攻击并检查结果：

```
S1#sh ip dhcp binding
Bindings from all pools not associated with VRF:
IP address          Client-ID/                                          Lease expiration   Type
                    Hardware address/
                    User name
172.16.0.10         0100.1122.3344.93                                   Mar 01 2002 12:28 AM
Automatic
172.16.0.11         0100.1122.3344.e2                                   Mar 01 2002 12:28 AM
Automatic
172.16.0.12         0100.1122.3344.9b                                   Mar 01 2002 12:28 AM
Automatic
172.16.0.13         0100.1122.3344.ce                                   Mar 01 2002 12:28 AM
Automatic
```

### 3. 保护 S1 F0/1 端口。

在 S1 上启用端口安全性并重新执行 TP。确保攻击不再发生。





本章将重点介绍以下主题：

- 密码学的基本概念；
- 密码学的不同分类：
  - 传统密码学，
  - 现代密码学，
  - 对称加密和非对称加密；
- 密钥管理：
  - Diffie-Hellman 密钥交换；
- 哈希函数；
- HMAC 码；
- 非对称密码学：
  - 数字签名，
  - 公钥基础设施。

### 8.1. 密码学的基本概念

#### 8.1.1. 定义

密码学是计算机科学的一个学科，它使得保护被判定为机密的消息成为可能。如果消息被未经授权的人员截获，则应无法理解且难以破解。

#### 8.1.2. 术语

- 明文：表示在修改前我们希望传输的所有数据。明文可能包括文本、图像、视频、音频等。
- 加密：将明文转换为无法理解的数据。
- 密文：指在明文上应用加密算法后获得的文本，也称为密码文本。
- 解密：指从密文中恢复明文。
- 算法：表示用于加密和解密数据的一系列操作。
- 密钥：指允许加密和解密数据的参数。
- 密码分析：指用于尝试从密文中恢复明文的所有技术和方法。

### 8.2. 密码学的不同分类

密码学是一种古老的技术，尤其用于确保被认为至关重要的文本消息的机密性。随着当今计算机的出现，密码学领域已经发展到足以允许加密任何类型的数据，同时还提供难以破解的加密算法。

图 8.1 展示了密码学不同分类的主要特征。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_160_0.png)

图 8.1. 密码学的不同分类

#### 8.2.1. 传统密码学

该密码学通常使用的加密方法包括：

##### 8.2.1.1. 代换加密

存在两种代换加密：

— 单表代换：这包括将一个字符仅替换为另一个字符，以避免解密过程中的歧义。此类别中最古老且最著名的加密方法有：

- 凯撒密码：基于字母的简单移位；
- Atbash 密码：基于按逆序书写字母表。

注：为了使这种方法更难破译，可以选择只替换某些字母。确切的替换方法可称为加密密钥。

— 多表代换包括将一个字符替换为另一个字符，该字符动态选择，由加密密钥决定，而不是以固定方式选择。

示例：让我们使用密钥“123”加密单词“ABCABD”，该密钥表示第一个字符移动一个空格，第二个字符移动两个，第三个字符移动三个，以此类推。这将给出以下结果：“BDFBDG”。

##### 8.2.1.2. 置换加密

此外，这种方法使用遵循明确规则的字母顺序重新排列。

示例：让我们使用密钥“7514263”加密文本“ISTA BAB TZIMI”，采用置换加密。

为此，我们创建以下表格：

- 第一行由密钥值组成；
- 然后通过填写要加密的消息字母来填充表格。最后一行可能不完整。

结果：

| 7 | 5 | 1 | 4 | 2 | 6 | 3 |
|---|---|---|---|---|---|---|
| I | S | T | A | B | A | B |
| T | I | Z | I | M | I | |

结果是按 1 到 7 的列顺序连接字符：TZBM BAIS IAII T。

注：在某些情况下，加密表可以定义为一系列字符。在这种情况下，每个字符将与一个数值关联，然后应用前述过程。

#### 8.2.2. 现代密码学

##### 8.2.2.1. 分组加密

分组加密包括将数据分成块，其大小通常固定（32 到 512 位之间），然后逐个加密。分组加密背后的一般原理可以总结如下：

- 使用二进制代码替换字符；
- 将此链分为给定长度的块。
- 基于密钥逐位加密一个块；
- 根据需要重复步骤 3；
- 移到下一个块。

分组加密算法的不完全列表包括：

- 数据加密标准 (DES)；
- 高级加密标准 (AES)；
- 三重数据加密标准 (3DES)；
- Blowfish；
- 国际数据加密算法 (IDEA)。

##### 8.2.2.2. 流加密

流加密包括持续对数据进行操作，而无需收集一块数据来启动操作。这种类型的加密常用于实时通信，因为它具有更快的特性。流加密算法的不完全列表包括 RC4 和 SEAL 标准。

#### 8.2.3. 对称加密和非对称加密

##### 8.2.3.1. 对称加密

- 在对称加密中，加密和解密使用相同的密钥，因此需要保持密钥机密。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_162_0.png)

- 对称加密算法的不完全列表包括：
  - DES；
  - 3DES；
  - AES；
  - IDEA；
  - RC2、RC4、RC5、RC6；
  - Blowfish。

— 对称加密算法最常用于数据保护，因为它们提供快速的处理时间，并且在使用大密钥时具有相当高的安全级别。然而，其脆弱性在于用于交换共享密钥的方法。

##### 8.2.3.2. 非对称加密

— 在非对称加密（或公钥加密）中，加密和解密数据使用不同的密钥，并且无法从一个密钥生成另一个密钥。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_163_0.png)

图 8.3. 非对称加密

非对称加密算法包括：

- RSA：以其创建者的姓名缩写命名：Rivest、Shamir 和 Adleman；
- DH：DH（Diffie-Hellman）是一种非对称加密算法，允许两个主机在不可靠网络上交换共享的密钥。该协议通常与 3DES 和 AES 等对称算法结合使用；
- DSA：由美国国家安全局开发的数字签名算法。

- 与对称算法相比，非对称算法较慢。它们通常用于低容量加密情况，例如数字签名和密钥交换。

注：本章后面将对非对称加密进行更详细的介绍（参见第 8.6 节）。

### 8.3. 密钥管理

#### 8.3.1. 简介

密码学的目标在很大程度上依赖于加密密钥的保护。建立高效可靠的管理来安全存储和分发加密密钥非常重要。这种管理对于任何加密项目的成功至关重要。

有两种密钥管理方法可以帮助解决此问题：

- 手动管理：包括在每个设备上手动配置安全链路的所有参数，包括加密密钥。这种方法在静态且小规模的环境中已被证明相对实用。然而，它不适合大型网络；
- 自动管理：这包括使用协议（例如 ISAKMP）动态配置安全链路的所有参数。

#### 8.3.2. Diffie-Hellman 密钥交换

Diffie-Hellman (DH) 是一种方法，允许两个网络元素建立一个系统，以便它们可以以受保护的方式交换秘密密钥。这种方法使得可以基于两个初始秘密密钥创建一个新的共享密钥，而无需使用安全通道来交换它们。

### 工作原理

| 步骤 | U1 | U2 |
| :--- | :--- | :--- |
| 1 | 两个用户共同选择：<br>- 一个质数 _p_；<br>- 一个整数 _g_，使得 1 ≤ g ≤ p–1。<br>注意：此交换不需要安全。 | |




| | | |
|:---|:---|:---|
| 2 | U1 选择一个随机值 A | U2 选择一个随机值 B |
| 3 | U1 计算值：a = g^A(mod p) | U2 计算值：b = g^B(mod p) |
| 4 | U1 和 U2 交换 a 和 b 的值。<br>a ↔ b<br>注意：此次交换不需要安全。 | |
| 5 | U1 计算值：K = b^A(mod p) | U2 计算值：K = a^B(mod p) |
| | 两用户随后共享一个相同的密钥 K，而无需共享 A 和 B 的值。 | |

注意。

- A 和 B 可以取与 U1 和 U2 关联的密钥的值。
- 从 p、g、a、b 和 K 的值中理论上不可能找到 A 和 B 的值。
- 在实践中，使用的数字是 300 位数的 100 位数次幂，强度非常高。

## 示例

| 步骤 | U1 | U2 |
|:---|:---|:---|
| 1 | p = 23<br>g = 7 | |
| 2 | A=3 | B=6 |
| 3 | a = 7^3(mod 23) = 21 | b = 7^6(mod 23) = 4 |
| 4 | U1 和 U2 交换 a 和 b 的值。<br>a ↔ b | |
| 5 | K = 4^3(mod 23) = 18 | K = 21^6(mod 23) = 18 |
| | 两用户随后共享一个相同的密钥 18。 | |

### 8.4. 哈希函数

哈希函数是用于确保数据完整性的单向函数。哈希函数处理一个数据块（可能体积较大或性质多样），以返回一个小的哈希值，称为“消息摘要”，其大小固定。哈希函数具有以下特性：

- 无法从哈希值重构消息；
- 修改消息总会导致另一个哈希值。

两个不同的消息不可能具有相同的哈希值。

最常用的哈希函数列表如下：

- MD5：支持创建 128 位消息摘要；
- SHA-1：支持创建 160 位消息摘要；
- SHA-2：支持创建 224 位和 512 位消息摘要。

### 8.5. HMAC 码

基于哈希的消息认证码（HMAC）允许你通过使用现有哈希函数结合共享密钥来计算消息摘要。这使得可以确保数据的认证和完整性。

Cisco 使用两个 HMAC 函数：

- 基于 MD 哈希算法、带共享密钥的 HMAC-MD5；
- 基于 SHA-1 哈希算法、带共享密钥的 HMAC-SHA-1。

### 8.6. 非对称加密

#### 8.6.1. 简介

非对称加密是一种基于一对密钥（公钥和私钥）的数据加密和解密过程。两个密钥都可以加密数据。但是，解密数据需要互补密钥。

非对称加密基于复杂的数学算法，因此计算时间比对称算法更长。

非对称加密用于确保机密性和认证。

#### 8.6.2. 工作原理

| 保密性 | 保密性 → 公钥（加密）+ 私钥（解密） |
|:---|:---|
| | – 公钥用于加密；相应的私钥用于解密。 |
| | – 鉴于私钥仅存在于单个系统上，此过程保证保密性。 |
| | – 此场景常用于密钥交换。 |
| 认证 | 认证 → 私钥（加密）+ 公钥（解密） |
| | – 私钥用于加密；相应的公钥用于解密。 |
| | – 鉴于私钥仅存在于一个系统上，当其公钥解密消息时，认证得到保证。 |

图 8.4. 总结了确保**保密性**的流程。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_167_0.png)

**图 8.4.** 只有 A 可以读取 B 发送的消息

图 8.5. 介绍了确保**认证**的流程。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_168_0.png)

图 8.5. 只有 A 可能发送了这条消息

#### 8.6.3. 数字签名

##### 8.6.3.1. 简介

数字签名可以确保电子文档的完整性并验证文档作者的身份。它具有以下特性：

- 无法伪造；
- 它是签署文档的一部分，不能移动到另一个文档；
- 已签署的文档不能再被修改。

数字签名提供三个安全功能：

- 签名者的真实性：签名者的身份已得到最终确认；
- 数据完整性：数字签名保证文档自传输以来始终保持完整；
- 不可否认性：签名者不能否认对文档的签名。

##### 8.6.3.2. 工作原理

验证由用户 A 发送给用户 B 的已签署文档的过程可以总结如下：

### 步骤 1：签署文档

第一个用户“A”将：

- 1) 生成一个私钥 **Kpr** 和一个公钥 **Kpb**；
- 2) 使用哈希函数 **H** 计算文档的哈希值；
- 3) 使用其私钥 **Kpr** 加密哈希值；
- 4) 向接收者“B”发送以下信息：
  - 公钥 **Kpb**；
  - 文档；
  - 函数 H；
  - 加密后的哈希值。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_169_0.png)

**图 8.6.** 文档的签名

### 步骤 2：验证已签署的文档

第二个用户“B”将：

- 2) 使用哈希函数 H 计算文档的哈希值；
- 3) 比较文档生成的消息摘要和使用公钥 Kpb 先前解密的消息摘要。如果两个消息摘要相同，则签名有效。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_170_0.png)

图 8.7. 验证已签署的文档

#### 8.6.4. 公钥基础设施

##### 8.6.4.1. 简介

公钥基础设施（PKI）是一组服务，可以确保组织中数据的机密性、完整性和认证，并基于非对称加密的基本原理。PKI 解决方案基于数字证书和可靠第三方的担保。

##### 8.6.4.2. 术语

| 概念 | 定义和特性 |
|:---|:---|
| **证书颁发机构（CA）** | – 证书颁发机构是一家可靠组织，能够将公钥与用户、公司、设备等关联。<br>– 该机构负责对这些公钥进行数字签名和发布，并保证其真实性。<br>– 证书颁发机构可以是私营组织（例如 VeriSign、Cisco 等）或公共组织。 |
| **证书** | – 一种将用户名或组织名与公钥关联的电子文档。<br>– 数字证书由证书颁发机构进行数字签名。<br>– 除了相关实体的公钥之外，数字证书还包含证书的有效期、用于签署证书的算法等信息。 |
| **证书吊销列表（CRL）** | – CRL 是不再有效的证书列表。<br>– 证书可能因多种原因失效：<br>  - 有效期届满；<br>  - 与证书关联的私钥或公钥被泄露；<br>  - 证书持有者名称中至少一个字段发生更改；<br>  - 其他。 |

##### 8.6.4.3. PKI 标准

最广泛使用的 PKI 规范包括：

- X.509：这是由 ITU-T 组织创建的标准，用于定义公钥证书、证书吊销列表（CRL）及其他证书属性的基本标准格式；
- **公钥加密标准（PKCS）**：这些是由“RSA”实验室设计的一套规范，用于实施公钥加密技术。IT 界中最常采用的 PKCS 包括：



| PKCS 标准 | 描述 |
|---|---|
| PKCS#1 | RSA 密码学标准 |
| PKCS#3 | Diffie-Hellman 密钥交换标准 |
| PKCS#5 | 基于密码的加密标准 |
| PKCS#7 | 密码消息语法标准 |
| PKCS#8 | 私钥信息语法标准 |
| PKCS#10 | 证书请求标准 |

##### 8.6.4.4 PKI 拓扑

PKI 基础设施可以使用三种拓扑实现：

- 简单拓扑：在此拓扑中，单个证书颁发机构（根证书颁发机构）负责向最终用户颁发所有证书。该模型的优点是简单。然而，它也存在以下缺点：
  - 在大型环境中难以管理该拓扑；
  - 需要严格的集中式管理；
  - 在使用单个签名私钥时存在关键漏洞。如果此密钥被泄露或窃取，整个基础设施将崩溃。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_172_0.png)

### 图 8.8. 简单 PKI 拓扑

- 层次拓扑：在此拓扑中，CA 可以直接向最终用户颁发证书，或将此任务委派给下属 CA。这些下属 CA 反过来可以向最终用户或其他证书颁发机构颁发证书。层次拓扑的主要优势是其可扩展性和简化的管理。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_173_0.png)

- 交叉拓扑：在此拓扑中，多个根证书颁发机构建立水平信任关系，相互验证其证书。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_173_1.png)

### 8.7 应用练习

ETL 3.-

### 部分 A：传统密码学

#### 1. 使用单表代替加密数据。

- 1.1. 使用位移为三个字符的单表代替加密文本“OFPP ISTA TRI”（加密密钥等于 3）。

| 明文 | O | F | P | P | T | I | S | T | A | T | R | I |
|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|
| 位移 | 3 | 3 | 3 | 3 | 3 | 3 | 3 | 3 | 3 | 3 | 3 | 3 |
| 密文 | | | | | | | | | | | | |

- 1.2. 使用位移为五个字符的单表代替加密文本“The Office of Vocational Training and Work Promotion”。

- 1.3. 解密以下文本“PEGVCTXSKVETLMIGPEWWMUYI”，已知它是使用位移为四个字符的单表代替加密的（添加空格）。

#### 2. 使用多表代替加密。

- 2.1. 使用偏移量“132”或 (bdc) 的多表代替加密文本“OFPP ISTA TRI”（加密密钥为 132）。

| 明文 | O | F | P | P | T | I | S | T | A | T | R | I |
|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|
| 位移 | 1 | 3 | 2 | 1 | 3 | 2 | 1 | 3 | 2 | 1 | 3 | 2 |
| 密文 | | | | | | | | | | | | |

- 2.2. 使用位移为“202”的多表代替加密文本“Office of Vocational Training and Promotion of Work”。

- 2.3. 解密以下文本“MDGSBTURKSDTILIDOETVMRI”，已知它是使用位移为“134”或 (BDE) 的多表代替加密的（添加空格）。

#### 3. 使用置换加密。

使用位置“52143”的置换加密对文本“OFFPPT ISTA TRI”进行加密。

### 部分 B：现代密码学

#### 1. 对称加密。

#### 1.1. 回顾原理。

#### 1.2. 对称加密的主要弱点是什么？

- a) 加密时间，被认为较高。
- b) 对称加密算法的漏洞。
- c) 交换共享密钥的方法。
- d) 无法加密文本以外的数据。

#### 1.3. 以下哪项不是对称算法？

- a) DES。
- b) 3DES。
- c) AES。
- d) RSA。
- e) RC6。
- f) Blowfish。

#### 1.4. 如果 10 个人需要使用对称密钥密码学进行通信，需要多少个密钥？

- a) 100。
- b) 1000。
- c) 9。
- d) 10。

#### 1.5. 在 ____________ 中，密钥称为共享密钥。

- a) 对称加密。
- b) 非对称加密。
- c) (a) 和 (b)。
- d) 既不是 (a) 也不是 (b)。

#### 1.6. 使用对称算法的主要缺点之一是什么？

- a) 它不提供更好的访问控制。
- b) 它是一个较慢的过程。
- c) 它不提供交付的不可否认性。
- d) 它更难以实现。

#### 2. 非对称加密。

#### 2.1. 回顾原理。

#### 2.2. 一对密钥用于 ____________。

- a) 对称加密。
- b) 非对称加密。
- c) (a) 和 (b)。
- d) 既不是 (a) 也不是 (b)。

#### 2.3. 在非对称密钥加密中，发送方使用 ____________ 密钥加密数据。

- a) 私钥。
- b) 公钥。
- c) 两者。
- d) 既不是 (a) 也不是 (b)。

#### 2.4. 在非对称密钥加密中，接收方使用 ____________ 密钥解密数据。

- a) 私钥。
- b) 公钥。
- c) 两者。
- d) 既不是 (a) 也不是 (b)。

#### 2.5. 哪个陈述描述了非对称加密算法？

- a) 它们的密钥长度范围从 64 到 256 位。
- b) 它们包括 DES、3DES 和 AES。
- c) 它们也称为共享密钥算法。
- d) 它们相对较慢，因为基于计算复杂的算法。

#### 2.6. 在什么情况下强烈建议使用非对称加密算法？

- a) 登录本地计算机。
- b) 在互联网上进行购物。
- c) 通过 FTP 下载音乐。
- d) 在两个企业站点之间发送大量数据。

#### 2.7. 在非对称密钥密码学中，什么是公钥？

- a) 仅加密密钥。
- b) 仅解密密钥。
- c) 两个密钥。
- d) 都不是。

#### 2.8. 以下哪项不是非对称算法？

- a) RSA。
- b) DH。
- c) DSA。
- d) 3DES。

### 练习 12.–

### 拓扑

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_177_0.png)

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_178_0.png)

此图彩色版本，请参见 www.iste.co.uk/sadiqui/computer.zip

### 寻址表

| 设备 | 接口 | IP 地址 | 子网掩码 | 网关 |
|:---|:---|:---|:---|:---|
| PCA | NIC | 192.168.0.2 | /24 | - |
| PCB | NIC | 192.168.0.3 | /24 | - |
| Email-Server | NIC | 192.168.0.10 | /24 | - |

### 目标

- 使用对称和非对称加密。

### 使用的软件

- Packet Tracer。

### 部分 A：建立基本设备配置。

根据寻址表将 IP 地址应用于设备接口，并检查组件之间的连通性。

### 部分 B：使用对称和非对称加密

#### 1. 分析发送明文消息的风险。

#### 1.1. 回顾嗅探器的作用。

#### 1.2. 回顾“中间人”攻击的原理。

#### 1.3. 参数化并测试嗅探器。

在嗅探器上，仅过滤 ICMP、POP3 和 SMTP 数据包。在 PCA 和 PCD 之间发送 ping，并检查该数据包是否出现在嗅探器屏幕上。

#### 1.4. 在服务器、PCA 和 PCD 上配置电子邮件服务。

- 按如下配置电子邮件服务器：

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_179_0.png)

- 按如下配置 PCA 上的电子邮件应用程序：

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_179_1.png)

同样，使用选项 b、b@ofppt.ma 和账户 b 及其密码配置 PCB 上的电子邮件应用程序。

#### 1.5. 从 PCA 向 PCB 发送电子邮件。

使用 PCA 上的电子邮件应用程序，发送以下消息：

- 致：b@ofppt.ma；
- 主题：明文测试
- 消息：A 到 B 的一条秘密消息。

#### 1.6. 验证消息是否已被嗅探器拦截。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_180_0.png)

#### 1.7. 为什么黑客能够读取被嗅探器拦截的消息？

#### 2. 使用对称加密保护发送的消息。

#### 2.1. 下载并安装工具“Paranoia Text Encryption for PC”¹。





![](img/6cc1cc8bbb23ba3014958aee841c4ff5_181_0.png)

### 2.3. Define the parameters for this encryption:

- the plain text: ...................................
- 明文：.................................
- the encryption algorithm: ...................................
- 加密算法：.................................
- the number of bits in the key: ...................................
- 密钥的比特数：.................................
- the encryption key: ...................................
- 加密密钥：.................................
- the encrypted text: ...................................
- 加密文本：.................................
- the type of encryption: .................................
- 加密类型：.................................

### 2.4. Replace the “plain-text” contents of the previous message with the “encrypted message” and resend it.

### 2.4. 将前一条消息中的“明文”内容替换为“加密消息”，并重新发送。

### 2.5. Why is it impossible for a hacker to decrypt the message, even if they know the encryption algorithm, the number of bits in the key as well as the encrypted text?

### 2.5. 为什么即使黑客知道加密算法、密钥的比特数以及加密文本，也无法解密该消息？

### 2.6. What is the other name given to the “encryption key” in symmetric encryption?

### 2.6. 在对称加密中，“加密密钥”的另一个名称是什么？

### 2.7. Propose a secure method to exchange the “encryption key” between A and B.

### 2.7. 提出一种在A和B之间安全交换“加密密钥”的方法。

## 3. Secure a message using asymmetric encryption.

## 3. 使用非对称加密来保护消息。

### 3.1. Download and install the “AEP file encryption” tool².

### 3.1. 下载并安装“AEP文件加密”工具²。

### 3.2. Review the principle of asymmetric encryption.

### 3.2. 回顾非对称加密的原理。

### 3.3. Create the pair of keys for account A.

### 3.3. 为账户A创建密钥对。

From the Tools / RSA Key Generator/ menu, click on “Create new Key Pair”。

从“工具/RSA密钥生成器”菜单中，单击“创建新密钥对”。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_182_0.png)

Choose a folder on the desktop and fill in the comment with “A” then click on “Create” and confirm.

在桌面上选择一个文件夹，将注释填写为“A”，然后单击“创建”并确认。

### 3.4. Define the parameters for this encryption:

### 3.4. 为本次加密定义参数：

- the encryption algorithm: ....................................
- 加密算法：..................................
- the number of bits in the key: ....................................
- 密钥的比特数：..................................
- the name of the file containing the public key: ................................
- 包含公钥的文件名：..............................
- the name of the file containing the private key: ................................
- 包含私钥的文件名：..............................
- the type of encryption: ....................................................
- 加密类型：....................................................

2 http://www.aeppro.com/download/latest.shtml.

### 3.5. Display the contents of both keys using the “Notepad” software.

### 3.5. 使用“记事本”软件显示两个密钥的内容。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_183_0.png)

### 3.6. To encrypt messages exchanged between users A and B (using PCA and PCB), tick the appropriate key to use:

### 3.6. 要加密用户A和B之间交换的消息（使用PCA和PCB），请勾选应使用的适当密钥：

| Key to be used | Must use key to send encrypted data | | | | Must use key to decrypt the data received. | | | |
|---|---|---|---|---|---|---|---|---|
| 需使用的密钥 | 必须使用的密钥以发送加密数据 | | | | 必须使用的密钥以解密接收到的数据 | | | |
| User | Public for A | Private for A | Public for B | Private for B | Public for A | Private for A | Public for B | Private for B |
| 用户 | A的公钥 | A的私钥 | B的公钥 | B的私钥 | A的公钥 | A的私钥 | B的公钥 | B的私钥 |
| A | | | | | | | | |
| A | | | | | | | | |
| B | | | | | | | | |
| B | | | | | | | | |

### 3.7. Which of these objectives of cryptography was (were) satisfied by applying the method used in question 3.6?

### 3.7. 应用问题3.6中使用的方法满足了密码学的哪些目标？

- a) Authentication.
- a) 身份验证。
- b) Integrity.
- b) 完整性。
- c) Confidentiality.
- c) 保密性。
- d) Non-repudiation.
- d) 不可否认性。

### 3.8. Tick the correct key to use to digitally sign messages exchanged between users A and B:

### 3.8. 勾选用于对用户A和B之间交换的消息进行数字签名时应使用的正确密钥：

| | Must use key to send signed data | | | |
|---|---|---|---|---|
| | 必须使用的密钥以发送签名数据 | | | |
| User | Public for A | Private for A | Public for B | Private for B |
| 用户 | A的公钥 | A的私钥 | B的公钥 | B的私钥 |
| A | | | | |
| A | | | | |
| B | | | | |
| B | | | | |

### 3.9. Which of these objectives of cryptography was (were) satisfied by applying the method used in question 3.8?

### 3.9. 应用问题3.8中使用的方法满足了密码学的哪些目标？

- a) Authentication.
- a) 身份验证。
- b) Integrity.
- b) 完整性。
- c) Confidentiality.
- c) 保密性。
- d) Non-repudiation.
- d) 不可否认性。

## 4. Secure a message using hash functions.

## 4. 使用哈希函数保护消息。

### 4.1. Download and install the “HashTool” program³.

### 4.1. 下载并安装“HashTool”程序³。

### 4.2. Review the definition of a hash function.

### 4.2. 回顾哈希函数的定义。

### 4.3. In the dedicated zone, paste the text “A secret message from A to B” and compute the hash value.

### 4.3. 在专用区域中粘贴文本“A secret message from A to B”并计算哈希值。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_185_0.png)

Fill in the following values:

填写以下值：

- the text to be secured: ....................................
- 要保护的文本：..................................
- the hash function used: ....................................
- 使用的哈希函数：..................................
- the hash value: ....................................
- 哈希值：..................................

### 4.4. Using the same hash function and after making the required changes to the original text, write the first 10 digits of the hash value of the following texts:

### 4.4. 使用相同的哈希函数，并在对原始文本进行所需更改后，写出以下文本哈希值的前10位数字：

| Text | Modification | The first 10 digits of the hash value for the following texts |
| :--- | :--- | :--- |
| 文本 | 修改 | 以下文本哈希值的前10位数字 |
| A secret message from A to B. | Add a full-stop at the end | |
| A secret message from A to B. | 在末尾添加一个句号 | |
| A secret message from A to B | Add a space between the words “message” and “secret” | |
| A secret message from A to B | 在单词“message”和“secret”之间添加一个空格 | |
| A secret message from A to B | Add a space at the end of the sentence | |
| A secret message from A to B | 在句末添加一个空格 | |
| A secret message from A to B | Add a space at the beginning of the sentence | |
| A secret message from A to B | 在句首添加一个空格 | |

### 4.5. Using the same hash function and after making the requested changes to the original file, write the first ten digits of the Hash value of the following image files:

### 4.5. 使用相同的哈希函数，并在对原始文件进行所请求的更改后，写出以下图像文件哈希值的前十位数字：

NOTE: -- The original file, whose path is C:\Users\Public\Pictures\Sample Pictures\Chrysanthème.jpg, can be used as an example.

注意：-- 原始文件，其路径为 C:\Users\Public\Pictures\Sample Pictures\Chrysanthème.jpg，可用作示例。

| Image | Modification | The first 10 digits of the hash value of the following text |
|---|---|---|
| 图像 | 修改 | 以下文本哈希值的前10位数字 |
| [Image of red flower pattern] | No modification | |
| [红色花卉图案图像] | 无修改 | |
| [Image of red flower pattern] | Using the Paint software, add a small, nearly-invisible dot and save the file. | |
| [红色花卉图案图像] | 使用图画软件添加一个小的、几乎不可见的点并保存文件。 | |
| [Image of red flower pattern] | Resize the file to 99% using Paint and save the file. | |
| [红色花卉图案图像] | 使用图画软件将文件大小调整为99%并保存文件。 | |

### 4.6. Which of the objectives of cryptography has been (were) satisfied by applying the procedures used in questions 4.4 and 4.5?

### 4.6. 应用问题4.4和4.5中使用的程序满足了密码学的哪些目标？

- a) Authentication.
- a) 身份验证。
- b) Integrity.
- b) 完整性。
- c) Confidentiality.
- c) 保密性。
- d) Non-repudiation.
- d) 不可否认性。

## IPsec VPNs

## IPsec VPN

This chapter will focus on the following topics:

本章将重点介绍以下主题：

- the IPsec protocol:
- IPsec协议：
- objectives of IPsec,
- IPsec的目标，
- protocols based on IPsec,
- 基于IPsec的协议，
- the IPsec framework,
- IPsec框架，
- the IPsec security association,
- IPsec安全关联，
- IPsec modes;
- IPsec模式；
- the IKE protocol:
- IKE协议：
- components of IKE,
- IKE的组件，
- the IKE phases,
- IKE阶段，
- the IPsec framework,
- IPsec框架，
- the IPsec security association,
- IPsec安全关联，
- the differences between the two IKE versions;
- 两个IKE版本之间的区别；
- the configuration of the IPsec VPN.
- IPsec VPN的配置。

### 9.1. The IPsec protocol

### 9.1. IPsec协议

#### 9.1.1. Objectives of IPsec

#### 9.1.1. IPsec的目标

IPsec is a security architecture, based on standardized norms, that allows two entities to establish secure communication.

IPsec是一种基于标准化规范的安全架构，允许两个实体建立安全通信。

The objectives of the IPsec protocol may be summarized as follows:

IPsec协议的目标可总结如下：

- confidentiality: this consists of transforming clear text into an encrypted text;
- 保密性：这包括将明文转换为加密文本；
- data integrity: uses a hash function or HMAC code to ensure that the data was not modified as it travelled over the network;
- 数据完整性：使用哈希函数或HMAC代码确保数据在通过网络传输过程中未被修改；
- authentication: consists of end-to-end authentication of VPNs using a pre-shared key (PSK) or digital signature;
- 身份验证：包括使用预共享密钥(PSK)或数字签名对VPN进行端到端身份验证；
- antireplay protection: ensuring that no packet was re-sent during the data exchange.
- 重放保护：确保在数据交换过程中没有数据包被重新发送。

#### 9.1.2. Basic IPsec protocols

#### 9.1.2. 基本IPsec协议

The three main components of IPsec are:

IPsec的三个主要组件是：

- AH: this protocol only ensures the integrity of the data and the authentication of the source. AH is appropriate when confidentiality is not required or permitted;
- AH：此协议仅确保数据的完整性和源的身份验证。当不需要或不允许保密性时，AH是合适的；
- ESP: in addition to the functions offered by AH it offers data confidentiality. It is for these reasons that this is the most widely used protocol;
- ESP：除了AH提供的功能外，还提供数据保密性。出于这些原因，这是最广泛使用的协议；
- Internet Key Exchange (IKE): is a protocol responsible for negotiating a connection before an IPsec transmission is possible.
- Internet Key Exchange (IKE)：是一种在IPsec传输成为可能之前负责协商连接的协议。

#### 9.1.3. The IPsec framework

#### 9.1.3. IPsec框架

IPsec is a norm that uses existing algorithms to implement privacy, integrity, authentication, and key exchange.

IPsec是一种使用现有算法来实现隐私、完整性、身份验证和密钥交换的规范。

The combination of these elements offers the administrator a great deal of flexibility, especially when configuring several connections with different security options.

这些元素的组合为管理员提供了很大的灵活性，特别是在配置具有不同安全选项的多个连接时。

An IPsec frame contains five basic elements that must be configured to ensure a secured connection.

IPsec帧包含五个基本元素，必须配置这些元素以确保安全连接。

Figure 9.1 depicts the components of the IPsec configuration.

图9.1描绘了IPsec配置的组件。

Figure 9.1. The IPsec framework

图9.1. IPsec框架

#### 9.1.4. The IPsec security association

#### 9.1.4. IPsec安全关联

- An IPsec Security Association (SA) makes it possible to specify the security settings associated with a communication.
- IPsec安全关联(SA)使得可以指定与通信相关的安全设置。
- Each SA is identified uniquely by:
    - the destination address of the packets;
    - 每个SA由以下内容唯一标识：
    - 数据包的目标地址；
    - the basic IPsec protocol (AH or ESP);
    - 基本IPsec协议(AH或ESP)；
    - the SA identifier: the SPI.
    - SA标识符：SPI。
- An SA is unidirectional. We thus need two SAs to protect communications in both directions.
- SA是单向的。因此我们需要两个SA来保护双向通信。

All SAs together make up the Security Policy Database (SPD).

所有SA共同构成安全策略数据库(SPD)。

#### 9.1.5. IPsec modes

#### 9.1.5. IPsec模式

There are two modes in which IPsec can be used: transport mode and tunnel mode.

IPsec可以使用两种模式：传输模式和隧道模式。

- Transport mode:
- 传输模式：
    - protects data within a packet. However, the original IP headers remain intact;
    - 保护数据包内的数据。但是，原始IP头保持完整；
    - is used for communications between two hosts that support IPsec;
    - 用于两个支持IPsec的主机之间的通信；
    - is generally combined with the GRE protocol to protect traffic.
    - 通常与GRE协议结合使用以保护流量。




- 隧道模式：
  - 原始 IP 数据包的完整性受到保护；
  - IPSec 封装原始数据包，对其加密，添加新的 IP 头，然后将其发送到 VPN 隧道另一端；
  - 隧道模式最常用于 IPsec 网关之间（Cisco 路由器或 ASA 防火墙）。

### 9.2. IKE 协议

#### 9.2.1. 简介

Internet 密钥交换 (IKE) 是一种用于动态协商与 IPSec 通信相关的安全设置的协议。必须注意的是，IPsec 实现也可以支持对这类设置交换的手动管理。但是，IKE 协议被认为更快且更安全。

IKE 有两个版本可用。版本 v2 提供多项优势，包括（但不限于）修复 IKEv1 中的漏洞以及优化带宽使用。

#### 9.2.2. IKE 组件

IKE 是三种协议的组合，即：ISAKMP、SKEME 和 Oakley。这些协议被组合在一起以确保协商和建立安全通信。

- ISAKMP：使能够协商 IPsec 通信两端之间的安全关联（SA）。
- Oakley：使用 Diffie-Hellman 算法在 IPsec 连接双方之间进行密钥交换。
- SKEME：定义确保匿名性和不可否认性的密钥交换技术。

#### 9.2.3. IKE 阶段

IKE 协议在两个主要阶段运行，以在两个 IPsec 点之间创建安全通信通道。第一阶段用于协商隧道安全设置，而第二阶段确保数据的安全传输。

##### 9.2.3.1. IKE 第 1 阶段

第 1 阶段的特征可总结如下：

- 目标是建立一个 ISAKMP SA（或 IKE SA）。IKE 协商通信的安全选项，例如加密算法、哈希函数、身份验证方法和 Diffie-Hellman；
- SA 协商是双向的；
- 此阶段生成三个密钥。两个密钥用于保护 ISAKMP SA 消息，第三个密钥用于生成另外两个用于保护 IPsec 交换的密钥；
- 为证明其身份，发送方发送与身份及所有先前消息相关联的密钥的哈希值。身份密钥要么是共享密钥，要么是一对私钥/公钥；
- 生成多个密钥这一事实保证了数据机密性。即使将来共享密钥已知（或所使用的公钥被攻破），数据也始终会受到保护，因为它是由会话密钥加密的。会话密钥是身份密钥与随机（nonce）值以及其他几个难以预测的值的组合；
- 此阶段可以在两种模式下建立：
  - 主模式；由六条消息组成。它通过加密最后两条消息来保证双方的匿名性；
  - 激进模式：仅由三条消息组成。因此，它更快，但不提供主模式的优势。

##### 9.2.3.2. IKE 第 2 阶段

第 2 阶段的特征可总结如下：

- 目标是建立一个 IPsec SA；
- SA 协商是 *单向的*。

此阶段定义的唯一模式是 *快速模式*。

##### 9.2.3.3. 两个 IKE 版本之间的差异

版本 1 和 2 之间的主要差异包括：

- 消息交换简化：
  - IKEv1 交换九条消息（第 1 阶段 = 6，第 2 阶段 = 3）；
  - IKEv2 交换六条消息（第 1 阶段 = 4，第 2 阶段 = 2）；
- 安全性：
  - IKEv1 易受拒绝服务 (DoS) 攻击；
  - IKEv2 受到 DoS 攻击防护。仅在申请者经过身份识别后才处理请求。

### 9.3. 站点到站点 VPN 配置

#### 9.3.1. 简介

站点到站点 VPN 连接两个远程局域网，以便安全地通过 *互联网* 共享资源。它以内部主机透明的方式设置在 VPN 连接的两侧之间。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_193_0.png)

**图 9.3. 站点到站点 VPN**

#### 9.3.2. IPsec VPN 配置

### 要遵循的步骤

要使用 CLI 命令配置站点到站点 VPN，请执行以下步骤：

- 1) 通过创建扩展 ACL 识别“感兴趣流量”；
- 2) 创建 IKE 策略并配置第 1 阶段所需的设置；
- 3) 指定 PSK 共享密钥并识别 VPN 隧道另一端的 IP 地址；
- 4) 创建第 2 阶段所需的 IPsec 策略；
- 5) 创建加密映射并配置加密映射的具体内容；
- 6) 将加密映射应用到接口；
- 7) 验证 VPN 隧道设置。

注意：此顺序对所有步骤并非必需。

### 配置示例

考虑以下网络拓扑：

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_194_0.png)

要在两个站点之间配置 VPN 链路，请按以下步骤操作：

- 1) 创建 ACL 以识别感兴趣的流量。

| 命令 | 说明 |
|---|---|
| R1(config)# ip access-list extended VPN-ACL | 创建扩展 ACL。 |
| R1(config-ext-nacl)# permit ip 192.168.1.0 0.0.0.255 192.168.2.0 0.0.0.255 | 识别“感兴趣流量”。 |

- 2) 创建 IKE 策略并配置第 1 阶段所需的设置。

| 命令 | 说明 |
|---|---|
| R1(config)# crypto isakmp policy 10 | 创建 IKE 策略。 |
| R1(config-isakmp)# authentication pre-share | 定义身份验证方法。 |
| R1(config-isakmp)# encr aes 128 | 定义加密协议。 |
| R1(config-isakmp)# hash sha | 定义哈希函数。 |
| R1(config-isakmp)# group 5 | 定义要使用的 DH 组。 |
| R1(config-isakmp)# lifetime 86400 | 定义 IKE 超时。 |

- 3) 指定共享密钥 (PSK) 并识别 VPN 隧道另一端的 IP 地址。

| 命令 | 说明 |
|---|---|
| R1(config)# crypto isakmp key PassVPN address 44.113.202.129 | 定义共享密钥和 VPN 隧道另一端的 IP 地址。 |

- 4) 创建第 2 阶段所需的 IPsec 策略。

| 命令 | 说明 |
|---|---|
| R1(config)# crypto ipsec transform-set R1-to-R2-SET esp-sha-hmac esp-aes 128 | 定义第 2 阶段的通信设置。 |

- 5) 创建加密映射并配置加密映射的参数。

| 命令 | 说明 |
|---|---|
| R1(config)# crypto map R1-to-R2-MAP 10 ipsec-isakmp | 创建与 IKE 策略编号 10 连接的加密映射。 |
| R1(config-crypto-map)# set transform-set R1-to-R2-SET | 定义第 2 阶段所需的 IPsec 策略标识符。 |
| R1(config-crypto-map)# set peer 44.113.202.129 | 设置 VPN 隧道另一端的 IP 地址。 |
| R1(config-crypto-map)# match address VPN-ACL | 设置感兴趣流量的 ACL ID。 |

- 6) 将加密映射应用到接口。

| 命令 | 说明 |
|---|---|
| R1(config)# interface s0/0<br>R1(config-if)# crypto map R1-to-R2-MAP | 选择接口并应用加密映射。 |

- 7) 验证 VPN 隧道设置。

| 命令 | 说明 |
|---|---|
| R1# show crypto isakmp transform-set | 显示第 2 阶段所需 IPsec 策略的配置。 |
| R1# show crypto map | 显示加密映射配置。 |
| R1# show crypto ipsec sa | 显示已建立的 IPsec 隧道。 |

## 9.4. 应用练习

练习 13。

### 拓扑

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_196_0.png)

有关此图的彩色版本，请参见 www.iste.co.uk/sadiqui/computer.zip

### 寻址表

| 设备 | 接口 | IP 地址 | 子网掩码 | 网关 |
|---|---|---|---|---|
| R1 | F0/0 | 192.168.0.1 | /24 | - |
| | F0/1 | 192.168.1.1 | /24 | - |
| | S0/0 | 192.168.10.1 | /30 | - |
| R2 | S0/0 | 192.168.10.2 | /30 | - |
| | F0/0 | 192.168.2.1 | /24 | - |
| ServerS2 | NIC | 192.168.0.2 | /24 | 192.168.0.1 |
| PC1 | NIC | 192.168.1.2 | /24 | 192.168.1.1 |
| ServerS1 | NIC | 192.168.2.2 | /24 | 192.168.2.1 |

### 目标

- 保护密码；
- 使用 Cisco IOS 配置站点到站点 IPsec VPN。

### 要使用的软件

- Packet Tracer。

### A 部分：建立基本设备设置

- 1. 配置基本设备设置。
  - 1.1. 按拓扑图所示配置主机名。
  - 1.2. 根据寻址表将 IP 地址应用到设备接口。
  - 1.3. 为串行接口设置时钟值 128000。
- 2. 使用 EIGRP 配置路由。
  - 2.1. 在两台路由器上启用 EIGRP，AS ID 使用值 1。
  - 2.2. 为 R1 设置 RID 值 1.1.1.1，为 R2 设置 RID 值 2.2.2.2。
  - 2.3. 将所有网络添加到 EIGRP。
  - 2.4. 测试所有网络元素之间的连通性。



## Part B: 保护密码

在R1上

- 1. 设置最小密码长度为8个字符。
- 2. 为特权模式设置密码“Ci$c0ena”。
- 3. 配置控制台、辅助端口和虚拟访问线路。
  - 3.1. 将“Ci$c0con”设置为控制台端口密码，并将非活动间隔设置为5分钟。
  - 3.2. 将“Ci$c0vty”设置为VTY线路的密码，并将非活动间隔设置为2分钟。
  - 3.3. 禁用辅助端口。
- 4. 加密所有密码。

## Part C: 使用Cisco IOS配置站点到站点IPsec VPN

加密Server1和Server2之间的流量。

### 1. 在R1和R2上创建扩展ACL以识别“有趣流量”。

```
R1(config)# access-list 101 permit ip 192.168.0.0 0.0.255.255 192.168.2.0 0.0.255.255
R2(config)# access-list 101 permit ip 192.168.2.0 0.0.255.255 192.168.0.0 0.0.255.255
```

### 2. 创建IKE策略并配置第1阶段所需的设置。

### 2.1. IKE协议第1阶段的作用是什么？

### 2.2. 在R1上配置第1阶段所需的设置。

```
R1(config)# crypto isakmp policy 10
R1(config-isakmp)# authentication pre-share
R1(config-isakmp)# encryption aes 256
R1(config-isakmp)# hash sha
R1(config-isakmp)# group 5
R1(config-isakmp)# lifetime 3600
R1(config-isakmp)# end
```

### 2.3. 根据上述命令，填写以下表格：

| IKE第1阶段设置 |
|---|
| ISAKMP策略ID | |
| 身份验证方法 | |
| 加密算法 | |
| 加密密钥使用的位数 | |
| 哈希算法 | |
| Diffie-Hellman组 | |
| 安全关联的生存期 | |

### 2.4. 验证IKE策略的设置。

```
R1# show crypto isakmp policy
Global IKE policy
Protection suite of priority 10
encryption algorithm: AES - Advanced Encryption Standard
(256 bit keys).
Hash algorithm: Secure Hash Standard
Authentication method: Pre-Shared Key
Diffie-Hellman group: #5 (1536 bit)
Lifetime: 3600 seconds, no volume limit
```

### 2.5. 在R2上重复上述相同的配置。

### 3. 指定PSK共享密钥并识别VPN隧道另一端的IP地址。

在两台路由器上配置预共享密钥。
```
R1(config)# crypto isakmp key Tri123 address 192.168.10.2
R2(config)# crypto isakmp key Tri123 address 192.168.10.1
```

### 4. 创建第2阶段所需的IPsec策略。

### 4.1. IKE协议第2阶段的作用是什么？

### 4.2. 在R1上创建第2阶段所需的IPsec策略。

```
R1(config)# crypto ipsec transform-set 10 esp-aes 256 esp-sha-hmac
```

### 4.3. 根据上述命令，填写以下表格：

| IKE第2阶段设置 | |
|---|---|
| 转换集策略的标识符。 | |
| 使用的基本IPsec协议。 | |
| 加密算法 | |
| 加密密钥使用的位数。 | |
| 哈希算法 | |

注意.— 可以修改IPsec关联的生存期，使其不同于ISAKMP关联的生存期。可以使用以下命令：

```
R1(config)# crypto ipsec security-association lifetime seconds 1800
```

### 4.4. 验证转换集策略的设置。

```
R1# show crypto ipsec transform-set
Transform set 10: { esp-256-aes esp-sha-hmac }
will negotiate = { Tunnel, },
```

### 4.5. 在R2上重复相同的配置。

### 5. 创建加密映射并配置加密映射参数。

### 5.1. 在R1上创建加密映射。

```
R1(config)# crypto map carte_crypto1 10 ipsec-isakmp
R1(config-crypto-map)# match address 101
R1(config-crypto-map)# set peer 192.168.10.2
R1(config-crypto-map)# set transform-set 10
R1(config-crypto-map)# exit
```

### 5.2. 根据上述命令，填写以下表格：

| 加密映射的设置 |
| :--- |
| 加密映射的名称 | |
| ISAKMP策略ID | |
| 有趣流量的ACL标识符 | |
| VPN隧道另一端的IP地址 | |
| 转换集策略的标识符 | |

### 5.3. 在R2上重复上述相同的配置。

### 6. 将加密映射应用于R1和R2的相应接口。

```
R1(config)# interface S0/0
R1(config-if)# crypto map carte_crypto1
R2(config)# interface S0/0
R2(config-if)# crypto map carte_crypto2
```

### 7. 验证VPN隧道设置。

### 7.1. 验证加密映射设置。

```
R1# show crypto map
Crypto Map carte_crypto1 10 ipsec-isakmp
Peer = 192.168.10.2
Extended IP access list 101
access-list 101 permit ip 192.168.0.0 0.0.255.255 192.168.2.0 0.0.255.255
Current peer: 192.168.10.2
Security association lifetime: 4608000 kilobytes/3600 seconds
PFS (Y/N): N
Transform sets={
10,
}
Interfaces using crypto map carte_crypto1:
Serial0/0
```

### 7.2. 显示ISAKMP和IPsec安全关联。

```
R1# show crypto isakmp sa
IPv4 Crypto ISAKMP SA
dst   src   state   conn-id slot status

IPv6 Crypto ISAKMP SA
R1# show crypto ipsec sa
interface: Serial0/0/0
Crypto map tag: carte_crypto1, local addr 192.168.10.1
protected vrf: (none)
local ident (addr/mask/prot/port): (192.168.0.0/255.255.255.0/0/0)
remote ident (addr/mask/prot/port): (192.168.2.0/255.255.255.0/0/0)
current_peer 192.168.10.2 port 500
PERMIT, flags={origin_is_acl ,}
...
```

### 7.3. 在Server2、PC1和Server1之间发送ping，并再次显示ISAKMP和IPsec安全关联。

```
Router# show crypto isakmp sa
IPv4 Crypto ISAKMP SA
dst   src   state   conn-id slot    status
192.168.10.2 192.168.10.1 QM_IDLE   1033 0 ACTIVE
```

### 7.4. 将两台路由器之间的串行链路替换为FastEthernet（或以太网）链路，并添加Sniffer以捕获两台路由器之间交换的帧。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_202_0.png)

注意.— FastEthernet接口的IP地址必须与串行接口的IP地址相同。

### 7.5. 将加密映射应用于R1和R2的相应接口。

```
R1(config)# interface F0/2
R1(config-if)# crypto map carte_crypto1
R2(config)# interface F0/1
R2(config-if)# crypto map carte_crypto2
```

### 7.6. 在Server 2和Server 1之间ping，并解释Sniffer捕获的IPsec帧。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_203_0.png)

### 7.7. 为什么只为Server2和Server1之间的流量创建了安全关联，而没有为PC1和Server1之间的流量创建安全关联？

注意.— 如果在保存配置后重启其中一台路由器，也可以捕获ISAKMP帧。

## 学习高级防火墙

本章将重点介绍以下主题：

- 思科ASA防火墙：
  - ASA型号，
  - ASA设备的使用模式，
  - ASA 5505概述；
- 使用CLI配置ASA：
  - ASA许可证类型，
  - 配置接口，
  - 配置DHCP服务，
  - 配置ACL，
  - 配置NAT服务，
  - 配置AAA；
- 使用CCP和ASDM图形工具配置思科设备；
- TMG 2010防火墙。

### 10.1. 思科ASA防火墙

#### 10.1.1. 简介

思科ASA（自适应安全设备）是一种结合防火墙、防病毒、入侵防御系统（IPS）和VPN功能的安全设备。

它因此提供了广泛的技术和解决方案，用于有效的网络安全。

#### 10.1.2. ASA型号

ASA有不同型号。所有型号都提供高级防火墙和VPN功能。型号之间最大的区别在于每个型号可以管理的最大流量以及接口的数量和类型。ASA型号根据组织的要求选择，例如流量、每秒最大连接数和公司预算。

ASA设备还支持虚拟化环境。这些环境运行与物理设备相同的软件，以提供相同的安全功能。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_205_0.png)

图10.1 不同的ASA型号¹

注意.— 本章将限于研究ASA 5505型号和防火墙功能。

#### 10.1.3. ASA设备的使用模式

- 路由器模式：
- 这是常规的部署模式；


- 此模式支持多个接口，且每个接口位于不同的子网中，拥有独立的 IP 地址；
- ASA 在网络中表现得像路由器一样，并可在连接的网络之间执行网络地址转换 (NAT)。

### 透明模式

- ASA 作为第 2 层组件工作；
- 此模式支持多个接口，包括动态路由协议和 VPN 功能。

#### 10.1.4. ASA 5505 概述

### ASA 5505 正面视图

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_206_0.png)

此图的彩色版本，请参见 www.iste.co.uk/sadiqui/computer.zip

| | |
|---|---|
| 1 | USB 接口：主要用于备份或更新。 |
| 2 | 速度指示灯：<br>– 绿灯常亮表示带宽为 100 Mbps；<br>– 灯光熄灭表示带宽为 10 Mbps。 |
| 3 | 链路指示灯：<br>– 绿灯常亮表示已建立网络链路；<br>– 绿灯闪烁表示有网络活动。 |
| 4 | 电源指示灯：绿灯亮表示设备正在接收电力。 |
| 5 | 状态指示灯：<br>– 电源指示灯：绿灯亮表示设备正在启动；<br>– 绿灯常亮表示系统正在运行；<br>– 橙灯常亮表示系统启动失败。 |
| 6 | 活动指示灯：绿灯亮表示在配置为交换时，此 ASA 设备处于活动状态。 |
| 7 | VPN 指示灯：绿灯亮表示有一个或多个 VPN 隧道处于活动状态。 |
| 8 | SSC 指示灯：绿灯亮表示 SSC 卡插在 SSC 插槽中（参见下图）。 |

### ASA 5505 背面视图

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_207_0.png)

此图的彩色版本，请参见 www.iste.co.uk/sadiqui/computer.zip

| 1 | 电源 |
|---|---|
| 2 | SSC 插槽：此插槽可用于插入提供 Cisco 高级安全检测和预防服务 (IPS) 的 SSC 卡 |
| 3 | USB 接口 |
| 4 | 复位按钮 |
| 5 | 控制台端口 |
| 6 | 防盗缆索插槽 |
| 7 | 10/100 Mbps 以太网端口（端口 0 至 5） |
| 8 | PoE 10/100 Mbps 端口（端口 6 至 7） |

#### 10.1.5. ASA 安全级别

ASA 根据可靠性为不同网络段分配安全级别，以进行分类。安全级别具有以下特征：

- 安全级别数值范围为 0（不可靠）至 100（非常可靠）；
- 安全级别越高，接口越可靠；
- 每个激活的 ASA 接口必须具有名称和安全级别；
- 默认情况下，名为“inside”的接口取值为 100，名为“outside”的接口取值为 0。

#### 10.1.6. 使用 CLI 配置 ASA

##### 10.1.6.1. ASA 5505 许可证类型

ASA 5505 预装操作系统，提供两种许可证：“基本许可证”和“安全增强许可证”。安全增强许可证支持更多功能。

| 特性 | 基本许可证 | 安全增强许可证 |
|---|---|---|
| 防火墙的最大连接数 | 10,000 | 25,000 |
| VPN 会话的最大数量 | 10 | 25 |
| 可创建的 VLAN 最大数量 | 3，且限制仅两个区域可相互通信。 | 20，区域间通信无限制。 |

##### 10.1.6.2. ASA 上的 CLI 概述

ASA 设备的操作系统提供了命令行接口 (CLI)，其外观与 Cisco 路由器使用的 IOS 类似。不过，两种操作系统中的多条命令有所不同。

| IOS 系统上的命令 | ASA 上的等效命令 |
|---|---|
| enable secret password | enable password password |
| line con 0 password password login | passwd password |
| ip route | route outside |
| show ip interfaces brief | show interfaces ip brief |
| show ip route | show route |
| show vlan | show switch vlan |
| show ip nat translations | show xlate |
| copy running-config startup-config | write [ memory ] |

##### 10.1.6.3. 配置接口

- ASA 5510 有两种类型的接口：
- **路由接口**：这些接口直接配置 IP 地址。配置通过 SVI（交换虚拟接口）进行。
- 第 2 层以太网接口：这些接口被分配到 VLAN 接口。

- 在 ASA 上配置 SVI，请执行以下操作：

| 命令 | 描述 |
|---|---|
| ciscoasa(config)# interface vlan vlan-id | 创建 SVI |
| ciscoasa(config-if)# nameif { inside \| outside \| name } | 为 SVI 命名 |
| ciscoasa(config-if)# security-level level | 定义或修改 SVI 的安全级别 |
| ciscoasa(config-if)# ip address ip-address netmask | 为 SVI 分配 IP 地址和子网掩码 |
| ciscoasa(config-if)# no forward interface vlan vlan-id2 | 防止两个 VLAN 之间的流量路由 |

- 在 ASA 上配置第 2 层接口，请执行以下操作：

| 命令 | 描述 |
|---|---|
| ciscoasa(config)# interface interface/number | 进入接口 |
| ciscoasa(config-if)# switchport access vlan vlan-id | 将其分配到 VLAN |
| ciscoasa(config-if)# no shutdown | 激活接口 |

##### 10.1.6.4. DHCP 服务配置

可以使用以下步骤在 ASA 上配置 DHCP 服务：

| 命令 | 描述 |
|---|---|
| ciscoasa(config)# dhcpd address [ start-of-pool ]-[ end-of-pool ] inside | 定义要分配给内部用户的 IP 地址池 |
| ciscoasa(config)# dhcpd domain domain-name | 配置域名 |
| ciscoasa(config)# dhcpd dns dns-ip-address | 配置 DNS IP 地址 |
| ciscoasa(config)# dhcpd lease seconds | 配置租用期 |
| ciscoasa(config)# dhcpd enable interface-name | 在指定的 ASA 接口上启用 DHCP 服务器服务 |

注意：现在可以尝试练习 14。

##### 10.1.6.5. ACL 配置

- ASA ACL 与 IOS ACL 之间有许多相似之处。主要差异可总结如下：

- ASA ACL 使用网络掩码而非通配符掩码；
- ASA ACL 使用名称而非编号；
- 默认情况下，接口的安全级别会在未配置 ACL 的情况下应用访问控制。

- 可按以下步骤在 ASA 上配置 ACL：

| 命令 | 描述 |
|---|---|
| ciscoasa(config)# access-list id extended { deny \| permit } protocol { source_addr source_mask \| any \| host src_host \| interface src_if_name [ operator port [ port ]{ dest_addr dest_mask } \| any \| host dst_host \| interface dst_if_name [ operator port [ port ]] \| object-group acl-id } | 创建扩展 ACL |
| ciscoasa(config)# access-group acl-id { in \| out } interface interface-name | 在接口上激活 ACL |

##### 10.1.6.6. NAT 服务配置

- ASA 支持以下 NAT 类型：

- 动态 NAT：将多个专用 IP 地址转换为多个公共 IP 地址；
- 动态 PAT：将多个专用 IP 地址转换为一个公共 IP 地址；
- 静态 NAT：将一个专用 IP 地址转换为一个公共 IP 地址。

- 在 ASA 上配置动态 NAT，请执行以下操作：

| 命令 | 描述 |
|---|---|
| ciscoasa(config)# object network public-pool-obj | 为公共 IP 地址池创建网络对象 |
| ciscoasa(config-network-object)# {host ip_addr \| subnet net_addr net_mask \| range ip_addr_1 ip_addr_2 } | 使用主机地址、子网或 IP 地址范围定义公共 IP 地址池 |
| ciscoasa(config)# object network private-pool-obj | 为专用 IP 地址池创建另一个网络对象 |
| ciscoasa(config-network-object)# { subnet net_addr net_mask \| range ip_addr_1 ip_addr_2 } | 使用子网或地址范围定义内部 IP 地址池 |
| ciscoasa(config-network-object)# nat ( real-ifc , mapped-ifc ) dynamic public-pool-object | 在两个接口之间激活动态 NAT |

- 在 ASA 上配置动态 PAT，请执行以下操作：

| 命令 | 描述 |
|---|---|
| ciscoasa(config)# object network pat-obj-name | 为内部 IP 地址池创建网络对象 |
| ciscoasa(config-network-object)# { subnet net_addr net_mask \| range ip_addr_1 ip_addr_2 } | 使用子网或地址范围定义内部 IP 地址池 |
| ciscoasa(config-network-object)# nat ( real-ifc , mapped-ifc ) dynamic [ interface \| ip-address ] | 在此接口与公共接口之间激活动态 PAT |

- 在 ASA 上配置静态 NAT，请执行以下操作：

| 命令 | 描述 |
|---|---|
| ciscoasa(config)# object network static-nat-obj-name | 为内部 IP 地址创建网络对象 |
| ciscoasa(config-network-object)# host ip_addr | 定义主机的内部 IP 地址 |
| ciscoasa(config-network-object)# nat ( real-ifc , mapped-ifc ) static mapped-ip-addr | 在内部 IP 地址与公共接口之间激活静态 NAT |





| Command | Description |
|---|---|
| ciscoasa(config)# access-list acl-id extended permit ip any host inside_host | 创建扩展 ACL，以允许外部用户访问内部 IP 地址 |
| ciscoasa(config-if)# access-group acl-id interface outside | 将 ACL 应用到相应的接口 |

##### 10.1.6.7. AAA 配置

- ASA 可以配置为使用本地用户数据库或外部服务器对其自身进行身份验证，或同时使用两种方法。

- 要为访问 EXEC、HTTP、SSH 或 Telnet 模式激活 AAA 身份验证，请执行以下操作：

| Command | Description |
|---|---|
| ciscoasa(config)# aaa authentication enable console LOCAL | 使用本地数据库为访问 EXEC 模式激活 AAA 身份验证 |
| ciscoasa(config)# aaa authentication http console LOCAL | 使用本地数据库为 HTTP 访问激活 AAA 身份验证 |
| ciscoasa(config)# aaa authentication ssh console LOCAL | 使用本地数据库为 SSH 访问激活 AAA 身份验证 |
| ciscoasa(config)# aaa authentication telnet console LOCAL | 使用本地数据库为 Telnet 访问激活 AAA 身份验证 |

- 要使用外部服务器激活 AAA 身份验证，请执行以下操作：

| Command | Description |
|---|---|
| ciscoasa(config)# aaa-server server-tag protocol [ tacacs+ \| radius ] | 创建 TACACS+ 或 RADIUS 服务器组 |
| ciscoasa(config-aaa-server-group)# aaa-server server-tag [ (interfacename) ] host { server-ip \| name } [ key ] | 定义 AAA 服务器的设置 |
| ciscoasa(config)# aaa authentication { enable \| http \| ssh \| telnet } console server-tag [ LOCAL ] | 基于外部服务器激活 AAA 身份验证 |

### 10.2. 应用练习

练习 14.-

### 拓扑

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_213_0.png)

要查看此图的彩色版本，请参阅 www.iste.co.uk/sadiqui/computer.zip

### 寻址表

| Device | Interface | IP address | Subnet mask | Gateway |
|---|---|---|---|---|
| ASA1 | E0/0 (VLAN2) | 212.212.1.1 | /30 | - |
| | E0/1 (VLAN1) | 192.168.1.1 | /24 | - |
| R1 | F0/0 | 212.212.1.2 | /30 | - |
| | F0/1 | 192.168.2.1 | /24 | - |
| PC1 | NIC | 192.168.1.2 | /24 | 192.168.1.1 |
| PC2 | NIC | 192.168.2.2 | /24 | 192.168.2.1 |
| Server1 | NIC | 192.168.2.3 | /24 | 192.168.2.1 |

### 目标

- 安全密码；
- 使用 CLI 配置 ASA 5505 防火墙。

### 要使用的软件

- Packet Tracer.

### 部分 A：建立基本设备配置

- 1. 配置基本设备设置。

### 部分 B：保护密码

在 R1 上

- 1. 设置最小密码长度为 8 个字符。
- 2. 为特权模式设置密码“Ci$c0ena”。
- 3. 配置控制台、辅助端口和虚拟访问线路。
- 3.1. 将“Ci$c0con”设置为控制台端口密码，并将非活动间隔设置为 5 分钟。
- 3.2. 将“Ci$c0vtty”设置为 VTY 线路上的密码，并将非活动间隔设置为 2 分钟。
- 3.3. 禁用辅助端口。
- 4. 加密所有密码。
- 5. 创建指向公司内部网络的静态路由。

```
R1(config)#ip route 192.168.1.0 255.255.255.0 212.212.1.1
```

### 部分 C：使用 CLI 配置 ASA 5505 防火墙

- 1. 确定 ASA 设备的基本特性。
- 1.1. 回顾 ASA 设备所扮演的角色。
- 1.2. 显示 ASA 设备的特性。

```
ciscoasa>
ciscoasa>enable
Password:       (empty)
ciscoasa#
ciscoasa#show version
```

```
Cisco Adaptive Security Appliance Software Version 8.4(2)
Device Manager Version 6.4(5)
Compiled on Wed 15-Jun-11 18:17 by mnguyen
System image file is "disk0:/asa842-k8.bin"
Config file at boot was "startup-config"
ciscoasa up 19 minutes 18 seconds
Hardware: ASA5505, 512 MB RAM, CPU Geode 500 MHz
Internal ATA Compact Flash, 128MB
BIOS Flash M50FW016 @ 0xfff00000, 2048KB
...
```

### 1.3. 根据上一命令的输出，填写以下表格：

| ASA 设备的特性 | |
|---|---|
| 正在运行的 ASA 软件版本 | |
| 映像文件名 | |
| RAM 大小 | |
| Flash 存储器大小 | |
| 以太网端口数量 | |
| 系统许可证类型 | |
| 可创建的 VLAN 数量 | |

### 2. 配置 ASA 设备的基本设置。

### 2.1. 配置主机名。

```
ciscoasa(config)#hostname ASA1
ASA1(config)#
```

### 2.2. 设置系统日期。

```
ASA1(config)#clock set 14:25:00 May 12 2018
```

### 2.3. 配置特权模式密码。

```
ASA1(config)#enable password 1234
```

### 2.4. 配置 Telnet 连接密码。

```
ASA1(config)#passwd Cisco123
```

### 3. 从内部网络配置对 ASA 的 Telnet 和 SSH 访问。

### 3.1. 从内部网络配置 Telnet 访问。

```
ASA1(config)#telnet 192.168.1.0 255.255.255.0 inside
```

### 3.2. 将 Telnet 超时设置为 10 分钟。

```
ASA1(config)#telnet timeout 10
```

### 3.3. 配置对 ASA 的远程 SSH 访问。

```
ASA1(config)#crypto key generate rsa modulus 1024
WARNING: You have a RSA keypair already defined named <Default-RSA-Key>.
Do you really want to replace them? [yes/no]: y
Keypair generation process begin. Please wait..
ASA1(config)# ssh 192.168.1.0 255.255.255.0 inside
ASA1(config)# ssh timeout 10
```

### 4. 配置 ASA 设备的接口。

### 4.1. 为内部网络配置 VLAN 1 逻辑接口，并将安全级别设置为最高。

```
ASA1 (config)# interface vlan 1
ASA1 (config-if)# nameif inside
ASA1 (config-if)# ip address 192.168.1.1 255.255.255.0
ASA1 (config-if)# security-level 100
```

### 4.2. 为外部网络配置 VLAN 2 逻辑接口，并将安全级别设置为最低。

```
ASA1 (config)# interface vlan 2
ASA1 (config-if)# nameif outside
ASA1 (config-if)# ip address 212.212.1.1 255.255.255.252
ASA1 (config-if)# security-level 0
```

### 4.3. 将 ASA 端口分配给连接的 VLAN。

```
ASA1 (config)# interface e0/1
ASA1 (config-if)# switchport access vlan 1
ASA1 (config-if)# no shutdown
```

```
ASA1 (config-if)# interface e0/0
ASA1 (config-if)# switchport access vlan 2
ASA1 (config-if)# no shutdown
```

### 4.4. 检查端口的配置和分配。

```
ASA1#sh interface ip brief
```

| 接口 | IP 地址 | OK? | 方法 | 状态 | 协议 |
|---|---|---|---|---|---|
| Ethernet0/0 | unassigned | YES | unset | up | up |
| Ethernet0/1 | unassigned | YES | unset | up | up |
| Ethernet0/2 | unassigned | YES | unset | up | up |
| ... | | | | | |
| Vlan1 | 192.168.1.1 | YES | manual | up | up |
| Vlan2 | 212.212.1.1 | YES | manual | up | up |

```
ASA1#sh ip address
```

| 接口 | 名称 | IP 地址 | 子网掩码 | 方法 |
|---|---|---|---|---|
| Vlan1 | inside | 192.168.1.1 | 255.255.255.0 | manual |
| Vlan2 | outside | 212.212.1.1 | 255.255.255.252 | manual |

```
ASA1#sh switch vlan
```

| VLAN | 名称 | 状态 | 端口 |
|---|---|---|---|
| 1 | inside | up | Et0/1, Et0/2, Et0/3, Et0/4, Et0/5, Et0/6, Et0/7 |
| 2 | outside | up | Et0/0 |

4.5. 确保 ASA1 与 R1 之间以及 ASA1 与 PC1 之间的 ping 命令成功。

### 5. 为 ASA 配置默认静态路由。

### 5.1. 配置指向外部网络的默认路由。

```
ASA1(config)#route outside 0.0.0.0 0.0.0.0 212.212.1.2
```

### 5.2. 显示路由表。

```
ASA1#sh route
Codes: C - connected, S - static, I - IGRP, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2, E - EGP
       i - IS-IS, L1 - IS-IS level-1, L2 - IS-IS level-2, ia - IS-IS inter area
       * - candidate default, U - per-user static route, o - ODR
       P - periodic downloaded static route
Gateway of last resort is 212.212.1.2 to network 0.0.0.0
C    192.168.1.0 255.255.255.0 is directly connected, inside
    212.212.1.0/30 is subnetted, 1 subnets
C    212.212.1.0 255.255.255.252 is directly connected, outside
S*   0.0.0.0/0 [1/0] via 212.212.1.2
```

### 6. 修改应用于 ASA 的默认安全策略。

### 6.1. 创建 Class-Map 以识别授权流量。

```
ASA1(config)#class-map CMAP-IN-TO-OUT
```

### 6.2. 显示“match”命令的可用选项。

```
ASA1(config-cmap)#match?
```

### 6.3. 选择默认流量。

```
ASA1(config-cmap)#match default-inspection-traffic
ASA1(config-cmap)#exit
```

### 6.4. 创建 Policy-Map 以将访问规则应用到 Class-Map。

```
ASA1(config)#policy-map PMAP-IN-TO-OUT
ASA1(config-pmap)#class CMAP-IN-TO-OUT
ASA1(config-pmap-c)#inspect icmp
ASA1(config-pmap-c)#inspect http
ASA1(config-pmap-c)#exit
```





## 6.5. 在所有 ASA 接口上启用此安全策略。

```
ASA1(config)#service-policy PMAP-IN-TO-OUT global
```

## 7. 测试防火墙配置。

- 确保可以从 PC1 向 PC2 发送 ping 请求。
- 确保无法从 Server1 向 PC1 发送 ping 请求。
- 确保可以从 PC1 访问 Server1 的 http 服务。
- 确保无法从 PC1 访问 Server1 的 ftp 服务。

## 练习 15

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_219_0.png)

要查看此图的彩色版本，请参见 www.iste.co.uk/sadiqui/computer.zip

## 寻址表

| Device | Interface | IP address | Subnet mask | Gateway |
|---|---|---|---|---|
| ASA1 | E0/0 (VLAN2) | 212.212.1.1 | /30 | - |
| ASA1 | E0/1 (VLAN1) | 192.168.1.1 | /24 | - |
| ASA1 | E0/2 (DMZ) | 192.168.10.1 | /24 | - |
| R1 | F0/0 | 212.212.1.2 | /30 | - |
| R1 | F0/1 | 192.168.2.1 | /24 | - |
| PC1 | NIC | 自动 | | |
| PC2 | NIC | 192.168.2.2 | /24 | 192.168.2.1 |
| Server0 | NIC | 192.168.2.3 | /24 | 192.168.2.1 |
| Server_http | NIC | 192.168.10.2 | /24 | 192.168.10.1 |
| Server_ftp | NIC | 192.168.10.3 | /24 | 192.168.10.1 |

## 目标

- 使用 CLI 配置 ASA 5505 防火墙。

## 所需软件

- Packet Tracer。

## 部分 A：建立基本设备配置

### 1. 配置基本设备设置。

### 1.1. 按拓扑图配置主机名。

### 1.2. 根据寻址表将 IP 地址应用于设备接口。

### 2. 创建指向公司内部网络的静态路由。

```
R1(config)#ip route 192.168.1.0 255.255.255.0 212.212.1.1
R1(config)#ip route 192.168.10.0 255.255.255.0 212.212.1.1
```

## 部分 B：使用 CLI 配置 ASA 5505 防火墙

### 1. 配置 ASA 设备的基本设置。

### 1.1. 配置主机名。

```
ciscoasa(config)#hostname ASA1
ASA1(config)#
```

### 1.2. 设置系统日期。

```
ASA1(config)#clock set 14:25:00 May 12 2018
```

### 1.3. 配置特权模式密码。

```
ASA1(config)#enable password 1234
```

### 1.4. 配置 Telnet 连接密码。

```
ASA1(config)#passwd Cisco123
```

### 2. 从内部网络配置对 ASA 的 Telnet 和 SSH 访问。

### 2.1. 从内部网络配置 Telnet 访问。

```
ASA1(config)#telnet 192.168.1.0 255.255.255.0 inside
```

```
ASA1(config)#telnet timeout 10
```

### 2.2. 配置对 ASA 的远程 SSH 访问。

```
ASA1(config)#crypto key generate rsa modulus 1024
```

警告：已定义名为 <Default-RSA-Key> 的 RSA 密钥对。
您确实要替换它们吗？[yes/no]: y
密钥对生成过程已开始，请稍候。

```
ASA1(config)# ssh 192.168.1.0 255.255.255.0 inside
```

```
ASA1(config)# ssh timeout 10
```

### 3. 配置 ASA 设备的接口。

### 3.1. 为内部网络配置 VLAN 1 逻辑接口，并将安全级别设置为 100。

```
ASA1(config)# interface vlan 1
ASA1(config-if)# nameif inside
ASA1(config-if)# ip address 192.168.1.1 255.255.255.0
ASA1(config-if)# security-level 100
```

### 3.2. 为外部网络配置 VLAN 2 逻辑接口，并将安全级别设置为 0。

```
ASA1(config)# interface vlan 2
ASA1(config-if)# nameif outside
ASA1(config-if)# ip address 212.212.1.1 255.255.255.252
ASA1(config-if)# security-level 0
```

### 3.3. 为 DMZ 网络配置 VLAN 3 逻辑接口。

```
ASA1(config)# interface vlan 3
ASA1(config-if)# nameif DMZ
ERROR: This license does not allow configuring more than 2 interfaces with nameif and without a "no forward" command on this interface or on 1 interface(s) with nameif already configured.
```

### 3.4. 解释显示此错误消息的原因。

### 3.5. 阻止内部网络 (vlan1) 与 DMZ (vlan3) 之间的任何流量。

```
ASA1(config-if)#no forward interface vlan 1
ASA1(config-if)#nameif DMZ
ASA1(config-if)# ip address 192.168.10.1 255.255.255.0
ASA1(config-if)# security-level 50
```

### 3.6. 将 ASA 端口分配给连接的 VLAN。

```
ASA1(config)# interface e0/1
ASA1(config-if)# switchport access vlan 1
ASA1(config-if)# no shutdown
ASA1(config-if)# interface e0/0
ASA1(config-if)# switchport access vlan 2
ASA1(config-if)# no shutdown
ASA1(config-if)# interface e0/2
ASA1(config-if)# switchport access vlan 3
ASA1(config-if)# no shutdown
```

### 3.7. 使用 sh interface ip brief、sh ip address 和 sh switch vlan 命令检查配置和端口分配。

### 4. 在 ASA 上配置 DHCP 服务。

### 4.1. 为公司内部网络配置 DHCP 服务。

```
ASA1(config)#dhcpd address 192.168.1.5-192.168.1.100 inside
Warning, DHCP pool range is limited to 32 addresses, set address range as: 192.168.1.5-192.168.1.36
ASA1(config)# dhcpd dns 192.168.1.1
```

### 4.2. 在内部网络上启用 DHCP 服务。

```
ASA1(config)# dhcpd enable inside
```

### 4.3. 检查 PC1 是否已接收到有效的 IP 地址。

注意：在内部网络上，DHCP 服务默认在 ASA 服务中启用。

### 5. 为 ASA 配置默认静态路由。

```
ASA1(config)#route outside 0.0.0.0 0.0.0.0 212.212.1.2
```

### 6. 修改应用于 ASA 的默认安全策略。

### 6.1. 创建 Class-Map 以识别授权流量。

```
ASA1(config)#class-map CMAP-IN-TO-OUT
```

### 6.2. 显示 "match" 命令的可用选项。

```
ASA1(config-cmap)#match ?
```

### 6.3. 选择默认流量。

```
ASA1(config-cmap)#match default-inspection-traffic
```

```
ASA1(config-cmap)#exit
```

### 6.4. 创建 Policy-Map 以应用访问规则。

```
ASA1(config)#policy-map PMAP-IN-TO-OUT
ASA1(config-pmap)#class CMAP-IN-TO-OUT
ASA1(config-pmap-c)#inspect icmp
ASA1(config-pmap-c)#inspect ftp
ASA1(config-pmap-c)#inspect http
ASA1(config-pmap-c)#exit
```

### 6.5. 在所有 ASA 接口上启用此安全策略。

```
ASA1(config)#service-policy PMAP-IN-TO-OUT global
```

### 7. 在 ASA 上配置 NAT 服务。

### 7.1. 配置 PAT 服务以允许内部网络访问 Internet。

```
ASA1(config)# object network inside-internet
ASA1(config-network-object)# subnet 192.168.1.0 255.255.255.0
ASA1(config-network-object)# nat (inside,outside) dynamic interface
ASA1(config-network-object)# end
```

### 7.2. 配置静态 NAT 服务以允许从 Internet 访问 DMZ 区域中的服务器。

```
ASA1(config)# object network dmz-server-http
ASA1(config)# host 192.168.10.2
ASA1(config)# nat (dmz,outside) static 212.212.1.10
ASA1(config)# object network dmz-server-ftp
ASA1(config)# host 192.168.10.3
ASA1(config)# nat (dmz,outside) static 212.212.1.11
```

### 8. 配置 ACL 以定义授权访问。

### 8.1. 创建 ACL 以授权访问 DMZ 服务器。

```
ASA1(config)# access-list outside-dmz extended permit ip any host 192.168.10.2
ASA1(config)# access-list outside-dmz extended permit tcp any host 192.168.10.2 eq www
ASA1(config)# access-list outside-dmz extended permit ip any host 192.168.10.3
ASA1(config)# access-list outside-dmz extended permit tcp any host 192.168.10.3 eq ftp
```

### 8.2. 在外部接口上激活 ACL

```
ASA1(config)# access-group outside-dmz in interface outside
```

### 9. 测试防火墙配置。

### 9.1. 使用 show running-config 命令检查 ASA 防火墙配置。

### 9.2. 测试以下要素：

- 确保可以从 PC1 访问 Server0 的 http 服务；
- 确保可以使用 IP 地址 212.212.1.10 从 PC2 访问 Server_http 的 http 服务；
- 确保可以使用 IP 地址 212.212.1.11 从 PC2 访问 Server_ftp 的 FTP 服务。

### 9.3. 显示已执行的 NAT 转换。

```
ASA1#sh xlate
```

### 10.3. 使用图形工具配置 Cisco 元素

#### 10.3.1. CCP 概述

Cisco Configuration Professional (CCP) 是一款图形工具，可在不使用 Cisco IOS CLI 命令的情况下，便于配置、监控和故障排除 Cisco 路由器。

CCP 有两个版本：

- CCP：这是一个完整版本，用于通过安装在主机上的应用程序来组织和管理多个路由器；
- CCP Express：这是 CCP 的轻量版本，可在路由器的闪存中使用。它允许对设备进行基本配置。

#### 10.3.2. ASDM 概述

Cisco Adaptive Security Device Manager (ASDM) 是一款 Java 图形工具，允许配置、监控和故障排除 Cisco ASA 系统。

#### 10.3.3. 使用 CCP 和 ASDM

完成练习 16。





### 10.4. TMG 2010 防火墙

#### 10.4.1. 简介

Forefront Threat Management Gateway (TMG) 是一款微软产品，可保护公司免受主要来自 Web 的威胁。

此解决方案包括防火墙、VPN、URL 过滤和 IPS。

Forefront TMG 提供两个版本：Enterprise 和 Standard。所选版本取决于要保护的网络基础设施的规模。

NOTE.— 目前，Forefront TMG 2010 已不再商业提供，但仍接收来自 Microsoft 的更新和补丁。

#### 10.4.2. 安装和配置

完成练习 17。

### 练习 16。

### 拓扑

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_226_0.png)

### 寻址表

| 设备 | 接口 | IP 地址 / 子网掩码 | 操作系统 | 网关 |
|---|---|---|---|---|
| R1 | F0/0 | 192.168.10.1/24 | c2600-adventerprisek9-mz.124-1 | - |
| PC | NIC | 192.168.10.2/24 | Windows 7 或更高版本 | 192.168.10.1 |

### 目标

- 使用 Cisco Configuration Professional (CCP) 配置路由器。

### 使用的软件

- GNS3。

### 部分 A：建立基本设备配置

### 1. 在 PC1 上安装 Cisco Configuration Professional (CCP) 工具。

通常在运行 Windows 7 或更高版本 Windows 的 PC 上安装 CCP 没有问题。如果出现任何问题，请首先确保具备以下最低参数：

- Internet Explorer 6.0 或更高版本；
- Java Runtime Environment 版本 1.6.0 _11 或更高版本；
- Adobe Flash Player 版本 10 或更高版本。

NOTE.— 在某些情况下，还可能需要其他配置参数，特别是 Java 应用程序使用的内存，以确保应用程序正常运行。

### 2. 将 PC1 的 IP 地址设置为 192.168.10.2/24。

### 3. 配置 R1 的基本设置以支持 CCP 连接。

```
Router(config)# username admin privilege 15 secret 1234
R1(config)# hostname R1
R1(config)# ip http server
R1(config)# ip http authentication local
R1(config)# interface E0/0
R1(config-if)# ip address 192.168.10.1 255.255.255.0
R1(config-if)# no shutdown
```

### 部分 B：使用 Cisco Configuration Professional (CCP) 配置路由器

### 1. 在 PC1 上启动 CCP 工具并连接到 R1。

1.1. 作为管理员，在 PC1 上启动 CCP 工具，在相应字段中输入 R1 的 IP 地址以及登录名 admin 及其密码，然后单击 OK。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_228_0.png)

1.2. 单击“Discover”按钮连接到 R1，并单击“Router status”按钮显示路由器的特性。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_228_1.png)

1.3. 使用菜单“Utilities > View > Running Configuration”（请参阅箭头），显示 R1 的运行配置。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_229_0.png)

### 2. 使用 CCP 配置 R1。

NOTE.— 以下问题中指定的所有配置均可使用菜单“Configure > Router >...”中的选项实现。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_229_1.png)

### 2.1. 将路由器重命名为“R1”。

2.2. 配置以下警告（**横幅**）“严禁未经授权的人员访问”。

2.3. 将“Cisco12”设置为特权模式的加密密码。

2.4. 设置系统日期和时间。

2.5. 创建密码为“123456”且特权级别为 3 的用户“User1”。

2.6. 创建具有以下参数的 DHCP 范围：
- 范围名称：scope1；
- 网络地址：192.168.10.0/24；
- 范围：192.168.10.50-192.168.10.100；
- 租期：8 天；
- DNS 地址：192.168.50.10。

2.7. 创建指向 E0/1 接口的默认路由。

2.8. 配置具有以下参数的 OSPF 协议：
- 进程编号：10；
- network1 192.168.10.0/24 area 0；
- network2 192.168.20.0/24 area 0。

2.9. 创建具有以下参数的 ACL：
- ACL 名称：ACL1
- 目标 1：允许 172.16.0.0/16 网络访问 IP 地址为 192.168.10.13 的 HTTP 服务器；
- 目标 2：允许网络 192.168.0.0/24 访问 IP 地址为 192.168.10.14 的 FTP 服务器；
- 目标 3 允许工作站 192.168.10.56/24 访问 IP 地址为 192.168.10.10 的 Telnet 服务器。

将此 ACL 应用到 E0/1 接口。

### 3. 使用 CCP 监督 R1。

使用菜单“Monitor > Router > Overview”（请参阅箭头）显示 R1 的状态。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_231_0.png)

### 练习 17。

### 拓扑

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_231_1.png)

### 寻址表

| 设备 | 操作系统 | IP 地址 / 掩码 |
|---|---|---|
| ASA0 | ASAv 版本：asa921-smp-k8 | 192.168.10.20/24 |
| PC1 | Windows 7 或更高版本 | 192.168.10.10/24 |

### 目标

使用 Adaptive Security Device Manager (ASDM) 配置 ASA 防火墙。

### 使用的软件

VMware。

### 部分 A：在 PC1 和 ASA0 上配置基本设置以支持 ASDM 连接

### 1. 在 ASA0 上配置以下参数。

```
ciscoasa(config)#hostname ASA0
ASA0(config)#username admin password 1234
ASA0 (config)# ssl encryption aes128-sha1 aes256-sha1
ASA0(config)#interface g0/0
ASA0(config-if)#ip address 192.168.10.20 255.255.255.0
ASA0(config-if)# no shutdown
ASA0(config-if)#nameif inside
ASA0(config-if)# http server enable
ASA0(config-if)#http 192.168.10.0 255.255.255.0 inside
```

### 2. 将 PC1 IP 地址设置为 192.168.10.10/24，并确保 PC1 和 ASA0 之间执行“ping 请求”。

### 3. 使用 tftpd32 工具从 ASA0 下载库“asdm-x.x.x.bin”。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_232_0.png)

```
ASA0#copy tftp: flash:
Address or name of remote host [?] 192.168.10.10
Source filename []?asdm-752-153
Destination filename [asdm-752-153]?
Accessing tftp://192.168.10.10/
```

### 4. 在 PC1 上启动浏览器，并使用以下链接访问 ASA0：“https://192.168.10.20”。

### 5. 验证异常后，单击“Install ASDM Launcher”按钮，使用登录名“admin”及其密码下载“Cisco ASDM-IDM Launcher”工具。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_233_0.png)

### 6. 安装并启动“Cisco ASDM-IDM Launcher”工具。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_233_1.png)

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_234_0.png)

NOTE.— 在版本 7.2 中，Cisco ASDM-IDM Launcher 工具是一个“jar”文件，必须从其安装位置启动。

### 部分 B：使用 ASDM 配置 ASA 5505 防火墙

### 1. 使用菜单“wizards/startup wizard”在 ASA 设备上配置以下基本设置：

- 主机名：ASA1；
- 域名：Cisco.com；
- 特权模式密码：1234；
- 接口 g0/1：
  - IP 地址：212.212.1.10/24；
  - 区域名称：outside；
  - 安全级别：0；
  - 状态：active；
  - 从“outside”区域到 IP 地址 212.212.1.11/24 的默认静态路由；
  - 公司内部网络的 DHCP 服务：
    - IP 地址范围：192.168.10.50 – 192.168.10.100；
    - DNS 服务器：192.168.10.2；
    - 在 g0/1 上启用 PAT。

保存配置。

### 2. 设置系统日期。

### 3. 创建密码为“1234”且特权级别为 5 的用户“User3”。

### 4. 设置最小密码长度为 8 个字符。

### 5. 使用菜单“Configuration > Firewall > Service Policy Rules”创建 Class-Map 和 Policy-Map 以检查“inside”和“outside”区域之间的“icmp”流量。

### 6. 使用菜单“Configuration > Firewall > Access Rules”创建一个 ACL，授权来自“inside 区域”到 Internet 的所有 HTTP 和 FTP 流量。

### 7. 配置静态 NAT 服务，以允许从 Internet 访问以下内部服务器：
- Server-http：内部 IP 地址：192.168.10.2/24；外部 IP 地址：212.212.1.20/30；
- Server-ftp：内部 IP 地址：192.168.10.3/24；外部 IP 地址：212.212.1.21/30。

### 部分 C：测试防火墙（可选）

### 拓扑

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_235_0.png)





## 实现拓扑并测试 ASA 5505 防火墙的工作。

### 练习 18

### 拓扑

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_236_0.png)

### 使用的软件

- VMware Workstation.

### 寻址表

| 设备 | 接口 | IP 地址 / 掩码 |
| :--- | :--- | :--- |
| TMG 服务器 2010 | 内部网络 | 192.168.0.1/24 |
| | DMZ | 192.168.10.1/24 |
| | 外部网络 | 212.212.212.4/32 |

### 目标

- 安装并配置 Forefront TMG 2010 服务器的基本元素。

### 将使用的软件

- VMware。

注：根据本文档上述目标，本练习将仅限于 TMG2010 某些基本元素的安装和配置。读者可查阅有关该产品的其他专业文档以获取更多信息。

### 部分 A：安装 Forefront TMG 2010

Forefront TMG 2010 服务器只能安装在 Windows Server 2008 或 Windows Server 2008 R2 上。在安装服务器之前，请先安装更新。这两项任务通常都可以轻松完成。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_237_0.png)

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_238_0.png)

### 部分 B：Forefront TMG 2010 的初始配置

- 1. 根据寻址表配置 Forefront TMG 2010 服务器接口。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_238_1.png)

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_239_0.png)

- 2. 通过填写主机名、域或工作组以及 DNS 后缀来配置系统参数。保留所有这些参数的默认值，因为在本练习中不会用到它们。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_239_1.png)

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_240_0.png)

- 3. 退出向导并启动 TMG2010 管理控制台。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_240_1.png)

### 部分 C：配置 Forefront TMG 2010 的某些基本元素

- 1. 创建名为“Rule1”的访问规则，该规则将授权内部网络与 Internet 之间的所有 https 和 FTP 流量。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_241_0.png)

- 2. 创建名为“Rule2”的访问规则，该规则将授权内部网络与 DMZ 之间的所有 https 和 ssh 流量。

- 3. 创建名为“Rule3”的访问规则，该规则允许 IPsec ESP 客户端访问 DMZ。

- 4. 开始配置 Web 访问策略。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_241_1.png)

- 4.1. 创建一个阻止访问娱乐、游戏和新闻网站的 Web 访问策略。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_241_2.png)

### Web 访问策略向导

### Web 访问策略规则

此向导创建一条默认规则，允许所有内部用户访问 Internet。您也可以创建一条默认阻止规则。

您希望向导创建一条阻止访问潜在恶意 URL 类别的默认规则吗？

- 是，创建一条阻止最小推荐 URL 类别的规则
- 否，请勿为我创建该规则

您可以在向导的下一页编辑默认阻止规则或创建自己的阻止规则。

关于 URL 类别的帮助

### Web 访问策略向导

### 阻止的 Web 目标

将创建一条名为“阻止的 Web 目标”的规则。您可以在本向导的下一页定义该规则的例外。

阻止访问这些 Web 目标：

- 游戏
- 新闻
- 娱乐

要对使用 URL 类别或类别集的规则应用 URL 筛选，Forefront TMG 会查询远程托管的 Microsoft 信誉服务。完整的 URL 字符串将通过安全连接发送到该服务。

阅读我们的隐私声明

### 添加目标

- 幽默/漫画
- 非法药物
- 互联网服务
- 法律服务与参考
- 恶意
- 成人内容
- 媒体共享
- 机动车辆
- 新闻
- 非营利/倡导/非政府组织
- 裸露
- 猥亵/低俗
- 在线社区
- 在线交易/经纪
- P2P/文件共享
- 泊域名
- 个人网络存储

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_243_0.png)

- 4.2. 创建名为“Rule-Web1”的访问规则，该规则授权经过身份验证的用户仅能访问专业网站。

## 练习 19

### 拓扑

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_243_1.png)

### 使用的软件

- VMware Workstation.
- GNS3.

### 寻址表

| 设备 | 操作系统 | IP 地址 / 掩码 |
|---|---|---|
| Kali-Linux | Kali Linux 2018.2 版 | 192.168.21.163/24 |
| PC1 | Windows XP SP3 | 192.168.21.164/24 |

### 目标

- 了解不同类型攻击的工作原理；
- 了解为保护计算机网络而需实施的对策；
- 使用 Kali-Linux 系统测试网络漏洞以保护网络。

### 将使用的软件

- VMware。

### Kali-Linux 系统概述

Kali-Linux 是一个基于 Debian 的 Linux 发行版，允许您执行安全审计。该系统包含多种工具，可促进各种信息安全任务，例如入侵测试和漏洞查找等。Kali-Linux 当前被归类为任何希望学习或专攻计算机安全领域的人员的必备工具。

### 在 PC 上配置基本设置

- 1. 根据地址表配置两台 PC 接口上的 IP 地址。
- 2. 测试两台 PC 之间的连通性。

### 部分 A：利用操作系统中的漏洞

### 攻击概述

此攻击涉及利用 Windows Samba 服务中名为“MS08-067”的漏洞。这会影响所有 Windows XP 操作系统：Windows XP SP1、SP2 和 SP3。由于已被归类为过时系统，Windows XP 不再接收来自 Microsoft 的更新或补丁。

### 用于测试攻击的工具

- Metasploit 是集成到 Kali-Linux 中的一个项目，旨在提供计算机系统中漏洞的信息，并协助进行渗透测试。
- Armitage 是一个图形界面，可方便地使用 Metasploit。

### 1. 在操作系统中激活漏洞。

在 PC1 上启动控制面板，在防火墙设置中选择“文件和打印机共享”。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_245_0.png)

注：如果受害者工作站上的防火墙已完全禁用，攻击同样可行。

### 2. 利用漏洞。

- 2.1. 通过单击图标在 Kali-Linux 上启动“armitage”工具：

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_245_1.png)

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_246_0.png)

### 2.2. 发起侦察攻击。

在“主机/Nmap 扫描/Ping 扫描”菜单中，对网络 192.168.21.0/24 发起“ping 扫描”。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_246_1.png)

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_246_2.png)

### 2.3. 发起攻击。

从攻击列表中，选择以下路径：“exploit/windows/smb/ms08_067_netapi”并双击。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_247_0.png)

单击“启动”按钮，确保攻击成功执行。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_247_1.png)

### 2.4. 利用受害者计算机。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_247_2.png)

### 对策

始终更新操作系统并迁移到最新系统。

### 部分 B：利用应用程序漏洞

### 攻击概述

此攻击涉及利用“Windows Shell”软件中名为“ms10_046_shortcut_icon_dllloader”的漏洞。它在多个 Windows 操作系统上运行（请参阅 Microsoft 安全公告 MS10-046 - Critical）。

### 用于测试攻击的工具

- Metasploit。
- Armitage。

### 1. 利用漏洞。

### 1.1. 释放工作站 PC1。

在“armitage”工具中，单击 PC1 地址，然后选择子菜单“Kill”以将其从先前的攻击中释放出来。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_248_0.png)

### 1.2. 发起攻击。

从攻击列表中，选择以下路径：“exploit/windows/browser/ms10_046_shortcut_icon_dllloader”并双击。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_248_1.png)





单击“Launch”按钮。

### 1.3. 激活漏洞。

启动 Internet Explorer 并输入链接 http://192.168.21.163。确保攻击成功执行。

注.— 在实际操作中，攻击者使用与域名关联的公共 IP 地址。该链接通过电子邮件发送给受害者。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_249_0.png)

### 1.4. 利用受害者的机器。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_249_1.png)

### 对策

为应用程序和操作系统应用所有补丁。

## 部分 C：利用“特洛伊木马”的执行

### 攻击概述

特洛伊木马（或简称特洛伊）是包含两种功能的恶意代码：第一种执行有用任务，第二种可能导致数据间谍活动甚至数据删除。

### 用于测试攻击的工具

- Metasploit。
- Armitage。

### 1. 准备攻击。

### 1.1. 释放工作站 PC1。

### 1.2. 创建特洛伊木马。

从攻击列表中，选择以下路径：“windows/meterpreter/reverse_tcp”并双击。然后，从下拉选项“Output”中，选择“.exe”选项，并单击“Launch”按钮。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_250_0.png)

记下 LPORT 参数的值（9,257）。该值可以是您在 1024 到 65,536 之间选择的任何值。

将生成的文件保存为桌面上的“Trojan”。

### 1.3. 激活漏洞。

将文件“Trojan.exe”复制到 PC1 并运行它。

注.— 在实际操作中，已创建的文件要么集成到看起来合法的另一个程序中（游戏、屏幕保护程序等），要么与办公文件（pdf、Word 等）甚至图像相关联，并在用户执行时触发。

### 2. 发起攻击。

从攻击目录中，选择以下路径：“exploit/multi/handler”并双击。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_251_0.png)

将 LPORT 参数设置为接收端口上已配置的值，并单击“Launch”按钮。

### 3. 利用受害者的机器。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_251_1.png)

### 对策

- 安装并更新防病毒软件。
- 不要运行来自不可靠来源的程序。

## 部分 D：利用未加密连接的漏洞

### 攻击概述

“中间人”攻击的原理是将自己置于两个网络元素之间，以利用交换的未加密数据。其中，攻击者可以从客户端和服务器之间的未加密连接中窃取登录名和密码详细信息。

### 用于测试攻击的工具

**Setoolkit** 是一套专门针对个人使用（PC、平板电脑、手机等）的网络元素攻击而定制的工具集。这些工具允许创建“中间人”攻击等。

注.— 对于本部分，您需要修改网络设置以连接到 Internet。

### 1. 配置计算机的基本设置。

### 1.1. 释放工作站 PC1。

### 1.2. 修改两台计算机上的 VMware 网络设置。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_252_0.png)

确保两台工作站都有 Internet 连接。

### 2. 发起攻击。

### 2.1. 启动终端并输入“setoolkit”命令。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_252_1.png)

### 2.2. 连续输入以下选项：1；2；3。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_253_0.png)

### 2.3. 输入以下选择：2 并输入以下参数：

- 保留默认 IP 地址；
- 输入链接：https://www.facebook.com/。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_253_1.png)

### 3. 激活漏洞。

- 在客户端工作站上启动浏览器并输入以下链接：http://192.168.1.25（Kali-Linux 工作站的 IP 地址）。确保您的浏览器显示您的连接不安全。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_253_2.png)

注.— 在实际操作中，攻击者使用与域名关联的公共 IP 地址，该域名与目标站点名称非常接近，例如：facebook.com、facebooke.com。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_254_0.png)

- 在指定字段中输入登录名：test@yahoo.fr 和密码：1234，然后验证。请注意，您将被重定向到网站 www.facebook.com。
- 在 Kali-Linux 工作站上，输入 Ctrl+C 以停止攻击。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_254_1.png)

- 打开工具生成的报告并检查登录名和密码是否已被捕获并保存（打开保存路径为 /root/.set/report/ 的“.html”文件）。

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_254_2.png)

### 对策

确保连接到敏感网站由 https 协议保护。

## 部分 E：利用简单密码的漏洞

### 攻击概述

密码攻击的目的是发现用户名和密码以访问各种资源。这种攻击常用的两种方法是字典攻击和暴力破解攻击。

### 用于测试攻击的工具

- Crunch：这是一个可以生成给定字符集所有可能组合的工具。它用于暴力破解密码攻击。
- Hydra：这是一个可以执行密码攻击并支持多种网络协议的工具。它速度非常快且灵活，新模块可以轻松添加。

注.— 对于本节，您需要使用 GNS3 来完成练习。

### 1. 配置计算机和 R1 的基本设置。

### 拓扑

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_255_0.png)

有关此图的彩色版本，请参见 www.iste.co.uk/sadqui/computer.zip。

### 1.1. 根据拓扑配置两台计算机接口的 IP 地址。

### 1.2. 测试两个元素之间的连通性。

### 1.3. 在 R1 上输入以下命令：

```
R1(config)#username admin password 1234
R1(config)#line vty 0
R1(config-line)#login local
```

### 2. 准备攻击。

### 2.1. 生成密码列表。

在 Kali-Linux 上启动终端并输入以下命令：

```
root@kali:~#crunch 4 4 1234 -o /root/PassList.txt
```

注.— 为简单起见，我们将限制创建 4 个字符的密码，由数字 1、2、3 和 4 的组合组成。

### 2.2. 生成用户列表。

```
root@kali:~#echo admin >> /root/listeUser.txt
root@kali:~#echo cisco >> /root/listeUser.txt
root@kali:~#echo administrateur >> /root/User.List.txt
```

### 3. 发起攻击。

使用仅“admin”账户结合先前生成的所有可能密码来发起攻击。

```
root@kali:~#hydra -l -t 4 -l admin -P /root/PassList.txt 192.168.34.10 telnet
```

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_256_0.png)

### 注.—

- 要使用“UserList”文件，只需输入命令：

```
root@kali:~#hydra -l -t 4 -L /root/UserList.txt -P /root/pass0.txt 192.168.34.10 telnet
```

- “Xhydra”工具是 hydra 实用程序的图形界面。它简化了此类攻击的执行。但是，它提供的选项比命令行少。

### 对策

- 确保密码难以猜测，包含高复杂性，并且最小长度为 8 个字符。
- 安装 IPS 以检测此类攻击。

## 参考文献

- Anandh, V., Vinod, M., Singh, G.D. (2018). *CCNA Security 210-260 认证指南*. Packt Publishing, Birmingham.
- Cisco (2018). *思科网络学院* [在线]. 可在: https://www.netacad.com/fr 查阅.
- Frahim, J., Santos, O., Ossipov, A. (2012). *Cisco ASA：一体化下一代防火墙、IPS 和 VPN 服务*，第 3 版. Cisco Press, Indianapolis.
- Keith, B., Scott, M. (2012). *CCNA Security 640-554 官方认证指南*. Cisco Press, Indianapolis.
- Santos, O., Stuppi, J. (2015). *CCNA Security 210-260 官方认证指南*. Cisco Press, Indianapolis.
- Vachon, B. (2012). *CCNA Security 便携式命令指南*. Cisco Press, Indianapolis.




## 索引

### A

- AAA, 21, 36, 67–73, 75–78, 189, 197
- ACL, 10, 17, 18, 79, 81–84, 89–95, 109, 114, 118, 179, 180, 183, 186, 187, 189, 195, 197, 209, 215
- 广告软件, 4, 10
- AH, 174, 175
- AIP-SSM, 103
- ARP 欺骗, 127
- ASA, 176, 189–210, 217, 219, 221
- ASDM, 189, 210, 217–219
- 原子，另见 复合, 105

### B, C

- 分组密码, 146
- BPDU 保护, 125, 131
- 卡商, 3, 9
- CCP, 189, 210, 212, 214, 215
- 思科 SensorBase, 106
- 类映射, 86, 87, 98, 99, 114, 115, 118, 119, 203, 208
- 复合，另见 原子, 105
- 密码分析, 144

### D

- DAI, 125, 127, 131
- DDoS, 7, 13
- DH, 148, 149, 162, 180
- DHCP 嗅探, 127, 135
- 数字, 140, 150
- DMZ, 7, 84, 97–99, 113–115, 118, 119, 204, 206, 207, 209, 221, 226
- DoS, 7, 12, 14, 24, 108, 178
- 双标记, 129, 131
- 丢弃, 85, 87, 99
- DTP, 128, 131, 136

### E, F

- ESP, 174, 175, 180, 185, 226
- 防火墙, 5, 8–10, 79, 80, 81, 84, 96, 97, 100, 106, 113, 115–119, 176, 189, 190, 193, 198, 199, 204, 205, 209, 211, 217, 219–221, 230
  - 应用层, 80
  - NAT, 另见, 79, 80
  - 分组过滤, 80
  - 有状态, 80
- 帧 802.1Q, 129

### G, H

- 全局关联, 106, 111
- 根保护, 125, 130, 131, 137
- 黑客, 2, 3, 7
- 劫持, 6, 13
- HMAC, 143, 151, 174, 180, 185
  - MD5, 151
  - SHA, 151

### I

- IDS, 102, 103, 106, 123
- IKE, 173, 174, 176–180, 183–185
- IKEv1, 176–178
- IKEv2, 178
- 检查, 85–87, 98, 99, 114, 115, 203, 208
- IPS, 5, 8, 10, 12, 111, 117, 119–124, 189, 192, 211, 242
- 内联, 104, 108, 110, 123
- 混杂, 103
- IPSec, 180, 181, 185–187
- ISAKMP, 149, 176, 180, 181, 183–188

### K, L, M

- Kali Linux, 229, 241
- 许可证
  - 基础, 193
  - 安全加强版, 193
- 中间人攻击, 6, 13, 14, 24, 127, 164, 236
- 消息摘要, 54, 151
- 模式
  - 激进, 177
  - 主模式, 177
  - 路由, 190
  - 透明, 191

### N, O

- NAT, 另见 防火墙 NAT, 80, 189, 191, 193, 195, 196, 209, 210, 220
- NTP, 16, 41–43, 50, 51, 54–56, 58, 60, 61
- 层, 42, 43, 55
- Oakley, 176

### P, R

- 通过, 85, 87, 98, 99, 109, 115
- pharming, 6, 13
- 网络钓鱼, 6, 13
- 电话骇客, 3, 9
- PKCS, 156, 157
- PKI, 155–158
- 策略映射, 86, 87, 98, 99, 115, 118, 119, 203, 208, 220
- 端口安全, 125, 126, 131, 134, 135
- PSK, 174, 179, 180, 184
- radius, 另见 Tacacs+, 69–71, 77, 197
- 勒索软件, 4

### S

- SA, 47, 58, 73, 148, 151, 152, 154, 175–178, 181, 187, 188
- 吓唬软件, 4
- 脚本小子, 3
- 传感器, 106
- 服务策略, 86, 99, 208
- 签名, 104, 106, 107, 109–111, 119–123, 148, 153–157, 174
- 签名微引擎, 106, 107
- SK EME, 176
- SNMP, 16, 41, 46–50, 58, 63–66, 108, 109
  - GET, 49, 65, 66
  - GetBulk, 49
  - GetNext, 49
  - Informiter, 49, 229
  - MIB, 47–49, 65, 66, 191, 192
  - SET, 33, 49, 60, 65, 122, 180, 181, 185, 186, 200, 205, 207, 239
  - SNMP 代理, 47, 49, 63–65
  - SNMP 管理器, 47, 49, 63–65
  - Trap, 46, 49, 56, 62–66, 109
- SPD, 175
- 欺骗, 6, 8, 12
- 间谍软件, 3, 10
- SSC 插槽, 191, 192
- STP, 125, 130, 131, 136, 137
- 流密码, 147
- Syslog, 41, 44–46, 50, 51, 54–56, 58, 61–63, 108, 117, 120, 122, 123

### T, V

- Tacacs+, 另见 radius, 69, 71, 197
- 文本
  - 明文, 27, 48, 144, 159, 166, 174
  - 密文, 144
- TMG, 189, 211, 221–223, 225
- 木马病毒, 4, 10, 234, 235
- 中继, 128–131, 136
- 病毒, 3, 6, 8, 9, 11, 13, 236

### W, X, Z

- 蠕虫, 3
- X.509, 156
- ZFW, 79, 84–86

## 计算机工程领域 iSTE 其他书名

### 2019

贝西布·瓦利德，杜伊布·迪亚拉，瓦桑·尼亚兹，马雷克奇·艾玛
解决运输问题：迈向绿色物流

莫里斯·克莱克
迭代优化器：难度度量与基准

里亚德·格拉拉
SQL Server 2014/2016 中的分析型 SQL

维姆·图恩西
网络警觉与数字信任：云计算和 IoT 时代的网络安全

### 2018

马西奥·安德罗
数字图书馆与众包
（数字工具与应用丛书 – 第 5 卷）

布鲁诺·阿尔诺迪，帕斯卡尔·吉通，纪尧姆·莫罗
虚拟现实与增强现实：神话与现实

蒂埃里·贝尔捷，布鲁诺·特布尔
从数字痕迹到算法投影

阿兰·卡尔东
超越人工智能：从人类意识到人工意识

S. 马赫迪·霍马尤尼，达利拉·B.M.M.·丰特斯
海运作业的元启发式
（优化启发式丛书 – 第 1 卷）

罗伯特·让苏兰
JavaScript 与开放数据

奥利维尔·皮韦
NoSQL 数据模型：趋势与挑战
（数据库与大数据丛书 – 第 1 卷）

索拉亚·塞德考维
数据分析与大数据

伊马德·萨利赫，梅迪·阿米，塞缪尔·齐奥尼茨基
物联网的挑战：技术、应用与伦理
（数字工具与应用丛书 – 第 7 卷）

塞缪尔·齐奥尼茨基
生态系统知识：信息与通信的建模与分析方法
（数字工具与应用丛书 – 第 6 卷）

### 2017

巴德尔·本马玛
Java 中的并发、实时与分布式编程

弗雷德里克·埃利奥多尔，阿米尔·纳基布，布萨德·伊斯迈尔，萨尔马·乌什拉，洛朗·施米特
智能电网的元启发式
（元启发式丛书 – 第 10 卷）

马海平，丹·西蒙
*基于生物地理学的优化的进化计算*
*(元启发式丛书 – 第 8 卷)*

阿兰·佩特罗夫斯基，萨纳·本·哈米达
*进化算法*
*(元启发式丛书 – 第 9 卷)*

G.A. 维贾亚拉克什米·帕伊
*投资组合优化的元启发式*
*(元启发式丛书 – 第 11 卷)*

### 2016

克里斯蒂安·布鲁姆，帕奥拉·费斯塔
*生物信息学中字符串问题的元启发式*
*(元启发式丛书 – 第 6 卷)*

劳伦特·德鲁西
*物流的元启发式*
*(元启发式丛书 – 第 4 卷)*

克拉里斯·德南斯和莱蒂西亚·朱尔当
*大数据的元启发式*
*(元启发式丛书 – 第 5 卷)*

内西玛·拉巴迪，克里斯蒂安·普兰斯，卡罗莱娜·普罗东
*车辆路由问题的元启发式*
*(元启发式丛书 – 第 3 卷)*

劳尔·勒罗伊
*立体视觉中的视觉疲劳减轻*

埃维琳·吕顿，娜塔莉·佩罗，阿尔贝·通达
*食品科学与技术的进化算法*
*(元启发式丛书 – 第 7 卷)*

弗雷德里克·马古勒，赵海翔
*建筑能耗分析中的数据挖掘与机器学习*

米歇尔·里戈
高级图论与组合数学

### 2015

弗朗克·巴比耶，让-吕克·勒库辛
COBOL 软件现代化：基于 BLU AGE® 方法的从原则到实现

肯·陈
基于仿真与分析的性能评估及其在计算机网络中的应用

莫里斯·克莱克
优化中的引导随机性
（元启发式丛书 – 第 1 卷）

尼古拉·迪吕尔，戴维·吉亚扎，让-巴蒂斯特·戈特兰，让-马克·阿里奥
空中交通管理的元启发式
（元启发式丛书 – 第 2 卷）

弗雷德里克·马古勒，弗朗索瓦-泽维埃·鲁，吉约姆·乌佐
并行科学计算

帕萨恩·穆尼萨旺，素恰特·亚门
硬盘驱动器行业的目视检测技术

### 2014

让-路易·布朗热
工业复杂系统的形式化方法应用

让-路易·布朗热
复杂系统的形式化方法应用：
B 方法的实现

弗雷德里克·加尔迪，蒂埃里·布努阿，朱利安·达莱，贝特朗·埃斯泰隆，罗曼·梅热
基于局部搜索的数学规划求解器

索森·克里申，朱海娜·沙瓦希
图相关优化与决策支持系统

尼古拉·拉里约，安托万·瓦雷
航空电子系统软件快速原型设计：面向复杂系统认证的模型导向方法

穆拉德·夏巴内·乌萨拉
软件架构 1
软件架构 2

范杰利斯·萨科斯
组合优化 – 3卷系列，第 2 版
组合优化概念 – 第 1 卷，第 2 版
问题与新方法 – 第 2 卷，第 2 版
组合优化的应用 – 第 3 卷，第 2 版

弗拉维安·凯内尔
大规模虚拟化基础设施的调度：走向合作式管理

米歇尔·里戈
形式语言、自动机与计数系统 1：单词组合论入门
形式语言、自动机与计数系统 2：可识别性与可判定性的应用

帕特里克·圣迪济耶
音乐修辞：基础与标注方案

西德·图阿蒂，布努瓦·德迪内尚
高级后端优化

### 2013

埃蒂安·安德烈，罗曼·苏拉
反演方法：实时嵌入式系统的参数化验证




BOULANGER Jean-Louis
基于软件的设备安全管理

DELAHAYE Daniel, PUECHMOREL Stéphane
航空交通建模与优化

FRANCOPOULO Gil
LMF — 词汇标记框架

GHÉDIRA Khaled
约束满足问题

ROCHANGE Christine, UHRIG Sascha, SAINRAT Pascal
时序可预测架构

WAHBI Mohamed
分布式约束满足问题的算法与排序启发式

ZELM Martin et al.
企业互操作性

## 2012

ARBOLEDA Hugo, ROYER Jean-Claude
模型驱动与软件产品线工程

BLANCHET Gérard, DUPOUY Bertrand
计算机体系结构

BOULANGER Jean-Louis
形式方法的工业应用：形式验证

BOULANGER Jean-Louis
形式方法：从模型到代码的工业应用

CALVARY Gaëlle, DELOT Thierry, SÈDES Florence, TIGLI Jean-Yves
计算机科学与环境智能

MAHOUT Vincent
汇编语言程序设计：ARM Cortex-M3 2.0：组织、创新与领域

MARLET Renaud
程序特化

SOTO Maria, SEVAUX Marc, ROSSI André, LAURENT Johann
嵌入式系统中的内存分配问题：优化方法

## 2011

BICHOT Charles-Edmond, SIARRY Patrick
图分区

BOULANGER Jean-Louis
软件静态分析：抽象解释

CAFERRA Ricardo
计算机科学与人工智能逻辑

HOMES Bernard
软件测试基础

KORDON Fabrice, HADDAD Serge, PAUTET Laurent, PETRUCCI Laure
分布式系统：设计与算法

KORDON Fabrice, HADDAD Serge, PAUTET Laurent, PETRUCCI Laure
分布式系统的模型与分析

LORCA Xavier
基于树的图分区约束

TRUCHET Charlotte, ASSAYAG Gerard
音乐中的约束编程

VICAT-BLANC PRIMET Pascale et al.
计算网络：从集群到云计算

## 2010

AUDIBERT Pierre
面向信息学与计算机科学的数学

BABAU Jean-Philippe et al.
面向分布式实时嵌入式系统的模型驱动工程

BOULANGER Jean-Louis
计算机体系结构安全

MONMARCHÉ Nicolas et al.
人工蚁群

PANETTO Hervé, BOUDJLIDA Nacer
企业软件与应用互操作性 2010

SIGAUD Olivier et al.
人工智能中的马尔可夫决策过程

SOLNON Christine
蚁群优化与约束编程

AUBRUN Christophe, SIMON Daniel, SONG Ye-Qiong et al.
可靠网络化控制系统的协同设计方法

## 2009

FOURNIER Jean-Claude
图论及其应用

GUÉDON Jeanpierre
莫叶变换 / 理论与应用

JARD Claude, ROUX Olivier
通信嵌入式系统 / 软件与设计

LECOUTRE Christophe
约束网络 / 面向技术与算法的简化目标

## 2008

BANATRÉ Michel, MARRÓN Pedro José, OLLERO Hannibal, WOLITZ Adam
协作嵌入式系统与无线传感器网络

MERZ Stephan, NAVET Nicolas
实时系统建模与验证

PASCHOS Vangelis Th
组合优化与理论计算机科学：界面与视角

WALDNER Jean-Baptiste
纳米计算机与群体智能

## 2007

BENHAMOU Frédéric, JUSSIEN Narendra, O’SULLIVAN Barry
约束编程趋势

JUSSIEN Narendra
数独全书

## 2006

BABAU Jean-Philippe et al.
从 MDD 概念到实验与示例 – DRES 2006

HABRIAS Henri, FRAPPIER Marc
软件规格说明方法

MURAT Cecile, PASCHOS Vangelis Th
图上的概率组合优化

PANETTO Hervé, BOUDJLIDA Nacer
企业软件与应用互操作性 2006 / IFAC-IFIP I-ESA ’2006

## 2005

GÉRARD Sébastien et al.
面向分布式实时嵌入式系统的模型驱动工程

PANETTO Hervé
企业软件与应用互操作性 2005

## WILEY END USER LICENSE AGREEMENT

WILEY 最终用户许可协议

Go to www.wiley.com/go/eula to access Wiley's ebook EULA.

访问 www.wiley.com/go/eula 获取 Wiley 的电子书 EULA。

Developed in collaboration with a training and certification team from Cisco, *Computer Network Security* is an exploration of the state-of-the-art and good practices in setting up a secure computer system. Concrete examples are offered in each chapter, to help the reader to master the concept and apply the security configuration.

与思科培训与认证团队合作开发，*计算机网络安全*探讨了构建安全计算机系统的最新技术与良好实践。每章均提供具体示例，帮助读者掌握概念并应用安全配置。

This book is intended for students preparing for the CCNA Security Exam (210-260 IINS) – whether at professional training centers, technical faculties, or training centers associated with the “Cisco Academy” program. It is also relevant to anyone interested in computer security, be they professionals in this field or users who want to identify the threats and vulnerabilities of a network to ensure better security.

本书面向准备参加 CCNA Security 考试（210-260 IINS）的学生——无论是在专业培训中心、技术学院，还是与“思科学院”项目相关的培训中心。它也适合任何对计算机安全感兴趣的人，无论是该领域的专业人士，还是希望识别网络威胁与漏洞以确保更好安全性的用户。

**Ali Sadiqui** is a trainer-researcher at the Office de la Formation Professionnelle et de la Promotion du Travail (OFPPPT), Morocco. He is a member of several research laboratories and obtained his doctorate from the Sidi Mohamed Ben Abdellah University, Morocco.

**阿里·萨迪基** 是摩洛哥职业培训与劳动推广办公室 (OFPPPT) 的培训师兼研究员。他是多个研究实验室的成员，并获得西迪·穆罕默德·本·阿卜杜拉大学（摩洛哥）的博士学位。
