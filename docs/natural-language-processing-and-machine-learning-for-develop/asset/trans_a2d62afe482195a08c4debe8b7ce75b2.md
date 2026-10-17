
import tensorflow 为 tf model = tf.keras.models.Sequential([ tf.keras.layers.Dense(512, activation=tf.nn.relu), ]) 

我们有三个更多的要讨论的项目，从编译步骤开始。Keras 提供 compile() API 供此步骤，示例如下：

model.compile(optimizer='adam', loss='sparse_categorical_crossentropy', metrics=['accuracy'])

接下来我们需要指定训练步骤，Keras 提供 fit() API（可以看出它不叫 train()），示例如下：

model.fit(x_train, y_train, epochs=5)

最后一步是通过 predict() API 进行预测，示例如下：

pred = model.predict(x)

请注意，evaluate() 方法用于评估已训练的模型，其输出为准确率或损失。然而，predict() 方法对输入数据进行预测。

[Listing D.1](#appD.xhtml#listD.1) 显示 tf2_basic_keras.py 的内容，该文件将前面步骤中的代码块合并为一个代码示例。

***LISTING D.1: tf2_basic_keras.py***

import tensorflow 为 tf # NOTE: 我们需要训练数据和测试数据 model = tf.keras.models.Sequential([ tf.keras.layers.Dense(1, activation=tf.nn.relu), ]) model.compile(optimizer='adam', loss='sparse_categorical_crossentropy', metrics=['accuracy']) model.fit(x_train, y_train, epochs=5) model.evaluate(x_test, y_test)

[Listing D.1](#appD.xhtml#listD.1) 并无新代码，我们已基本略过一些术语，如优化器（用于与损失函数配合使用的算法）、损失（损失函数的类型）以及指标（衡量模型效能的指标）。

对这些细节的详尽解释无法在几段文字中压缩（遗憾的是），但好消息是，您可以在网络上找到大量详细的博客文章来讨论这些概念。

## **Keras 与线性回归**

本节包含一个简单的示例，演示如何使用 Keras 创建模型来解决线性回归任务：给定一个正数表示意面的千克数，预测其对应的价格。[Listing D.2](#appD.xhtml#listD.2) 显示 pasta.csv 的内容，[Listing D.3](#appD.xhtml#listD.3) 显示 keras_pasta.py 的内容，该文件执行此任务。

***LISTING D.2: pasta.csv***

weight,price 5,30 10,45 15,70 20,80 25,105 30,120 35,130 40,140 50,150 

***LISTING D.3: keras_pasta.py***

import tensorflow 为 tf import numpy as np import pandas as pd import matplotlib.pyplot as plt # 意面每千克的价格 df = pd.read_csv("pasta.csv") weight = df['weight'] price = df['price'] model = tf.keras.models.Sequential([ tf.keras.layers.Dense(units=1,input_shape=[1]) ]) # MSE 损失函数和 Adam 优化器 model.compile(loss='mean_squared_error', optimizer=tf.keras.optimizers.Adam(0.1)) # 训练模型 history = model.fit(weight, price, epochs=100, verbose=False) # 绘制 # 时代与损失值的图 # xlabel('Number of Epochs') plt.ylabel("Loss Values") plt.plot(history.history['loss']) plt.show() print("Cost for 11kg:",model.predict([11.0])) print("Cost for 45kg:",model.predict([45.0]))

[Listing D.3](#appD.xhtml#listD.3) 使用 Pandas 数据框 df 加载 pasta.csv 的内容，然后分别用 df 的第一列和第二列初始化 weight 和 price 变量。

随后，[Listing D.3](#appD.xhtml#listD.3) 定义了一个包含单个 Dense 层的 Keras 模型，该模型随后被编译、训练，并绘制一个图表，显示“时代数”在横轴、对应的损失函数值在纵轴。运行 [Listing D.3](#appD.xhtml#listD.3) 的代码后，将看到以下输出：

Cost for 11kg: [[41.727108]] Cost for 45kg: [[159.02121]]

图 Figure D.1 显示训练过程中的时代数与损失值的关系。

![Figure D.1. ¶ A Graph of Epochs versus Loss.](images/figD.1.jpg)

Figure D.1. ¶ A Graph of Epochs versus Loss.

##**Keras、MLP 与 MNIST**

本节包含一个简单的示例，演示如何使用 Keras 创建 MLP 神经网络，并使用 MNIST 数据集进行训练。[Listing D.4](#appD.xhtml#listD.4) 显示 keras_mlp_mnist.py 的内容，该文件执行此任务。

***LISTING D.4: keras_mlp_mnist.py***

import tensorflow 为 tf import numpy as np # 实例化 MNIST 并加载数据：mnist = tf.keras.datasets.mnist (x_train, y_train), (x_test, y_test) = mnist.load_data() # 对所有标签进行 one-hot 编码，生成 1x10 向量以与最终层比较：y_train = tf.keras.utils.to_categorical(y_train) y_test = tf.keras.utils.to_categorical(y_test) image_size = x_train.shape[1] input_size = image_size * image_size # 对 28x28 图像进行 reshape 与归一化：x_train = np.reshape(x_train, [-1, input_size]) x_train = x_train.astype('float32') / 255 x_test = np.reshape(x_test, [-1, input_size]) x_test = x_test.astype('float32') / 255 # 初始化一些超参数：batch_size = 128 hidden_units = 128 dropout_ratea = 0.20 # 定义一个 Keras 模型：model = tf.keras.models.Sequential() model.add(tf.keras.layers.Dense(hidden_units, input_dim=input_size)) model.add(tf.keras.layers.Activation('relu')) model.add(tf.keras.layers.Dropout(dropout_rate)) model.add(tf.keras.layers.Dense(hidden_units)) model.add(tf.keras.layers.Activation('relu')) model.add(tf.keras.layers.Dense(10)) model.add(tf.keras.layers.Activation('softmax')) model.summary() model.compile(loss='categorical_crossentropy', optimizer='adam', metrics=['accuracy']) # 在训练数据上训练网络：model.fit(x_train, y_train, epochs=10, batch_size=batch_size) # 计算并显示测试集准确率：loss, acc = model.evaluate(x_test, y_test, batch_size=batch_size) print("\\nTest accuracy: %.1f%%" % (100.0 * acc))

[Listing D.4](#appD.xhtml#listD.4) 包含常规的 import 语句，然后将 mnist 变量指向 MNIST 数据集。随后，代码加载训练集和测试集，并使用“one-hot”编码将标签转换为数值向量。

接着，初始化了一些超参数，并定义了一个包含三个 Dense 层、relu 激活函数的 Keras 模型。该模型随后被编译、训练，并在测试集上计算准确率并打印出来。运行 [Listing D.4](#appD.xhtml#listD.4) 的代码后，将看到以下输出：

