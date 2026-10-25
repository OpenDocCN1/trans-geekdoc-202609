
模型权重通过均值为0.0、标准差为0.02的随机高斯分布进行初始化。输入到模型的图像尺寸为256 × 256。

> ... 在优化D时，我们将目标函数除以2，这会减慢D相对于G的学习速率。我们使用小批量SGD并应用Adam求解器，学习率为0.0002，动量参数为β1 = 0.5，β2 = 0.999。
> 
> — 《基于条件对抗网络的图像到图像翻译》，2016年。

模型以一张图像的批量大小进行训练，并使用带有较小学习率和适度动量的Adam版本随机梯度下降。每次模型更新时，判别器的损失都加权为50%。将所有这些整合在一起，我们可以定义一个名为define_discriminator()的函数，用于创建70 × 70 PatchGAN判别器模型。定义模型的完整示例如下。

```python
# example of defining a 70x70 patchgan discriminator model
from keras.optimizers import Adam
from keras.initializers import RandomNormal
from keras.models import Model
from keras.models import Input
from keras.layers import Conv2D
from keras.layers import LeakyReLU
from keras.layers import Activation
from keras.layers import Concatenate
from keras.layers import BatchNormalization
from keras.utils.vis_utils import plot_model

# define the discriminator model
def define_discriminator(image_shape):
    # weight initialization
    init = RandomNormal(stddev=0.02)
    # source image input
    in_src_image = Input(shape=image_shape)
    # target image input
    in_target_image = Input(shape=image_shape)
    # concatenate images channel-wise
    merged = Concatenate()([in_src_image, in_target_image])
    # C64
    d = Conv2D(64, (4,4), strides=(2,2), padding='same', kernel_initializer=init)(merged)
    d = LeakyReLU(alpha=0.2)(d)
    # C128
    d = Conv2D(128, (4,4), strides=(2,2), padding='same', kernel_initializer=init)(d)
    d = BatchNormalization()(d)
    d = LeakyReLU(alpha=0.2)(d)
    # C256
    d = Conv2D(256, (4,4), strides=(2,2), padding='same', kernel_initializer=init)(d)
    d = BatchNormalization()(d)
    d = LeakyReLU(alpha=0.2)(d)
    # C512
    d = Conv2D(512, (4,4), strides=(2,2), padding='same', kernel_initializer=init)(d)
    d = BatchNormalization()(d)
    d = LeakyReLU(alpha=0.2)(d)
    # second last output layer
    d = Conv2D(512, (4,4), padding='same', kernel_initializer=init)(d)
    d = BatchNormalization()(d)
    d = LeakyReLU(alpha=0.2)(d)
    # patch output
    d = Conv2D(1, (4,4), padding='same', kernel_initializer=init)(d)
    patch_out = Activation('sigmoid')(d)
    # define model
    model = Model([in_src_image, in_target_image], patch_out)
    # compile model
    opt = Adam(lr=0.0002, beta_1=0.5)
    model.compile(loss='binary_crossentropy', optimizer=opt, loss_weights=[0.5])
    return model

# define image shape
image_shape = (256,256,3)
# create the model
model = define_discriminator(image_shape)
# summarize the model
model.summary()
# plot the model
plot_model(model, to_file='discriminator_model_plot.png', show_shapes=True,
show_layer_names=True)
```

清单22.3：定义和总结PatchGAN判别器模型的示例。

运行示例首先会总结模型，提供关于输入形状如何在各层之间转换以及模型中参数数量的见解。为简洁起见，此处省略了输出。创建了一个模型图，以图形形式显示大部分相同的信息。该模型并不复杂，具有两个输入图像和一个单一输出预测的线性路径。

注意：创建模型图假设已安装pydot和graphviz库。如果这是一个问题，你可以注释掉导入语句和plot_model()函数调用。

我们可以看到，两个输入图像被连接在一起，作为第一个隐藏卷积层的一个256 × 256 × 6输入。这种输入图像的连接可能发生在模型输入层之前，但允许模型执行连接可以使模型的行为更清晰。我们可以看到，模型输出将是一个大小为16 × 16像素或激活值且只有一个通道的激活图，图中的每个值对应输入256 × 256图像的一个70 × 70像素补丁。如果输入图像尺寸减半为128 × 128，则输出特征图也将减半为8 × 8。该模型是一个二分类模型，意味着它将输出预测为[0,1]范围内的概率，在此例中，是输入图像是真实图像还是来自目标数据集的可能性。可以对补丁中的值进行平均，以给出模型的真实/假预测。训练时，目标与目标值矩阵进行比较，0表示假，1表示真。

## 22.3. 如何实现PatchGAN判别器模型

```
input_1: InputLayer
input: (None, 256, 256, 3)
output: (None, 256, 256, 3)

input_2: InputLayer
input: (None, 256, 256, 3)
output: (None, 256, 256, 3)

concatenate_1: Concatenate
input: [(None, 256, 256, 3), (None, 256, 256, 3)]
output: (None, 256, 256, 6)

conv2d_1: Conv2D
input: (None, 256, 256, 6)
output: (None, 128, 128, 64)

leaky_re_lu_1: LeakyReLU
input: (None, 128, 128, 64)
output: (None, 128, 128, 64)

conv2d_2: Conv2D
input: (None, 128, 128, 64)
output: (None, 64, 64, 128)

batch_normalization_1: BatchNormalization
input: (None, 64, 64, 128)
output: (None, 64, 64, 128)

leaky_re_lu_2: LeakyReLU
input: (None, 64, 64, 128)
output: (None, 64, 64, 128)

conv2d_3: Conv2D
input: (None, 64, 64, 128)
output: (None, 32, 32, 256)

batch_normalization_2: BatchNormalization
input: (None, 32, 32, 256)
output: (None, 32, 32, 256)

leaky_re_lu_3: LeakyReLU
input: (None, 32, 32, 256)
output: (None, 32, 32, 256)

conv2d_4: Conv2D
input: (None, 32, 32, 256)
output: (None, 16, 16, 512)

batch_normalization_3: BatchNormalization
input: (None, 16, 16, 512)
output: (None, 16, 16, 512)

leaky_re_lu_4: LeakyReLU
input: (None, 16, 16, 512)
output: (None, 16, 16, 512)

conv2d_5: Conv2D
input: (None, 16, 16, 512)
output: (None, 16, 16, 512)

batch_normalization_4: BatchNormalization
input: (None, 16, 16, 512)
output: (None, 16, 16, 512)

leaky_re_lu_5: LeakyReLU
input: (None, 16, 16, 512)
output: (None, 16, 16, 512)

conv2d_6: Conv2D
input: (None, 16, 16, 512)
output: (None, 16, 16, 1)

activation_1: Activation
input: (None, 16, 16, 1)
output: (None, 16, 16, 1)
```

图22.1：Pix2Pix GAN架构中使用的PatchGAN模型图。

既然我们知道如何实现PatchGAN判别器模型，现在可以着手实现U-Net生成器模型。

## 22.4 如何实现U-Net生成器模型

Pix2Pix GAN的生成器模型实现为U-Net。U-Net模型是一种用于图像翻译的编码器-解码器模型，其中跳跃连接用于将编码器中的层与解码器中具有相同尺寸特征图的对应层连接起来。模型的编码器部分由使用2 × 2步长将输入源图像下采样至瓶颈层的卷积层组成。模型的解码器部分读取瓶颈输出，并使用转置卷积层上采样到所需的输出图像尺寸。

> ... 输入通过一系列逐步下采样的层传递，直到
> 瓶颈层，此时过程被反转。
> 
> — 《基于条件对抗网络的图像到图像翻译》，2016年。

![](img/443014fed0f53a293f6ece3b211c1603_489_0.png)

图22.2：U-Net生成器模型架构。摘自《基于条件对抗网络的图像到图像翻译》。

在具有相同尺寸特征图的层之间添加跳跃连接，以便第一个下采样层与最后一个上采样层连接，第二个下采样层与倒数第二个上采样层连接，以此类推。这些连接将下采样层中的特征图通道与上采样层中的特征图通道进行拼接。

具体来说，我们在每个层i和层n - i之间添加跳跃连接，其中n是层的总数。每个跳跃连接只是将层i中的所有通道与层n - i中的通道进行拼接。

> — 《基于条件对抗网络的图像到图像翻译》，2016年。

与GAN架构中的传统生成器模型不同，U-Net生成器不以潜在空间中的一个点作为输入。相反，在训练期间以及使用模型进行预测（例如在推理时生成图像）时，都使用丢弃层作为随机性来源。同样，批量归一化在训练期间也以相同的方式使用。
