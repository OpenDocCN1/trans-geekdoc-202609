

![](img/ca72c1626f4850f058a9edc138c1ac73_903_0.png)

图 25.10: 基于在 CelebA-HQ-256 图像上训练的基于分数的生成模型的合成人脸。引自 [Son+21b] 的图 12。特感谢 Yang Song 允许使用。

更糟。在本节中，我们简要提及一些为解决这一重要问题而提出的技术。许多其他技术在最近的综述论文 [UAP22; Yan+22; Cao+22] 中有所提及。

## 25.5.1 DDIM sampler

在本节中，我们描述 [SME21] 的去噪扩散隐式模型（DDIM），可用于高效的确定性生成。第一步是使用非马尔可夫前向扩散过程，因此它始终在上一步之外还对输入进行条件设定：

$q(\mathbf{x}_{t-1}|\mathbf{x}_t, \mathbf{x}_0) = \mathcal{N}(\sqrt{\overline{\alpha}_{t-1}}\mathbf{x}_0 + \sqrt{1 - \overline{\alpha}_{t-1} - \tilde{\sigma}_t^2}\frac{\mathbf{x}_t - \sqrt{\overline{\alpha}_t}\mathbf{x}_0}{\sqrt{1 - \overline{\alpha}_t}}, \tilde{\sigma}_t^2 \mathbf{I})$

对应的反向过程是

$p_{\boldsymbol{\theta}}(\mathbf{x}_{t-1}|\mathbf{x}_t) = \mathcal{N}(\sqrt{\overline{\alpha}_{t-1}}\hat{\mathbf{x}}_0 + \sqrt{1 - \overline{\alpha}_{t-1} - \tilde{\sigma}_t^2}\frac{\mathbf{x}_t - \sqrt{\overline{\alpha}_t}\hat{\mathbf{x}}_0}{\sqrt{1 - \overline{\alpha}_t}}, \tilde{\sigma}_t^2 \mathbf{I})$

其中 $\hat{\mathbf{x}}_0 = \hat{\mathbf{x}}_{\boldsymbol{\theta}}(\mathbf{x}_t, t)$ 是模型的预测输出。通过设置 $\tilde{\sigma}_t^2 = 0$，反向过程在给定初始先验样本（其方差由 $\tilde{\sigma}_T^2$ 控制）的情况下变得完全确定。与第 25.4.4 节讨论的方法相比，使用少量步骤时，由此产生的概率流 ODE 可取得更好的结果。

请注意，该模型的加权负 VLB 与第 25.2 节中的 $L_{\text{simple}}$ 相同，因此 DDIM 采样器可应用于已训练的 DDPM 模型。

## 25.5.2 Non-Gaussian decoder networks

如果反向扩散过程采取较大步骤，则在给定噪声输入的情况下，干净输出的诱导分布将变得多模态，如图 25.11 所示。这要求分布 $p_{\boldsymbol{\theta}}(\mathbf{x}_{t-1}|\mathbf{x}_t)$ 采用更复杂的形式。在 [Gao+21] 中，他们使用 EBM 来拟合该分布。然而，这仍然需要使用 MCMC 来绘制样本。在 [XKV22] 中，他们使用 GAN（第 26 章）来拟合该分布。这使我们能够通过传递

![](img/ca72c1626f4850f058a9edc138c1ac73_904_0.png)

图 25.11: 说明为什么在反向扩散过程中采取较大步骤需要更复杂、多模态的条件分布。引自 [KGV22] 的第 90 张幻灯片。特感谢 Arash Vahdat 允许使用。

![](img/ca72c1626f4850f058a9edc138c1ac73_904_1.png)

图 25.12: 渐进式蒸馏。引自 [SH22] 的图 1。特感谢 Tim Salimans 允许使用。

高斯噪声通过生成器。与单阶段 GAN 相比，其优势在于生成器和判别器都在解决一个简单得多的问题，从而提高了模式覆盖率并改善了训练稳定性。与标准扩散模型相比，其优势在于我们可以在更少的步骤中生成高质量样本。

## 25.5.3 Distillation

在本节中，我们讨论 [SH22] 的 **渐进式蒸馏** 方法，该方法提供了一种创建扩散模型的方式，该模型只需少量步骤即可生成高质量样本。基本思想如下。首先，我们以常规方式训练一个 DDPM 模型，并使用 DDIM 方法对其进行采样；我们将其视为“教师”模型。我们使用它来生成中间隐式状态，并训练一个“学生”模型来预测教师在每隔一个步骤上的输出，如图 25.11 所示。学生训练完成后，它可以生成与教师一样好的结果，但步骤数减半。然后，该学生可以教授新一代更快速的学生。请参见算法 25.4 了解伪代码，应将其与标准训练程序的算法 25.3 进行比较。请注意，每一轮教学都会变得更快，因为教师模型变得更小，因此进行蒸馏的总时间相对较小。结果模型只需 4 步即可生成高质量样本。

![](img/ca72c1626f4850f058a9edc138c1ac73_905_0.png)

图 25.13: 将 VAE 与扩散模型相结合。此处 E 和 D 是 VAE 的编码器和解码器。扩散模型通过拼接或使用交叉注意力机制对输入进行条件设定。引自 [Rom+22] 的图 3。特感谢 Robin Rombach 允许使用。

```
Algorithm 25.3: Standard training
Input: Model \(\hat{x}_\theta(z_t)\) to be trained
Input: Dataset \(\mathcal{D}\)
Input: Loss weight function \(w\)
1 while not converged do
    2 \(x \sim \mathcal{D}\)
    3 \(t \sim \text{Unif}(0, 1)\)
    4 \(\epsilon \sim \mathcal{N}(\mathbf{0}, \mathbf{I})\)
    5 \(z_t = \alpha_t x + \sigma_t \epsilon\)
    ...
    6 \(\tilde{x} = x\) (Clean data is target)
    7 \(\lambda_t = \log(\alpha_t^2 / \sigma_t^2)\) (Log SNR)
    8 \(L_\theta = w(\lambda_t) \|\tilde{x} - \hat{x}_\theta(z_t)\|_2^2\)
    9 \(\theta := \theta - \gamma \nabla_\theta L_\theta\)
```

```
Algorithm 25.4: Progressive distillation
Input: Trained teacher model \(\hat{x}_\eta(z_t)\)
Input: Dataset \(\mathcal{D}\)
Input: Loss weight function \(w\)
Input: Student sampling steps \(N\)
1 foreach \(K\) iterations do
    2 \(\theta := \eta\) (Assign student)
    3 while not converged do
    4 \(x \sim \mathcal{D}\)
    5 \(t \sim \text{Cat}(1, 2, \dots, N)\)
    6 \(\epsilon \sim \mathcal{N}(\mathbf{0}, \mathbf{I})\)
    7 \(z_t = \alpha_t x + \sigma_t \epsilon\)
    8 \(t' = t - 0.5/N, \quad t'' = t - 1/N\)
    9 \(z_{t'} = \alpha_{t'} \hat{x}_\eta(z_t) + \frac{\sigma_{t'}}{\sigma_t} (z_t - \alpha_t \hat{x}_\eta(z_t))\)
    10 \(z_{t''} = \dots\)
    11 \(\tilde{x} = \dots\) (Teacher is target)
    12 \(\lambda_t = \log(\alpha_t^2 / \sigma_t^2)\)
    13 \(L_\theta = w(\lambda_t) \|\tilde{x} - \hat{x}_\theta(z_t)\|_2^2\)
    14 \(\theta := \theta - \gamma \nabla_\theta L_\theta\)
    15 \(\eta := \theta\) (Student becomes next teacher)
    16 \(N := N/2\) (Halve number of sampling steps)
```

## 25.5.4 Latent space diffusion

加速图像扩散模型的另一种方法是先将图像嵌入到低维空间，然后将扩散模型拟合到嵌入式中。该想法已在多篇论文中得到探讨。在 [Rom+22] 的潜在扩散模型（LDM）中，他们采用两阶段训练方案，即先拟合带有感知损失的 VAE，然后将扩散模型拟合到嵌入式中。该架构如图 25.13 所示。LDM 构成了由 **Stability AI** 创建的非常流行的 **稳定扩散**（stable diffusion）系统的基础。在 [VKK21] 的潜在基于分数的生成模型（**LSGM**）中，他们首先训练层次化 VAE，然后联合训练 VAE 和扩散模型。

除了速度之外，将扩散模型与自动编码器相结合的另一个优势是，它使将扩散应用于多种不同类型的数据（例如文本和图）变得简单：我们只需要定义合适的架构来将输入域嵌入到连续空间中。然而，请注意，定义扩散直接应用于离散状态空间也是可能的，如第 25.7 节所讨论。

迄今为止，我们讨论了将扩散“应用于” VAE 之上的方法。然而，我们也可以做相反的事情，即在 DDPM 模型之上拟合 VAE，使用扩散模型来对来自 VAE 的模糊样本进行“后处理”。详情请参见 [Pan+22]。

## 25.6 Conditional generation

在本节中，我们讨论如何从扩散模型生成样本，其中我们基于某些侧边信息 c（例如类标签或文本提示）进行条件设定。

### 25.6.1 Conditional diffusion model

控制生成模型生成的最简单方法是在 (c, x) 对上对其进行训练，以最大化条件似然 p(x|c)。如果条件信号 c 是标量（例如，类标签），则可以将其映射到嵌入向量，然后通过空间相加或使用它来调制组归一化层将其纳入网络。如果输入 c 是另一张图像，则可以简单地将其与 x_t 作为额外通道集进行拼接。如果输入 c 是文本提示，则可以将其嵌入，然后使用空间相加或交叉注意力（如图 25.13 所示）。

### 25.6.2 Classifier guidance

条件扩散模型的一个问题是，我们需要为想要执行的每种条件重新训练它们。一种替代方法，即 **分类器引导**（classifier guidance），在 [DN21b] 中被提出，它允许我们利用预训练的判别式分类器 p_ϕ(c|x) 来控制生成过程。其思想如下。首先，我们使用贝叶斯法则来写出

```
log p(x|c) = log p(c|x) + log p(x) - log p(c) (25.60)
```

由此得到的得分函数为

```
∇_x log p(x|c) = ∇_x log p(x) + ∇_x log p(c|x) (25.61)
```

现在我们可以使用这个条件得分来生成样本，而不是无条件得分。我们可以通过将条件信号乘以因子 w > 1 来进一步放大其影响：

```
∇_x log p_w(x|c) = ∇_x log p(x) + w ∇_x log p(c|x) (25.62)
```

在实践中，可以通过从以下分布生成样本来实现这一点

```
x_{t-1} ~ N(μ + wΣg, Σ), μ = μ_θ(x_t, t), Σ = Σ_θ(x_t, t), g = ∇_{x_t} log p_ϕ(c|x_t) (25.63)
```

