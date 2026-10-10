
## 表 9.4：各研究用于 Deepfake 检测的性能指标

| 年份 | 引用 | 数据集 | 测试集 | 指标 (AUC%) |
| :--- | :--- | :--- | :--- | :--- |
| 2022 | [56] | FF++ (c40), FF++ (c23) | Celeb-df, Celeb-df | 82.37, 83.28 |
| 2022 | [61] | FF++ | Celeb-DF | 66 |
| 2023 | [64] | FF++ | Celeb-DF | 72.30 |
| 2023 | [65] | FF++ c40, FF++ c40 | Celeb-DF, DFDC | 83.58, 71.53 |
| 2023 | [66] | Self-generated dataset | Self-collected dataset | 82.33 |
| 2023 | [67] | FF++ DF (c23), FF++ DF (c40) | Celeb-DF, Celeb-DF | 86.24, 86.84 |
| 2023 | [68] | FF++ | Celeb-DF | 72.43 |
| | | FF++ | DFDC | 73.68 |

**表 9.4** 各研究用于 Deepfake 检测的性能指标[⏎](#ch19.xhtml#t37b)

## 表 9.5：Deepfake 检测评估指标定义

| 指标 | 定义 |
| :--- | :--- |
| **Accuracy (ACC)** | 准确率是所有预测中正确预测总数的度量。`ACC = (TN + TP) / (TP + FP + TN + FN)` |
| **ROC curve** | 接收者操作特征曲线（ROC 曲线）是一种图形化绘图，通过在不同阈值下展示真正例率（TPR）与假正例率（FPR）之间的权衡，以图形方式表示性能，并将信号与噪声分离。 |
| **Area Under Curve (AUC)** | AUC 代表 ROC 曲线下的面积。AUC 越大，模型性能越好。如果 AUC 等于 1，分类器能够完美区分所有正例和负例。 |
| **Precision** | 精确率是指模型正确正例预测占所有正例预测的比例。`Precision = TP / (TP + FP)` |
| **Recall** | 召回率，也称为灵敏度，提供所有实际正例中正确正例预测比例的度量。`Recall = TP / (TP + FN)` |
| **F1 score** | F1 分数衡量精确率和召回率的调和平均数，以提供模型的综合评估。`F1 = 2 * Recall * Precision / (Recall + Precision)` |
| **log loss** | 对数损失评估分类模型的性能，是用于分类的重要指标。 |
| **Error Rate** | 错误率通过提供分类模型预测错误的实例数量来评估性能。`Error Rate = (FP + FN) / (TP + TN + FP + FN)` |
| **MCC** | 马修斯相关系数（MCC）提供一个单一值来汇总混淆矩阵。 |

为了评估各种方法的性能，[表 9.5](#ch19.xhtml#t37) 展示了用于 Deepfake 检测方法评估的各种指标。观察发现，最常用的指标是准确率、接收者操作特征（ROC）曲线和 AUC。虽然错误率、召回率和 F1 分数在 Deepfake 检测方法中相对不太流行，但准确率和 AUC 是用于性能评估的最流行指标。

## 9.4 新兴挑战与开放性问题

随着 Deepfake 的兴起，Deepfake 检测方法面临着新的挑战。这些挑战可总结如下：

*   **制作篡改媒体的成本降低**：深度学习使得任何人都能在更短的时间和精力内进行操纵，从而降低了制作篡改媒体的成本；这与早期需要个人熟练掌握某种图像处理工具才能创建逼真的变形图像的情况形成对比。
*   **强大的 Deepfake 生成方法持续演进**：新方法不断涌现，如变分自编码器（VAEs）[[69]](#ch19.xhtml#r341) 和扩散模型[[22]](#ch19.xhtml#r294)，它们能创建非常逼真的篡改媒体。
*   **设备计算能力增强**：设备计算能力的提升以及 GPU 等强大硬件的易得性，促进了超逼真 Deepfake 的生成。
*   **Deepfake 生成源代码和应用公开可用**：任何人只需接入互联网即可轻松生成 Deepfake。

## 9.5 评估指标

### 9.5.1 开放性问题

除了新兴挑战外，还有若干开放性问题需要未来研究者在 Deepfake 检测领域予以关注。

*   **计算成本高昂**：大多数现有方法需要高计算量和大量时间来执行 Deepfake 检测。这阻碍了实时数据上的 Deepfake 检测。这一差距需要未来研究者通过开发计算量更小、耗时更少的检测方法来解决。
*   **缺乏泛化性好的方法**：对各种现有方法的分析显示，需要提高检测方法的泛化能力，并改善在后处理视频中的性能，这需要工业界和学术界研究者立即关注，开发能够以高效率、鲁棒性和可靠性检测 Deepfake 的工具和技术，从而为公众提供辨别真伪的方法，对抗虚假信息。
*   **需要平衡的高质量数据集**：大多数现有 Deepfake 数据集不平衡，且随着 Deepfake 新变体的持续涌现和演进，需要一个包含使用多样化操纵方法和扰动方法创建的真实与伪造数据的平衡数据集。

## 9.6 结论

在本综述中，我们详细调查了 Deepfake 从其起源和生成过程到多年来开发的各种 Deepfake 检测方法。我们发现 Deepfake 的生成过程在持续演变，过去几年互联网上 Deepfake 传播急剧增加。FF++ 是最流行的 Deepfake 数据集，已被大多数 Deepfake 检测方法使用，准确率是最流行的评估指标。我们还观察到，基于 CNN 的方法是用于 Deepfake 检测的最广泛使用的技术。

随着互联网上 Deepfake 传播的快速增加和 Deepfake 生成过程的持续演变，Deepfake 检测方法仍面临各种挑战，需要研究者给予更多关注。本文涵盖了与 Deepfake 相关的广泛主题，如 Deepfake 类别、可用于 Deepfake 检测方法训练和测试的互联网数据集、各种现有 Deepfake 检测方法以及与 Deepfake 相关的威胁和挑战等，旨在作为宝贵的资源，希望能帮助研究者开发有效的 Deepfake 检测方法。

## 参考文献

*   [1] “‘Deepfakes’ ranked as most serious AI crime threat,” *ScienceDaily*, Aug. 20, 2020. Available: [www.sciencedaily.com/releases/2020/08/200804085908.htm](http://www.sciencedaily.com/releases/2020/08/200804085908.htm)[⏎](#ch19.xhtml#r273b)
*   [2] Sumsub, “Deepfake cases surge in countries holding 2024 elections, Sumsub research shows,” *Sumsub*, Jun. 5, 2024. [Online]. Available: [https://sumsub.com/newsroom/deepfake-cases-surge-in-countries-holding-2024-elections-sumsub-research-shows/](https://sumsub.com/newsroom/deepfake-cases-surge-in-countries-holding-2024-elections-sumsub-research-shows/)[⏎](#ch19.xhtml#r274b)
*   [3] A. Rossler, D. Cozzolino, L. Verdoliva, C. Riess, J. Thies, and M. Nießner, “Faceforensics++: Learning to detect manipulated facial images,” in *Proceedings of the IEEE/CVF International Conference on Computer Vision*, pp. 1–11, 2019.[⏎](#ch19.xhtml#r275b)
*   [4] T. Karras, T. Aila, S. Laine, and J. Lehtinen, “Progressive growing of gans for improved quality, stability, and variation,” *arXiv preprint arXiv:1710.10196*.[⏎](#ch19.xhtml#r276b)
