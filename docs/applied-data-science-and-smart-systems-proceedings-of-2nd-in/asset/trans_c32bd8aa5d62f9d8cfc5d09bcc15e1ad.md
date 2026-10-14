
-   [为了有效处理患者数据，需要建立链与基于 RPM 的 EHR 系统需求之间的关联。所有医疗中心均作为实体存在于 fabric 网络之中。患者数据被视为存储在账本中的有价值资源。当前，患者记录仅包含有限的类别，涵盖个人和医疗信息，如年龄、居住地、过敏、症状、治疗、随访等。当医生为患者给药时，他们将能够查看患者的病历数据，这有助于他们确定最合适的医疗方案。[Figure 21.2](#ch21.xhtml#fig21_2) 说明了系统架构。

![Figure 21.2 System architecture for hyperledger fabric](images/fig21_2_C.jpg)

[Figure 21.2 System architecture for hyperledger fabric](#ch21.xhtml#R_fig21_2)

-   医疗数据库用于在所提议系统中建立交易存储库。orderer 与 peer 节点在 Docker 容器中执行。Hyperledger Fabric 框架设计为最少配置两个组织——hospital1 和 hospital2。每个组织将被分配到一个单独的 peer 节点、一个通道以及 ordering 服务中的 orderer 节点。网络中每个 peer 节点都拥有账本的副本。链码（chaincode）旨在为网络中的两个组织提供访问。使用 Java 语言编写链码。[Figure 21.3](#ch21.xhtml#fig21_3) 是 minifab 使用的 network spec.yaml 文件的截图，它是网络配置文件。[Table 21.1](#ch21.xhtml#tab21_1) 描述了使用 minifab 创建网络的步骤。

| 步骤 | 命令 | 描述 |
| --- | --- | --- |
| 1 | minifab netup -s couchdb -e true -i 2.4.8 -o hospital1. health.com | 通过添加 hospital1. health.com 作为当前组织来启动网络 |
| 2 | minifab create -c healthchannel | 创建名为 healthchannel 的通道 |
| 3 | minifab join -c healthchannel | 网络加入 healthchannel |
| 4 | minifab anchorupdate | 更新锚点节点 |
| 5 | minifab profilegen -c healthchannel | 为 healthchannel 生成配置文件 |

-   网络成功构建后，链码在 health channel 上部署。已为 admin、patient 和 doctor 实体创建了一个链码。链码本质上是智能合约的集合。创建块使用 invoke 命令，查询使用 evaluation 命令。admin、patient 和 doctor 智能合约的功能在[Figure 21.4](#ch21.xhtml#fig21_4) 中展示。

![Figure 21.4 Smart contracts for entities](images/fig21_4_C.jpg)

[Figure 21.4 Smart contracts for entities](#ch21.xhtml#R_fig21_4)

-   医疗信息极其敏感，必须得到保护。只有患者授权的医疗提供者和机构才能访问其医疗记录。私有数据集（private data collections）是 Hyperledger Fabric 中存储敏感信息的选项。部分患者信息必须免受其他医疗机构的调查人员查看。[Figure 21.4](#ch21.xhtml#fig21_4) 展示了 admin 智能合约创建新患者的调用命令。这里添加的患者数据保持私有。[Figure 21.5](#ch21.xhtml#fig21_5)、[Figure 21.6](#ch21.xhtml#fig21_6) 和 [Figure 21.7](#ch21.xhtml#fig21_7) 描述了读取患者私有数据的查询命令和输出。

![Figure 21.5 Screenshot for creating a patient](images/fig21_5_C.jpg)

[Figure 21.5 Screenshot for creating a patient](#ch21.xhtml#R_fig21_5)

![Figure 21.6 Screenshot for query a patient](images/fig21_6_C.jpg)

[Figure 21.6 Screenshot for query a patient](#ch21.xhtml#R_fig21_6)

![Figure 21.7 Result for query a patient](images/fig21_7_C.jpg)

[Figure 21.7 Result for query a patient](#ch21.xhtml#R_fig21_7)

## 结果

Hyperledger Explorer 是一个设计用于提供用户友好界面以查看、分析和交互 Hyperledger Fabric 网络中的区块链数据的工具。Minifab 网络使用 Hyperledger Explorer 工具进行评估，该工具是开源工具。[Figure 21.8](#ch21.xhtml#fig21_8)(a) 和 (b) 展示了每分钟创建的块总数以及各组织创建的块数。它提供了完整的块信息，如数据哈希、前一个哈希、块哈希、事务数量、通道名称。共有 9 个块为 9 笔交易、2 个节点创建。

![Figure 21.8 (a) Blocks per min, (b) Transactions per organization](images/fig21_8_C.jpg)

[Figure 21.8 (a) Blocks per min, (b) Transactions per organization](#ch21.xhtml#R_fig21_8)

## 结论

本系统性方法实现 Hyperledger Fabric 用于远程患者监护，解决了医疗领域的关键挑战，即数据管理和安全。区块链技术在医疗领域的部署前景光明，能够提升数据完整性、隐私性和互操作性。

在整个研究过程中，我们阐述了全面的实施框架，包括智能合约和数据管理策略，以促进安全高效的远程患者监护。随着医疗行业的持续演变和数字化转型，将 Hyperledger Fabric 用于远程患者监护有望通过实现医疗提供者之间的实时数据共享、确保数据准确性以及保护患者隐私，彻底改变患者护理方式。然而，仍存在可扩展性问题以及广泛采用的需求。

未来，进一步的研究和实际实施应探索可扩展性解决方案，并持续与医疗生态系统中的利益相关者进行互动，以克服采用障碍。

## 参考文献

*   [Dabbagh, M., Mohsen, K., Mohammad, T., and Angela, A.](#ch21.xhtml#R_ref21_1) (2020). Performance analysis of blockchain platforms: Empirical evaluation of hyperledger fabric and ethereum. 2020IEEE 2nd Int. Conf. Artif. Intel. Engg. Technol. (IICAIET), 1–6.

*   Garg, S., Rajesh Kumar, K., and Naveen, K. (2022). Blockchain-based electronic health record and open research challenges. 202210th Int. Conf. Reliabil. Infocom Technol. Optimiz. (Trends and Future Directions)(ICRITO), 1–5.

*   [Ichikawa, D., Kashiyama, M., and Ueno, T.](#ch21.xhtml#R_ref21_3) (2017). Tamperresistant mobile health using blockchain technology. JMIR mHealth and uHealth, 5(7), 1–11. [https://doi.org/10.2196/mhealth.7938](https://doi.org/10.2196/mhealth.7938).

*   [Jennath, H. S., Anoop, V. S., and Asharaf, S.](#ch21.xhtml#R_ref21_4) (2020). Blockchain for healthcare: Securing patient data and enabling trusted artificial intelligence. 15–23. [https://doi.org/10.9781/ijimai.2020.07.002](https://doi.org/10.9781/ijimai.2020.07.002).

*   [Kantorowska, Agata, Koral Cohen, Maxwell Oberlander, Anna R. Jaysing, Meredith B. Akerman, Anne-Marie Wise, Devin M. Mann et al.](#ch21.xhtml#R_ref21_5) (2023). Remote patient monitoring for management of diabetes mellitus in pregnancy is associated with improved maternal and neonatal outcomes. American Journal of Obstetrics and Gynecology. 228, 6 pp. 1-11.

*   [Kumar, A., Sharad, S., Nitin, G., Aman, S., Xiaochun, C., and Parminder, S.](#ch21.xhtml#R_ref21_6) (2021). Secure and energy-efficient smart building architecture with emerging technology IoT. Comp. Comm., 176, 207–217.
