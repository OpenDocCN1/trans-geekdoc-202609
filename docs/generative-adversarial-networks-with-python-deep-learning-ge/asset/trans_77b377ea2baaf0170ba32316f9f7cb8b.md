

## 2.3.2 连接层

模型中的层是成对连接的。这是通过在定义每个新层时指定输入来源来完成的。使用括号或函数式表示法，这样在创建层后，就会指定当前层的输入来自哪个层。让我们通过一个简短的示例来澄清这一点。我们可以像上面一样创建输入层，然后创建一个隐藏层作为 Dense 层，该层仅接收来自输入层的输入。

```
...
visible = Input(shape=(2,))
hidden = Dense(2)(visible)
```

清单 2.19：将隐藏层连接到可见层的示例。

正是在创建 Dense 层后的（可见）层将输入层的输出作为输入连接到 Dense 隐藏层。正是这种成对连接层的方式赋予了函数式 API 其灵活性。例如，你可以看到开始定义临时层图是多么容易。

## 2.3.3 创建模型

在创建完所有模型层并将它们连接在一起后，你必须定义模型。与 Sequential API 一样，模型是你可以总结、拟合、评估并用于进行预测的对象。Keras 提供了一个 Model 类，你可以使用它从创建的层中创建模型。它要求你只需指定输入层和输出层。例如：

```
...
visible = Input(shape=(2,))
hidden = Dense(2)(visible)
model = Model(inputs=visible, outputs=hidden)
```

清单 2.20：使用函数式 API 创建完整模型的示例。

现在我们了解了 Keras 函数式 API 的所有关键部分，让我们通过定义一系列不同的模型来练习并积累一些使用经验。每个示例都可执行，并打印结构并创建计算图的图示。我建议你为自己的模型也这样做，以便清楚地了解自己定义了什么。我希望这些示例能在你将来想要使用函数式 API 定义自己的模型时为你提供模板。

## 2.4 标准网络模型

在开始使用函数式 API 时，查看一些标准神经网络模型的定义是个好主意。在本节中，我们将研究如何定义一个简单的多层感知机、卷积神经网络和循环神经网络。这些示例将为理解后面更复杂的示例奠定基础。

### 2.4.1 多层感知机

在本节中，我们定义一个用于二分类的多层感知机模型。该模型有 10 个输入、3 个隐藏层（分别包含 10、20 和 10 个神经元）以及一个具有 1 个输出的输出层。每个隐藏层使用整流线性激活函数，输出层使用 sigmoid 激活函数，用于二分类。

```
# example of a multilayer perceptron
from keras.utils import plot_model
from keras.models import Model
from keras.layers import Input
from keras.layers import Dense
visible = Input(shape=(10,))
hidden1 = Dense(10, activation='relu')(visible)
hidden2 = Dense(20, activation='relu')(hidden1)
hidden3 = Dense(10, activation='relu')(hidden2)
output = Dense(1, activation='sigmoid')(hidden3)
model = Model(inputs=visible, outputs=output)
# summarize layers
model.summary()
# plot graph
plot_model(model, to_file='multilayer_perceptron_graph.png')
```

清单 2.21：使用函数式 API 定义 MLP 的示例。

运行示例将打印网络的结构。

| 层 (类型) | 输出形状 | 参数数量 |
|---|---|---|
| input_1 (InputLayer) | (None, 10) | 0 |
| dense_1 (Dense) | (None, 10) | 110 |
| dense_2 (Dense) | (None, 20) | 220 |
| dense_3 (Dense) | (None, 10) | 210 |
| dense_4 (Dense) | (None, 1) | 11 |

总参数: 551  
可训练参数: 551  
不可训练参数: 0  

清单 2.22：使用函数式 API 定义的 MLP 模型摘要。

模型图的图表也已创建并保存到文件中。

**注意**: 创建模型图假设已安装 `pydot` 和 `graphviz` 库。如果这有问题，你可以注释掉导入语句和 `plot_model()` 的函数调用。

![](img/443014fed0f53a293f6ece3b211c1603_41_0.png)

### 2.4.2 卷积神经网络

在本节中，我们将定义一个用于图像分类的卷积神经网络。该模型接收黑白 64 × 64 图像作为输入，然后有一系列两个卷积层和池化层作为特征提取器，接着是一个全连接层来解释特征，以及一个带有 sigmoid 激活的输出层用于二类预测。

```
# example of a convolutional neural network
from keras.utils import plot_model
from keras.models import Model
from keras.layers import Input
from keras.layers import Dense
from keras.layers import Flatten
from keras.layers.convolutional import Conv2D
from keras.layers.pooling import MaxPooling2D
visible = Input(shape=(64,64,1))
conv1 = Conv2D(32, (4,4), activation='relu')(visible)
pool1 = MaxPooling2D()(conv1)
conv2 = Conv2D(16, (4, 4), activation='relu')(pool1)
pool2 = MaxPooling2D()(conv2)
flat1 = Flatten()(pool2)
hidden1 = Dense(10, activation='relu')(flat1)
output = Dense(1, activation='sigmoid')(hidden1)
model = Model(inputs=visible, outputs=output)
# summarize layers
model.summary()
# plot graph
plot_model(model, to_file='convolutional_neural_network.png')
```

清单 2.23：使用函数式 API 定义 CNN 的示例。

运行示例将汇总模型层。

| 层 (类型) | 输出形状 | 参数数量 |
| :--- | :--- | :--- |
| input_1 (InputLayer) | (None, 64, 64, 1) | 0 |
| conv2d_1 (Conv2D) | (None, 61, 61, 32) | 544 |
| max_pooling2d_1 (MaxPooling2D) | (None, 30, 30, 32) | 0 |
| conv2d_2 (Conv2D) | (None, 27, 27, 16) | 8208 |
| max_pooling2d_2 (MaxPooling2D) | (None, 13, 13, 16) | 0 |
| flatten_1 (Flatten) | (None, 2704) | 0 |
| dense_1 (Dense) | (None, 10) | 27050 |
| dense_2 (Dense) | (None, 1) | 11 |
| 总参数: 35,813 | | |
| 可训练参数: 35,813 | | |
| 不可训练参数: 0 | | |

清单 2.24：使用函数式 API 定义的 CNN 模型摘要。

模型图的图表也已创建并保存到文件中。

> **注意:** 创建模型图假设已安装 `pydot` 和 `graphviz` 库。如果这有问题，你可以注释掉导入语句和 `plot_model()` 的函数调用。

![](img/443014fed0f53a293f6ece3b211c1603_43_0.png)

图 2.3: CNN 模型图的图表。

### 2.4.3 循环神经网络

在本节中，我们将定义一个用于序列分类的长短期记忆循环神经网络。该模型期望 100 个时间步的单个特征作为输入。该模型有一个单一的 LSTM 隐藏层来从序列中提取特征，接着是一个全连接层来解释 LSTM 输出，接着是一个用于进行二进制预测的输出层。

```
# example of a recurrent neural network
from keras.utils import plot_model
from keras.models import Model
from keras.layers import Input
from keras.layers import Dense
from keras.layers.recurrent import LSTM
visible = Input(shape=(100,1))
hidden1 = LSTM(10)(visible)
hidden2 = Dense(10, activation='relu')(hidden1)
output = Dense(1, activation='sigmoid')(hidden2)
model = Model(inputs=visible, outputs=output)
# summarize layers
model.summary()
# plot graph
plot_model(model, to_file='recurrent_neural_network.png')
```

清单 2.25：使用函数式 API 定义 RNN 的示例。

运行示例将汇总模型层。

| 层 (类型) | 输出形状 | 参数数量 |
| :--- | :--- | :--- |
| input_1 (InputLayer) | (None, 100, 1) | 0 |
| lstm_1 (LSTM) | (None, 10) | 480 |
| dense_1 (Dense) | (None, 10) | 110 |
| dense_2 (Dense) | (None, 1) | 11 |
| 总参数: 601 | | |
| 可训练参数: 601 | | |
| 不可训练参数: 0 | | |

清单 2.26：使用函数式 API 定义的 RNN 模型摘要。

模型图的图表也已创建并保存到文件中。

注意: 创建模型图假设已安装 `pydot` 和 `graphviz` 库。如果这有问题，你可以注释掉导入语句和 `plot_model()` 的函数调用。

![](img/443014fed0f53a293f6ece3b211c1603_44_0.png)

图 2.4: RNN 模型图的图表。

