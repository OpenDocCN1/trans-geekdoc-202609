
10: 注意：{对于自编码器层，`![image](images/ch04_si273.gif)` 是激活矩阵 `![image](images/ch04_si274.gif)` (`![image](images/ch04_si275.gif)`)。对于决策层，`![image](images/ch04_si276.gif)` 是标签矩阵 `![image](images/ch04_si277.gif)`。

11: `end if`

12: `end for`

TNN 旨在开发高维权重并使用张量列车分解方法对其进行压缩。例如，一个 `![image](images/ch04_si278.gif)` 全连接层可以表示为一个 4D `![image](images/ch04_si279.gif)` 张量。因此，我们不生成随机输入权重 `![image](images/ch04_si280.gif)`，而是通过指定每个核 `![image](images/ch04_si282.gif)` 的秩来生成一个低秩张量 `![image](images/ch04_si281.gif)`。然后输入权重可以通过 ([4.23](#Chapter4.html#c04_eqn23)) 生成，其中每个核 `![image](images/ch04_si283.gif)` 都是随机生成的。

正如在通用神经网络中所讨论的，TNN 的训练需要在张量列车数据格式下求解一个最小二乘（LS）问题。对于 ([4.29](#Chapter4.html#c04_eqn29)) 中的输出权重 `![image](images/ch04_si284.gif)`，我们提出了一种基于张量列车的最小二乘训练方法，使用 MALS 算法（在量子动力学中也称为密度矩阵重整化群）[203,204]。`![image](images/ch04_si285.gif)` 最小化的 MALS 算法工作流程如下。

对于输出权重 `![image](images/ch04_si286.gif)`，我们有两种潜在的解决方案来实现张量列车数据格式。一种直接的方法是求解通用矩阵最小二乘问题，然后按照迭代截断奇异值分解（SVD）算法 [197] 将其重塑为高维张量。这类似于高阶 SVD，且在相对较小的压缩率下性能退化显著。相反，我们提出了一种基于张量列车的最小二乘训练方法，使用 MALS 算法（在量子动力学中也称为密度矩阵重整化群）[203,204]。

1.  **初始化**：随机初始化核 `![image](images/ch04_si287.gif)` 并设置 `![image](images/ch04_si288.gif)`。该过程与 [算法 4.3](#Chapter4.html#c04_stat3) 中的步骤 3、4 相同。

2.  **核扫动**：在固定其他核的情况下优化核 `![image](images/ch04_si289.gif)`。从 `![image](images/ch04_si290.gif)` 到 `![image](images/ch04_si291.gif)` 进行从左到右的扫动。

3.  **生成超级核**：创建超级核 `![image](images/ch04_si292.gif)` 并通过最小化最小二乘问题 `![image](images/ch04_si293.gif)` 来求解它，重塑 `![image](images/ch04_si294.gif)` 和 `![image](images/ch04_si295.gif)` 以适应矩阵-矩阵乘法^([3](#Chapter4.html#ch04-03))。

4.  **分割超级核**：对 `![image](images/ch04_si299.gif)` 进行 SVD 分解，令 `![image](images/ch04_si300.gif)` 和 `![image](images/ch04_si301.gif)`。`![image](images/ch04_si302.gif)` 被确定，`![image](images/ch04_si303.gif)` 被更新。也可以通过移除较小的奇异值来执行截断 SVD 以降低秩。

5.  **扫动终止**：如果达到最大扫动次数或误差小于要求，则终止。

低秩初始化对于使每个核具有较小的秩 `![image](images/ch04_si304.gif)` 非常重要。每次超级核生成都是求解最小二乘问题的过程。`![image](images/ch04_si305.gif)` 的 LS 复杂度为 `![image](images/ch04_si306.gif)` [204]，而 SVD 压缩需要 `![image](images/ch04_si307.gif)`，其中 `![image](images/ch04_si308.gif)`、`![image](images/ch04_si309.gif)` 和 `![image](images/ch04_si310.gif)` 分别是激活矩阵 `![image](images/ch04_si311.gif)` 的秩、核 `![image](images/ch04_si312.gif)` 的最大秩和 `![image](images/ch04_si313.gif)` 的最大模态尺寸。通过使用截断 SVD，我们可以自适应地降低每个核的秩，以降低计算复杂度并节省内存存储。

这种张量化有利于实现大型神经网络。首先，通过执行张量化，神经网络的规模可以被压缩。此外，通过采用较小的张量秩，计算负载也可以减少。其次，权重矩阵的张量化可以将大矩阵分解为许多小的张量核矩阵，这可以有效减少 ReRAM 的配置时间。最后，小矩阵的乘法可以在 ReRAM 上以高度并行的方式执行，以加速大型神经网络的处理时间。

[¹](#Chapter4.html#ch04_01) 感兴趣的读者可参考 [197,198] 了解更多关于张量列车数据格式的细节。

[²](#Chapter4.html#ch04_02) 为便于说明，我们忽略了偏置项。

[³](#Chapter4.html#ch04_03) 关于 `![image](images/ch04_si296.gif)` 和 `![image](images/ch04_si297.gif)` 的详细信息可参见 [203,204]。由于每个核都是 3D 张量，因此需要置换为 2D 矩阵。在不滥用符号的前提下，我们用 `![image](images/ch04_si298.gif)` 来表示它。

## 第 5 章

**XIMA：ReRAM 内机器学习架构**

### 5.1 基于 ReRAM 网络的 ML 运算

在不同的硬件架构中，基于电阻式随机存取存储器（ReRAM）的架构被认为是在面积、功耗和计算延迟方面最高效的架构之一。在本章中，我们将介绍两种类型的 ReRAM 神经网络，重点关注密集矩阵乘法运算。ReRAM 交叉阵列网络可用作矩阵-向量乘法加速器，并用于说明详细映射。耦合 ReRAM 振荡器网络可应用于低功耗和高吞吐率的 L2 范数计算。

#### 5.1.1 ReRAM 交叉阵列网络

本节描述二进制 ReRAM 交叉阵列上的矩阵-向量乘法。这是各种数据分析应用（如压缩感知和机器学习 (ML)）中最常用的运算。例如，特征提取可以通过乘以 [205] 中的伯努利矩阵来实现。

矩阵乘法可以表示为 `![image](images/ch05_stripin_si1.gif)`，其中 `![image](images/ch05_stripin_si2.gif)` 和 `![image](images/ch05_stripin_si3.gif)` 是被乘矩阵，`![image](images/ch05_stripin_si4.gif)` 是结果矩阵。

##### 5.1.1.1 ReRAM 交叉阵列用于矩阵-向量乘法的映射

本节介绍矩阵乘法在 ReRAM 架构上的硬件映射。所需的逻辑是由 ReRAM 交叉阵列实现的矩阵-向量乘法器。通常，可以利用位线（BL）上的电流汇聚来实现矩阵-向量乘法，然后使用基于 ReRAM 的闪存模数转换器（ADC）进行格式转换。这里介绍了一种三步 ReRAM 交叉阵列二进制矩阵-向量乘法器，其中 ReRAM 交叉阵列的输入和输出均为二进制数据，无需 ADC。三个 ReRAM 交叉阵列步骤——并行数字化、异或（XOR）和编码——将详细介绍如下。由于一个 ReRAM 交叉阵列的输出可以连接到另一个 ReRAM 交叉阵列的输入，因此可以在逻辑块中利用多个 ReRAM 阵列进行映射。这里使用符号 `![image](images/ch05_stripin_si5.gif)` 来表示二进制矩阵-向量乘法的结果。因此，`![image](images/ch05_stripin_si6.gif)` 遵循

`![image](images/ch05_stripin_si165.gif)`

其中 `![image](images/ch05_stripin_si7.gif)` 是最大结果。为了更清晰地说明三步过程，让我们考虑以下矩阵-向量乘法作为一个说明性示例：

`![image](images/ch05_stripin_si166.gif)`

三步过程后的输出将显示在此，这里 `![image](images/ch05_stripin_si8.gif)` 和 `![image](images/ch05_stripin_si9.gif)`。

###### 并行数字化
