
```python
class VAE(models.Model):
    def __init__(self, encoder, decoder, **kwargs):
        super(VAE, self).__init__(**kwargs)
        self.encoder = encoder
        self.decoder = decoder
        self.total_loss_tracker = metrics.Mean(name="total_loss")
        self.reconstruction_loss_tracker = metrics.Mean(
            name="reconstruction_loss"
        )
        self.kl_loss_tracker = metrics.Mean(name="kl_loss")

    @property
    def metrics(self):
        return [
            self.total_loss_tracker,
            self.reconstruction_loss_tracker,
            self.kl_loss_tracker,
        ]

    def call(self, inputs):
        z_mean, z_log_var, z = encoder(inputs)
        reconstruction = decoder(z)
        return z_mean, z_log_var, reconstruction

    def train_step(self, data):
        with tf.GradientTape() as tape:
            z_mean, z_log_var, reconstruction = self(data)
            reconstruction_loss = tf.reduce_mean(
                500
                * losses.binary_crossentropy(
                    data, reconstruction, axis=(1, 2, 3)
                )
            )
            kl_loss = tf.reduce_mean(
                tf.reduce_sum(
                    -0.5
                    * (1 + z_log_var - tf.square(z_mean) - tf.exp(z_log_var)),
                    axis = 1,
                )
            )
            total_loss = reconstruction_loss + kl_loss

            grads = tape.gradient(total_loss, self.trainable_weights)

        self.optimizer.apply_gradients(zip(grads, self.trainable_weights))

        self.total_loss_tracker.update_state(total_loss)
        self.reconstruction_loss_tracker.update_state(reconstruction_loss)
        self.kl_loss_tracker.update_state(kl_loss)

        return {m.name: m.result() for m in self.metrics}
```

```python
vae = VAE(encoder, decoder)
vae.compile(optimizer="adam")
vae.fit(
    train,
    epochs=5,
    batch_size=100
)
```

1. 此函数描述了当我们在特定输入图像上调用 `VAE` 时我们希望返回的内容。
2. 此函数描述了 `VAE` 的一个训练步骤，包括损失函数的计算。
3. 重建损失中使用了 500 的 beta 值。
4. 总损失是重建损失和 KL 散度损失之和。

![](img/f0f0f5d89818fdddf117bbe758ac8143_109_0.png)

### 梯度带

TensorFlow 的 *Gradient Tape* 是一种机制，允许计算在模型前向传播期间执行的运算的梯度。要使用它，你需要将要进行微分的运算代码包装在 `tf.GradientTape()` 上下文中。一旦记录了运算，你就可以通过调用 `tape.gradient()` 来计算损失函数相对于某些变量的梯度。然后可以使用这些梯度通过优化器更新变量。

该机制对于计算自定义损失函数的梯度（正如我们在这里所做的）以及创建自定义训练循环非常有用，正如我们在第 4 章中将看到的那样。

### 变分自编码器的分析

现在我们已经训练好了 VAE，可以使用编码器对测试集中的图像进行编码，并在潜在空间中绘制 `z_mean` 值。我们也可以从标准正态分布中采样以在潜在空间中生成点，并使用解码器将这些点解码回像素空间，以查看 VAE 的表现。

图 3-13 显示了新的潜在空间的结构，以及一些采样点及其解码后的图像。我们可以立即看到潜在空间组织方式的几个变化。

![](img/f0f0f5d89818fdddf117bbe758ac8143_110_0.png)

图 3-13. 新的潜在空间：黑色点显示每个编码图像的 `z_mean` 值，而蓝色点显示潜在空间中的一些采样点（右侧为其解码后的图像）

首先，KL 散度损失项确保编码图像的 `z_mean` 和 `z_log_var` 值不会偏离标准正态分布太远。其次，由于编码器现在是随机的而非确定性的，潜在空间现在更加连续，因此不良形成的图像不再那么多。

最后，通过按服装类型对潜在空间中的点进行着色（图 3-14），我们可以看出没有任何一种类型受到偏爱。右侧的图显示了空间转换后的 p 值——我们可以看出每种颜色大致相等地分布。再次强调，重要的是要记住标签在训练期间根本没有使用；VAE 已自行学习了各种服装形式以帮助最小化重建损失。

![](img/f0f0f5d89818fdddf117bbe758ac8143_111_0.png)

图 3-14. 按服装类型着色的 VAE 潜在空间

### 探索潜在空间

到目前为止，我们对自编码器和变分自编码器的工作都局限于二维潜在空间。这帮助我们在页面上可视化 VAE 的内部工作原理，并理解我们对自编码器架构所做的微小调整如何将其转变为可用于生成建模的更强大的网络类别。

现在让我们把注意力转向一个更复杂的数据集，看看当我们增加潜在空间的维度时，变分自编码器能取得怎样令人惊叹的效果。

![](img/f0f0f5d89818fdddf117bbe758ac8143_111_1.png)

### 运行本示例的代码

本示例的代码可在书籍仓库中的 Jupyter notebook `notebooks/03_vae/03_faces/vae_faces.ipynb` 中找到。

### CelebA 数据集

我们将使用 CelebFaces Attributes（CelebA）数据集来训练下一个变分自编码器。这是一个包含超过 200,000 张名人面部彩色图像的集合，每张图像都标注了各种标签（例如，戴帽子、微笑等）。图 3-15 显示了一些示例。

![](img/f0f0f5d89818fdddf117bbe758ac8143_112_0.png)

图 3-15. 来自 CelebA 数据集的一些示例（来源：Liu et al., 2015）³

当然，我们不需要标签来训练 VAE，但当我们开始探索这些特征如何在多维潜在空间中被捕获时，它们将很有用。一旦我们的 VAE 训练完成，我们就可以从潜在空间中采样以生成新的名人面部示例。

CelebA 数据集也通过 Kaggle 提供，因此您可以运行书籍仓库中的 Kaggle 数据集下载脚本来下载数据集，如示例 3-14 所示。这将把图像和随附的元数据本地保存到 `/data` 文件夹。

#### 示例 3-14. 下载 CelebA 数据集

```bash
bash scripts/download_kaggle_data.sh jessicali9530 celeba-dataset
```

我们使用 Keras 函数 `image_dataset_from_directory` 来创建一个指向存储图像的目录的 TensorFlow Dataset，如示例 3-15 所示。这允许我们仅在需要时（例如在训练期间）将图像批读取到内存中，因此我们可以处理大型数据集，而不必担心将整个数据集装入内存。它还将图像调整为 64 × 64，并在像素值之间进行插值。

#### 示例 3-15. 预处理 CelebA 数据集

```python
train_data = utils.image_dataset_from_directory(
    "/app/data/celeba-dataset/img_align_celeba/img_align_celeba",
    labels=None,
    color_mode="rgb",
    image_size=(64, 64),
    batch_size=128,
    shuffle=True,
    seed=42,
    interpolation="bilinear",
)
```

原始数据按范围 [0, 255] 缩放以表示像素强度，我们将其重新缩放到范围 [0, 1]，如示例 3-16 所示。

#### 示例 3-16. 预处理 CelebA 数据集

```python
def preprocess(img):
    img = tf.cast(img, "float32") / 255.0
    return img

train = train_data.map(lambda x: preprocess(x))
```

### 变分自编码器的训练

人脸模型的网络架构与 Fashion-MNIST 示例类似，但有几个细微差异：

- 我们的数据现在有三个输入通道（RGB）而不是一个（灰度）。这意味着我们需要将解码器中最后的卷积转置层的通道数改为 3。
- 我们将使用 200 维的潜在空间而不是 2 维。由于人脸比 Fashion-MNIST 图像复杂得多，我们增加了潜在空间的维度，以便网络能够从图像中编码足够多的细节。
- 每个卷积层之后都有批归一化层以稳定训练。即使每个批次运行时间更长，达到相同损失所需的批次数量大大减少。
- 我们将 KL 散度的 β 因子增加到 2,000。这是一个需要调优的参数；对于该数据集和架构，该值被发现能产生良好的结果。

编码器和解码器的完整架构分别显示在表 3-5 和表 3-6 中。

#### 表 3-5. VAE 人脸编码器模型摘要

| 层（类型） | 输出形状 | 参数数 | 连接至 |
|---|---|---|---|
| `InputLayer (input)` | `(None, 32, 32, 3)` | 0 | `[]` |
| `Conv2D (conv2d_1)` | `(None, 16, 16, 128)` | 3,584 | `[input]` |
| `BatchNormalization (bn_1)` | `(None, 16, 16, 128)` | 512 | `[conv2d_1]` |
| `LeakyReLU (lr_1)` | `(None, 16, 16, 128)` | 0 | `[bn_1]` |
| `Conv2D (conv2d_2)` | `(None, 8, 8, 128)` | 147,584 | `[lr_1]` |
| `BatchNormalization (bn_2)` | `(None, 8, 8, 128)` | 512 | `[conv2d_2]` |
| `LeakyReLU (lr_2)` | `(None, 8, 8, 128)` | 0 | `[bn_2]` |
| `Conv2D (conv2d_3)` | `(None, 4, 4, 128)` | 147,584 | `[lr_2]` |
| `BatchNormalization (bn_3)` | `(None, 4, 4, 128)` | 512 | `[conv2d_3]` |
| `LeakyReLU (lr_3)` | `(None, 4, 4, 128)` | 0 | `[bn_3]` |
| `Conv2D (conv2d_4)` | `(None, 2, 2, 128)` | 147,584 | `[lr_3]` |
| `BatchNormalization (bn_4)` | `(None, 2, 2, 128)` | 512 | `[conv2d_4]` |
| `LeakyReLU (lr_4)` | `(None, 2, 2, 128)` | 0 | `[bn_4]` |
| `Flatten (flatten)` | `(None, 512)` | 0 | `[lr_4]` |
| `Dense (z_mean)` | `(None, 200)` | 102,600 | `[flatten]` |
| `Dense (z_log_var)` | `(None, 200)` | 102,600 | `[flatten]` |
| `Sampling (z)` | `(None, 200)` | 0 | `[z_mean, z_log_var]` |

总参数 653,584  
可训练参数 652,560  
不可训练参数 1,024

#### 表 3-6. VAE 人脸解码器模型摘要

| 层（类型） | 输出形状 | 参数数 |
|---|---|---|
| `InputLayer` | `(None, 200)` | 0 |
| `Dense` | `(None, 512)` | 102,912 |
| `BatchNormalization` | `(None, 512)` | 2,048 |
| `LeakyReLU` | `(None, 512)` | 0 |
| `Reshape` | `(None, 2, 2, 128)` | 0 |
| `Conv2DTranspose` | `(None, 4, 4, 128)` | 147,584 |
| `BatchNormalization` | `(None, 4, 4, 128)` | 512 |
| `LeakyReLU` | `(None, 4, 4, 128)` | 0 |
| `Conv2DTranspose` | `(None, 8, 8, 128)` | 147,584 |
| `BatchNormalization` | `(None, 8, 8, 128)` | 512 |
| `LeakyReLU` | `(None, 8, 8, 128)` | 0 |
| `Conv2DTranspose` | `(None, 16, 16, 128)` | 147,584 |
| `BatchNormalization` | `(None, 16, 16, 128)` | 512 |
| `LeakyReLU` | `(None, 16, 16, 128)` | 0 |
| `Conv2DTranspose` | `(None, 32, 32, 128)` | 147,584 |
| `BatchNormalization` | `(None, 32, 32, 128)` | 512 |
| `LeakyReLU` | `(None, 32, 32, 128)` | 0 |
| `Conv2DTranspose` | `(None, 32, 32, 3)` | 3,459 |

总参数 700,803  
可训练参数 698,755  
不可训练参数 2,048

训练大约五个 epoch 后，我们的 VAE 应该能够生成名人面部的全新图像！

### 变分自编码器的分析

首先，让我们看一下重建人脸的样本。图 3-16 中的顶行显示原始图像，底行显示它们经过编码器和解码器后的重建结果。

![](img/f0f0f5d89818fdddf117bbe758ac8143_115_0.png)

图 3-16. 经过编码器和解码器后的重建人脸

我们可以看出 VAE 已成功捕捉到每张面部的关键特征——头部角度、发型、表情等。一些精细细节缺失，但重要的是要记住构建变分自编码器的目标并不是实现完美的重建损失。我们的最终目标是从潜在空间中采样以生成新的人脸。

为了实现这一点，我们必须检查潜在空间中点的分布是否近似于多元标准正态分布。如果我们看到任何维度与标准正态分布显著不同，我们可能应该降低重建损失因子，因为 KL 散度项的影响还不够。

我们潜在空间中的前 50 个维度如图 3-17 所示。没有哪个分布明显不同于标准正态分布，因此我们可以继续生成一些人脸！

![](img/f0f0f5d89818fdddf117bbe758ac8143_116_0.png)

图 3-17. 潜在空间中前 50 个维度的点分布

### 生成新的人脸

要生成新的人脸，我们可以使用示例 3-17 中的代码。

#### 示例 3-17. 从潜在空间生成新的人脸

```python
grid_width, grid_height = (10,3)
z_sample = np.random.normal(size=(grid_width * grid_height, 200))

reconstructions = decoder.predict(z_sample)

fig = plt.figure(figsize=(18, 5))
fig.subplots_adjust(hspace=0.4, wspace=0.4)
for i in range(grid_width * grid_height):
    ax = fig.add_subplot(grid_height, grid_width, i + 1)
    ax.axis("off")
    ax.imshow(reconstructions[i, :, :])
```

1. 从 200 维的标准多元正态分布中采样 30 个点。
2. 解码采样得到的点。
3. 绘制图像！
