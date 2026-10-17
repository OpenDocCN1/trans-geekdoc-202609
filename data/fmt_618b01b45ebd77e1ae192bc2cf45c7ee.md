
![](img/f0f0f5d89818fdddf117bbe758ac8143_252_0.png)

图 8-13. 我们扩散模型的采样过程的一个步骤

如果我们重复这个过程多次，最终会得到一个在许多小步骤中逐步引导的 `x₀` 估计值。事实上，我们可以自由选择步数，而且关键是它不必与训练噪声过程中的大量步数相同（即 1,000）。它可以小得多——在本例中我们选择 20。

下面的方程（Song et al., 2020）从数学上描述了这一过程：

`x_{t-1}=√{\bar{α}_{t-1}} ( (x_t - √{1-\bar{α}_t} ε_θ^{(t)}(x_t))/√{\bar{α}_t} ) + √{1-\bar{α}_{t-1}-σ_t^2}·ε_θ^{(t)}(x_t) + σ_t ε_t` 预测的 x0  指向 x_t 的方向  随机噪声

让我们分解一下。方程右边括号内的第一项是估计的图像 `x₀`，使用我们网络预测的噪声 `ε_θ^{(t)}` 计算得到。然后我们将其按 t − 1 信号率 `√{\bar{α}_{t-1}}` 缩放，并重新应用预测的噪声，但这次按 t − 1 噪声率 `√{1-\bar{α}_{t-1}-σ_t^2}` 缩放。还会添加额外的高斯随机噪声 `σ_t ε_t`，其中因子 `σ_t` 决定我们希望生成过程有多随机。

特殊情况 `σ_t = 0` 对所有 t 成立，对应于一种称为去噪扩散隐式模型（DDIM）的模型，由 Song et al. 于 2020 年提出。⁹ 使用 DDIM 时，生成过程完全确定——也就是说，相同的随机噪声输入总会产生相同的输出。这是有益的，因为这样我们就有了从潜在空间样本到像素空间生成输出的明确映射。

在我们的示例中，我们将实现一个 DDIM，从而使生成过程确定性。DDIM 采样过程（反向扩散）的代码如示例 8-11 所示。

### 示例 8-11. 从扩散模型中采样

```python
class DiffusionModel(models.Model):
    ...
    def reverse_diffusion(self, initial_noise, diffusion_steps):
        num_images = initial_noise.shape[0]
        step_size = 1.0 / diffusion_steps
        current_images = initial_noise
        for step in range(diffusion_steps):
            diffusion_times = tf.ones((num_images, 1, 1, 1)) - step * step_size
            noise_rates, signal_rates = self.diffusion_schedule(diffusion_times)
            pred_noises, pred_images = self.denoise(
                current_images, noise_rates, signal_rates, training=False
            )
            next_diffusion_times = diffusion_times - step_size
            next_noise_rates, next_signal_rates = self.diffusion_schedule(
                next_diffusion_times
            )
            current_images = (
                next_signal_rates * pred_images + next_noise_rates * pred_noises
            )
        return pred_images
```

- 1. 遍历固定数量的步骤（例如 20 步）。
- 2. 扩散时间全部设为 1（即反向扩散过程的开始）。
- 3. 根据扩散调度计算噪声率和信号率。
- 4. 使用 U-Net 预测噪声，从而计算去噪图像估计。
- 5. 扩散时间减少一个步长。
- 6. 计算新的噪声率和信号率。
- 7. 根据 t-1 扩散调度率，通过将预测的噪声重新应用到预测的图像上计算 t-1 图像。
- 8. 20 步后，返回最终的 `x₀` 预测图像。

## 扩散模型的分析

我们现在来看三种不同的使用训练模型的方式：生成新图像、测试反向扩散步数对质量的影响，以及在潜在空间中对两幅图像进行插值。

### 生成图像

为了从训练好的模型中生成样本，我们只需运行反向扩散过程，并在最后确保对输出进行反归一化（即把像素值转换回 [0, 1] 范围）。我们可以在 `DiffusionModel` 类中使用示例 8-12 中的代码实现这一点。

### 示例 8-12. 使用扩散模型生成图像

```python
class DiffusionModel(models.Model):
    ...
    def denormalize(self, images):
        images = self.normalizer.mean + images * self.normalizer.variance**0.5 ①
        return tf.clip_by_value(images, 0.0, 1.0)

    def generate(self, num_images, diffusion_steps):
        initial_noise = tf.random.normal(shape=(num_images, 64, 64, 3)) ①
        generated_images = self.reverse_diffusion(initial_noise, diffusion_steps) ②
        generated_images = self.denormalize(generated_images) ③
        return generated_images
```

- ① 生成一些初始噪声图。
- ② 应用反向扩散过程。
- ③ 网络输出的图像均值为零、方差为单位，因此需要通过重新应用训练数据计算得到的均值和方差来反归一化。

图 8-14 中我们可以观察到训练过程不同 epoch 的扩散模型样本。

![](img/f0f0f5d89818fdddf117bbe758ac8143_255_0.png)

图 8-14. 训练过程不同 epoch 的扩散模型样本

### 调整扩散步数

我们还可以测试调整反向过程中的扩散步数如何影响图像质量。直观上，过程采用的步数越多，图像生成的质量就越高。

我们可以在图 8-15 中看到，生成的质量确实随着扩散步数的增加而提高。仅从初始采样噪声进行一次巨大跳跃时，模型只能预测出模糊的颜色块。随着步数的增加，模型能够细化和锐化其生成结果。然而，生成图像所需的时间随扩散步数线性增长，因此存在权衡。20 到 100 步扩散之间改进很小，因此在本例中我们选择 20 作为质量和速度之间的合理折中。

![](img/f0f0f5d89818fdddf117bbe758ac8143_256_0.png)

图 8-15. 图像质量随着扩散步数的增加而提高

### 图像插值

最后，正如我们在变分自编码器中看到的那样，我们可以在高斯潜在空间中的点之间进行插值，以便在像素空间中平滑地在图像之间过渡。这里我们选择使用一种球面插值形式，确保在混合两个高斯噪声图时方差保持不变。具体而言，每个步骤的初始噪声图由 `a sin(π/2 t) + b cos(π/2 t)` 给出，其中 `t` 从 0 平滑变化到 1，`a` 和 `b` 是我们希望在两者之间进行插值的两个随机采样高斯噪声张量。

结果图像如图 8-16 所示。

![](img/f0f0f5d89818fdddf117bbe758ac8143_257_0.png)

图 8-16. 使用去噪扩散模型在图像之间进行插值

### 摘要

在本章中，我们探索了近年来生成建模中最令人兴奋和最有前景的领域之一：扩散模型。特别是，我们实现了关于生成扩散模型的关键论文（Ho 等，2020）中的思想，该论文提出了原始的去噪扩散概率模型（DDPM）。随后，我们在此基础上扩展了《去噪扩散隐式模型》（DDIM）论文中的思想，使生成过程完全确定性。

我们看到扩散模型由前向扩散过程和反向扩散过程组成。前向扩散过程通过一系列小步骤向训练数据添加噪声，而反向扩散过程则由一个试图预测所添加噪声的模型组成。

我们使用重参数化技巧，以便在不经过多次加噪步骤的情况下计算前向过程中的任意步骤的加噪图像。我们看到，用于向数据添加噪声的参数所选的调度在模型的整体成功中起着重要作用。

反向扩散过程由 U-Net 参数化，该网络尝试在给定加噪图像和该步骤的噪声率的情况下预测每个时间步的噪声。U-Net 由 DownBlocks 组成，DownBlocks 在减小图像尺寸的同时增加通道数，以及 UpBlocks，在增大图像尺寸的同时减小通道数。噪声率使用正弦嵌入进行编码。

从扩散模型采样是在一系列步骤中进行的。U-Net 用于预测添加到给定加噪图像的噪声，然后用于计算原始图像的估计值。预测的噪声随后使用更小的噪声率重新应用。该过程在一系列步骤中重复（这些步骤可能明显少于训练期间使用的步骤数），从标准高斯噪声分布中采样的随机点开始，以获得最终生成结果。

我们看到，增加反向过程中的扩散步数可以提高图像生成质量，但会以速度为代价。我们还执行了潜在空间算术，以便在两幅图像之间进行插值。

### 参考文献

- 1. Jascha Sohl-Dickstein 等，“使用非平衡热力学的深度无监督学习”，2015 年 3 月 12 日, https://arxiv.org/abs/1503.03585
- 2. Yang Song and Stefano Ermon，“通过估计数据分布的梯度进行生成建模”，2019 年 7 月 12 日, https://arxiv.org/abs/1907.05600.
- 3. Yang Song and Stefano Ermon，“训练基于分数的生成模型的改进技术”，2020 年 6 月 16 日, https://arxiv.org/abs/2006.09011.
- 4. Jonathon Ho 等，“去噪扩散概率模型”，2020 年 6 月 19 日, https://arxiv.org/abs/2006.11239.
- 5. Alex Nichol and Prafulla Dhariwal，“改进的去噪扩散概率模型”，2021 年 2 月 18 日, https://arxiv.org/abs/2102.09672.
- 6. Ashish Vaswani 等，“注意力就是你所需要的”，2017 年 6 月 12 日, https://arxiv.org/abs/1706.03762.
- 7. Ben Mildenhall 等，“NeRF：用神经辐射场表示场景以进行视图合成”，2020 年 3 月 1 日, https://arxiv.org/abs/2003.08934.
- 8. Kaiming He 等，“用于图像识别的深度残差学习”，2015 年 12 月 10 日, https://arxiv.org/abs/1512.03385.
- 9. Jiaming Song 等，“去噪扩散隐式模型”，2020 年 10 月 6 日, https://arxiv.org/abs/2010.02502

## 第三部分

### 应用

在第三部分，我们将探索迄今为止所见的生成建模技术的一些关键应用，涵盖图像、文本、音乐和游戏。我们还将看到如何使用最先进的多模态模型遍历这些领域。

在第 9 章，我们将把注意力转向 Transformers，这是一种最先进的架构，驱动着大多数现代文本生成模型。特别是，我们将探索 GPT 的内部工作原理，并使用 Keras 构建自己的版本，我们将看到它如何构成 ChatGPT 等工具的基础。

在第 10 章，我们将研究一些对图像生成产生影响的最重要的 GAN 架构，包括 ProGAN、StyleGAN、StyleGAN2、SAGAN、BigGAN、VQ-GAN 和 ViT VQ-GAN。我们将探索每个架构的关键贡献，并试图了解该技术如何随时间演变。

第 11 章介绍音乐生成，这带来了诸如建模音乐音高和节奏等额外挑战。我们将看到许多适用于文本生成的技术（如 Transformers）也可以应用于该领域，但我们还将探索一种名为 MuseGAN 的深度学习架构，该架构采用基于 GAN 的方法生成音乐。

第 12 章展示了生成模型如何在其他机器学习领域中使用，例如强化学习。我们将重点关注“World Models”论文，该论文展示了如何将生成模型用作智能体训练的环境，使其能够在环境的一种幻觉梦境版本中训练，而不是在真实环境中。

在第 13 章，我们将探索跨越图像和文本等领域的最先进多模态模型。这包括 DALL.E 2、Imagen 和 Stable Diffusion 等文本到图像模型，以及 Flamingo 等视觉语言模型。

最后，第 14 章总结了迄今为止的生成式 AI 之旅、当前的生成式 AI 格局以及我们未来可能的发展方向。我们将探讨生成式 AI 如何改变我们的生活和工作方式，并考虑它是否有可能在未来几年解锁更深层次的人工智能形式。

## Transformers

#### 章节目标

在本章中你将：

- 了解 GPT 的起源，这是一种用于文本生成的强大解码器 Transformer 模型。
- 从概念上了解注意力机制如何模仿我们对句子中某些词赋予比其他词更多重要性的方式。
- 从第一性原理深入探讨注意力机制的工作原理，包括查询、键和值是如何创建和操作的。
- 了解因果掩码对文本生成任务的重要性。
- 理解注意力头如何组合成多头注意力层。
- 了解多头注意力层如何构成 Transformer 块的一部分，该块还包括层归一化和跳跃连接。
- 创建位置编码，以捕捉每个 token 的位置以及词 token 嵌入。
- 在 Keras 中构建 GPT 模型以生成葡萄酒评论中的文本。
- 分析 GPT 模型的输出，包括询问注意力分数以检查模型正在关注的位置。
- 了解不同类型的 Transformers，包括每个类型可以处理的任务示例以及最著名最先进实现方法的描述。
- 理解编码器-解码器架构的工作原理，如 Google 的 T5 模型。
- 探索 OpenAI ChatGPT 背后的训练过程。

我们在第 5 章中看到如何使用循环神经网络（RNNs），例如 LSTMs 和 GRUs，在文本数据上构建生成模型。这些自回归模型一次处理一个 token 的序列数据，不断更新一个隐藏向量，以捕捉输入的当前潜在表示。RNN 可以通过在隐藏向量上应用密集层和 softmax 激活来设计以预测序列中的下一个词。这被认为是在 2017 年之前生成文本的最复杂方式，当时一篇论文永远改变了文本生成的格局。

### 引言

Google Brain 论文，自信地题为“Attention Is All You Need，”¹ 因推广 *attention* 概念而闻名——该机制现在驱动着大多数最先进的文本生成模型。

作者展示了如何创建强大的神经网络 *Transformers* 用于序列建模，这些网络不需要复杂的循环或卷积架构，而是仅依赖于注意力机制。这种方法克服了 RNN 方法的一个关键缺点，即难以并行化，因为它必须一次处理一个 token 的序列。Transformers 高度可并行化，使其能够在海量数据集上进行训练。

在本章中，我们将深入探讨现代文本生成模型如何利用 Transformer 架构在文本生成挑战上达到最先进的性能。特别是，我们将探索一种称为 *generative pre-trained transformer*（GPT）的自回归模型，该模型驱动 OpenAI 的 GPT-4 模型，被广泛认为目前是文本生成的最先进水平。

### GPT

OpenAI 于 2018 年 6 月在论文“Improving Language Understanding by Generative Pre-Training，”² 中引入了 GPT，几乎正好是在原始 Transformer 论文发表一年后。

在本文中，作者展示了如何在一个 Transformer 架构上进行训练，使用大量文本数据来预测序列中的下一个词，然后再微调到特定的下游任务。

GPT 的预训练过程涉及在名为 BookCorpus 的大型文本语料库上训练模型（来自 7,000 本不同类型未出版书籍的 4.5 GB 文本）。在预训练期间，模型被训练根据之前的词预测序列中的下一个词。该过程被称为 *language modeling*，用于教会模型理解自然语言的结构和模式。

After pre-training, the GPT model can be fine-tuned for a specific task by providing it with a smaller, task-specific dataset. Fine-tuning involves adjusting the parameters of the model to better fit the task at hand. For example, the model can be fine-tuned for tasks such as classification, similarity scoring, or question answering.
