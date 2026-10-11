

# GAN 训练实现与挑战

## 损失函数

```python
cross_entropy = tf.keras.losses.BinaryCrossentropy(from_logits=True)

def discriminator_loss(real_output, fake_output):
    real_loss = cross_entropy(tf.ones_like(real_output), real_output)
    fake_loss = cross_entropy(tf.zeros_like(fake_output), fake_output)
    total_loss = real_loss + fake_loss
    return total_loss

def generator_loss(fake_output):
    return cross_entropy(tf.ones_like(fake_output), fake_output)
```

## 梯度计算

为了计算更新参数所需的梯度，我们可以使用两个梯度带：一个用于生成器，另一个用于判别器，因为它们是分别更新的。这两个带将分别用于计算相对于判别器参数和生成器参数的梯度，如以下代码所示：

```python
noise_dim = 100
G = generator(noise_dim)
D = discriminator()
noise = tf.random.normal([BATCH_SIZE, noise_dim])

with tf.GradientTape() as gen_tape, tf.GradientTape() as disc_tape:
    generated_images = G(noise, training=True)
    real_output = D(images, training=True)
    fake_output = D(generated_images, training=True)

    gen_loss = generator_loss(fake_output)
    disc_loss = discriminator_loss(real_output, fake_output)

gradients_of_G = gen_tape.gradient(gen_loss, G.trainable_variables)
gradients_of_D = disc_tape.gradient(disc_loss, D.trainable_variables)
```

## 结果

结果如 [图 12.12](#c12.xhtml#fig12_12) 所示：

![](images/Image49323.jpg)

**图 12.12：** DCGAN 生成器在 Celeba 人脸数据集上的输出

# GAN 训练挑战

尽管从理论上证明了 GAN 的收敛性，但在实践中，达到这种极大极小博弈的均衡状态相当困难。通常，GAN 训练会遭遇三类问题：

1.  模型不收敛，且由于具有连续高维参数的非凸目标，训练过程不稳定。
2.  **模式崩溃**：生成器产生的图像种类很少，但图像质量很好，因此能够欺骗判别器。但这样的生成器毫无用处，因为它无法表征复杂的真实世界数据分布。生成器的所有输出都趋向于判别器当前认可为真实图像的单一点。一个可能的原因是，当我们相对于生成器进行最小化，然后相对于判别器进行最大化时，我们保持判别器不变，使得空间中的单个区域成为最可能为真实的点。
3.  生成器梯度消失导致训练缓慢。拥有一个完美的判别器时，模型对来自生成器的所有图像将有 `D(x) = 0`；因此，呈现给生成器的梯度为零，生成器不会发生任何更新。

# 缓解 GAN 训练问题的解决方案

以下是一些缓解 GAN 训练问题的技术：

## 特征匹配

可以约束生成器生成与真实数据某些描述性统计量（如均值和方差）相匹配的数据。我们使用一个额外的目标来训练生成器，使其匹配判别器中间层特征的期望值。这将防止判别器过拟合并缓解梯度消失问题。设 `f(x)` 表示判别器中间层的激活值。对于 DCGAN，我们可以取网络末端的任意全连接稠密层。生成器目标函数中的新项为 ![](images/2883.jpg)。

设 `conv2d_2` 为判别器中拥有 512 个滤波器的第二个卷积层的名称。我们可以将此层用作 `f(x)`，如以下代码所示，并更新生成器损失：

```python
from tensorflow.keras import Model
intermediate_D = Model(D.inputs, D.get_layer('conv2d_2').output)

def generator_loss(real_output, fake_output):
    features_fake = tf.reduce_mean(intermediate_D(fake_output))
    features_real = tf.reduce_mean(intermediate_D(real_output))

    return cross_entropy(tf.ones_like(fake_output), fake_output) \
        + tf.square(tf.norm(features_fake - features_real))
```

## 小批量判别

为避免模式崩溃，我们可以让判别器模型组合查看多个生成样本，而不是孤立地查看单个样本。其思想是：真实数据集的随机样本将拥有一组多样化的图像，因此真实图像的一个小批量将是多样化的。因此，如果我们以某种方式测量真实随机样本的图像的批内相似度，我们应该得到一个非常低的相似度分数。如果生成器足够好，来自生成器的样本也应具备这些特征。为了测量批内相似度，取判别器中间层的输出 `f(x)`，然后使用随机投影（如保距操作）将层输出投影到低维空间。

假设 `f(x)` 是 `L` 维向量，我们选择一个维度为 ![](images/2884.jpg) 的正交投影矩阵 `M`，则 ![](images/2885.jpg) 是一个 `d` 维向量，其中 ![](images/2886.jpg)。

对于大小为 `n` 的小批量中的每个样本 ![](images/2148.jpg)，我们现在都有一个低维表示 ![](images/2888.jpg)。对于每个样本 ![](images/890.jpg)，我们可以计算 ![](images/2148.jpg) 与任何其他样本 ![](images/2891.jpg) 之间的 L1 距离，即 ![](images/2892.jpg)。现在，相似度是距离的倒数，因此我们可以应用负指数来获得相似度值，并将两个样本 ![](images/890.jpg) 和 ![](images/2894.jpg) 之间的相似度表示为 ![](images/2895.jpg)。为了获得图像的批内相似度分数，我们可以将所有这些相似度度量相加，为每个图像 ![](images/2148.jpg) 得到一个实数 ![](images/2896.jpg) ![](images/2897.jpg)。

如果一个批次包含外观相似的图像，我们可以预期这些量会非常高；如果小批量是多样化的，所有 ![](images/2899.jpg) 的值将非常低。现在，我们不使用单个投影矩阵，而是可以取一组 `K` 个这样的低维投影矩阵，从而为每个图像获得一个批内相似度分数向量，而不是单个标量 ![](images/2900.jpg)。为了实现这一点，我们用一个维度为 ![](images/2902.jpg) 的不同矩阵 `K` 左乘 ![](images/2148.jpg)。

这种方法的一种用于紧凑实现的替代方式是堆叠所有 `K` 个投影矩阵，创建一个维度为 ![](images/2903.jpg) 的张量 `T`。例如，如果 `K=2`，我们可以从 2 个随机矩阵 `M1` 和 `M2` 创建 `T`，如以下代码所示：

```python
M1 = tf.random.uniform([L, d])
M2 = tf.random.uniform([L, d])
T = tf.concat([tf.expand_dims(M1, axis=1),
               tf.expand_dims(M2, axis=1)], axis=1)
```

将向量 `f(`![](images/2148.jpg)`)` 与张量 `T` 相乘，我们得到一个维度为 ![](images/2906.jpg) 的矩阵 ![](images/2905.jpg)，这可以使用 TensorFlow 中的爱因斯坦求和运算来完成，如以下代码所示：

```python
fx = tf.random.uniform([n, L])
T = tf.random.uniform([L, K, d])
features = tf.einsum('ij,jkl->ikl', fx, T)
```

这里，`K` 行具有 `K` 个维度为 `d` 的 `f(xi)` 投影。对于每个 `xj`，我们得到 ![](images/2907.jpg)，因此，为了计算成对距离，我们可以计算跨样本 ![](images/2909.jpg) 的结果矩阵 ![](images/2907.jpg) 对应行之间的 L1 距离，如 [图 12.13](#c12.xhtml#fig12_13) 所示：

![](images/Image49330.jpg)

**图 12.13：** 小批量判别

L1 距离的计算及负指数运算如以下代码所示：

