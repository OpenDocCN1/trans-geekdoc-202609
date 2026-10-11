

#### 3. 定义 GAN 模型的生成器和判别器

如果给定许多二维坐标点，但不知道真实分布，可以训练一个 GAN 模型，使其生成器生成的坐标点分布非常接近这些真实坐标点的分布。

与生成一组实数的 GAN 建模和训练过程相同，你只需要为该问题定义一个特定的生成器和判别器。当然，针对不同问题的 GAN，生成器和判别器的训练参数也必须做相应的调整（即参数调整）。

```python
from NeuralNetwork import *
# from util import *
from train import *

np.random.seed(0)

G_hidden, D_hidden = 10, 10
z_dim = 2                            # 隐变量的维度

G = NeuralNetwork()
G.add_layer(Dense(z_dim, G_hidden))
G.add_layer(Leaky_relu(0.2)) # Relu()
G.add_layer(Dense(G_hidden, 2))

D = NeuralNetwork()
D.add_layer(Dense(2, D_hidden))
D.add_layer(Leaky_relu(0.2)) # Relu()
D.add_layer(Dense(D_hidden, 1))
```

#### 4. 训练 GAN 模型

首先定义一个显示中间结果的函数 `show_result()`：

```python
def draw_loss(ax, D_losses=None, G_losses=None):
    ax.clear()
    i = np.arange(len(D_losses))
    if D_losses:
        ax.plot(i, D_losses, '-')
    if D_losses:
        ax.plot(i, G_losses, '-')
    ax.legend(['D_losses', 'G_losses'])

def show_ellipse_gan(D_losses=None, G_losses=None, m=100):
    fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(10, 4))
    draw_loss(ax1, D_losses, G_losses)
    ax2.clear()
    if True:
        data = sample_ellipse(100, cx, cy, a, b)
        ax2.scatter(data[:, 0], data[:, 1])
    else:
        alpha = np.linspace(0, 2 * math.pi, 100)
        x, y = cx + a * np.cos(alpha), cy + b * np.sin(alpha)
        ax2.plot(x, y, label='real data')
    noise_it = noise_z_iterator(m, z_dim)
    z = next(noise_it)
    fake_data = G(z)
    ax2.scatter(fake_data[:, 0], fake_data[:, 1], label='fake data')
    plt.show()

show_result = show_ellipse_gan  # lambda D_losses, G_losses: show_ellipse_gan(D_losses, G_losses)
```

然后定义分别对应判别器和生成器的参数优化器 `D_optimizer` 和 `G_optimizer`。它们的学习率仍为 `1e-4`，并将每个判别器和生成器的迭代次数 `d_steps` 和 `g_steps` 设置为 12 和 1。设置正则化参数 `reg = 1e-4`。开始训练：

```python
from util import *

# 为训练 G 和 D 定义优化器算法对象
momentum = 0.9
D_lr = 1e-4  # 1e-4
G_lr = 1e-4  # 1e-4
beta_1, beta_2 = 0.9, 0.999
D_optimizer = Adam(D.parameters(), D_lr, beta_1, beta_2)
G_optimizer = Adam(G.parameters(), G_lr, beta_1, beta_2)
reg = 1e-4  # 0.001 # 1e-5 # 1e-5
iterations = 300000
d_steps, g_steps = 12, 1
print_n = 500
D_losses, G_losses = GAN_train(D, G, D_optimizer, G_optimizer, data_it, noise_it, BCE_loss_grad, iterations,
                               reg, show_result, d_steps, g_steps, print_n)
```

以下是迭代过程中的部分中间输出结果：

```
0 iter: D_loss 2.1742366959961332 G_loss 0.8968873898437348
![](8_GAN\ellipse_gan_0.png)
2000 iter: D_loss 0.3267357227744408 G_loss 2.3412898225834082
![](8_GAN\ellipse_gan_2000.png)
7000 iter: D_loss 1.2152731903087477 G_loss 0.9141720546508202
![](8_GAN\ellipse_gan_7000.png)
30000 iter: D_loss 1.0173900698057503 G_loss 1.1880948654376398
![](8_GAN\ellipse_gan_30000.png)
160000 iter: D_loss 1.3094760434222943 G_loss 0.9307732117439997
![](8_GAN\ellipse_gan_160000.png)
299500 iter: D_loss 1.350800595219167 G_loss 0.8432568162317724
```

![](EPUB/media/file192.png)

图 8-27 一组二维坐标点 GAN 模型训练过程中的部分中间结果

### 8.5.3 MNIST 数据集的 GAN 建模

同样的过程可用于训练 GAN 模型以生成 Mnist 手写数字图像。

#### 1. 读取训练数据

以下代码读取 Mnist 数据集并将数值归一化到 -1 和 1 之间。

```python
import data_set as ds
import matplotlib.pyplot as plt
%matplotlib inline

train_set, valid_set, test_set = ds.read_mnist()
train_X, train_y = train_set
valid_X, valid_y = valid_set
test_X, test_y = test_set

print(train_X.dtype)
print(train_X.shape)
print(train_y.dtype)
print(train_y.shape)
print(np.min(train_X[0]), np.max(train_X[0]))

train_X = (train_X - 0.5) * 2
print(np.min(train_X[0]), np.max(train_X[0]))

ds.draw_mnists(plt, train_X, range(10))
plt.show()
```

```
float32
(50000, 784)
int64
(50000,)
0.0 0.99609375
-1.0 0.9921875
```

![](EPUB/media/file193.png)

#### 2. 定义数据迭代器

```python
z_dim = 64
batch_size = 32
data_it = data_iterator_X(train_X, batch_size, shuffle=True, repeat=True)
noise_it = noise_z_iterator(batch_size, z_dim)
```

#### 3. 定义生成器和判别器及其优化器

```python
from util import *
from NeuralNetwork import *
# from train import *
import time

np.random.seed(0)

image_dim = 784
g_hidden_dim = 256
d_hidden_dim = 256
d_output_dim = 1

G = NeuralNetwork()
G.add_layer(Dense(z_dim, g_hidden_dim))
G.add_layer(Relu())  # Leaky_relu(0.2)
G.add_layer(Dense(g_hidden_dim, g_hidden_dim))
G.add_layer(Relu())  # Leaky_relu(0.2)
G.add_layer(Dense(g_hidden_dim, image_dim))
G.add_layer(Tanh())

D = NeuralNetwork()
D.add_layer(Dense(image_dim, d_hidden_dim))
D.add_layer(Leaky_relu(0.2))  # Relu()
D.add_layer(Dense(d_hidden_dim, d_hidden_dim))
D.add_layer(Leaky_relu(0.2))  # Relu()
D.add_layer(Dense(d_hidden_dim, d_output_dim))

# 为训练 G 和 D 定义优化器算法对象
D_lr = 0.0002  # 0.0001
G_lr = 0.0002  # 0.0001
beta_1, beta_2 = 0.9, 0.999
D_optimizer = Adam(D.parameters(), D_lr, beta_1, beta_2)
G_optimizer = Adam(G.parameters(), G_lr, beta_1, beta_2)
```

#### 4. 训练模型

定义一个显示中间结果的复杂函数 `show_result_mnist()`：

```python
def plot_images(images, subplot_shape):
    plt.style.use('ggplot')
    fig, axes = plt.subplots(*subplot_shape)
    for image, ax in zip(images, axes.flatten()):
        ax.imshow(image.reshape(28, 28), cmap='Greys')
        # ax.imshow(image.reshape(28, 28), vmin=0, vmax=1.0, cmap='gray')
        ax.axis('off')
    plt.show()

def show_result_mnist(D_losses=None, G_losses=None, m=10):
    # fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(10, 4))
    # ax1.clear()
    if D_losses and G_losses:
        i = np.arange(len(D_losses))
        plt.plot(i, D_losses, '-')
        plt.plot(i, G_losses, '-')
        plt.legend(['D_losses)', 'G_losses'])
        plt.show()
    # ax2.clear()
    z = np.random.randn(m, z_dim)
    x_fake = G(z)
    # ds.draw_mnists(plt, x_fake, range(m))
    plot_images(x_fake, subplot_shape=[1, 10])
    plt.show()

show_result = show_result_mnist
```

使用以下训练过程训练 GAN 模型：

```python
start = time.time()
reg = 1e-6  # 1e-5 # 1e-5
iterations = 180000
d_steps, g_steps = 1, 1  # 2,1 # 12,1
print_n = 500
D_losses, G_losses = GAN_train(D, G, D_optimizer, G_optimizer, data_it, noise_it, BCE_loss_grad, iterations,
                               reg, show_result, d_steps, g_steps, print_n)
done = time.time()
elapsed = done - start
print("Training time: %d Second" % (elapsed))
```

```
121500 iter: D_loss 1.2937134810406197 G_loss 1.4630274260796108
```

