

在这种情况下，更多的训练似乎能产生更高质量的生成图像，主要障碍出现在第 200-300 个 epoch 左右，之后模型的质量保持相当好。在此障碍之前和周围，图像质量较差；例如：

![](img/443014fed0f53a293f6ece3b211c1603_342_0.png)

图 16.3：来自 Wasserstein GAN 在第 97 个 epoch 生成的 100 个手写数字 7 图像示例。

此 epoch 之后，WGAN 开始生成逼真的手写数字。

![](img/443014fed0f53a293f6ece3b211c1603_343_0.png)

图 16.4：来自 Wasserstein GAN 在第 970 个 epoch 生成的 100 个手写数字 7 图像示例。

### 16.6 如何使用 WGAN 生成图像

我们可以使用保存的生成器模型按需创建新图像。这可以通过首先根据图像质量选择最终模型，然后加载它并从潜在空间提供新点作为输入，以便从该领域生成新的逼真图像来实现。在此示例中，我们将使用 10 个 epoch 后保存的模型，即 970 次训练迭代。

```
# example of loading the generator model and generating images
from keras.models import load_model
from numpy.random import randn
from matplotlib import pyplot

# generate points in latent space as input for the generator
def generate_latent_points(latent_dim, n_samples):
    # generate points in the latent space
    x_input = randn(latent_dim * n_samples)
    # reshape into a batch of inputs for the network
    x_input = x_input.reshape(n_samples, latent_dim)
    return x_input

# create a plot of generated images (reversed grayscale)
def plot_generated(examples, n):
    # plot images
    for i in range(n * n):
        # define subplot
        pyplot.subplot(n, n, 1 + i)
        # turn off axis
        pyplot.axis('off')
        # plot raw pixel data
        pyplot.imshow(examples[i, :, :, 0], cmap='gray_r')
    pyplot.show()

# load model
model = load_model('model_0970.h5')
# generate images
latent_points = generate_latent_points(50, 25)
# generate images
X = model.predict(latent_points)
# plot the result
plot_generated(X, 5)
```

清单 16.24：加载保存的 WGAN 生成器模型并使用它生成图像的示例。

运行该示例将生成一个 5 x 5（即 25 个）新的逼真手写数字 7 的图表。

![](img/443014fed0f53a293f6ece3b211c1603_344_0.png)

图 16.5：25 个 WGAN 生成的逼真手写数字 7 的图表。

### 16.7 进一步阅读

如果您希望深入了解，本节提供了更多关于该主题的资源。

#### 16.7.1 论文

- Wasserstein GAN，2017 年。
  https://arxiv.org/abs/1701.07875
- 改进的 Wasserstein GAN 训练，2017 年。
  https://arxiv.org/abs/1704.00028

#### 16.7.2 API

- Keras 数据集 API。
  https://keras.io/datasets/
- Keras 序列模型 API。
  https://keras.io/models/sequential/
- Keras 卷积层 API。
  https://keras.io/layers/convolutional/
- 如何“冻结” Keras 层？
  https://keras.io/getting-started/faq/#how-can-i-freeze-keras-layers
- Matplotlib API。
  https://matplotlib.org/api/
- NumPy 随机采样 (numpy.random) API。
  https://docs.scipy.org/doc/numpy/reference/routines.random.html
- NumPy 数组操作例程。
  https://docs.scipy.org/doc/numpy/reference/routines.array-manipulation.html

#### 16.7.3 文章

- Wasserstein GAN，GitHub。
  https://github.com/martinarjovsky/WassersteinGAN
- Wasserstein 生成对抗网络 (WGANS) 项目，GitHub。
  https://github.com/kpandey008/wasserstein-gans
- Keras-GAN：Keras 生成对抗网络实现，GitHub。
  https://github.com/eriklindernoren/Keras-GAN
- 改进的 WGAN，keras-contrib 项目，GitHub。
  https://github.com/keras-team/keras-contrib/blob/master/examples/improved_wgan.py

### 16.8 总结

在本教程中，您了解了如何从零开始实现 Wasserstein 生成对抗网络。具体来说，您学习了：

- 标准 DCGAN 与新 Wasserstein GAN 之间的区别。
- 如何从零开始实现 Wasserstein GAN 的具体细节。
- 如何开发用于图像生成的 WGAN 并解释模型行为。

#### 16.8.1 下一步

这是本部分的最后一个教程。在下一部分中，您将探索一系列不同的条件 GAN 模型。

## 第 V 部分

### 条件 GAN

### 概述

在本部分中，您将发现条件 GAN，它们为模型生成的图像类型增加了一些控制。阅读本部分的章节后，您将了解：

- 了解如何使用 cGAN 生成类条件图像（第 17 章）。
- 了解如何使用 InfoGAN 添加控制变量以影响图像生成（第 18 章）。
- 了解如何通过添加辅助分类器模型使用 AC-GAN 改进图像生成过程（第 19 章）。
- 了解如何在 SGAN 中与判别器一起训练半监督模型（第 20 章）。

## 第 17 章

### 如何开发条件 GAN (cGAN)

生成对抗网络（GAN）是一种用于训练生成模型的架构，例如用于生成图像的深度卷积神经网络。尽管 GAN 模型能够为给定数据集生成新的随机逼真示例，但除了试图弄清楚生成器输入的潜在空间与生成图像之间的复杂关系之外，无法控制生成的图像类型。条件生成对抗网络（cGAN）是一种 GAN，涉及由生成器模型进行的条件图像生成。图像生成可以基于类标签（如果可用）进行条件控制，从而允许有针对性地生成特定类型的图像。在本教程中，您将了解如何开发条件生成对抗网络，以有针对性地生成服装项目。完成本教程后，您将了解：

- 使用 GAN 生成随机样本的局限性，可通过条件生成对抗网络克服。
- 如何开发和评估用于生成服装项目照片的无条件生成对抗网络。
- 如何开发和评估用于生成服装项目照片的条件生成对抗网络。

让我们开始吧。

### 17.1 教程概述

本教程分为五个部分，分别是：

- 条件生成对抗网络
- Fashion-MNIST 服装照片数据集
- 用于 Fashion-MNIST 的无条件 GAN
- 用于 Fashion-MNIST 的条件 GAN
- 条件服装生成

### 17.2 条件生成对抗网络

生成对抗网络（GAN）是一种用于训练基于深度学习的生成模型的架构。该架构由生成器模型和判别器模型组成。生成器模型负责生成新的逼真示例，理想情况下这些示例与数据集中的真实示例无法区分。判别器模型负责将给定图像分类为真实（来自数据集）或假（生成）。这些模型以零和或对抗的方式一起训练，即判别器的改进是以牺牲生成器的能力为代价的，反之亦然。

GAN 在图像合成方面很有效，即为目标数据集生成新的图像示例。某些数据集包含额外信息，例如类标签，利用这些信息是可取的。例如，MNIST 手写数字数据集具有相应整数的类标签，CIFAR-10 小型物体照片数据集具有照片中相应物体的类标签，Fashion-MNIST 服装数据集具有相应服装项目的类标签。在 GAN 模型中利用类标签信息有两个动机。

- 改进 GAN。
- 有针对性的图像生成。

与输入图像相关的附加信息（例如类标签）可用于改进 GAN。这种改进可能表现为更稳定的训练、更快的训练和/或质量更好的生成图像。类标签也可用于有意或有针对性地生成特定类型的图像。GAN 模型的一个局限性是它可能会从该领域生成随机图像。潜在空间中的点与生成的图像之间存在关系，但这种关系复杂且难以映射。或者，可以以一种方式训练 GAN，使生成器和判别器模型都基于类标签进行条件控制。这意味着，当训练好的生成器模型作为独立模型用于在该领域生成图像时，可以生成特定类型或类标签的图像。

如果生成器和判别器都基于某些额外信息 y 进行条件控制，生成对抗网络可以扩展为条件模型。[...] 我们可以通过将 y 作为额外输入层馈送到判别器和生成器中来执行条件控制。

> ——《条件生成对抗网络》，2014 年。

例如，在 MNIST 的情况下，可以生成特定的手写数字，例如数字 9；在 CIFAR-10 的情况下，可以生成特定的物体照片，例如青蛙；在 Fashion-MNIST 数据集的情况下，可以生成特定的服装项目，例如连衣裙。这种模型称为条件生成对抗网络（CGAN 或 cGAN）。cGAN 最初由 Mehdi Mirza 和 Simon Osindero 在其 2014 年题为《条件生成对抗网络》的论文中描述。在该论文中，作者基于引导生成器模型图像生成过程的愿望来阐述该方法。

... 通过基于附加信息对模型进行条件控制，可以引导数据生成过程。这种条件控制可以基于类标签

