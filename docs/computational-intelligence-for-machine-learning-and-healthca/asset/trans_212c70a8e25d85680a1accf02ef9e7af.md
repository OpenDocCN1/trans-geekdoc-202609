

此外，连续心跳之间的 `R-wave` 到 `R-wave` 信息被测量以通过心跳估计心率变异性。因此，计算了四种类型的 `R-` 到 `R-wave` 信息作为特征，其类似于心跳的模式，即先前、后、局部和平均 `R` 波峰到 `R` 波峰信息。在此，估计先前和当前 `R-wave` 之间的周期以计算先前的 `R` 到 `R` 信息。估计当前 `R-wave` 与即将到来的 `R-wave` 之间的周期以计算后 `R` 到 `R` 信息。先前和后 `R-` 到 `R-wave` 周期的组合作为心跳的特征可称为瞬时节律特征。平均 `R-wave` 到 `R-wave` 特征是通过取每个心跳的先前三分钟片段的 `R-wave` 到 `R-wave` 间隔的平均值来估计的。类似地，局部 `R-wave` 信息是通过取当前心跳的前八秒事件的所有 `R-wave` 到 `R-wave` 间隔的平均值来估计的。这两个特征，即平均和局部，对应于一系列心跳的平均特征。

最后，这些心率变异性特征被连接到作为特定心跳的 `S-transform` 结果而获得的输出系数。

### 3.3.4.1 特征分类

在本工作中，使用了 `TSVM` 分类器模型（[Hsu and Lin, 2002](#bodymatter-003.xhtml#b_9783110648195-003_ref_008)；[Tomar and Agarwal, 2015](#bodymatter-003.xhtml#b_9783110648195-003_ref_039)）来识别表示每个心跳的 16 类 `ST` 和心率变异性特征提取。最初，`TSVMs` 被设计为解决二元类别识别问题。本研究通过使用一对一（`OAO`）`SVM` 模型（[Hsu and Lin, 2002](#bodymatter-003.xhtml#b_9783110648195-003_ref_008)；[Tomar and Agarwal, 2015](#bodymatter-003.xhtml#b_9783110648195-003_ref_039)）来解决多类别识别问题。在该方案下，核参数和代价函数参数的选择在报告更高的分类性能方面起着重要作用。核函数的使用使得特征的非线性分类成为可能。换句话说，核的使用有助于在高维空间中对非线性数据或重叠特征实现更好的分类性能。因此，使用了所有核函数，如线性、径向基函数（`RBF`）和多项式函数来分析准确率。这些不同核函数的分类准确率摘要报告在 [Table 3.1](#bodymatter-003.xhtml#b_9783110648195-003_tab_001) 中。[Table 3.1](#bodymatter-003.xhtml#b_9783110648195-003_tab_001) 得出结论，`RBF` 核在用于分类的所有核中实现了最高准确率。需要注意的是，假设用于衡量性能的训练和测试数据集与 [Section 3.3.1](#bodymatter-003.xhtml#b_9783110648195-003_s_003_s_003_s_001) 中介绍的相同。因此，仅报告并详细研究了 `RBF` 核的分类性能。

Table 3.1: Accuracy reported using different kernel functions.

| Kernel | | Training performance (%) | | Testing performance (%) |
| --- | --- | --- |
| Linear | | 98.1 | | 84.23 |
| --- | --- | --- |
| Radial basis function | | 99.7 | | 85.92 |
| Multilayer perceptron | | 99.2 | | 87.32 |
| Polynomial | | 99.5 | | 86.97 |

*The performance is computed in terms of accuracy.

此外，核（`γ`）和代价函数（`C`）指标使用 `ABC` 算法逐步优化，以根据 [Table 3.1](#bodymatter-003.xhtml#b_9783110648195-003_tab_001) 中报告的结果提高分类器模型的准确性。在 `ABC` 技术实现中，所涉及的步骤在 [Karaboga (2005](#bodymatter-003.xhtml#b_9783110648195-003_ref_012)) 中提出。每个食物源的适应度由 `ABC`（[Karaboga, 2005](#bodymatter-003.xhtml#b_9783110648195-003_ref_012)）技术评估，并旨在确定分类器模型的最优性。由于本研究涉及使用 `OAO-SVM` 模型对五类心跳进行分类，因此采用 `ABC` 算法对 10 个二元 `SVM` 分类器的学习参数进行调优。在此，选择了简单的 `SV` 计数技术作为适应度标准，以优化 `ABC` 框架以限制误差边界条件，从而导致识别模型的无偏性能。在训练阶段，`TSVM` 模型的 learning 参数，即 `C` 和 `γ`，通过采用 `ABC` 技术进行优化。参数是基于 `m`-fold `CV` 技术（[Stone, 1974](#bodymatter-003.xhtml#b_9783110648195-003_ref_038)）在训练阶段选择的。为了避免分类器模型的偏差，使用二十二折 `CV` 对测试和训练数据集进行，以估计 `C` 和 `γ` 参数的更好参数估计，从而使所开发模型的分类性能最佳。

### 3.3.5 Performance metrics

在估计混淆矩阵后，`ECG` 搏动的每个类别的性能指标均以五个性能指标确定，即准确率（`A[C]`）、灵敏度（`S[E]`）、`F-score`（`Fs`）、误差（`E[R]`）和阳性预测值（`P[P]`）。`S[E]` 定义为正确识别实例与实例总数之比，`S[E] = T[P]/(T[P] + F[N])`（[Raj and Ray, 2018e](#bodymatter-003.xhtml#b_9783110648195-003_ref_034)）。`P[P]` 确定为正确识别的 `ECG` 搏动与检测到的 `ECG` 搏动总数之比，`P[P] = T[P]/(T[P] + F[P])`（[Raj and Ray, 2018e](#bodymatter-003.xhtml#b_9783110648195-003_ref_034)）。`A[C]` 定义为正确识别实例总数与分类实例总数之比，`A[C] = (T[P] + T[N])/(T[P] + T[N] + F[P] + F[N])`，而 `F-score`（`Fs`）定义为 `(2*T[P]/(2*T[P] + F[N] + F[P]))`。上述性能指标是在患者特定方案中对所开发方法在基准 PhysioNet 数据上计算的（[Raj and Ray, 2018e](#bodymatter-003.xhtml#b_9783110648195-003_ref_034)）。

## 3.4 Simulation results

