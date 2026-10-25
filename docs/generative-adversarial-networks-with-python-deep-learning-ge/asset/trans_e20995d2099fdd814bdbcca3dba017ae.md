
运行示例会计算每个输入值的输出值，并创建输入与输出值的图表。我们可以看到，远离 0.0 的值会产生较大的输出值，而接近零的值会产生较小的输出值，并且这种行为在零周围是对称的。这是 X^2 一维函数的著名 U 形图。

![](img/443014fed0f53a293f6ece3b211c1603_87_0.png)

图 6.1: X^2 函数的输入与输出值图表。

我们可以从函数中生成随机样本或点。这可以通过生成 -0.5 到 0.5 之间的随机值并计算相关的输出值来实现。重复此过程多次将得到函数的一组点样本，例如真实样本。使用散点图绘制这些样本将显示相同的 U 形图，尽管由单独的随机样本组成。完整示例如下。首先，我们在 0 到 1 之间生成均匀随机值，然后将其移动到 -0.5 到 0.5 的范围。然后，我们为每个随机生成的输入值计算输出值，并将数组合并为一个具有 n 行（100）和两列的单个 NumPy 数组。

```
# example of generating random samples from X^2
from numpy.random import rand
from numpy import hstack
from matplotlib import pyplot

# generate random sample from x^2
def generate_samples(n=100):
    # generate random inputs in [-0.5, 0.5]
    X1 = rand(n) - 0.5
    # generate outputs X^2 (quadratic)
    X2 = X1 * X1
    # stack arrays
    X1 = X1.reshape(n, 1)
    X2 = X2.reshape(n, 1)
    return hstack((X1, X2))

# generate samples
data = generate_samples()
# plot samples
pyplot.scatter(data[:, 0], data[:, 1])
pyplot.show()
```

清单 6.3: 为目标函数采样域的示例。

运行示例会生成 100 个随机输入及其计算输出，并将样本绘制为散点图，显示熟悉的 U 形。

![](img/443014fed0f53a293f6ece3b211c1603_88_0.png)

图 6.2: X^2 函数随机生成的输入与计算输出的图表。

我们可以将此函数作为为判别器函数生成真实样本的起点。具体来说，一个样本由一个包含两个元素的向量组成，一个用于输入，一个用于我们的一维函数的输出。我们还可以想象生成器模型如何生成新样本，我们可以将其绘制出来并与 \(X^2\) 函数的预期 U 形进行比较。具体来说，生成器将输出一个包含两个元素的向量：一个用于输入，一个用于我们的一维函数的输出。

## 6.3 定义判别器模型

下一步是定义判别器模型。该模型必须接受我们问题中的一个样本（例如包含两个元素的向量），并输出一个分类预测，判断该样本是真实的还是伪造的。这是一个二分类问题。

- 输入：包含两个实数值的样本。
- 输出：二分类，样本为真实（或伪造）的可能性。

这个问题非常简单，这意味着我们不需要复杂的神经网络来对其进行建模。判别器模型将具有一个包含 25 个节点的隐藏层，我们将使用 ReLU 激活函数和一种称为 He 权重初始化的适当权重初始化方法。输出层将具有一个节点，用于使用 sigmoid 激活函数进行二分类。该模型将最小化二元交叉熵损失函数，并将使用 Adam 版本的随机梯度下降，因为它非常有效。下面的 `define_discriminator()` 函数定义并返回判别器模型。该函数参数化了预期的输入数量，默认值为两个。

```
# define the standalone discriminator model
def define_discriminator(n_inputs=2):
    model = Sequential()
    model.add(Dense(25, activation='relu', kernel_initializer='he_uniform',
                    input_dim=n_inputs))
    model.add(Dense(1, activation='sigmoid'))
    # compile model
    model.compile(loss='binary_crossentropy', optimizer='adam', metrics=['accuracy'])
    return model
```

清单 6.4: 定义判别器模型的函数示例。

我们可以使用此函数来定义判别器模型并对其进行总结。完整示例如下。

```
# define the discriminator model
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

model = define_discriminator()
# summarize the model
model.summary()
# plot the model
plot_model(model, to_file='discriminator_plot.png', show_shapes=True, show_layer_names=True)
```

清单 6.5: 定义并总结判别器模型的示例。

运行示例会定义判别器模型并对其进行总结。

| 层 (类型) | 输出形状 | 参数数量 |
|---|---|---|
| dense_1 (Dense) | (None, 25) | 75 |
| dense_2 (Dense) | (None, 1) | 26 |

总参数数: 101
可训练参数数: 101
不可训练参数数: 0

清单 6.6: 定义并总结判别器模型的示例输出。

> 注意：创建模型图假设已安装 `pydot` 和 `graphviz` 库。如果这是一个问题，您可以注释掉导入语句和 `plot_model()` 的函数调用。

![](img/443014fed0f53a293f6ece3b211c1603_90_0.png)

图 6.3: GAN 中判别器模型的图。

我们现在可以开始使用带有类标签 1 的真实示例和带有类标签 0 的随机生成样本来训练此模型。没有必要这样做，但我们将要开发的元素以后会很有用，并且有助于看到判别器只是一个普通的神经网络模型。首先，我们可以更新预测部分中的 generate_samples() 函数，将其命名为 generate_real_samples()，并使其也返回真实样本的输出类标签，具体来说，是一个值为 1 的数组，其中 class = 1 表示真实。

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

清单 6.7: 为目标函数创建随机样本的函数示例。

接下来，我们可以创建此函数的副本用于创建伪造示例。在这种情况下，我们将为样本的两个元素生成 -1 到 1 范围内的随机值。所有这些示例的输出类标签均为 0。此函数将充当我们的伪造生成器模型。

```
# generate n fake samples with class labels
def generate_fake_samples(n):
    # generate inputs in [-1, 1]
    X1 = -1 + rand(n) * 2
    # generate outputs in [-1, 1]
    X2 = -1 + rand(n) * 2
    # stack arrays
    X1 = X1.reshape(n, 1)
    X2 = X2.reshape(n, 1)
    X = hstack((X1, X2))
    # generate class labels
    y = zeros((n, 1))
    return X, y
```

清单 6.8: 为目标函数创建随机伪造样本的函数示例。

接下来，我们需要一个函数来训练和评估判别器模型。这可以通过手动枚举训练时代来实现，对于每个时代，生成一半批次的真实示例和一半批次的伪造示例，并分别对每个进行更新，例如一整批示例。可以使用 train() 函数，但在此情况下，我们将直接使用 train_on_batch() 函数。然后可以在生成的示例上评估模型，并报告真实和伪造样本上的分类准确率。下面的 train_discriminator() 函数实现了这一点，训练模型 1,000 个批次，每个批次使用 128 个样本（64 个伪造和 64 个真实）。

```
# train the discriminator model
def train_discriminator(model, n_epochs=1000, n_batch=128):
    half_batch = int(n_batch / 2)
    # run epochs manually
    for i in range(n_epochs):
        # generate real examples
        X_real, y_real = generate_real_samples(half_batch)
