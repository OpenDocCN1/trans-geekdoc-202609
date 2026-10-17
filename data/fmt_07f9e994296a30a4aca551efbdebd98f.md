
- 27. Z. A. El Houda, L. Khouhi, and A. S. Hafid, “Bringing intelligence to software defined networks: Mitigating DDoS attacks,” IEEE Transactions on Network and Service Management, p. 1–10, 2020.

- 28. Z Abou El Houda, S. Zerkane, D. Espes, and C.-T. Pan, "Method for processing a packet and associated device, switching equipment and computer program," Patent WO 020 020 91A1, January, 2020. [Online]. Available: https://rl.archives.org/fr-hl3702399

- 29. Z. A. Houda, B. Brik, and S.-M. Senouci,"A IoT-based explainable learning framework for intrusion detection systems," Internet of Things Magazine, vol. 5, no. 2, p. 20–23, 2022.

- 30. Z. A. Houda and L. Khoukhi, "A hierarchical fog computing framework for network attack detection in SDN," in ICC 2022-IEEE International Conference on Communications, 2022, Seoul, South Korea, p. 4366–4371.

- 31. Z. A. El Houda, B. Brik, A. Ksteni, and L. Khouhi,”A mec-based architecture to secure IoT using federated learning,” Internet of Things Magazine, vol. 6, no. 1, p. 60–63, 2023.

- 32. Z. A. El Houda, B. Brik, and L. Khouki,”Ensemble learning for intrusion detection in SDN-based smart grids,” 2022 IEEE 47th Conference on Local Computer Networks (LCN), 2022, Edmonton, Canada, p. 149–156.

- 33. D. Adessa, C.-C. Hisek, Y. Sagduy, and L. Qian,"Adversarial machine learning in wireless communications using RF data: a review," IEEE Communications Tutorials, vol. 25, no. 1, p. 77–100, 2023.

- 34. M Ul Hassan, H. M. Rehani, and J. Chen,"Anomaly detection in blockchain networks: A comprehensive survey," IEEE Communications Tutorials, vol. 25, no. 1, p. 289–319, 2023.

- 35. "IEEE standard for security systems for network power generating standards," IEEE Std 692–2010 (Revision of IEEE Std 692–2010), p. 1–5, 2013. [Online]. Available: https://standards.ieee.org/ieee/692/5755

- 36. "IEEE guide for animal mitigation of electric power substations," IEEE Std 1264–2022 (Revision of IEEE Std 1264–2015), p. 1–48, 2022. [Online]. Available: https://standards.ieee.org/ieee/1264/10562

# 网络威胁攻击者的视角

101

+ 37. H. Jo and K. Kim, “Security service-aware reinforcement learning for efficient network service provisioning,” in 2022 23rd Asia-Pacific Network Operations and Management Symposium (APNOMS), 2022, IEEE, Takamatsu, Japan, pp. 1–4.

+ 38. P. Tague, D. Slater, J. Rogers, and R. Poovendra, “Evaluating the vulnerability of network traffic using joint security and routing analysis,” IEEE Transactions on Dependable and Secure Computing, vol. 6, no. 2, pp. 111–123, 2009.

+ 39. M. Sheng, H. Liu, X. Yang, W. Wang, J. Huang, and B. Wang, “Network security situation prediction in software defined networking data plane,” in 2020 IEEE International Conference on Electrical Engineering and Computer Applications (AECA), 2020, IEEE, Dalian, LianNing, China, pp. 475–479.

+ 40. Fang Lan, W. Chunlei, Miao Qing, and Liu Li, “Dynamically validate network security based on adaptive control theory,” in 2013 International Conference on Information and Network Security (ICINS 2013), 2013, IEEE, Bangkok, Thailand, pp. 1–6.

+ 41. “IEEE standard for local and metropolitan area networks—media access control (mac) security corrigendum 1: Tag control information figure,” IEEE Std 802.1AE2018/Cor-2020 (Corrigendum to IEEE Std 802.1AE-2018), pp. 1–14, 2020. [Online]. Available: https://standards.ieee.org/ieee/802.1AE-2018/Cor_1/7588/

## 6 物联网网络中基于层的安全威胁

Muna Muhammad, Ahthasham Sajid, and Hira Arshad

### 6.1 引言

物联网（IoT）是传感器、执行器、智能设备、智能系统或任何嵌入在互联网或通过互联网连接的、用于发送和接收与特定应用或服务相关的数据设备的互联。目前的物联网应用通常提供高效率、自动化和舒适性，因为工业目前正在生产大量包含智能应用的物联网设备。物联网通过智能应用（如智能家居 [1]、智能农业 [2]、智能城市 [3]、智能电网 [4]、智能制造 [5] 等）智能服务降低了个人对服务的控制和监控。物联网设备和服务的极端增长已席卷世界。具体而言，整个世界开始实施工业革命，并将工业推向数字经济的先进水平。根据《2021–30年全球物联网预测报告》，2021年底活跃物联网设备总计113亿，但到2030年这将大幅增加到294亿[6]。

#### 6.1.1 物联网中的安全

由于在大量的物联网应用中使用大量的物联网设备 [6]，通信必须是安全的，以保持用户数据隐私，防止物联网网络发生攻击且不存在漏洞。但通常情况下，物联网应用预计会面临许多安全挑战，因为物联网网络中的智能设备在带宽、不安全的基础和漏洞方面消耗更多功率。如果没有一个可信且互操作的物联网生态系统，其应用将无法满足需求，并因此失去其潜力 [7]。研究人员已经针对物联网数据交换的安全提出了不同的解决方案。IPv6 CoA 是 [8] 提出的协议，旨在保障物联网中的网络安全，特别是设备的互操作性。除了互联网面临的通用安全挑战外，无线传感器网络（WSNs）、蜂窝网络、云计算计算物联网也有其仍需解决的特定安全挑战，例如隐私数据泄露、用户身份验证、用户授权、加密、Web接口、安全威胁、数据存储等。

## 物联网网络中基于层的安全威胁

#### 表 6.1 影响物联网与 IT 安全的因素

| IT 安全 | 物联网安全 |
|---|---|
| 广泛的 IT 包含许多设备，且资源丰富。 | 物联网中的设备需要提供安全措施，但资源较匮乏。 |
| 广泛的 IT 依赖于资源丰富的设备。 | 物联网系统由资源匮乏的设备组成，如软件和硬件。 |
| 为了广泛的安全，使用了复杂的算法。 | 偏于轻量级算法。 |
| 由于同质化技术，安全性很高。 | 物联网包含异构技术，导致产生了大量异构数据，扩大了攻击面。 |

由于表 6.1 所示的许多因素，保护物联网环境通常比通用物联网设备更具挑战性 [7]。考虑到漏洞和问题，物联网环境为许多网络威胁铺平了道路。威胁或攻击发生在物联网网络的不同层；物联网网络架构的通用层如图6.1 所示。

由于物联网应用中的众多挑战，同一项研究中需要不同的解决方案和技术，以便通过不同技术理解并保护不同的物联网应用。本调查包含以下主要贡献：

- 识别物联网网络不同层中的安全攻击
- 识别物联网应用中的安全需求
- 对物联网中的漏洞、安全威胁和待解决问题进行分类
- 回顾现有的保护物联网系统的技术和方法
- 物联网安全的未来研究方向

#### 6.1.2 物联网中的安全挑战

物联网生态系统是由异构网络集成而成的。这不仅带来了早期通信网络的通用安全问题，还由于其特定属性引入了新的安全问题。这从传感器设备开始，包括监控环境变量并负责物联网中虚拟世界与物理世界的融合。传感器设备具有有限的存储和计算能力，防止了复杂稳健的安全系统（例如用于身份验证的系统）建立 [9]。另一个方面是物联网设备潜在移动性和普及性的异构性。随着物理设备或对象被安装并成为物联网的一部分，攻击面大幅增加。物联网网络中的智能环境带来了不同的漏洞，这些漏洞可以被攻击者利用。

![](img/6cda7de083ea84ec227ad15ed4045807_118_0.png)

图 6.1 物联网中基于层的问题和攻击。

此外，对于访问和身份验证过程，用如此大量的物联网设备管理身份更加困难。在信任方面，依赖物联网设备更具挑战性，因为它们倾向于被篡改。通过考虑网络层，物联网生态系统带来了通用漏洞，但由于缺乏可用标准，集成需求变得困难。

物联网应用中的异构性增加了安全挑战。许多应用需要敏感数据，如个人信息或工业过程监控数据。由于被攻击者利用的漏洞，实现安全目标非常困难，保护物联网中传输的数据非常重要，因此需要一个独特且集成的安全框架 [9]

#### 6.1.3 物联网的安全目标

通用安全属性——机密性、完整性和可用性（CIA三角）是必须的，特别是在物联网安全中，这些属性尤为重要。此外，身份验证和访问控制也是应该考虑的属性。通过信息的机密性，只有授权用户可以读取。通过信息的完整性，信息必须是准确且未被更改的。通过可用性，信息需要用户任何时候都可以。通过身份验证，在使用系统之前验证用户的身份。通过使用授权或访问控制，经过验证的用户获得访问特定资源的权限。通过实施所有安全属性，系统在漏洞和风险方面将是安全的，但如果缺失任何一项，将会出现安全问题。如果用户没有经过身份验证，就会产生漏洞，攻击者可以轻松进入系统并引发不同的威胁。之后，如果身份验证正确但没有授权，就会为攻击者访问系统中的任何资源创建不同的漏洞和机会，并影响整个物联网网络。

### 物联网的安全需求

通过了解影响物联网的这些通用安全问题，我们可以添加安全需求来增强物联网的安全性和隐私。相应的，也可以添加一些安全功能，例如防病毒软件、防火墙、安全软件等。加密算法可以满足安全需求，但需要在物理层引入特定的算法以满足安全需求 [10]。物联网安全的一些需求如下：

- 在部署设备时对风险进行估计
- 基于漏洞正确使用加密技术
- 对交换和连接设备进行正确的身份验证，以减少机密性问题
- 为整个物联网网络而非特定区域制定规划和策略
- 保护云端（作为数据存储的中心），配备适当的安全（在云端对数据加密可以减少被盗的风险 [11]）。
- 使用人工智能（AI）和机器学习的智能技术减少人工干预和计算负担 [12]

# 下一代计算技术的网络安全

## 6.1.5 IoT 环境

有大量的物联网（IoT）环境已从传统环境转向智能环境。文中讨论了以下此类物联网环境：

- *智慧城市*：智慧城市的开发旨在利用新兴的通信和计算资源来提高人们的生活质量。它涉及智能交通管理、智能家居、智能公用事业以及灾害管理等，如图6.2 所示。为了实现全国范围内先进的发展和智能化管理，需要将城市转变为智慧城市。尽管智慧城市旨在提高公民的生活方式，但给公民的隐私带来了许多问题。例如，如果使用了智能移动，用户的位置可能会被追踪；或者通过智能卡，用户的数据可能面临风险 [7]。

- *智能家居*：智能家居或家庭自动化是物联网的一个概念，将家庭及周围环境的不同应用控制在一个中心点上，以为用户提供安全、舒适、便利和保障。通过为家居环境增加智能化，可以提高生活质量。通过实施自动化，信息可以快速收集并在设备之间顺畅传输，因为它们被同时监控。所有设备都将连接到一个中心点，如图 6.3 所示。人们可以远程监控并控制家里所有的活动，并可以通过智能手机、笔记本电脑、PC 等不同设备进行处理 [13]。通过这种方式，人们可以远程访问和控制家居活动，在发生危险时向主人发送警报信息，并监控家中的能源消耗。尽管有所有这些

![](img/6cda7de083ea84ec227ad15ed4045807_120_0.png)

图 6.2 智慧城市组成。

- **智能工业平台：**随着物联网应用使用的剧增，人们已将目光转向工业平台物联网自动化。它是对工业中不同部门和任务过程的自动化，如信息收集、远程监控、劳动。通过该平台，工业工作可以变得更简单、高效且可靠。可以缩短工作时间，并通过一个点连接并监控不同的流程。它已用于数字油田、智能电网 [4]、智能化工行业、智能工厂等。

- **智能农业：**农业物联网实施用于监测土壤水分、干旱地区的入入选择、控制微气候条件以及控制温度湿度。通过使用物联网提供的这些增强农业功能，农民可以实现高产并避免经济损失。通过更好地控制蔬菜和谷物生产中的温湿度水平，可以防止微生物污染物和真菌，提高作物质量。然而，由于涉及云端数据存储和物联网环境，农民的数据隐私可能面临风险 [7]。

![](img/6cda7de083ea84ec227ad15ed4045807_121_0.png)

图 6.3 单点控制下的智能家居。

除了上述这些益处外，我们还需要考虑安全风险，例如业主隐私是否被破坏，或者物联网中是否出现了安全威胁。

# 物联网网络中基于层的安全威胁

## 6.2 跨物联网层的威胁

如图 6.1 所示，通常每个物联网环境都涉及四层：(1) 感知层处理传感器设备，负责从周围环境收集信息以供执行器使用。(2) 网络层负责通过建立传输网络来进行通信。(3) 中间件层作为网络层和应用层之间的中间层，有助于增强这两层的存储和计算资源。然后，网关是各层的接入点，它们提供了不同服务之间的互连。如果没有经过适当的身份验证，它们将非常脆弱。(4) 最后一层是应用层，负责为最终用户提供服务。接下来将讨论这些层的安全攻击。

### 6.2.1 感知层攻击

该层包括大量设备，如执行器、传感器、智能设备。该层的安全攻击和威胁如图 6.4 所示。

- *节点捕获/篡改*：这种攻击可以通过篡改节点或用恶意节点替换节点来实现。攻击者的目标是获取对物联网设备的访问和控制权。未受保护的环境使得捕获攻击非常困难。如果攻击者可以获得节点的物理访问权限，任何关键加密信息都可能被盗 [15]。

- *睡眠剥夺*：物联网设备电池较小，这使得它们更容易受到 DoS 攻击，在攻击中，攻击者试图耗尽电池并强制设备进入关机状态，导致拒绝服务 [16]。这会对应用程序的功能产生严重影响，例如在紧急情况下，设备将无法运行和报告紧急情况。此外，攻击者通过向边缘设备运行无限迭代的恶意算法导致设备睡眠剥夺，使设备保持唤醒并阻止进入睡眠模式，最终导致睡眠剥夺 [10]。

- *恶意代码注入攻击*：这种攻击通过向设备内存中注入恶意代码来实现。攻击者随后可以使用此类设备作为网关，执行如提供虚假信息和注入整个物联网系统等操作 [10]。

- *侧信道攻击 (SCA)*：这种攻击通过向设备内存中注入恶意代码来实现。攻击者随后可以使用此类设备作为网关，执行如提供虚假信息和注入整个物联网系统等操作 [10]。 (注：原文此处存在大量重复描述，译文已按逻辑精简)

# 下一代计算技术的网络安全

![](img/6cda7de083ea84ec227ad15ed4045807_124_0.png)

**图 6.4** 针对不同层的常见攻击。

- **云恶意软件注入攻击**：此类攻击的目标是通过使用恶意代码注入虚拟机来获取对云的控制。该虚拟机充当网络中的合法成员，以便访问物联网（IoT）系统提供的服务。
