
为了`sake`患者做出明智决策，使用了从`IoT`收集的信息。完全交互的技术加强并改进了治疗效果。

## 4.5 IoHT 中的安全协议

本节详细描述了在利用物联网时确保通信环境安全的某些协议。上述节描述的安全问题可以通过以下分类类别的不同协议来处理（图 4.6）。这些安全协议也可用于医疗健康物联网 (`IoHT`) 安全模型 [33]。

![](img/81d4baf48f6d3ce2c324d659b1914fad_93_0.png)

图 4.6 IoHT 中的安全协议。

### 4.5.1 密钥管理

密钥管理协议解决`IoT`/`IoHT`通信实体加密密钥的访问、分配和实现。为了提高性能，整个过程的制定通过将步骤划分为某些部分来实现。这些步骤包括一系列工作，如密钥生成、密钥交换、密钥使用以及密钥取消步骤。密钥管理机制涉及密钥服务器知识（即可信设备实体）、单独的用户分类（如电话或静态）以及多台机器，并使用密码学方法（即`IoT`设备）。应该开发严格的密钥管理机制来执行受保护通信 [34]。

### 4.5.2 用户/设备身份验证

这是一种定义和检查联系组身份的方法。在共享认证环境中，不同的用户可以共享其身份（例如患者、智能医疗设备）。人们可以验证另一个用户或设备以访问或参与通信。对于未来的通信，它们可以创建一个组内每位成员都可以访问的会话密钥。

### 4.5.3 访问控制/用户访问控制

访问控制已被用于，其主要目标是限制访问控制计算机的用户对网络/系统的资源。通过此过程，为用户/设备提供了访问若干可用资源的链接。研究得出结论：智能设备与`IoT`和`IoHT`的系统架构相结合，这确保了框架寿命的延长。可能会出现由于电池故障或某些物理损伤导致的机器故障情况。攻击者还可能在网络上部署设备。文献解释认为，需要对原始系统与具有恶意意图的系统进行区分。这一目标可以通过设计安全网关来实现，通过授予控制机制，该机制能够具有隔离系统访问`IoT`/`IoHT`平台的能力。

### 4.5.4 入侵检测

入侵或异常检测是当今快速增长的通信系统和互联网服务面临的最大挑战之一。随着互联网应用的增加，安全威胁也随之增加。因此，为了检测互联网上的恶意活动，入侵检测被认为是一种有效的安全工具。根据研究，机器学习技术被认为是一种更广泛的应用，用于设计更高效的入侵检测工具，以实现高准确率和低误报率。通过应用机器学习方法，可以为这种庞大的网络数据集构建更准确的预测模型，而这使用传统的安全工具是无法实现的。基于机器学习的`IDS`学习网络中捕获的数据模式，以确定其行为是异常还是正常。传统的`IDS`只能识别机器已知的攻击。它无法确定未知攻击及其行为。僵尸网络程序存在架构干扰的可能性，该程序专门针对`IoT`架构的内存，将恶意软件引入其特定的攻击代码中。此类攻击的结果是系统完全崩溃或程序故障。某些情况可能会导致架构运行异常。可能存在更极端、离谱的情况，例如对植入心脏起搏器的患者产生电击，这可能导致其死亡。得出的结论指向：确保`IoT`框架在通信过程中免受不必要的入侵的适当保护 [33–38]。

## 4.6 机器学习在 IoHT 入侵检测中的应用

如今物联网（`IoT`）是技术进步时代的一个里程碑，特别是对于千禧一代来说，因为这一代人只经历过人类时间线上的全球化后期时期。在健康监测部门，在医生或其他合格医疗助理在场的情况下进行人工检查是监测患者恢复的不可争议的必要性。医疗测试结果需要等待几天，然后根据诊断进行解释。研究描绘了由`IoHT`驱动的、依赖`IoT`平台监控的系统中，涉及隐私因素更为关键且困难的医疗安全问题。`IoT`平台的前提条件要求在基于`IoT`的工作架构的基础上增加额外的设备定位服务，以提高隐私以及安全问题方面的性能。架构设计为`IoHT`系统提供了分层功能，必须为每一层设计安全和隐私准则。必须为每一层实现适当的隐私设计，从而防止来自多种旨在通过这些算法精确识别的网络攻击。图 4.7 提到了一些主要问题。

在本节中，研究人员的一些主要贡献集中在利用机器学习或人工智能进行入侵检测领域。在 [33] 中，作者设计了一种用于`IoT`应用网络异常检测的模型。该模型从数据中提取样本以分析网络流量的行为，这种行为可能会导致网络破解。在 [39] 中，作者提供了关于不同机器学习方法以及机器学习工具的综述，以提供基于云的`IoT`框架，应用机器学习为数据提供安全保护。在 [40] 中，作者利用生物识别特征结合机器学习构建了实时健康监测系统。被监测的数据在远程进行诊断，并在安全网络上做出治疗决策。中间人攻击在此被视为一种入侵，通过机器学习检测到，检测率从 7% 提高到 25%。在 [41] 中，作者设计了一个模型来保护连接了医疗设备的网络。设计了一个集成回归机器学习的代理模型以观察网络。在 [42] 中，作者开发了一种异常-`IDS`以区分网络流量为异常或正常。作者使用主成分分析减少了数据的维度。该工作假设了云存储存储系统。在 [43] 中，作者在雾计算网络上提出了一种深度学习入侵检测系统。

![Attacks in IoHT](img/81d4baf48f6d3ce2c324d659b191fad_99_0.png)

图 4.7 IoHT 中的攻击。

医疗健康物联网

处理数据在应用了雾节点的分布式网络中收集。然后使用深度学习对收集的数据进行处理和分析。这项工作使用了反传播学习，在训练过程中可能会引起复杂问题。在 [44] 中，为了更快的训练和更准确的结果，工作在基于雾的架构中通过`OS-ELM`机器学习进行了扩展。在 [45] 中，通过应用在线学习机器学习`EOS-ELM`的集成来检测雾网络中的恶意活动，改进了工作。在 [46] 中，作者将深度置信网络（`DBN`）应用于`IoT`入侵检测，对已知攻击实现了 99% 的精确率，但对未知攻击的精确率为 86%。在 [47] 中，作者提出了用于`IoHT`入侵检测的`PCA-GWO`算法，实现了 99.9% 的准确率和 93.2% 的灵敏度。在 [48] 中，作者针对智能城市中的`IoT`应用提出了一种分布式入侵检测，并实现了 99% 的检测率，但针对二分类。

## 4.7 提出的框架

众周知在`IoT`环境中，网络产生并传输了大量数据。为了为了分析处理和组织这些海量数据，准确性是一个需要关注的重要因素之一。对于大型数据集，在医生和患者通信期间，手动特征选择需要很长的时间。在`IoHT`中，多个传感器被用于监测个人健康。因此，需要监控网络流量以防止敏感数据被入侵者窃取。这可以通过机器学习以及深度学习来实现。对于网络安全、入侵检测，深度学习在特征选择和数据包的异常与正常分类方面证明了优于其他方法的有效性。在本节中，现有机器学习方法中发现的一些主要问题如下：

- 对未知攻击无效。
- 仅适用于二分类。
- 在多分类中性能水平会下降。
- 计算和通信开销高。
- 大多数工作是集中协调的。
- 如果中心管理员被攻击，决策也可能发生改变。
- 无关特征的识别会增加计算时间并降低准确率。

图 4.8 展示了提出的用于`IoHT`的入侵检测框架。该框架概述了一个通用框架，主要由三层组成：数据层、通信或网络层、存储层和分析层。数据层由智能传感器数据或任何与患者、医院或保险公司相关的信息组成。收集的数据（来自传感器或任何数据）被传输到下一层，即通信或网络层。该层由网关或交换设备组成，负责分析收集的网络数据。使用机器学习对异常包进行分析并报告给管理员。正常数据包随后被传输到下一层用于存储和分析。收集到的数据由医生或专家进行分析，并进一步存储在云服务器上，患者可以通过身份验证访问这些报告。因此，该框架是双向的，且安全、健壮且灵活的。

![](img/81d4baf48f6d3ce2c324d659b1914fad_101_0.png)

图 4.8 IoHT 中的安全协议。

所提模型的算法所示：

```
Algorithm:
1. 开始
2. 输入: 入侵特征集={F₁, F₂, ...F_n}
3. 输出: 入侵报告 → Data(status)
4. 节点初始化与部署
5. 数据包捕获雾→传感器节点
6. 特征提取
7. 数据分析雾→相关性分析与降维
8. 集成 DNN 训练
9. 决策雾→Data(status)
10. 生成告警
11. 更新学习模型
12. 结束
```

所提模型由四个分布式雾化节点组成，它们相互通信，以便更好地识别网络攻击（图 4.9）。

协调节点：该节点处理来自现有有入侵数据库的训练过程，并训练集成`DNN`网络以创建决策规则。训练基于`TCP`、`UDP`和`ICMP`协议类型进行。

数据包捕获雾节点：该节点收集网络流量并传递给下一个节点。

数据分析雾节点：该节点提取特征并发现特征之间的相关性。相关特征被进一步考虑处理，从而实现特征降维。

![](img/81d4baf48f6d3ce2c324d659b1914fad_102_0.png)

图 4.9 提出的多雾架构。

雾节点：该雾节点负责决定分析和处理未分类的数据包。根据协议（即`TCP`、`UDP`和`ICMP`）对数据包进行分类。它允许网络和安全管理员通过与入侵数据库和深度训练算法交互，对所有检测到的入侵执行报告任务。该雾节点本质上是分布式的，如图 4.10 所示。

下面讨论了所提算法的关键特征，这些特征对未来的研究方向有所贡献：

- 所提框架通过融合隐私保护和深度学习方法，可以增强医疗物联网（`IoHT`）的安全性和可信度。
- 使用仿生优化技术进行特征选择消除了局部最优的缺点，且收敛速度更快。
- 通过应用特征还原结合深度学习方法，缩短了训练时间。
- 性能水平的提高需要高度相关的特征。不必要的特征会导致计算复杂性增加。

![](img/81d4baf48f6d3ce2c324d659b1914fad_103_0.png)

图 4.10 提出的分布式分类。

- 所提框架在`IoHT`场景中是有效的，因为该方法可以处理大量的医疗数据以及最佳特征。
- 特征减少后执行速度更快，能够更快告警入侵并采取预防措施。

## 4.8 结论

医疗物联网（`IoHT`）作为一种改进医疗部门的兴起技术出现，但其在互联网上的部署了安全和隐私问题。许多现有架构、算法或协议容易受到网络攻击。因此，本章的主要范围是概述`IoT`或`IoHT`的各种入侵检测系统。然而，每天都有新的攻击出现，本章的主要目标是提出一种利用深度学习保护数据隐私的框架。该框架将整合隐私、安全性和性。

## 参考文献

1. Gubbi, J., Buyya, R., Marusic, S., Palaniswami, M., Internet of Things (`IoT`): A vision, architectural elements, and future directions. Futur. Gener. Comput. Syst., 29, 7, 1645–1660, 2013.

2. Atzori, L., Iera, A., Morabito, G., The internet of things: A survey. Comput. Netw., 54, 15, 2787–2805, 2010.

3. Kumar, M., and Chand, S., Secure and Efficient Cloud-Centric Internet-Medical-Things-Enabled Healthcare System With Verifiability. IEEE Internet Things J, 7, 10, 10650–10659, 2020.

4. Song, T., Li, R., Mei, B., Yu, J., A privacy protocol for `IoT` in smart homes. IEEE Internet Things J, 4, 1852–1852, 2017.

5. Tawalbeh, L., Muheid, E., Tawalbeh, M., Kwaider, M., `IoT` privacy and security: Challenges. Appl. Sci., 10, 1012, 2020, https://doi.org/10.3390/app10102

6. Weber, R., Internet of Things—New security and privacy challenges. Comput. Law Sec. Rev., 26, 1, 23–30, 2010.

7. Ang, K.L., and Seng, J.K., Application Specific Internet Things (`AIoTs`): Taxonomy, use case and future directions. IEEE Access, 7, 5677–5690, 2019.

8. Montori, E., Bedogni, L., Bononi, L., Collaborative Internet of Things for smart cities and environmental monitoring. IEEE Int. Things J, 5, 2, 592–605, 2018.

9. Khan, M., Islam, M.S., Deng, H., Design of a reconfigurable sensing platform toward the future Internet Things. IEEE Int. Things J, 1, 4, 300–310, 2014.

10. Tran-Dang, H., Kromnacher, N., Champertier, P., Kim, D., Toward the Internet of Things for physical internet: Perspectives and challenges. IEEE Int. Things J, 7, 6, 4711–4736, 2020.

11. Li, X., Wei, P., Wei, Z.J., Quosong, L., Ping, W., Research on security issues of military Internet Things. Int. Comput. Wavelet Media Tech. Inf. Proc. (`ICCWAMT`), pp. 399–403, 2020.

12. Guth, J., Buticher, U., Falkenthaler, M., Lehmann, F., Reinfurt, L., Comparison of `IoT` platform architectures: A field study based on a reference architecture. Cloudification of the Internet of Things (`CIoT`); Paris, France, pp. 1–6, 23–25, 2016.

13. Bansal, M. and Gandhi, B., `IoT` based development boards for smart healthcare applications, in: International Conference on Computing Communication and Automation (`ICCCA`), Greater Noida, India, pp. 1–7, 2018.

14. Arias, O., Wurm, J., Hoang, K., Jin, Y., Privacy and security in internet of things and wearable devices. IEEE Trans. MultiClass Syst., 1, 2, 99–109, 2015, https://doi.org/10.1109/TMCS.2015.2498605

15. Yang, G., Jiang, M., Ouyang, Y., Xie, X., Rahmani, A.M., Lijberg, P., Tenhuen, H., `IoT`-based remote monitoring system: From device to cloud platform. IEEE J. Biomed. Health Inf., 22, 6, 1711–1719, 2017, https://doi.org/10.1109/JBHI.2017.276351

16. Das, A., Wajid, M., Kumar, N., Khan, M.K., Choo, K.K.R., Park, Y., Design of secure and lightweight authentication protocol for wearable devices environment. J Biomed. Health Inf., 22, 4, 1310–1322, 2017, https://doi.org/10.1109/JBHI.2017.275364

17. Kumar, P., Baereck, A., Gurtov, A., Linatti, i., Ha, P.H., Anonymous framework in smart home environments. IEEE Trans. Secur., 2, 4, 968–979, 2017, https://doi.org/10.1109/TIFS.2016.2647225

18. Wajid, M., Das, A., Kumar, M., Conti, M., and Vasilakos, A.V., A new authentication and key agreement scheme for implantable medical devices deployment. IEEE J. Biomed. Health Inf., 22, 4, 1299–1309, 2017.

19. Dua, A., Kumar, N., Das, A., Asikul, S., Secure message communication protocol among vehicles in smart city, IEEE Trans. Veh. Technol., 67, 5, 4359–4373, 2017, https://doi.org/10.1109/TVT.2017.2780183.
