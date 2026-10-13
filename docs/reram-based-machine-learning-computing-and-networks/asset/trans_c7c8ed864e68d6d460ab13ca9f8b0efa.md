
此外，可选择性地应用池化操作以从特征中选取最显著的信息，该操作在特征上一个 `![image](images/ch07_si62.gif)` 的连续区域内执行下采样。CNN 网络中常用的池化方案有两种：最大池化和平均池化。最大池化取池化区域的最大值，而平均池化取池化区域的平均值。深度 ResNet 以最大池化开始，以全局平均池化层和一个带有 softmax 层的 `![image](images/ch07_si63.gif)` 路全连接（FC）层结束。为了节省推理时的运行时内存和存储开销，我们可以进行融合，因为 `![image](images/ch07_si64.gif)` 函数与最大池化函数可交换：

```
![image](images/ch07_eqn9.gif)
```

量化最大池化（称为 QPooling）按以下公式应用：

```
![image](images/ch07_eqn10.gif)
```

其中 `![image](images/ch07_si65.gif)` 和 `![image](images/ch07_si66.gif)` 分别为池化前后的特征。

#### 7.2.5 量化深度神经网络概览

带有量化和并行化的深度 ResNet 模型的整体工作流程如 [图 7.3](#Chapter7.html#c07_fig3) 所示。第一层之后，QPooling 将主要工作并将下采样后的特征送入 4-bit QConv。然后每个 4-bit QConv 层在 4-bit 量化特征和权重之间执行量化卷积。接着，QConv 的特征输出将由 QBN 和 QReLUs 函数进一步处理。每三个卷积层后，将在残差块末尾使用 4-bit 量化参数执行加残差操作。

由于所有主要参数和昂贵计算均以 4-bit 量化执行，所提出的 4-bit ResNet 将获得更低的存储开销、更快的速度以及更高的能效。

**算法 7.1：** 使用 4-bit 权重、特征训练量化 ResNet。`![image](images/ch07_si67.gif)` 为层数，`![image](images/ch07_si68.gif)` 为参数梯度。

**要求**：前一层输入 `ak−1` 和前一层权重 `wk`

**保证**：更新后的权重 `w∗ k` 。

1. 计算前向传播：

```
1: for k = 1 : L do
2: wq k ← quantize(wk )
3: a q k−1 ← quantize(ak−1)
4: s q k ← compute(wb k , a q k−1)
5: a qbn k ← compute(s q k ,μ, σ2, γ , β)
6: if max-pooling layer then
7: a qp k ← compute(a qbn k )
8: a qrelu k ← compute(a qp k )
9: else
10: a qrelu k ← compute(a qbn k )
11: end if
12: a q k ← a qrelu k
13: end for
```

2. 计算反向梯度：

```
14: for k = L : 1 do
15: ga q k−1 ← backward(ga q k ,wq k )
16: gwq k ← backward(ga q k , a q k−1)
17: end for
```

3. 累积参数梯度：

```
18: for k = 1 : L do
19: w∗ k ← update(wq k , gwq k )
20: end for
```

#### 7.2.6 训练策略

详细的训练策略见算法 2.5。假设网络具有前馈线性拓扑，计算以高并行性和高效率的 4-bit 量化执行。注意 `![image](images/ch07_si86.gif)` 和 `![image](images/ch07_si87.gif)` 函数代表上述相应的量化和计算方法，`![image](images/ch07_si88.gif)` 函数指定如何在反向传播中计算参数梯度 [254]，`![image](images/ch07_si89.gif)` 函数展示当梯度已知时如何更新参数 [269]。

训练后，可获得所提出的 4-bit ResNet 模型，该模型通过量化实现了高度压缩。与原始 ResNet 相比，量化 ResNet 从大幅压缩和高并行化中获益良多。它将降低复杂度并提升低位宽参数网络的吞吐率，使在存内计算设备上的实现变得更加切合实际。

### 7.3 存内计算设备

本节将介绍可同时用于存储和计算的 ReRAM 交叉阵列设备。它将被用于支持 CMOS-ReRAM 存内计算加速器。第 7.2 节讨论的带有量化的大规模深度 ResNet 将被映射到其上。

#### 7.3.1 ReRAM 交叉阵列

ReRAM [62] 是一款面向未来的存内计算设备。ReRAM 的不同电阻状态可在计算时代表不同参数。除了作为存储内存工作外，ReRAM 交叉阵列还可用于执行逻辑运算 [263]，特别是基于点积的卷积。

[258, 259] 等先前工作通常选择仅有两种非易失性状态的两端子 ReRAM 器件：高电阻态（HRS）和低电阻态（LRS）来构建存内架构，如 [图 7.4](#Chapter7.html#c07_fig4)(a) 所示。然而，当应用网络变得更深、更复杂时，两端子计算导致 ReRAM 交叉阵列性能受限，同时牺牲了网络精度。为实现所提出的 4-bit ResNet-50，我们采用 [270] 中的 ReRAM 模型，该模型具有多位电阻状态。所提出的 ReRAM 器件状态由置位电压 `![image](images/ch07_si90.gif)` 的分布决定。

```
![image](images/PBPC0390-07-f04.jpg)
```

图 7.4 (a) 传统两端子 ReRAM 交叉阵列；(b) 带有 4-bit DAC/ADC 电路的 4-bit ReRAM 交叉阵列

在一个 ReRAM 交叉阵列中，给定每条字线（WL）上的输入探测电压 `![image](images/ch07_si91.gif)`，每条位线（BL）上的电流 `![image](images/ch07_si92.gif)` 成为流过每个 ReRAM 器件电流的自然乘加运算。因此，ReRAM 交叉阵列可内在地执行矩阵-向量乘法。给定输入电压向量 `![image](images/ch07_si93.gif)`，输出向量 `![image](images/ch07_si94.gif)` 可表示为

```
![image](images/ch07_eqn11.gif)
```

其中 `![image](images/ch07_si95.gif)` 为 ReRAM 电阻 `![image](images/ch07_si96.gif)` 的可配置电导，可代表权重的真实值。与传统 CMOS 实现相比，ReRAM 器件可实现更高级别的并行性，并消耗更少的功耗（含待机功耗）。

不同于传统的非量化两端子 ReRAM 交叉阵列，所提出的 4-bit 量化 ReRAM 交叉阵列如 [图 7.4](#Chapter7.html#c07_fig4)(b) 所示，每个 ReRAM 器件配置 4-bit 电阻。此外，WL 上采用新设计的 4-bit DAC 传输数字输入，BL 上采用 4-bit ADC 识别模拟输出。因此，感测到的模拟输出可编码为量化数字信号以产生乘法结果 [237]。

与两端子 ReRAM 交叉阵列相比，4-bit ReRAM 交叉阵列在大规模实现中对 IR-drop（压降）具有更好的鲁棒性，使得线电阻对 IR-drop 影响甚微。此外，由于量化 ReRAM 交叉阵列中仅配置 4-bit 输入，其具有更好的编程精度，可为映射更深、更大规模的网络提供更好的策略。

#### 7.3.2 定制化 DAC 与 ADC 电路
