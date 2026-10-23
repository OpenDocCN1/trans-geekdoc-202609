
## 其他重要的深度学习库

首先，我们需要考虑的是获取 MNIST 数据。幸好 TensorFlow 也在 `https://github.com/tensorflow/tensorflow/blob/master/tensorflow/examples/tutorials/mnist/input_data.py` 提供了获取数据的代码，我们把该代码放到同一目录下。然后，编写以下代码即可导入 MNIST 数据：

```python
import input_data
```

可以使用以下代码导入 MNIST 数据：

```python
mnist = input_data.read_data_sets("MNIST_data/", one_hot=True)
```

与 Theano 类似，我们将没有实际值的变量定义为占位符：

```python
x_placeholder = tf.placeholder("float", [None, 784])
label_placeholder = tf.placeholder("float", [None, 10])
```

这里，784 是输入层的单元数，10 是输出层的单元数。我们这样做是因为占位符中的值会随着小批量数据的变化而变化。一旦定义了占位符，就可以继续构建模型并进行训练。这里，我们在 `inference()` 中使用 `softmax` 函数设置非线性激活：

```python
def inference(x_placeholder):

    W = tf.Variable(tf.zeros([784, 10]))
    b = tf.Variable(tf.zeros([10]))

    y = tf.nn.softmax(tf.matmul(x_placeholder, W) + b)

    return y
```

这里，W 和 b 是模型的参数。损失函数，即 `cross_entropy` 函数，在 `loss()` 中定义如下：

```python
def loss(y, label_placeholder):

    cross_entropy = - tf.reduce_sum(label_placeholder * tf.log(y))

    return cross_entropy
```

定义了 `inference()` 和 `loss()` 之后，我们可以通过编写以下代码来训练模型：

```python
def training(loss):
    train_step = tf.train.GradientDescentOptimizer(0.01).minimize(loss)

    return train_step
```

GradientDescentOptimizer() 应用的是梯度下降算法。但请注意，这种方法只是定义了训练方式，实际训练尚未执行。TensorFlow 还支持 AdagradOptimizer()、MomentumOptimizer() 以及其他主要的优化算法。

前面解释的代码和方法都是用来定义模型的。要执行实际训练，你需要初始化一个 TensorFlow 会话：

```python
init = tf.initialize_all_variables()
sess.run(init)
```

然后我们使用小批量数据训练模型。一个小批量中的所有数据都存储在 `feed_dict` 中，并在 `sess.run()` 中使用：

```python
for i in range(1000):
    batch_xs, batch_ys = mnist.train.next_batch(100)
    feed_dict = {x_placeholder: batch_xs, label_placeholder: batch_ys}

    sess.run(train_step, feed_dict=feed_dict)
```

模型训练就是这样。非常简单，不是吗？你可以通过编写以下代码来显示结果：

```python
def res(y, label_placeholder, feed_dict):
    correct_prediction = tf.equal(
        tf.argmax(y, 1), tf.argmax(label_placeholder, 1)
    )

    accuracy = tf.reduce_mean(
        tf.cast(correct_prediction, "float")
    )

    print sess.run(accuracy, feed_dict=feed_dict)
```

TensorFlow 让深度学习的实现变得超级简单，而且非常有用。此外，TensorFlow 还有另一个强大的功能——TensorBoard，用于深度学习可视化。只需在前面的代码片段中添加几行代码，就可以使用这个有用的功能。

我们先来看看模型是如何可视化的。代码位于 `DLW/src/resources/tensorflow/1_3_mnist_TensorBoard.py`，直接运行即可。运行程序后，输入以下命令：

```bash
$ tensorboard --logdir=<ABSOLUTE_PATH>/data
```

这里的 `<ABSOLUTE_PATH>` 是程序的绝对路径。然后，如果你在浏览器中访问 `http://localhost:6006/`，就可以看到如下页面：

![](img/9315e45972ec0fbaf15f9144035bca79_231_0.png)

这里显示了 `cross_entropy` 值的变化过程。另外，当你点击页眉菜单中的 **GRAPH** 时，你会看到模型的可视化图：

![](img/9315e45972ec0fbaf15f9144035bca79_231_1.png)

当你在页面上点击 **inference** 时，可以看到模型结构：

![](img/9315e45972ec0fbaf15f9144035bca79_232_0.png)

现在让我们看看代码内部。要启用可视化，你需要用作用域 `with tf.Graph().as_default()` 包裹整个区域。添加这个作用域后，作用域内声明的所有变量都会显示在图中。可以通过添加名称标签来设置显示名称，如下所示：

```python
x_placeholder = tf.placeholder("float", [None, 784], name="input")
label_placeholder = tf.placeholder("float", [None, 10], name="label")
```

定义其他作用域会在图中创建节点，而这正是 `inference()`、`loss()` 和 `training()` 的定义凸显其真正价值的地方。你可以在定义各自作用域的同时不损失任何可读性：

```python
def inference(x_placeholder):
    with tf.name_scope('inference') as scope:
        W = tf.Variable(tf.zeros([784, 10]), name="W")
        b = tf.Variable(tf.zeros([10]), name="b")

        y = tf.nn.softmax(tf.matmul(x_placeholder, W) + b)

    return y

def loss(y, label_placeholder):
    with tf.name_scope('loss') as scope:
        cross_entropy = - tf.reduce_sum(label_placeholder * tf.log(y))

        tf.scalar_summary("Cross Entropy", cross_entropy)

    return cross_entropy

def training(loss):
    with tf.name_scope('training') as scope:
        train_step = tf.train.GradientDescentOptimizer(0.01).minimize(loss)

    return train_step
```

loss() 中的 tf.scalar_summary() 会让变量显示在 EVENTS 菜单中。要实现可视化，我们需要以下代码：

```python
summary_step = tf.merge_all_summaries()
init = tf.initialize_all_variables()

summary_writer = tf.train.SummaryWriter('data', graph_def=sess.graph_def)
```

然后可以通过以下代码添加变量的变化过程：

```python
summary = sess.run(summary_step, feed_dict=feed_dict)
summary_writer.add_summary(summary, i)
```

当使用更复杂的模型时，这一可视化功能会更有用。

### Caffe

Caffe 是一个以速度快而闻名的库。官方项目页面是 http://caffe.berkeleyvision.org/，GitHub 页面是 https://github.com/BVLC/caffe。与 TensorFlow 类似，Caffe 主要用 C++ 开发，但它提供了 Python 和 MATLAB API。此外，Caffe 的独特之处在于，你不需要任何编程经验，只需编写配置或协议文件，即 `.prototxt` 文件，就能进行深度学习实验和研究。这里我们重点介绍基于协议的方法。

Caffe 是一个功能非常强大的库，可以快速构建、训练和测试模型；但是，要从中获得诸多好处，安装这个库会有点困难。从 http://caffe.berkeleyvision.org/installation.html 的安装指南可以看出，你需要预先安装以下内容：

- CUDA
- BLAS（ATLAS、MKL 或 OpenBLAS）
- OpenCV
- Boost
- 其他：snappy、leveldb、gflags、glog、szip、lmdb、protobuf 和 hdf5

然后，从 GitHub 页面克隆仓库，并根据 `Makefile.config.example` 创建 `Makefile.config` 文件。运行 make 命令前，你可能需要预先安装 Anaconda（一个 Python 发行版）。你可以从 https://www.continuum.io/downloads 下载它。运行 `make`、`make test` 和 `make runtest` 命令（你可能希望通过 `-jN` 选项来加速，例如 `make -j4` 或 `make -j8`）并通过测试后，你就会领略到 Caffe 的强大。下面来看一个例子。进入 `$CAFFE_ROOT`（你克隆仓库的路径），然后输入以下命令：

```bash
$ ./data/mnist/get_mnist.sh
$ ./examples/mnist/train_lenet.sh
```

这就是使用 CNN 解决标准 MNIST 分类问题所需的全部内容。那么，这里发生了什么？如果你看一下 `train_lenet.sh`，就会看到以下内容：

```sh
#!/usr/bin/env sh

./build/tools/caffe train --solver=examples/mnist/lenet_solver.prototxt
```

