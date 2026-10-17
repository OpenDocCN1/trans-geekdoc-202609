
```python
LISTING 6.22: tf-zip-batch.py

import tensorflow as tf
import numpy as np

ds1 = tf.data.Dataset.range(100)
ds2 = tf.data.Dataset.range(0, -100, -1)
ds3 = tf.data.Dataset.zip((ds1, ds2))
ds4 = ds3.batch(4)
```

```python
iterator = ds4.make_one_shot_iterator()
next_element = iterator.get_next()

with tf.Session() as sess:
    print(sess.run(next_element))
    print(sess.run(next_element))
    print(sess.run(next_element))
```

列表 6.22 初始化了变量 `ds1`、`ds2`、`ds3` 和 `ds4`，这些 TF 数据集是连续创建的，其中从 `ds1` 开始，`ds1` 包含 0 到 99 之间的整数。

列表 6.22 的下部分将变量 `iterator` 定义为“单次（one-shot）”迭代器，其后是变量 `next_element`，该变量被填充为数据集中的第一个元素。列表 6.22 的最后部分打印了三行“批处理（batched）”输出，如下：

```
array([0, 1, 2, 3]), array([ 0, -1, -2, -3])
array([4, 5, 6, 7]), array([-4, -5, -6, -7])
array([ 8, 9, 10, 11]), array([ -8, -9, -10, -11])
```

# 组合 TF ZIP() 和 TAKE() 运算符

列表 6.23 显示了 `tf-zip-take.py` 的内容，它展示了如何在 TensorFlow 中组合 `zip()` 和 `take()` 运算符。

## 列表 6.23: tf-zip-take.py

```python
import tensorflow as tf
import numpy as np
x = np.arange(0, 10)
y = np.arange(1, 11)

# 从数组创建数据集对象
dx = tf.data.Dataset.from_tensor_slices(x)
dy = tf.data.Dataset.from_tensor_slices(y)

# 将两个数据集合并
dcomb = tf.data.Dataset.zip((dx, dy)).batch(3)
iterator = dcomb.make_initializable_iterator()

# 提取一个元素
next_element = iterator.get_next()

with tf.Session() as sess:
    sess.run(iterator.initializer)
    for i in range(15):
        val = sess.run(next_element)
        print(val)
        if (i + 1) % (10 // 3) == 0 and i > 0:
            sess.run(iterator.initializer)
```

列表 6.23 将变量 `x` 和 `y` 分别初始化为 0 到 11 和 0 到 12 的整数范围。接下来，变量 `dx` 和 `dy` 初始化为 TF 数据集，这些数据集分别由变量 `x` 和 `y` 的内容创建。

下一个代码段将变量 `dcomb` 定义为 TF 数据集，它通过 `zip()` 运算符以配对的方式组合 `dx` 和 `dy` 中的元素，如下：

```python
dcomb = tf.data.Dataset.zip((dx, dy)).batch(3)
```

注意通过在定义 `dcomb` 时作为其一部分“附加” `batch(3)` 运算符是如何实现链式调用的。

下一个代码段将变量 `iterator` 定义为“可初始化的（initializable）”迭代器，其后是变量 `next_element`，该变量被填充为 `dx` 中的第一个整数（即整数 0）。

列表 6.23 的最后部分包含一个执行 15 次的循环，在每次迭代中，循环都会打印变量 `iterator` 的当前内容。每行输出由两个数字“块”组成，每个块包含三个连续的整数。运行列表 6.23 中的代码的输出如下：

```
array([0, 1, 2]), array([1, 2, 3])
array([3, 4, 5]), array([4, 5, 6])
array([6, 7, 8]), array([7, 8, 9])
array([0, 1, 2]), array([1, 2, 3])
array([3, 4, 5]), array([4, 5, 6])
array([6, 7, 8]), array([7, 8, 9])
array([0, 1, 2]), array([1, 2, 3])
array([3, 4, 5]), array([4, 5, 6])
array([6, 7, 8]), array([7, 8, 9])
array([0, 1, 2]), array([1, 2, 3])
array([3, 4, 5]), array([4, 5, 6])
array([6, 7, 8]), array([7, 8, 9])
```

# TF 数据集与随机数 (1)

列表 6.24 显示了 `tf-random-one-shot.py` 的内容，它展示了如何创建一个带有随机数的 TF 数据集。

## 列表 6.24: tf-random-one-shot.py

```python
import tensorflow as tf
import numpy as np
x = np.random.sample((100,2))

# 从 numpy 数组创建数据集
dataset = tf.data.Dataset.from_tensor_slices(x)

iter = dataset.make_one_shot_iterator()
el = iter.get_next()

with tf.Session() as sess:
    print(sess.run(el))
```

列表 6.24 将变量 `x` 初始化为包含 100 行 2 列生成数字的 NumPy 数组。接下来，变量 `dataset` 初始化为由变量 `x` 的内容创建的 TF 数据集。

下一个代码段将变量 `iter` 定义为“单次（one-shot）”迭代器，其后是变量 `el`，该变量被填充为数据集中的第一个元素。

列表 6.24 的最后部分打印了第一行转换后的数据，如下：

```
[0.6907335, 0.2112917]
```

# TF 数据集与随机数 (2)

列表 6.25 显示了 `tf-random-one-shot.py` 的内容，它展示了如何创建一个带有随机数的 TF 数据集。（注：此处原文文件名与上文重复均为 `tf-random-one-shot.py`）

## 列表 6.25: tf-random-one-shot.py

```python
import tensorflow as tf
import numpy as np

# 两个带有随机数的 Numpy数组
features = np.random.sample((100,2))
labels = np.random.sample((100,1))
dataset = tf.data.Dataset.from_tensor_slices((features, labels))

iter = dataset.make_one_shot_iterator()
el = iter.get_next()

with tf.Session() as sess:
    print(sess.run(el))
```

列表 6.25 初始化了变量 `features` 和 `labels`，它们分别由一个包含 100 行 2 列随机数字的 NumPy 数组以及一个包含 100 行 1 列生成数字的 NumPy 数组生成。

接下来，变量 `dataset` 初始化为由 `features` 和 `labels` 的内容创建的 TF 数据集。下一个代码段将变量 `iter` 定义为“单次（one-shot）”迭代器，其后是变量 `el`，该变量被填充为数据集中的第一个元素。列表 6.25 的最后部分打印了第一行转换后的数据，如下：

```
[0.47582573, 0.36387
```

# 从 CSV 文件创建 TF 数据集

列表 6.26 显示了 `simple.csv` 的内容，列表 6.27 显示了 `tf-csv-dataset.py` 的内容，它展示了如何从 CSV 文件中的数据创建 TF 数据集。

## 列表 6.26: simple.csv

```
text,sentiment
'a good restaurant', 1
'a poor movie ', 0
'a great dessert', 1
'a plain hamburger', 0
```

## 列表 6.27: tf-csv-dataset.py

```python
import tensorflow as tf
import numpy as np

csv_file = './simple.csv'
dataset = tf.data.experimental.make_csv_dataset(csv_file, batch_size=2)
iter = dataset.make_one_shot_iterator()
next = iter.get_next()

# next 是一个键为列名、值为列数据的字典
print("next:", next)
inputs, labels = next['text'], next['sentiment']

with tf.Session() as sess:
    sess.run([inputs, labels])
    print("inputs:", sess.run([inputs, labels]))
```

# 使用 TF.ESTIMATORS 和 TF.LAYERS (可选)

下面介绍的第一个子节对于具有使用 scikit-learn 等 Python 库处理常用机器学习算法经验的人非常有用。你将看到一组与 Python 机器学习中算法对应的 TensorFlow 类列表，包括用于回归任务的类和用于分类任务的类。

第二个子节包含了与在 TensorFlow 中定义 CNN（卷积神经网络）相关的 TensorFlow 类列表。

如果你是机器学习的新手，该部分目前对你来说价值有限，但你仍然可以了解可用内容以供未来参考。

## 什么是 TF Estimator?

`tf.estimator` 命名空间包含各种类，它们实现了机器学习中提供的各种算法，例如提升树、DNN 分类器、DNN 回归器、线性分类器和线性回归器。

与估计相关的类 `DNNRegressor`、`LinearRegressor` 和 `DNNLinearCombinedRegressor` 用于回归任务，而 `DNNClassifier`、`LinearClassifier` 和 `DNNLinearCombinedClassifier` 用于分类任务。下面列出了更详细的估计器类列表（带有非常简短的描述）：

- `BoostedTreesClassifier`: 针对 TensorFlow 提升树模型的分类器

- `BoostedTreesRegressor`: 针对 TensorFlow 提升树模型的回归器

- `CheckpointSaverHook`: 每隔 N 步或每秒保存一次 checkpoint

- `DNNClassifier`: 用于 TensorFlow DNN 模型的分类器

- `DNNEstimator`: 具有用户指定头部（head）的 TensorFlow DNN 模型的估计器

- `DNNLinearCombinedClassifier`: 用于 TensorFlow 线性与 DNN 联合分类模型的估计器

- `DNNLinearCombinedRegressor`: 用于 TensorFlow 和 DNN 联合回归模型的估计器

- `DNNRegressor`: 用于 TensorFlow DNN 模型的回归器

- `Estimator`: 用于训练和评估 TensorFlow 模型的估计器类

- `LinearClassifier`: 线性分类模型

- `LinearEstimator`: 具有用户指定头部的 TensorFlow 线性模型的估计器

- `LinearRegressor`: 用于 TensorFlow 线性回归问题的估计器

所有的估计类都在 `tf.estimator` 命名空间中，并且所有的估计类都继承自 `tf.estimator.Estimator` 类。请阅读在线文档获取上述类的详细信息，并查看在线教程的相关代码示例。

### TF Estimators 和 tf.data.Dataset（可选）

此节标记为可选，因为你需要使用 TF 2 而不是 TF 1.x 来运行代码。

除了从 NumPy 数组或 Pandas DataFrame 创建数据集外，你还可以从现有数据集创建数据集。例如，列表 6.28 显示了 `tf2-mnist-estimator.py` 的内容，说明了如何从 MNIST 数据集创建 `tf.data.Dataset`。

## 列表 6.28：tf2-mnist-estimator.py

```python
import tensorflow as tf

train, test = tf.keras.datasets.mnist.load_data()
mnist_x, mnist_y = train

mnist_ds = tf.data.Dataset.from_tensor_slices(mnist_x)
print(mnist_ds)

iterator = tf.compat.v1.data.make_one_shot_iterator(mnist_ds)

count = 0
max_count = 4

try:
    while True:
        print("value:",iterator.get_next())
        count += 1
        if(count > max_count):
            break
except tf.errors.OutOfRangeError:
    pass
```

列表 6.28 首先初始化了变量 `train` 和 `test`，它们分别包含训练数据和测试数据。接下来，变量 `mnist_ds` 被初始化为 `tf.data.Dataset` 类的一个实例。变量 `iterator` 被初始化为“单次”（one shot）迭代器，它在 TF 2 中工作是因为使用了定义变量迭代器的 `tf.compat.v1.data` 命名空间。

列表 6.28 的下部分初始化了两个标量变量，随后是一个包含 `while` 循环的 `try/except` 块。`while` 循环内部的代码在迭代器“遍历” `mnist_ds` 中的元素时，打印迭代器变量的当前值。

运行列表 6.30 中代码的输出在这里：

```
<TensorSliceDataset shapes: (28, 28), types: tf.uint8>
value: tf.Tensor(
  [[ 0 0 0 0 0 0 0 0 0 0
    0 0 0 0 0 0 0 0]
  [ 0 0 0 0 0 0 0 0 0 0
    0 0 0 0 0 0 0 0]
  [ 0 0 0 0 0 0 0 0
    0 0 0 0 0 0 0 0]
  [ 0 0 0 0 0 0 0 0
    0 0 0 0 0 0 0 0]
  [ 0 0 0 0 0 0 0 0
    0 0 0 0 0 0 0 0]
  [ 0 0 0 0 0 0 0 0
    0 0 0 0 0 0 0 0]
  [ 0 0 0 0 0 0 0 0
    0 0 0 0 0 0 0 0
    0 0 0 0 0 0 0 0]
  [ 175 26 166 255 242 127 0 0
    0 0 0 0 0 0 30 36 94 154 170 253
    253 253 253 253]
  [ 225 172 253 242 195 64 0 0
    0 0 0 0 0 0 49 238 253 253 253 253
    253 253 253 251]
  [ 93 82 82 56 39 0 0
    0 0 0 0 0 0 18 219 253 253
    198 82 247 247]
  [ 0 0 0 0 0 0 0 0
    // output omitted for brevity
    0 0 0 0 0 0 0 0 0 0 218 252 56 0]
  [ 0 0 0 0 0 0 0 0
    0 0 0 0 0 0 0 0 0 0 96 252 189 42]
  [ 0 0 0 0 0 0 0 0
    0 0 0 0 0 0 0 0 0 0 184 252 170]
  [ 11 0 0 0 0 0 0 0
    0 0 0 0 0 0 0 0 0 0 147 252]
  [ 42 0 0 0 0 0 0 0
    0 0 0 0 0 0 0 0 0 0 0 0 0]
  [ 0 0 0 0 0 0 0 0]], shape=(28,
    28), dtype=uint8)
```

### 什么是 tf.layers?

`tf.layers` 命名空间包含了一系列用于神经网络层的类，包括 DNN（深层连接神经网络）和 CNN（卷积神经网络）。`tf.layers` 命名空间中一些较常见的类列如下：

- `BatchNormalization`: 批次归一化层

- `Conv2D`: 2D 卷积层（例如，图像的空间卷积）

- `Dense`: 全连接层

- `Dropout`: 对输入应用 Dropout

- `Flatten`: 在保留批次轴（轴 0）的同时展平输入张量

- `Layer`: 基础层
