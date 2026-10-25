

```
# demonstrate creating the three models in the gan
from keras.models import Sequential
from keras.layers import Dense
from keras.utils.vis_utils import plot_model

# define the standalone discriminator model
def define_discriminator(n_inputs=2):
	model = Sequential()
	model.add(Dense(25, activation='relu', kernel_initializer='he_uniform',
		input_dim=n_inputs))
	model.add(Dense(1, activation='sigmoid'))
	# compile model
	model.compile(loss='binary_crossentropy', optimizer='adam', metrics=['accuracy'])
	return model

# define the standalone generator model
def define_generator(latent_dim, n_outputs=2):
	model = Sequential()
	model.add(Dense(15, activation='relu', kernel_initializer='he_uniform',
		input_dim=latent_dim))
	model.add(Dense(n_outputs, activation='linear'))
	return model

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
	model.compile(loss='binary_crossentropy', optimizer='adam')
	return model

# size of the latent space
latent_dim = 5
# create the discriminator
discriminator = define_discriminator()
# create the generator
generator = define_generator(latent_dim)
# create the gan
gan_model = define_gan(generator, discriminator)
# summarize gan model
gan_model.summary()
# plot gan model
plot_model(gan_model, to_file='gan_plot.png', show_shapes=True, show_layer_names=True)
```

清单 6.19: 定义并汇总用于训练生成器的复合模型示例。

运行该示例会先创建复合模型的摘要。您可能会收到关于未调用 `compile()` 函数的 UserWarning，可以安全地忽略。

| 层 (类型) | 输出形状 | 参数数量 |
|---|---|---|
| sequential_2 (Sequential) | (None, 2) | 122 |
| sequential_1 (Sequential) | (None, 1) | 101 |
| 总参数: 223 | | |
| 可训练参数: 122 | | |
| 非可训练参数: 101 | | |

清单 6.20: 定义并汇总用于训练生成器的复合模型的示例输出。

还会创建模型的图，我们可以看到该模型期望将潜在空间中的五个元素点作为输入，并将预测单个输出分类标签。

**注意:** 创建模型图假设已安装 `pydot` 和 `graphviz` 库。如果这有问题，可以注释掉导入语句和 `plot_model()` 的函数调用。

![](img/443014fed0f53a293f6ece3b211c1603_101_0.png)

图 6.6: GAN 中复合生成器和判别器模型的图。

训练复合模型涉及通过前一节中的 `generate_latent_points()` 函数在潜在空间生成一批点，以及 `class = 1` 标签并调用 `train_on_batch()` 函数。下面的 `train_gan()` 函数演示了这一点，尽管它相当无趣，因为每个时代只会更新生成器，而判别器保留默认模型权重。

```
# train the composite model
def train_gan(gan_model, latent_dim, n_epochs=10000, n_batch=128):
    # manually enumerate epochs
    for i in range(n_epochs):
        # prepare points in latent space as input for the generator
        x_gan = generate_latent_points(latent_dim, n_batch)
        # create inverted labels for the fake samples
        y_gan = ones((n_batch, 1))
        # update the generator via the discriminator's error
        gan_model.train_on_batch(x_gan, y_gan)
```

清单 6.21: 训练复合模型的函数示例。

相反，需要的是我们先使用真实和假样本更新判别器模型，然后通过复合模型更新生成器。这需要结合判别器部分中定义的 `train_discriminator()` 函数和上面定义的 `train_gan()` 函数的元素。它还要求 `generate_fake_samples()` 函数使用生成器模型生成假样本，而不是生成随机数。用于更新判别器模型和生成器（通过复合模型）的完整训练函数如下所示。

```
# train the generator and discriminator
def train(g_model, d_model, gan_model, latent_dim, n_epochs=10000, n_batch=128):
    # determine half the size of one batch, for updating the discriminator
    half_batch = int(n_batch / 2)
    # manually enumerate epochs
    for i in range(n_epochs):
        # prepare real samples
        x_real, y_real = generate_real_samples(half_batch)
        # prepare fake examples
        x_fake, y_fake = generate_fake_samples(g_model, latent_dim, half_batch)
        # update discriminator
        d_model.train_on_batch(x_real, y_real)
        d_model.train_on_batch(x_fake, y_fake)
        # prepare points in latent space as input for the generator
        x_gan = generate_latent_points(latent_dim, n_batch)
        # create inverted labels for the fake samples
        y_gan = ones((n_batch, 1))
        # update the generator via the discriminator's error
        gan_model.train_on_batch(x_gan, y_gan)
```

清单 6.22: 训练判别器和生成器模型的函数示例。

我们几乎拥有开发一维函数 GAN 所需的一切。剩下的一个方面是模型评估。

### 6.6 评估 GAN 的性能

通常，没有客观的方法来评估 GAN 模型的性能。在此特定情况下，由于我们知道真实的底层输入域和目标函数，并可以计算客观误差度量，因此可以为生成的样本制定客观度量。尽管如此，本教程不会计算此客观误差分数。相反，我们将使用大多数 GAN 应用中采用的主观方法。具体来说，我们将使用生成器生成新样本，并将其与域中的真实样本进行相对检查。首先，我们可以使用上面判别器部分中开发的 `generate_real_samples()` 函数生成真实示例。创建这些示例的散点图将形成我们目标函数的熟悉 U 形。

```
# generate n real samples with class labels
def generate_real_samples(n):
    # generate inputs in [-0.5, 0.5]
    X1 = rand(n) - 0.5
    # generate outputs X^2
    X2 = X1 * X1
    # stack arrays
    X1 = X1.reshape(n, 1)
    X2 = X2.reshape(n, 1)
    X = hstack((X1, X2))
    # generate class labels
    y = ones((n, 1))
    return X, y
```

清单 6.23: 用于生成训练真实样本的函数示例。

接下来，我们可以使用生成器模型生成相同数量的假样本。这需要首先通过上面生成器部分中开发的 `generate_latent_points()` 函数在潜在空间生成相同数量的点。然后可以将这些点传递给生成器模型，并用于生成也可以在同一散点图上绘制的样本。

```
# generate points in latent space as input for the generator
def generate_latent_points(latent_dim, n):
    # generate points in the latent space
    x_input = randn(latent_dim * n)
    # reshape into a batch of inputs for the network
    x_input = x_input.reshape(n, latent_dim)
    return x_input
```

清单 6.24: 用于在潜在空间生成随机点的函数示例。

下面的 `generate_fake_samples()` 函数生成这些假样本及其关联的类标签 0，这在以后会很有用。

```
# use the generator to generate n fake examples, with class labels
def generate_fake_samples(generator, latent_dim, n):
    # generate points in latent space
    x_input = generate_latent_points(latent_dim, n)
    # predict outputs
    X = generator.predict(x_input)
    # create class labels
    y = zeros((n, 1))
    return X, y
```

清单 6.25: 用于生成假样本的函数示例。

将两个样本绘制在同一图上，可以直接比较，以查看是否覆盖了相同的输入和输出域，以及目标函数的预期形状是否已被适当捕获，至少在主观上是这样。下面的 `summarize_performance()` 函数可以在训练期间随时调用，以创建真实点和生成点的散点图，从而了解生成器模型的当前能力。

```
# plot real and fake points
def summarize_performance(generator, latent_dim, n=100):
    # prepare real samples
    x_real, y_real = generate_real_samples(n)
```

