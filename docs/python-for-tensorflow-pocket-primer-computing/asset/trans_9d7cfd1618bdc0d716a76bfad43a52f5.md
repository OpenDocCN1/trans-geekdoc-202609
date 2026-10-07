

# TensorFlow 的 batch() 运算符 (2)

列表 6.12 显示了 `tf-batch2.py` 的内容，它说明了如何在 TensorFlow 中结合单次迭代器（one-shot iterator）使用 `batch()` 运算符。

列表 6.12: tf-batch2.py

```
import tensorflow as tf
import numpy as np

x = np.arange(0, 33)
ds = tf.data.Dataset.from_tensor_slices(x).batch(3)
iterator = ds.make_one_shot_iterator()
next_element = iterator.get_next()

with tf.Session() as sess:
    for i in range(11):
        val = sess.run(next_element)
        print(val)
```

列表 6.12 将变量 `x` 初始化为包含从 0 到 32（包含）整数的 NumPy 数组。接下来，变量 `ds` 初始化为根据变量 `x` 的内容创建的 TF Dataset。注意如何通过在定义 `ds` 时“附上” `batch(3)` 运算符来实现方法链（method chaining）。

接下来的代码段将变量 `iterator` 定义为“单次”迭代器，随后是变量 `next_element`，它填充了 `ds` 中的第一个整数（整数 0）。

列表 6.12 的最后部分包含一个执行 11 次的循环，在每次迭代中，循环都会打印出连续整数的“三元组”，从三元组 `[0 1 2]` 开始。运行列表 6.12 中的代码的输出如下：

```
[0 1 2]
[0 1 2]
[3 4 5]
[6 7 8]
[ 9 10 11]
[12 13 14]
[15 16 17]
[18 19 20]
[21 22 23]
[24 25 26]
[27 28 29]
[30 31 32]
```

![](img/55c2af1cab44d6186a8b2008b93f459f_294_0.png)

光盘包含了 `tf-batch3.py`、`tf-batch4.py` 和 `tf-batch5.py`，它们展示了上述代码示例的变体。通过更改硬编码的值来实验代码，看看你是否能正确预测输出。

# TensorFlow 的 map() 运算符 (1)

列表 6.13 显示了 `tf-map.py` 的内容，它说明了如何在 TensorFlow 中结合单次迭代器使用 `map()` 运算符。

# 列表 6.13: tf-map.py

```
import tensorflow as tf
import numpy as np

# 一个简单的 Numpy array
x = np.array([[1],[2],[3],[4]])

# 从 numpy 数组创建数据集
dataset = tf.data.Dataset.from_tensor_slices(x)

# 使用 lambda 表达式将每个值翻倍
dataset = dataset.map(lambda x: x*2)

# 定义迭代器
iter = dataset.make_one_shot_iterator()
el = iter.next()

with tf.Session() as sess:
    for _ in range(len(x)):
        print("value:", sess.run(el))
```

列表 6.13 将变量 `x` 初始化为包含四个元素的 NumPy 数组，其中每个元素都是一个包含数字 1、2、3 和 4 的 1x1 数组。接下来，变量 `dataset` 初始化为根据变量 `x` 的内容创建的 TF Dataset。注意 `dataset.map()` 随后定义了一个 lambda 表达式，将每个输入值翻倍（在本例中，这些值是从 1 到 4 的整数）。

接下来的代码段将变量 `iter` 定义为“单次”迭代器，随后是变量 `el`，它填充了变量 `dataset` 中的第一个元素。

列表 6.13 的最后部分遍历 `dataset` 的元素并显示它们的值。运行列表 6.13 中的代码的输出如下：

```
('value:', array([2]))
('value:', array([4]))
('value:', array([6]))
('value:', array([8]))
```

# TensorFlow 的 map() 运算符 (2)

列表 6.14 显示了 `tf-map2.py` 的内容，它说明了如何在 TensorFlow 中结合单次迭代器调用三次 `map()` 运算符。

# 列表 6.14: tf-map2.py

```
import tensorflow as tf
import numpy as np

# 一个简单的 Numpy array
x = np.array([[1],[2],[3],[4]])

# 从一个 Numpy 数组创建数据集
dataset = tf.data.Dataset.from_tensor_slices(x)

# 方法 #1：较长的方法
# 使用 lambda 表达式将每个值翻倍
dataset = dataset.map(lambda x: x*2)
# 使用 lambda 表达式给每个值加 1
dataset = dataset.map(lambda x: x+1)
# 使用 lambda 表达式将每个值立方
dataset = dataset.map(lambda x: x**3)

# 方法 #2：更简的方法
dataset = dataset.map(lambda x: (x*2+1)**3)

# 定义迭代器
iter = dataset.make_one_shot_iterator()
el = iter.next()

with tf.Session() as sess:
    for _ in range(len(x)):
        print("value:", sess.run(el))
```

