
- 9. Andre Henri Mayer, Vinicius Ricardo, Cristiano Da Rocha, Alex Rocha, and Rodolfo Stoffel, “FogChain: A Fog Computing Architecture Integrating Blockchain and Internet of Things for Personal Health Records,” IEEE Access, 9, 7223–7237, 2021.

- 10. Carlos Perez-Gomez, Carmen, and Blanca Caminoero, “HIDRA: A Distributed Blockchain-Based Architecture for Fog/Edge Computing,” IEEE Access, 9, 5231–5251, 2021.

- 11. Ruhul Amin, S.K. Hafiz Ismail, Muhammad Khurram Khan, Arijit Karati, Debasis Gari, and Sarum Kumari, “A Two-Factor RSA-Based Robust Authentication for Multiserver Environments,” Security and Communication Networks, 7(1), 598–611, 2017.

- 12. Oussama Mounna, Abdelkim Ouatassim, Otman Manad, Tarik Hidar, Abnas El Kabul, Noureddine Ibnafar, “Privacy-Aware Authentication Based on Blockchain with Fault Tolerance for IoT Edge Computing,” In Fifth International Conference on Fog and Mobile Edge Computing (FMEC), pp. 347–352, IEEE, 2020.

- 13. Shyamalendu Kand, and Abhishek Ghosh, “Smart Card Based Remote User Authentication in Multierver Environment using Chebyshev Map,” Wireless Personal Communications, 133(4), 2657–2685, 2024, 10.1007/s11277-024-10895-w.

- 14. Shuan Sun, Weixin Bian, Dong Xie, Deqin Xu, and Yi Huang, “Lightweight and Privacy-Preserving Multi-server Authentication Scheme Based on PUF and Biometrics,” Journal of Intelligent and Fuzzy Systems, 45(1), 911–928, 2023, 10.3233/JIFS-221354.

- 15. Y. Liu, J. Zhang, and J. Zhan, “Privacy Protection for Fog Computing and the Internet of Things Data Based on Blockchain,” Cluster Computing, 2020.

- 16. P.K. Sharma, and J.H. Park, “Blockchain-Based Secure Mist Computing Network Architecture for Intelligent Transportation Systems”, IEEE Transactions on Intelligent Transportation Systems, 22(8), 5168–5177, 2020.

- 17. T.A. Oyewobi, S. Misra, and C. Lal, “Mobility as a Service (MaaS) Enabled Fog Computing: An Innovative for Smart City Infrastructure,” Journal of Ambient Intelligence and Humanized Computing, 10(1), 1–17, 2019.

- 18. T.A. Rahoof, and V.R. Deepthi, “HealthChain: A Secure Health Care Data Management System Using BC,” In Proceedings of International Conference on Distributed Computing and Internet Technology, 2020, pp. 380–391.

- 19. G. Li, M. Dong, L.T. Yang, K. Ota, J. Wu, and J. Li, “Preserving Edge Knowledge Sharing among IoT Services: A BC-Based Approach”, IEEE Transactions on Emerging Topics in Computational Intelligence, 4(5), 653–665, Oct. 2020.

- 20. P. Gope, and B. Sikdar, “Lightweight and Privacy-Preserving Two-Factor Authentication for IoT Devices,” IEEE Internet of Things Journal, 6(1), 580–589, 2018.

- 21. G. Srivastava, J. Crichigno, and S. Dhar, “A Light and Secure Healthcare Blockchain for IoT Medical Devices,” 2019 IEEE Canadian conference of electrical and computer engineering (CCECE) (pp. 1–5). IEEE., 2019.

# 第5章

# 使用机器学习模型保障物联网安全

Arbaz Adib Dalwai, Shivani Jaswal 和 Rohit Verma

物联网（IoT）可以被描述为革命性技术之一，因为它连接了事物、数据和云，以提高运营效率和集成性。但这种扩展的环境给 IoT 环境带来了严重的弱点，使其暴露在各种类型的网络威胁之下。在这些威胁中，分布式拒绝服务（DDoS）攻击相当独特，因为它们会淹没网络资源，导致服务无法运行。此类威胁不仅影响依赖 IoT 的操作或渐进控制，还会损害云平台 [1]。防火墙和入侵检测系统（IDS） [2] 等常见的安全解决方案已经在减少许多漏洞方面发挥作用。然而，攻击手段的不断进步要求在 IoT 背景下更强大、更智能的安全防护。由于传统的模式匹配在 IoT 架构有限带宽和计算能力的范围内，实时分析和分类变化的攻击方面存在局限性，因此必须切换到一种更好且对攻击更具韧性的系统。这些局限性促成了构建混合系统的必要性，该系统将先进的机器学习 [3]（ML）模型与 IDS 和安全信息和事件管理（SIEM）等系统技术相结合，以提高对 IoT 网络中 DDoS [4] 攻击的检测和区分能力。通过将基于规则和基于机器学习的方法集成到云环境中，系统的整体检测能力可以得到大幅提升。

为了应对动态云环境中不断演变的威胁格局带来的挑战，本研究调查了以下问题：

使用 SIEM、IDS 和机器学习模型的云端实时安全监控系统如何自适应且有效地区分类针对 IoT 设备的 DDoS 攻击？

本研究的首要目标是设计并实现一种混合安全解决方案，该方案将基于规则的检测与机器学习模型相结合，以增强系统准确识别模式的适应性，并最终保障 IoT 设备的安全。该研究将在仿真环境下进行测试来评估系统性能，仿真将模拟真实环境，以确定其能够实时检测和分类威胁。

图 5.1 展示了所提系统的核心组成部分。

本研究旨在通过几个关键点为网络安全领域做出贡献，例如展示 SIEM、IDS 和机器学习模型的实际集成：

![](img/1f35685e7cacbaf02cbf5bba7a561027_97_0.png)

图 5.1 网络安全威胁检测布局。

旨在创建一个混合检测框架，该框架能够通过防御 DDoS 等攻击保障 IoT 系统。通过 Kibana 仪表板提供视觉告警，本研究提供了实时洞察，帮助分析师做出更好的决策。尽管有这些贡献，研究并非没有限制。实验设置依赖模拟攻击流量，可能无法完全捕捉攻击的复杂性，这要求未来在更复杂的设置下测试该框架。

本章结构如下：5.2 节介绍了相关工作，详细说明了该领域现有研究的分析。5.3 节介绍了方法论概述，包含研究框架和实验计划的信息。5.4 节介绍了设计规范，5.5 节讨论实现，侧重于研究的技术方面。5.6 节提供了由实验结果和讨论组成的评估。最后，5.7 节总结本章并提出未来的改进方向。

### 5.2 相关工作

网络安全领域在过去几年中经历了巨大变化，集成了 SIEM 和 IDS 等先进工具进行实时威胁检测 [2,6]。此外，传统的网络安全实践也取得了许多进展，其中引入了机器学习模型。这些技术在不同攻击的检测和监控技术的整体增强中起着至关重要的作用。接下来的小节将讨论为本研究进行的文献综述。关键领域包括用于实时监控的 SIEM 和 IDS 的、IoT 系统及其相关的攻击/安全挑战，以及用于 DDoS 检测的机器学习模型实现。文献综述为本研究的方法论和实现部分奠定了基础。

#### 5.2.1 网络安全中的 SIEM、IDS 和机器学习模型

许多近期研究已彻底调查了 SIEM 和 IDS 解决方案的使用，定义了这些工具在云安全领域的重要性。Tuishime 等人（2023）[7] 的研究提出了一种基于 SIEM 的方法，通过虚拟机、负载均衡器和 Web 应用防火墙等组件进行云环境的威胁监控，以便建立日志分析的中心点。它特别强调了 SIEM 在生成自动告警以缩短响应时间方面，同时尝试评估框架在处理大量数据时的扩展性。然而，它主要关注系统架构和运行效率，在识别特定攻击类型方面的工作非常有限。Granadillo、Zarzosa 和 Diaz（2021）[8] 通过对现有 SIEM 解决方案进行全面分析（包括其功能、优势和局限性），进一步扩展了这一理解。它主要关注在网络安全基础设施中集成 SIEM 的必要性，同时也指出了解决方案必须面临的挑战。同样，Lee 等人（2017）[9] 的研究扩展了这些观点，设计了一种用于云端安全即服务（SeCaaS）的 SIEM 架构。该研究描述了在将 SIEM 系统适配于云原生应用时的关键因素，包括扩展性、灵活性和多租户性。然而，这项研究缺乏用于在真实场景中测试系统的评估集。

为了进一步改进 SIEM 技术，Ayu 等人（2024）[10] 提出了将机器学习与 SIEM 集成的概念，以改进传统基于规则系统的缺陷。研究人员使用随机森林（RF）分类器在 CSE-IDS-2018 数据集上实现了异常检测，该数据经过了主成分分析的预处理。尽管结果良好，但该研究未在实时数据上评估模型性能，且仅关注一个特定的数据集。同样，Saeed 等人（2022）[3] 提出了一种为云环境定制的机器学习 IDS，通过整合多种算法（如朴素贝叶斯分类器、决策树分类器、支持向量分类器、逻辑回归和 RF 分类器）来分析网络流量并检测异常。该研究强调实施机器学习技术可以降低误报并增强云基础设施中 IDS 的检测能力。而 Innab 等人（2024）[11] 展示了云环境中的不同安全攻击，评估了应对这些攻击的不同 IDS 类型和技术，将 IDS 分为基于签名、基于异常、基于混合和其他方法，并分析了它们在处理和检测安全事件方面的有效性。他们的研究指出，基于签名的攻击可以有效检测已知威胁，但无法检测未知威胁；基于异常的攻击以检测未知威胁而闻名，但误报率较高；而混合方法平衡了两者并提供了更高的检测准确率。尽管这项研究很全面，但缺乏任何实际实现来展示研究结果。

#### 5.2.2 IoT 设备

在 Munshi 等人（2020）[12] 的研究中，作者解释了 IoT 设备对 DDoS 攻击日益增长的敏感性，以及 IoT 网络扩展所带来的严重安全风险。该论文概述了集成 IoT 设备如何提高设备的可用性和功能，而这些

攻击者所应对的新型威胁和风险。它强调了基础性风险，例如识别和识别设备交互协议的方法不当或无效，这使得 IoT 设备在 DDoS 攻击期间面临着与其他接入设备同等水平的风险。反，为了解决这些问题，作者建议通过改进身份验证机制、安全协议和网络监控来构建和增强安全性，以便能够识别并实时中和攻击。这项工作对于 IoT 场景下的威胁研究具有特别的相关性，同时强调了使用动态方法应对 DDoS 攻击风险的重要性。此外，这些发现与本研究的目标相匹配，并为考虑基于 IoT 的系统的 DDoS 威胁向量和设计检测方法提供了理论背景。

#### 5.2.3 DDoS 检测机制

针对 DDoS 检测的广泛研究表明，已经有多种使用 SIEM 和机器学习（ML）技术来应对这种日益复杂的攻击的方法。Cakmakçı 等人（2021）[13] 提出了一个通过 SIEM 检测各种类型 DDoS 攻击的框架。它包含了 SIEM 内部的事件检测引擎，用于识别攻击模式。它还拥有一个推理引擎，可以在检测后自动建议响应和恢复步骤，从而缩短对正在进行的攻击的反应时间。未来对该框架的研究可以在多样化的网络环境中测试时，增强该系统的检测能力 [13]。使用极端梯度提升（XGBoost）对基于聚类的局部离群因子（LOF）进行特征工程进行补充，用于检测 DDoS 攻击。该模型在 CIC-IDS 2017 和 CIC-IDS 2018 上进行了实现和测试，实现了 99.99% 的准确率和 100% 的精确率。然而，其有效性尚未在动态环境中得到测试。同样，Chen 等人（2018）[15] 使用 XGBoost 算法检测软件定义云环境中的 DDoS 攻击。提出的模型在检测正常和恶意流量方面具有高水平，，证明了使用 XGBoost 的有效性。它还表明 XGBoost 能够有效处理动态云环境中的大量数据。探索具有不同流量和攻击类型的真实世界噪声数据的影响，将真正测试本研究所缺乏的性能。总而言之，这些研究突显了 SIEM 和高级机器学习模型（尤其是 XGBoost）在提高 DDoS 检测方面的效率。

### 表 5.1 现有技术发现

| 方面 | 发现 | 识别出的差距 | 研究贡献 |
|---|---|---|---|
| SIEM 和 IDS | SIEM 被认为是事件管理的关键组件，而 IDS 提高了检测率。 | 机器学习模型与 SIEM 和 IDS 的集成不足，不足以创建新的混合系统。 | 将机器学习模型与 SIEM 和 IDS 结合，以提高整体检测率。 |
| DDoS 检测 | 从机器学习模型（RF 和 XGBoost）获得的结果在识别 DDoS 攻击方面具有更高的准确率。 | 模型未在真实动态数据上进行测试，因此扩展性受到质疑。 | 设计了一个用于云环境中 DDoS 检测机器学习模型进行实时评估的框架。 |
| 循环出现的差距 | 缺乏实时实验，且基于规则的预测与基于机器学习的方法结合不充分。 | 在实时条件下对混合系统中的结果评估不足。 | 提出了一种在实时云设置中集成基于规则和基于机器学习的预测的系统，并评估其有效性和扩展性。 |

### 5.2.4 总结

本节探讨了针对 SIEM、IDS 和高级机器学习技术在各种环境（尤其是云环境）中检测包括 DDoS 在内的不同攻击的现有研究。表 5.1 简要列出了其他发现的总结，同时提出了本研究可以提供的解决方案。

### 5.3 研究方法论

本研究采用实验和定量的方法论设计，其中对攻击的受控模拟、使用 SIEM 和 IDS 进行监控和分析反映了实验方面，而收集的日志的数值性质以及使用机器学习模型和评估指标对其进行分析则类似于定量方面。所设计的系统同时使用了基于规则和基于机器学习的检测技术，以识别和分析 DDoS 攻击。该方法论被结构化并分为以下标准研究类别。

设计了一个由三个主要部分组成的实验方法——模拟攻击、监控网络活动和检测机制——以有效回答所述的研究问题。

第一部分包括对 DDoS 攻击的模拟。攻击通过 Amazon Web Services (`AWS`) `EC2` 实例上的攻击设置启动，模拟设计的设计旨在反映真实世界的威胁场景。DDoS 攻击专门针对托管在 `EC2` 实例上的 IoT 服务器，使用来自攻击机制中 `docker` 服务的 `hping3` 命令生成了海量流量。这台服务器是用于 MQTT 代理上构建 IoT 设备的同一台服务器。攻击模拟步骤经过设计和实施，以便在 IDS 上生成并捕获大量的网络活动日志。

如前所述，第二部分是实时监控云环境中的所有活动。对于开源 IDS `Suricata`，它被部署在与 IoT 服务器相同的虚拟私有云 (`VPC`) 中的 `EC2` 实例上，通过 `AWS` 上的流量镜像确保 IDS 能够捕获设计中描述流量的所有日志。IDS 包含了所有新兴的威胁规则，确保 IDS 是最新的。为了确保 IDS 能够检测设计中的流量，涵盖了所有新兴威胁规则。`Filebeat` 也在同一实例上进行了安装和配置，以将日志发送到 `ELK`（`Elasticsearch`, `Logstash` 和 `Kibana`），这确保了 SIEM 收到的日志是经过处理的。

## 表 5.2 元数据

| 捕获字段 | 理由 |
|--- | --- |
| 源 IP (`src_ip`) | 网络流量的源头 |
| 目的 IP (`dest_ip`) | 目标系统或服务 |
| 源端口 (`src_port`) | 与源应用程序关联的端口 |
| 目的端口 (`dest_port`) | 目标攻击的服务，TCP/IP(端口 1883) 预留给 MQTT 使用 |
| 协议 | 使用的网络协议（例如 TCP 和 UDP）。 |
| 时间戳 | 记录活动的精确时间 |
| 事件类型 (`event_type`) | 分类网络活动的性质，是告警、流还是正常 |
