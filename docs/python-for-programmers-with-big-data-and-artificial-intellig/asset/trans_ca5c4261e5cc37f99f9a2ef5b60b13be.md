

单击此处查看代码图像

```python
[47]: def display_probabilities(prediction):
    for index, probability in enumerate(prediction):
        print(f'{index}: {probability:.10%}')
```

虽然图像输出第一行中的 8（索引为 495）看起来像 8，但我们的模型对它感到棘手。如下面的输出所示，模型将此图像预测为 0，但也认为它有 16% 的可能性是 6，23% 的可能性是 8：

单击此处查看代码图像

```
[48]: display_probabilities(predictions[495])
0: 59.7235262394%
1: 0.0000015465%
2: 0.8047289215%
3: 0.0001740813%
4: 0.0016636326%
5: 0.0030567855%
6: 16.1390662193%
7: 0.0000001781%
8: 23.3022540808%
9: 0.0255270657%
```

第一行中的 2（索引为 583）被模型以 62.7% 的确定性预测为 7，但模型也认为它有 36.4% 的可能性是 2：

单击此处查看代码图像

```
[49]: display_probabilities(predictions[583])
0: 0.0000003016%
1: 0.0000005715%
2: 36.4056706429%
3: 0.0176281916%
4: 0.0000561930%
5: 0.0000000003%
6: 0.0000000019%
7: 62.7455413342%
8: 0.8310816251%
9: 0.0000114385%
```

第二行开头的 6（索引为 625）被预测为 4，尽管这远非确定。在这种情况下，4 的概率（51.6%）仅略高于 6 的概率（48.38%）：

单击此处查看代码图像

```
[50]: display_probabilities(predictions[625])
0: 0.0008245181%
1: 0.0000041209%
2: 0.0012774357%
3: 0.0000000009%
4: 51.6223073006%
5: 0.0000001779%
6: 48.3754962683%
7: 0.000000085%
8: 0.0000048182%
9: 0.0000785786%
```

## 15.6.6 保存和加载模型

神经网络模型可能需要大量的训练时间。一旦你设计并测试了符合需求的模型，就可以保存其状态。这样以后可以加载它来进行更多预测。有时模型会被加载并针对新问题进一步训练。例如，我们模型中的层已经知道如何识别线条和曲线等特征，这在手写字符识别（如 EMNIST 数据集）中也很有用。因此，你可能加载现有模型，并将其作为更强大模型的基础。此过程称为 **迁移学习** <sup>5</sup> <sup>6</sup>——你将现有模型的知识迁移到新模型。Keras 模型的 **save 方法** 将模型的架构和状态信息存储在称为 **分层数据格式 (HDF5)** 的格式中。此类文件默认使用 `.h5` 文件扩展名：

<sup>5</sup> https://towardsdatascience.com/transfer-learning-from-pre-trained-models-f2393f124751.

<sup>6</sup> https://medium.com/nanonets/nanonets-how-to-use-deep-learning-when-you-have-limited-data-f68c0b512cab.

```
[51]: cnn.save('mnist_cnn.h5')
```

你可以使用 `tensorflow.keras.models` 模块中的 `load_model` 函数加载保存的模型：

单击此处查看代码图像

```python
from tensorflow.keras.models import load_model
cnn = load_model('mnist_cnn.h5')
```

然后可以调用其方法。例如，如果你获取了更多数据，可以调用 `predict` 对新数据进行额外预测，也可以调用 `fit` 使用额外数据开始训练。

Keras 提供了几个其他函数，使你能够保存和加载模型的各个方面。有关详细信息，请参阅

https://keras.io/getting-started/faq/#how-can-i-save-a-keras-model

## 15.7 使用 TensorBoard 可视化神经网络训练

在深度学习网络中，内部发生的事情非常复杂且大部分对你隐藏，因此很难了解并完全理解所有细节。这在测试、调试和更新模型及算法时带来了挑战。深度学习学习特征，但特征数量可能非常多，并且对你来说可能并不明显。

Google 提供了 TensorBoard 7, 8 工具，用于可视化在 TensorFlow 和 Keras 中实现的神经网络。就像汽车仪表板可视化来自汽车传感器的数据（例如车速、发动机温度和剩余燃油量）一样，TensorBoard 仪表板可视化来自深度学习模型的数据，可让你了解模型学习效果如何，并可能帮助你调整超参数。在这里，我们将介绍 TensorBoard。

7 https://github.com/tensorflow/tensorboard/blob/master/README.md.

8 https://www.tensorflow.org/guide/summaries_and_tensorboard.

### 执行 TensorBoard

TensorBoard 监视系统上的一个文件夹，查找包含它将在 Web 浏览器中可视化的数据的文件。在这里，你将创建该文件夹，执行 TensorBoard 服务器，然后通过 Web 浏览器访问它。执行以下步骤：

- 1. 在终端、Shell 或 Anaconda 命令提示符中切换到 ch15 文件夹。

- 2. 确保自定义 Anaconda 环境 tf_env 已激活：

```
conda activate tf_env
```

- 3. 执行以下命令创建一个名为 logs 的子文件夹，深度学习模型将在此文件夹中写入 TensorBoard 将可视化的信息：

```
mkdir logs
```

- 4. 执行 TensorBoard

```
tensorboard --logdir=logs
```

- 5. 现在可以在 Web 浏览器中访问 TensorBoard：

```
http://localhost:6006
```

如果在执行任何模型之前连接到 TensorBoard，它最初将显示一个页面，指示“当前数据集没有活动的信息中心。” 9

- 9 TensorBoard 目前不支持 Microsoft Edge 浏览器。

### TensorBoard 控制面板

TensorBoard 监视你指定的文件夹，查找模型在训练期间输出的文件。当 TensorBoard 看到更新时，它会将数据加载到控制面板中：

![](img/34b7fc2f1ee27beb73bca14927d42340_709_0.png)

你可以在训练期间或训练完成后查看数据。上面的控制面板显示了 TensorBoard **标量** 标签页，该标签页显示随时间变化的单个值的图表，例如第一行显示的训练准确率（acc）和训练损失（loss），以及第二行显示的验证准确率（val_acc）和验证损失（val_loss）。这些图表可视化了我们 MNIST 卷积神经网络的 10 个时代运行，我们在笔记本 MNIST_CNN_TensorBoard.ipynb 中提供了该运行。时代沿 x 轴显示，从第一个时代的 0 开始。准确率和损失值沿 y 轴显示。查看训练和验证准确率时，你可以在前 5 个时代看到与前一节中五个时代运行相似的结果。

对于 10 个时代的运行，训练准确率一直提升到第 9 个时代，然后略微下降。这可能是我们开始过拟合的时点，但我们可能需要训练更长时间才能发现。对于验证准确率，你可以看到它迅速上升，然后在五个时代内保持相对平坦，之后再次上升然后下降。对于训练损失，你可以看到它迅速下降，然后一直下降到第 9 个时代，之后略有增加。验证损失迅速下降然后波动。我们可以运行更多时代的模型来看看结果是否改善，但根据这些图表，大约在第六个时代，我们获得了训练和验证准确率的良好组合，且验证损失最小。

通常，这些图表在控制面板中垂直堆叠。我们使用搜索字段（位于图表上方）来显示文件夹名称中包含“mnist”的任何图表——我们稍后将配置这一点。TensorBoard 可以一次加载多个模型的数据，你可以选择要可视化哪个。这样可以轻松比较多个不同模型或同一模型的多个运行。

### 复制 MNIST 卷积网络的笔记本

要为此示例创建新笔记本：

- 1. 在 JupyterLab 的文件浏览器标签页中右键单击 MNIST_CNN.ipynb 笔记本，然后选择 Duplicate 以制作笔记本的副本。

