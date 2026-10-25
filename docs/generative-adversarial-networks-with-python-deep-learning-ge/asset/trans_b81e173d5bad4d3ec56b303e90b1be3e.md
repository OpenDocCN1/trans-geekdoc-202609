

```python
# example of defining the discriminator model
from keras.models import Sequential
from keras.optimizers import Adam
from keras.layers import Dense
from keras.layers import Conv2D
from keras.layers import Flatten
from keras.layers import Dropout
from keras.layers import LeakyReLU
from keras.utils.vis_utils import plot_model

# define the standalone discriminator model
def define_discriminator(in_shape=(32,32,3)):
    model = Sequential()
    # normal
    model.add(Conv2D(64, (3,3), padding='same', input_shape=in_shape))
    model.add(LeakyReLU(alpha=0.2))
    # downsample
    model.add(Conv2D(128, (3,3), strides=(2,2), padding='same'))
    model.add(LeakyReLU(alpha=0.2))
    # downsample
    model.add(Conv2D(128, (3,3), strides=(2,2), padding='same'))
    model.add(LeakyReLU(alpha=0.2))
    # downsample
    model.add(Conv2D(256, (3,3), strides=(2,2), padding='same'))
    model.add(LeakyReLU(alpha=0.2))
    # classifier
    model.add(Flatten())
    model.add(Dropout(0.4))
    model.add(Dense(1, activation='sigmoid'))
    # compile model
    opt = Adam(lr=0.0002, beta_1=0.5)
    model.compile(loss='binary_crossentropy', optimizer=opt, metrics=['accuracy'])
    return model

# define model
model = define_discriminator()
# summarize the model
model.summary()
# plot the model
plot_model(model, to_file='discriminator_plot.png', show_shapes=True, show_layer_names=True)
```

清单 8.6：定义和汇总判别器模型的示例。

运行该示例首先会汇总模型架构，显示每个层的输出形状。我们可以看到，激进的 2 × 2 步长起到了下采样输入图像的作用，首先从 32 × 32 变为 16 × 16，然后变为 8 × 8，以此类推，直到模型做出输出预测。这种模式是经过设计的，因为我们不使用池化层，而是使用大步长来实现类似的下采样效果。在下一节中，我们将在生成器模型中看到类似的模式，但方向相反。

| 层 (类型) | 输出形状 | 参数数量 |
| :--- | :--- | :--- |
| conv2d_1 (Conv2D) | (None, 32, 32, 64) | 1792 |
| leaky_re_lu_1 (LeakyReLU) | (None, 32, 32, 64) | 0 |
| conv2d_2 (Conv2D) | (None, 16, 16, 128) | 73856 |
| leaky_re_lu_2 (LeakyReLU) | (None, 16, 16, 128) | 0 |
| conv2d_3 (Conv2D) | (None, 8, 8, 128) | 147584 |
| leaky_re_lu_3 (LeakyReLU) | (None, 8, 8, 128) | 0 |
| conv2d_4 (Conv2D) | (None, 4, 4, 256) | 295168 |
| leaky_re_lu_4 (LeakyReLU) | (None, 4, 4, 256) | 0 |
| flatten_1 (Flatten) | (None, 4096) | 0 |
| dropout_1 (Dropout) | (None, 4096) | 0 |
| dense_1 (Dense) | (None, 1) | 4097 |

=================================================================
总参数量: 522,497
可训练参数量: 522,497
不可训练参数量: 0
=================================================================

## 8.3. 如何定义和训练判别器模型

清单 8.7：定义和汇总判别器模型的示例输出。

还会创建模型的图，我们可以看到该模型期望两个输入，并将预测一个单一输出。

**注意**：创建模型图假设已安装 `pydot` 和 `graphviz` 库。如果这造成问题，你可以注释掉导入语句和 `plot_model()` 的函数调用。

![](img/443014fed0f53a293f6ece3b211c1603_154_0.png)

图 8.2：CIFAR-10 生成对抗网络中判别器模型的图。

我们现在可以使用类别标签为 1 的真实示例开始训练此模型，并随机生成类别标签为 0 的样本。开发这些元素以后会很有用，而且有助于看到判别器只是一个用于二分类的普通神经网络模型。首先，我们需要一个函数来加载和准备真实图像的数据集。我们将使用 `cifar.load_data()` 函数来加载 CIFAR-10 数据集，并仅使用训练数据集的输入部分作为真实图像。

```python
# load cifar10 dataset
(trainX, _), (_, _) = load_data()
```

清单 8.8：加载 CIFAR-10 训练数据集的示例。

我们必须将像素值从无符号整数范围 [0,255] 缩放到归一化范围 [-1,1]。生成器模型将生成像素值在范围 [-1,1] 的图像，因为它将使用 Tanh 激活函数，这是一种最佳实践。将真实图像也缩放到相同范围也是一种良好实践。

```python
# convert from unsigned ints to floats
X = trainX.astype('float32')
# scale from [0,255] to [-1,1]
X = (X - 127.5) / 127.5
```

清单 8.9：缩放已加载数据集的像素值的示例。

下面的 `load_real_samples()` 函数实现了真实 CIFAR-10 照片的加载和缩放。

```python
# load and prepare cifar10 training images
def load_real_samples():
    # load cifar10 dataset
    (trainX, _), (_, _) = load_data()
    # convert from unsigned ints to floats
    X = trainX.astype('float32')
    # scale from [0,255] to [-1,1]
    X = (X - 127.5) / 127.5
    return X
```

清单 8.10：加载和缩放 CIFAR-10 训练数据集像素值的函数示例。

判别器模型将以批次方式更新，具体是使用一组真实样本和一组生成样本。在训练中，一个时代被定义为遍历整个训练数据集一次。我们可以系统地枚举训练数据集中的所有样本，这是一种好方法，但通过随机梯度下降进行良好训练要求在每个时代之前对训练数据集进行随机打乱。一种更简单的方法是从训练数据集中选择随机图像样本。下面的 `generate_real_samples()` 函数将训练数据集作为参数，并将选择图像的随机子样本；它还将为样本返回类别标签，具体是类别标签 1，以指示真实图像。

```python
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

清单 8.11：在已加载数据集中采样图像的函数示例。

现在，我们需要一个假图像的来源。我们还没有生成器模型，因此，我们可以生成由随机像素值组成的图像，具体是范围 [0,1] 中的随机像素值，然后将其缩放到范围 [-1, 1]，就像我们缩放的真实图像一样。下面的 generate_fake_samples() 函数实现了此行为，并生成随机像素值的图像及其关联的类别标签 0，用于假图像。

```python
# generate n fake samples with class labels
def generate_fake_samples(n_samples):
    # generate uniform random numbers in [0,1]
    X = rand(32 * 32 * 3 * n_samples)
    # update to have the range [-1, 1]
    X = -1 + X * 2
    # reshape into a batch of color images
    X = X.reshape((n_samples, 32, 32, 3))
    # generate 'fake' class labels (0)
    y = zeros((n_samples, 1))
    return X, y
```

清单 8.12：生成具有随机像素值图像的函数示例。

最后，我们需要训练判别器模型。这涉及反复检索真实图像样本和生成图像样本，并在固定数量的迭代中更新模型。我们暂时忽略时代的概念（例如，完整遍历训练数据集），而是将判别器模型拟合为固定数量的批次。模型将快速学会区分真实图像和假图像（随机生成），因此在它学会完美区分之前，不需要许多批次。

train_discriminator() 函数实现了这一点，每批次使用 128 张图像的批量大小，每次迭代中 64 张是真实图像，64 张是假图像。我们分别对真实示例和假示例更新判别器，以便在更新之前可以计算模型在每个样本上的准确性。这能让我们了解判别器模型随时间的表现情况。

```python
# train the discriminator model
def train_discriminator(model, dataset, n_iter=20, n_batch=128):
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

