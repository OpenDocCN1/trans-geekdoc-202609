

## 清单 7.13：选择真实图像样本的函数示例。

现在，我们需要一个假图像的来源。我们还没有生成器模型，因此，我们可以生成由随机像素值组成的图像，具体来说，就是范围 [0,1] 内的随机像素值，就像我们缩放后的真实图像一样。下面的 `generate_fake_samples()` 函数实现了此行为，并生成随机像素值的图像及其相关的类标签 0，用于假图像。

```
# generate n fake samples with class labels
def generate_fake_samples(n_samples):
    # generate uniform random numbers in [0,1]
    X = rand(28 * 28 * n_samples)
    # reshape into a batch of grayscale images
    X = X.reshape((n_samples, 28, 28, 1))
    # generate 'fake' class labels (0)
    y = zeros((n_samples, 1))
    return X, y
```

## 清单 7.14：生成随机假图像的函数示例。

最后，我们需要训练判别器模型。这涉及反复获取真实图像样本和生成图像样本，并固定迭代次数地更新模型。目前我们将忽略 epoch（即完整遍历训练数据集）的概念，而是按固定批次数拟合判别器模型。该模型将快速学会区分真实图像和假图像（随机生成的图像），因此，在它学会完美区分之前，不需要太多批次。

`train_discriminator()` 函数实现了此功能，每次迭代使用 256 图像的批量大小，其中 128 个是真实图像，128 个是假图像。我们分别对真实和假示例更新判别器，以便在更新前计算模型在每个样本上的准确率。这能让我们了解判别器模型随时间的表现情况。

```
# train the discriminator model
def train_discriminator(model, dataset, n_iter=100, n_batch=256):
    half_batch = int(n_batch / 2)
    # manually enumerate epochs
    for i in range(n_iter):
        # get randomly selected 'real' samples
        X_real, y_real = generate_real_samples(dataset, half_batch)
        # update discriminator on real samples
        _, real_acc = model.train_on_batch(X_real, y_real)
        # generate 'fake' examples
        X_fake, y_fake = generate_fake_samples(half_batch)
        # update discriminator on fake samples
        _, fake_acc = model.train_on_batch(X_fake, y_fake)
        # summarize performance
        print('>%d real=%.0f%% fake=%.0f%%' % (i+1, real_acc*100, fake_acc*100))
```

## 清单 7.15：训练判别器模型的函数示例。

将所有这些结合起来，下面列出了在真实和生成（假）图像上训练判别器模型实例的完整示例。

```
# example of training the discriminator model on real and random mnist images
from numpy import expand_dims
from numpy import ones
from numpy import zeros
from numpy.random import rand
from numpy.random import randint
from keras.datasets.mnist import load_data
from keras.optimizers import Adam
from keras.models import Sequential
from keras.layers import Dense
from keras.layers import Conv2D
from keras.layers import Flatten
from keras.layers import Dropout
from keras.layers import LeakyReLU
```

```
# define the standalone discriminator model
def define_discriminator(in_shape=(28,28,1)):
    model = Sequential()
    model.add(Conv2D(64, (3,3), strides=(2, 2), padding='same', input_shape=in_shape))
    model.add(LeakyReLU(alpha=0.2))
    model.add(Dropout(0.4))
    model.add(Conv2D(64, (3,3), strides=(2, 2), padding='same'))
    model.add(LeakyReLU(alpha=0.2))
    model.add(Dropout(0.4))
    model.add(Flatten())
    model.add(Dense(1, activation='sigmoid'))
    # compile model
    opt = Adam(lr=0.0002, beta_1=0.5)
    model.compile(loss='binary_crossentropy', optimizer=opt, metrics=['accuracy'])
    return model
```

```
# load and prepare mnist training images
def load_real_samples():
    # load mnist dataset
    (trainX, _), (_, _) = load_data()
    # expand to 3d, e.g. add channels dimension
    X = expand_dims(trainX, axis=-1)
    # convert from unsigned ints to floats
    X = X.astype('float32')
    # scale from [0,255] to [0,1]
    X = X / 255.0
    return X
```

```
# select real samples
def generate_real_samples(dataset, n_samples):
    # choose random instances
    ix = randint(0, dataset.shape[0], n_samples)
    # retrieve selected images
    X = dataset[ix]
    # generate 'real' class labels (1)
    y = ones((n_samples, 1))
    return X, y
```

```
# generate n fake samples with class labels
def generate_fake_samples(n_samples):
    # generate uniform random numbers in [0,1]
    X = rand(28 * 28 * n_samples)
    # reshape into a batch of grayscale images
    X = X.reshape((n_samples, 28, 28, 1))
    # generate 'fake' class labels (0)
    y = zeros((n_samples, 1))
    return X, y
```

```
# train the discriminator model
def train_discriminator(model, dataset, n_iter=100, n_batch=256):
    half_batch = int(n_batch / 2)
    # manually enumerate epochs
    for i in range(n_iter):
        # get randomly selected 'real' samples
        X_real, y_real = generate_real_samples(dataset, half_batch)
        # update discriminator on real samples
        _, real_acc = model.train_on_batch(X_real, y_real)
        # generate 'fake' examples
        X_fake, y_fake = generate_fake_samples(half_batch)
        # update discriminator on fake samples
        _, fake_acc = model.train_on_batch(X_fake, y_fake)
        # summarize performance
        print('>%d real=%.0f%% fake=%.0f%%' % (i+1, real_acc*100, fake_acc*100))

# define the discriminator model
model = define_discriminator()
# load image data
dataset = load_real_samples()
# fit the model
train_discriminator(model, dataset)
```

## 清单 7.16：定义和训练判别器模型的示例。

运行示例首先定义模型，加载 MNIST 数据集，然后训练判别器模型。

**注意**：由于学习算法的随机性，您的具体结果可能会有所不同。建议运行示例几次并比较平均性能。

在此示例中，判别器模型能够非常快速地学会区分真实和生成的 MNIST 图像，大约需要 50 个批次。

```
...
>96 real=100% fake=100%
>97 real=100% fake=100%
>98 real=100% fake=100%
>99 real=100% fake=100%
>100 real=100% fake=100%
```

## 清单 7.17：定义和训练判别器模型的示例输出。

既然我们知道如何定义和训练判别器模型，接下来需要研究开发生成器模型。

## 7.4 如何定义和使用生成器模型

灰度图像。潜在空间是一个任意定义的、服从高斯分布的向量空间，例如 100 维。它本身没有意义，但通过从该空间中随机抽取点并在训练期间将其提供给生成器模型，生成器模型会为这些潜在点赋予意义。训练结束时，潜在向量空间代表输出空间（即 MNIST 图像）的压缩表示，只有生成器知道如何将其转换为逼真的 MNIST 图像。

- **输入**：潜在空间中的点，例如一个包含 100 个元素的高斯随机数向量。
- **输出**：像素值在 [0,1] 范围内的 28 × 28 像素的二维正方形灰度图像。

输入向量不必非要是 100 个元素；这是一个整数且广泛使用，但我预期 10、50 或 500 也同样有效。开发生成器模型要求我们将来自潜在空间的 100 维向量转换为包含 28 × 28 或 784 个值的二维数组。实现此目标有多种方法，但有一种方法在深度卷积生成对抗网络中已被证明是有效的。它涉及两个主要元素。第一个是作为第一个隐藏层的 Dense 层，该层拥有足够的节点来表示输出图像的低分辨率版本。具体来说，输出图像一半大小（四分之一面积）的图像将是 14 × 14 或 196 个节点，而输出图像四分之一大小（八分之一面积）的图像将是 7 × 7 或 49 个节点。

我们不仅想要图像的一个低分辨率版本，而是想要输入的许多并行版本或解释。这是卷积神经网络中的一种模式，其中有许多并行滤波器，产生多个并行激活图（称为特征图），对输入有不同的解释。我们希望在输出端实现同样的事情：拥有输出的许多并行版本，具有不同的学习特征，这些特征可以在输出层中合并为最终图像。模型需要空间来发明、创建或生成。因此，第一个隐藏层（即 Dense 层）需要足够的节点来表示输出图像的多个低分辨率版本，例如 128 个。

```
...
# foundation for 7x7 image
model.add(Dense(128 * 7 * 7, input_dim=100))
```

## 清单 7.18：定义生成器模型基础激活的示例。

这些节点的激活值随后可以重塑为类似图像的形式，以传入卷积层，例如 128 个不同的 7 × 7 特征图。

```
...
model.add(Reshape((7, 7, 128)))
```

## 清单 7.19：将激活值重塑为适合 Conv2D 层的形状的示例。

下一个主要架构创新涉及将低分辨率图像上采样为更高分辨率的图像版本。执行此上采样过程有两种常见方法，有时称为反卷积。一种方法是使用 UpSampling2D 层（类似于反池化层），随后跟一个普通的 Conv2D 层。另一种可能更现代的方法是将这两个操作合并为一个单一层，称为 Conv2DTranspose。我们将为生成器采用后一种方法。

