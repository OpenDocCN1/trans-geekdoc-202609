

鉴别器在真实样本和假样本上的损失出现震荡（橙色和蓝色）。在底部子图中，我们可以看到，鉴别器在整个运行过程中对假图像的分类准确率始终很高。这表明生成器以某种一致的方式生成样本的能力较差，这使得鉴别器很容易识别出假图像。

![](img/443014fed0f53a293f6ece3b211c1603_244_0.png)

图 10.5：带有模式崩溃的生成对抗网络的损失和准确率折线图。

查看生成的图像显示了模式崩溃的预期特征，即许多几乎相同的生成示例，无论潜在空间中的输入点如何。碰巧的是，我们将潜在空间的维度改为非常小，以强制产生这种效果。我选择了一个有助于说明这一点的生成图像示例。图中似乎只有几种类型的数字8，一个向左倾斜，一个向右倾斜，还有一个模糊地竖直放置。我在下面的图像中对一些相似的示例画了方框，以便更清楚地说明这一点。

![](img/443014fed0f53a293f6ece3b211c1603_245_0.png)

图 10.6：来自遭受模式崩溃的GAN在315个时代生成的100个手写数字8的样本。

鉴于DCGAN模型架构和训练配置的研究结果，训练期间模式崩溃较少见。总结来说，你可以按以下方式识别模式崩溃：

- 生成器（以及可能的鉴别器）的损失预计会随时间震荡。
- 生成器模型预计会从潜在空间的不同点生成相同的输出图像。

## 10.4 如何识别收敛失败

训练GAN时最常见的失败可能是收敛失败。通常，当模型损失在训练过程中不稳定时，神经网络就会无法收敛。在GAN的情况下，收敛失败是指找不到鉴别器和生成器之间的平衡。你识别此类失败的可能方式是鉴别器的损失降至零或接近零。在某些情况下，生成器的损失在同一时期也可能上升并继续上升。

这种损失最常见的原因是生成器输出了鉴别器可以轻松识别的垃圾图像。这种失败可能发生在运行开始时并贯穿整个训练过程，此时你应该停止训练过程。对于某些不稳定的GAN，GAN可能会陷入这种失败模式进行若干批次更新，甚至若干个时代，然后恢复。有许多方法可以破坏我们稳定的GAN以实现收敛失败，例如将一个或两个模型更改为容量不足，将Adam优化算法更改为过于激进，以及在模型中使用非常大或非常小的内核大小。

在这种情况下，我们将更新示例，在更新鉴别器时合并真实样本和假样本。这个简单的更改会导致模型无法收敛。这个更改简单到只需使用`vstack()`NumPy函数合并真实样本和假样本，然后调用`train_on_batch()`函数来更新鉴别器模型。结果也是单个损失和准确率分数，这意味着模型性能的报告也必须更新。为完整起见，下面提供了包含这些更改的完整代码清单。

```
# example of training an unstable gan for generating a handwritten digit
from os import makedirs
from numpy import expand_dims
from numpy import zeros
from numpy import ones
from numpy import vstack
from numpy.random import randn
from numpy.random import randint
from keras.datasets.mnist import load_data
from keras.optimizers import Adam
from keras.models import Sequential
from keras.layers import Dense
from keras.layers import Reshape
from keras.layers import Flatten
from keras.layers import Conv2D
from keras.layers import Conv2DTranspose
from keras.layers import LeakyReLU
from keras.layers import BatchNormalization
from keras.initializers import RandomNormal
from matplotlib import pyplot

# define the standalone discriminator model
def define_discriminator(in_shape=(28,28,1)):
    # weight initialization
    init = RandomNormal(stddev=0.02)
    # define model
    model = Sequential()
    # downsample to 14x14
    model.add(Conv2D(64, (4,4), strides=(2,2), padding='same', kernel_initializer=init, input_shape=in_shape))
    model.add(BatchNormalization())
    model.add(LeakyReLU(alpha=0.2))
    # downsample to 7x7
    model.add(Conv2D(64, (4,4), strides=(2,2), padding='same', kernel_initializer=init))
    model.add(BatchNormalization())
    model.add(LeakyReLU(alpha=0.2))
    # classifier
    model.add(Flatten())
    model.add(Dense(1, activation='sigmoid'))
    # compile model
    opt = Adam(lr=0.0002, beta_1=0.5)
    model.compile(loss='binary_crossentropy', optimizer=opt, metrics=['accuracy'])
    return model
```

```
# define the standalone generator model
def define_generator(latent_dim):
    # weight initialization
    init = RandomNormal(stddev=0.02)
    # define model
    model = Sequential()
    # foundation for 7x7 image
    n_nodes = 128 * 7 * 7
    model.add(Dense(n_nodes, kernel_initializer=init, input_dim=latent_dim))
    model.add(LeakyReLU(alpha=0.2))
    model.add(Reshape((7, 7, 128)))
    # upsample to 14x14
    model.add(Conv2DTranspose(128, (4,4), strides=(2,2), padding='same',
        kernel_initializer=init))
    model.add(BatchNormalization())
    model.add(LeakyReLU(alpha=0.2))
    # upsample to 28x28
    model.add(Conv2DTranspose(128, (4,4), strides=(2,2), padding='same',
        kernel_initializer=init))
    model.add(BatchNormalization())
    model.add(LeakyReLU(alpha=0.2))
    # output 28x28x1
    model.add(Conv2D(1, (7,7), activation='tanh', padding='same', kernel_initializer=init))
    return model
```

```
# define the combined generator and discriminator model, for updating the generator
def define_gan(generator, discriminator):
    # make weights in the discriminator not trainable
    discriminator.trainable = False
    # connect them
    model = Sequential()
    # add generator
    model.add(generator)
    # add the discriminator
    model.add(discriminator)
    # compile model
    opt = Adam(lr=0.0002, beta_1=0.5)
    model.compile(loss='binary_crossentropy', optimizer=opt)
    return model
```

```
# load mnist images
def load_real_samples():
    # load dataset
    (trainX, trainy), (_, _) = load_data()
    # expand to 3d, e.g. add channels
    X = expand_dims(trainX, axis=-1)
    # select all of the examples for a given class
    selected_ix = trainy == 8
    X = X[selected_ix]
    # convert from ints to floats
    X = X.astype('float32')
    # scale from [0,255] to [-1,1]
    X = (X - 127.5) / 127.5
    return X

## select real samples
def generate_real_samples(dataset, n_samples):
    # choose random instances
    ix = randint(0, dataset.shape[0], n_samples)
    # select images
    X = dataset[ix]
    # generate class labels
    y = ones((n_samples, 1))
    return X, y

## generate points in latent space as input for the generator
def generate_latent_points(latent_dim, n_samples):
    # generate points in the latent space
    x_input = randn(latent_dim * n_samples)
    # reshape into a batch of inputs for the network
    x_input = x_input.reshape(n_samples, latent_dim)
    return x_input

## use the generator to generate n fake examples, with class labels
def generate_fake_samples(generator, latent_dim, n_samples):
    # generate points in latent space
    x_input = generate_latent_points(latent_dim, n_samples)
    # predict outputs
    X = generator.predict(x_input)
    # create class labels
    y = zeros((n_samples, 1))
    return X, y

## generate samples and save as a plot and save the model
def summarize_performance(step, g_model, latent_dim, n_samples=100):
    # prepare fake examples
    X, _ = generate_fake_samples(g_model, latent_dim, n_samples)
    # scale from [-1,1] to [0,1]
    X = (X + 1) / 2.0
    # plot images
    for i in range(10 * 10):
        # define subplot
        pyplot.subplot(10, 10, 1 + i)
        # turn off axis
        pyplot.axis('off')
        # plot raw pixel data
        pyplot.imshow(X[i, :, :, 0], cmap='gray_r')
    # save plot to file
    pyplot.savefig('results_convergence/generated_plot_%03d.png' % (step+1))
    pyplot.close()
    # save the generator model
    g_model.save('results_convergence/model_%03d.h5' % (step+1))

## create a line plot of loss for the gan and save to file
def plot_history(d_hist, g_hist, a_hist):
    # plot loss
    pyplot.subplot(2, 1, 1)
    pyplot.plot(d_hist, label='dis')
    pyplot.plot(g_hist, label='gen')
```

