
1. `matplotlib.pyplot` 将被导入；  
2. 你会将图表调整到你想要的尺寸，因此子图的大小保持一致；  
3. 子图的设置将由你的参数决定，从而让你有调整图像布局的选项；  
4. 完成以上操作后，你会填充图表；  
5. 子图需要初始化，这可以通过将每个子图放置到合适的网格位置来实现；  
6. 现在图表已填充，你可以初始化子图；  
7. 每个点的添加都会在网格上的图像上显示，就像彩色地图一样。插值方法会对网格上的数据进行插值，使其不完全平滑；  
8. 最后一步是向子图中添加文本；  
9. 最后，切记使用 `plt.show()` 函数绘制点。  

第9章：Keras 与机器学习 如果你关注最新的技术新闻，你就会知道 Tensorflow。这是一个由 Google 于 2015 年开源的机器学习框架，受到公众热烈欢迎。如果你以前从未使用过机器学习，那么这个框架会对你来说很难理解。但这可以通过 Keras 来解决，Keras 可以与 Tensorflow 以及其他几种机器学习框架一起使用，构建更快、更易用的神经网络。当你设置 Keras 时，你会想要下载与 Python 兼容的 Anaconda 发行版。如果你之前未使用过它，你会发现它使用非常简单。安装 Anaconda 后，你会进入 Anaconda 的 bin 目录中的 CD 并运行以下命令以确保一切正常工作。  

1. `pip install pandas`；  
2. `pip install Tensorflow`；以及  
3. `pip install Keras`。  

现在你知道一切都已正常工作，你就可以开始使用了！如果你以前从未使用过 Python，这没关系，因为你只需要了解程序的基本工作原理。如果你想在更复杂的层面使用 Python，那么学习如何在个人和职业生活中使用 Python 的每个方面会很有帮助。Keras 使用的数据集将处理一个包含患者到达就诊次数与取消就诊次数特征的数据集。你将使用这些特征构建神经网络，以预测患者将出席其就诊的次数。第一步是准备数据，然后才能训练模型。你需要读取数据并将其分为两个变量：一个是患者的特征，另一个是不出席的情况。  

Syntax `import pandas as pds` `Dataframex = pds.read_csv(no show issue comma 3000k. csv, usecols = [ 0, 1, 4, 6, 8, 9, 10, 11, 12, 13])` `Dataframe y = pds.read_csv(no show issue comma 300k csv, usecols = (\[ 5\])) Print (dataframe x.head()) Print (dataframe y.head())`  

在将数据导入程序后，你会发现有几个特征无法用数字表示，这将通过 `pandas` 库进行转换。此时，你需要将特征的值替换为数字，并对 `y` 数据框同样进行操作。在创建神经网络时，你需要先构建模型，然后在 Keras 中进行训练。你会将模型描述为一个顺序层的数据流，该流会在程序中经过处理。完成后，你会将其放入数据集并相应地训练模型。  

Syntax `import numpy as np` `Seed = 9` `np.random.seed(seed)` `from keras.models import sequential` `from keras.layers import dense` `Model = sequential()` `Model.add(dense(12, input_shape = 11, init = 'uniform', activation = sigmoid))` `Model.add(dense(12, init = 'uniform', activation = sigmoid))` `Model.add(dense(12, init = 'uniform', activation = sigmoid))` `Model.add(dense(2, init = 'uniform', activation = sigmoid))` `Model.summary()` `import keras` `Tbcallback = keras.callbacks.Tensorboard(log_dir = /tmp/keras_logs, write_graph = true)` `Model.compile(loss = 'mean_squared_error', optimizer = Adam, metrics = [accuracy])` `Model.fit(dataframe x.values, dataframe y.values, epochs = 9, batch_size = 43, verbose = 2, validation_split = 0.3, callbacks = [Tbcallback])`  

为了理解你刚刚做的事情，我们将其分解为步骤。首先，你会使用常量种子来生成伪随机数，以便每次使用时都能得到相同的序列，这在使用不同模型并比较性能时很有用。接下来，你会定义神经网络，使其完全连接到使用 sigmoid 函数的层和节点。Tensorboard 将用于可视化正在训练的模型。模型现在会使用优化器和损失函数进行训练。epoch 表示数据集被送入网络的次数。`validation_split` 将告诉你有多少数据会被保留用于验证模型的性能。`validation_split` 将告诉你有多少数据会被保留用于验证模型的性能。你现在可以使用 Tensorboard 通过以下代码可视化已训练的模型：在 Anaconda 的 bin 文件夹中运行 `tensorboard – logdir = /tmp/keras_logs`。  

第10章：Theano 与机器学习 Theano 是另一个 Python 库，你可以使用它定义、优化和评估包含多个数组和维度的各种数学方程。Theano 与 Keras 类似，但使用不同的命令，允许你用 Python 编写自己的文档。语法 `Python. / doc/ scripts/ docgen. Py` 你也可以使用 HTML 或 PDF 来生成文档。Theano 将是导入 Python 时使用的分发目录，它包含你正在使用的包。但有多个子模型可供选择，以便实现你的目标。`Sandbox` 将依赖于你使用的其他代码。`Gof` 加 `compile` 是核心命令。`Scalar` 将取决于核心内部的内容。`Sparse` 依赖于 `Tensor`。`Tensor` 依赖于 `scalar`。`Theano/ examples` 是程序或网络中已有的示例的复制件。`Theano/benchmark` 和 examples 是程序的分发内容，但不会随 Python 包一起安装。`Theano/bin` 包含在 bin 文件夹中复制的所有可执行脚本。Tests 是随包分发的测试部分，会落入相应的子模型。`Theano/doc` 是用于创建文档的文件和脚本。`Theano/html` 是生成文档的程序区域。每个命令都可以与机器学习一起使用，只要你像使用 Keras 那样编写代码。  
