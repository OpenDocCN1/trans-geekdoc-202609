

# 使用 TensorFlow 进行深度学习

TensorBoard 使用浏览器来显示代码的可视化。上面的图表示所用模型的不同部分。`Const` 和 `const_1` 分别代表 `a` 和 `b`，节点代表 `c`。

# 实现

使用 TensorFlow 编写简单的 python hello 代码。你可以使用 Jupyter notebook、Spyder、PyCharm 框架来编写代码，也可以在 cmd 中打开 python 解释器。

图 29。

![](img/c5cbbc72cd5e7b9be32079eac36d685c_130_0.png)

上述代码段的输出是 `b'hello world!'`，其中 `b` 代表字节字符串而非 Unicode 字符。你可以使用 `Print(sess.run(hello).decode())` 来移除输出中的 `b`。

# TensorFlow 提供的数据集

在 TensorFlow 中，有 29 个著名的数据集，例如 MNIST、大型电影评论数据集（Large Movie Reviews Dataset）、10 亿词语言模型基准（1 Billion Word Language Model Benchmark）和街景门牌号（Street View House Numbers）等（介绍 TensorFlow Datasets, 2019）。

你可以在给定链接中查看 TensorFlow 不同类别下可用数据集的详细说明：

https://www.tensorflow.org/datasets/catalog/overview

你可以使用以下命令安装所有数据集：

图 30。

```
Anaconda Prompt - python
(tensorflow_cpu) C:\Users\sanwarul>pip install tensorflow-datasets
```

# 可用数据集列表的命令

安装数据集后，导入 `tensorflow-datasets` 为 `tfds`

图 31。

```
Anaconda Prompt - python
>>> import tensorflow_datasets as tfds
```

导入数据集后，你可以使用 `tfds.list_builders` 检查可用数据集列表。

图 32。

```
tfds.list_builders(
['abstract_reasoning', 'afjw2k3d', 'amazon_us_reviews', 'bair_robot_pushing_small', 'bigearthent', 'binarized_mnist', 'binary_digits', 'catech101', 'caltech3_birds2010', 'caltech3_birds2017', 'cat22', 'coco', 'coco_capt', 'coco2012', 'coco2014', 'coco2017', 'colobrio101', 'colorext_mnist', 'color_histology', 'colovectal_histology_layer', 'curated_breast_image_dc', 'cycle_gan', 'deep_weeds', 'definitive_pronoun_recognition', 'digits', 'fashion_mnist', 'euro100', 'food_mnist', 'food101', 'food102', 'gap', 'groove', 'grooves', 'horses', 'house_classification', 'image_classification', 'image_net', 'image_net_v1', 'images_gold', 'inception_mnist', 'dumper_mnist', 'euristot', 'fashion_mnist', 'floors', 'flowers', 'lmc_12b', 'lisin', 'lsun', 'mnist', 'mnist_corrupted', 'moving_mnist', 'mnist_multi', 'nys', 'omiglot', 'open_images', 'oxford_flowers102', 'pcal_mnist', 'pura_leaf', 'patch_catmylon', 'pet_finder', 'quickdraw_sketch', 'resisccd_4', 'cele', 'standard_mnist', 'standard_online_products', 'starcraft_video', 'sun37', 'super_gle', 'svhn_cropped', 'tdlr_translate', 'tdlr_multi_translate', 'tdlr_word_translate', 'translator', 'w13_translate', 'w15_translate', 'w16_translate', 'w17_translate', 'w18_translate', 'w19_translate', 'wt2c_translate', 'wt_translate', 'xnl11'])
```

# 使用 MNIST 数据集识别手写数字的深度学习实际实现

在这个 Python 深度学习实际实现中，作者使用了 MNIST 数据集（LeCun, Cortes & Burges, 1998）。该数据集由大小为 28*28 像素的手写数字图像组成，如图 33 所示。

图 33. MNIST数据集 (LeCun, Cortes & Burges, 1998)

![](img/c5cbbc72cd5e7b9be32079eac36d685c_132_0.png)

#  1 ：导入数据集

首先，导入 TensorFlow 库，然后添加代码导入 MNIST 数据集并将图像数据存储在 `mnist` 变量中。这里使用独热编码（one-hot-encoding）来描述标签。它使用二值化向量来表示数值或类别值。该向量包含十个值，对应从 0-9 的每个可能的数字。为了表示任何特定数字，向量在该索引处的值为 1，其余部分为 0。例如，数字 4 由向量 `[0,0,0,0,1,0,0,0,0,0]` 表示。现在，28*28 像素的图像被转换为大小为 784 像素的 1D 向量。每个 784 像素都包含 0 到 255 之间的值，因为我们使用的是灰度图像。

在黑白图像中，255 代表黑色像素，白色由 0 表示。

```python
import tensorflow as tf
import tensorflow_datasets as tfds

(train, test) = tfds.load('mnist', split=['train[:90%]', 'train[90%:]'])

x_train, y_train = train['image'], train['label']
x_test, y_test = test['image'], test['label']

x_train = tf.reshape(x_train, [-1, 784])
x_test = tf.reshape(x_test, [-1, 784])

y_train = tf.one_hot(y_train, 10)
y_test = tf.one_hot(y_test, 10)
```

图 34。

# 步骤 2：准备数据

导入数据集后，使用 `tfds.list_builders` 检查可用数据集。

图 35。

```python
import tensorflow_datasets as tfds

(train, test) = tfds.load('mnist', split=['train[:90%]', 'train[90%:]'])

x_train, y_train = train['image'], train['label']
x_test, y_test = test['image'], test['label']

x_train = tf.reshape(x_train, [-1, 784])
x_test = tf.reshape(x_test, [-1, 784])

y_train = tf.one_hot(y_train, 10)
y_test = tf.one_hot(y_test, 10)
```

# 步骤 3：构建模型

```python
import tensorflow as tf

w1 = tf.get_variable("w1", [784, 256], initializer=tf.random_normal_initializer())
b1 = tf.get_variable("b1", [256], initializer=tf.zeros)
w2 = tf.get_variable("w2", [256, 128], initializer=tf.random_normal_initializer())
b2 = tf.get_variable("b2", [128], initializer=tf.zeros)
w3 = tf.get_variable("w3", [128, 10], initializer=tf.random_normal_initializer())
b3 = tf.get_variable("b3", [10], initializer=tf.zeros)

h1 = tf.nn.relu(tf.matmul(x_train, w1) + b1)
h2 = tf.nn.relu(tf.matmul(h1, w2) + b2)
logits = tf.matmul(h2, w3) + b3
```

图 36。

```python
loss = tf.reduce_mean(tf.nn.softmax_cross_entropy_with_logits(labels=y_train, logits=logits))
train_step = tf.train.AdamOptimizer(1e-4).minimize(loss)
```

图 37。

```python
with tf.Session() as sess:
    sess.run(tf.global_variables_initializer())
    for i in range(1000):
        loss_val = sess.run(train_step)
        if i % 100 == 0:
            print(f"step {i}, loss: {loss_val}")
```

# 步骤 4：评估模型

```python
predictions = sess.run(tf.argmax(logits, axis=1), feed_dict={x_test: x_test})
accuracy = tf.reduce_mean(tf.cast(tf.equal(predictions, tf.argmax(y_test, axis=1)), tf.float32))
print(sess.run(accuracy, feed_dict={x_test: x_test}))
```

