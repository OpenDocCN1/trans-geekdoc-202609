

(Szegedy et al., 2014; Goodfellow et al., 2015) 导致模型误预测。相反，C-examples 是无数据的，旨在通过剪枝后的基模型变体实现 *高鲁棒性*，并通过 *低可迁移性* 筛选出任何与基模型不同的其他模型。

Wang et al. (2021d) 考虑 C-examples 中涉及的三种 DNN 模型类型。
- 基模型：用于完成某些指定任务（例如图像分类）的预训练模型。
- 剪枝模型：从基模型剪枝得到并部署在边缘设备上以执行推理的模型。
- 其他模型：既不是 ① 也不是 ② 的任何其他模型。例如，如果 VGG16 是基模型，那么 VGG19、ResNet 系列等均属于其他模型。

所提出的 DNN 指纹框架如下：使用 ① 基模型生成带标签的 C-examples。因此 C-examples 在基模型上的准确率为 100%。随后，将 C-examples 用作指纹来测试部署在边缘设备上的模型。如果部署的模型是 ②，则预期准确率较高；如果部署的模型是 ③，则预期准确率较低。C-example 生成过程的系统示意图如图 20.2 所示。

![](img/fa92deee3de0f00ea56e92ca0b92c8e4_247_0.png)

图 20.2 Wang et al. (2021d) 提出的生成 LTRC-example 的系统图。

香草 C-examples。设 \(\mathbf{x} \in \mathbb{R}^{3 \times H \times W}\) 表示一张彩色 RGB 图像，其中 \(H\) 和 \(W\) 分别为图像的高度和宽度。为数学上的简便起见，我们将 \(\mathbf{x}\) 的像素值缩放到 \([0, 1]\)。\(F_\theta\) 表示基模型，其输出 \(\mathbf{y} = F_\theta(\mathbf{x})\) 作为总共 \(K\) 个类别的概率分布。元素 \(\gamma_i\) 表示输入 \(\mathbf{x}\) 属于第 \(i\) 个类别的概率。参数为 \(\theta\) 的基模型 \(F_\theta\) 是预训练的。随后，从 \(F_\theta\) 生成 C-examples。如果给定从训练数据集标签中随机选择的 \(P\) 个标签的子集 \(\{l_1, l_2, \dots, l_P\}\)，则一组 \(\eta\)-最优 C-examples \(X^*\) 可表征为

```
\(X^* = \left\{ (\mathbf{x}, l) | \text{Loss}_\theta(\mathbf{x}, l) < \eta, \mathbf{x} \in [0, 1]^n \right\}.\) (20.6)
```

术语 \(\text{Loss}_\theta\) 表示 \(F_\theta\) 的损失函数。针对指定标签 \(l\) 最小化损失的 C-example \(\mathbf{x}\) 应满足上述约束。为在提取基模型特征时不依赖数据，我们直接使用随机种子生成 C-example，因此生成的 C-examples 在人类感知上与自然图像不同。图 20.3(a) 展示了一个香草版本的 C-example。

![](img/fa92deee3de0f00ea56e92ca0b92c8e4_248_0.png)

图 20.3 使用不同生成过程可视化的特征示例。这些图像分配的标签均为“草莓”。

我们可以使用第 3 章介绍的投影梯度下降 (PGD) 算法来寻找 C-examples。C-example 生成问题 (20.6) 可通过 PGD 算法按以下方式求解：

```
\(\mathbf{x}^{t+1} = \mathbf{Clip} \left( \mathbf{x}^t - \alpha \cdot \text{sign}(\nabla_{\mathbf{x}} \text{Loss}_\theta(\mathbf{x}^t, l)) \right),\) (20.7)
```

其中 \(t\) 为迭代步数索引，\(\mathbf{x}^0\) 为随机起点，\(\alpha\) 为步长，sign 返回向量的逐元素符号，\(\nabla_{\mathbf{x}}\) 计算输入梯度，\(\mathbf{Clip}\) 表示裁剪操作以满足 \(\mathbf{x} \in [0, 1]^n\) 约束。

**鲁棒 C-examples。** Wang et al. (2021d) 在香草 C-examples 的基础上进一步提出了一种名为鲁棒 C-examples (RC-examples) 的增强方法，即通过向神经网络参数 \(\theta\) 添加受 \(\epsilon\) 约束的噪声，以模拟模型压缩过程导致的模型权重扰动。在此，损失函数更改为 \(\text{Loss}_{\theta+\Delta}\)，其中 \(\Delta\) 表示在 \([-\epsilon, \epsilon]\) 范围内均匀分布的权重扰动。此外，受期望-over-变换 (EOT) 方法 (Athalye et al., 2018) 的启发（用于更强的对抗攻击，EOT 攻击细节见第 4 章），所提 RC-examples 可通过在每次迭代步骤中对 \(\Delta\) 的不同随机实现计算输入梯度均值（梯度均值 (GM) 方法）来进一步增强。

LTRC-examples。最后，除了增强 C-examples 对 ② 剪枝模型的鲁棒性外，还希望其对 ③ 其他模型表现出低可迁移性。因此，通过强制实施低可迁移性对 RC-examples 进行进一步改进，命名为 *低可迁移性 RC-examples* (*LTRC-examples*)。这样一来，我们可以提高 C-examples 在检测 *假阳性* 案例中的能力，其中阳性意味着在知识产权保护中声称模型归属权为我们所有。

频率分析 (Guo et al., 2018; Sharma et al., 2019; Cheng et al., 2019b) 提示，低频分量可以提高对抗样本的可迁移性。受此启发，我们提出利用高频分量来实现具有低可迁移性的 C-examples。具体来说，我们可以在 *离散余弦变换* (DCT) (Rao and Yip, 2014) 上应用频率掩码，以在 C-example 的频率域中实现高通滤波器。作为信号处理中的重要工具，DCT 将给定信号分解为不同频率和振幅的余弦函数。对于 2D 图像，执行 \(\omega = \text{DCT}(\mathbf{x})\) 的 DCT 可以将图像 \(\mathbf{x}\) 转换到频率域，其中 \(\omega_{(i,j)}\) 是对应余弦函数的幅度，\(i\) 和 \(j\) 的值表示频率，较小的值表示较低频率。DCT 是可逆的，逆 DCT (IDCT) 表示为 \(\mathbf{x} = \text{IDCT}(\omega)\)。需要注意的是，Wang et al. (2021d) 对不同颜色通道独立地应用 DCT 和 IDCT。

受低频在机器分类中起更重要作用且因此更具可迁移性的观察启发，Wang et al. (2021d) 提议滤除这些分量以有效降低指纹可迁移性。为证明这一点，如图 20.2 所示施加高通频率掩码，其中高频带大小 \(k\) 控制被滤除的低频分量范围。频率掩码设计为一个 2D 矩阵，元素为 0 或 1，即 \(\mathbf{m} \in \{0, 1\}^{H \times W}\)，与 C-example 的 DCT 进行逐元素乘积。在生成指纹的每次迭代步骤中，高通掩码将低频分量设为 0，即当 \(1 \le i+j \le k\) 时 \(\omega_{(i,j)} = 0\)，同时保留其余高频分量。利用高通频率掩码，第 \((t+1)\) 次迭代步骤中的 LTRC-example 可由以下公式导出：

$$\mathbf{x}^{t+1} = \text{HighPass}\left\{ \mathbf{Clip} \left( \mathbf{x}^t - \alpha \cdot \text{sign} \left( \nabla_{\mathbf{x}} \text{Loss}_{\theta+\Delta}(\mathbf{x}^t, \text{I}) \right) \right) \right\}, \tag{20.8}$$

其中 HighPass 滤波器定义为

HighPass(·) = IDCT(FrequencyMask(DCT(·))). (20.9)

## 20.3 实证比较

在这里，我们比较 Wang et al. (2021d) 提出的不同 C-examples 变体。它们的可视化比较如图 20.3 所示。

在实验中，C-examples 在剪枝模型上的准确率用于表示其鲁棒性，在变体模型（与基模型功能相似，例如基模型 VGG-16 对应的 VGG-19 模型）上的准确率用于表示其可迁移性。最初，所有类型的 C-examples 在基模型上的准确率在生成期间均为 100%。为有效评估剪枝模型鲁棒性与其他变体模型可迁移性之间的权衡，我们将鲁棒性与可迁移性之差定义为 _唯一性评分_（_唯一性评分_ = _鲁棒性_ − _可迁移性_），更高的唯一性评分意味着 C-examples 对剪枝模型更具鲁棒性且对变体模型的可迁移性更低。直觉上，更好的指纹方法应当获得更高的唯一性评分。唯一性评分也可用于指示误阳性问题，即，如果唯一性评分为负，则相应的指纹方法容易做出错误的模型声明。

表 20.2 展示了在 ImageNet 数据集上使用基模型 VGG-16 和不同剪枝比来评估鲁棒性时，C-examples、RC-examples 和 LTRC-examples 在不同剪枝模型上的有效性。为测试对其他变体模型（例如 VGG-19、ResNet 系列、DenseNet 系列）的可迁移性，由于 VGG-19 与 VGG-16 架构最为相似，且在 VGG-16 上生成的指纹在 VGG-19 上更具可迁移性，我们仅报告 VGG-19 上的可迁移性，省略 ResNet 系列或 DenseNet 系列等其他模型的可迁移性结果。需要注意的是，对其他模型的可迁移性应低于 VGG-19，从而获得更高的唯一性评分，表现更好。

如表 20.2 所示，RC-examples、RC-examples+GM 和 LTRC-examples 的唯一性评分均高于基线香草 C-examples。我们注意到，当剪枝比为 70% 和 80% 时，C-examples 因对其他模型具有高可迁移性而出现负唯一性评分。可以观察到，\(\epsilon = 0.001\) 的 LTRC-examples 达到最佳唯一性评分，且优势幅度相对较大

