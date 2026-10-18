
贝叶斯网络中的算法 [7]，计算了四个结果：

1. 对现场设备层进行 DoS 和 MitM 攻击的概率
2. 在网络中其他节点存在攻击证据的情况下，对现场设备层进行 DoS 和 MitM 攻击的概率
3. 在存在攻击证据且管理层未发生钓鱼和恶意软件注入攻击的情况下，对现场设备层进行 DoS 和 MitM 攻击的概率
4. 在现场设备层存在 DoS 和 MitM 攻击证据的情况下，最可能的解释

前三个结果分别展示在表 7.4、7.5 和 7.6 中。至于最可能的解释：如果有证据表明现场设备层发生了 DoS 攻击但未发生 MitM 攻击，或发生了 MitM 攻击但未发生 DoS 攻击，最可能的解释包括对管理层进行社会工程攻击，然后是对管理层进行钓鱼攻击，之后是对 KNX IP 路由器进行 DoS 攻击，最后是证据中出现的任何攻击。

**表 7.4.** 对现场设备层进行 DoS 和 MitM 攻击的概率

| 攻击 | 概率 |
|---|---|
| DOSF | 0.3257822 |
| MITMF | 0.2627260 |
| DOSF and MITMF | 0.1897563 |

**表 7.5.** 在网络中其他节点存在攻击证据的情况下对现场设备层进行 DoS 和 MitM 攻击的概率

| 攻击 | 证据 | 概率 |
|---|---|---|
| DOSF | SECP | 0.4134291 |
| MITMF | SECP | 0.3334087 |
| DOSF and MITMF | SECP | 0.2408075 |
| DOSF | PHCP | 0.6054472 |
| MITMF | PHCP | 0.4905264 |
| DOSF and MITMF | PHCP | 0.3567098 |
| DOSF | MICP | 0.6333557 |
| MITMF | MICP | 0.5179413 |
| DOSF and MITMF | MICP | 0.3813129 |
| DOSF | DOSR | 0.7190847 |
| MITMF | DOSR | 0.5931191 |
| DOSF and MITMF | DOSR | 0.4460161 |
| DOSF | RTPR | 0.7592573 |
| MITMF | RTPR | 0.6449062 |
| DOSF and MITMF | RTPR | 0.5024086 |
| DOSF | PAR | 0.7097519 |
| MITMF | PAR | 0.6507042 |
| DOSF and MITMF | PAR | 0.4829878 |

**表 7.6.** 在存在攻击证据且管理层未发生钓鱼和恶意软件注入攻击的情况下对现场设备层进行 DoS 和 MitM 攻击的概率

| 攻击 | 证据 1 | 证据 2 | 概率 |
|---|---|---|---|
| DOSF | No PHCP | MICP | 0.5625418 |
| MITMF | No PHCP | MICP | 0.4474423 |
| DOSF and MITMF | No PHCP | MICP | 0.3165204 |
| DOSF | PHCP | No MICP | 0.5468065 |
| MITMF | PHCP | No MICP | 0.4323725 |
| DOSF and MITMF | PHCP | No MICP | 0.3036255 |
| DOSF | PHCP | MICP | 0.7013511 |
| MITMF | PHCP | MICP | 0.5856344 |
| DOSF and MITMF | PHCP | MICP | 0.4435267 |

## 7.7 结论与未来工作

在本章中，使用贝叶斯网络实现了一个智能家居物联网网络的风险评估模型，其有向无环图来自 [4] 中提出的攻击图，其参数来自对通过仿真获得的数据集应用最大似然方法获得。本章中，使用贝叶斯网络实现了一个智能家居物联网网络的风险评估模型，其有向无环图来自 [4] 中提出的攻击图，其参数来自对通过仿真获得的数据集应用最大似然方法获得。表 7.4、7.5 和 7.6 提供了在智能家居网络存在或不存在其他攻击证据的情况下，对现场设备层进行不同攻击的概率。这些结果可供网络安全评估人员使用；例如，如果认为智能家居网络具有与模型中提出的类似的选择和漏洞概率，并且有证据表明管理层发生了钓鱼攻击，则现场设备层发生 DoS 攻击的概率为 60.54%，发生 MitM 攻击的概率为 49.05%。因此，一个可行的选择是采取行动保护设备免受 DoS 攻击。使用表 7.6，如果有证据表明管理层还发生了恶意软件注入攻击，则 DoS 攻击的概率上升到 70.15%，使防止 DoS 攻击变得紧迫。使用该方法论的优势在于它允许对这些概率进行量化，这对决策很有用。

通过贝叶斯推理，可以以更高的细节水平获得有关不同事件的新信息，因为对现象的了解会随着证据而更新。在风险评估中，这些证据可以是观察到的或假设的，在第二种情况下，可以了解在不同情况下会发生什么，并且基于此分析可以做出更好的决策。贝叶斯网络模型的主要优点之一是它考虑了随机变量的条件依赖性。

在本章中，风险评估包括查找网络上不同网络攻击事件的概率。这种类型的分析在决策基于概率的情况下很有用。未来的工作将侧重于根据评估者的需求为风险评估添加更多细节。例如，可以包括网络攻击的影响，既可以由评估者创建的分数形式，也可以与网络攻击造成的财务损失相关，并且这种财务损失可以集中在信息丢失或服务中断上。

本章包括对智能家居结构进行的总体分析。未来的工作可以包括对特定智能家居的研究，详细说明每个设备及其自身特征。为此，必须指定新的选择概率和用于模拟攻击的漏洞概率的 CVSS 分数。然而，理想的情况是使用提供的数据集，以获得对智能家居状况的更现实分析。有了真实案例的数据集，将遵循本工作的相同程序，只是攻击的模拟除外。

应该提到的是，由于攻击图的使用并不仅限于智能家居，因此该分析可以扩展到不同类型的物联网网络。一个有趣的研究可能集中在智慧城市上，这是目前蓬勃发展的技术，因此在这些环境中研究网络安全是人们和网络安全评估人员迫切需要的。

## 参考文献

1. Poolsappasit, N., Dewri, R., and Ray, I. “使用贝叶斯攻击图进行动态安全风险管理”. *IEEE Transactions on Dependable and Secure Computing*, 9(1):61–74, 2012.
2. H. Rajab and T. Cinkler. “基于物联网的智慧城市”. In *2018 International Symposium on Networks, Computers and Communications (ISNCC)*. IEEE, 2018.
3. D. Bastos, M. Shackleton, and F. El-Moussa. “物联网：智能家居和城市环境中的技术与安全风险综述”. In *Living in the Internet of Things: Cybersecurity of the IoT – 2018*. Institution of Engineering and Technology, 2018. DOI:10.1049/CP.2018.0030
4. M. Ibrahim and I. Nabulsi. “应用攻击图对智能家居系统进行安全分析”. In *2021 Fifth World Conference on Smart Trends in Systems Security and Sustainability (WorldS4)*. IEEE, 2021.
5. Koller, D. and Friedman, N. “概率图模型：原理与技术”. *Adaptive Computation and Machine Learning series*. MIT Press, 2009.
6. A. Darwiche. *使用贝叶斯网络进行建模与推理*. Cambridge University Press, 2009.
7. Scutari, M. and Denis, J.-B. (2014). *使用 R 的贝叶斯网络*. Chapman and Hall/CRC.
8. Liu, Y. and Man, H. “使用贝叶斯网络进行网络漏洞评估”. In Dasarathy, B. V., editor, *Data Mining, Intrusion Detection, Information Assurance, and Data Networks Security 2005*, volume 5812, pp. 61–71. International Society for Optics and Photonics, SPIE, 2005.
9. 通用漏洞评分系统版本 3.1 规范文档. [Online] www.first.org/cvss/v3.1/specification-document
10. S. Rizvi, N. McIntyre and J. Ryoo, “计算物联网设备漏洞的安全分数,” *2019 International Conference on Software Security and Assurance (ICSSA)*, 2019, pp. 52–59.
11. Frigault, M., Wang, L., Singhal, A., and Jajodia, S. “使用动态贝叶斯网络衡量网络安全”. In *Proceedings of the 4th ACM Workshop on Quality of Protection*, QoP ‘08, pp. 23–30, New York, NY, USA, 2008. Association for Computing Machinery.
12. Muñoz-González, L., Sgandurra, D., Barrère, M., and Lupu, E. C. “贝叶斯攻击图分析的精确推理技术”. *IEEE Transactions on Dependable and Secure Computing*, 16(2):231–244, 2019.
13. Zeng, J., Wu, S., Chen, Y., Zeng, R., and Wu, C. “从数据和知识处理的角度对攻击图分析方法进行综述”. *Security and Communication Networks*, 2019:1–16, 2019.
