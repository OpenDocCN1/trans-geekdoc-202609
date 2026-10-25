

```python
model.add(LeakyReLU(alpha=0.2))
# output layer
model.add(Conv2D(3, (3,3), activation='tanh', padding='same'))
return model
```

代码清单 8.19：定义生成器模型的函数示例。

我们可以汇总模型，以便更好地理解输入和输出形状。完整示例如下。

```python
# example of defining the generator model
from keras.models import Sequential
from keras.layers import Dense
from keras.layers import Reshape
from keras.layers import Conv2D
from keras.layers import Conv2DTranspose
from keras.layers import LeakyReLU
from keras.utils.vis_utils import plot_model

# define the standalone generator model
def define_generator(latent_dim):
    model = Sequential()
    # foundation for 4x4 image
    n_nodes = 256 * 4 * 4
    model.add(Dense(n_nodes, input_dim=latent_dim))
    model.add(LeakyReLU(alpha=0.2))
    model.add(Reshape((4, 4, 256)))
    # upsample to 8x8
    model.add(Conv2DTranspose(128, (4,4), strides=(2,2), padding='same'))
    model.add(LeakyReLU(alpha=0.2))
    # upsample to 16x16
    model.add(Conv2DTranspose(128, (4,4), strides=(2,2), padding='same'))
    model.add(LeakyReLU(alpha=0.2))
    # upsample to 32x32
    model.add(Conv2DTranspose(128, (4,4), strides=(2,2), padding='same'))
    model.add(LeakyReLU(alpha=0.2))
    # output layer
    model.add(Conv2D(3, (3,3), activation='tanh', padding='same'))
    return model

# define the size of the latent space
latent_dim = 100
# define the generator model
model = define_generator(latent_dim)
# summarize the model
model.summary()
# plot the model
plot_model(model, to_file='generator_plot.png', show_shapes=True, show_layer_names=True)
```

代码清单 8.20：定义并汇总生成器模型的示例。

运行示例将汇总模型的各层及其输出形状。可以看到，正如设计的那样，第一个隐藏层有 4,096 个参数或 256 × 4 × 4，其激活值被重塑为 256 个 4 × 4 特征图。然后，这些特征图通过三个 Conv2DTranspose 层上采样到所需的输出形状 32 × 32，直到输出层，在那里创建了三个滤波器映射（通道）。

| 层 (类型) | 输出形状 | 参数 # |
| :--- | :--- | :--- |
| dense_1 (Dense) | (None, 4096) | 413696 |
| leaky_re_lu1 (LeakyReLU) | (None, 4096) | 0 |
| reshape_1 (Reshape) | (None, 4, 4, 256) | 0 |
| conv2d_transpose_1 (Conv2DTranspose) | (None, 8, 8, 128) | 524416 |
| leaky_re_lu2 (LeakyReLU) | (None, 8, 8, 128) | 0 |
| conv2d_transpose_2 (Conv2DTranspose) | (None, 16, 16, 128) | 262272 |
| leaky_re_lu3 (LeakyReLU) | (None, 16, 16, 128) | 0 |
| conv2d_transpose_3 (Conv2DTranspose) | (None, 32, 32, 128) | 262272 |
| leaky_re_lu4 (LeakyReLU) | (None, 32, 32, 128) | 0 |
| conv2d_1 (Conv2D) | (None, 32, 32, 3) | 3459 |
| 总参数数: 1,466,115 | | |
| 可训练参数数: 1,466,115 | | |
| 不可训练参数数: 0 | | |

代码清单 8.21：定义并汇总生成器模型的示例输出。

还会创建模型的图，可以看到模型期望从潜在空间输入一个 100 元素的点，并将预测一个两元素向量作为输出。

**注意：** 创建模型图假设已安装 `pydot` 和 `graphviz` 库。如果这有问题，可以注释掉导入语句和 `plot_model()` 的函数调用。

## 8.4. 如何定义和使用生成器模型

![](img/443014fed0f53a293f6ece3b211c1603_163_0.png)

图 8.3：CIFAR-10 生成对抗网络中生成器模型的图。

目前该模型功能有限。尽管如此，我们可以演示如何使用它来生成样本。这是一个有用的演示，用于理解生成器只是另一个模型，其中一些元素以后会有用。第一步是在潜在空间中生成新点。我们可以通过调用 **randn()** NumPy 函数来实现这一点，该函数用于生成从标准高斯分布中抽取的随机数数组。然后可以将随机数数组重塑为样本，即 _n_ 行，每行 100 个元素。下面的 **generate_latent_points()** 函数实现了此功能，并在潜在空间中生成所需数量的点，这些点可用作生成器模型的输入。

```python
# generate points in latent space as input for the generator
def generate_latent_points(latent_dim, n_samples):
    # generate points in the latent space
    x_input = randn(latent_dim * n_samples)
    # reshape into a batch of inputs for the network
    x_input = x_input.reshape(n_samples, latent_dim)
    return x_input
```

代码清单 8.22：在潜在空间中生成随机点的函数示例。

接下来，我们可以使用生成的点作为生成器模型的输入来生成新样本，然后绘制样本。我们可以更新上一节中的 **generate_fake_samples()** 函数，使其将生成器模型作为参数，并通过首先调用 **generate_latent_points()** 函数在潜在空间中生成所需数量的点作为模型输入，从而用它来生成所需数量的样本。下面列出了更新后的 **generate_fake_samples()** 函数，它既返回生成的样本，也返回相关的类标签。

```python
# use the generator to generate n fake examples, with class labels
def generate_fake_samples(g_model, latent_dim, n_samples):
    # generate points in latent space
    x_input = generate_latent_points(latent_dim, n_samples)
    # predict outputs
    X = g_model.predict(x_input)
    # create 'fake' class labels (0)
    y = zeros((n_samples, 1))
    return X, y
```

代码清单 8.23：使用生成器创建图像的函数示例。

然后，我们可以像第一部分处理真实 CIFAR-10 示例那样，通过调用 **imshow()** 函数来绘制生成的样本。下面列出了使用未训练的生成器模型生成新 CIFAR-10 图像的完整示例。

```python
# example of defining and using the generator model
from numpy import zeros
from numpy.random import randn
from keras.models import Sequential
from keras.layers import Dense
from keras.layers import Reshape
from keras.layers import Conv2D
from keras.layers import Conv2DTranspose
from keras.layers import LeakyReLU
from matplotlib import pyplot

# define the standalone generator model
def define_generator(latent_dim):
    model = Sequential()
    # foundation for 4x4 image
    n_nodes = 256 * 4 * 4
    model.add(Dense(n_nodes, input_dim=latent_dim))
    model.add(LeakyReLU(alpha=0.2))
    model.add(Reshape((4, 4, 256)))
    # upsample to 8x8
    model.add(Conv2DTranspose(128, (4,4), strides=(2,2), padding='same'))
    model.add(LeakyReLU(alpha=0.2))
    # upsample to 16x16
    model.add(Conv2DTranspose(128, (4,4), strides=(2,2), padding='same'))
    model.add(LeakyReLU(alpha=0.2))
    # upsample to 32x32
    model.add(Conv2DTranspose(128, (4,4), strides=(2,2), padding='same'))
    model.add(LeakyReLU(alpha=0.2))
    # output layer
    model.add(Conv2D(3, (3,3), activation='tanh', padding='same'))
    return model

# generate points in latent space as input for the generator
def generate_latent_points(latent_dim, n_samples):
    # generate points in the latent space
    x_input = randn(latent_dim * n_samples)
    # reshape into a batch of inputs for the network
    x_input = x_input.reshape(n_samples, latent_dim)
    return x_input

# use the generator to generate n fake examples, with class labels
def generate_fake_samples(g_model, latent_dim, n_samples):
    # generate points in latent space
    x_input = generate_latent_points(latent_dim, n_samples)
    # predict outputs
    X = g_model.predict(x_input)
    # create 'fake' class labels (0)
    y = zeros((n_samples, 1))
    return X, y

# size of the latent space
latent_dim = 100
# define the discriminator model
model = define_generator(latent_dim)
# generate samples
n_samples = 49
X, _ = generate_fake_samples(model, latent_dim, n_samples)
# scale pixel values from [-1,1] to [0,1]
X = (X + 1) / 2.0
# plot the generated samples
for i in range(n_samples):
    # define subplot
    pyplot.subplot(7, 7, 1 + i)
    # turn off axis labels
    pyplot.axis('off')
    # plot single image
    pyplot.imshow(X[i])
    # show the figure
    pyplot.show()
```

