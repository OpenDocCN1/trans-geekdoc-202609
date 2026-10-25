
Conv2DTranspose 层可以配置为 (2 x 2) 的步幅，这将使输入特征图的面积扩大四倍（将其宽度和高度维度加倍）。最佳实践是使用步幅的因子（例如两倍）作为内核大小，以避免在上采样时可能观察到的棋盘格模式（有关上采样层的更多信息，请参见第 3 章）。

```
# upsample to 14x14
model.add(Conv2DTranspose(128, (4,4), strides=(2,2), padding='same'))
```

清单 7.20：定义上采样层的示例。

可以重复此过程以得到我们的 28 x 28 输出图像。同样，我们将使用默认斜率为 0.2 的 LeakyReLU 激活函数，这在训练 GAN 模型时被推荐为最佳实践。模型的输出层是一个具有一个滤波器、内核大小为 7 x 7 且填充为 'same' 的 Conv2D 层，旨在创建单个特征图并将其尺寸保持在 28 x 28 像素。使用 sigmoid 激活函数以确保输出值在所需范围 [0,1] 内。下面的 define_generator() 函数实现了此功能并定义了生成器模型。生成器模型未编译，也不指定损失函数或优化算法。这是因为生成器不是直接训练的。我们将在下一节中了解更多相关内容。

```
# define the standalone generator model
def define_generator(latent_dim):
    model = Sequential()
    # foundation for 7x7 image
    n_nodes = 128 * 7 * 7
    model.add(Dense(n_nodes, input_dim=latent_dim))
    model.add(LeakyReLU(alpha=0.2))
    model.add(Reshape((7, 7, 128)))
    # upsample to 14x14
    model.add(Conv2DTranspose(128, (4,4), strides=(2,2), padding='same'))
    model.add(LeakyReLU(alpha=0.2))
    # upsample to 28x28
    model.add(Conv2DTranspose(128, (4,4), strides=(2,2), padding='same'))
    model.add(LeakyReLU(alpha=0.2))
    model.add(Conv2D(1, (7,7), activation='sigmoid', padding='same'))
    return model
```

清单 7.21：定义生成器模型的函数示例。

我们可以汇总模型以帮助更好地理解输入和输出形状。完整示例如下所示。

```
# example of defining the generator model
from numpy import zeros
from numpy.random import randn
from keras.models import Sequential
from keras.layers import Dense
from keras.layers import Reshape
from keras.layers import Conv2D
from keras.layers import Conv2DTranspose
from keras.layers import LeakyReLU
from keras.utils.vis_utils import plot_model
from matplotlib import pyplot

# define the standalone generator model
def define_generator(latent_dim):
    model = Sequential()
    # foundation for 7x7 image
    n_nodes = 128 * 7 * 7
    model.add(Dense(n_nodes, input_dim=latent_dim))
    model.add(LeakyReLU(alpha=0.2))
    model.add(Reshape((7, 7, 128)))
    # upsample to 14x14
    model.add(Conv2DTranspose(128, (4,4), strides=(2,2), padding='same'))
    model.add(LeakyReLU(alpha=0.2))
    # upsample to 28x28
    model.add(Conv2DTranspose(128, (4,4), strides=(2,2), padding='same'))
    model.add(LeakyReLU(alpha=0.2))
    model.add(Conv2D(1, (7,7), activation='sigmoid', padding='same'))
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

清单 7.22：定义和汇总生成器模型的示例。

运行示例将汇总模型的层及其输出形状。我们可以看到，如设计所示，第一个隐藏层有 6,272 个参数，即 128 x 7 x 7，其激活值被重塑为 128 个 7 x 7 特征图。然后，特征图通过两个 Conv2DTranspose 层上采样到所需的输出形状 28 x 28，直到输出层，其中输出单个激活图。

| 层 (类型) | 输出形状 | 参数数量 |
|---|---|---|
| dense_1 (Dense) | (None, 6272) | 633472 |
| leaky_re_lu_1 (LeakyReLU) | (None, 6272) | 0 |
| reshape_1 (Reshape) | (None, 7, 7, 128) | 0 |
| conv2d_transpose_1 (Conv2DTranspose) | (None, 14, 14, 128) | 262272 |
| leaky_re_lu_2 (LeakyReLU) | (None, 14, 14, 128) | 0 |
| conv2d_transpose_2 (Conv2DTranspose) | (None, 28, 28, 128) | 262272 |
| leaky_re_lu_3 (LeakyReLU) | (None, 28, 28, 128) | 0 |
| conv2d_1 (Conv2D) | (None, 28, 28, 1) | 6273 |

总参数: 1,164,289
可训练参数: 1,164,289
不可训练参数: 0

清单 7.23：定义和汇总生成器模型的示例输出。

还会创建模型的图表，我们可以看到模型期望从潜在空间接收一个 100 元素的向量作为输入，并将生成图像作为输出。

**注意：** 创建模型图表假设已安装 `pydot` 和 `graphviz` 库。如果这是一个问题，您可以注释掉导入语句和 `plot_model()` 的函数调用。

![](img/443014fed0f53a293f6ece3b211c1603_125_0.png)

图 7.3：MNIST GAN 中生成器模型的图表。

目前该模型功能有限。尽管如此，我们可以演示如何使用它来生成样本。这是一个有用的演示，用于理解生成器只是另一个模型，其中一些元素以后会很有用。第一步是从潜在空间中抽取新点。我们可以通过调用 `randn()` NumPy 函数来实现这一点，该函数用于生成从标准高斯分布中抽取的随机数数组。然后可以将随机数数组重塑为样本，即 n 行，每行 100 个元素。下面的 `generate_latent_points()` 函数实现了此功能，并在潜在空间中生成所需数量的点，这些点可以用作生成器模型的输入。

```
# generate points in latent space as input for the generator
def generate_latent_points(latent_dim, n_samples):
    # generate points in the latent space
    x_input = randn(latent_dim * n_samples)
    # reshape into a batch of inputs for the network
    x_input = x_input.reshape(n_samples, latent_dim)
    return x_input
```

清单 7.24：在潜在空间中生成随机点的函数示例。

接下来，我们可以使用生成的点作为生成器模型的输入来生成新样本，然后绘制样本。我们可以更新上一节中的 `generate_fake_samples()` 函数，使其将生成器模型作为参数，并通过首先调用 `generate_latent_points()` 函数在潜在空间中生成所需数量的点作为模型输入，来使用它生成所需数量的样本。下面列出了更新后的 `generate_fake_samples()` 函数，它既返回生成的样本，也返回关联的类标签。

```
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

清单 7.25：使用生成器模型生成合成图像的函数示例。

然后，我们可以像在第一节中处理真实 MNIST 示例那样，通过调用带有反转灰度颜色映射的 `imshow()` 函数来绘制生成的样本。使用未训练的生成器模型生成新 MNIST 图像的完整示例如下所示。

```
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
    # foundation for 7x7 image
    n_nodes = 128 * 7 * 7
```
