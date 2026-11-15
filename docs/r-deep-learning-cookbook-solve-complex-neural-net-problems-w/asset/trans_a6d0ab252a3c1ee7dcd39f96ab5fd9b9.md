

前面的脚本将生成两个列表文件：pks.lst_train.lst 和 pks.lst_val.lst。训练集和验证集的划分由前面脚本中的 train-ratio 参数控制。类别数量基于训练目录中文件夹的数量。在此场景中，选取了两个类别：汽车和飞机。

8. 将训练和验证数据集的 *.rec 文件进行转换：

```
# Creating .rec file from training sample list
System("python ~/mxnet/tools/im2rec.py --num-thread=4 --pass-through=1 /home/prakash/deep\ learning/cifar_224/pks.lst_train.lst /home/prakash/deep\ learning/cifar_224/training/")
# Creating .rec file from validation sample list
System("python ~/mxnet/tools/im2rec.py --num-thread=4 --pass-through=1 /home/prakash/deep\ learning/cifar_224/pks.lst_val.lst /home/prakash/deep\ learning/cifar_224/training/")
```

前面的脚本将创建 pks.lst_train.rec 和 pks.lst_val.rec 文件，以便在下一个示例中使用预训练模型来训练模型。

## 构建图像分类模型

本示例专注于使用迁移学习构建图像分类模型。它将使用之前示例中准备的数据集，并采用 Inception-BN 架构。Inception-BN 中的 BN 代表批量归一化。计算机视觉中 Inception 模型的详细信息可参见 Szegedy et al. (2015)。

### 准备工作

本节介绍使用 Inception-BN 预训练模型设置分类模型所需的先决条件。

- 1. 将图像转换为用于训练和验证的 .rec 文件。
- 2. 从 http://data.dmlc.ml/models/imagenet/inception-bn/ 下载 Inception-BN 架构。
- 3. 安装 R 和 R 中的 mxnet 包。

### 操作步骤...

1. 将 .rec 文件加载为迭代器。以下是加载 .rec 数据为迭代器的函数：

```
# Function to load data as iterators
data.iterator <- function(data.shape, train.data, val.data,
BATCHSIZE = 128) {
# Load training data as iterator
train <- mx.io.ImageRecordIter(
path.imgrec = train.data,
batch.size = BATCHSIZE,
data.shape = data.shape,
rand.crop = TRUE,
rand.mirror = TRUE)
# Load validation data as iterator
val <- mx.io.ImageRecordIter(
path.imgrec = val.data,
batch.size = BATCHSIZE,
data.shape = data.shape,
rand.crop = FALSE,
rand.mirror = FALSE
)
return(list(train = train, val = val))
}
```

在前面的函数中，mx.io.ImageRecordIter 从 RecordIO (.rec) 文件中读取图像批次。

2. 使用 data.iterator 函数加载数据：

```
# Load dataset
data <- data.iterator(data.shape = c(224, 224, 3),
train.data = "pks.lst_train.rec",
val.data = "pks.lst_val.rec",
BATCHSIZE = 8)

train <- data$train
val <- data$val
```

3. 从 Inception-BN 文件夹加载 Inception-BN 预训练模型：

```
# Load Inception-BN model
inception_bn <- mx.model.load("Inception-BN", iteration = 126)
symbol <- inception_bn$symbol
```

可以使用函数 symbol$arguments 查看模型的不同层。

4. 获取 Inception-BN 模型的层：

```
# Load model information
internals <- symbol$get.internals()
outputs <- internals$outputs
flatten <- internals$get.output(which(outputs == "flatten_output"))
```

5. 定义新层以替换 flatten_output 层：

```
# Define new layer
new_fc <- mx.symbol.FullyConnected(data = flatten,
                                             num_hidden = 2,
                                             name = "fc1")
new_soft <- mx.symbol.SoftmaxOutput(data = new_fc,
                                             name = "softmax")
```

6. 为新定义的层初始化权重。要重新训练最后一层，使用以下脚本进行权重初始化：

```
# Re-initialize the weights for new layer
arg_params_new <- mxnet:::mx.model.init.params (
  symbol = new_soft,
  input.shape = c(224, 224, 3, 8),
  output.shape = NULL,
  initializer = mxnet:::mx.init.uniform(0.2),
  ctx = mx.cpu(0)
)$arg.params
fc1_weights_new <- arg_params_new[["fc1_weight"]]
fc1_bias_new <- arg_params_new[["fc1_bias"]]
```

在上述层中，权重使用 [-0.2, 0.2] 之间的均匀分布进行赋值。ctx 定义执行所在的设备。

7. 重新训练模型：

```
# Mode re-train
model <- mx.model.FeedForward.create (
  symbol = new_soft,
  X = train,
  eval.data = val,
  ctx = mx.cpu(0),
  eval.metric = mx.metric.accuracy,
  num.round = 5,
  learning.rate = 0.05,
  momentum = 0.85,
  wd = 0.00001,
  kvstore = "local",
  array.batch.size = 128,
  epoch.end.callback = mx.callback.save.checkpoint("inception_bn"),
  batch.end.callback = mx.callback.log.train.metric(150),
  initializer = mx.init.Xavier(factor_type = "in", magnitude = 2.34),
  optimizer = "sgd",
  arg.params = arg_params_new,
  aux.params = inception_bn$aux.params
)
```

前面的模型设置为在 CPU 上运行五轮，使用准确率作为评估指标。以下截图显示了所描述模型的执行情况：

![](img/88a9c35e3059565190fbb6413f1ca217_271_0.png)

使用 CIFAR-10 数据集训练的 Inception-BN 模型输出

训练后的模型训练准确率为 0.97，验证准确率为 0.95。

## 在 GPU 上训练深度学习模型

图形处理单元 (GPU) 是使用大量内核来渲染图像的硬件。Pascal 是 NVIDIA 发布的最新 GPU 微架构。GPU 中数百个内核的存在有助于增强计算能力。本节介绍了使用 GPU 运行深度学习模型的示例。

### 准备工作

本节介绍运行 GPU 和 CPU 所需的依赖项：

- 1. 本示例中进行的实验使用 GTX 1070 等 GPU 硬件。
- 2. 为 GPU 安装 mxnet。要为特定机器安装适用于 GPU 的 mxnet，请按照 mxnet.io 上的安装说明操作。如截图所示选择要求，并按照说明操作：

![](img/88a9c35e3059565190fbb6413f1ca217_272_0.png)

获取 MXNet 安装说明的步骤

### 操作步骤...

以下是在 GPU 上训练深度学习模型的方法：

- 1. 前一节中讨论的 Inception-BN 迁移学习示例可以通过更改设备设置（如以下脚本所示）在已安装和配置的 GPU 机器上运行：

```
# Mode re-train
model <- mx.model.FeedForward.create (
	symbol = new_soft,
	X = train,
	eval.data = val,
	ctx = mx.gpu(0),
	eval.metric = mx.metric.accuracy,
	num.round = 5,
	learning.rate = 0.05,
	momentum = 0.85,
	wd = 0.00001,
	kvstore = "local",
	array.batch.size = 128,
	epoch.end.callback = mx.callback.save.checkpoint ("inception_bn"),
	batch.end.callback = mx.callback.log.train.metric(150),
	initializer = mx.init.Xavier(factor_type = "in", magnitude = 2.34),
	optimizer = "sgd",
	arg.params = arg_params_new,
	aux.params = inception_bn$aux.params
)
```

在上述模型中，设备设置已从 mx.cpu 更改为 mx.gpu。CPU 进行五次迭代计算约需 2 小时，而使用 GPU 则在约 15 分钟内完成相同的迭代。

### 使用 CPU 和 GPU 比较性能

更换设备时的一个问题是：当设备从 CPU 切换到 GPU 时，为什么会观察到如此大的性能提升。由于深度学习架构涉及大量矩阵计算，GPU 利用大量通常用于图像渲染的并行内核来加速这些计算。

许多算法都利用了 GPU 的强大性能来加速执行。以下示例介绍了使用 `gpuR` 包进行矩阵计算的基准测试。`gpuR` 包是用于在 R 中进行 GPU 计算的通用包。

### 准备工作

本节介绍设置 GPU 与 CPU 比较所需的条件。

- 1. 使用已安装的 GTX 1070 等 GPU 硬件。
- 2. 使用 URL https://developer.nvidia.com/cuda-downloads 安装 CUDA 工具包。
- 3. 安装 `gpuR` 包：

  ```r
  install.packages("gpuR")
  ```
- 4. 测试 `gpuR`：

  ```r
  library(gpuR)
  # verify you have valid GPUs
  detectGPUs()
  ```

### 操作步骤...

首先加载包：

- 1. 加载包，并将精度设置为 `float`（默认情况下，GPU 精度设置为单精度）：

  ```r
  library("gpuR")
  options(gpuR.default.type = "float")
  ```
- 2. 将矩阵分配到 GPU：

  ```r
  # Assigning a matrix to GPU
  A<-matrix(rnorm(1000), nrow=10)
  vcl1 = vclMatrix(A)
  ```

