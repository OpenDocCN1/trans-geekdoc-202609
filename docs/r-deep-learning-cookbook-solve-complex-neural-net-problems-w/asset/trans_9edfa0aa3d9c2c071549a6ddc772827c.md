

The objective function shows similar behaviors for train and test cost function; thus, the model seems to be stable for the given case with convergence attaining around 1,600 iterations.

## 从多层感知机开始

This section will focus on extending the logistic regression concept to neural networks.

> 神经网络，也称为人工神经网络（ANN），是一种受生物大脑神经元结构启发的计算范式。

## 准备工作

The ANN is a collection of artificial neurons that perform simple operations on the data; the output from this is passed to another neuron. The output generated at each neuron is called its activation function. An example of a multilayer perceptron model can be seen in the following screenshot:

![](img/88a9c35e3059565190fbb6413f1ca217_66_0.png)

Each link in the preceding figure is associated to weights processed by a neuron. Each neuron can be looked at as a processing unit that takes input processing and the output is passed to the next layer, as shown in the following screenshot:

![](img/88a9c35e3059565190fbb6413f1ca217_67_0.png)

An example of a neuron getting three inputs and one output

The preceding figure demonstrates three inputs combined at neuron to give an output that may be further passed to another neuron. The processing conducted at the neuron could be a very simple operation such as the input multiplied by weights followed by summation or a transformation operation such as the sigmoid activation function.

## 操作方法...

This section covers type activation functions in multilayer perceptrons. Activation is one of the critical component of ANN as it defines the output of that node based on the given input. There are many different activation functions used while building a neural network:

- **Sigmoid**: Sigmoid 激活函数是一个连续函数，也称为逻辑函数，形式为 1/(1+exp(-x))。Sigmoid 函数在训练期间倾向于将反向传播项归零，导致响应饱和。在 TensorFlow 中，Sigmoid 激活函数使用 `tf.nn.sigmoid` 函数定义。
- **ReLU**: 修正线性单元（ReLU）是神经网络中用于捕捉非线性的最著名的连续但不平滑的激活函数之一。ReLU 函数定义为 `max(0,x)`。在 TensorFlow 中，ReLU 激活函数定义为 `tf.nn.relu`。
- **ReLU6**: 它将 ReLU 函数上限限制为 6，定义为 `min(max(0,x), 6)`，因此值不会变得非常小或非常大。该函数在 TensorFlow 中定义为 `tf.nn.relu6`。
- **tanh**: 双曲正切是另一种用作神经网络激活函数的平滑函数，范围限定为 [-1 到 1]，并实现为 `tf.nn.tanh`。
- **softplus**: 它是 ReLU 的连续版本，因此存在导数，定义为 `log(exp(x)+1)`。在 TensorFlow 中，softplus 定义为 `tf.nn.softplus`。

## 更多内容...

神经网络中有三种主要的神经网络架构：

- **Feedforward ANN**: 这是一类神经网络模型，其中信息流从输入到输出是单向的；因此，架构不形成任何循环。下图显示了一个前馈网络示例：

![](img/88a9c35e3059565190fbb6413f1ca217_68_0.png)

神经网络的前馈架构

- **Feedback ANN**: 这也称为 Elman 循环网络，是一类神经网络，其中输出节点的误差用作反馈以迭代更新以最小化误差。下图显示了一个单层反馈神经网络架构示例：

![](img/88a9c35e3059565190fbb6413f1ca217_68_1.png)

神经网络的反馈架构

- **Lateral ANN**: 这是反馈和前馈神经网络之间的一类神经网络，其中神经元在层内相互作用。下图显示了一个侧向神经网络架构示例：

![](img/88a9c35e3059565190fbb6413f1ca217_69_0.png)

侧向神经网络架构

## 另请参阅

有关 TensorFlow 支持的更多激活函数，可访问 https://www.tensorflow.org/versions/r0.10/api_docs/python/nn/activation_functions_。

## 使用 H2O 设置神经网络

In this section, we will cover the application of H2O in setting up a neural network. The example will use a similar dataset as used in logistic regression.

## 准备工作

我们首先使用以下代码加载所有所需的包：

```
# Load the required packages
require(h2o)
```

然后，使用 h2o.init() 函数在八个核心上初始化单节点 H2O 实例，并在 IP 地址 localhost 和端口号 54321 上实例化相应的客户端模块：

```
# Initialize H2O instance (single node)
localH2O = h2o.init(ip = "localhost", port = 54321, startH2O = TRUE, min_mem_size = "20G", nthreads = 8)
```

## 操作方法...

本节展示如何使用 H2O 构建神经网络。

- 在 R 中加载占用率训练和测试数据集：

```
# Load the occupancy data
occupancy_train <-
read.csv("C://occupancy_detection/datatraining.txt",stringsAsFactors = T)
occupancy_test <-
read.csv("C://occupancy_detection/datatest.txt",stringsAsFactors = T)
```

- 将使用以下自变量（x）和因变量（y）来建模 GLM：

```
# Define input (x) and output (y) variables
x = c("Temperature", "Humidity", "Light", "CO2", "HumidityRatio")
y = "Occupancy"
```

- 根据 H2O 的要求，将因变量转换为因子，如下所示：

```
# Convert the outcome variable into factor
occupancy_train$Occupancy <- as.factor(occupancy_train$Occupancy)
occupancy_test$Occupancy <- as.factor(occupancy_test$Occupancy)
```

- 然后将数据集转换为 H2OParsedData 对象：

```
# Convert Train and Test datasets into H2o objects
occupancy_train.hex <- as.h2o(x = occupancy_train,
destination_frame = "occupancy_train.hex")
occupancy_test.hex <- as.h2o(x = occupancy_test, destination_frame = "occupancy_test.hex")
```

- 数据加载并转换为 H2OParsedData 对象后，使用 h2o.deeplearning 函数构建多层前馈神经网络。在当前设置中，使用以下参数构建 NN 模型：

  - 使用 hidden 的五个神经元的单个隐藏层
  - 使用 epochs 的 50 次迭代
  - 使用自适应学习率（adaptive_rate）而不是固定学习率（rate）
  - 基于 ReLU 的整流器激活函数
  - 使用 nfold 的五折交叉验证

```
# H2O based neural network to Train the model
occupancy.deepmodel <- h2o.deeplearning(x = x,
                                      y = y,
                                      training_frame =
                                      occupancy_train.hex,
                                      validation_frame =
                                      occupancy_test.hex,
                                      standardize = F,
                                      activation = "Rectifier",
                                      epochs = 50,
                                      seed = 1234567,
                                      hidden = 5,
                                      variable_importances = T,
                                      nfolds = 5,
                                      adaptive_rate = TRUE)
```

- 除了使用 H2O 执行逻辑回归食谱中描述的命令外，您还可以定义其他参数来微调模型性能。以下列表并未涵盖所有功能参数，但根据重要性涵盖了一些。完整的参数列表可在 h2o 包的文档中找到。

  - 选项：使用预训练自编码器模型初始化模型。
  - 通过修改时间衰减因子（rho）和平滑因子（epsilon）的选项来微调自适应学习率。在固定学习率（rate）的情况下，可以修改退火率（rate_annealing）和层间衰减因子（rate_decay）。

