

| tf.estimator tf.feature_column | 高级深度学习 API | tf.saved_model tf.autograph tf.lite tf.distribute tf.quantization tf.graph_util | 部署与优化 |
| :--- | :--- | :--- | :--- |
| tf.keras | | | |
| tf.data tf.io tf.queue tf.image tf.strings | I/O 与预处理 | tf.summary tf.sparse tf.ragged tf.sets | 使用 TensorBoard 可视化 |
| tf.nn tf.rnn tf.train | 低级深度学习 API | tf.math tf.linalg tf.signal tf.random tf.bitwise | 数学，包括线性代数、信号处理等 |
| tf.GradientTape tf.gradients () | 自动微分 | | |

图 12-1：TensorFlow 的 Python API

![](img/0684d2da98e09085c0a622d4fd69aaad_394_0.png)

我们将涵盖 TensorFlow API 的许多包和函数，但涵盖所有内容是不可能的，因此你应该花时间浏览一下 API：你会发现它非常丰富且文档完备。

在最底层，每个 TensorFlow 操作都是使用高度高效的 C++ 代码实现的。许多操作（或简称 ops）有多个实现方式和内核（kernels）；每个内核专门用于特定的设备类型，例如 CPU、GPU 或 TPU（TensorFlow 处理单元）。正如你可能所知的，TPU 可以通过将计算拆分为许多块并在许多 GPU 上并行运行来极大地加速计算。你可以运行自己的 GPU 设备，目前TensorFlow 仅支持具有 CUDA 计算能力 3.5+ 的 Nvidia 设备，但 TPUs 仅在 Google Cloud Learning Engine 上可用（见 ???）。

TensorFlow 的架构如图 12-2 所示：大多数时候，你的代码将使用高级 API（特别是 `tf.keras` 和 `tf.data`），但当你需要灵活性时，将使用低级 Python API 直接处理张量（tensors）。注意，还提供了其他语言的 API。在任何情况下，TensorFlow 的执行引擎都会负责高效地运行操作，即使你让它跨多个设备机器运行也可以。

- 如果你有需要（尽管可能不会），你可以使用 C++ API 编写自己的操作。
- 如果你是一名研究人员，你可能符合免费使用这些 TPUs 的条件，详见 https://tensorflow.org/tfrc。

TensorFlow 概览 | 369

WOW! eBook
www.wowebook.org

![](img/0684d2da98e09085c0a622d4fd69aaad_395_0.png)

图 12-2：TensorFlow 的架构

TensorFlow 不仅运行在 Windows、Linux 和 MacOS 上，还可以在多个设备上（使用 TensorFlow Lite），包括 iOS 和 Android（见 ???）。如果你不想使用 Python API，还有 C++、Java、Go 和 Swift API。有一个名为 TensorFlow.js 的 JavaScript 实现，它让你能够直接在浏览器中运行模型。

TensorFlow 不仅仅是一个库。TensorFlow 是一个庞大库生态系统的中心。首先，有用于可视化的 Board（见第 10 章）。接下来是 TensorFlow Extended (TFX)，这是由 Google 构建的一组用于 TensorFlow 项目生产环境的库：它包含了数据验证、预处理、模型分析和服务的工具（使用 TF Serving，见 ???）。Google 还发布了 TensorFlow Hub，这是一种轻松下载和重用预训练神经网络的方法。你可以找到 TensorFlow 的模型库。查看 TensorFlow Resources，或者访问 https://github.com/jtoy/awesome-tensorflow 获取更多基于 TensorFlow 的项目。你将在 GitHub 上找到数百个 TensorFlow 项目，因此对于你尝试做的任何事情，都很容易找到现有代码。

越来越多的 ML 论文发布时都带有实现代码，有时甚至带有预训练模型。查看 https://paperswithcode.com/ 可以轻松找到它们。

![](img/0684d2da98e09085c0a622d4fd69aaad_395_1.png)

最后但同样重要的是，TensorFlow 拥有一由热情且热心的开发者组成的专门团队，以及一个致力于改进它的大型社区。要提技术问题，你应该使用 http://stackoverflow.com/ 并为你的问题标记 `tensorflow` 和 `python` 标签。你可以通过 GitHub 发现图形 Bug 和功能请求。对于一般讨论，请加入 Google小组。

好了，该开始编码了！

# 像使用 NumPy一样使用 TensorFlow

TensorFlow 的 API 围绕张量（tensors）展开，因此名为 Tensor-Flow。张量通常是一个多维数组（与 NumPy ndarray 完全相同），但它也可以包含标量（单个值，例如 42）。当我们创建自定义函数、自定义指标、自定义层等时，这些张量将非常重要，所以，让我们看看如何创建和操作它们。

# 张量与操作

你可以使用 `tf.constant()` 轻松地创建一个张量。例如，这里有一个表示两行三列浮点数矩阵的张量：

```
>>> tf.constant([[1., 2., 3.], [4., 5., 6]]) # matrix
<tf.Tensor: id=0, shape=(2, 3), dtype=float32, numpy=array([[1., 2., 3.], [4., 5., 6.]], dtype=float32)>
>>> tf.constant(42) # scalar
<tf.Tensor: id=1, shape=(), dtype=int32, numpy=42)
```

就像 ndarray 一样，`tf.tensor` 具有形状（shape）和数据类型（dtype）：

```
>>> t = tf.constant([[1., 2., 3.], [4., 5., 6]])
>>> t.shape
TensorShape([2, 3])
>>> t.dtype
float32
```

索引工作原理与 NumPy 非常相似：

```
>>> t[:, :2]
<tf.Tensor: id=5, shape=(2, 2), dtype=float32, numpy=array([[1., 2.], [4., 5.]], dtype=float32)>
>>> t[..., 1, tf.newaxis]
<tf.Tensor: id=15, shape=(2, 1), dtype=float32, numpy=array([[2.], [5]]], dtype=float32)
```

最重要的是，所有的张量操作都是可用的：

```
>>> t + 10
<tf.Tensor: id=18, shape=(2, 3), dtype=float32, numpy=array([[11., 12., 13.], [14., 15., 16.]], dtype=float32)>
```

