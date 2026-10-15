
-   因此，我们为 CapsNet 的训练循环实现了不同的前沿学习率策略，使得 `这些技术针对胶囊结构和 CapsNet 相关参数进行增强`。`[Table 3.1](#chapter3.xhtml#tbl3_1)` 显示了不同优化技术下 LeNet5 与 CapsNet 在 MNIST 数据集上的准确率变化情况。

`[Table 3.1:](#chapter3.xhtml#b3tbl3_1)` 一个表格，总结在应用相同的学习率策略且考虑到适当的功能增强（不违背其优化功能和流程）时，LeNet5 与 CapsNet 的比较差异。表格中每个网络的不同列显示达到最大准确率的训练轮数、以及达到固定学习率策略下网络相同准确度所需的训练轮数。

|  | LeNet5 | CapsNet |
| --- | --- | --- |
| Max Accuracy | Epoch of Max Accuracy | Epochs to Reach Accuracy of Fixed LR | Max Accuracy | Epoch of Max Accuracy | Epochs to Reach Accuracy of Fixed LR |
| Fixed | 98.86% | 17 | 17 | 99.37% | 29 | 29 |
| --- | --- | --- | --- | --- | --- | --- |
| Exp. Decay | 99.24% | 28 | 6 | 99.40% | 12 | 7 |
| OCP | 99.22% | 30 | 19 | 99.38% | 24 | 23 |
| WR | 99.23% | 20 | 4 | 99.44% | 11 | 6 |
| AdaBatch | 99.18% | 19 | 5 | 99.41% | 8 | 5 |

基于此分析，我们得出以下 `关键观察`：

1. `warm restarts` 技术最有前景，因为它能在与固定学习率 CapsNet 相同的准确率（99.37%）的同时，将训练时间缩短 79.31%。

2. 使用 `warm restarts` 进行更长的训练，可使准确率提升 0.07%。

3. `adaptive batch size` 表现出类似的准确率提升（99.41%）和训练轮数。

4. 较小批量的前期 epoch 执行时间相对较长，相比于较大批量的情况。

### 3.1.4 FasTrCaps 框架概述

训练 CapsNet 是一个多目标优化问题，因为我们的目标是最大化准确率，同时最小化训练时间和网络复杂度。`[Figure 3.3](#chapter3.xhtml#fig3_3)` 展示了我们的 `FasTrCaps` 框架的完整处理流程。在描述如何自动集成不同优化措施到训练方法中、以及如何生成用户选定的优化标准的优化 CapsNet 之前，我们先介绍这些优化措施是如何实现并针对 CapsNet 进行增强的，这是实现集成训练框架的必要前提。

![Figure 3.3: FasTrCaps 处理流程: 输入的 CapsNet 经过多个优化阶段，搜索合适的学习率策略、批量大小和复杂度降低，最终输出基于用户选择的优化标准的 Optimized CapsNet。](images/fig3_3.jpg)

`[Figure 3.3:](#chapter3.xhtml#b3fig3_3)` FasTrCaps 处理流程: 输入的 CapsNet 经过多个优化阶段，搜索合适的学习率策略、批量大小和复杂度降低，最终输出基于用户选择的优化标准的 Optimized CapsNet。

#### 3.1.4.1 CapsNet 学习率策略

学习率是提升 CapsNet 训练过程的首要参数。我们在 0.0001 到 0.001 的范围内评估最佳学习率范围。我们在以下参数中使用这些学习率策略：

- `Fixed learning rate`: 0.001

- `Exponential decay`: 起始值 0.001，衰减率 0.96，衰减步数 2000：`l_r = l_r[0] ⋅ 0.96^(current_step/2000)`

- `One cycle policy`: 下限 0.0001，上限 0.001，在训练步数的最后 10%（即 10^(−5)）进行衰减（见 `[Algorithm 2](#chapter3.xhtml#comp03_2)`）

- `Warm restarts`: 下限 0.0001，上限 0.001，周期长度为一个 epoch（见 `[Algorithm 3](#chapter3.xhtml#comp03_3)`）

![](images/comp03_1.jpg)![](images/comp03_2.jpg)

#### 3.1.4.2 批量大小

为实现 `adaptive batch size`，我们在前 3 个 epoch 将批量大小设为 1，之后每 5 个 epoch 增加 3 倍。即用户可以选择一个值 `P`，批量大小将取 2^P、2^(P+1) 和 2^(P+2) 的值（见 `[Algorithm 4](#chapter3.xhtml#comp03_4)`）。

![](images/comp03_3.jpg)

#### 3.1.4.3 CapsNet Decoder 的复杂度

解码器是 CapsNet 的关键组件，缺少解码器会导致准确率下降。ClassCaps 层的输出向量会输入解码器：最大值的向量（胶囊）保持不变，其余 9 个向量被置零（`[Figure 3.4a](#chapter3.xhtml#fig3_4)`）。因此，解码器接收 10 × 16 的数值，其中 9 × 16 为零。于是，我们通过使用压缩的解码器（`[Figure 3.4b](#chapter3.xhtml#fig3_4)`）进行优化，仅保留与产生最高概率的胶囊对应的 1 × 16 输入。原始解码器拥有 1.4M 参数（权重和偏置），而压缩解码器将参数量降低 5%，即 1.3M 参数。

![Figure 3.4: (a) 除最大值的 ClassCaps 输出外，其余全部置零。解码器接收 10 × 16 的输入。 (b) 仅将最大值的 ClassCaps 输出输入压缩解码器，输入为 1 × 16。](images/fig3_4.jpg)

`[Figure 3.4:](#chapter3.xhtml#b3fig3_4)` **(a)** 除最大值的 ClassCaps 输出外，其余全部置零，解码器接收 10 × 16 的输入。 **(b)** 仅将最大值的 ClassCaps 输出输入压缩解码器，输入为 1 × 16。

#### 3.1.4.4 通过重量共享（WS）降低复杂度

`[Algorithm 5](#chapter3.xhtml#comp03_5)` 展示了如何通过为每个 6 × 6 胶囊内的 8 元素向量共享单个张量权重，实现 PrimaryCaps 与 ClassCaps 层之间的权重共享。该方法可将总参数量降低超过 15%，从 8.2 百万降至 6.7 百万。但相比基准 CapsNet，准确率下降约 0.3%。

![](images/comp03_4.jpg)

#### 3.1.4.5 WarmAdaBatch（WAB）

在探索的学习率策略中，`warm restarts` 表现出最有前景的准确率提升。另一方面，`adaptive batch size` 在提供快速收敛的同时取得了良好的权衡。我们提出 `WarmAdaBatch`（见 `[Algorithm 6](#chapter3.xhtml#comp03_6)`），一种混合学习率策略，结合两者的优势，扩大解空间。前 3 个 epoch 批量大小设为 1，之后保持 16 不变。`warm restarts` 的第一个周期持续前 3 个 epoch，第二个周期覆盖其余训练 epoch。

![](images/comp03_5.jpg)

#### 3.1.4.6 优化选择

我们的框架可以根据用户希望改进的参数自动优化 CapsNet 及其训练过程。例如，使用 `WarmAdaBatch` 时，准确率和训练时间会自动协同优化。通过启用 `weight sharing` 并配合 `WarmAdaBatch`，可以在牺牲一定准确率和增加训练时间的前提下，降低模型参数量。

### 3.1.5 FasTrCaps 框架评估

#### 3.1.5.1 实验设置

