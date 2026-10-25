
```
sudo pip install git+https://www.github.com/keras-team/keras-contrib.git
```

### 列表 25.1: 使用 pip 安装 keras-contrib 的示例。

或者，如果您使用的是 Anaconda 虚拟环境（例如在 EC2 上）：

```
git clone https://www.github.com/keras-team/keras-contrib.git
cd keras-contrib
sudo ~/anaconda3/envs/tensorflow_p36/bin/python setup.py install
```

### 列表 25.2: 使用 Anaconda 安装 keras-contrib 的示例。

然后可以按如下方式使用新的 InstanceNormalization 层：

```
...
from keras_contrib.layers.normalization.instancenormalization import InstanceNormalization
# define layer
layer = InstanceNormalization(axis=-1)
...
```

### 列表 25.3: 使用 InstanceNormalization 层的示例。

axis 参数设置为 -1，以确保按特征图对特征进行归一化。网络权重初始化为标准差为 0.02 的高斯随机数，如 DCGAN 中更通用的描述所述。

权重从高斯分布 N (0, 0.02) 中初始化。

> — 使用循环一致对抗网络进行无配对图像到图像翻译，2017年。

判别器模型使用最小二乘损失（L2）进行更新，即所谓的最小二乘生成对抗网络，或 LSGAN。

... 我们用最小二乘损失替换负对数似然目标。该损失在训练期间更稳定，并生成更高质量的结果。

> — 使用循环一致对抗网络进行无配对图像到图像翻译，2017年。

这可以通过实像类别 = 1 和伪像类别 = 0 的目标值之间的均方误差来实现。此外，论文建议在训练期间将判别器的损失减半，以相对于生成器减慢判别器的更新速度。

在实践中，在优化 D 时我们将目标除以 2，这使得 D 的学习速度相对于 G 的学习速度减慢。

> — 使用循环一致对抗网络进行无配对图像到图像翻译，2017年。

这可以通过在编译模型时将 loss_weights 参数设置为 0.5 来实现。这种加权似乎未在官方 Torch 实现中实现，当更新判别器模型时定义在 fDx_basic() 函数中。1https://github.com/junyanz/CycleGAN/blob/master/models/cycle_gan_model.lua#L136

下面的示例将这些内容结合在一起，使用 `define_discriminator()` 函数定义 PatchGAN 判别器。模型配置与论文附录中的描述相匹配，并包含来自官方 Torch 实现的其他细节，该实现定义在 `defineD_n_layers()` 函数²中。

```
# example of defining a 70x70 patchgan discriminator model
from keras.optimizers import Adam
from keras.initializers import RandomNormal
from keras.models import Model
from keras.models import Input
from keras.layers import Conv2D
from keras.layers import LeakyReLU
from keras.contrib.layers.normalization.instancenormalization import InstanceNormalization
from keras.utils.vis_utils import plot_model

# define the discriminator model
def define_discriminator(image_shape):
	# weight initialization
	init = RandomNormal(stddev=0.02)
	# source image input
	in_image = Input(shape=image_shape)
	# C64
	d = Conv2D(64, (4, 4), strides=(2, 2), padding='same', kernel_initializer=init)(in_image)
	d = LeakyReLU(alpha=0.2)(d)
	# C128
	d = Conv2D(128, (4, 4), strides=(2, 2), padding='same', kernel_initializer=init)(d)
	d = InstanceNormalization(axis=-1)(d)
	d = LeakyReLU(alpha=0.2)(d)
	# C256
	d = Conv2D(256, (4, 4), strides=(2, 2), padding='same', kernel_initializer=init)(d)
	d = InstanceNormalization(axis=-1)(d)
	d = LeakyReLU(alpha=0.2)(d)
	# C512
	d = Conv2D(512, (4, 4), strides=(2, 2), padding='same', kernel_initializer=init)(d)
	d = InstanceNormalization(axis=-1)(d)
	d = LeakyReLU(alpha=0.2)(d)
	# second last output layer
	d = Conv2D(512, (4, 4), padding='same', kernel_initializer=init)(d)
	d = InstanceNormalization(axis=-1)(d)
	d = LeakyReLU(alpha=0.2)(d)
	# patch output
	patch_out = Conv2D(1, (4, 4), padding='same', kernel_initializer=init)(d)
	# define model
	model = Model(in_image, patch_out)
	# compile model
	model.compile(loss='mse', optimizer=Adam(lr=0.0002, beta_1=0.5), loss_weights=[0.5])
	return model

# define image shape
image_shape = (256, 256, 3)
# create the model
model = define_discriminator(image_shape)
# summarize the model
model.summary()
# plot the model
plot_model(model, to_file='discriminator_model_plot.png', show_shapes=True, show_layer_names=True)
```

### 列表 25.4: 定义和总结 PatchGAN 判别器的示例。

**注意：** 创建模型图表假设已安装 `pydot` 和 `graphviz` 库。如果这是一个问题，您可以注释掉导入语句和 `plot_model()` 的函数调用。

运行示例会总结模型，显示每层的输入和输出大小。

| Layer (type) | Output Shape | Param # |
| :--- | :--- | :--- |
| input_1 (InputLayer) | (None, 256, 256, 3) | 0 |
| conv2d_1 (Conv2D) | (None, 128, 128, 64) | 3136 |
| leaky_re_lu1 (LeakyReLU) | (None, 128, 128, 64) | 0 |
| conv2d_2 (Conv2D) | (None, 64, 64, 128) | 131200 |
| instance_normalization_1 (InstanceNormalization) | (None, 64, 64, 128) | 256 |
| leaky_re_lu2 (LeakyReLU) | (None, 64, 64, 128) | 0 |
| conv2d_3 (Conv2D) | (None, 32, 32, 256) | 524544 |
| instance_normalization_2 (InstanceNormalization) | (None, 32, 32, 256) | 512 |
| leaky_re_lu3 (LeakyReLU) | (None, 32, 32, 256) | 0 |
| conv2d_4 (Conv2D) | (None, 16, 16, 512) | 2097664 |
| instance_normalization_3 (InstanceNormalization) | (None, 16, 16, 512) | 1024 |
| leaky_re_lu4 (LeakyReLU) | (None, 16, 16, 512) | 0 |
| conv2d_5 (Conv2D) | (None, 16, 16, 512) | 4194816 |
| instance_normalization_4 (InstanceNormalization) | (None, 16, 16, 512) | 1024 |
| leaky_re_lu5 (LeakyReLU) | (None, 16, 16, 512) | 0 |
| conv2d_6 (Conv2D) | (None, 16, 16, 1) | 8193 |
| Total params: 6,962,369 | | |
| Trainable params: 6,962,369 | | |
| Non-trainable params: 0 | | |

### 列表 25.5: 定义和总结 PatchGAN 判别器的示例输出。

还会创建模型架构图，以帮助了解图像数据通过模型时的输入、输出和转换。

![](img/443014fed0f53a293f6ece3b211c1603_551_0.png)

### 图 25.1: CycleGAN 的 PatchGAN 判别器模型图。

## 25.4 如何实现 CycleGAN 生成器模型

CycleGAN 生成器模型以图像作为输入，并生成翻译后的图像作为输出。该模型使用一系列下采样卷积块来编码输入图像，使用若干残差网络（ResNet）卷积块来转换图像，并
使用若干上采样卷积块来生成输出图像。

令 c7s1-k 表示带有 k 个过滤器且步幅为 1 的 7 × 7 卷积-InstanceNorm-ReLU 层。dk 表示带有 k 个过滤器且步幅为 2 的 3 × 3 卷积-InstanceNorm-ReLU 层。使用反射填充来减少伪影。Rk 表示一个残差块，包含两个 3 × 3 卷积层，两个层的过滤器数量相同。uk 表示带有 k 个过滤器且步幅为 1/2 的 3 × 3 分数步幅卷积-InstanceNorm-ReLU 层。

> — 使用循环一致对抗网络进行无配对图像到图像翻译，2017年。

用于 128 × 128 图像的 6-resnet 块生成器架构如下：

- c7s1-64,d128,d256,R256,R256,R256,R256,R256,R256,u128,u64,c7s1-3

首先，我们需要一个函数来定义 ResNet 块。这些块由两个 3 × 3 CNN 层组成，块的输入与块的输出按通道方向连接。这在 resnet_block() 函数中实现，该函数创建两个带有 3 × 3 过滤器和 1 × 1 步幅的 Conv-InstanceNorm 块，并且在第二个块后没有 ReLU 激活，与官方 Torch 实现中的 build_conv_block() 函数匹配。为简单起见，使用相同填充而不是论文中推荐的反射填充。

```
# generator a resnet block
def resnet_block(n_filters, input_layer):
    # weight initialization
    init = RandomNormal(stddev=0.02)
    # first layer convolutional layer
    g = Conv2D(n_filters, (3,3), padding='same', kernel_initializer=init)(input_layer)
    g = InstanceNormalization(axis=-1)(g)
    g = Activation('relu')(g)
    # second convolutional layer
    g = Conv2D(n_filters, (3,3), padding='same', kernel_initializer=init)(g)
    g = InstanceNormalization(axis=-1)(g)
    # concatenate merge channel-wise with input layer
    g = Concatenate()([g, input_layer])
    return g
```

### 列表 25.6: 定义 ResNet 块函数的示例。

接下来，我们可以定义一个函数来创建用于 256 × 256 输入图像的 9-resnet 块版本。这可以通过将 image_shape 参数设置为 (128 × 128 × 3) 并将 n_resnet 函数参数设置为 6，轻松更改为 6-resnet 块版本。重要的是，模型输出与输入形状相同的像素值，且像素值范围为 [-1, 1]，这对于 GAN 生成器模型来说是典型的。

```
# define the standalone generator model
def define_generator(image_shape=(256,256,3), n_resnet=9):
    # weight initialization
    init = RandomNormal(stddev=0.02)
    # image input
    in_image = Input(shape=image_shape)
    # c7s1-64
```
