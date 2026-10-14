
损失曲线（噪声平均绝对误差 [MAE]）如图 8-12 所示。

![](img/f0f0f5d89818fdddf117bbe758ac8143_251_0.png)

图 8-12. 按 epoch 计算的噪声平均绝对误差损失曲线

## 从去噪扩散模型中采样

为了从训练好的模型中采样图像，我们需要应用反向扩散过程——也就是说，我们需要从随机噪声开始，并使用模型逐步撤销噪声，直到得到一幅可识别的花朵图像。

我们必须牢记，我们的模型训练的目标是预测从训练集中给定的带噪图像中添加的总噪声量，而不仅仅是噪声过程中最后一步添加的噪声。然而，我们不想一次性撤销所有噪声——一次从纯随机噪声中预测图像显然行不通！我们更愿意模仿前向过程，并逐步在许多小步骤中撤销预测的噪声，以便模型能够调整其自身的预测。

为此，我们可以分两步从 $x_t$ 跳到 $x_{t-1}$——首先利用模型的噪声预测计算原始图像 $x_0$ 的估计值，然后将预测的噪声重新应用到该图像上，但仅限于 $t-1$ 个时间步，以生成 $x_{t-1}$。这个想法如图 8-13 所示。

![](img/f0f0f5d89818fdddf117bbe758ac8143_252_0.png)

图 8-13. 我们扩散模型的采样过程的一个步骤

如果我们重复这个过程多次，最终会得到一个在许多小步骤中逐步引导的 x₀ 估计值。事实上，我们可以自由选择步数，而且关键是它不必与训练噪声过程中的大量步数相同（即 1,000）。它可以小得多——在本例中我们选择 20。

下面的方程（Song et al., 2020）从数学上描述了这一过程：

x_{t-1}=√{\bar{α}_{t-1}} ( (x_t - √{1-\bar{α}_t} ε_θ^{(t)}(x_t))/√{\bar{α}_t} ) + √{1-\bar{α}_{t-1}-σ_t^2}·ε_θ^{(t)}(x_t) + σ_t ε_t  预测的 x0  指向 x_t 的方向  随机噪声

让我们分解一下。方程右边括号内的第一项是估计的图像 x₀，使用我们网络预测的噪声 ε_θ^{(t)} 计算得到。然后我们将其按 t − 1 信号率 √{\bar{α}_{t-1}} 缩放，并重新应用预测的噪声，但这次按 t − 1 噪声率 √{1-\bar{α}_{t-1}-σ_t^2} 缩放。还会添加额外的高斯随机噪声 σ_t ε_t，其中因子 σ_t 决定我们希望生成过程有多随机。

特殊情况 σ_t = 0 对所有 t 成立，对应于一种称为去噪扩散隐式模型（DDIM）的模型，由 Song et al. 于 2020 年提出。⁹ 使用 DDIM 时，生成过程完全确定——也就是说，相同的随机噪声输入总会产生相同的输出。这是有益的，因为这样我们就有了从潜在空间样本到像素空间生成输出的明确映射。

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
- 8. 20 步后，返回最终的 x₀ 预测图像。

## 扩散模型的分析

我们现在来看三种不同的使用训练模型的方式：生成新图像、测试反向扩散步数对质量的影响，以及在潜在空间中对两幅图像进行插值。

### 生成图像

为了从训练好的模型中生成样本，我们只需运行反向扩散过程，并在最后确保对输出进行反归一化（即把像素值转换回 [0, 1] 范围）。我们可以在 DiffusionModel 类中使用示例 8-12 中的代码实现这一点。

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

最后，正如我们在变分自编码器中看到的那样，我们可以在高斯潜在空间中的点之间进行插值，以便在像素空间中平滑地在图像之间过渡。这里我们选择使用一种球面插值形式，确保在混合两个高斯噪声图时方差保持不变。具体而言，每个步骤的初始噪声图由 a sin(π/2 t) + b cos(π/2 t) 给出，其中 t 从 0 平滑变化到 1，a 和 b 是我们希望在两者之间进行插值的两个随机采样高斯噪声张量。

结果图像如图 8-16 所示。
