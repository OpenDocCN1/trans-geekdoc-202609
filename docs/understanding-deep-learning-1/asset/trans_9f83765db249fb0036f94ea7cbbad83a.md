
第一项表明，如果在样本密度 `Pr(x**)` 较高的地方，混合分布 `(Pr(x**) + Pr(x))/2` 具有较高概率，则距离将很小。换句话说，它惩罚有样本 `x**` 但无真实样本 `x` 的区域；它强制要求 `quality`（质量）。第二项表明，如果在真实密度 `Pr(x)` 较高的地方，混合分布 `(Pr(x**) + Pr(x))/2` 具有较高概率，则距离将很小。换句话说，它惩罚有真实样本但无生成样本的区域。它强制要求 `coverage`（覆盖度）。参考公式 15.6，我们看到第二项不依赖于生成器，因此生成器并不关心覆盖度；它乐于准确地生成可能样本的一个子集。这是模式丢失的推定原因。

***

附录 C.5.1

Kullback-Leibler 散度（KL 散度）

***

### 15.2.2 梯度消失

在上一节中，我们看到当判别器达到最优时，损失函数最小化生成样本与真实样本之间距离的一种度量。然而，使用概率分布之间的这种距离作为优化 GAN 的标准存在一个潜在问题。如果概率分布完全不相交，则该距离为无穷大，对生成器的任何微小改动都不会降低损失。当我们考虑原始公式时，也可以看到相同的现象；如果判别器能完美区分生成样本和真实样本，则生成数据的任何微小改动都不会改变分类得分（[图 15.6](#c015.xhtml#c15-fig-0006)）。

![Figure 15.6 Problem with GAN loss function. If the generated samples (orange arrows) are easy to distinguish from the real examples (cyan arrows), then the discriminator (sigmoid) may have a very shallow slope at the positions of the samples; hence, the gradient to update the parameter of the generator may be tiny.](images/c15-fig-0006.jpg)

[图 15.6](#c015.xhtml#c15-fig-0006a) GAN 损失函数的问题。如果生成样本（橙色箭头）易于与真实样本（青色箭头）区分，则判别器（Sigmoid 函数）在样本位置处的斜率可能非常平缓；因此，用于更新生成器参数的梯度可能非常微小。

不幸的是，生成样本和真实样本的分布*确实可能*不相交；生成样本位于大小为潜在变量 `z` 的子空间中，而由于产生数据的物理过程，真实样本也位于低维子空间中（图 1.9）。这些子空间之间可能几乎没有或完全没有重叠，结果导致梯度非常小或没有梯度。

[图 15.7](#c015.xhtml#c15-fig-0007) 提供了支持这一假设的实证证据。如果冻结 DCGAN 生成器并反复更新判别器以提高其分类性能，生成器的梯度会减小。简而言之，判别器和生成器的质量之间存在着非常微妙的平衡；如果判别器变得太好，生成器的训练更新就会被削弱。

![Figure 15.7 Vanishing gradients in the generator of a DCGAN. The generator is frozen after 1, 10, and 25 epochs, and the discriminator is trained further. The gradient of the generator decreases rapidly (note log scale); if the discriminator becomes too accurate, the gradients for the generator vanish. Adapted from Arjovsky & Bottou (2017).](images/c15-fig-0007.jpg)

[图 15.7](#c015.xhtml#c15-fig-0007a) DCGAN 生成器中的梯度消失。生成器在 1、10 和 25 个 epoch 后被冻结，判别器继续训练。生成器的梯度迅速减小（注意对数刻度）；如果判别器变得太准确，生成器的梯度就会消失。改编自 Arjovsky & Bottou (2017)。

### 15.2.3 Wasserstein 距离

前几节表明：(i) GAN 损失可以用概率分布之间的距离来解释；(ii) 当生成样本太容易与真实样本区分时，该距离的梯度变为零。显而易见的前进方向是选择一个具有更好性质的距离度量。

*Wasserstein* 距离（对于离散分布称为 *earth mover's* 距离，即“推土机距离”）是将概率质量从一个分布转移以创建另一个分布所需的工作量。这里，“工作”被定义为质量乘以移动距离。这听起来立刻更有希望了；即使分布不相交，Wasserstein 距离也定义良好，并且随着它们相互靠近而平滑减小。

### 15.2.4 离散分布的 Wasserstein 距离

Wasserstein 距离对于离散分布最容易理解（[图 15.8](#c015.xhtml#c15-fig-0008)）。考虑定义在 `K` 个箱上的分布 `Pr(x = i)` 和 `q(x = j)`。假设将一个单位质量从第一个分布的箱 `i` 移动到第二个分布的箱 `j` 有一个代价 `P[ij]`；这个代价可能是索引之间的绝对差值 `|i - j|`。移动的量构成 *transport plan*（传输计划），并存储在矩阵 `P` 中。

![Figure 15.8 Wasserstein or earth mover's distance. a) Consider the discrete distribution Pr(x = i). b) We wish to move the probability mass to create the target distribution q(x = j). c) The transport plan P identifies how much mass will be moved from i to j. For example, the cyan highlighted square p54 indicates how much mass will be moved from i = 5 to j = 4. The elements of the transport plan must be non-negative, the sum over j must be Pr(x = i), and the sum over i must be q(x = j). Hence P is a joint probability distribution. d) The distance matrix between elements i and j. The optimal transport plan P minimizes the sum of the pointwise product of P and the distance matrix (termed the Wasserstein distance). Hence, the elements of P tend to lie close to the diagonal where the distance cost is lowest. Adapted from Hermann (2017).](images/c15-fig-0008.jpg)

[图 15.8](#c015.xhtml#c15-fig-0008a) Wasserstein 距离或推土机距离。a) 考虑离散分布 `Pr(x = i)`。b) 我们希望移动概率质量以创建目标分布 `q(x = j)`。c) 传输计划 `P` 标识了将从 `i` 移动到 `j` 的质量有多少。例如，青色高亮的方块 `p[54]` 表示将从 `i = 5` 移动到 `j = 4` 的质量有多少。传输计划的元素必须为非负，对 `j` 求和必须等于 `Pr(x = i)`，对 `i` 求和必须等于 `q(x = j)`。因此 `P` 是一个联合概率分布。d) 元素 `i` 和 `j` 之间的距离矩阵。最优传输计划 `P` 最小化 `P` 与距离矩阵逐点乘积的和（称为 Wasserstein 距离）。因此，`P` 的元素倾向于位于距离代价最低的对角线附近。改编自 Hermann (2017)。

Wasserstein 距离定义为：

![c15-fig-5016.jpg](images/c15-fig-5016.jpg)

(15.10)

受以下约束：

![c15-fig-5017.jpg](images/c15-fig-5017.jpg)

(15.11)

换句话说，Wasserstein 距离是一个将一个分布的质量映射到另一个分布的约束最小化问题的解。这很不方便，因为每次计算距离时，我们都必须对元素 `P[ij]` 求解这个最小化问题。幸运的是，这是一个标准问题，对于小型方程组很容易求解。它是*原始形式*下的*线性规划问题*。

![](images/c15-fig-5018.jpg)
