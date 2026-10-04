

`ch7/tuned_learning.py` 模块中的代码执行与本章前面介绍的 `ch7/deep_learning.py` 模块相同的 MNIST 分类任务。不同之处在于它对神经网络进行了调优以提高准确率和性能。它还通过调用 `tf.contrib.layers.fully_connected` 而不是 `tf.add` 和 `tf.matmul` 来创建全连接层。 [代码清单 7-2](#12_9788126592555-ch07.xhtml#c07-fea-0002) 展示了该代码。

### [代码清单 7-2](#12_9788126592555-ch07.xhtml#rc07-fea-0002) 带调优的深度学习

```python
# Read MNIST data
dataset = learn.datasets.mnist.read_data_sets('MNIST-data', one_hot=True)

# Placeholders for MNIST images
img_holder = tf.placeholder(tf.float32, [None, 784])
lbl_holder = tf.placeholder(tf.float32, [None, 10])
train = tf.placeholder(tf.bool)

# Layer settings
hid_nodes = 200
out_nodes = 10
keep_prob = 0.5

# Create layers
with tf.contrib.framework.arg_scope(
 [fully_connected],
 normalizer_fn=tf.contrib.layers.batch_norm,
 normalizer_params={'is_training': train}):
 layer1 = fully_connected(img_holder, hid_nodes, scope='layer1')
 layer1_drop = tf.layers.dropout(layer1, keep_prob, training=train)
 layer2 = fully_connected(layer1_drop, hid_nodes, scope='layer2')
 layer2_drop = tf.layers.dropout(layer2, keep_prob, training=train)
 layer3 = fully_connected(layer2_drop, hid_nodes, scope='layer3')
 layer3_drop = tf.layers.dropout(layer3, keep_prob, training=train)
 out_layer = fully_connected(layer3_drop, out_nodes,
 activation_fn=None, scope='layer4')

# Compute loss
loss = tf.reduce_mean(
 tf.nn.softmax_cross_entropy_with_logits(
 logits=out_layer, labels=lbl_holder))

# Create optimizer
learning_rate = 0.01
num_epochs = 15
batch_size = 100
num_batches = int(dataset.train.num_examples/batch_size)
optimizer = tf.train.AdamOptimizer(learning_rate).minimize(loss)

# Initialize variables
init = tf.global_variables_initializer()

# Launch session
with tf.Session() as sess:
 sess.run(init)

 # Loop over epochs
 for epoch in range(num_epochs):

 # Loop over batches
 for batch in range(num_batches):
 img_batch, lbl_batch = dataset.train.next_batch(batch_size)
 sess.run(optimizer, feed_dict={img_holder: img_batch,
 lbl_holder: lbl_batch, train: True})

 # Determine success rate
 prediction = tf.equal(tf.argmax(out_layer, 1), tf.argmax(lbl_holder, 1))
 success = tf.reduce_mean(tf.cast(prediction, tf.float32))
 print('Success rate: ', sess.run(success,
 feed_dict={img_holder: dataset.test.images,
 lbl_holder: dataset.test.labels, train: False}))
```

该模块采用三种方法来调优其多层神经网络：

* 它将每个全连接层的输出发送到 dropout 层。模块将 `keep_prob` 设置为 0.5，因此 dropout 层将其一半的输入设为 0。
* 模块调用 `tf.contrib.layers.batch_norm` 对隐藏层执行批归一化。
* 默认情况下，`tf.contrib.layers.fully_connected` 使用 Glorot 方法初始化网络的权重。

每个隐藏层有 200 个节点，输出层有 10 个节点。在创建层之前，模块通过调用 `tf.contrib.framework.arg_scope` 定义了一个参数作用域。 `arg_scope` 接受一个包含函数（`fully_connected`）和要插入到函数内部的参数的列表。

每次调用 `fully_connected` 时，`scope` 参数都被设置为不同的值。创建此作用域会更改层变量的名称。应用程序可以通过调用 `tf.get_collection` 来检索这些变量。

前三次 `fully_connected` 调用未设置 `activation_fn`，因此层的节点使用默认的 ReLU 激活函数计算其输出。最后一次 `fully_connected` 调用将 `activation_fn` 设置为 `None`，因此输出层的每个节点返回其输入的加权和。 `tf.nn.softmax_cross_entropy_with_logits` 函数接受这些加权和并从十个类别中选择一个。

# 第 8 章

# 使用卷积神经网络 (CNNs) 对图像进行分类

本章内容

![check](images/check.png)**探索图像滤波和卷积**

![check](images/check.png)**了解卷积神经网络 (CNN)**

![check](images/check.png)**介绍 CIFAR-10 数据集**

![check](images/check.png)**介绍 TensorFlow 的图像操作**

本章解释了如何使用 TensorFlow 和卷积神经网络 (CNNs) 编码图像识别应用程序。这些应用程序与 [第 7 章](#12_9788126592555-ch07.xhtml) 中的 vanilla 神经网络类似，但它们包含专门用于图像分类的层。

## 滤波图像

如果你使用过 Adobe Photoshop 等图像编辑应用程序，你可能熟悉滤波工具，它们会为图像添加模糊、锐化或浮雕等效果。从数学上讲，这些工具使用一种称为 *卷积* 的过程执行其操作。该过程在图像识别中起着关键作用，虽然不必掌握所有细节，但了解一般过程是很有帮助的。

### 卷积

图像卷积用二维点积的结果替换图像的每个像素。此点积接受两个矩阵并返回其对应元素乘积之和。

例如，假设 A 和 B 是两个 3-x-3 矩阵，其元素如下所示：

![images](images/eq08001.png)<m:math xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mrow><m:mi>A</m:mi><m:mo>=</m:mo><m:mrow><m:mo>|</m:mo><m:mrow><m:mtable><m:mtr><m:mtd><m:mn>1</m:mn></m:mtd><m:mtd><m:mn>2</m:mn></m:mtd><m:mtd><m:mn>3</m:mn></m:mtd></m:mtr><m:mtr><m:mtd><m:mn>4</m:mn></m:mtd><m:mtd><m:mn>5</m:mn></m:mtd><m:mtd><m:mn>6</m:mn></m:mtd></m:mtr><m:mtr><m:mtd><m:mn>7</m:mn></m:mtd><m:mtd><m:mn>8</m:mn></m:mtd><m:mtd><m:mn>9</m:mn></m:mtd></m:mtr></m:mtable></m:mrow><m:mo>|</m:mo></m:mrow><m:mi mathvariant="normal">&#160;&#160;&#160;&#160;</m:mi><m:mi>B</m:mi><m:mo>=</m:mo><m:mrow><m:mo>|</m:mo><m:mrow><m:mtable><m:mtr><m:mtd><m:mrow><m:mo>&#45;</m:mo><m:mn>10</m:mn></m:mrow></m:mtd><m:mtd><m:mrow><m:mo>&#45;</m:mo><m:mn>9</m:mn></m:mrow></m:mtd><m:mtd><m:mrow><m:mo>&#45;</m:mo><m:mn>8</m:mn></m:mrow></m:mtd></m:mtr><m:mtr><m:mtd><m:mrow><m:mo>&#45;</m:mo><m:mn>7</m:mn></m:mrow></m:mtd><m:mtd><m:mrow><m:mo>&#45;</m:mo><m:mn>6</m:mn></m:mrow></m:mtd><m:mtd><m:mrow><m:mo>&#45;</m:mo><m:mn>5</m:mn></m:mrow></m:mtd></m:mtr><m:mtr><m:mtd><m:mrow><m:mo>&#45;</m:mo><m:mn>4</m:mn></m:mrow></m:mtd><m:mtd><m:mrow><m:mo>&#45;</m:mo><m:mn>3</m:mn></m:mrow></m:mtd><m:mtd><m:mrow><m:mo>&#45;</m:mo><m:mn>2</m:mn></m:mrow></m:mtd></m:mtr></m:mtable></m:mrow><m:mo>|</m:mo></m:mrow></m:mrow></m:math>

你可以通过将对应值对相乘并将结果相加来计算 A 和 B 的二维点积：

