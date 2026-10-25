
```python
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
n_samples = 25
X, _ = generate_fake_samples(model, latent_dim, n_samples)
# plot the generated samples
for i in range(n_samples):
	# define subplot
	pyplot.subplot(5, 5, 1 + i)
	# turn off axis labels
	pyplot.axis('off')
	# plot single image
	pyplot.imshow(X[i, :, :, 0], cmap='gray_r')
# show the figure
pyplot.show()
```

清单 7.26: 使用未训练的生成器输出随机图像的示例。

运行该示例将生成 25 个伪造的 MNIST 图像示例，并在 5×5 的单个图表中对其进行可视化。由于模型未经过训练，生成的图像是 [0, 1] 范围内完全随机的像素值。

![](img/443014fed0f53a293f6ece3b211c1603_128_0.png)

图 7.4: 未训练生成器模型输出的 25 张 MNIST 图像示例。

现在我们知道如何定义和使用生成器模型，下一步是训练该模型。

## 7.5 如何训练生成器模型

生成器模型的权重根据判别器模型的性能进行更新。当判别器擅长检测伪造样本时，生成器会被更新更多；而当判别器模型在检测伪造样本时表现较差或感到困惑时，生成器模型会被更新较少。这定义了这两个模型之间的零和或对抗关系。使用 Keras API 实现这一点可能有多种方法，但也许最简单的方法是创建一个结合生成器和判别器的新模型。具体来说，可以定义一个新的 GAN 模型，将生成器和判别器堆叠在一起，使生成器以潜在空间中的随机点作为输入并生成样本，这些样本直接输入判别器模型进行分类，而这个更大模型的输出可用于更新生成器的模型权重。

为了澄清，我们并不是在谈论一个新的第三个模型，而是一个新的逻辑模型，它使用独立生成器和判别器模型中已定义的层和权重。只有判别器关注区分真实样本和伪造样本，因此判别器模型可以像我们在上面的判别器模型部分中所做的那样，以独立方式对每类样本进行训练。生成器模型只关注判别器在伪造样本上的性能。因此，当判别器作为 GAN 模型的一部分时，我们会将其所有层标记为不可训练，以便它们不会被更新并在伪造样本上过度训练。当通过这个逻辑 GAN 模型训练生成器时，还有一个重要的变化。我们希望判别器认为生成器输出的样本是真实的，而不是伪造的。因此，当生成器作为 GAN 模型的一部分进行训练时，我们会将生成的样本标记为真实（class = 1）。

**我们为什么要这样做？** 我们可以想象，判别器随后会将生成的样本分类为非真实（class = 0）或真实概率较低（0.3 或 0.5）。用于更新模型权重的反向传播过程会将其视为较大的误差，并更新模型权重（即仅更新生成器中的权重）以纠正此误差，从而使生成器更擅长生成高质量的伪造样本。让我们具体说明一下。

- **输入**：潜在空间中的点，例如 100 个元素的高斯随机数向量。
- **输出**：二元分类，样本是真实（或伪造）的可能性。

下面的 `define_gan()` 函数以已定义的生成器和判别器模型作为参数，并创建包含这两个模型的新逻辑第三个模型。判别器中的权重被标记为不可训练，这仅影响 GAN 模型所看到的权重，而不影响独立的判别器模型。随后，GAN 模型使用与判别器相同的二元交叉熵损失函数，以及高效的 Adam 版本的随机梯度下降，学习率为 0.0002，动量为 0.5，在训练深度卷积 GAN 时推荐使用。

```python
# define the combined generator and discriminator model, for updating the generator
def define_gan(g_model, d_model):
    # make weights in the discriminator not trainable
    d_model.trainable = False
    # connect them
    model = Sequential()
    # add generator
    model.add(g_model)
    # add the discriminator
    model.add(d_model)
    # compile model
    opt = Adam(lr=0.0002, beta_1=0.5)
    model.compile(loss='binary_crossentropy', optimizer=opt)
    return model
```

清单 7.27: 定义复合模型的函数示例，用于通过判别器模型更新生成器模型。

在 Keras API 中，将判别器设置为不可训练是一个巧妙的技巧。trainable 属性在模型编译后影响模型。判别器模型是使用可训练层编译的，因此当通过调用 `train_on_batch()` 函数更新独立模型时，这些层中的模型权重会被更新。随后，判别器模型被标记为不可训练，添加到 GAN 模型中并进行编译。在这个模型中，判别器模型的模型权重不可训练，当通过调用 `train_on_batch()` 函数更新 GAN 模型时，这些权重无法更改。trainable 属性的这一更改不会影响独立判别器模型的训练。创建判别器、生成器和复合模型的完整示例如下所示。

```python
# demonstrate creating the three models in the gan
from keras.optimizers import Adam
from keras.models import Sequential
from keras.layers import Dense
from keras.layers import Reshape
from keras.layers import Flatten
from keras.layers import Conv2D
from keras.layers import Conv2DTranspose
from keras.layers import LeakyReLU
from keras.layers import Dropout
from keras.utils.vis_utils import plot_model

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

# define the combined generator and discriminator model, for updating the generator
def define_gan(g_model, d_model):
    # make weights in the discriminator not trainable
    d_model.trainable = False
    # connect them
    model = Sequential()
    # add generator
    model.add(g_model)
    # add the discriminator
    model.add(d_model)
```
