

![图 6. 一个通信多智能体系统，展示了反应性和反思性行为。](images/fig2_6_B.jpg)

[图 6. 一个通信多智能体系统，展示了反应性和反思性行为。](#ch2.xhtml#R_fig2_6)

智能体的表示包含一个 `ANN`（左上部分），它提供可能的下一步移动信息（反应性行为）。此外，右上角的符号代表反思性行为的逻辑，即对替代移动进行推理。包含的圆圈代表智能体的生命代码，在该代码下观察当前内部状态，并产生下一个内部状态。

表示反思性行为的方法主要受 `ACT-R` 启发。`ACT-R` 是一种用于认知研究的概念架构，特别是针对人类行为的研究（[[108](#ch2.xhtml#ref2_108), [109](#ch2.xhtml#ref2_109), [110](#ch2.xhtml#ref2_110) 和 [111](#ch2.xhtml#ref2_111)])，但在此被泛化用于鸟类研究，甚至更广泛地用于智能体概念的研究。

### 8.2.1.2 局部

一方面，在局部层面，在 `FL` 的背景下，场景应该相当清晰。也就是说，每只鸟都在执行单独的 `ANN` 训练阶段，例如，根据[图 1](#ch2.xhtml#fig2_1)。尽管如此，鸟类的行为不仅仅由该步骤定义，还由我们提出并指出的 `反思性行为` 定义。此类动作可能更难泛化，因为它们更多地基于个体基础进行硬编码，而不是通过集成到 `FL` 动作中的 `ANN`。

### 8.2.1.3 全局

正如本章所述，`FL` 已达到一个成熟点，`FL` 的动作可以通过预开发的 `API` 实现自动化。因此，根据[图 1](#ch2.xhtml#fig2_1)，训练所有单个鸟类的 `ANN` 这一步骤应被视为完全可行。尽管如此，训练过程的聚合只能基于鸟类行为模式的 `ML` 部分，即 `反应性` 部分，而非反思性部分。我们作者将此问题视为未来研究的挑战和进一步研究的机会。同样，此示例的目的是在抽象层面上指出 `FL` 和智能体的概念。正在进行的生态研究将扩展到考察游泳和飞行之外的鸟类更多方面，目前的观点是，互补建模技术将更加重要，并为 `FL` 和智能体背景提供更多有趣的启发。

## 9. 总结

本章从两个视角探讨了 `联邦学习` 的概念，一方面是从基于经验的视角，另一方面是从阐述性的视角。基于经验的方法在此基于 `工业 4.0` 背景下的先前工作，更确切地说是采矿业及其机器人背景，其中数据融合和我们可以称之为“融合”分析的需求。`联邦学习` 配合数据标准和数据模型，显然能为该行业的发展做出贡献。带宽和数据处理受限的远程环境，面临各种数据分析挑战，可从 `联邦学习` 范式中受益。一方面由 `机器学习 (ML)` 支持的 `人工智能 (AI)`，另一方面由 `认知科学` 方法支持的面向基于传感器设备的 `AI`，二者可以在双重性中延伸人类能力并协助人类进行机器人操作。

本贡献的第二个视角着重于进一步指导和展示作为 `AI` 一部分的认知层面（除了 `ML` 之外）如何构建整体数据视图，并促进智能体固有的自主、自我感知行为。在此，已讨论了当前的 `联邦学习` 过程主要基于 `ML` 和 `人工神经网络`，且必须开展更多研究，以将数字设备的认知层面与此类 `联邦学习` 过程相集成。作者讨论了如何在中心聚合层面理解 `联邦学习` 和边缘设备上的本地数据模型，以免丢失关于何时融合不同数据以构建整体数据模型的局部或全局感知。

## 参考文献

1.  [VoxelNET 4D 数据集成平台 -CSIRO](#ch2.xhtml#R_ref2_1)。

2.  [Apheris -制造业中的协作数据生态系统](#ch2.xhtml#R_ref2_2)。[在线] 2022 [引用日期 2022 年 12 月 29 日]。可从以下网址获取：[https://www.apheris.com/resources/learning-hub/article/guide-to-collaborative-data-ecosystems](https://www.apheris.com)。

3.  [ISO -标准。[在线] 2022 [引用日期 2022 年 12 月 29 日]](#ch2.xhtml#R_ref2_3)。可从以下网址获取 [https://www.iso.org/standards.html](https://www.iso.org)。

4.  [Gregersen, E.](#ch2.xhtml#R_ref2_4) 2022. John MacCarthy -美国数学家和计算机科学家。[在线] 2022 [引用日期 2022 年 12 月 13 日]。可从以下网址获取：[https://www.britannica.com/biography/John-McCarthyEncyclopedia Britannica](https://www.britannica.com)。

5.  [MacCarthy, J.](#ch2.xhtml#R_ref2_5) 2022. What is AI? Basic Questions, [在线] [引用日期 2022 年 12 月 13 日]。可从以下网址获取：[http://jmc.stanford.edu/artificial-intelligence/what-is-ai/index.html](http://jmc.stanford.edu)。

6.  [WIKI (瑞典语)](#ch2.xhtml#R_ref2_6)：[https://sv.wikipedia.org/wiki/Artificiell_intelligens](https://www.sv.wikipedia.org)。

7.  [Jamil, S. and Rahman, M.](#ch2.xhtml#R_ref2_7) 2022. Fawad. 面向工业物联网 (IIoT)、车联网 (IoV) 和无人机物联网 (IoD) 的数字孪生与联邦学习综述。Appl. Syst. Innov., 5: 56。

8.  [什么是联邦学习？| IBM Research Blog [在线]](#ch2.xhtml#R_ref2_8) [引用日期 2022 年 11 月 23 日]。可从以下网址获取：[https://research.ibm.com/blog/what-is-federated-learning](https://research.ibm.com)。

9.  [免费云计算服务 -AWS Free Tier (amazn.com) [在线]](#ch2.xhtml#R_ref2_9) [引用日期 2022 年 11 月 23 日]。可从以下网址获取：[https://aws.amazon.com/free](https://aws.amazon.com)。

10.  [Frends iPaaS | iPaaS [在线]](#ch2.xhtml#R_ref2_10) [引用日期 2022 年 11 月 23 日]。[https://frends.com/landing/ipaas](https://frends.com)。

11.  [McMahan, H.B., Moore, E., Ramage, D., Hampson, S. and y Arcas, B.A.](#ch2.xhtml#R_ref2_11) 2017. Communication-efficient learning of deep networks from decentralized data. Proceedings of the 20th International Conference on Artificial Intelligence and Statistics (AISTATS). JMLR: W&CP volume 54. [https://doi.org/10.48550/arXiv.1602.05629](http://dx.doi.org/10.48550/arXiv.1602.05629)。

12.  [Han, B.](#ch2.xhtml#R_ref2_12) 2019 年 3 月 31 日. An Overview of Federated Learning, Published in Data Driven Investor. [https://medium.datadriveninvestor.com/an-overview-of-federatedlearning-8a1a62b0600d](https://medium.datadriveninvestor.com)。

13.  [Yang, Q., Liu, Y., Chen, T. and Tong, Y.](#ch2.xhtml#R_ref2_13) 2019 年 3 月. Federated Machine Learning: concept and applications. Published in Association for Computing Machinery, 10(2). ISSN:2157-6904. [https://dl-acm-org.ezproxy.hkr.se/doi/pdf/10.1145/3298981](https://dl-acm-org.ezproxy.hkr.se)。

14.  [Zec, E.L., Mogren, O., Martinsson, J., Sütfeld, L.R. and Gillblad, D.](#ch2.xhtml#R_ref2_14) 2020. Federated Learning using a Mixture of Experts. [https://arxiv.org/abs/2010.02056](https://arxiv.org)。

15.  [Konečný, J., McMahan, H.B., Ramage, D. and Richtárik, P.](#ch2.xhtml#R_ref2_15) 2016 年 10 月. Federated optimization: Distributed machine learning for on-device intelligence. [https://doi.org/10.48550/arXiv.1610.02527](http://dx.doi.org/10.48550/arXiv.1610.02527)。

16.  [世界上有多少智能手机？](#ch2.xhtml#R_ref2_16) (来源：[https://www.bankmycell.com/blog/how-many-phones-are-in-the-world)](https://www.bankmycell.com)。

