
```
$a_k = \frac{exp(a_k)}{\sum_{i=1}^{l} exp(a_i)} \quad (18)$
```

其中 `$W_k$` 是用于指定输入特征表示 `$h_{k,j} = [\overrightarrow{h_{k,j}}, h_{k,j}]$` 的权重，`elu` 代表指数线性激活函数 [58]，其定义为：

```
$elu(x) = \begin{cases} a \cdot (exp(x) - 1) & \text{if } x < 0 \\ x & \text{if } x \geq 0 \end{cases} \quad (19)$
```

其中 `$a=1$`。每个自注意力权重表示了特定图像与视频序列中所表达的情绪状态的相关性。因此，相关图像计算出的权重值应显著高于无关图像。输入序列的最终表示是通过根据计算出的自注意力权重 `[a_k]_{k=1}^l` 对 BiLSTM 输出 `[h_{1,j}, h_{2,j}, \dots, h_{l,j}]` 进行加权聚合而得到的：

```
$h_j = \sum_{k=1}^{l} a_k \cdot h_{k,j} \quad (20)$
```

并进一步用于分类任务。

## 4. 实验

在后续节中，提供了用于评估所提方法的实验描述。简要描述了用于评估的数据集，随后是所进行的数据预处理步骤。随后还描述了实验设置以及执行的实验。本节最后对实验结果进行了描述和讨论。

所提方法在 BioVid Heat Pain Database (Part A) (BVVD) [4] 和 SenseEmotion Database (SEDB) [6] 上进行了评估。这两个数据集的设计目标都是促进脸识别领域的研究。事实上，若干健康参与者接受了一系列单独的热诱导疼痛刺激。BVVD 包含 87 名个体，他们接受四个逐渐增加的热诱导刺激（`T_1, T_2, T_3` 和 `T_4`）；SEDB 包含 40 名个体，他们接受三个逐渐增加的热诱导刺激（`T_1, T_2` 和 `T_3`）。每种热诱导疼痛刺激在 BVVD 中随机触发 20 次，在 SEDB 中随机触发 30 次。每次引发持续 4 秒，随后是 8 到 12 秒的恢复期，期间达到基准温度 `T_0` (`32^\circ C`)。BVVD 的引发仅在特定的手部进行，而 SEDB 的实验则进行了两次，在特定的手臂（左前臂和右前臂）上进行引发。因此，加上基准温度 `T_0`，数据集总共包含 `87 × 20 × 5 = 8700` 个样本，而 SEDB 包含 `40 × 30 × 4 = 4800` 个样本。在实验期间，每个参与者的神态都使用多种模态（视频和生物生理通道）进行记录，SEDB 则包含了音频、视频和生物生理通道。当前工作专门关注视频模态，读者可以参考文献 [10,14–16,33,59–64] 以获取更多关于其他模态的实验。

### 4.2. 数据预处理

当前工作专门关注视频模态，读者可以参考文献 [10,14–16,33,59–64] 以获取更多关于其他模态的实验。

### 4.3. 实验设置

当前工作专门关注视频模态，读者可以参考文献 [10,14–16,33,59–64] 以获取更多关于其他模态的实验。

## 表 2. 分类器架构。

| 层级 | 单元数量 |
| --- | --- |
| Dropout | -- |
| 全连接 | 64 |
| Dropout | -- |
| 全连接 | c |

Dropout 率根据经验设置为 0.25。第一个全连接层使用 `elu` 激活函数，而最后一个全连接层由一个 softmax 层组成（其中 `c` 表示分类任务的类别数）。

图 6 展示了针对输入通道的特定分类架构（MHIs 和 OFIs）的性能，以及加权评分聚合方法的性能。在这种情况下，性能衡量指标是准确率（Accuracy），其定义为：

```
$Accuracy = \frac{tp + tn}{tp + fp + tn + fn}$ (22)
```

其中，`tp` 指真阳性（true positives），`tn` 指真阴性（true negatives），`fp` 指假阳性（false positives），`fn` 指假阴性（false negatives）（因为处理的是具有两个平衡数据集的二分类任务）。对于两个数据集和分类任务，聚合方法的性能均优于基于 MHIs 的分类架构。此外，仅基于 OFIs 的架构在 BVDB 案例中显示出显著的性能提升。对于两个分类任务，聚合方法的性能也略优于仅基于 OFIs 的架构，尽管在许多情况下并不显著。唯一的显著提升出现在 SEDB 的 `T_1` 对比 `T_3` 分类任务中。此外，两种通道特定架构的性能和评分聚合方法的性能都显著高于随机水平（二分类任务的随机水平为 50%），这表明所设计方法的有效性。此外，通过使用两个通道并对这两个通道特定的深度深度注意力方法的评分进行加权聚合，提升了分类架构的性能。

![](img/601340ca744b738277eef45ff127492a_31_0.png)

(a) 生物热力疼痛数据库（基础视频）。(b) SenseEmotion 数据库。

**图 6.** 分类性能（准确率）。星号 (*) 表示性能有显著提升。测试是使用显著性水平为 5% 的 Wilcoxon 符号秩检验（Wilcoxon signed rank test）进行的。在每个箱线图中，平均分类准确率和中分类准确率分别用点和水平线表示。

此外，为了对自注意力机制提供更深入的见解，图 7 展示了 BVDB 在留一交叉法（LOSO）交叉验证过程中每个评估步骤计算出的帧权重值，图 8 展示了 SEDB 的对应值（仅针对 `T_0` 对比 `T_i` 分类任务，类似于 `T_1` 对比 `T_i` 分类任务）。两个数据库中特定 MHI 深度注意力模型的权重值分布（BVDB 的图 7a,c，SEDB 的图 8a,c）呈现偏态。它描述了权重值沿每个序列时间轴的稳步增长，序列末尾的 MHIs 显著高于其他帧。这是因为随着 MHIs 的顺序提取过程，每张提取的图像都比前一张包含更多的运动信息，因此，对于实际分类任务而言，最后的 MHIs 比早期图像更有意义且相关性更高。因此，此类图像应该相应地赋予更高的权重。因此，设计的网络能够通过使用自注意力机制执行此类任务。

(a) 注意力历史图像。

(b) 光流图像。

(c) 平均注意力权重。

> 图 7. BioVid 热力疼痛数据库（A 部分）：分类任务 `T_0, T_i` 的注意力权重值。(a,b) 中的每个子图和平均权重值分别用水平线表示。在 (e) 中，平均权重值被归一化在最大值和最小平均值之间，以便更好地可视化数值分布。

对于 OFIs 的权重值分布也可以观察到类似的现象（详见 BVDB 的图 `7_b`，SEDB 的图 `8_b`）。所示的两种分布也呈现偏态，权重值相对于时间轴逐渐增加。这表明记录的疼痛相关面部表情从中性面部描述（与实际分类任务无关）开始，到面部运动的顶点（这是所描述面部表情最相关的帧）逐渐增加，然后逐渐转回中性面部描述。因此，网络利用注意力机制根据这种恐慌面部运动的特定特征分配权重值，从而证明了此类方法在面部表情分析中的相关性。

此外，加权聚合的性能进一步基于以下额外的性能指标：

```
Macro Precision = \frac{1}{c} \sum \frac{tP_i}{tP_i + tF_i}  (23)
```

```
Macro Recall = \frac{1}{c} \sum_{i=1}^c \frac{tP_i}{tP_i + fn_i}  (24)
```

```
Macro F1 Score = \frac{2 \times Macro Precision \times Macro Recall}{Macro Precision + Macro Recall}  (25)
```

其中，`tp_i, fp_i` 和 `fn` 分别是第 `i` 类的真阳性、假阳性和假阴性。评估结果如图 9 所示，分别对应 BVDB（图 9a）和 SEDB（图 9b）。

![](img/601340ca744b738277eef45ff127492a_33_0.png)

(a) 运动情绪图像。(b) 光流。

图 8. SenseEmotion 数据库：分类任务 `T_0, T_i` 的注意力权重值。(a,b) 中的每个子图和平均权重值分别用水平线表示。在 (c) 中，平均权重值被归一化在最大值和最小平均值之间，以便更好地可视化数值分布。![](img/601340ca744b738277eef45ff127492a_33_0.png)(a) 运动情绪图像。(b) 光流。(c) 平均注意力权重。

这项工作的目标并非优化实验中的方法，而是为了评估此类架构分析疼痛相关面部表情的能力。多阶段训练策略也可能提高该架构的整体性能，因为在考虑耦合聚合层将输入序列转换为其属性时，端到端的方法可能会遭受过拟合。所进行的评估表明，MHIs（运动图像历史）和 OFs（光流）已将序列的时间维度整合到其属性中。在大多数情况下，该评估结果优于对 MHIs 的评估。结果还表明，构建 MHIs 的大多数感兴趣区域位于每个序列时间轴的末端，而从整个序列中提取的单个 MHIs 也可以作为深度架构的输入。总体而言，所做的实验表明，区分高低疼痛水平仍然是一项艰巨的任务。

作者贡献：概念化，P.T. 和 FS：方法论；P.T.：软件；P.T.：验证；P.T.：正式分析；PT, IT 和 FS：初稿写作与准备，P.T.：写作与编辑，P.T., H.A.K 和 FS：视化；指导，H.A.K 和 FS：项目管理，H.A.K 和 FS：资金获取，H.A.K 和 ES。所有作者均已阅读并同意稿的最终版本。

资助：这些结果的研究收到了联邦教育与研究部 (BMBF, SenseEmotion) 对 FS 的资；eMed, CONFIRM 01IZ1708C 对 H.A.K 的资；以及巴登符州信号识别部 (ZIV) 对 H.A.K 的资。

致谢：我们感谢 NVIDIA 的赞助，捐赠了本研究使用的 Tesla K40 GPU。

冲突：作者声明无利益冲突。

## 参考文献

- 1. Ahad, M.A.R., Tan, J.K.; Kim, H.; Ishikawa, S. 运动图像历史：其变体与应用。Mach. Vis. April. 2012, 23–255. [CrossRef]

- 2. Horn, B.K.; Puschnik, B.G. 自动检测光流的方法确定。Art. Ital. 1981, 185–203. [CrossRef]

- 3. Luce, C.; John, F.E.; Prkachman, K.; Solomon, P.E.; Mathews, I. 痛苦数据：UNBC-McMaster 肩部疼痛表情数据库。In Proceedings of Face and Gesture, Santa Barbara, CA, USA, 2011年3月21–25日; 57–64.

- 4. Walter, S.; S.; Ehleter, H.; Tan, J.; Traue, H.; Cwcarcrow, S.; Werner, P.; Al-Hamadi, A.; Andrade, A. BioVid 头部疼痛数据库，用于自动疼痛识别系统的评估和系统性验证。In Proceedings of the IEEE International Conference on Computer Vision, Lausanne, Switzerland, 2015年6月15–20日; 121–128.

- 5. Zheng, J.; Kohberg, S.; Romero-Paredes, R.; Martinez, B.; Singh, A.; Cella, M.; Valst, M.; Meng, H.; Kemp, A.; Shafizadeh, M.; 等. 疼痛相关表情的自动检测：挑战与多模态数据集。IEEE Trans. Affect. Comput. 2016, 7–435–451. [CrossRef]

- 6. Vela, M.; Mayer, G.; Zhang, Y.; Dessler, V.; Gross, S.; Neumann, H.; Kim, J.; 等. SenseEmotion：一种多模态数据库和自动疼痛与情绪识别系统的系统验证。In Proceedings of the Multimodal Pattern Recognition of Signals in Human-Computer Interaction, Cancun, Mexico, 2016年12月; 127–139.

- 7. Thomas, P.; Werner, V.; Schenkier, F. 用于个性化疼痛等级识别的视频特征分层分解。In Proceedings of the 25th European Symposium on Artificial Neural Networks, Computational Intelligence and Learning, Bergen, Belgium, 2017年4月26–28日; 465–470.

- 8. Werner, P.; Al-Hamadi, A.; Limbrecht-Endlich, K.; Walter, S.; Traue, H. 基于面部活动描述的自动疼痛评估。IEEE Trans. Affect Comput. 2007, 2, 286–299. [CrossRef]

- 9. Tsai, F.S.; Hsu, Y.L.; Chen, W.; W, Y.; Lin, C.J. 语音特征和面部表情疼痛等级评分量的前的前开发与评估。In Proceedings of the Interspeech 2016, San Francisco, CA, USA, 2016年9月8–12日; 92–96.

- 10. Thiam, P.; Schwenker, F. 结合手工特征进行基于音频的疼痛分类。In Proceedings of the Multimodal Pattern Recognition of Social Signals in Human-Computer-Interaction, Beijing, China 2018年8月; pp. 49–58.

- 11. Walter, S.; Imbrecht-Ecklund, L.; Traue, H.C.; Werner, P.; Al-Hamadi, A.; Diniz, N.; Silva, G.M.; Andrado, A.O. 使用超声参数的多模态疼痛分类。Psychol. 2014, 7, 363–380. [CrossRef]

- 12. Chu, Y.; Zhao, X.; Han, J.; Su, Y. 基于生理体征的疼痛强度测量方法。NeuroFront. 2017, 111, 279. [CrossRef]

- 13. Lopez-Martinez, D.; Garcia, R. 利用神经网络从自主信号中进行连续疼痛识别。In Proceedings of the 40th Annual International Conference of the IEEE Engineering in Medicine and Biology, Honolulu, HI, USA 2018年7月17–28日; pp. 5624–5627.

- 14. Thiam, P.; Schwenker, F. 用于疼痛强度评估和分类的多模态数据融合。In Proceedings of the 7th International Conference on Image Processing Techniques and Tools, Montreal, QC, Canada, 2017年11月28日; 1–4.

- 15. Thiam, X.; Kellner, A.; Bellmann, M.; Layher, G.; Zhang, Y.; Vela, M.; Gruss, S.; Walter, S.; 等. 探索用于觉感知的模型。IEEE Trans. Affect. 2019, 19, 4503. [CrossRef]

- 16. Ekman, P.; Friedrich, W. 面部系统：运动测量。Psychologist: Mountain View, 1998.

- 17. Senechal, T.; McDuff, D. 使用面部动作单元进行疼痛评估。In Proceedings of the International Conference on Recognition, Santiago, Chile, 2015; 7–10.

- 18. Lucy, J.; Lusey, S.; Sudhakaran, S. 使用无监督迁移学习的面部疼痛检测。In the International Workshop on Artificial Intelligence in Health, Stockholm, Sweden, 2018; pp. 162–180.

- 19. Abo, S. 支持机分类。Springer: Berlin, 2005.

- 20. Brümner, J.; Reed, J. 基于神经网络的疼痛识别。In the IEEE International Symposium on Signal Processing and Information Theory, Vancouver, BC, Canada, 2007:23–30. [CrossRef]

- 21. Zafar, Z.; Khan, N.A. 通过面部动作进行疼痛评估。In Proceedings of the 22nd International Conference on Pattern Recognition, Stockholm, Sweden, 2014; pp. 4696–4701.

- 22. Cover, T.; Hart, P. 最近邻模式。IEEE Trans. Inf. Theory 1967, 13, 21–27. [CrossRef]
