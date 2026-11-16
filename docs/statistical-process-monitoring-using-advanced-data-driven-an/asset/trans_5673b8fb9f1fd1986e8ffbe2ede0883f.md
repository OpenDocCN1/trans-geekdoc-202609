

控制图在下述条件下发出偏移信号：

$Q_f = \max_{k=1,\dots,q} \frac{W_{j,k} - \text{E}(W_{j,y})}{\sqrt{\text{Var}(W_{j,y})}} > L,$

其中 \( L \) 是为特定的IC ARL而选取的控制限。该 \( L \) 可通过仿真确定，且必须在进行第II阶段监控之前进行一次性计算。在实际应用中，\( W_{j,y} \) 中的 \(\frac{2-\lambda}{\lambda[1-(1-\lambda)^{2j}]}\) 因子可替换为渐近形式 \((2-\lambda)/\lambda\)。LEWMA通过仿真进行评估，尤其关注其在OC设置下的ARL，针对 \( p=5 \) 和 \( p=15 \)。该方法与其他两种EWMA图统计量进行了比较，涵盖不同变量数量下的多种偏移大小。结果表明，从ARL角度看，LEWMA能对多种偏移提供全面的保护。此外，作者评估了该方法在15个变量的集合中正确识别所有偏移变量的能力。在15个变量中仅有1个偏移变量的情况下，LEWMA在约55%至60%的仿真中能正确识别该偏移变量；不过，随着偏移变量数量从1增加到2再到3，正确识别偏移变量的仿真最高比例从60%下降到37%，再下降到24%。相反，在识别偏移变量时出现错误（即未识别出偏移变量，或选中了未偏移变量）的仿真比例随偏移变量数量增加而上升：1个偏移变量时为6%，2个偏移变量时为22%，3个偏移变量时为34%。尽管如此，LEWMA的性能仍优于其竞争方法。该研究是除了故障检测之外，最早评估故障隔离性能的研究之一，同样与[25]的结果表明，故障隔离是一个非常具有挑战性的问题，方法仍有改进空间。

### 示例方法 3. APC-PCSR。

自适应主成分与基于主成分的信号恢复（APC-PCSR）自适应地选择主成分（PCs），允许其随时间变化，随后引入一种利用自适应LASSO[55]的诊断方法。与[2,6,16,17]相比，该方法在高维环境下表现往往更好，后者随着维度增加计算负担变重。当变量存在依赖关系时可使用该方法，且无需了解故障方向、大小和/或受影响变量的数量。

为了降低数据维度，执行PCA。这里，\(\mathbf{A}\) 是 \(\mathbf{\Sigma}\) 的 \( p \times p \) 特征向量矩阵，\(\mathbf{y}_i = \mathbf{A}\mathbf{x}_i\) 表示主成分得分。\(\mathbf{A}\) 中的特征向量按顺序排列，使得对应的特征值呈递减顺序，即 \(\lambda_1 \ge \lambda_2 \ge \cdots \ge \lambda_p\)。仅监控前 \( l \) 个主成分（通常是特征值最大的那些）有时可能会漏掉故障，因为前几个主成分的方差较大，因此后几个主成分对故障可能更敏感。为考虑这一点，标准化主成分得分计算如下

\(\tilde{y}_{i,j} = \frac{y_{i,j}}{\sqrt{\lambda_j}}, \quad j=1,\dots,p.\)

假设IC观测服从分布 \(\mathbf{x}_i \sim N(\mathbf{0}, \mathbf{\Sigma})\)，但在OC条件下，分布变为 \(\mathbf{x}_i \sim N(\mu, \Sigma)\)。因此，OC过程的主成分得分分布为 \(\mathbf{y}_i \sim N(\mathbf{\Lambda}'\mu, \mathbf{\Lambda})\)，其中 \(\mathbf{\Lambda} = \text{diag}(\lambda_1, \lambda_2, \dots, \lambda_p)\)。随后，使用EWMA统计量进行监控，类似于Eq. (3.14)中所示，但经修改以应用于标准化主成分得分，如下所示：

\(u_{i,j} = \lambda \tilde{y}_{i,j} + (1 - \lambda)u_{i-1}, \quad i = 1, 2, \dots, \quad j = 1, 2, \dots, p,\)

其中 \(u_0 = 0\)，且 \(\lambda \in (0, 1]\)，与之前相同。注意，无下标的 \(\lambda\) 表示EWMA统计量中的权重，而带下标的 \(\lambda\) 表示特征值。那么，IC过程将具有 \(u_{i,j} \sim N(0, \sigma^2 = \frac{\lambda}{1-\lambda})\)，其平方标准化值为

\(d_{i,j} = \left( \frac{u_{i,j}}{\sqrt{\frac{\lambda}{1-\lambda}}} \right)^2 \sim \chi^2_{(1)}.\)

在存在均值偏移的OC过程中，部分 \(d_{i,j}\) 将变大，但 Ebrahimi et al. [55] 建议滤除部分主成分。他们仅使用 \(\chi^2_{(1)}\) 分布的 \(\alpha\) 上尾分位数对 \(d_{i,j}\) 进行阈值处理，并监控新统计量，

\(R_i = \sum_{j=1}^p \left( d_{i,j} - \chi^2_{(1), \alpha} \right)_+, \quad\)

其中 \((\cdot)_+ = \max(0, \cdot)\)。当 \(R_i\) 超过某个阈值时，则发出警报，该阈值通过在IC条件下的仿真获得，以实现预设的ARL。

一旦检测到故障，第二步是将主成分整合到故障隔离中。假设每个观测均带有噪声，OC状态可表示为 \(\mathbf{x}_i = \mu + \epsilon_i\)，其中 \(\epsilon \sim (\mathbf{0}, \mathbf{\Sigma})\)。此时，OC主成分得分为 \(\mathbf{y}_i = \mathbf{A}\mathbf{x}_i = \mathbf{A}\mu + \tilde{\epsilon}\)，其中 \(\tilde{\epsilon} = \mathbf{A}\epsilon\)。目标是估计稀疏的 \(\mu\)，因此采用自适应LASSO

\(\mu^* = \text{argmin}_{\mu} \left( (\mathbf{y}_i - \mathbf{A}\mu)'(\mathbf{y}_i - \mathbf{A}\mu) + \gamma \sum_{j=1}^p \frac{1}{\tilde{x}_j} |\mu_j| \right), \quad\)

其中 \(\tilde{x}_j\) 是第 \(j\) 个变量的最小二乘均值。不过，\(\mathbf{y}_i\) 中每个变量的协方差各不相同，因此采用标准化主成分得分和主成分，以矩阵形式表示如下：

\(\tilde{\mathbf{y}}_i = \mathbf{\Lambda}^{-1/2}\mathbf{y}_i, \quad \text{and} \quad \tilde{\mathbf{A}} = \mathbf{\Lambda}^{-1/2}\mathbf{A}.\)

将这些代入自适应LASSO估计中，得到以下目标函数：

\(\mu^* = \text{argmin}_\mu \left( (\tilde{\mathbf{y}}_i - \tilde{\mathbf{A}}\mu)'(\tilde{\mathbf{y}}_i - \tilde{\mathbf{A}}\mu) + \gamma \sum_{j=1}^p \frac{1}{\tilde{x}_j} |\mu_j| \right) .\)

Ebrahimi et al. [55] 在仿真中对其方法进行了测试，\(p\) 的取值范围从100到10,000，因此能够测试非常高维的环境。在IC设置中，报告了误检百分比，当 \(p \ge 5000\) 时，该比例达到名义设置 \(\alpha = 0.05\)。对不同偏移幅度的OC设置计算了ARL，APC-PCSR方法优于基准比较方法。还通过多个指标评估了PCSR方法隔离偏移变量的能力，包括

- 假阴性率（FN%）——未检测出的偏移变量占偏移变量总数的百分比；
- 假正率（FP%）——被识别出的未偏移变量占未偏移变量总数的百分比；以及
- 参数选择得分（PSS）——被错误分类的变量总数（无论是作为偏移变量还是未偏移变量）。

虽然在多种偏移大小和仿真设置下FN%相对较低，但对于小偏移，FP%和PSS可能较大，不过两者随着偏移大小增加而迅速下降。对于协方差矩阵非稀疏的过程，PCSR的表现与[3]（另一种基于LASSO的故障隔离方法）相似。不过，如果过程具有稀疏协方差矩阵，则PCSR表现更好，[55]的作者认为此类设置在实践中很常见，因为变量通常仅与总监控变量的一个小子集相关。因此，APC-PCSR是一种在高维环境下应用前景广阔的方法，其应用在3.5.2节的案例研究中有所说明。Jiang et al. [56] 也使用优化算法对变量进行降维，以用于基于PCA的监控。

## 其他第II阶段故障隔离方法。

针对特定目的，已提出许多第II阶段故障隔离方法。Jiang et al. [6] 提出了一种变量选择多元EWMA（VS-MEWMA）图，继续使用[2]的VS-MSPC图中的 \(L_0\) 惩罚。Yan et al. [57] 提出了一种针对高维高斯混合模型的基于VS的控制图。Kuang et al. [58] 将变量选择纳入判别分析，用于多元故障隔离。[59] 和 [60] 使用了多种类型的卡尔曼滤波器来检测和隔离传感器故障。

此处描述的第II阶段基于VS的控制图假设均值和协方差矩阵已知，因此 Li et al. [61] 引入了一种稳健的自启动方法，以减少启动VS-MEWMA图所需的IC观测数量。Liang et al. [62] 提出了一种LEWMA [16]的版本，可应用于椭圆分布族内生成的任何连续过程，在重尾和偏态多元

