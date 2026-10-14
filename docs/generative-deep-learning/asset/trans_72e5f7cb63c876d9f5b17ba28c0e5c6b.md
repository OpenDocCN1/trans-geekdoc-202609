

![](img/f0f0f5d89818fdddf117bbe758ac8143_207_0.png)

Figure 6-9. 堆叠耦合层，并在每层交替掩码

## 训练 RealNVP 模型

现在我们已经构建了 RealNVP 模型，可以训练它来学习双月数据集的复杂分布。记住，我们希望最小化模型下数据的负对数似然 – log p_X(x)。使用公式 6-1，我们可以将其写为如下形式：

- log p_X(x) = - log p_Z(z) - log |det(∂z/∂x)|

我们选择前向过程 f 的目标输出分布 p_Z(z) 为标准高斯分布，因为我们可以轻松地从该分布中采样。然后，我们可以通过应用逆过程 g，将从高斯分布中采样的点转换回原始图像域，如图 6-10 所示。

![](img/f0f0f5d89818fdddf117bbe758ac8143_207_1.png)

Figure 6-10. 在 1D（中间行）和 2D（底部行）中在复杂分布 p_X(x) 与简单高斯分布 p_Z(z) 之间进行转换

示例 6-3 展示了如何作为自定义 Keras 模型构建 RealNVP 网络。

### 示例 6-3. 在 Keras 中构建 RealNVP 模型

```
class RealNVP(models.Model):
    def __init__(self, input_dim, coupling_layers, coupling_dim, regularization):
        super(RealNVP, self).__init__()
        self.coupling_layers = coupling_layers
        self.distribution = tfp.distributions.MultivariateNormalDiag(
            loc=[0.0, 0.0], scale_diag=[1.0, 1.0]
        ) ①
        self.masks = np.array(
            [[0, 1], [1, 0]] * (coupling_layers // 2), dtype="float32"
        ) ②
        self.loss_tracker = metrics.Mean(name="loss")
        self.layers_list = [
            Coupling(input_dim, coupling_dim, regularization)
            for i in range(coupling_layers)
        ] ③

    @property
    def metrics(self):
        return [self.loss_tracker]

    def call(self, x, training=True):
        log_det_inv = 0
        direction = 1
        if training:
            direction = -1
        for i in range(self.coupling_layers)[::direction]: ④
            x_masked = x * self.masks[i]
            reversed_mask = 1 - self.masks[i]
            s, t = self.layers_list[i](x_masked)
            s *= reversed_mask
            t *= reversed_mask
            gate = (direction - 1) / 2
            x = (
                reversed_mask
                * (x * tf.exp(direction * s) + direction * t * tf.exp(gate * s))
                + x_masked
            ) ⑤
            log_det_inv += gate * tf.reduce_sum(s, axis = 1) ⑥
        return x, log_det_inv

    def log_loss(self, x):
        y, logdet = self(x)
        log_likelihood = self.distribution.log_prob(y) + logdet ⑦
        return -tf.reduce_mean(log_likelihood)

    def train_step(self, data):
        with tf.GradientTape() as tape:
            loss = self.log_loss(data)
            g = tape.gradient(loss, self.trainable_variables)
            self.optimizer.apply_gradients(zip(g, self.trainable_variables))
            self.loss_tracker.update_state(loss)
            return {"loss": self.loss_tracker.result()}

    def test_step(self, data):
        loss = self.log_loss(data)
        self.loss_tracker.update_state(loss)
        return {"loss": self.loss_tracker.result()}

model = RealNVP(
    input_dim = 2
  , coupling_layers= 6
  , coupling_dim = 256
  , regularization = 0.01
)

model.compile(optimizer=optimizers.Adam(learning_rate=0.0001))

model.fit(
    normalized_data
  , batch_size=256
  , epochs=300
)
```

- 1. 目标分布是标准二维高斯分布。
- 2. 在这里，我们创建交替的掩码模式。
- 3. 定义 RealNVP 网络的 Coupling 层列表。
- 4. 在网络的主 call 函数中，我们遍历 Coupling 层。如果 training=True，则向前遍历层（即从数据到潜在空间）。如果 training=False，则向后遍历层（即从潜在空间到数据）。
- 5. 该行描述了取决于方向的前向和后向方程（尝试代入 direction = -1 和 direction = 1 来自行验证！）。
- 6. 雅可比矩阵的对数行列式，我们需要计算损失函数，仅仅是缩放因子的总和。
- 7. 损失函数是转换后数据在目标高斯分布下的对数概率与雅可比矩阵对数行列式的负和。

## RealNVP 模型的分析

一旦模型训练完成，我们就可以使用它将训练集转换到潜在空间（使用前向方向 f），更重要的是，将潜在空间中的采样点转换回看起来像是从原始数据分布中采样的点（使用后向方向 g）。

Figure 6-11 显示了在没有任何学习发生之前网络的输出——前向和后向方向几乎没有转换就直接传递信息。

![](img/f0f0f5d89818fdddf117bbe758ac8143_210_0.png)

Figure 6-11. 训练前 RealNVP 模型输入（左）和输出（右），前向过程（上）和逆过程（下）

训练后（图 6-12），前向过程能够将训练集中的点转换为类似高斯的分布。同样，后向过程可以取从高斯分布中采样的点并将其映射回类似原始数据的分布。

![](img/f0f0f5d89818fdddf117bbe758ac8143_211_0.png)

Figure 6-12. 训练后 RealNVP 模型输入（左）和输出（右），前向过程（上）和逆过程（下）

训练过程的损失曲线如图 6-13 所示。

![](img/f0f0f5d89818fdddf117bbe758ac8143_211_1.png)

Figure 6-13. RealNVP 训练过程的损失曲线

这完成了我们对 RealNVP 的讨论，RealNVP 是归一化流生成模型的一个特例。在下一节中，我们将介绍一些扩展了 RealNVP 论文中引入思想的现代归一化流模型。

## 其他归一化流模型

另外两个成功且重要的归一化流模型是 GLOW 和 FFJORD。以下各节描述了它们取得的关键进展。

### GLOW

在 NeurIPS 2018 上发表，GLOW 是最早展示归一化流生成高质量样本并产生可遍历以操纵样本的有意义潜在空间能力的模型之一。关键步骤是用可逆的 1 × 1 卷积层取代反向掩码设置。例如，将 RealNVP 应用于图像时，通道的顺序在每一步后都会翻转，以确保网络有机会转换所有输入。在 GLOW 中则应用 1 × 1 卷积，它有效地充当了一种通用方法，可生成模型期望的通道的任意排列。作者表明，即使有此改进，整体分布仍然是可处理的，其行列式和逆在规模上易于计算。

![](img/f0f0f5d89818fdddf117bbe758ac8143_212_0.png)

Figure 6-14. 来自 GLOW 模型的随机样本（来源：Kingma and Dhariwal, 2018）²

### FFJORD

RealNVP 和 GLOW 是离散时间归一化流——即它们通过一组离散的耦合层转换输入。FFJORD（可扩展可逆生成模型的自由形式连续动力学），于 ICLR 2019 提出，展示了如何将转换建模为连续时间过程（即通过使流中的步数趋于无穷大且步长趋于零的极限）。在这种情况下，动力学使用常微分方程（ODE）建模，其参数由神经网络 ($f_\theta$) 生成。黑盒求解器用于在时间 $t_1$ 求解 ODE——即在 $t_0$ 从高斯分布采样初始点 $z_0$ 的情况下找到 $z_1$，如以下方程所述：

$z_0 \sim p(z_0)$

$\frac{\partial z(t)}{\partial t} = f_\theta(x(t), t)$

$x = z_1$

转换过程的示意图如图 6-15 所示。

![](img/f0f0f5d89818fdddf117bbe758ac8143_213_0.png)

Figure 6-15. FFJORD 通过神经网络参数化的常微分方程对数据分布与标准高斯之间的转换进行建模（来源：Will Grathwohl et al., 2018）³

