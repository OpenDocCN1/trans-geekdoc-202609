

### 11.6.2 用于 IED 检测的逻辑回归分类器

(11.26) 
```
f(x) = Σ(j=1 to L) w(j) x(j) + b
```
其中 `L` 为特征数量，`j` 为特征索引。针对此处的 IED 和非 IED 片段两个类别，`f(x)` 的符号表示数据 `x` 类别成员身份的预测。逻辑回归的一个优点是它提供了一种自然的方式，根据观测数据表达类别成员身份概率。`f(x)` 的幅度对应类别成员身份概率 `p(IED|x)`，即数据片段 `x` 包含 IED 的概率，由逻辑函数表示为：

(11.27) 
```
p(IED|x) = 1 / (1 + exp(-f(x)))
```
且
`p(IED|x) = 1 - p(nonIED|x)`。

权重向量 `w` 通过最小化二次正则化逻辑回归损失函数来估计，其中分类准确性与过拟合及泛化性能之间存在权衡。控制该权衡的正则化参数通过交叉验证进行估计 [[124]](#c11.xhtml#c11-bib-0124)。

分类器采用留一受试者检测策略，为每位受试者单独训练，该策略移除某一受试者的数据（测试受试者），并将其余受试者的分类器以线性投票方案进行组合。各个分类器被赋予相等的权重。这种加权过程对应于各个分类器的朴素贝叶斯组合 [[125]](#c11.xhtml#c11-bib-0125)。线性投票方案产生的分类器准确率是针对测试受试者的切片 IED 和非 IED 数据片段获得的。受试者内或受试者间分类性能低于 55% 的个体分类器将从集成中排除。每位受试者分类器的性能通过最佳正则化参数的准确率来估计。IED 检测通过扫描数据并将分类器应用于头皮 EEG 的 ±162.5 ms 信号窗口来执行。

为获得最佳训练集，专家癫痫学家根据 iEEG 数据中识别出的每个 IED 模式为 IED 的确定程度给出了评分。这产生了 [图 11.17](#c11.xhtml#c11-fig-0017) 所示的直方图。从该直方图可知，评分高于 5 分表示属于癫痫尖波的可能性足够大，该片段可用于 IED 训练集。

[图 11.18](#c11.xhtml#c11-fig-0018) 显示了集成分类器的分类准确率随训练受试者数量的变化。对于每个训练受试者数量，完整集合的 100 个不同子集被用于集成中。可以观察到，当受试者数量约为 10 时达到上限水平，然而不同子集之间准确率的标准差（灰色区域）随着用于训练的受试者增多而减小。

该算法在识别头皮 IED 与非 IED 片段方面达到了 65% 的准确率，而在同一受试者上训练和测试时准确率为 68%。此外，它还能以较低的假阳性检测数识别大多数患者的头皮不可见 IED 事件。这些结果代表了一个概念验证：即即使 IED 在视觉上不可识别，头皮 EEG 中也包含 IED 信息；且受试者间 IED 拓扑和形状的差异足够小，使得通用算法可以被使用。

在 [图 11.19](#c11.xhtml#c11-fig-0019) 中，展示了检测到的 IED（来自头皮 EEG）与专家癫痫学家识别的 IED 总数之比，按从高（红）到低（黑）的检测阈值，针对每个评分值绘制。检测阈值越高，被视为 IED 的检测数量越少。同时，假阳性也随之减少。

![Figure 11.17 The scoring histogram provided by an expert in epilepsy.](images/c11f017.gif)

**图 11.17** 癫痫专家提供的评分直方图。

![Figure 11.18 Classification accuracy of the ensemble classifier with respect to the number of training subjects.](images/c11f018.gif)

**图 11.18** 集成分类器的分类准确率随训练受试者数量的变化。

![Figure 11.19 The ratio of detected IEDs (from the scalp EEG), to the total number of IEDs that were identified from the iEEGs by the expert epileptologist for each score value for high (red) to low (black) detection thresholds. FP refers to percentage of false positives.](images/c11f019.gif)

**图 11.19** 检测到的 IED（来自头皮 EEG）与专家癫痫学家从 iEEG 中识别出的 IED 总数之比，针对从高（红）到低（黑）的检测阈值，按每个评分值绘制。FP 指假阳性百分比。

例如，在产生 3.6 FP/min 的检测阈值下，算法检测到了 21% 的评分为 9 分的 IED。值得注意的是，不到 9% 的尖波在头皮上可见。

确认真阳性和假阳性的方法是将检测到的成分投影到头皮地形图上，如 [图 11.20](#c11.xhtml#c11-fig-0020) 所示。

![Figure 11.20 Detected scalp‐invisible IEDs with true positive on the top and false positive at the bottom. The distributions of the sources in the right‐hand side topographs verify the claim.](images/c11f020a.gif)

**图 11.20** 检测到的头皮不可见 IED，上方为真阳性，下方为假阳性。右侧地形图中的源分布验证了该论点。

### 11.6.3 用于 IED 检测的多视角方法

利用上述数据，[[126]](#c11.xhtml#c11-bib-0126) 尝试了一种使用 Tucker 张量分解进行 IED 检测的多视角方法。在他们的工作中，他们将张量分解应用于一组癫痫患者的 EEG 数据，并将数据分解为三个模态：空间、时间和频率，每个模态包含若干成分或特征。随后，在对应于这些模态和成分互补组合的各种特征集上分别训练分类器，并测试每个特征集的分类准确率。然后分析空间、时间或频率特征对分类准确率的相对影响，并做出了有用的解释。此外，还表明通过张量分解，通过评估分类性能随模态成分数量的变化并拒绝对分类准确率贡献不显著的成分，可以实现降维。

### 11.6.4 用于 IED 检测的耦合字典学习

