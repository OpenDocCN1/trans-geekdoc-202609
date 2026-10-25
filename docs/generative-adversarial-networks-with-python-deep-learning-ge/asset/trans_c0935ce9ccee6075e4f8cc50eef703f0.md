

```python
# define output layer of the critic model
...
model.add(Dense(1, activation='linear'))
```

清单 16.1：判别器输出层中线性激活函数的示例。

线性激活是层的默认激活函数，因此我们实际上可以不指定激活函数来达到相同的结果。

```python
# define output layer of the critic model
...
model.add(Dense(1))
```

清单 16.2：判别器输出层中线性激活函数的示例。

### 16.4.2 真实和假图像的类标签

DCGAN 对假图像使用类 0，对真实图像使用类 1，这些类标签用于训练 GAN。在 DCGAN 中，这些是判别器预期要达到的精确标签。WGAN 对评论家没有精确标签。相反，它鼓励评论家为真实图像和假图像输出不同的分数。这是通过巧妙利用正负类标签的 Wasserstein 函数实现的。WGAN 可以实现为：真实图像使用 -1 类标签，假图像或生成图像使用 1 类标签。这可以使用 ones() NumPy 函数实现。例如：

```python
...
# generate class labels, -1 for 'real'
y = -ones((n_samples, 1))
...
# create class labels with 1.0 for 'fake'
y = ones((n_samples, 1))
```

清单 16.3：定义真实和假图像目标值的示例。

### 16.4.3 Wasserstein 损失函数

我们可以将 Wasserstein 损失实现为 Keras 中的自定义函数，用于计算真实或假图像的平均分数。真实样本的分数被最大化，假样本的分数被最小化。鉴于随机梯度下降是一种最小化算法，我们可以将类标签乘以平均分数（例如，真实为 -1，假为 1，这没有影响），以确保真实和假图像的损失对网络来说是最小化的。下面列出了该损失函数在 Keras 中的高效实现。

```python
from keras import backend

# implementation of wasserstein loss
def wasserstein_loss(y_true, y_pred):
    return backend.mean(y_true * y_pred)
```

清单 16.4：计算 Wasserstein 损失的函数示例。

编译模型时指定函数名，即可使用该损失函数训练 Keras 模型。例如：

```python
...
# compile the model
model.compile(loss=wasserstein_loss, ...)
```

清单 16.5：编译模型以使用 Wasserstein 损失的示例。

### 16.4.4 评论家权重裁剪

DCGAN 不使用任何梯度裁剪，尽管 WGAN 要求对评论家模型进行梯度裁剪。我们可以将权重裁剪实现为 Keras 约束。这是一个必须扩展 Constraint 类的类，并定义 `__call__()` 函数的实现以应用操作，以及 `get_config()` 函数以返回任何配置。我们还可以定义 `__init__()` 函数来设置配置，在此例中，即权重超立方体边界框的对称大小，例如 0.01。下面定义了 `ClipConstraint` 类。

```python
# clip model weights to a given hypercube
class ClipConstraint(Constraint):
    # set clip value when initialized
    def __init__(self, clip_value):
        self.clip_value = clip_value

    # clip model weights to hypercube
    def __call__(self, weights):
        return backend.clip(weights, -self.clip_value, self.clip_value)

    # get the config
    def get_config(self):
        return {'clip_value': self.clip_value}
```

清单 16.6：自定义权重约束类的示例。

要使用该约束，可以构造该类，然后通过设置 `kernel_constraint` 参数在层中使用；例如：

```python
...
# define the constraint
const = ClipConstraint(0.01)
...
# use the constraint in a layer
model.add(Conv2D(..., kernel_constraint=const))
```

清单 16.7：在层中使用自定义权重约束的示例。

仅在更新评论家模型时才需要该约束。

### 16.4.5 更新评论家的次数多于生成器

在 DCGAN 中，生成器和判别器模型必须以相同的量进行更新。具体来说，判别器在每次迭代中使用半批真实样本和半批假样本进行更新，而生成器使用单批生成样本进行更新（如第 4 章所述）。例如：

```python
...
# main gan training loop
for i in range(n_steps):
    # update the discriminator
    # get randomly selected 'real' samples
    X_real, y_real = generate_real_samples(dataset, half_batch)
    # update critic model weights
    c_loss1 = c_model.train_on_batch(X_real, y_real)
    # generate 'fake' examples
    X_fake, y_fake = generate_fake_samples(g_model, latent_dim, half_batch)
    # update critic model weights
    c_loss2 = c_model.train_on_batch(X_fake, y_fake)
    # update generator
    # prepare points in latent space as input for the generator
    X_gan = generate_latent_points(latent_dim, n_batch)
    # create inverted labels for the fake samples
    y_gan = ones((n_batch, 1))
    # update the generator via the critic's error
    g_loss = gan_model.train_on_batch(X_gan, y_gan)
```

清单 16.8：DCGAN 训练算法的示例。

在 WGAN 模型中，评论家模型的更新次数必须多于生成器模型。具体来说，定义了一个新的超参数来控制每次更新生成器模型时评论家更新的次数，称为 n_critic，并设置为 5。这可以作为主 GAN 更新循环内的一个新循环来实现；例如：

```python
...
# main gan training loop
for i in range(n_steps):
    # update the critic
    for _ in range(n_critic):
        # get randomly selected 'real' samples
        X_real, y_real = generate_real_samples(dataset, half_batch)
        # update critic model weights
        c_loss1 = c_model.train_on_batch(X_real, y_real)
        # generate 'fake' examples
        X_fake, y_fake = generate_fake_samples(g_model, latent_dim, half_batch)
        # update critic model weights
        c_loss2 = c_model.train_on_batch(X_fake, y_fake)
    # update generator
    # prepare points in latent space as input for the generator
    X_gan = generate_latent_points(latent_dim, n_batch)
    # create inverted labels for the fake samples
    y_gan = ones((n_batch, 1))
    # update the generator via the critic's error
    g_loss = gan_model.train_on_batch(X_gan, y_gan)
```

清单 16.9：WGAN 训练算法的示例。

### 16.4.6 使用 RMSProp 随机梯度下降

DCGAN 使用带有小学习率和适度动量的 Adam 版本随机梯度下降。WGAN 建议改用 RMSProp，学习率为 0.00005。这可以在编译模型时在 Keras 中实现。例如：

```python
...
# compile model
opt = RMSprop(lr=0.00005)
model.compile(loss=wasserstein_loss, optimizer=opt)
```

清单 16.10：编译模型以使用 RMSProp 随机梯度下降的示例。

## 16.5 如何训练 Wasserstein GAN 模型

既然我们知道了 WGAN 的具体实现细节，就可以实现图像生成模型了。在本节中，我们将开发一个 WGAN，从 MNIST 数据集（如第 7.2 节所述）中生成一个手写数字（数字 7）。这是 WGAN 的一个良好测试问题，因为它是一个小数据集，需要一个适度的模型且训练速度快。第一步是定义模型。

评论家模型将一张 28 × 28 灰度图像作为输入，并输出图像真实或假的分数。它被实现为一个适度的卷积神经网络，采用 DCGAN 设计的最佳实践，例如使用斜率为 0.2 的 LeakyReLU 激活函数、批量归一化以及使用 2 × 2 步幅进行下采样。评论家模型使用新的 ClipConstraint 权重约束在小批量更新后裁剪模型权重，并使用自定义 wasserstein_loss() 函数以及学习率为 0.00005 的 RMSProp 版本随机梯度下降进行优化。下面的 define_critic() 函数实现了这一点，定义并编译评论家模型并返回它。图像的输入形状被参数化为默认函数参数，以便清楚地说明。

```python
# define the standalone critic model
def define_critic(in_shape=(28,28,1)):
    # weight initialization
    init = RandomNormal(stddev=0.02)
    # weight constraint
    const = ClipConstraint(0.01)
    # define model
    model = Sequential()
    # downsample to 14x14
    model.add(Conv2D(64, (4,4), strides=(2,2), padding='same', kernel_initializer=init,
                     kernel_constraint=const, input_shape=in_shape))
    model.add(BatchNormalization())
    model.add(LeakyReLU(alpha=0.2))
    # downsample to 7x7
    model.add(Conv2D(64, (4,4), strides=(2,2), padding='same', kernel_initializer=init,
                     kernel_constraint=const))
    model.add(BatchNormalization())
    model.add(LeakyReLU(alpha=0.2))
    # scoring, linear activation
    model.add(Flatten())
    model.add(Dense(1))
```

