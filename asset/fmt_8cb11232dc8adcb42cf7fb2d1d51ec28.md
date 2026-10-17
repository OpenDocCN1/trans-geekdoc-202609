
`i`是样本，而`m`是特征总数。

由于只最小化训练损失可能会导致网络过拟合，为了缓解过拟合，我们考虑了网络复杂度。如 [9] 所示，两个目标`f_1`与`f_2`是相互冲突的，因为较低的训练损失通常对应更高的复杂度。然而，由于进化多目标优化提供的精密选择策略可以在两个目标之间取得良好平衡的解，并获得训练损失可以且无过拟合的网络。

#### 9.2.3.2 优解的更新

一旦完成进化优化过程，为了最终利用设计了更新优解的策略。具体而言，移除群体中的支配解，然后对每个非支配解使用`SGD` [46] 以 0.1 的学习率进行一个 epoch 的微调。值得注意的是，这里只更新非零权重，而零权重保持不变。这种所提的技巧可以在保持网络稀疏性的同时降低训练损失，我们以后称之为稀疏随机梯度下降（`SSGD`）。

#### 9.2.3.3 最终解的选择

最后但重要的是，需要从微调后的群体中选择一个解作为输出。直觉上，选择具有最低训练损失或复杂的解是不合理的，因为前者倾向于过拟合训练集，而后者通常没有训练充分。由于群体中膝部区域的解在两个目标之间有更好的平衡 [9]，它们在许多场景中通常更青睐 [10, 31]。基于此想法，所提出的`GEMONN`根据以下标准选择解`p`：

![Layout 1st Row 1st Column upper X 1 2nd Column equals StartSet bold x vertical-bar int left-parenthesis log Subscript 10 Baseline f 2 left-parenthesis bold x right-parenthesis right-parenthesis minus int left-parenthesis log Subscript 10 Baseline f 2 left-parenthesis bold x Superscript plus Baseline right-parenthesis right-parenthesis less-than 1 EndSet comma, 2nd Row 1st Column upper X 2 2nd Column equals left-brace bold x vertical-bar f 2 left-parenthesis bold x right-parenthesis less-than 2 asterisk f 2 left-parenthesis bold x Superscript plus Baseline right-parenthesis comma, bold x element-of upper X 1 right-brace comma 3rd Row 1st Column bold p 2nd Column equals arg min Underscript bold x Endscripts gamma left-parenthesis bold x right-parenthesis comma, bold element-of upper X 2 period.](img/c09-math-0018.png)

第一个准则旨在寻找训练损失数量与`x⁺`相同数量级的解，其中`x⁺`是种群中训练损失最低的解，即`x⁺ = arg minₓ f₂(x)`。第二个准则也旨在保证所选解的训练性能。第三个准则用于根据`γ(x)`寻找最终解，该函数计算了解的左右邻居 [47] 之间的角度。

#### 9.2.3.4 时间复杂度分析

提出的`GEMONN`的时间复杂度主要由两个部分决定，即梯度计算和`NSGA-II`的优化过程。根据 [48]，计算梯度的时间复杂度为`O(Nm)`，其中`N`和`m`分别是批量大小和维度。`NSGA-II`每一代的时间复杂度为`O(p²)` [44]，其中`p`是种群规模。因此，`GEMONN`的总时间复杂度为`O(Nmp + p²)`。由于通常情况下`Nm ≫ p`，`GEMONN`的时间复杂度可以认为是`O(Nmp)`，这与`SGD` [48] 相同。

### 9.2.4 实验研究

#### 9.2.4.1 待训练的神经网络

提出的`GEMONN`的性能在四种神经网络上进行了验证，包括`AE`、`SAE` [49]、`LSTM` [50] 和`CNN` [18]。下面将给出这四种神经网络训练的简要介绍。

### 1. 自动编码器 (AE)

作为一种具有单隐藏层的全连接（`FC`）前馈神经网络，`AE`通常用于降维，其输出被期望与输入相同，且隐藏层可以被视为训练样本的有意义且降维的表示。因此，`AE`可以以无监督的方式进行训练，并采用了许多现有的进化算法（`EAs`）来训练它 [10, 11, 31]。为了通过所提出的`GEMONN`训练`AE`，采用了`MSE`作为第二个目标。此外，在隐藏层中使用了`sigmoid`激活函数。

### 2. 堆叠自动编码器 (SAE)

通过使用`AE`作为构建模块，`SAE`可以逐层减少训练样本并在最后进行分类。通过贪心逐层训练过程，可以适当处理不同层之间的权重依赖关系，并单独优化每一层的权重。`SAE`的训练包含两个阶段 [11, 51]，即预训练和微调。预训练阶段通过最小化重构误差来训练一组具有不同数量隐藏节点的`AEs`。然后，将这些`AEs`堆叠在一起并在末尾接上一个`FC`层，微调阶段则优化所有权重以最小化分类误差。为了通过所提出的`GEMONN`训练`SAE`，在预训练阶段采用`MSE`作为第二个目标，在微调阶段采用`CE`。

### 3. 长短期记忆网络 (LSTM)

`LSTM`是目前许多深度学习任务中最流行的循环神经网络之一，其层与层之间的连接比前馈神经网络复杂得多。由于`LSTM`中的所有权重都应该一起优化，因此它比逐层优化权重的`SAE`困难得多，且目前还没有现有的进化方法应用于它。为了证明所提出的遗传算子在不进行降维的情况下训练`DNNs`的有效性，我们还使用所提出的`GEMONN`来训练`LSTM`，其结构所示于图 9.6(a)，其中采用`CE`作为第二个目标。

### 4. 卷积神经网络 (CNNs)

`CNNs`也是许多深度学习任务的强大神经网络，尤其是计算机视觉。为了研究`GEMONN`训练`CNNs`的能力，我们考虑了`LeNet-5` [52] 及其变体（称为`LeNet-deeper`），后者具有更多的卷积操作和更多的滤波器，所示于图 9.6(c)，其中每个卷积操作后都紧跟一个`ReLu` [53] 激活函数。为了研究更深层`CNN`的结果，使用了一种通道设置为 [8, 16, 32, 55] 的`Vgg16`变体，其最后两个`FC`层设置为 512 和 256。此外，还考虑了一种有效的基于单元的`CNN` [56]，称为`Cell-CNN`，其普通单元和缩减单元被设置为 [18] 中发现的最优架构，如图 9.6(b) 和 (d) 所示。为了方便`Cell-CNN`的训练，如 [24] 所示，该神经网络包含 6 个单元，所有节点共有 16 个滤波器，以及一个损失权重为 0.4 的辅助头分类器。

![图 9.6 使用的神经网络结构，包括 LSTM、LeNet-5 及其变体（更深且更多滤波器）以及基于单元的 CNN。(a) LSTM。(b) Cell-CNN（普通单元）。(c) LeNet-5 及其变体。(d) Cell-CNN（缩减单元）。](img/c09f006.png)

图 9.6 使用的神经网络结构，包括`LSTM`、`LeNet-5`及其变体（更深且更多滤波器），以及基于单元的`CNN`。(a) `LSTM`。(b) `Cell-CNN`（普通单元）。(c) `LeNet-5`及其变体。(d) `Cell-CNN`（缩减单元）。(d) 结构

#### 9.2.4.2. 基准数据集

如表 9.1 所示，实验采用了 17 个广泛使用的数据集。第一个数据集包括`MNIST` [52] 及其变体 [57] 以及`Cifar10` [58]，用于`AE`和`SAE`。接下来的六个数据集收集自`UCR`归档 [59]，用于`LSTM`。此外，`Cifar10` [58] 用于`CNNs`。![表 9.1](img/c09-i057)

#### 9.2.4.3. 对比算法

由于实验是在`AE`、`SAE`和`CNNs`上进行的，不同的神经网络需要不同的对比方法。

##### AE 的算法

训练`AE`选择了以下对比方法：

* `SGD` [4]：随机梯度下降；
* `Adam` [6]：`Adam`算法；
* `NSGA-II` [44]：带有`SBX`算子的`NSGA-II`；
* `NSGA-II (+gradient)`：基于`NSGA-II`，在每一代通过`SGD`更新所有种群；
* `NSGA-II (+gradient 0)`：基于`NSGA-II`，在每一代通过`SSGD`更新所有种群；
* `GEMONN (-SSGD)`：不通过`SSGD`更新帕托最优解的`GEMONN`；
