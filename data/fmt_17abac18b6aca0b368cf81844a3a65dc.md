
在 GAN 训练中，`f(x)` 是判别器的神经网络函数，但必须保证其满足上述 `1-Lipschitz` 函数的条件。在 WGAN 原始论文中，这是通过**权重裁剪**这一实用技巧限制权重参数大小来保证的，即将权重参数限制在某个范围 `[−c, c]` 内，通常 `c=0.01`。也可设为 `c=0.1` 或 `c=0.001`，即 `c` 也是一个需要调试的参数。

对于判别器，要使公式 (8-29) 取上确界，即使 `𝔼[x ∼ P[r]]f(x) − 𝔼[x ∼ P[θ]]f(x)` 取最大值。可用梯度上升法更新其参数（如 `w`），甚至使 Wasserstein 距离尽可能大，以提高区分真实数据与生成数据的能力。生成器希望最小化 Wasserstein 距离，因此其参数（如 `θ`）用梯度下降法更新。对生成器而言，公式 (8-29) 的第一项与其无关，即只需使 `−𝔼[x ∼ P[θ]]f(x)` 最小化。

WGAN 的损失函数是 `f(x)` 或 `−f(x)` 的和，损失函数关于 `f(x)` 的梯度为 `1`（或 `-1`）。因此，WGAN 的损失函数及其梯度计算更简单。只需在 GAN 代码中稍微修改计算损失函数和计算损失函数关于 `f(x)` 的梯度的代码即可。下面是 WGAN 算法的伪代码，如图 8-33 所示：

图 8-33 WGAN 算法伪代码。

后来又提出了一些改进的 WGAN，如 Improved WGAN (WGAN-GP)，它在损失函数中增加了梯度惩罚项，代替裁剪权重参数。

$$L(p_{r},p_{g}) = \mathbb{E}_{\overset{\sim}{x} \sim p_{g}}[f(\overset{\sim}{x})] - \mathbb{E}_{x \sim p_{r}}[f(x))] + \mathbb{E}_{\hat{x} \sim p_{\hat{x}}}[{(| \parallel \nabla f(\hat{x}) \parallel_{2} - 1)}^{2}]$$

其中，`𝔼[x̃ ∼ p[g]][f(x̃)] − 𝔼[x ∼ p[r]][f(x)]` 为负 Wasserstein 距离 `−W(p[g], p[r])`，`𝔼[x̂ ∼ p[x̂]][(|∥∇f(x̂)∥[2] − 1)²]` 为梯度惩罚项，它尽可能将梯度的绝对值限制为单位长度，从而防止梯度爆炸和消失。

权重参数裁剪主要是防止权重参数过大，以保证神经网络函数仍为 `1-Lipschitz` 函数。梯度惩罚项类似于前面模型参数的正则项，也是防止梯度更新过程中梯度爆炸导致参数变大，将梯度限制在一定范围内也保证了模型参数限制在一定范围内。

近期实践表明，WGAN 和 WGAN GP 实际上并不优于 GAN，因此在实践中，人们仍习惯使用最原始的 GAN。

### 8.7.2 WGAN 代码实现

根据 WGAN 的损失函数，对之前的 `D_train()` 和 `G_train()` 函数稍作修改，即可得到使用 WGAN 损失的判别器和生成器训练函数 `WGAN_D_train()` 和 `WGAN_G_train()`：

#### WGAN 训练代码实现

##### 判别器单轮训练

```python
def WGAN_D_train(D, D_optimizer, x_real, x_fake, clip_value=0.01, reg=1e-3):
    assert x_real.shape[0] == x_fake.shape[0]

    # 1. 梯度清零
    D_optimizer.zero_grad()

    # 2. 计算损失和梯度
    f_real = D(x_real)
    m = f_real.size
    real_loss = np.mean(f_real)
    real_grad = (1 / m) * np.ones(f_real.shape)
    D.backward(-real_grad, reg)

    f_fake = D(x_fake)
    assert f_fake.size == f_real.size
    fake_loss = np.mean(f_fake)
    fake_grad = (1 / m) * np.ones(f_fake.shape)
    D.backward(fake_grad, reg)

    loss = real_loss - fake_loss
    # loss += D.reg_loss(reg)

    # 3. 更新梯度
    D_optimizer.step()

    # 4. 权重裁剪
    for i, _ in enumerate(D_optimizer.params):
        D_optimizer.params[i][0][:] = np.clip(D_optimizer.params[i][0], -clip_value, clip_value)

    return loss
```

##### 生成器单轮训练

```python
def WGAN_G_train(D, G, G_optimizer, z, clip_value=0.01, reg=1e-3):
    # 1. 梯度清零
    G_optimizer.zero_grad()

    # 2. 计算损失和梯度
    x_fake = G(z)
    f_fake = D(x_fake)

    loss = -np.mean(f_fake)
    m = f_fake.size
    grad = -(1 / m) * np.ones(f_fake.shape)

    grad = D.backward(grad)
    G.backward(grad, reg)

    # loss += G.reg_loss(reg)

    # 3. 更新梯度
    G_optimizer.step()

    return loss
```

##### WGAN 完整训练流程

```python
def WGAN_train(D, G, D_optimizer, G_optimizer, real_dataset, noise_z, iterations=10000, reg=1e-3,
               clip_value=0.01, n_critic=4, show_result=None, print_n=20):
    iter = 0
    D_losses = []
    G_losses = []

    while iter < iterations:
        # 训练判别器
        x_real = next(real_dataset)
        x_fake = G(next(noise_z))
        D_loss = WGAN_D_train(D, D_optimizer, x_real, x_fake, clip_value, reg)

        # 训练生成器
        if iter % n_critic == 0:
            G_loss = WGAN_G_train(D, G, G_optimizer, next(noise_z), clip_value, reg)

        if iter % print_n == 0:
            print(iter, "iter:", "D_loss", D_loss, "G_loss", G_loss)
            D_losses.append(D_loss)
            G_losses.append(G_loss)

            if show_result:
                show_result(D, G, D_losses, G_losses)

        iter += 1

    return D_losses, G_losses
```

#### 第 8.5.1 节实数集合 GAN 模型的 WGAN 训练示例

对于第 8.5.1 节中包含一组实数的 GAN 模型，可以使用上述 WGAN 损失函数进行训练，代码如下：

```python
from NeuralNetwork import *
# from util import *

np.random.seed(0)

hidden = 4

D = NeuralNetwork()
D.add_layer(Dense(1, hidden))
D.add_layer(Leaky_relu(0.2))  # Relu()
D.add_layer(Dense(hidden, 1))
# D.add_layer(Sigmoid())

G = NeuralNetwork()
z_dim = 1  # 隐变量维度
G.add_layer(Dense(z_dim, hidden))
G.add_layer(Leaky_relu(0.2))  # Relu()
G.add_layer(Dense(hidden, 1))

# 定义 G 和 D 的优化器对象
D_lr = 0.0003  # 1e-4
G_lr = 0.0001  # 1e-4
beta_1, beta_2 = 0.9, 0.999

D_optimizer = Adam(D.parameters(), D_lr, beta_1, beta_2)
G_optimizer = Adam(G.parameters(), G_lr, beta_1, beta_2)

from util import *

clip_value = 0.01
reg = 0  # 1e-5
iterations = 200000  # 100000
n_critic = 1  # 5
print_n = 500

D_losses, G_losses = WGAN_train(D, G, D_optimizer, G_optimizer, data_it, noise_it, iterations, reg,
                                clip_value, n_critic, show_result, print_n)
```

#### 最终训练结果

```
...
500 iter: D_loss 0.0011615003991261863 G_loss -0.01023799847202126
27000 iter: D_loss -8.578426744787482e-07 G_loss -0.009488053321470099
...
90000 iter: D_loss 1.3109091936969186e-11 G_loss -0.009999930339860416
...
199500 iter: D_loss 4.4971589611975116e-09 G_loss -0.01000896809522164
```

![](img/file200.png "fig:")

图 8-33 针对一组实数问题的 WGAN 训练结果

`D_loss` 是生成数据分布与真实数据分布之间的 Wasserstein 距离，它随着迭代收敛到 0，表明逐渐收敛。

## 8.8 深度卷积对抗网络 DCGAN

最基本的 GAN 是使用全连接神经网络来表示判别器和生成器函数。对于图像等具有空间结构的数据，GAN 的训练不稳定，难以生成高质量的生成数据。Radford 等人提出的深度卷积生成对抗网络是基本 GAN 的扩展，适用于具有空间结构的数据。

判别器是一个二分类函数，可以用卷积神经网络表示。该判别器可以通过卷积（包括池化）操作将图像分辨率从高到低不断降低，直到最后的全连接层转换为代表二分类的分数。生成器如何将低维一维隐向量转换为高维多通道图像（特征图）？

普通卷积操作是一种**下采样**，可以将高分辨率特征图转换为低分辨率特征图，但无法将低维隐向量转换为高维图像，而普通卷积操作恰恰相反。**转置卷积**操作属于**上采样**操作，可以将低分辨率特征图转换为高分辨率特征图。转置卷积也称为**分步长卷积**，部分文献也称为**反卷积**（但反卷积与通常数学意义上的反卷积并非同一概念），因此一般使用前两个术语。如图 8-35 所示，使用四个转置卷积层将长度为 100 的向量转换为 3 × 64 × 64 的彩色图像。

图 8-35. 四个转置卷积层将长度为 100 的向量转换为 3 × 64 × 64 的彩色图像。

为了使训练更稳定，DCGAN 论文还做了若干改进：判别器网络移除了全连接层，用步长卷积替代池化操作，生成器和判别器网络均使用批量归一化，生成器除输出层使用 tanh 激活函数外，其余层均使用 ReLU 激活函数，判别器所有层均使用 LeakyReLU 激活函数。

为了实现 DCGAN，必须先实现转置卷积。下面讨论转置卷积的原理和实现。

### 8.8.1 一维向量的转置卷积

对于长度为 5 的输入向量 `x` = (`x`[0], `x`[1], `x`[2], `x`[3], `x`[4])，进行卷积核宽度为 3、步长和填充分别为 1 和 0 的一维卷积，过程如图 8-36 所示：

图 8-36 对长度为 5 的输入向量 `x` = (`x`[0], `x`[1], `x`[2], `x`[3], `x`[4]) 进行卷积核宽度为 3、步长和填充分别为 1 和 0 的一维卷积过程

如果输入向量长度为 `n`，卷积核宽度为 `k`，步长为 `s`、左右填充为 `p` 的卷积操作生成的结果张量长度为 $o = \frac{n - k + 2 * p}{s} + 1$，对上述示例，结果张量长度为 $o = \frac{5 - 3 + 0}{1} + 1 = 3$。即若不填充，卷积结果向量的长度往往小于输入向量的长度。

卷积通过卷积核计算并累加一个与卷积核形状大小相同的数据块以获得一个输出值，即一个数据块与卷积核运算产生一个输出值。卷积核按步长沿数据滑动，遇到的每个对应数据块产生一个输出值。

转置卷积与卷积恰好相反。对于输入张量的每个元素，该元素与卷积核的每个元素相乘，产生一个与卷积核形状相同的输出，即输入张量的每个元素将产生与卷积核元素数量相同的元素，如图 8-37 所示：

图 8-37 转置卷积：对于输入张量的每个元素，将该元素与卷积核的每个元素相乘，产生与卷积核形状相同的输出

宽度为 3 的卷积核与输入 `x` = (`x`[0], `x`[1], `x`[2]) 的第一个元素 `x`[0] 对齐，将此 `x`[0] 与卷积核的每个元素相乘得到输出值，卷积核宽度为 3，因此产生 3 个输出值。若进行步长为 1 的转置卷积，卷积核滑动到 `x`[1] 产生 3 个输出值，直到输入的最后一个元素，如图 8-38 所示：

图 8-38 宽度为 3 的卷积核作用于长度为 3 的输入一维张量生成由 5 个元素组成的一维张量

图 8-39 是一个具体示例，

图 8-39 卷积核 (1,2,-1) 与输入一维张量 (5,15,12) 的转置卷积过程

如图 8-40 所示，在转置卷积操作中，每个元素与卷积核逐元素相乘输出的三个值累加到输出向量对应位置的元素上。

图 8-40 每个元素与卷积核逐元素相乘输出的三个值累加到输出张量对应位置的元素上

如果将图 8-36 中卷积操作的 `z` 作为转置卷积的输入，将 `x` 作为转置卷积的输出，转置计算过程如图 8-41 所示：

图 8-41 转置卷积是卷积的逆过程。将图 8-36 中卷积的输出 `z` 作为转置卷积的输入，转置卷积产生与卷积输入形状相同的输出

可以看出，转置卷积的计算过程是卷积过程的逆过程，正如卷积的逆向推导是卷积的逆过程。因此，转置卷积的计算过程与卷积的逆向推导过程完全相似，通过卷积核将一个输入值分配并累加到输出向量中。

根据卷积输出与输入向量、步长、填充的关系，可以得到转置卷积输出与输入向量、步长、填充的关系。输入张量长度为 o，步长为 s，左右填充为 p 的转置卷积操作生成的结果张量长度为 `n` = (`o` − 1) * `s` + `k` − 2 * `p`。对上述示例中的转置卷积操作，结果张量长度为 (3 − 1) * 1 + 3 − 0 = 5

卷积可以使用矩阵乘法实现其前向计算和逆向推导。因此，转置卷积也可以使用矩阵乘法实现其前向计算和逆向推导。转置卷积的前向计算完全类似于卷积的逆向推导，转置卷积的逆向推导类似于卷积的前向计算。

回顾第 6.3.3 节一维卷积的逆向推导过程，计算公式为：

`dx`[`row`] = `dz`[`row`] * `K`[`col`]^(`T`)

将 `dz`[`row`] 视为转置卷积的输入，`dx`[`row`] 视为转置卷积的输出，可得到转置卷积前向计算的矩阵乘法公式：

`zz`[`row`] = `xx`[`row`] * `K`[`col`]^(`T`)

其中 `xx`[`row`] 为转置卷积的输入，`zz`[`row`] 为转置卷积的输出，`KK`[`col`] 为卷积核的列向量表示。对上述具体示例，计算过程为：

$$

\begin{matrix} {z_{row} = x_{row}k_{col} = \begin{bmatrix} x_{0} \\ x_{1} \\ x_{2} \\ \end{bmatrix}\begin{bmatrix} k_{0} & k_{1} & k_{2} \\ \end{bmatrix} = \begin{bmatrix} 5 \\ 15 \\ 12 \\ \end{bmatrix}\begin{bmatrix} 1 & 2 & {- 1} \\ \end{bmatrix} = \begin{bmatrix} 5 & 15 & 12 \\ 15 & 30 & {- 15} \\ 12 & 24 & {- 12} \\ \end{bmatrix}} \\ \end{matrix}

$$

类似于卷积的逆向推导，该扁平化 `zz`[`row`] 的每一行代表一次分配计算，每一行都需要累加到最终输出 `zz` 的对应位置（如图 8-40 所示）。

将 `zz`[`row`] 转换为 `zz` 的过程可使用卷积逆向推导将 `ddx`[`row`] 转换为 `dxx` 的函数 `row2im()` 完成。
