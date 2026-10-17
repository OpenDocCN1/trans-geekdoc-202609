
# 本章概述

在本章中，在对恶意软件进行基础介绍和简要历史回顾后，我们讨论了恶意软件在新数字化转型时代的演变，以及某些用于中和或减轻其影响的反病毒技术的发展。本章讨论并回答了以下一些问题：

- 恶意软件如何影响我们的生活，它在新的数字化转型时代引发了哪些复杂性和挑战？
- 该领域有哪些新兴技术（例如云端恶意软件分析、对抗性机器学习等）是因为数字化转型而演变的？
- 攻击者如何使用混淆等不同技术创建如此复杂的恶意软件？
- 这些恶意程序是如何规避当前安全架构使用的某些技术的检测的？
- 恶意软件编写者如何创建原始恶意软件的变体（副本）使其不被反病毒程序检测？

最近，智能手机（尤其是安卓手机）中的恶意软件急剧增加。这些设备提供了来自各种市场的第三方应用程序。这通过安装并收集这些设备中的传感器数据和个人信息的恶意软件，构成了严峻的安全和隐私问题。最初，使用简单的技术（使用简单的特征码）来检测恶意软件。现在，这些技术已经演变为可以检测某些复杂的、多态的和变态恶意软件。

我们还讨论了困扰恶意软件分析和检测的一些关键挑战和问题，例如自动化、原生代码、混淆、变形和反逆向工程。我们提供了解决其中一些挑战和问题的解决方案和建议。为了刺激该领域的进一步研究，我们强调了一些未来的研究方向。我们相信，本章为兴趣了解更多恶意软件演变的未来研究人员提供了一个极具前景的基础，并将成为改进现有及开发新的恶意软件分析与检测技术的动力。

## 参考文献

- Aho, A. V., Lam, M. S., Sethi, R., & Ullman, J. D. (2007). *Compilers: Principles, techniques, and tools* (2nd ed.). Academic Press.
- Alam, S., Horspool, R. N., & Traore, I. (2013, November). MAIL: Malware Analysis Intermediate Language: a step towards automating and optimizing malware detection. In *Proceedings of the 6th International Conference on Security of Information and Networks* (pp. 233-240). 10.1145/2523514.2527006
- Alam, S., Qu, Z., Riley, R., Chen, Y., & Rastogi, V. (2017). DroidNative: Automating and optimizing detection of Android native code malware variants. *Computers & Security*, 65, 230-246.
- Alam, S., & Sogukpinar, I. (2021). DroidClone: Attack of the android malware clones - A step towards stopping them. *Computer Science and Information Systems*, 18(1), 67–91. doi:10.2298/CSIS200330035A
- Alam, S., Sogukpinar, I., Traore, I., & Coady, Y. (2014, September). In-cloud malware analysis and detection: State of the art. In *Proceedings of the 7th International Conference on Security of Information and Networks* (pp. 473-478). 10.1145/2659651.2659730
- Alam, S., Sogukpinar, I., Traore, I., & Horspool, R. N. (2015). Sliding window and control flow weight for metamorphic malware detection. *Journal of Computer Virology and Hacking Techniques*, 11(2), 75–88. doi:10.1007/s11416-014-0222-y
- Alam, S., Traore, I., & Sogukpinar, I. (2015). Annotated control flow graph for metamorphic malware detection. *The Computer Journal*, 58(10), 2608–2621. doi:10.1093/comjnl/bxu148
- Balakrishnan, G., & Reps, T. (2010). WYSINWYX: What you see is not what you eXecute. *ACM Transactions on Programming Languages and Systems*, 32(6), 1–84. doi:10.1145/1749608.1749612
- Bilar, D. (2007). Opcodes as predictor for malware. *International Journal of Electronic Security and Digital Forensics*, 1(2), 156-168.
- Clarke, E. M., Grumberg, O., & Peled, D. A. (1999). *Model checking*. The MIT Press.
- Goodfellow, I. J., Pouget-Abadie, J., Mirza, M., Xu, B., Warde-Farley, D., Ozair, S., Courville, A., & Bengio, Y. (2014). Generative Adversarial Networks. arXiv:1406.2661.
- Hasan, H., Ladani, B. T., & Zamani, B. (2021). MEGDroid: A Model-Driven Event Generation Framework for Android Malware Detection. 10.1016/infsof.2021.106594
- Hu, W., & Tan, Y. (2017). Generating adversarial examples for black-box attacks based on gan. arXiv:1702.0598
- Imtiaz, S., Rehman, S., Javed, A., Jalil, Z., Liu, X., & Alnumay, W. (2021). DeepAMD: Detection and identification of Android malware using high-efficient Deep Neural Network. *Future Generation Computer Systems*, 115, 84
- Martins, N., Cruz, J. M., Cruz, T., & Abreu, P. (2020). Adversarial machine learning applied to intrusion and malware scenarios: A systematic review. *IEEE Access: Practical Innovations, Open Solutions*, 8, 35403–35419. doi:10.1109/ACCESS.2020.297472
- McGraw, G., & Morrisett, G. (2000). Attacking malicious code: A report to the infosec research council. *IEEE Software*, 17(5), 33–41. doi:10.1109/52.8757
- Nagra, J., & Collberg, C. (2009). *Surreptitious Software: Obfuscation, Watermarking, and Tamperproofing for Software Protection*. Pearson Education.
- Narayanan, A., Bonneau, J., Felten, E., Miller, A., & Goldfeder, S. (2016). *Bitcoin and cryptocurrency technologies: a comprehensive introduction*. Princeton University Press.
- Szor, P. (2005). *The Art of Computer Virus Research and Defense*. Addison Wesley Professional.
- Zouave, E., Bruce, M., Colde, K., Jaitner, M., Rodhe, I., & Gustafsson, T. (2020). *Artificially intelligent cyberattacks*. Academic Press.

## 术语表

- **计算机取证**：计算机取证是数字取证科学的一个分支，涉及计算机和数字存储媒体中发现的证据。
- **控制流**：在计算机科学中，控制流是命令式程序中各个语句、指令或函数调用的执行或评估的顺序。
- **加密货币**：任何仅以数字形式存在的货币形式，它通常没有中央发行或监管机构，而是使用去中心化系统记录交易并管理新单位的发行，并依赖密码学来防止伪造和欺诈交易。
- **网络攻击**：为了造成损害或伤害而试图非法访问计算机或计算机系统的尝试。
- **调试**：在计算机编程和软件开发中，调试是发现并解决计算机程序、软件或系统内部错误（bug）的过程。
- **反编译器**：反编译器是一种计算机程序，它以可执行文件作为输入，尝试创建一个可以成功重新编译的高源代码。
- **嵌入式系统**：嵌入式系统是计算机硬件和软件的结合，设计用于较大系统中特定或多个功能。
- **终端系统**：终端系统是与其连接的网络进行双通信的远程计算设备。终端的一些示例包括台式机、笔记本电脑、智能手机、服务器、工作站和物联网设备。
- **指令集架构**：在计算机科学中，指令集架构（`ISA`）是计算机的抽象模型。
- **元语言**：用于描述或分析另一种语言的语言形式或术语集。
- **混淆**：混淆某些意味着使其变得不清晰或透明，就像脏水很难看清池塘底一样。
- **操作码**：在计算中，操作码（operation code）是机器语言指令中指定要执行的操作的部分。
- **符号执行**：在计算机科学中，符号执行（也称为符号评估）是一种分析程序的方法，用于确定哪些输入会导致程序的每个部分执行。
- **虚拟**：不是以物理形式存在，而是通过软件使其看起来存在。
- **漏洞**：漏洞指的是（系统或单元）抵御敌对环境影响的能力。

# 第 14 章

Tansif ur Rehman

![Orcid Image](https://orcid.org/0000-0002-5454-2150)

巴基斯坦卡拉奇大学

## 摘要

在这个科技时代，几乎所有知名银行都配备了与增强其服务密切相关的最新技术，并为客户提供了电子银行服务。然而，网络安全一直是许多机构的重点。银行正在提供更多设施，以方便客户在电子银行方面更加便利。然而，在巴基斯坦，情况并非如此。由于各种问题，人们仍然克制使用电子银行，但电子银行部门在过去十年中呈指数级增长。由于银行等企业仍鼓励客户进行电子交易（如公用事业费用支付、访问账户信息和转账），它更大的增长潜力。在此过程中，网络犯罪分子试图窃取客户数据并破解在线会话。对于电子银行欺诈，数字化引发了一场革命。网络犯罪分子利用各种工具通过身份盗窃、木马、病毒和网络钓鱼来窃取关键信息。

## 引言

金融、储蓄、私人和公立银行是易受网络安全威胁的各种类型企业。然而，它们共同拥有目标，即在网络空间为消费者、公司和政府资金提供服务这一必要前提。在当今世界，银行正经历数字化企业转型，并开展从贷款、购买房地产和车辆到大型贸易相关交易的金融活动（Holzhauer, 2021）。这些数字交易日益成为网络黑客的目标，导致了网络安全违规。因此，应该在这些机构中定期监控银行的网络安全，因为网络世界是一个充满风险的居所，在没有任何安全规定的情况下，存在窃取金钱的可能，以及其他风险和危害情况（Frazier, 2021; Phaneuf, 2021a）。使用网上银行的客户可以获得物理银行服务网点无法提供的广泛银行服务。这些企业从传统银行到移动设备不等，并且通常在互联网上进行（Marous, 2021; Overby, 2020）。然而，由于许多此类服务具有更高的数据盗取、数据入侵、数据黑客风险，因为客户并不清楚网络安全，而且安装的许多网络安全软件是非注册的、过时的、不合规的、没有更新，且对网络攻击的保护处于最低水平。

由于业务往来只需点击一下即可完成，它改变了个人关于其支出方式的行为。这种简单性和便利性吸引了客户关注商业机构保护其资金的方式。商业机构保护客户的资金（Amoros, 2019; Phaneuf, 2021b; Singh et al., 2006）。网络攻击对任何金融机构造成的损害很难计算，因为其影响不仅体现在经济方面。然而，其他因素使得评估变得具有挑战性，例如对组织声誉和信誉的损害，组织对机构和客户缺乏信任。因此，机构遭受网络攻击的代价将远高于网络犯罪分子窃取的金额。

虽然电子银行系统已引入多年，但网络犯罪案件在过去十年中开始剧增，特别是在过去几年中，随着社交媒体的出现，这往往揭露了人们信息的脆弱性。因此，电子银行的使用有所减少，而风险呈指数级增长（Amoros, 2019; Zaidi, 2021）。然而，由于其他因素，例如新的加密系统，它在最近增加了实力。如果客户决定被抢劫，这一切并无益处，因为这主要执行了这一点。网络犯罪分子利用客户在数据安全方面的天真和缺乏经验。此类方法的风险产生程度与保护方法的推广程度相当（Carminati et al., 2018; Overby, 2020）。

电子支付系统，也称为电子银行或网银，允许银行客户通过基于互联网的网站和银行进行交易。它为拥有资源的银行提供了互联网访问。它还提供了多种服务，包括转账、账单支付、账户验证、在线购物和充值（Li et al., 2021）。网上银行因为其方便易用、访问快速、成本效益高且可以随地进行而流行。由于这些优点，在线伪造（即利用个人账户转移资金以获取商业利益）正成为网络欺诈的焦点。

目前，网上银行欺诈已位居全球网络犯罪列表的顶端。因此，对于银行的安全和身份验证策略的竞争力而言，这是一个至关重要的时代。然而，网络犯罪分子构建了先进的工具和技术来入侵银行网络。电子银行网络必须拥有可靠的安全协议，能够准确识别用户并授权连接，从而减少欺诈。这涉及到两种关键的识别方案：即客户此前持有的独特机密数据和银行密码，以及访问设备指纹服务所需的唯一设备特征。然而，如果这些方案中的任何一个被攻破，整个网络安全系统将受到损害（Khrais, 2015）。

因此，巴基斯坦的电子银行发展落后于发达国家（Akhlaq, 2011）。对巴基斯坦未来电子银行进行彻底审查无疑需要在多个领域进行研究。研究旨在识别阻碍巴基斯坦客户采用电子银行服务的问题。在巴基斯坦，2002 年通过了《电子交易条例》（ETO），用以进一步促进电子商务活动，并为电子交易提供了法律保护。它还高度重视公钥基础设施（PKI），这是一套数字加密技术和设施。它允许多家企业以最大程度对其在线通信和业务活动进行加密。

许多以往的研究倾向于仅关注电子银行的积极影响，例如效益（Suganthi, Balachandher, & Balachandran, 2001）、信任度（Suh & Han, 2002）以及创新（Gerrard & Cunningham, 2003）。这项研究在卡拉奇进行，因为它是巴基斯坦最大的城市，人口达 149 万，并汇聚了来自巴基斯坦的多民族的人群。它将帮助银行制定合适的计划，以确保消费者尽可能快地迁移到网上银行，让这种自助服务技术更有效、更方便地增长。

## 背景

网上银行在全球范围内仍被广泛使用，很难想象它在不久前还不存在。20 世纪 80 年代初，纽约的中央银行开始向客户提供家庭化银行服务。客户可以随时访问其银行账户、显示银行账单、支付账单并查看银行语句。尽管如此，电子银行运动始于 20 世纪 90 年代中期，当时互联网被认为是一种有前景的传播媒介。使用电子银行带来的舒适和快捷引发了突破，从根本上改变了商业环境。

虽然银行接触的开放程度以及个人账户管理的便利性具有优势且极具前景，但人们很快发现这种便利是付出了代价的。通过网络入侵，网络犯罪分子开始看到电子银行在实现获取金钱利益的恶意动机方面的潜力。电子银行诈骗迅速取代了传统的银行欺诈策略。然而，作为结果，寻求增长的银领域所拥抱的技术进步也开启了高级别网络威胁的视野。这可能导致系统出现新的脆弱性和复杂性。

在当今时代，黑客正在寻找这些漏洞，并发现并采用针对现代银行系统漏洞的新策略。针对所审查的关键主题，即网上银行诈骗，已开展了不同的研究。这方面的研究涵盖了预防性保护措施、框架改进以及伪造识别。银行不断提高安全性，并使用各种方法保持基础设施安全，包括加密业务网络、双重认证以及确保无人利用系统的各种技术。人员使用数据分析软件检查银行业务记录，以确定内部控制的充分性并识别伪造交易。

当银行采取的安全措施收紧时，黑客的技术也随之进步，因为他们努力保持领先一步。因此，需要几个小时来理解该方向的安全步骤，即等同于这些网络犯罪分子所应用的技术。因此，该领域需要高技能的网络安全专业人才，他们头脑敏捷，能够勤奋致力于电子银行系统安全，并有能力实现所有潜在网上银行伪造的应对措施。

## 研究侧重点
