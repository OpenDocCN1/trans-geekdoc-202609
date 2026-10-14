
## 示例 7-5. 缓冲区
```
class Buffer:
    def __init__(self, model):
        super().__init__()
        self.model = model
        self.examples = [
            tf.random.uniform(shape = (1, 32, 32, 1)) * 2 - 1
            for _ in range(128)
        ] ①

    def sample_new_exmps(self, steps, step_size, noise):
        n_new = np.random.binomial(128, 0.05) ②
        rand_imgs = (
            tf.random.uniform((n_new, 32, 32, 1)) * 2 - 1
        )
        old_imgs = tf.concat(
            random.choices(self.examples, k=128-n_new), axis=0
        ) ③
        inp_imgs = tf.concat([rand_imgs, old_imgs], axis=0)
        inp_imgs = generate_samples(
            self.model, inp_imgs, steps=steps, step_size=step_size, noise = noise
        ) ④
        self.examples = tf.split(inp_imgs, 128, axis = 0) + self.examples ⑤
        self.examples = self.examples[:8192]
        return inp_imgs
```
- 1. 采样缓冲区使用一批随机噪声进行初始化。
- 2. 平均而言，每次有 5% 的观测是从头生成的（即随机噪声）。
- 3. 其余部分则随机从现有缓冲区中抽取。
- 4. 这些观测被拼接后通过朗之万采样器运行。
- 5. 生成的样本被添加到缓冲区中，缓冲区会被修剪至最大长度 8,192 个观测。

图 7-5 显示了对比散度一次训练步骤。算法会降低真实观测的分数并提高伪观测的分数，而不关心在每一步之后对这些分数进行归一化。

![](img/f0f0f5d89818fdddf117bbe758ac8143_225_0.png)

图 7-5. 对比散度的一步

我们可以在自定义 Keras 模型中实现对比散度算法的训练步骤，如示例 7-6 所示。

## 示例 7-6. 使用对比散度训练的 EBM
```python
class EBM(models.Model):
    def __init__(self):
        super(EBM, self).__init__()
        self.model = model
        self.buffer = Buffer(self.model)
        self.alpha = 0.1
        self.loss_metric = metrics.Mean(name="loss")
        self.reg_loss_metric = metrics.Mean(name="reg")
        self.cdiv_loss_metric = metrics.Mean(name="cdiv")
        self.real_out_metric = metrics.Mean(name="real")
        self.fake_out_metric = metrics.Mean(name="fake")

    @property
    def metrics(self):
        return [
            self.loss_metric,
            self.reg_loss_metric,
            self.cdiv_loss_metric,
            self.real_out_metric,
            self.fake_out_metric
        ]

    def train_step(self, real_imgs):
        real_imgs += tf.random.normal(
            shape=tf.shape(real_imgs), mean = 0, stddev = 0.005
        ) ①
        real_imgs = tf.clip_by_value(real_imgs, -1.0, 1.0)
        fake_imgs = self.buffer.sample_new_exmps(
            steps=60, step_size=10, noise = 0.005
        ) ②
        inp_imgs = tf.concat([real_imgs, fake_imgs], axis=0)
        with tf.GradientTape() as training_tape:
            real_out, fake_out = tf.split(self.model(inp_imgs), 2, axis=0) ③
            cdiv_loss = tf.reduce_mean(fake_out, axis = 0) - tf.reduce_mean(
                real_out, axis = 0
            ) ④
            reg_loss = self.alpha * tf.reduce_mean(
                real_out ** 2 + fake_out ** 2, axis = 0
            ) ⑤
            loss = reg_loss + cdiv_loss
            grads = training_tape.gradient(loss, self.model.trainable_variables) ⑥
            self.optimizer.apply_gradients(
                zip(grads, self.model.trainable_variables)
            )
            self.loss_metric.update_state(loss)
            self.reg_loss_metric.update_state(reg_loss)
            self.cdiv_loss_metric.update_state(cdiv_loss)
            self.real_out_metric.update_state(tf.reduce_mean(real_out, axis = 0))
            self.fake_out_metric.update_state(tf.reduce_mean(fake_out, axis = 0))
            return {m.name: m.result() for m in self.metrics}

    def test_step(self, real_imgs): ⑦
        batch_size = real_imgs.shape[0]
        fake_imgs = tf.random.uniform((batch_size, 32, 32, 1)) * 2 - 1
        inp_imgs = tf.concat([real_imgs, fake_imgs], axis=0)
        real_out, fake_out = tf.split(self.model(inp_imgs), 2, axis=0)
        cdiv = tf.reduce_mean(fake_out, axis = 0) - tf.reduce_mean(
            real_out, axis = 0
        )
        self.cdiv_loss_metric.update_state(cdiv)
        self.real_out_metric.update_state(tf.reduce_mean(real_out, axis = 0))
        self.fake_out_metric.update_state(tf.reduce_mean(fake_out, axis = 0))
        return {m.name: m.result() for m in self.metrics[2:]}

ebm = EBM()
ebm.compile(optimizer=optimizers.Adam(learning_rate=0.0001), run_eagerly=True)
ebm.fit(x_train, epochs=60, validation_data = x_test,)
```
- 1. 在真实图像中添加少量随机噪声，以避免模型对训练集过拟合。
- 2. 从缓冲区中采样一组伪图像。
- 3. 真实图像和伪图像通过模型运行以产生真实分数和伪分数。
- 4. 对比散度损失只是真实观测分数与伪观测分数之间的差值。
- 5. 添加正则化损失以避免分数变得过大。
- 6. 计算损失函数相对于网络权重的梯度以进行反向传播。
- 7. test_step 在验证期间使用，并计算一组随机噪声的分数与训练集数据的分数之间的对比散度。它可用于衡量模型训练的良好程度（参见以下章节）。

## 能量基模型的分析

训练过程中的损失曲线和支持指标如图 7-6 所示。

![](img/f0f0f5d89818fdddf117bbe758ac8143_227_0.png)

图 7-6. EBM 训练过程的损失曲线和指标

首先，注意到训练步骤中计算的损失在各轮次中大致恒定且很小。虽然模型在不断改进，但缓冲区中生成的图像质量也在提高，而这些图像需要与训练集中的真实图像进行比较，因此我们不应该期望训练损失显著下降。

因此，为了判断模型性能，我们还设置了一个验证过程，该过程不从缓冲区采样，而是对随机噪声样本进行评分并将其与训练集示例的分数进行比较。如果模型在改进，我们应该看到对比散度在轮次中下降（即它在区分随机噪声和真实图像方面变得更好），如图 7-6 所示。

从 EBM 生成新样本只是从静止开始（随机噪声）运行朗之万采样器大量步数的情况，如示例 7-7 所示。观测被迫沿着评分函数相对于输入的梯度向下移动，使得从噪声中出现一个合理的观测。

## 示例 7-7. 使用 EBM 生成新的观测
```
start_imgs = np.random.uniform(size = (10, 32, 32, 1)) * 2 - 1
gen_img = generate_samples(
    ebm.model,
    start_imgs,
    steps=1000,
    step_size=10,
    noise = 0.005,
    return_img_per_step=True,
)
```

训练 50 个轮次后采样器产生的观测示例如图 7-7 所示。

![](img/f0f0f5d89818fdddf117bbe758ac8143_228_0.png)

图 7-7. 使用 EBM 模型引导梯度下降的朗之万采样器产生的示例

我们甚至可以通过在朗之万采样过程中拍摄当前观测的快照来回放单个观测是如何生成的——如图 7-8 所示。

![](img/f0f0f5d89818fdddf117bbe758ac8143_228_1.png)

图 7-8. 朗之万采样过程中不同步骤的观测快照

## 其他能量基模型

在之前的示例中，我们使用了使用对比散度训练的深度 EBM，并采用朗之万动力学采样器。然而，早期的 EBM 模型并未使用朗之万采样，而是依赖于其他技术和架构。

最早的 EBM 示例之一是 *玻尔兹曼机*。$^{6}$ 这是一个全连接的无向神经网络，其中二进制单元要么是 *可见* (*v*) 要么是 *隐藏* (*h*)。网络给定配置的能量定义如下：

$E_{\theta}(v, h) = -\frac{1}{2}\left(v^{T} L v + h^{T} J h + v^{T} W h\right)$

其中 $W, L, J$ 是模型学习到的权重矩阵。训练通过对比散度实现，但使用吉布斯采样在可见层和隐藏层之间交替，直到找到平衡。在实践中，这非常缓慢且无法扩展到大量隐藏单元。

![](img/f0f0f5d89818fdddf117bbe758ac8143_229_0.png)

请参阅 Jessica Stringham 的博客文章 "Gibbs Sampling in Python"，其中提供了吉布斯采样的一个优秀简单示例。

该模型的扩展是 *受限玻尔兹曼机* (RBM)，它去除了同类型单元之间的连接，从而创建了一个两层二分图。这使得 RBM 可以堆叠成 *深度信念网络* 以建模更复杂的分布。然而，由于仍需要长时间混合的吉布斯采样，使用 RBM 建模高维数据仍然不切实际。

直到 2000 年代后期，才证明 EBM 有潜力建模更高维的数据集，并建立了构建深度 EBM 的框架。$^{7}$ *朗之万动力学* 成为 EBM 的首选采样方法，后来演变为一种称为 *评分匹配* 的训练技术。这进一步发展为一种称为 *去噪扩散概率模型* 的模型类别，它为 DALL.E 2 和 ImageGen 等最先进的生成模型提供动力。我们将在第 8 章更详细地探讨扩散模型。

## 摘要

能量基模型是一类生成模型，使用能量评分函数——一个神经网络，其训练输出真实观测的低分数和生成观测的高分数。计算该评分函数给出的概率分布需要通过不可处理的分母进行归一化。EBM 通过利用两个技巧来避免这个问题：用于训练网络的对比散度以及用于采样新观测的朗之万动力学。

能量函数通过最小化生成样本分数与训练数据分数之间的差异进行训练，该技术称为对比
