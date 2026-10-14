
![](img/f0f0f5d89818fdddf117bbe758ac8143_234_0.png)

### 运行本例的代码

本例的代码可以在书籍仓库中位于 `notebooks/08_diffusion/01_ddm/ddm.ipynb` 的 Jupyter 笔记本中找到。

代码改编自 András Béres 在 Keras 网站上创建的关于去噪扩散隐式模型的优秀教程。

### 花卉数据集

我们将使用通过 Kaggle 可用的 Oxford 102 Flower 数据集。这是一组超过 8,000 张各种花卉的彩色图像。

你可以通过在书籍仓库中运行 Kaggle 数据集下载脚本来下载数据集，如示例 8-1 所示。这将把花卉图像保存到 `/data` 文件夹。

### 示例 8-1. 下载 Oxford 102 花卉数据集

```
bash scripts/download_kaggle_data.sh nunenuh pytorch-challenge-flower-dataset
```

如常，我们将使用 Keras `image_dataset_from_directory` 函数加载图像，将图像调整为 64 × 64 像素，并将像素值缩放到范围 [0, 1]。我们还将数据集重复五次以增加 epoch 长度，并将数据批处理为每组 64 张图像，如示例 8-2 所示。

### 示例 8-2. 加载 Oxford 102 花卉数据集

```
train_data = utils.image_dataset_from_directory(
"/app/data/pytorch-challenge-flower-dataset/dataset",
labels=None,
image_size=(64, 64),
batch_size=None,
shuffle=True,
)
```

```
seed=42,
interpolation="bilinear",
)

def preprocess(img):
    img = tf.cast(img, "float32") / 255.0
    return img

train = train_data.map(lambda x: preprocess(x))
train = train.repeat(5)
train = train.batch(64, drop_remainder=True)
```

- 1. 使用 Keras 的 `image_dataset_from_directory` 函数在训练时按需加载数据集。
- 2. 将像素值缩放到 [0, 1] 范围。
- 3. 重复数据集五次。
- 4. 将数据集批处理为每组 64 张图像。

数据集中的示例图像如图 8-2 所示。

![](img/f0f0f5d89818fdddf117bbe758ac8143_235_0.png)

图 8-2. 来自 Oxford 102 Flower 数据集的示例图像

现在我们有了数据集，可以探索如何使用前向扩散过程向图像添加噪声。

## 前向扩散过程

假设我们有一张图像 $x_0$，想要在大量步骤（例如 $T = 1,000$）中逐渐对其进行破坏，使得最终它与标准高斯噪声无法区分（即 $x_T$ 应具有零均值和单位方差）。我们应该如何实现这一点？

我们可以定义一个函数 $q$，它向图像 $\mathbf{x}_{t-1}$ 添加少量方差为 $\beta_t$ 的高斯噪声以生成新的图像 $\mathbf{x}_t$。如果我们不断应用此函数，将生成一系列逐渐更嘈杂的图像 $(\mathbf{x}_0,...,\mathbf{x}_T)$，如图 8-3 所示。

![](img/f0f0f5d89818fdddf117bbe758ac8143_236_0.png)

图 8-3. 前向扩散过程 $q$

我们可以按如下方式数学地写出此更新过程（此处，$\epsilon_{t-1}$ 是零均值和单位方差的标准高斯）：

$\mathbf{x}_t = \sqrt{1-\beta_t}\,\mathbf{x}_{t-1} + \sqrt{\beta_t}\,\epsilon_{t-1}$

请注意，我们还对输入图像 $\mathbf{x}_{t-1}$ 进行缩放，以确保输出图像 $\mathbf{x}_t$ 的方差随时间保持恒定。这样，如果我们将原始图像 $\mathbf{x}_0$ 归一化为零均值和单位方差，那么对于足够大的 $T$，$\mathbf{x}_T$ 将近似于标准高斯分布，通过归纳如下。

如果我们假设 $\mathbf{x}_{t-1}$ 具有零均值和单位方差，则 $\sqrt{1-\beta_t}\,\mathbf{x}_{t-1}$ 的方差为 $1-\beta_t$，而 $\sqrt{\beta_t}\,\epsilon_{t-1}$ 的方差为 $\beta_t$，使用规则 $Var(aX)=a^2Var(X)$。将它们相加，我们得到一个新的分布 $\mathbf{x}_t$，其零均值和方差为 $1-\beta_t+\beta_t=1$，使用规则 $Var(X+Y)=Var(X)+Var(Y)$，适用于独立的 $X$ 和 $Y$。因此，如果 $\mathbf{x}_0$ 归一化为零均值和单位方差，则我们保证这对所有 $\mathbf{x}_t$ 都成立，包括最终图像 $\mathbf{x}_T$，它将近似于标准高斯分布。这正是我们需要的，因为我们希望能够轻松采样 $\mathbf{x}_T$，然后通过训练好的神经网络模型应用反向扩散过程！

换句话说，我们的前向加噪过程 $q$ 也可以写成如下形式：

$q(\mathbf{x}_t|\mathbf{x}_{t-1}) = \mathcal{N}\left(\mathbf{x}_t; \sqrt{1-\beta_t}\,\mathbf{x}_{t-1}, \beta_t\mathbf{I}\right)$

### 重参数化技巧

能够直接从图像 $\mathbf{x}_0$ 跳转到图像 $\mathbf{x}_t$ 的任意加噪版本，而无需经过 $t$ 次 $q$ 的应用，这也很有用。幸运的是，我们可以使用重参数化技巧来实现这一点。

如果我们定义 $\alpha_t = 1 - \beta_t$ 和 $\bar{\alpha}_t = \prod_{i=1}^t \alpha_i$，则可以写出如下内容：

$$
x_t = \sqrt{\alpha_t} x_{t-1} + \sqrt{1-\alpha_t} \epsilon_{t-1}
= \sqrt{\alpha_t \alpha_{t-1}} x_{t-2} + \sqrt{1-\alpha_t \alpha_{t-1}} \epsilon
= \ldots
= \sqrt{\bar{\alpha}_t} x_0 + \sqrt{1-\bar{\alpha}_t} \epsilon
$$

请注意，第二行使用了可以将两个高斯分布相加得到新的高斯分布这一事实。因此，我们有一种方法可以从原始图像 $x_0$ 跳转到前向扩散过程 $x_t$ 的任意步骤。此外，我们可以使用 $\bar{\alpha}_t$ 值而不是原始 $\beta_t$ 值来定义扩散计划，其解释是 $\bar{\alpha}_t$ 是由于信号（原始图像，$x_0$）引起的方差，而 $1 - \bar{\alpha}_t$ 是由于噪声（$\epsilon$）引起的方差。

前向扩散过程 $q$ 因此也可以写成如下形式：

$$
q(x_t | x_0) = \mathcal{N}(x_t; \sqrt{\bar{\alpha}_t} x_0, (1 - \bar{\alpha}_t) I)
$$

## 扩散计划

请注意，我们也可以在每个时间步选择不同的 $\beta_t$——它们不必都相同。$\beta_t$（或 $\bar{\alpha}_t$）值随 $t$ 的变化方式称为扩散计划。

在原始论文（Ho et al., 2020）中，作者为 $\beta_t$ 选择了线性扩散计划——即 $\beta_t$ 随 $t$ 线性增加，从 $\beta_1 = 0.0001$ 增加到 $\beta_T = 0.02$。这确保了在加噪过程的早期阶段，我们采取的加噪步长小于后期阶段，此时图像已经非常嘈杂。

我们可以按示例 8-3 所示实现线性扩散计划。

### 示例 8-3. 线性扩散计划

```
def linear_diffusion_schedule(diffusion_times):
    min_rate = 0.0001
    max_rate = 0.02
    betas = min_rate + tf.convert_to_tensor(diffusion_times) * (max_rate - min_rate)
    alphas = 1 - betas
    alpha_bars = tf.math.cumprod(alphas)
    signal_rates = alpha_bars
    noise_rates = 1 - alpha_bars
    return noise_rates, signal_rates
```

```
T = 1000
diffusion_times = [x/T for x in range(T)] ①
linear_noise_rates, linear_signal_rates = linear_diffusion_schedule(
    diffusion_times
) ②
```

① 扩散时间是 0 到 1 之间等间距的步长。

② 线性扩散计划应用于扩散时间以产生噪声和信号率。

在后来的论文中发现余弦扩散计划优于原始论文中的线性计划。⁵ 余弦计划定义了 $\bar{\alpha}_t$ 的以下值：

$$
\bar{\alpha}_t = \cos^2\left(\frac{t}{T} \cdot \frac{\pi}{2}\right)
$$

因此更新后的方程如下（使用三角恒等式 $\cos^2(x) + \sin^2(x) = 1$）：

$$
x_t = \cos\left(\frac{t}{T} \cdot \frac{\pi}{2}\right)x_0 + \sin\left(\frac{t}{T} \cdot \frac{\pi}{2}\right)\epsilon
$$

该方程是论文中实际使用的余弦扩散计划的简化版本。作者还添加了偏移项和缩放，以防止扩散过程开始时加噪步长过小。我们可以按示例 8-4 所示实现余弦和偏移余弦扩散计划。

### 示例 8-4. 余弦和偏移余弦扩散计划

```
def cosine_diffusion_schedule(diffusion_times): ①
    signal_rates = tf.cos(diffusion_times * math.pi / 2)
    noise_rates = tf.sin(diffusion_times * math.pi / 2)
    return noise_rates, signal_rates
```

```
def offset_cosine_diffusion_schedule(diffusion_times): ②
    min_signal_rate = 0.02
    max_signal_rate = 0.95
    start_angle = tf.acos(max_signal_rate)
    end_angle = tf.acos(min_signal_rate)

    diffusion_angles = start_angle + diffusion_times * (end_angle - start_angle)

    signal_rates = tf.cos(diffusion_angles)
    noise_rates = tf.sin(diffusion_angles)
    return noise_rates, signal_rates
```

- 1. 纯余弦扩散计划（无偏移或重缩放）。
- 2. 我们将使用的偏移余弦扩散计划，它调整计划以确保加噪过程开始时加噪步长不会过小。

我们可以计算每个 $t$ 的 $\bar{\alpha}_t$ 值，以显示线性、余弦和偏移余弦扩散计划在每个阶段允许通过多少信号（$\bar{\alpha}_t$）和噪声（$1 - \bar{\alpha}_t$），如图 8-4 所示。

![](img/f0f0f5d89818fdddf117bbe758ac8143_239_0.png)

图 8-4. 线性、余弦和偏移余弦扩散计划在加噪过程每个步骤中的信号和噪声

请注意，余弦扩散计划中的噪声水平上升得更缓慢。余弦扩散计划比线性扩散计划更逐渐地向图像添加噪声，这提高了训练效率和生成质量。这也可以在被线性和余弦计划破坏的图像中看到（图 8-5）。

![](img/f0f0f5d89818fdddf117bbe758ac8143_239_1.png)

图 8-5. 图像被线性（上）和余弦（下）扩散计划破坏，在从 0 到 $T$ 的等间距 $t$ 值下（来源：Ho et al., 2020）

## 反向扩散过程

现在让我们来看一下反向扩散过程。回顾一下，我们正在构建一个神经网络 $p_\theta(\mathbf{x}_{t-1}|\mathbf{x}_t)$，它可以 *undo* 噪声过程——也就是说，近似逆分布 $q(\mathbf{x}_{t-1}|\mathbf{x}_t)$。如果我们能做到这一点，我们就可以从 $\mathcal{N}(0,\mathbf{I})$ 中采样随机噪声，然后多次应用反向扩散过程以生成新颖的图像。这在图 8-6 中进行了可视化。

![](img/f0f0f5d89818fdddf117bbe758ac8143_240_0.png)

图 8-6. 反向扩散过程 $p_\theta(\mathbf{x}_{t-1}|\mathbf{x}_t)$ 试图撤销前向扩散过程产生的噪声

反向扩散过程与变分自编码器的解码器之间存在许多相似之处。在两者中，我们的目标都是使用神经网络将随机噪声转换为有意义的输出。扩散模型与 VAE 之间的区别在于，在 VAE 中，前向过程（将图像转换为噪声）是模型的一部分（即它是可学习的），而在扩散模型中它是无参数化的。

因此，应用与变分自编码器相同的损失函数是有意义的。原始的 DDPM 论文推导了该损失函数的精确形式，并表明它可以通过训练网络 $\epsilon_\theta$ 来预测在时间步 $t$ 时添加到给定图像 $\mathbf{x}_0$ 的噪声 $\epsilon$ 来进行优化。

换句话说，我们采样图像 $\mathbf{x}_0$ 并通过 $t$ 步噪声处理将其转换得到图像 $\mathbf{x}_t = \sqrt{\bar{\alpha}_t}\mathbf{x}_0 + \sqrt{1-\bar{\alpha}_t}\epsilon$。我们将这个新图像和噪声率 $\bar{\alpha}_t$ 提供给神经网络，并要求它预测 $\epsilon$，并针对预测 $\epsilon_\theta(\mathbf{x}_t)$ 与真实 $\epsilon$ 之间的平方误差进行梯度步骤。

我们将在下一节中查看神经网络的结构。这里值得注意的是，扩散模型实际上维护了网络的两份拷贝：一份是使用梯度下降进行主动训练的，另一份（EMA 网络）是先前训练步骤中主动训练网络权重的指数移动平均（EMA）。EMA 网络不易受训练过程中短期波动和尖峰的影响，使其比主动训练的网络更稳健用于生成。因此，每当我们想从网络中生成输出时，我们都会使用 EMA 网络。

模型的训练过程如图 8-7 所示。

### 算法 1 训练

- 1: 重复
- 2: $x_0 \sim q(x_0)$
- 3: $t \sim \text{Uniform}(\{1, \ldots, T\})$
- 4: $\epsilon \sim \mathcal{N}(0, I)$
- 5: 对以下进行梯度下降步骤

    $\nabla_\theta \| \epsilon - \epsilon_\theta(\sqrt{\bar{\alpha}_t} x_0 + \sqrt{1-\bar{\alpha}_t} \epsilon, t) \|^2$
- 6: 直到收敛

图 8-7. 去噪扩散模型的训练过程（来源：Ho et al., 2020）

在 Keras 中，我们可以按示例 8-5 所示实现此训练步骤。

### 示例 8-5. Keras 扩散模型的 `train_step` 函数

```
class DiffusionModel(models.Model):
    def __init__(self):
        super().__init__()
        self.normalizer = layers.Normalization()
        self.network = unet
        self.ema_network = models.clone_model(self.network)
        self.diffusion_schedule = cosine_diffusion_schedule
    ...
    def denoise(self, noisy_images, noise_rates, signal_rates, training):
        if training:
            network = self.network
        else:
            network = self.ema_network
        pred_noises = network(
            [noisy_images, noise_rates**2], training=training
        )
        pred_images = (noisy_images - noise_rates * pred_noises) / signal_rates
        return pred_noises, pred_images
    def train_step(self, images):
        images = self.normalizer(images, training=True) ①
        noises = tf.random.normal(shape=tf.shape(images)) ②
        batch_size = tf.shape(images)[0]
        diffusion_times = tf.random.uniform(
            shape=(batch_size, 1, 1, 1), minval=0.0, maxval=1.0
        ) ③
        noise_rates, signal_rates = self.cosine_diffusion_schedule(
            diffusion_times
        ) ④
        noisy_images = signal_rates * images + noise_rates * noises ⑤
```
