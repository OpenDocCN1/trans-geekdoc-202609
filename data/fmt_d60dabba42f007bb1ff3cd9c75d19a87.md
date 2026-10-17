
# SGD 不一定按传统意义上“收敛”

然而，我们期望当接近全局极小值时，所有数据点都能被模型很好地描述。因此，无论选择哪个批次，梯度都会很小，参数也就不再发生太大变化。在实践中，SGD 通常配合`学习率调度`使用。学习率 `α` 从一个较高值开始，每 `N` 个周期按一个常数因子衰减。其逻辑是：在训练早期，我们希望算法探索参数空间，在山谷间跳跃以找到一个合理的区域。在后期，我们大致处于正确位置，更关注微调参数，因此减小 `α` 以进行更小幅度的改动。

## 6.3 动量

随机梯度下降的一种常见修改是添加`动量`项。我们用当前批次计算出的梯度与上一步移动方向的加权组合来更新参数：

![c6-fig-5012.jpg](img/c6-fig-5012.jpg)

 (6.11)

其中 `m[t]` 是动量（驱动第 `t` 次迭代的更新），`β ∈ [0, 1)` 控制梯度随时间平滑的程度，`α` 是学习率。

动量计算的递归公式意味着梯度步长是所有先前梯度的无限加权和，权重随时间倒退而变小。如果这些梯度在多次迭代中方向一致，有效学习率会增加；如果梯度方向反复变化，求和项相互抵消，有效学习率则会降低。整体效果是轨迹更平滑，并在山谷中减少了振荡行为（图 6.7）。

***

### 问题 6.10

***

![Figure 6.7 Stochastic gradient descent with momentum. a) Regular stochastic descent takes a very indirect path toward the minimum. b) With a momentum term, the change at the current step is a weighted combination of the previous change and the gradient computed from the batch. This smooths out the trajectory and increases the speed of convergence.](img/c6-fig-0007.jpg)

图 6.7 带动量的随机梯度下降。a) 常规随机下降走了一条非常迂回的路径趋向极小值。b) 有了动量项，当前步骤的变化是先前变化和从批次计算出的梯度的加权组合。这使轨迹更平滑并提高了收敛速度。

### 6.3.1 Nesterov 加速动量

动量项可被视为 SGD 算法下一步将移动位置的粗略预测。Nesterov 加速动量（图 6.8）计算的是在这个预测点而非当前点的梯度：

![c6-fig-5013.jpg](img/c6-fig-5013.jpg)

 (6.12)

此时梯度在 `ϕ[t] − α · m[t]` 处评估。理解这一点的一种方式是：梯度项现在修正了仅由动量提供的路径。

***

### 笔记本 6.4：动量

***

![Figure 6.8 Nesterov accelerated momentum. The solution has traveled along the dashed line to arrive at point 1. A traditional momentum update measures the gradient at point 1, moves some distance in this direction to point 2, and then adds the momentum term from the previous iteration (i.e., in the same direction as the dashed line), arriving at point 3. The Nesterov momentum update first applies the momentum term (moving from point 1 to point 4) and then measures the gradient and applies an update to arrive at point 5.](img/c6-fig-0008.jpg)

图 6.8 Nesterov 加速动量。解沿虚线移动到达点 1。传统动量更新在点 1 处测量梯度，沿该方向移动一段距离到达点 2，然后加上上一迭代的动量项（即与虚线同方向），到达点 3。Nesterov 动量更新先应用动量项（从点 1 移至点 4），然后测量梯度并应用更新到达点 5。

## 6.4 Adam

固定步长的梯度下降具有以下不良特性：它对关联大梯度的参数做大幅调整（此时或许应更谨慎），对关联小梯度的参数做小幅调整（此时或许应探索更远）。当损失曲面在某个方向上比另一个方向陡峭得多时，很难选择一个学习率既能（i）在两个方向上都取得良好进展，又能（ii）保持稳定（图 6.9a–b）。

![Figure 6.9 Adaptive moment estimation (Adam). a) This loss function changes quickly in the vertical direction but slowly in the horizontal direction. If we run full-batch gradient descent with a learning rate that makes good progress in the vertical direction, then the algorithm takes a long time to reach the final horizontal position. b) If the learning rate is chosen so that the algorithm makes good progress in the horizontal direction, it overshoots in the vertical direction and becomes unstable. c) A straightforward approach is to move a fixed distance along each axis at each step so that we move downhill in both directions. This is accomplished by normalizing the gradient magnitude and retaining only the sign. However, this does not usually converge to the exact minimum but instead oscillates back and forth around it (here between the last two points). d) The Adam algorithm uses momentum in both the estimated gradient and the normalization term, which creates a smoother path.](img/c6-fig-0009.jpg)

图 6.9 自适应矩估计。a) 该损失函数在垂直方向变化快，在水平方向变化慢。若用在垂直方向取得良好进展的学习率运行全批次梯度下降，算法需很长时间才能到达最终水平位置。b) 若学习率选为在水平方向取得良好进展，则在垂直方向会超调并变得不稳定。c) 一种直接的方法是每步沿每个轴移动固定距离，使两个方向都向下移动。这通过归一化梯度幅度并仅保留符号来实现。然而，这通常不收敛于精确极小值，而是在其周围来回振荡（此处在最后两点之间）。d) Adam 算法在估计梯度和归一化项中均使用动量，从而产生更平滑的路径。

一种直接的方法是归一化梯度，使我们在每个方向上移动固定距离（由学习率控制）。为此，我们首先测量梯度 `m[t+1]` 和逐点平方梯度 `v[t+1]`：

![c6-fig-5014.jpg](img/c6-fig-5014.jpg)

 (6.13)

然后我们应用更新规则：

![c6-fig-5015.jpg](img/c6-fig-5015.jpg)

 (6.14)

其中平方根和除法均为逐点进行，`α` 是学习率，`ϵ` 是一个防止梯度幅度为零时除以零的小常数。项 `v[t+1]` 是平方梯度，其正平方根用于归一化梯度本身，因此每个坐标方向上仅剩下符号。结果是算法沿每个坐标移动固定距离 `α`，方向由哪个方向是下坡决定（图 6.9c）。该简单算法在两个方向上都能取得良好进展，但除非恰好落在极小值点，否则不会收敛。相反，它会在极小值周围来回反弹。

`自适应矩估计`，或 `Adam`，采用了这一思路，并为梯度估计和平方梯度估计都添加了动量：

![c6-fig-5016.jpg](img/c6-fig-5016.jpg)

 (6.15)

其中 `β` 和 `γ` 是这两个统计量的动量系数。

使用动量等同于对这些统计量的历史进行加权平均。在过程开始时，所有先前的测量值实际上均为零，导致估计值异常地小。因此，我们使用以下规则修正这些统计量：

![c6-fig-5017.jpg](img/c6-fig-5017.jpg)

 (6.16)

由于 `β` 和 `γ` 在范围 `[0, 1)` 内，指数为 `t + 1` 的项随每个时间步变小，分母趋近于 1，因此这种修正的影响逐渐减弱。

最后，我们像以前一样更新参数，但使用修正后的项：

![c6-fig-5018.jpg](img/c6-fig-5018.jpg)

 (6.17)

结果是一种能够收敛到整体极小值、且在参数空间的每个方向上都能取得良好进展的算法。请注意，Adam 通常用于随机设置，其中梯度及其平方是从小批量计算得出的：

![c6-fig-5019.jpg](img/c6-fig-5019.jpg)

 (6.18)

因此在实践中轨迹是有噪声的。

***

### Notebook 6.5：Adam

***

正如我们将在第 7 章看到的，神经网络参数的梯度幅度可能取决于它们在网络中的深度。Adam 有助于补偿这种倾向，并平衡不同层之间的变化。在实践中，Adam 还有一个优势，即对初始学习率不那么敏感，因为它避免了图 6.9a–b 中那样的情况，所以不需要复杂的学习率调度。

## 6.5 训练算法超参数

学习算法、批量大小、学习率调度和动量系数的选择都被视为训练算法的`超参数`；这些直接影响最终模型性能，但不同于模型参数。选择这些参数更多是一门艺术而非科学，通常会用不同的超参数训练许多模型并选择最佳的一个。这被称为`超参数搜索`。我们将在第 8 章回到这个问题。

## 6.6 总结

本章讨论了模型训练。该问题被形式化为寻找对应于损失函数 `L[ϕ]` 极小值的参数 `ϕ`。梯度下降法测量当前参数下损失函数的梯度（即当我们对参数做微小改动时损失如何变化）。然后它沿着损失下降最快的方向移动参数。这会重复进行直到收敛。

对于非线性函数，损失函数可能同时存在局部极小值（梯度下降会陷入其中）和鞍点（梯度下降似乎已收敛但实则不然）。随机梯度下降有助于缓解这些问题。¹ 在每次迭代中，我们使用数据的不同随机子集（一个批次）来计算梯度。这为过程增加了噪声，有助于防止算法陷入参数空间的次优区域。由于每次迭代仅使用数据子集，计算成本也更低。我们了解到添加动量项可以使收敛更高效。最后，我们介绍了 Adam 算法。

本章的思想适用于优化`任意`模型。下一章将解决神经网络训练特有的两个方面。首先，我们将探讨如何计算损失相对于神经网络参数的梯度。这是通过著名的反向传播算法实现的。其次，我们将讨论如何在优化开始前初始化网络参数。如果没有谨慎的初始化，优化所用的梯度可能变得极大或极小，从而阻碍训练过程。

## 注释

### 优化算法

优化算法在工程中广泛使用，通常使用`目标函数`一词而非损失函数或代价函数。梯度下降由柯西发明于 1847 年，随机梯度下降至少可追溯至 Robbins & Monro (1951)。二者的一个现代折衷方案是随机方差缩减下降，其中周期性地计算完整梯度，并穿插随机更新。关于神经网络优化算法的综述可参见 Ruder (2016)、Bottou et al. (2018) 和 Sun (2020)。Bottou (2012) 讨论了 SGD 的最佳实践，包括不放回洗牌。

### 凸性、极小值和鞍点

如果没有任何弦（曲面上两点间的线段）与函数相交，则该函数为凸函数。这可以通过考虑`海森矩阵`（二阶导数矩阵）从代数上进行测试：

![c6-fig-5020.jpg](img/c6-fig-5020.jpg)

 (6.19)

如果海森矩阵对所有可能的参数值均为正定（具有正特征值），则该函数为凸函数；损失函数将呈现光滑碗状（如图 6.1c 所示），因此训练将相对容易。将存在单一全局极小值，且没有局部极小值或鞍点。

***

### Appendix B.3.7：特征值

***

对于任意损失函数，梯度为零处海森矩阵的特征值允许我们将该位置分类为：(i) 极小值（特征值均为正），(ii) 极大值（特征值均为负），或 (iii) 鞍点（正特征值对应极小值方向，负特征值对应极大值方向）。

### 线搜索

固定步长的梯度下降效率低下，因为移动距离完全取决于梯度幅度。当函数变化快时移动距离长（此时或许应更谨慎），而函数变化慢时移动距离短（此时或许应探索更远）。因此，梯度下降法通常结合线搜索过程，在期望方向上对函数进行采样，以尝试找到最优步长。一种此类方法是区间搜索（图 6.10）。梯度下降的另一个问题是，在下降山谷时倾向于导致低效的振荡行为（例如图 6.5a 中的路径 1）。

![图 6.10 使用括间法进行线搜索。a) 当前解位于位置 a（橙点），我们希望搜索区域 [a, d]（灰色阴影区域）。我们在搜索区域内部定义两个点 b、c 并在这些点处评估损失函数。此处 L[b] > L[c]，因此我们排除范围 [a, b]。b) 我们现在在细化后的搜索区域中重复此过程，并发现 L[b] < L[c]，因此我们排除范围 [c, d]。c) 我们重复此过程，直到该最小值被紧密括住。](images/c6-fig-0010.jpg)

图 6.10 使用括间法进行线搜索。a) 当前解位于位置 `a`（橙点），我们希望搜索区域 `[a, d]`（灰色阴影区域）。我们在搜索区域内部定义两个点 `b`、`c` 并在这些点处评估损失函数。此处 `L[b] > L[c]`，因此我们排除范围 `[a, b]`。b) 我们现在在细化后的搜索区域中重复此过程，并发现 `L[b] < L[c]`，因此我们排除范围 `[c, d]`。c) 我们重复此过程，直到该最小值被紧密括住。

#### 超越梯度下降

已经开发出许多算法来解决梯度下降的问题。其中最著名的是牛顿法，它利用海森矩阵的逆来考虑曲面的曲率；如果函数的梯度变化迅速，则应用更谨慎的更新。这种方法消除了对线搜索的需求，且不会遭受振荡行为的困扰。然而，它也有自己的问题；在其最简单的形式中，它朝最近的极值移动，但如果我们更接近山顶而非山谷底，这可能是一个最大值。此外，当参数数量很大时（如在神经网络中），计算逆海森矩阵是难以处理的。

---

### 问题 6.11

---

#### SGD 的性质

当学习率趋近于零时，SGD 的极限是一个随机微分方程。Jastrzębski 等人（2018）表明，该方程依赖于学习率与批量大小的比率，并且该比率与所发现极小值的宽度之间存在关系。更宽的极小值被认为更可取；如果测试数据的损失函数相似，则参数估计中的微小误差对测试性能影响甚微。He 等人（2019）证明了 SGD 的一个泛化界，该界与批量大小与学习率的比率呈正相关。他们在不同架构和数据集上训练了大量模型，并发现了经验证据：当批量大小与学习率的比率较低时，测试准确率会提高。Smith 等人（2018）和 Goyal 等人（2018）也确定了批量大小与学习率的比率对泛化很重要（见图 20.10）。

#### 动量

利用动量加速优化的想法可追溯至 Polyak（1964）。Goh（2017）深入讨论了动量的性质。Nesterov 加速梯度法由 Nesterov（1983）引入。Nesterov 动量首次由 Sutskever 等人（2013）在随机梯度下降的背景下应用。

#### 自适应训练算法

AdaGrad（Duchi 等人，2011）是一种优化算法，它通过为每个参数分配不同的学习率，来解决某些参数可能需要比其他参数移动得更远的可能性。AdaGrad 使用每个参数的累积平方梯度来衰减其学习率。这有一个缺点，即学习率会随时间减小，并且学习可能在找到最小值之前就停止。RMSProp（Hinton 等人，2012a）和 AdaDelta（Zeiler，2012）修改了该算法，通过递归更新平方梯度项来帮助防止这些问题。

迄今为止，使用最广泛的自适应训练算法是自适应矩估计或 Adam（Kingma & Ba，2015）。它结合了动量（对梯度向量随时间进行平均）以及 AdaGrad、AdaDelta 和 RMSProp（使用平滑的平方梯度项来修改每个参数的学习率）的思想。Adam 算法的原始论文为凸损失函数提供了收敛证明，但 Reddi 等人（2018）发现了一个反例，他们开发了一个称为 AMSGrad 的 Adam 修正版本，该版本确实收敛。当然，在深度学习中，损失函数是非凸的，Zaheer 等人（2018）随后开发了一种称为 YOGI 的自适应算法，并证明了它在这种情况下收敛。尽管存在这些理论上的异议，原始 Adam 算法在实践中效果良好且被广泛使用，不小因为它在广泛的超参数范围内表现良好并能取得快速的初始进展。

自适应训练算法的一个潜在问题是，学习率基于观察到的梯度的累积统计量。在训练开始时，当样本很少时，这些统计量可能非常嘈杂。这可以通过 `learning rate warm-up`（学习率预热）（Goyal 等人，2018）来补救，即在前几千次迭代中逐渐增加学习率。另一种解决方案是修正 Adam（Liu 等人，2021a），它以一种有助于避免高方差的方式随时间逐渐改变动量项。Dozat（2016）将 Nesterov 动量融入了 Adam 算法。

#### SGD 与 Adam
