
*   `leftOfSegment(x, y, Ls[i])`：检查 x 坐标是否在线段 `Ls[i]` 的左侧。

    ```
    leftOfSegment(x, y, Ls[i]) = ⇔ (x*(y[a] - y[b]) - y*(x[a] - x[b]) - (x[a]*y[b] - x[b]*y[a])) < 0.
    ```

    (18.4.2)

从图 18.5 可以看出，`leftOfLineSegment(x[t], y[t], Ls[1])` 对于数据点 `(x,y)` 返回 `true`。然而，它对于 `leftOfLineSegment(x[t], y[t], Ls[5])` 返回 `false`。

*   `intersect(x, y, Ls[i])`：我们从感兴趣的点 `(x,y)` 处画一条与 `x` 轴平行的虚线。该函数检查该虚线段 `Ls[i]` 是否与该虚线相交。如果一个数据点既在 `inRangeOfLineSegment` 中又是 `leftOfLineSegment`，则认为该点与线段相交，如方程 (18.4.3) 所示：`intersect(x, y, Ls[i]) ⇔ inRangeOfLineSegment(x, y, Ls[i]) ∧ leftOfLineSegment(x, y, Ls[i])` (18.4.3)

    从图 18.5 可以明显看出，`intersect(x[t], y[t], Ls[i])` 对于线段 1, 2, 3, 8 和 9 返回 `true`，而对其余返回 `false`。

*   `withinCluster(x, y, C[k])`：检查数据点 `(x,y)` 是否在簇 `C[k]` 内。该函数对特定簇的所有边界段执行 `intersect(x, y, Ls[i])` 并对结果进行异或（XOR）运算。如果从数据点 `(x,y)` 出出的平行于 x 轴的虚线与该簇的奇数条线段相交，则函数对该簇返回 `true`。方程 (18.4.4) 显示了该函数：`withinCluster(x, y, C[k]) ⇔ ⊕[i≤numofLs[k]](intersect(x, y, Ls[i]) ∧ In(C[k], Ls[i]))` (18.4.4)

这里，`In(C[k], Ls[i])` 决定簇 `C[k]` 是否包含线段 `Ls[i]`。例如，从图 18.5 可以看出 `(x[t], y[t])` 在簇 `C[1]` 内部但不在 `C[2]` 内，因为平行于 x 轴的虚线相交了该簇的三条线段（奇数个）。

从表 18.1 我们可以看到 `n` 表示传感器测量总数，所有可能的健康状态由 `l` 表示。在本文工作中，我们假设每个测量值都由传感器记录/报告。从表中我们还看到 `S` 代表所有传感器的集合，`P` 是这些传感器测量值的集合，`L` 是所有患者状态的集合。假设所考虑的患者状态用 `j` 表示，其中 `j∈L`。为了简单起见及其他原因，我们考虑二维簇，因此一次考虑两个传感器关系。因此，对于标签 `j∈L` 和传感器测量对 `(a,b)`（其中 `(a,b)∈S`），我们获得一个或多个簇 `C[k]`，它代表了该特定标签 `k` 下两个测量值之间的关系。这些簇由几条线段组成，表示为 `Ls[l]`。对于所有测量值 `P` 中的一对传感器测量值 `P[a,b] = (P[a], P[b]) ∈ P`，DBSCAN 算法使用 (18.4.5)、(18.4.6) 和 (18.4.7) 检查一致性。

```
consistent(P, j) ⇔ forall[(a,b) ∈ S ∧ (a≠b)] ∃k ∈ C withinCluster(P[a,b], C[k])
``` (18.4.5)

其中

```
withinCluster(P[a,b], C[k]) ⇔ ⊕[l](intersect(P[a], P[b], Ls[l]^{a,b,j}) ∧ In(C[k], Ls[l]))
``` (18.4.6)

```
intersect(P[a], P[b], Ls[l]^{a,b,j}) ⇔ inRangeOfLineSegment(P[a], P[b], Ls[l]^{a,b,j}) ∧ leftOfLineSegment(P[a], P[b], Ls[l]^{a,b,j})
``` (18.4.7)

#### 18.4.2 K-means

K-means 算法产生了与 DBSCAN 相似的约束，对于簇的数量、噪声点等（Likas et al., 2003）。K-means 算法的主要挑战之一是确定 `k`。

#### 18.4.3 One-class SVM (OCSVM)

OCSVM 模型与先进的支持向量机（SVM）略有不同。对于零日攻击/新攻击检测，可以使用 OCSVM 模型，通过调整超参数 gamma 和 nu 来实现。

#### 18.4.4 Autoencoder (AE)

AE 模型主要是用于重建特征的神经网络。普通神经网络与 AE 模型之间的主要区别在于 AE 模型包含一些严格的约束。例如，AE 编码隐藏层的节点数需要少于特征的数量。

### 18.4.2 Ensemble-based ADMs in SHS

DBSCAN 和 K-means 算法作为 SHS ADM 的效能在我们正在工作中进行了分析。此外，我们提出了 AE 和 OCSVM 的无监督集成，这在智能建筑领域显示了显著性能。所提出的集成模型也可以用于 SHS ADM。算法的工作流程如下：

#### 18.4.2.1 Data Collection and Preprocessing

集成 ADM 的主要阶段是从受信设备收集良好的传感器测量值。数据集存储了 SHS 传感器测量值和相应的执行。预处理的第一步是从数据集中删除重复。然后对特征进行归一化，随后通过主成分分析降低特征维度。预处理步骤允许更快的模型训练。特征降维仅针对 OCSVM 模型训练执行。

#### 18.4.2.2 Model Training

模型训练使用预处理数据训练 AE 和 OCSVM 模型。AE 模型直接在历史良好样本上进行训练，训练完成后，使用预测模型计算良好样本和异常样本的分离阈值。

AE 和 OCSVM 的阈值计算是所提 ADM 的关键步骤。阈值决定了区分攻击样本和良性样本的决策平面。OCSVM 的决策函数输出一个在 `[-1,1]` 之间的得分，该得分可以在无需进一步处理的情况下直接作为 OCSVM 模型的权重。OCSVM 模型的阈值为 `0`，这意味着预测值大于 `0` 的样本被归为良性样本，反之亦然。在 AE 模型中，实际特征（传感器测量值）与模型预测值之间的差异被称为误差。AE 模型的阈值计算 `threshAE` 可以通过取训练预测与对应特征之间的最大误差来实现，如算法 1 所示。然而，由于不同模型的阈值处于不同的尺度，因此需要对这些阈值进行归一化处理。

### 18.4.2.4 异常检测

所提出的集成 ADM 同时使用训练好的模型 `model(AE)`、`model(OCSVM)` 及其对应的阈值 `threshAE` 和 `threshOCSVM` 来检测异常。对于特定样本，AE 和 OCSVM 模型分别根据其与 `threshAE` 和 `threshOCSVM` 的距离赋予权重 `weightAE` 和 `weightOCSVM`。此外，距离的符号被用于确定模型的预测结果 `predAE` 和 `predOCSVM`。如果 AE 和 OCSVM 模型的输出结果不一致，则将模型的归一化权重（即 `normWeightAE` 和 `normWeightOCSVM`）与模型的预测结果相乘，得到集成结果。

> **算法 1：集成无监督机器学习模型**
>
> **输入：** `X`, `T`
>
> **输出：** `predSample`
>
> 在 `X` 上训练基于自编码器的 ADM `model(AE)`
>
> 在 `pca(X)` 上训练基于 OCSVM 的 ADS 模型 `model(OCSVM)`
>
> `threshAE = max(abs(X - model(AE)(X)))`
>
> `threshOCSVM = 0`
>
> **对于** `T` 中的每个样本：
>
> `weightAE = abs(sample - model(AE)(sample))`
>
> `weightOCSVM = model(OCSVM)(pca(sample))`
>
> `normWeightAE = abs(normalize(weightAE) - normalize(threshAE))`
>
> `normWeightOCSVM = abs(normalize(weightOCSVM) - normalize(threshOCSVM))`
>
> **if** `weightAE < threshAE`, **then** `predAE = 1`
>
> **else** `predAE = -1`
>
> **if** `weightOCSVM < threshOCSVM`, **then**
>
> `predOCSVM = -1`
>
> **else** `predOCSVM = 1`
>
> ```
> weightSample = 1/2 * (normWeightAE * predAE + normWeightOCSVM * predOCSVM)
> ```

形式攻击分析器获取 `SHS` 数据集并训练 `ADM` 和 `PSCM` 模型。回顾一下，`PSCM` 负责为患者状态标记标签，而 `ADM` 则检查 `PSCM` 提供的标签的传感器测量的一致性。攻击分析器利用从两个机器学习模型学习到的参数，并将其转换为决策边界以生成约束。这些约束被公式化为约束满足问题（`CSP`）并输入 `SMT` 求解器。求解器获取攻击者的能力、访问权限、攻击目标以及模型约束，并评估与传感器测量相关的威胁。

如果基于患者考虑量的约束不冲突，求解器将返回满足（`SAT`）结果，此时分析器可以报告攻击向量，表明需要修改可访问的传感器测量以通过 `PSCM` 并逃避 `ADM`，从而实现攻击目标。分析器能够确定最关键的威胁，即攻击者获取目标所需的最小能力。可以说，如果攻击者的能力小于分析器提供的能力，则攻击者无法成功发动攻击以完成目标，因此系统对该能力具有韧性。如果求解器产生不可满足（`UNSAT`）的结果，意味着根据攻击者的能力无法实现攻击目标。在这种情况下，分析器逐渐增加攻击者的能力，直到达到 `SAT` 点。`SMT` 求解器使用多种背景理论来解决 `CSP` 问题，并提供形式化保证。

### 18.5.1 案例研究

在本节中增加了两个案例研究以理解攻击分析器的工作原理。对于案例研究，由于在真实和合成数据集上的显著性能，考虑了基于 `DT` 的 `PSCM` 和基于 `DBSCAN` 的 `ADM`。

#### 案例研究 1

第一个案例研究是关于我们考虑的类似于未来医疗系统的合成数据集。该数据集包含心率、血压、酒精、呼吸率等多种生命体征，收集自多个数据集，如[胎儿 ECG 数据集](https://ch30.xhtml#b2-ref-604)、[UCI 糖尿病数据集](https://ch30.xhtml#b2-ref-605)、[氧饱和度变异数据集](https://ch30.xhtml#b2-ref-606)、[BIDMC PPG 呼吸数据集](https://ch30.xhtml#b2-ref-607)以及 [StatCrunch 数据集](https://ch30.xhtml#b2-ref-578)。这些数据集每个包含超过 17,000 个样本和 8 传感器测量。使用参考数据集 [表 18.3](https://ch30.xhtml#b2-table-wrap-044) 生成数据。数据集包含六种不同患者状态的传感器测量值。[表 18.3](https://ch30.xhtml#b2-table-wrap-044) 展示了患者的四种不同传感器测量。我们的攻击分析器报告称，攻击者无法通过修改单个传感器测量让 `SHS PSCM` 将高胆固醇患者错误分类为高血压患者。拥有两个传感器测量（即收缩压和血氧）可能会实现攻击目标并错误标记患者，导致护理人员提供错误的药物/治疗。然而，`ADM` 可以检测到攻击，因为修改两个传感测量违反了从历史数据得出的患者传感器测量分布一致性。我们的攻击分析器通过通过修改心率、收缩压、舒张压和血氧传感器测量（分别为 2%、7%、2.5% 和 5.7%）识别出可能的攻击路径。来自 `PSCM` 和 `ADM` 的示例 `DT` 和 `DBSCAN` 约束所示 [表 18.4](https://ch30.xhtml#b2-table-wrap-045) 和 [表 18.5](https://ch30.xhtml#b2-table-wrap-046) 中。

#### 案例研究 2
