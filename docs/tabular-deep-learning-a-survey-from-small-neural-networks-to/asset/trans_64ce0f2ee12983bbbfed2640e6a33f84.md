

## 早期融合

## 混合或中间融合

## 晚期融合

![](img/0cec9fcef02c2a21e786b62cd9d2c596_46_0.png)

图 17：多模态数据策略整合

当两个变量显示相同趋势时，它们具有相关性。相比之下，当存在因果关系时，即可理解因果关系，后者至少依赖于前者。相关性并不意味着因果关系，因果推断是关于效应发生条件的导出因果关系的过程 [372]。因果推断过程之所以复杂，是因为某些非可能的情况也可能是因果性的。考虑一个目标变量时，可能存在潜在变量（原因）和依赖变量（结果），它们通常被称为混杂因素（如果我们想衡量运动对减轻体重的影响，饮食就是一个潜在的混杂因素）。我们的想法是比较已经发生的情况与在其他情况下会发生的情况，或者进行反事实思考（对于患者，本该接受什么治疗？）。在医学中，使用随机对照试验来建立因果关系。我们必须能够确认原因（例如新药）确实是原因（在减轻症状方面）。因果 ML 试图在无法进行随机试验的地方寻找关联。因果 ML 尝试回答这些问题：如果我们改变特征会发生什么？观察到的效应是什么？如果情况不同会发生什么（反事实结果）。因果 ML 面临着若干挑战，例如收集偏偏（观测不是随机的）、隐藏混杂因素（某些混杂因素可能无法测量）、泛化问题和计算成本（ML 通常需要大型数据集）。在任何情况下，因果 ML 在医疗保健、营销、金融领域中都具有相关性，因果树 [11] 是因果 ML 的示例，侧重于将数据划分为子组以更准确地估计治疗效果（决策树最小化误差）。在深度学习方面，有一些示例，如因果感知的非对称自动编码器 CAT-MIWAE 更具可解释性，并且在 MCAR 和 MAR 机制下表现更好。Miracle [18] 是另一种用于插值的方法，这些策略不仅使用变量进行插值，还尝试推导出变量之间的因果链路。因果结构学习 (CASTLE) [19] 学习最优因果结构并尝试在主任务（例如分类）中执行。贝叶斯网络 [23] 是一种用于表示变量之间依赖关系的神经网络，这种依赖关系通过条件概率表示。因果学习是一个有趣的视角，允许我们了解因果 ML 和表格数据中仍然开放的一些问题：当数据集规模较小时，我们如何高效地进行选择和计算？如何可靠地识别和调整混杂因素？如何将这些方法整合到 ML 流水线以保持性能，特别是在医疗保健等高风险领域？对于表格数据，我们该如何设计保护措施（例如不确定性量化、置信区间、专家验证）以确保决策的可靠性？

- DNF: 析取范式
- FFNN: 前馈神经网络
- FL: 联邦学习
- GAN: 生成对抗网络
- GAN: 图注意力网络
- GNN: 图神经网络
- GBDT: 梯度提升决策树
- GNN: 图神经网络
- KAN: Kolmogorov-Arnold 神经网络
- KNN: K-近邻算法
- LLM: 大语言模型
- LOO: 留一法
- LM: 掩码语言建模
- MLP: 多层感知器
- MoE: 专家混合
- RAT: 检索增强生成
- RNN: 循环神经网络
- SAINT: 自注意力与交叉注意力
- VAE: 变分自动编码器

# 14. 结论

表格数据在现实应用（金融、医疗保健、网络安全、电子商务）中占据主导地位。然而，这是神经网络模型尚未超越传统机器学习的最后一个领域。这源于许多设计获胜架构的挑战。毫无疑问，与计算机视觉不同，表格数据很难处理。此外，跨数据集的大规模预处理技术是最有趣的领域之一。与此同时，由于这些数据集来自敏感领域，人们对可解释性有浓厚兴趣。此外，表格数据的无监督和半监督学习仍然不足，为该领域的未来更新提供了前景方向。因此，表格领域仍在进化，仍有改进和研究的空间。一些开放问题仍然，例如更好的归纳偏差、效率和可解释性，这些未来研究引人关注的问题。

# 参考文献

- [1] Abmedaged, N., 2020. 将数据集转换为知识谱. European Semantic Web Conference, pp. 217–224. Springer.
- [2] Ahmad, N., Lin, H., Washensky, A., Lin, S., & King, S. T., 2022. 擅长表格数据：基于 transformer 的患者预测系统. IEEE International Conference, pp. 1623–1630.
- [3] Abraham, A., Rahman, F., Kaur, D., 2022. 表格数据：用自然语言查询数据. https://arxiv.org/abs/2212.05648
- [4] Agrawal, C., L., Krishna, S., Saxena, E., Palewicz, M., Jain, P., & Vennik, M., 2021. OpenTab: 用于自动评估表格解释的 transformer 框架. https://arxiv.org/abs/2206.11104
- [5] Ahmed, M.A., Cheng, Q., 2024. Tabula: 用于表格数据的即插即用学习模型. https://arxiv.org/abs/2305.20897
- [6] Ala, A.M., Bertweij, B., van Leeuwen, S., Fevors, J., Drikker, R. C., Coulas, O., & Mittal, F., 2022. 你的合成数据样本忠实吗？评估和学习合成表格数据的综述. https://arxiv.org/abs/2102.08921
- [7] Ab, S., Wang, J., & Wei, Q., 2021. 一种基于 k-means 的数据插值算法方法. 2021 IEEE International Conference on Data Mining, Security and Privacy Applications, pp. 882–887.
- [8] Arik, S., Pisch, T., 2020. 表格数据：注意的可解释性学习. https://arxiv.org/abs/1908.0742
- [9] Armano, K., Jang, J., Fischer, M., Küstner, T., Hepp, N., Nikolopoulos, K., Geis, S., & Yang, Y., 2020. Medgan: 使用 gans 的医学图像翻译. 79, 10184.

# 15. 缩写

- AE: 编码器
- Boosting: 提升算法
- BN: 归一化
- CNN: 卷积神经网络
- CoT: 思维链
- DAG: 有向无环图
- DL: 深度学习

## 问题

## 描述

### 我们什么时候使用 GDBTs 还是 DL?

DL 方法在许多数据集上借用了视觉领域的偏差。然而，对于表格数据，我们没有相应的对应物。

与 NLP 或 CV 不同，表格数据集缺乏共享结构，特征工程是基础，这使得跨领域变得困难。

我们可以使用合成数据来训练模型吗？

合成数据没有覆盖特定领域的数据，导致了模型偏移。

数据增强在 CV 和 NLP 中取得了突破，但在表格数据中由于特征稀缺是局限的。

我们可以开发反映现实世界挑战的基准吗？

我们可以可靠地识别和调整现实世界数据集中的混杂因素，特别是在医疗保健等高风险领域？在保持性能的同时，我们如何将这些方法整合到 ML 流水线？在表格中使用模型的风险是什么？我们该如何设计保护措施（例如不确定性量化、置信区间、专家验证）以确保决策的可靠性？

![](img/0cec9fcef02c2a21e786b62cd9d2c596_46_0.png)

- [11] Alley, S., Wang, X., 2019. 鲁棒性. https://arxiv.org/abs/1902.0769.
- [12] Azur, J.M., Stuart, E., 2021. 深度神经网络. Neural information systems, 31–49.
- [13] Ba, D., Frey, B., 2013. 自适应丢弃. https://arxiv.org/abs/1308.0528.
- [14] Baek, D., Liu, Y., 2021. 表格数据. https://arxiv.org/abs/2106.1192.
- [15] Bahn, D., Han, J., 2022. 深度学习. https://arxiv.org/abs/2205.1417.
- [16] Just, S., Wang, J., 2022. 深度学习. Neural information processing systems, 31, 1540–1551.
- [17] Basu, P., Ghosh, S., 2020. 深度学习. https://arxiv.org/abs/2010.0610.
- [18] Fiesmann, S., Daler, C., Schmidt, S., 2018. 深度学习. Journal of machine learning research, 19(1):1971–2025.
- [19] Bengio, N., Courville, A., and Weiss, K., 2018. 理解批归一化. In Neural information processing systems, 31.
- [20] Just, S., Wang, J., 2020. 深度学习. https://arxiv.org/abs/2011.0567.
- [21] Boymasani, R., Hasson, D.A., 2022. https://arxiv.org/abs/2212.0781.
- [22] Zagor, O., Rart, S., 2020. 特征表示. Natural intelligence, 11(1):1–23.
- [23] Beauchamp, J., Rives, L.P., 2009. 支持向量机中的离群值处理. Journal of machine learning research, 10:247–279.
- [24] Bekker, A., Goldberg, J., 2016. 在无监督学习上训练深度神经网络. In 2016 IEEE International Conference on Acoustics Speech and Signal Processing (ICASAS), pp. 2660–2664.
- [25] Bereka, L., Gaves, E.,2022. 安全审计的可解释性. https://arxiv.org/abs/2204.1649.
- [26] Bersisha, V., Krastasevic, H., Hahn, P.H., Saharna, D., Turugan, G., 2021. 表格数据的深度学习：综述. Data Mining and Knowledge Discovery, 24(4):691–728.

