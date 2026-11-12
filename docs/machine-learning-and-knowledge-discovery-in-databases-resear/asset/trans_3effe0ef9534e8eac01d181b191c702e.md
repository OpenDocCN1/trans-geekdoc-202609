

## 6 结论

我们研究了在时序边流中计数时序三角形的问题。我们介绍了**STEP**，一种由预测器增强的采样算法，与最新方法相比，它在使用最少计算资源的同时提供高度准确的估计。据我们所知，**STEP**是使用预测进行时序三角形计数的_第一个算法_。实验结果表明，**STEP**比最新精确方法快得多，并且比近似最新流式算法需要的资源显著更少，通常能获得更准确的估计。最后，我们展示了如何高效计算一个简单的预测器，该预测器也可用于图的在线处理。

未来研究包括开发更先进的、依赖于领域的预测器（例如，学习特定的边权重用于分类在流中保留的重要边），并将**STEP**的方法扩展到其他时序图案[32,34]。

**致谢.** 这项研究由大学与研究部在国家互补计划 PNC-I.1“医疗和福利领域创新技术与路径研究计划”下资助。D.D. 931 of 06/06/2022, PNC0000002 DARE - Digital Lifelong Prevention CUP: B53C22006440001”以及 PRIN 项目 n. 2022TS4Y3N “EXPAND：异构动态网络数据探索性分析的可扩展算法”。这项研究还由 ERC 高级资助 REBOUND (834862) 和由 Knut and Alice Wallenberg 基金会资助的 Wallenberg AI、自主系统和软件计划 (WASP) 资助。

**利益披露.** 作者声明没有与本文内容相关的竞争利益需要披露。

## 参考文献

- 1. Azar, Y., Panigrahi, D., Touitou, N.: 带预测的在线图算法。SODA (2022)
- 2. Belth, C., Zheng, X., Koutra, D.: 持续演变网络中持久活动的挖掘。KDD (2020)
- 3. Bernardini, G., Lindermayr, A., Marchetti-Spaccamela, A., Megow, N., Stougie, L., Sweering, M.: 应用于在线图问题的输入预测的通用误差度量。NeurIPS (2022)
- 4. Boldin, C., Vandin, F.: 使用预测在图流中进行快速准确的三角形计数。ICDM (2024)
- 5. Boucheron, S., Lugosi, G., Bousquet, O.: 浓度不等式。Springer (2004)
- 6. Chen, J., Silwal, S., Vakilian, A., Zhang, F.: 通过学习预测加速基础图算法。ICML (2022)
- 7. Chen, J.Y., et al.: 图流中带预测的三角形和四元环计数。ICLR (2022)
- 8. Debrouvier, A., Parodi, E., Perazzo, M., Soliani, V., Vaisman, A.: 时序图数据库的模型和查询语言。VLDB 期刊 (2021)
- 9. Gao, Z., Cheng, C., Yu, Y., Cao, L., Huang, C., Dong, J.: 大规模时序图的可扩展图案计数。ICDE (2022)
- 10. Gionis, A., Oettershagen, L., Sarpe, I.: 时序网络挖掘。WWW (2024)
- 11. Heeg, F., Scholtes, I.: 使用因果感知图神经网络预测动态图中的时序中心性。NeurIPS (2024)
- 12. Hessel, J., Tan, C., Lee, L.: Science、AskScience 和 BadScience：关于高度相关社区共存的研究。ICWSM (2016)
- 13. Holme, P., Saramäki, J.: 时序网络。物理报告 (2012)
- 14. Holme, P., Saramäki, J.: 时序网络理论。Springer International 出版 (2023)
- 15. Jiang, S.H.C., Liu, E., Lyu, Y., Tang, Z.G., Zhang, Y.: 带预测的在线设施选址。ICLR (2022)
- 16. Kondor, D., Csabai, I., Szüle, J., Pósfai, M., Vattay, G.: 推断比特币中网络结构与市场效应之间的相互作用。新物理期刊 (2014)
- 17. Lattanzi, S., Ola, S., Sergei, V.: 通过最小违反排列加速 Bellman-Ford 算法。ICML (2023)
- 18. Li, J., Qi, J., Huang, Y., Cao, L., Yu, Y., Dong, J.: MoTTo：面向大规模时序图的带时间感知拓扑约束的可扩展图案计数。CIKM (2024)
- 19. Liu, L., et al.: QTCS：高效查询中心的时序社区搜索。PVLDB (2024)
- 20. Liu, P., Benson, A.R., Charikar, M.: 时序图案计数的采样方法。WSDM (2019)
- 21. Liu, P., Guarrasi, V., Sariyuce, A.E.: 时序网络图案：模型、局限性与评估。TKDE (2021)
- 22. Mackey, P., Porterfield, K., Fitzhenry, E., Choudhury, S., Chin, G.: 时序子图同构的基于时间顺序的边驱动方法。大数据 (2018)
- 23. Mang, Q., et al.: 通过图结构感知索引在大型时序双分网络中高效历史蝴蝶计数。arXiv (2024)
- 24. Matula, D.W., Beck, L.L.: 最小-最后排序、聚类和图着色算法。JACM (1983)
- 25. McGregor, A.: 图流算法：综述。SIGMOD (2014)
- 26. Mitzenmacher, M., Vassilvitskii, S.: 带预测的算法。CACM (2022)
- 27. Muthukrishnan, S., et al.: 数据流：算法与应用。载于：Found. Trends®. Theor. Comput. Sci. (2005)
- 28. Pan, Y., Bhalerao, O., Seshadhri, C., Talati, N.: 使用路径采样对时序图案进行准确快速的估计。ICDM (2024)
- 29. Paranjape, A., Benson, A.R., Leskovec, J.: 时序网络中的图案。WSDM (2017)
- 30. Pashanasangi, N., Seshadhri, C.: 基于退化序列的更快、更通用的时序三角形计数。KDD (2021)
- 31. Porter, A., Mirzasoleiman, B., Leskovec, J.: 时序网络中图案的分析模型。WWW (2022)
- 32. Pu, J., Wang, Y., Li, Y., Zhou, X.: 时序双分图上蝴蝶计数的采样算法。arXiv (2023)
- 33. Qin, H., Li, R.H., Yuan, Y., Wang, G., Qin, L., Zhang, Z.: 大规模时序图中的突发核心挖掘。PVLDB (2022)
- 34. Sarpe, I., Vandin, F.: Eden：大规模时序网络中多个图案计数的同时近似。CIKM (2021)
- 35. Sarpe, I., Vandin, F.: PRESTO：时序图案计数严格近似的简单可扩展采样技术。SDM (2021)
- 36. Sarpe, I., Vandin, F., Gionis, A.: 可扩展时序图案最密子网络发现。KDD (2024)
- 37. Seshadhri, C., Tirthapura, S.: 可扩展子图计数：疯狂背后的方法。WWW (2019)
- 38. Tang, J., Musolesi, M., Mascolo, C., Latora, V.: 社交网络分析的时序距离度量。SIGCOMM (2009)
- 39. Tu, K., Li, J., Towsley, D., Braines, D., Turner, L.D.: gl2vec：使用图形小图学习有向网络的特征表示。ASONAM (2019)
- 40. Venturin, G., Sarpe, I., Vandin, F.: 带预测的流式高效近似时序三角形计数（扩展版）。arXiv (2025)
- 41. Wang, J., Wang, Y., Jiang, W., Li, Y., Tan, K.L.: 时序图流中近似图案计数的高效采样算法。arXiv (2022)
- 42. Wang, P., Qi, Y., Sun, Y., Zhang, X., Tao, J., Guan, X.: 固定内存使用下包含边重复的大图流中近似三角形计数。PVLDB (2017)
- 43. Zhang, T., Fang, J., Yang, Z., Cao, B., Fan, J.: TATKC：一种用于快速近似时序 Katz 中心性排序的时序图神经网络。WWW (2024)

## 通过数据增强和动态中毒对图分类进行后门攻击

Yadong Wang$^1$, Zhiwei Zhang$^{1(\otimes)}$, Pengpeng Qiao$^2$, Ye Yuan$^1$,
和 Guoren Wang$^1$

$^1$ 北京理工大学, 北京, 中国
bit.wangyd@gmail.com, {zwzhang, yuan-ye}@bit.edu.cn, wanggrbit@126.com
$^2$ 科学东京研究所, 东京, 日本
peng2qiao@gmail.com

**摘要.** 图神经网络 (GNN) 在生物信息学、社交网络和化学信息学等领域已获得广泛应用，但它们仍然容易受到后门攻击。现有的后门攻击通常依赖于子图触发器，这往往会引入可检测的异常并采用随机毒化样本选择，导致隐蔽性和效率降低。为解决这些局限性，我们提出了一种新颖的后门攻击框架，该框架利用基于数据增强的触发器和动态毒化样本选择。具体而言，我们设计了三种替代的数据增强策略——由余弦相似度引导的边修改、基于度中心性的边移除以及通过梯度显著性进行的特征掩码——作为后门触发器。此外，我们引入了一种由遗忘事件告知的动态毒化样本选择方法。该方法动态地优先选择高影响的毒化样本，以增强攻击效率，同时减少达到相应攻击成功率 (ASR) 所需的样本数量。在 PROTEINS、NCI1、Mutagenicity 和 ENZYMES 四个基准数据集上的实验表明了我们方法的优越性。

**关键词.** GNNs · 图分类 · 后门攻击

## 1 引言

图分类已成为多个领域中的基本研究方向，特别是在生物信息学和药物发现 [17]、化学信息学 [11]、蛋白质-蛋白质交互网络 [10] 和社交网络分析 [5] 方面。随着 GNNs [1,2,9,14] 的快速发展，建模和处理图结构数据的能力已得到显著提升。通过捕获节点和边之间的高阶依赖关系，GNNs 在图分类任务中表现出卓越性能。然而，广泛

