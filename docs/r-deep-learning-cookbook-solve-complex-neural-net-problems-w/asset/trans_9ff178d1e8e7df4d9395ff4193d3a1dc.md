

## 在 R 中安装 MXNet

本节将介绍在 R 中安装 MXNet。

### 准备工作

MXNet 软件包是一个轻量级深度学习架构，支持 R、Python 和 Julia 等多种编程语言。从编程角度来看，它是符号式和命令式编程的结合，并支持 CPU 和 GPU。

基于 CPU 的 MXNet 在 R 中可以使用预构建的二进制包或源代码安装，源代码中的库需要构建。在 Windows/mac 上，可以直接从 R 控制台下载并安装预构建的二进制包。MXNet 要求 R 版本为 3.2.0 及更高版本。安装需要来自 CRAN 的 `drat` 软件包。`drat` 软件包有助于维护 R 仓库，可以使用 `install.packages()` 命令安装。

要在 Linux（13.10 或更高版本）上安装 MXNet，以下是一些依赖项：

- Git（用于从 GitHub 获取代码）
- libatlas-base-dev（用于执行线性代数运算）
- libopencv-dev（用于执行计算机视觉运算）

要安装带有 GPU 处理器的 MXNet，以下是一些依赖项：

- Microsoft Visual Studio 2013
- NVIDIA CUDA 工具包
- MXNet 软件包
- cuDNN（用于提供深度神经网络库）

另一种快速安装 `mxnet` 及其所有依赖项的方法是使用来自 `chstone` 仓库的预构建 Docker 镜像。将使用以下工具安装 `chstone/mxnet-gpu` Docker 镜像：

- 适用于 R 和 Python 的 MXNet
- Ubuntu 16.04
- CUDA（GPU 可选）
- cuDNN（GPU 可选）

### 操作步骤

1. 以下 R 命令使用预构建的二进制包安装 MXNet，非常方便。然后使用 drat 软件包添加来自 git 的 dmlc 仓库，接着安装 mxnet：

```
install.packages ("drat", repos="https://cran.rstudio.com")
drat:::addRepo("dmlc")
install.packages("mxnet")
```

2. 以下代码有助于在 Ubuntu 16.04 上安装 MXNet。前两行用于安装依赖项，其余行用于安装 MXNet，前提是满足所有依赖项：

```
sudo apt-get update
sudo apt-get install -y build-essential git libatlas-base-dev
libopencv-dev
git clone https://github.com/dmlc/mxnet.git ~/mxnet --recursive
cd ~/mxnet
cp make/config.mk .
echo "USE_BLAS=openblas" >>config.mk
make -j$(nproc)
```

3. 如果要为 GPU 构建 MXNet，则在 make 命令之前需要更新以下配置：

```
echo "USE_CUDA=1" >>config.mk
echo "USE_CUDA_PATH=/usr/local/cuda" >>config.mk
echo "USE_CUDNN=1" >>config.mk
```

![](img/88a9c35e3059565190fbb6413f1ca217_36_0.png)

其他操作系统上 MXNet 的详细安装可在 http://mxnet.io/get_started/setup.html 找到。

4. 以下命令用于使用 Docker 安装 MXNet（基于 GPU），并包含所有依赖项：

```
docker pull chstone/mxnet-gpu
```

## 在 R 中安装 TensorFlow

本节将介绍另一个非常流行的开源机器学习软件包 TensorFlow，它在构建深度学习模型方面非常有效。

### 准备工作

TensorFlow 是由 Google Brain 团队开发的另一个开源库，用于使用数据流图构建数值计算模型。TensorFlow 的核心是用 C++ 开发的，包装器使用 Python。R 中的 `tensorflow` 软件包为你提供对 TensorFlow API 的访问，该 API 由 Python 模块组成，用于执行计算模型。TensorFlow 支持基于 CPU 和 GPU 的计算。

R 中的 `tensorflow` 软件包调用 Python tensorflow API 进行执行，因此必须在 R 和 Python 中都安装 `tensorflow` 软件包，以便 R 能够正常工作。`tensorflow` 的以下依赖项：

- Python 2.7 / 3.x
- R (>3.2)
- R 中的 devtools 软件包，用于从 GitHub 安装 TensorFlow
- Python 中的 TensorFlow
- pip

### 操作步骤

1. 安装所有提到的依赖项后，可以直接使用 `devtools` 通过 `install_github` 命令安装 `tensorflow`，如下所示：

```
devtools::install_github("rstudio/tensorflow")
```

2. 在 R 中加载 `tensorflow` 之前，需要将 Python 路径设置为系统环境变量。可以直接从 R 环境中完成，如以下命令所示：

```
Sys.setenv(TENSORFLOW_PYTHON="/usr/bin/python")
library(tensorflow)
```

如果未安装 Python `tensorflow` 模块，R 会给出以下错误：

```
In [17]: # Loading and setting placeholder in tensorflow
Sys.setenv(TENSORFLOW_PYTHON="/usr/bin/python")
require(tensorflow)
x <- tf$placeholder(tf$float32, shape(NULL, 111))
Error: Python module tensorflow was not found.
Detected Python configuration:
python:         /usr/bin/python
libpython:      /usr/lib/python2.7/config-x86_64-linux-gnu/libpython2.7.so
pythonhome:     /usr:/usr
version:        2.7.12 (default, Nov 19 2016, 06:48:10)  [GCC 5.4.0 20160609]
numpy:          /usr/lib/python2.7/dist-packages/numpy
numpy_version:  [NOT FOUND]
tensorflow:     [NOT FOUND]
python versions found: 
/usr/bin/python
/usr/bin/python3
Traceback:
1. tf$placeholder
2. .python.builtin.module (tf, placeholder)
3. py_resolve_module_proxy(x)
4. stop(message, call. = FALSE)
```

如果 Python 中未安装 tensorflow，R 会引发上述错误：

可以使用 pip 在 Python 中安装 tensorflow：

```
pip install tensorflow # Python 2.7 with no GPU support
pip3 install tensorflow # Python 3.x with no GPU support
pip install tensorflow-gpu # Python 2.7 with GPU support
pip3 install tensorflow-gpu # Python 3.x with GPU support
```

### 工作原理

TensorFlow 遵循有向图哲学来设置计算模型，其中数学运算表示为节点，每个节点支持多个输入和输出，而边表示节点之间的数据通信。TensorFlow 中还存在称为 **控制依赖关系** 的边，它们不表示数据流；相反，它们提供与控制依赖相关的信息，例如控制依赖的节点必须先完成处理，然后控制依赖的目标节点才能开始执行。

逻辑回归评分的示例 TensorFlow 图如下图所示：

![](img/88a9c35e3059565190fbb6413f1ca217_39_0.png)

逻辑回归的 TensorFlow 图

前面的图示说明了使用优化权重对逻辑回归进行评分的 TensorFlow 图：

y = \frac{1}{1 + e^{-(\beta X + C)}}

MatMul 节点在输入特征矩阵 X 和优化权重 \beta 之间执行矩阵乘法。然后将常数 C 添加到 MatMul 节点的输出中。Add 的输出随后使用 Sigmoid 函数进行转换，以输出 Pr(y=1|X)。

### 另请参阅

使用 https://rstudio.github.io/tensorflow/low/ 中的资源在 R 中开始使用 TensorFlow。

## 在 R 中安装 H2O

H2O 是另一个非常流行的开源库，用于构建机器学习模型。它由 H2O.ai 生产，支持 R 和 Python 等多种语言。H2O 软件包是为分布式环境开发的多用途机器学习库，用于在大数据上运行算法。

### 准备工作

要设置 H2O，需要以下系统：

- 64 位 Java 运行时环境（版本 1.6 或更高版本）
- 最小 2 GB RAM

可以使用 h2o 软件包从 R 调用 H2O。h2o 软件包有以下依赖项：

- RCurl
- rjson
- statmod
- survival
- stats
- tools
- utils
- methods

对于未安装 curl-config 的计算机，RCurl 依赖项的安装在 R 中会失败，因此需要在 R 之外安装 curl-config。

### 操作步骤

1. 可以直接从 CRAN 安装 H2O，并将依赖项参数设置为 TRUE 以安装所有与 CRAN 相关的 h2o 依赖项。此命令将安装 h2o 软件包所需的所有 R 依赖项：

```
install.packages("h2o", dependencies = T)
```

