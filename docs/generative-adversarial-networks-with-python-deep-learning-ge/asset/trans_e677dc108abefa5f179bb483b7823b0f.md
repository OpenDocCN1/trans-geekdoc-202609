

此时此刻。不过，我们可以演示如何使用它来生成样本。这不是必须的，但同样，其中一些元素以后可能有用。第一步是在潜在空间中生成新的随机点。我们可以通过调用 `randn()` NumPy 函数来实现这一点，用于生成从标准高斯分布中抽取的随机数数组。

然后可以将随机数数组重塑为样本：即 n 行，每行五个元素。下面的 `generate_latent_points()` 函数实现了这一点，并在潜在空间中生成所需数量的点，这些点可以用作生成器模型的输入。

```python
# generate points in latent space as input for the generator
def generate_latent_points(latent_dim, n):
    # generate points in the latent space
    x_input = randn(latent_dim * n)
    # reshape into a batch of inputs for the network
    x_input = x_input.reshape(n, latent_dim)
    return x_input
```

清单 6.15: 采样潜在空间的函数示例。

接下来，我们可以使用生成的点作为生成器模型的输入来生成新样本，然后绘制样本。下面的 `generate_fake_samples()` 函数实现了这一点，其中定义的生成器和潜在空间的大小作为参数传递，以及模型要生成的点数。

```python
# use the generator to generate n fake examples and plot the results
def generate_fake_samples(generator, latent_dim, n):
    # generate points in latent space
    x_input = generate_latent_points(latent_dim, n)
    # predict outputs
    X = generator.predict(x_input)
    # plot the results
    pyplot.scatter(X[:, 0], X[:, 1])
    pyplot.show()
```

清单 6.16: 生成假样本的函数示例。

将这些整合在一起，完整示例如下所示。

```python
# define and use the generator model
from numpy.random import randn
from keras.models import Sequential
from keras.layers import Dense
from matplotlib import pyplot

# define the standalone generator model
def define_generator(latent_dim, n_outputs=2):
    model = Sequential()
    model.add(Dense(15, activation='relu', kernel_initializer='he_uniform',
                    input_dim=latent_dim))
    model.add(Dense(n_outputs, activation='linear'))
    return model

# generate points in latent space as input for the generator
def generate_latent_points(latent_dim, n):
    # generate points in the latent space
    x_input = randn(latent_dim * n)
    # reshape into a batch of inputs for the network
    x_input = x_input.reshape(n, latent_dim)
    return x_input

# use the generator to generate n fake examples and plot the results
def generate_fake_samples(generator, latent_dim, n):
    # generate points in latent space
    x_input = generate_latent_points(latent_dim, n)
    # predict outputs
    X = generator.predict(x_input)
    # plot the results
    pyplot.scatter(X[:, 0], X[:, 1])
    pyplot.show()

# size of the latent space
latent_dim = 5
# define the discriminator model
model = define_generator(latent_dim)
# generate and plot generated samples
generate_fake_samples(model, latent_dim, 100)
```

清单 6.17: 定义和使用生成器模型的示例。

运行示例将从潜在空间生成 100 个随机点，将其作为输入传递给生成器，并从我们的一维函数域中生成 100 个假样本。由于生成器尚未训练，生成的点完全是垃圾，正如我们所料，但我们可以想象，随着模型的训练，这些点将慢慢开始类似于目标函数及其 U 形。

## 6.4. 定义生成器模型

![](img/443014fed0f53a293f6ece3b211c1603_98_0.png)

图 6.5: 生成器模型预测的假样本散点图。

我们现在已经了解了如何定义和使用生成器模型。我们需要以这种方式使用生成器模型来创建供判别器分类的样本。我们尚未了解生成器模型是如何训练的；这将是接下来的内容。

## 6.5. 训练生成器模型

生成器模型中的权重根据判别器模型的性能进行更新。当判别器擅长检测假样本时，生成器会更新得更多（通过更大的误差梯度），而当判别器模型在检测假样本时表现相对较差或感到困惑时，生成器模型更新得较少。这定义了这两个模型之间的零和或对抗关系。使用 Keras API 实现这一点可能有多种方法，但也许最简单的方法是创建一个新模型，该模型包含或封装生成器和判别器模型。具体来说，可以定义一个新的 GAN 模型，它堆叠生成器和判别器，使生成器接收潜在空间中的随机点作为输入，生成直接输入到判别器模型的样本，进行分类，而这个更大模型的输出可用于更新生成器的模型权重。要澄清，我们说的不是一个新的第三个模型，只是一个逻辑上的第三个模型，它使用独立生成器和判别器模型中已定义的层和权重。

只有判别器关注区分真实样本和假样本；因此，判别器模型可以以独立方式在每类样本上进行训练。生成器模型只关心判别器在假样本上的表现。因此，当判别器作为 GAN 模型的一部分时，我们将其所有层标记为不可训练，以便它们不能被更新并在假样本上过度训练。

通过这个包含性 GAN 模型训练生成器时，还有一个重要的变化。生成器希望判别器认为生成器输出的样本是真实的，而不是假的。因此，当生成器作为 GAN 模型的一部分进行训练时，我们将生成的样本标记为真实（class = 1）。我们可以想象，判别器随后会将生成的样本分类为非真实（class = 0）或真实概率较低（0.3 或 0.5）。用于更新模型权重的反向传播过程会将其视为一个大错误，并将更新模型权重（即仅生成器中的权重）以纠正此错误，从而使生成器更擅长生成逼真的假样本。让我们具体化这一点。

- 输入：潜在空间中的点，例如五元素高斯随机数向量。
- 输出：二进制分类，样本为真实（或假）的可能性。

下面的 `define_gan()` 函数将已定义的生成器和判别器模型作为参数，并创建包含这两个模型的新逻辑第三个模型。判别器中的权重被标记为不可训练，这仅影响 GAN 模型所见的权重，而不影响独立判别器模型。然后 GAN 模型使用与判别器相同的二元交叉熵损失函数和高效的 Adam 版本的随机梯度下降。

```python
# define the combined generator and discriminator model, for updating the generator
def define_gan(generator, discriminator):
    # make weights in the discriminator not trainable
    discriminator.trainable = False
    # connect them
    model = Sequential()
    # add generator
    model.add(generator)
    # add the discriminator
    model.add(discriminator)
    # compile model
    model.compile(loss='binary_crossentropy', optimizer='adam')
    return model
```

清单 6.18: 定义用于训练生成器的复合模型的函数示例。

使判别器不可训练是 Keras API 中的一个巧妙技巧。trainable 属性在模型编译时影响模型。判别器模型是使用可训练层编译的，因此当独立模型通过调用 `train_on_batch()` 进行更新时，这些层中的模型权重将被更新。判别器模型被标记为不可训练，添加到 GAN 模型中，并进行编译。在这个模型中，判别器模型的模型权重不可训练，并且在 GAN 模型通过调用 `train_on_batch()` 进行更新时不能更改。创建判别器、生成器和复合模型的完整示例如下所示。

