
![Image](img/fig25_8.jpg)

图 25.8 Android 的卡仿真模式实现。

`HCE` 与简单的卡仿真不同，因为卡仿真代表了从外部非接触终端读取器直接到嵌入式 SE 的通信路由。事实上，操作系统并不控制此类通信。只有 SE 和 NFC 控制器参与，手机在读取器看来是一张非接触式智能卡。示例包括 Google Wallet、Softcard。由于卡仿真代表了从外部非接触终端读取器直接到嵌入式 SE 的通信路由，事实上，操作系统并不控制此类通信。只有 SE 和 NFC 控制器参与，手机在读取器看来是一张非接触式智能卡。然而，对于 Softcard 以及其他依赖卡仿真的 NFC 钱包，这种解决方案的缺点是 SE 访问速度慢，且向 SE 分发凭据是一个复杂的过程，涉及多个 TSM 以及多种 SE 类型。

值得注意的是，`HCE`（或软件卡仿真）与卡仿真不同，因为它不是将接收到的 NFC 指令直接路由到 SE，而是将其传递给安装在手机上的应用程序。因此，这种方法允许通过将凭据存储在任何地方（例如应用程序内存、`TEE` 或云端）打破对 SE 的依赖。在 `HCE` 方法引入的所有优点中，最重要的包括 [27]：

- NFC 仅作为通信标准使用，允许与 POS 通信。
- 无需担心复杂的 SE 分发。
- 多个 NFC 钱包可以在手机上，而不必担心 SE 容量或隔离。
- 无需为运营商进行空中 SE 分发和生命周期管理。

然而，这并非理想的解决方案，因为 Android 尚未向应用程序暴露软件仿真，且 `HCE` 补丁尚未合并到主分支。因此，除非智能手机已 root（根），否则 Android 用户无法使用它们。SimplyTapp [27] 被提议作为通过 NFC 支付的替代方案。在前者中凭据存储在云端，而在后者位于嵌入式 SE 中。SimplyTapp 通过创建一个 `HCE` 补丁来工作，解决了两个竞争应用程序（SimplyTapp 和 Google Wallet）注册同一个非接触读取器 NFC 事件时可能产生的冲突。

除了引发 `HCE` 趋势的 SimplyTapp，Android 4.4 还引入了通过 `HCE` 进行安全 NFC 交易的新平台支持，用于支付、忠诚计划、卡访问、通行和其他自定义服务。通过 `HCE`，Android 设备上的任何应用程序都可以仿真 NFC 智能卡，让用户可以使用他们选择的应用程序启动交易——无需设备中预置的 SE。应用程序还可以使用新的读取器模式作为 HCE 卡和其他基于 NFC 交易的读取器。Android `HCE` 需要设备中存在 NFC 控制器。`HCE` 支持在大多数 NFC 控制器上已广泛可用，这些控制器动态支持 `HCE` 和 SE 交易。支持 NFC 的 Android 4.4 设备将包含 Tap & Pay，以便使用 `HCE` 进行便捷支付。

### 25.6 相关工作

关于移动计算可信执行环境，Bouzefrane 和 Thinh [28] 旨在充分利用云计算设施的可用性，特别考虑移动云计算 (MCC)。MCC 允许移动用户利用云基础设施来克服移动技术的局限性，即限制存储、处理能力和电池寿命。特别是，Bouzefrane 和 Thinh [28] 调查了多种可用的可信平台，以评估 MCC 可信平台的安全性。该调查包含了对 `SE`、`HCE`、`TEE` 和 `TPM` 可信平台安全方面的概述。

TCG 软件栈（TSS）规定了应用程序开发者使用 TPM 提供的函数的软件层。然而，当前的 TSS 接口非常复杂，导致其使用非常困难且容易出错，这种高复杂性使其不适用于嵌入式设备或安全内核。Stüble 等人 [29] 提出了一种简化的 mTSS 设计和实现，基于 TPM 主规范为开发人员提供了一个轻量级且直观的编程接口。mTSS 设计的主要原则是降低复杂性、获取类型安全、对象封装和简单的错误处理。这些原则确保了所生成的 mTSS 具有可维护性且易于使用。此外，mTSS 的模块化架构允许根据需要仅使用提供的功能子集，例如用于嵌入式系统、移动设备或在安全内核的境下。

Winter 和 Dietrich [30] 分析了 TPM 与宿主平台之间的通信。虽然 TPM 被认为具有防篡能力，但这些模块与可信平台其他部分之间的通信通道被证明相当不安全。研究表明，可以使用相当廉价的设备对 TPM 及其总线通信进行被动攻击。然而，尚未报告过类似的主动攻击。Winter 和 Dietrich 追求主动攻击的想法，并展示了如何主动操纵 LPC 总线的通信协议，并展示了如何利用我们的这些操纵来绕过现代可信平台提供的安全机制（例如信任链）。Gonzáles 和 Bonnet [31] 提出了一种结合商用硬件和开源软件的框架，可以作为可信执行环境，用于研究未来的大数据平台（另见 图 25.9） [31]

基于 PKI 的 TCP 需要平台用户申请多个平台标识密钥（Platform Identity Key）证书以提供远程度量，且用户必须支付数字证书费用，这增加了用户的经济负担，导致几乎没有 TCP 真正执行过 TC（信任计算）的核心功能——平台远程度量，因此 TCP 的应用并不广泛。Yu 等人 [32] 提出了一种基于分层组合公密钥的 TC 方案，该方案可以减少单私钥生成器的风险，并允许验证者在没有第三方参与的情况下直接身份验证 TCP，因此平台用户不需要申请额外的数字证书。这种方案可以降低用户使用 TCP 的成本，并鼓励 TCP 应用的发展。

![Image](img/fig25_9.jpg)

图 25.9 UCON[ABC] 模型：参考监器根据属性、授权、义务和条件强制执行使用决策。（经 Springer Science+Business Media 许可：Cyberspace safety and security, lecture notes in computer science, Towards an open framework leveraging a trusted execution environment, Vol. 8300, 2013, pages 458–467, Javier González and Philippe Bonnet）。

提到在 OASIS 中存在的不可信执行环境 [33]，OASIS 是一种 CPU 指令集扩展，用于外部验证的隔离执行环境的启动、执行和终止，其 TC 基础完全由 CPU 组成。OASIS 利用商用 CPU 上可用的硬件组件来实现低成本、低开销的设计。

Jasim 等人 [34] 的一篇有趣的论文引入了 CCCE，这是一种结合了量子密钥分布（QKD）机制和高级加密标准的加密环境。另一个相关的贡献是 Iso-X [35]，这是一个灵活、细粒度的硬件支持框架，它为应用程序的安全关键部分提供隔离，使其即使在存在不可信系统软件的情况下也能安全地执行。Iso-X 通过创建和动态管理隔间（compartments）来托管关键代码片段和相关数据来实现隔离。Iso-X 在内存页级提供了细粒度的隔离、灵活的内存分配以及低复杂度的、纯硬件 TC 基础。Iso-X 需要极少的额外硬件、少量的新 ISA 指令来管理隔间，以及对操作系统进行极微的修改（而操作系统不需要在 TC 基础中）。Iso-X 声称比 Intel 的 SGX 设计具有更高的内存灵活性，允许可用内存空间进行流式分区以及隔间的动态增长。

如 Dunn 等人 [36] 等所示，TPM 也可以用于传播恶意软件。事实上，TPM 可以实现隐蔽计算（cloaked computation），其内存状态无法被任何其他软件（包括操作系统和虚拟机管理器）观察。Dunn 等人证明恶意软件可以使用隐蔽计算向恶意分析人员隐藏关键信息（如攻击目标）。受感染的主机可以向恶意分发平台证明此密钥的合法性，并以防止软件可见的方式接收并执行加密负载。

恶意操作系统内核可以轻松访问主内存中的用户数据和人机交互数据，即使在利用了隐私保护的情况下。Ren 等人 [37] 引入了 AppSec（见图 25.10），这是一种基于虚拟机的安全执行环境，能够透明地保护安全敏感应用程序的内存数据人机交互数据。AppSec 引入了一个安全加载器来检查应用程序和共享对象的代码完整性。在运行时，AppSec 保护应用程序和共享对象不被修改，并根据应用程序的意图验证内核访问。AppSec 提供了设备隔离机制，防止受损内核访问人机交互设备。此外，AppSec 进一步提供了一个基于特权的系统来保护应用程序资源。AppSec [37] 的主要有趣特性是它在运行时验证并保护共享对象。AppSec 根据应用程序的意图调停内核访问，但并不加密所有应用程序数据。此外，AppSec 提供了从端用户到应用程序的可信 I/O 路径。

图 25.10 Ren 等人的 AppSec 架构。（出自 Jianbao Ren 等 al. Appsec: A safe execution environment for security sensitive applications. In Proceedings of the 11th ACM SIGPLAN/SIGOPS International Conference on Virtual Execution Environments, VEE ’15, pages 187–199, ACM, New York, NY, 2015。）

### 25.7 总结

本章调查了一些相关的 TC 环境解决方案。考虑到云计算在安全和隐私方面需要相关的改进，本章展示了云如何利用可信执行技术来帮助保护代码执行并保护数据访问。大多数相关的硬件/软件行业和研究解决方案已经描述和讨论。然而，大多数研究工作正积极致力于开发新型、更先进的解决方案，因为目前的解决方案尚未证明具有足够的安全性。

## 参考文献

1. Sam Johnston. *Cloud computing*. Wikimedia Foundation, San Francisco, CA, 2013.

2. Helmut Krcmar, Ralf Reussner, 和 Bernhard Rumpe. *可信云计算*. Springer Publishing Company, 2014.

3. Vibhav Agarwal. *云与网络安全*. 西雅图, WA, 2014, 可访问 [`blog.cloudsecurityalliance.org`](http://blog.cloudsecurityalliance.org)。

4. Weiqi Dai, Hai Jin, Deqing Zou, Shouhuai Xu, Weide Zheng, Lei Shi, 和 Laurence Tianruo Yang. TEE: 一种用于安全云端计算的基于虚拟 DRTM 执行环境。*Future Gener. Comput. Syst.*, 49(C):47–57, 2015.

5. Liqun Chen 和 Jiangtao Li. `TPM` 2.0 中灵活且可扩展的数字签名。Proceedings of the 2013 ACM SIGSAC Conference on Computer and Communications Security, CCS ’13, pages 37–48, ACM, New York, NY, 2013.

6. Guillaume Piolle. *TPM*. Wikimedia Foundation, 旧金山, CA, 2013.

7. Richard Stallman. *你可以信任你的电脑吗？* Free Software Foundation, 波士顿, MA, 2015.

8. Katharina Krombholz, Heidelinde Hobel, Markus Huber, 和 Edgar Weippl. 高级社会工程攻击。*J. Inf. Secur. Appl.*, 22(C):113–122, 2015.

9. ARM. *TrustZone 硬件架构*. ARM Ltd., 剑桥, 2013.

10. Michael Pearce, Sherali Zeadally 和 Ray Hunt. 虚拟化：问题、安全威胁与解决方案。*ACM Comput. Surv.*, 45(2):17:1–17:39, 2013.

11. Raoul Strackx, Bart Jacobs, 和 Frank Piessens. Ice: 一种被式的、高速的状态连续方案。Proceedings of the 30th Annual Computer Security Applications Conference, ACSAC ’14, pages 106–115, ACM, New York, NY, 2014.

12. Frank McKeen, Ilia Alexandrovich 和 Carlos Berezon. *Intel 软件防护扩展*. Intel Corp., 圣拉拉, CA, 2013.

13. Intel. *Intel 软件防护扩展*. Intel Corp., Santa 圣拉拉, CA, 2013.

14. Ramya Jayaram Masti, Claudio Marforio 和 Srdjan Capkun. 云中安全环境并发执行架构。Proceedings of the 2013 ACM Workshop on Cloud Computing Security Workshop, CCSW ’13, pages 11–22, ACM, New York, NY, 2013.

15. Chen Chen, Himanshu Raj, Stefan Saroiu 和 Alec Wolman. cTPM: 一种用于跨设备可信应用的云 `TPM`。Proceedings of the 11th USENIX Conference on Networked Systems Design and Implementation, NSDI’14, pages 187–201, USENIX Association, 伯克利, CA, 2014.

16. Changlong Tang 和 Jiqiang Liu. 为你的 `SaaS` 程序选择可信云服务提供商。*Comput. Secur.*, 50(C):60–73, 2015.

17. Jiun Yi Yap 和 Allan Tomlinson. 可信平台模块的半虚拟化：一种基于版本 2.0 的企业框架。Proceedings of 5th International Conference on Trusted Systems—Volume 829, INTRUST 2013, pages 1–16, Springer-Verlag, 新纽约, NY, 2013.

18. David Wallom, Matteo Turilli, Andrew Martin, Anbang Raun, Gareth Taylor, Nigel Hargreaves 和 Alan McOran. myCloud: 针对安全计算的可信基础设施。

 of0,, 2010, and ,...移动 1 computing。Proceedings of 2011 IEEE International Conference on Cloud Technology and Science, CLCOM ’10, pages 247–254, IEEE Computer Society, 华士顿, DC, 2011.

19. Chris Newcombe, Tim Rath, Yang Mao, Bogdan Munteanu, Marc Brooker 和 Michael Humphrey. 亚马逊 Web 服务使用的形式化方法。*Commun.*, 58(4):66–73, 2015.

21. Johannes Winter 和 Kurt Dietrich. 可信平台通信接口的攻击者指南。mobile computing. Proceedings of 2014 IEEE International Conference on High Performance Computing and Communications, HPCC ’14, pages 1068–1075, IEEE Computer Society, 华盛顿, DC, 2014.

22. Javier González 和 Philippe Bonnet. 通向利用可信执行环境的开放框架。

23. Lishoy Francis, Gerhard Hancke, Keith Mayes. 移动手机上的安全-element relay 攻击。

Proceedings of 6th International Conference on Radio Frequency Identification, RFIDSec’10, pages 35–49, Springer-Verlag, 柏林, 海德堡, 2010.

24. Michael Roland. 攻击真实世界的近期安全元素。*CoRR*, abs/1209.0875, 2012.

25. NFCForum. *简单 NDEF 协议, v1.0*. Technical report, 2011.

26. Pascal Urien. `LLCPS, draft-urien-00.txt`. Technical report, Telecom Paris, 2012.

27. SimplyTapp. *面向全民的安全移动支付*. Technical report, 奥斯汀, TX, 2015.

28. Samia Bouzefrane 和 Le Vinh Thinh. 安全云计算的可信平台。

29. Christian Stüble 和 Anoosheh Zaerin. muTSS: 一种增强的可信软件栈。Proceedings of the 3rd International Conference on Trust and Trustworthy Computing, TRUST ’10, pages 124–140, Springer-Verlag, 柏林, 海德堡, 2010.

31. Fajiang Yu, Tong Li, Yang Lin, 和 Huanguo Zhang. 2011.
