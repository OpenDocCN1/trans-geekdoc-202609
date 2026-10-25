

## 22.4. 如何实现 U-Net 生成器模型

训练和推理，意味着统计量是针对每个批次计算的，而不是在训练过程结束时固定。这被称为实例归一化，特别是当批次大小设置为 1 时，就像 Pix2Pix 模型一样。

在推理时，我们以与训练阶段完全相同的方式运行生成器网络。这与常规协议不同，因为我们在测试时应用丢弃，并且使用测试批次的统计量应用批量归一化，而不是训练批次的聚合统计量。

> — 《基于条件对抗网络的图像到图像翻译》，2016年。

在 Keras 中，Dropout 和 BatchNormalization 等层在训练和推理模型下的运行方式不同。我们可以在调用这些层时将 training 参数设置为 True，以确保它们始终以训练模型运行，即使在推理期间使用也是如此。例如，可以将在推理和训练期间都会丢弃的 Dropout 层按如下方式添加到模型中：

```
...
g = Dropout(0.5)(g, training=True)
```

清单 22.4: 在推理期间配置 Dropout 层以运行的示例。

与判别器模型一样，生成器模型的配置细节在论文的附录中定义，并可以通过与官方 Torch 实现中的 defineG_unet() 函数进行比较来确认。编码器使用与判别器模型类似的 Convolution-BatchNorm-LeakyReLU 块，而解码器模型使用丢弃率为 50% 的 Convolution-BatchNorm-Dropout-ReLU 块。所有卷积层都使用 4 x 4 的滤波器大小和 2 x 2 的步长。

令 Ck 表示带有 k 个滤波器的 Convolution-BatchNorm-ReLU 层。CDk 表示丢弃率为 50% 的 Convolution-BatchNormDropout-ReLU 层。所有卷积都是应用步长 2 的 4 x 4 空间滤波器。

> — 《基于条件对抗网络的图像到图像翻译》，2016年。

U-Net 模型的架构使用简写符号定义如下：

- 编码器：C64-C128-C256-C512-C512-C512-C512-C512
- 解码器：CD512-CD1024-CD1024-C1024-C1024-C512-C256-C128

编码器的最后一层是瓶颈层，根据对论文的修订和代码中的确认，该层不使用批量归一化，而是使用 ReLU 激活函数而非带泄漏的 ReLU。

... 瓶颈层的激活值会被批量归一化操作置零，从而实际上跳过最内层。可以通过从该层中移除批量归一化来修复此问题，就像公共代码中所做的那样

> — 《基于条件对抗网络的图像到图像翻译》，2016年。

U-Net 解码器中的滤波器数量有些误导，因为它是与编码器中等效层连接后的层的滤波器数量。当我们创建模型图时，这可能会更清楚。模型的输出使用带有三个通道的单个卷积层，输出层使用 Tanh 激活函数，这在 GAN 生成器模型中很常见。解码器的第一层不使用批量归一化。

在解码器的最后一层之后，应用一个卷积来映射到输出通道数量（通常为 3 [...]），后跟一个 Tanh 函数 [...] 编码器的第一个 C64 层不应用 BatchNorm。编码器中的所有 ReLU 都是带泄漏的，斜率为 0.2，而解码器中的 ReLU 不是带泄漏的。

> — 《基于条件对抗网络的图像到图像翻译》，2016年。

将所有这些整合在一起，我们可以定义一个名为 define_generator() 的函数来定义 U-Net 编码器-解码器生成器模型。还提供了两个辅助函数，用于定义编码器层块和解码器层块。定义模型的完整示例如下所示。

```python
# example of defining a u-net encoder-decoder generator model
from keras.initializers import RandomNormal
from keras.models import Model
from keras.models import Input
from keras.layers import Conv2D
from keras.layers import Conv2DTranspose
from keras.layers import LeakyReLU
from keras.layers import Activation
from keras.layers import Concatenate
from keras.layers import Dropout
from keras.layers import BatchNormalization
from keras.layers import LeakyReLU
from keras.utils.vis_utils import plot_model

# define an encoder block
def define_encoder_block(layer_in, n_filters, batchnorm=True):
    # weight initialization
    init = RandomNormal(stddev=0.02)
    # add downsampling layer
    g = Conv2D(n_filters, (4,4), strides=(2,2), padding='same', kernel_initializer=init)(layer_in)
    # conditionally add batch normalization
    if batchnorm:
        g = BatchNormalization()(g, training=True)
    # leaky relu activation
    g = LeakyReLU(alpha=0.2)(g)
    return g

# define a decoder block
def decoder_block(layer_in, skip_in, n_filters, dropout=True):
    # weight initialization
    init = RandomNormal(stddev=0.02)
    # add upsampling layer
    g = Conv2DTranspose(n_filters, (4,4), strides=(2,2), padding='same',
         kernel_initializer=init)(layer_in)
    # add batch normalization
    g = BatchNormalization()(g, training=True)
    # conditionally add dropout
    if dropout:
        g = Dropout(0.5)(g, training=True)
    # merge with skip connection
    g = Concatenate()([g, skip_in])
    # relu activation
    g = Activation('relu')(g)
    return g

# define the standalone generator model
def define_generator(image_shape=(256,256,3)):
    # weight initialization
    init = RandomNormal(stddev=0.02)
    # image input
    in_image = Input(shape=image_shape)
    # encoder model: C64-C128-C256-C512-C512-C512-C512
    e1 = define_encoder_block(in_image, 64, batchnorm=False)
    e2 = define_encoder_block(e1, 128)
    e3 = define_encoder_block(e2, 256)
    e4 = define_encoder_block(e3, 512)
    e5 = define_encoder_block(e4, 512)
    e6 = define_encoder_block(e5, 512)
    e7 = define_encoder_block(e6, 512)
    # bottleneck, no batch norm and relu
    b = Conv2D(512, (4,4), strides=(2,2), padding='same', kernel_initializer=init)(e7)
    b = Activation('relu')(b)
    # decoder model: CD512-CD1024-CD1024-C1024-C1024-C512-C256-C128
    d1 = decoder_block(b, e7, 512)
    d2 = decoder_block(d1, e6, 512)
    d3 = decoder_block(d2, e5, 512)
    d4 = decoder_block(d3, e4, 512, dropout=False)
    d5 = decoder_block(d4, e3, 256, dropout=False)
    d6 = decoder_block(d5, e2, 128, dropout=False)
    d7 = decoder_block(d6, e1, 64, dropout=False)
    # output
    g = Conv2DTranspose(3, (4,4), strides=(2,2), padding='same', kernel_initializer=init)(d7)
    out_image = Activation('tanh')(g)
    # define model
    model = Model(in_image, out_image)
    return model

# define image shape
image_shape = (256,256,3)
# create the model
model = define_generator(image_shape)
# summarize the model
model.summary()
# plot the model
plot_model(model, to_file='generator_model_plot.png', show_shapes=True,
     show_layer_names=True)
```

运行示例首先会汇总模型。为简洁起见，此处省略了模型汇总的输出。该模型有一个输入和一个输出，但跳跃连接使得汇总难以阅读。创建了一个模型图，以图形形式显示大部分相同的信息。该模型很复杂，图有助于理解跳跃连接及其对解码器中滤波器数量的影响。

注意：创建模型图假设已安装 `pydot` 和 `graphviz` 库。如果这是一个问题，你可以注释掉导入语句和 `plot_model()` 的函数调用。

从输出层开始逆向推导，如果我们查看解码器中的 `Concatenate` 层和第一个 `Conv2DTranspose` 层，可以看到通道数量为：

- 128, 256, 512, 1024, 1024, 1024, 1024, 512

反转此列表即可得到论文中解码器每层滤波器数量的所述配置：

- CD512-CD1024-CD1024-C1024-C1024-C512-C256-C128

为简洁起见，此处省略了模型汇总和图。现在我们已经定义了两个模型，可以查看生成器模型如何通过判别器模型进行更新。

## 22.5 如何实现对抗损失和 L1 损失

判别器模型可以直接更新，而生成器模型必须通过判别器模型进行更新。可以通过在 Keras 中定义一个新的组合模型来实现这一点，该模型将生成器模型的输出作为输入连接到判别器模型。然后，判别器模型可以预测生成的图像是真实还是假冒。我们可以以这样的方式更新组合模型的权重，即生成的图像带有 *真实* 而不是 *假冒* 的标签，这将导致生成器权重朝着生成更好的假冒图像的方向更新。我们还可以在此上下文中将判别器权重标记为不可训练，以避免误导性更新。此外，生成器需要更新以更好地匹配输入图像的目标翻译。这意味着组合模型还必须直接输出生成的图像，以便将其与目标图像进行比较。因此，我们可以如下总结此组合模型的输入和输出：

- 输入：源图像
- 输出：真实/假冒分类，生成的目标图像。

生成器的权重将通过判别器输出的对抗损失和直接图像输出的 L1 损失同时更新。损失分数相加，其中 L1 损失被视为正则化项，并通过名为 lambda (λ) 的超参数加权，设置为 100。

loss = 对抗损失 + λ × L1 损失 (22.2)

