
- `1/16777216` 的数字二进制表示末二十四位为 0。
- `1/33554432` 的数字二进制表示末二十五位为 0。
- `1/67108864` 的数字二进制表示末二十六位为 0。
- `1/134217728` 的数字二进制表示末二十七位为 0。
- `1/268435456` 的数字二进制表示末二十八位为 0。
- `1/536870912` 的数字二进制表示末二十九位为 0。
- `1/1073741824` 的数字二进制表示末三十位为 0。

最后设置 `BITMAP[i] = 1`。 (注：此处原文文本似乎存在逻辑重复或乱码，已根据指令尽可能翻译并保留结构)

*(注：由于提供的原文后半部分存在大量逻辑重复和无意义的数字占位，译文已根据其核心含义进行了处理，并确保了格式的正确性)*

由于数据速率高且无法获取所有数据点，问题在数据流的情况下变得更加严重。

更正式地说，在数据挖掘和机器学习中，我们试图找到一个将输入 `$x$` 映射到输出 `$y$` 的函数 `$f$`。

```
y = f(x) \quad (1.2)
```

假设这种函数是平稳的，即生成数据的分布是固定的（但未知的）。然而，现实数据是：

- 非平稳的。
- 演进的。

因此，我们需要能够检测并适应底层函数变化的方法。底层函数被称为*概念*（concept），函数的变化被称为*概念漂移*（concept-drift），也称为*变化检测、协变量偏移、数据集偏移*（dataset shift）等等。

在这里，我们需要区分噪声和*概念漂移*。变化是指变化区域的变化，或者当变化区域内没有足够的示例，或者这些示例无法形成自身的新概念。主要的困难在于确定阈值，以判断数据的变化是形成了一个新概念还是应该被视为噪声。概念漂移的一个示例如图 1.6 所示。如图中所示，信号的方差发生了变化；因此它是信号的概念漂移。

通常，漂移的原因是未知的。然而，大多数研究人员尝试根据模型的变化来寻找原因。关于原因的解释可见 [Kelly et al., 1999]。让我们来看朴素贝叶斯中使用的贝叶斯决策公式。

![](img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_20_0.png)

**图 1.6** 信号中的概念漂移。

$$p(c|D) = \frac{P(D/c)p(c)}{p(D)} \text{ posterior} \propto \text{likelihood} \times \text{prior}$$

当 `$D$` 和 `$c$` 表示数据和类别标签时。变化可以归于：

- 类别先验 `$p(c)$` 可能会随时间变化；
- 似然性 `$p(D/c)$` 可能会变化；
- 后验概率 `$p(c/D)$` 可能会变化。

前两种变化被称为*虚拟*概念漂移，而最后一种被称为*真实*概念漂移。关于这三种情况的进一步说明见图 1.7。我们可以看到原始决策边界由于类别先验的变化而改变了位置，变为 (b)（红色类别的分布发生变化）。在图 1.7(c) 中，决策

![](img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_21_0.png)

FIGURE 1.7 (a) 原始决策边界受 (b) 先验类别变化、(c) 似然性和 (d) 后验类别变化的影响。 (Wang et al., 2018)。

边界保持不变。在图 1.7(d) 中，由于后验概率的变化，决策边界发生了剧烈变化。结果是之前学习的决策函数变得无用或无效。这就是为什么处理由于后验概率变化引起的概念漂移更加难以应对。

在文献中，有很多方法来应对概念漂移。它们通常具有以下特征（图 1.8）（Gamma, 2010）：

在处理概念漂移的数据管理中，学习机制利用内存来保留数据。在全内存机制中，通过不同类型的权重对数据集维护充分统计量，并据此训练模型。在部分内存机制中，数据存储在窗口中并在其基础上构建模型。在检测方法中，技术侧重于学习机制如何检测变化以及变化率。这些方法通常通过监控性能指标或维护时间窗口来检测变化。第一种方法的示例由 Klinkenberg 和 Joachims (2000) 提供，第二种方法由 Kifer 等人 (2004) 给出。

在适应方法中，学习者通过知情的方式或盲目的的方式来跟踪数据演进的变化。在第一种情况下，学习器仅在发生变化时更新；而在后种情况下，学习器无论是否发生变化都会更新自身。在决策模型管理中，该技术描述了内存中保留的决策模型数量。每当检测到变化时，就会积累并尝试学习新模型。动态加权多数算法（Kolter and Malof, 2007）就是决策模型管理的一个示例。

在接下来的章节中，我们将查看几个变化检测算法的示例。

让我们来看一种名为 CUSUM（累计和）的经典变化检测算法（Basseville and Nikiforov, 1993）。它通过监控对数似然比的累计和来检测变化。考虑序列独立的

![](img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_22_0.png)

FIGURE 1.8 处理概念漂移的方法。

随机变量 `$x$`，其概率密度函数为 `$\theta(x)$`。我们的参数是 `$\theta$`，它在变化前为 `$\theta_0$`，变化后为 `$\theta_1$`。假设 `$\theta_0$` 是已知的。对数似然比定义为：

```
$S_t = \log \frac{p_{\theta_1}(x)}{p_{\theta_0}(x)} \quad (1.3)$
```

正式地，令 `$S_t$` 为对数似然的当前累积和，`$m_t$` 为 `$S_t$` 的当前最小值。CUSUM 以阈值 `$\delta$` 统计此差异如下：

```
$g_t = S_t - m_t, \geq \delta$
```

```
$S_t = \sum_{i=0}^t s_i, s_i = \log \frac{p_{\theta_1}(x)}{p_{\theta_0}(x)}, m_t = \min_{0 \leq j \leq t} S_j$
```

其中

```
$t_o = \min \{t : S_t \geq \delta, m_t + \delta\} \quad (1.4)$
```

因此，变化点为：

注意，上述检测规则是累计的 `$S_t$` 与自适应阈值 `$m_t + \delta$` 之间的比较。由于 `$m_t$` 的变化，这不仅是离线的，还保留了整个信息。应用 CUSUM 检测信号变化的示例如图 1.9 所示。如图所示，信号的方差发生了变化；因此它是信号的概念漂移。由于变化是缓慢的，报警会延迟触发（标记为红点）。上图是使用修正因子与阈值比较的 CUSUM 变体。图中值的累计和。

Higia (Garcia et al., 2019) 是一种用于概念漂移和新颖性检测在线聚类算法。该算法的主要思想基于演进流的聚类（Aggrawal 等，2003）。让我们先理解算法的直觉，然后给出完整描述。Higia 算法分为两个阶段：离线阶段和在线阶段。在离线阶段，它创建聚类。然后，对于每个输入数据点，它计算与聚类的距离。如果距离大于指定的阈值，则将其放入缓冲区，并在足够的点后声明为新颖性。当新数据点增加簇的半径时，宣告概念漂移。

时间序列和检测的变化（阈值=1, 漂移=0.05）：N=5

![](img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_24_0.png)

正负变化的累计和时间序列

![](img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_24_1.png)

FIGURE 1.9 （上方）来自正弦函数的时间序列，标记了变化的开始和结束。（下方）正变化的累计和图。

![](img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_24_2.png)

FIGURE 1.10 Higia 离线步骤。

现在我们更正式地查看该算法。如图 1.10 所示，一组初始标记数据按照 Aggrawal 等人 (2003) 使用 CluStream 算法的策略进行聚类。下一步是如图 1.11 所示的在线阶段。在在线阶段，新的输入数据点拟合到模型。这里会发生两种情况。如果新数据点拟合模型，会出现两种情况：新点在微簇半径内或在外部。如果点在最近的微簇内，则数据点被标记为该簇的标签。然而，如果它在外部但在半径的某些系数（用户指定参数）范围内，则更新微簇的半径并将新的数据点被标记为该微簇的标签。这里的第二种情况是概念漂移的一个示例。另一方面，如果数据点不能很好地拟合模型，它被放入

15

![](img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_25_0.png)

图 1.11 Higia 在线。

进入缓冲区。当缓冲区接收到足够的数据点时，运行 CluStream 算法并将新簇放入训练好的模型中。

Higia 如图算法 1.1 所示。我们将以更正式的形式说明该算法。算法的输入是 `$X_{tr}$`，它是一个新的测试点。`$T$` 和 `$k$` 是用户参数。在第二步中，`$w_i$` 是最近的 `$k$` 个微聚类的标签。如果大多数聚类具有相同的标签，我们将新点标记为最近微聚类 `$C_j$` 的质心 `$c_j$`，并将其半径标记为 `$radius(C_j)$`。如果该点从质心到新点的欧几得距离在半径范围内，则用新点更新聚类并对该聚类的标签分类（第 7–10 行）。否则，如果欧几得距离大于聚类半径的 `$T$` 倍，则创建一个聚类的扩展，并将新点分类为相同的标签（第 11–13 行）。如果两种情况都失败，缓冲区中的新数据点需要将新数据点分类为未知簇级（第 15–16 行）。

下面，我们展示了在某些基准数据集上运行 Higia 算法的一些实验结果。准确率时间绘制在图 1.13。

**算法 1.** Higia: 在线阶段

1: 输入：`$X_{tr}, T, k$`

2: 令 `$w_i$` 为距离 `$X_{tr}$` 最近的 `$k$` 个微聚类的标签

3: 如果大多数 `$w_i$` 具有相同标签

4: 令 `$C_j$` 为距离 `$X_{tr}$` 最近的微聚类

5: 令 `$c_j$` 为 `$C_j$` 的质心

6: 令 `$radius(C_j)$` 为 `$C_j$` 的半径

7: `$dist \leftarrow EuclideanDistance(X_{tr}, C_j)$`

8: 如果 `$dist \leq radius(C_j)$` 则

9: 用 `$X_{tr}$` 更新 `$C_j$`

10: 用 `$C_j$` 的相同标签对 `$X_{tr}$` 分类

11: 否则如果 `$dist \leq (radius(C_j) \times T)$` 则

12: 用质心 `$X_{tr}$` 和半径 0.5 创建 `$C_j$` 的扩展

13: 用 `$C_j$` 的相同标签对 `$X_{tr}$` 分类

14: 否则

15: 将 `$X_{tr}$` 添加到缓冲区

16: 将 `$X_{tr}$` 分类为未知

图 12 Higia 算法。

![](img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_26_0.png)

**图 13** Higia 随时间变化的准确率。来源：Garcia 等 (2019)。

![](img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_26_1.png)

**图 14** Higia 随时间变化的准确率。来源：Garcia 等 (2019)。

以及 14。AS 和 kNN 作为基准算法。这里展示了 Higia 算法的性能。可以看出，在四种情况下，Higia 均优于其他算法。kNN 的表现最差。

动态权重多数（ter 和 Maloof, 2007）简称为 DWM，是一种用于跟踪概念漂移的算法。DWM 的基本思想是根据性能动态地创建和移除专家。该算法根据以下四个想法工作：学习者的集成；根据性能对其加权；移除专家；添加新的学习者。

DWM 算法如算法 1.3 所示。我将解释算法的每一个步骤。训练对由 `$\{x, y\}$` 表示，有 `$m$` 个专家，`$c$` 个类有机e, w\}$ 表示专家及其权重。在第 1–3 行，我们初始化专家数量，创建一个新专家并将其权重设置为 1。在最外循环中，我们逐个遍历数据流。首先，我们设置向量 `$\sigma$`，表示加权预测之和为 0。在第二个循环中，我们遍历专家，对每个数据点进行预测，如果出错则降低其权重。在第 11 行，我们更新预测。第 13 行设置全局预测 `$\eta$`。在部分（14–22 行），我们归一化权重。这样做的原因是某些专家可能是正确的，它们的权重可以增加（由于权重的增加）。如果专家的权重低于阈值 `$\alpha$`，则从专家列表中移除。如果全局预测与真实标签不同，说明整个专家集合表现不好，这是创建新专家的时刻。最后，在第 23–25 行，我们训练新专家并在第 26 行返回全局预测。DWM 是用于概念漂移的通用算法。可以使用任何在线算法作为基学习器，例如决策树、朴素贝叶斯或神经网络。

```
输入 $\{x, y\}_j^1$: 训练数据，$c \in \mathbb{N}, c \geq 2$: 类别数量，$\alpha$: 删除专家的阈值，$\beta$: 降低权重，$q$: 权重更新时间，$\{e, w\}^1_m$: 专家及其权重，$\eta_g, \eta_l$: 全局和局部预测，$\sigma \in \mathbb{R}$: 每个类别的加权预测之和
$m \leftarrow 1$
$e_m \leftarrow Create\New\Expert()$
$w_m \leftarrow 1$
for $i \in \{1, \dots, n\}$ do
$\sigma \leftarrow 0$
for $j \in \{1, \dots, m\}$ do
$\eta_l \leftarrow Classify(e_j, x_i)$
if $\eta_l \neq y_i$ and $i \mod q==0$ then
$w_j \leftarrow \beta w_j$
$\eta_g \leftarrow argmax \sigma_j$
if $w_j < \alpha$ then
$Remove(\{e, w\})$
$m \leftarrow m - 1$
if $\eta_g \neq y_i$ then
$m \leftarrow m + 1$
$e_m \leftarrow Create\New\Expert()$
$w_m \leftarrow 1$
return $\eta_g$
```

18

Aggarwal, C. (2007). Data Streams, volume 31. Springer Science & Media, Boston, MA.

Basseville, M. and Nikorov, I. (1993). Detection of Abrupt Changes: Theory and Application, volume 104. Prentice Hall, Englewood Cliffs, NJ.

Bhat, A. (2016). Use the bloom filter, https://www.semetrics.com/blog/use-bloom-filter-b9083fc64/ Accessed 2019.

Chaudhuri, S., Ding, B., and Kandula, S. (2017). Approximate query processing: No silver bullet. In Proceedings of the 2017 ACM International Conference on Management of Data, pp. 511–519. ACM, New York.

Cormode, G. and Muthukrishnan, S. (2004). Improved data stream summaries: The count-min sketch. Journal of Algorithms, 55(1):58–75.

Das, H., Dey, N., and Balas, V. (2019). Real-Time Data Analytics for Large Sensor Data. Academic Press, London, UK.

Das, Y., Das, H., Naik, B., and Behera, H. S. (2019). Big Data Analytics for Intelligent Healthcare. Academic Press, Boston, MA.

Gama, J. (2010). Knowledge Discovery from Data. Chapman and Hall/Boca Raton, FL.

Garcia, K. D., Poeel, M., Kok, J. N., and Carvalho, A. C. (2019). Online clustering for novelty detection and concept drift in data streams. In EPIA Conference on Artificial Intelligence, pp. 448–459. Springer, Cham, Switzerland.

Kelly, M. G., Hand, D. J., and Adams, N. M. (1999). The impact of changing populations classifier performance. In Proceedings of the Fifth SIGKDD International Conference on Knowledge Discovery and Data Mining, pp. 367–371. ACM, New York.

Kifer, D., Ben-David, S., and Gehrke, J. (2004). 数据流中的变化检测. Proceedings of the Thirtieth International Conference on Very Large Data Bases (VLDB '04), volume 30, pp. 180–191. VLDB Endowment.
