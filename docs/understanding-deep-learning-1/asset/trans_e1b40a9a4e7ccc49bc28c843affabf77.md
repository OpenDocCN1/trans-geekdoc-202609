
由于最佳参数使该表达式最小化，我们称之为*最小二乘*损失。平方运算意味着偏差的方向（即直线位于数据上方还是下方）并不重要。对于这一选择也存在理论依据，我们将在第 5 章中回到这一点。

损失 *L* 是参数 `ϕ` 的函数；当模型拟合较差时（[图 2.2b,c](#c002.xhtml#c2-fig-0002)）它会较大，而当拟合良好时（[图 2.2d](#c002.xhtml#c2-fig-0002)）它会较小。从这个角度来看，我们称 `L[ϕ]` 为*损失函数*或*代价函数*。目标是找到使该量最小化的参数 `ϕ̂`：

```
(2.6)
```

***

### 笔记本 2.1：监督学习

***

只有两个参数（y 轴截距 `ϕ[0]` 和斜率 `ϕ[1]`），因此我们可以计算所有值组合的损失，并将损失函数可视化为一个曲面（[图 2.3](#c002.xhtml#c2-fig-0003)）。“最佳”参数位于该曲面的最小值处。

***

### 问题 2.1–2.2

***

![Figure 2.3 Loss function for linear regression model with the dataset in figure 2.2a. ¶ a) Each combination of parameters ϕ = [ϕ0, ϕ1] has an associated loss. The resulting loss function L[ϕ] can be visualized as a surface. The three circles represent the three lines from figure 2.2b–d. b) The loss can also be visualized as a heatmap, where brighter regions represent larger losses; here we are looking straight down at the surface in (a) from above and gray ellipses represent isocontours. The best fitting line (figure 2.2d) has the parameters with the smallest loss (green circle).](images/c2-fig-0003.jpg)

[图 2.3](#c002.xhtml#c2-fig-0003a) 使用 [图 2.2a](#c002.xhtml#c2-fig-0002) 中数据集的线性回归模型的损失函数。¶ a) 参数 `ϕ` = [`ϕ[0]`, `ϕ[1]`] 的每种组合都有一个相关的损失。由此产生的损失函数 `L[ϕ]` 可以可视化为一个曲面。三个圆圈代表 [图 2.2b–d](#c002.xhtml#c2-fig-0002) 中的三条线。b) 损失也可以可视化为热力图，其中更亮的区域代表更大的损失；这里我们从上方垂直向下俯视 (a) 中的曲面，灰色椭圆代表等高线。最佳拟合线（[图 2.2d](#c002.xhtml#c2-fig-0002)）具有损失最小的参数（绿色圆圈）。

### 2.2.3 训练

寻找使损失最小化的参数的过程称为*模型拟合*、*训练*或*学习*。基本方法是随机选择初始参数，然后通过“沿着”损失函数“向下走”来改进它们，直到到达底部（[图 2.4](#c002.xhtml#c2-fig-0004)）。实现这一点的一种方法是测量当前位置处曲面的梯度，并沿最陡峭的下坡方向迈出一步。然后我们重复此过程，直到梯度变平，无法再进一步改进。[²](#c002.xhtml#c2-fn-0002)

![Figure 2.4 Linear regression training. The goal is to find the y-intercept and slope parameters that correspond to the smallest loss. a) Iterative training algorithms initialize the parameters randomly and then improve them by “walking downhill” until no further improvement can be made. Here, we start at position 0 and move a certain distance downhill (perpendicular to the contours) to position 1. Then we re-calculate the downhill direction and move to position 2. Eventually, we reach the minimum of the function (position 4). b) Each position 0–4 from panel (a) corresponds to a different y-intercept and slope and so represents a different line. As the loss decreases, the lines fit the data more closely.](images/c2-fig-0004.jpg)

[图 2.4](#c002.xhtml#c2-fig-0004a) 线性回归训练。目标是找到对应最小损失的 y 轴截距和斜率参数。a) 迭代训练算法随机初始化参数，然后通过“向下走”来改进它们，直到无法再进一步改进。这里，我们从位置 0 开始，沿下坡方向（垂直于等高线）移动一段距离到位置 1。然后我们重新计算下坡方向并移动到位置 2。最终，我们到达函数的最小值处（位置 4）。b) 面板 (a) 中的位置 0–4 每个都对应不同的 y 轴截距和斜率，因此代表不同的线。随着损失减小，线条对数据的拟合更紧密。

### 2.2.4 测试

训练好模型后，我们想知道它在现实世界中的表现如何。我们通过在单独的*测试数据*集上计算损失来实现这一点。预测准确度*泛化*到测试数据的程度部分取决于训练数据的代表性和完整性。然而，这也取决于模型的表达能力。像直线这样的简单模型可能无法捕捉输入和输出之间的真实关系。这被称为*欠拟合*。相反，一个表达能力很强的模型可能会描述训练数据中那些非典型的统计特性，从而导致异常的预测。这被称为*过拟合*。

## 2.3 总结

监督学习模型是一个函数 `y = f[x, ϕ]`，它将输入 `x` 映射到输出 `y`。具体的映射关系由参数 `ϕ` 决定。为了训练模型，我们在训练数据集 `{x[i], y[i]}` 上定义一个损失函数 `L[ϕ]`。这量化了模型预测 `f[x[i], ϕ]` 与观测输出 `y[i]` 之间的不匹配程度，作为参数 `ϕ` 的函数。然后我们寻找使损失最小化的参数。我们在另一组测试数据上评估模型，以查看它对新输入的泛化能力如何。

第 3–9 章将展开阐述这些思想。首先，我们解决模型本身的问题；线性回归有一个明显的缺点，即它只能将输入和输出之间的关系描述为一条直线。浅层神经网络（第 3 章）仅比线性回归稍微复杂一些，但能描述大得多的输入/输出关系族。深层神经网络（第 4 章）表达能力相当，但可以用更少的参数描述复杂函数，且在实践中效果更好。

第 5 章研究不同任务的损失函数，并揭示最小二乘损失的理论基础。第 6 章和第 7 章讨论训练过程。第 8 章讨论如何衡量模型性能。第 9 章探讨*正则化*技术，旨在提高该性能。

## 注释

**损失函数与代价函数：** 在大部分机器学习文献及本书中，损失函数和代价函数这两个术语可互换使用。然而，更严格地说，损失函数是与单个数据点相关的项（即方程 2.5 右侧的每个平方项），而代价函数是被最小化的总体量（即方程 2.5 右侧的整体）。代价函数可以包含不与单个数据点相关的额外项（见第 9.1 节）。更一般地，*目标函数*是指任何待最大化或最小化的函数。

**生成模型与判别模型：** 本章中的模型 `y = f[x, ϕ]` 是*判别模型*。这些模型从现实世界的测量值 `x` 中进行输出预测 `y`。另一种方法是构建*生成模型* `x = g[y, ϕ]`，其中现实世界的测量值 `x` 作为输出 `y` 的函数被计算得出。

***

### 问题 2.3

***
