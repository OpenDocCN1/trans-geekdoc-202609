

```
# C512
d = Conv2D(512, (4,4), strides=(2,2), padding='same', kernel_initializer=init)(d)
d = BatchNormalization()(d)
d = LeakyReLU(alpha=0.2)(d)
# second last output layer
d = Conv2D(512, (4, 4), padding='same', kernel_initializer=init)(d)
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
```

### 列表 23.7：定义 PatchGAN 判别器函数的示例。

生成器模型比判别器模型更复杂。生成器是一个使用 U-Net 架构的编码器-解码器模型。该模型接受源图像（例如卫星照片）作为输入并生成目标图像（例如 Google 地图图像）。它首先将输入图像下采样或编码到瓶颈层，然后将瓶颈表示上采样或解码到输出图像的大小。U-Net 架构意味着在编码层和相应的解码层之间添加跳跃连接，形成 U 形。生成器的编码器和解码器由标准化的卷积层、批量归一化层、丢弃层和激活层块组成。这种标准化意味着我们可以开发辅助函数来创建每个层块，并反复调用它来构建模型的编码器和解码器部分。

下面的 define_generator() 函数实现了 U-Net 编码器-解码器生成器模型。它使用 define_encoder_block() 辅助函数为编码器创建层块，并使用 decoder_block() 函数为解码器创建层块。输出层使用 Tanh 激活函数，这意味着生成图像中的像素值将在范围 [-1,1] 内。

```
# define an encoder block
def define_encoder_block(layer_in, n_filters, batchnorm=True):
    # weight initialization
    init = RandomNormal(stddev=0.02)
    # add downsampling layer
    g = Conv2D(n_filters, (4,4), strides=(2,2), padding='same',
               kernel_initializer=init)(layer_in)
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
    # encoder model
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
    # decoder model
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
```

### 列表 23.8：定义 U-Net 生成器函数的示例。

判别器模型直接在真实图像和生成图像上进行训练，而生成器模型则不是。相反，生成器模型是通过判别器模型进行训练的。它会根据判别器对被标记为真实的生成图像所预测的损失进行更新，以最小化该损失。因此，它被鼓励生成更真实的图像。生成器还会根据生成图像与目标图像之间的 L1 损失或平均绝对误差进行更新，以最小化该损失。生成器通过对抗损失和 L1 损失的加权和进行更新，模型作者建议将权重设置为 100 比 1，偏向 L1 损失。

这是为了强烈鼓励生成器生成输入图像的合理翻译，而不仅仅是目标域中的合理图像。

这可以通过定义一个新的逻辑模型来实现，该模型由现有独立生成器和判别器模型中的权重组成。这个逻辑或组合模型涉及将生成器堆叠在判别器之上。源图像作为输入提供给生成器和判别器，尽管生成器的输出作为相应的 *目标* 图像连接到判别器。然后，判别器预测生成图像是源图像的真实翻译的可能性。判别器以独立方式更新，因此权重在此组合模型中被重用，但被标记为不可训练。组合模型使用两个目标进行更新，一个指示生成的图像是真实的（交叉熵损失），迫使生成器进行大权重更新以生成更真实的图像，另一个是图像的实际真实翻译，它与生成器模型的输出进行比较（L1 损失）。下面的 `define_gan()` 函数实现了这一点，将已定义的生成器和判别器模型作为参数，并使用 Keras 函数式 API 将它们连接成一个组合模型。两个损失函数分别针对模型的两个输出指定，每个损失使用的权重在 `compile()` 函数的 `loss_weights` 参数中指定。

```
# define the combined generator and discriminator model, for updating the generator
def define_gan(g_model, d_model, image_shape):
    # make weights in the discriminator not trainable
    d_model.trainable = False
    # define the source image
    in_src = Input(shape=image_shape)
    # connect the source image to the generator input
    gen_out = g_model(in_src)
    # connect the source input and generator output to the discriminator input
    dis_out = d_model([in_src, gen_out])
    # src image as input, generated image and classification output
    model = Model(in_src, [dis_out, gen_out])
    # compile model
    opt = Adam(lr=0.0002, beta_1=0.5)
    model.compile(loss=['binary_crossentropy', 'mae'], optimizer=opt, loss_weights=[1,100])
    return model
```

### 列表 23.9：定义用于训练生成器的组合模型函数的示例。

接下来，我们可以以压缩 NumPy 数组格式加载配对图像数据集。这将返回一个包含两个 NumPy 数组的列表：第一个用于源图像，第二个用于相应的目标图像。

```
# load and prepare training images
def load_real_samples(filename):
    # load the compressed arrays
    data = load(filename)
    # unpack the arrays
    X1, X2 = data['arr_0'], data['arr_1']
    # scale from [0,255] to [-1,1]
    X1 = (X1 - 127.5) / 127.5
    X2 = (X2 - 127.5) / 127.5
    return [X1, X2]
```

### 列表 23.10：加载准备好的数据集函数的示例。

