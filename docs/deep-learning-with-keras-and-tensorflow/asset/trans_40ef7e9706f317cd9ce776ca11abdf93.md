

# 目錄

1. [使用 Keras 和 Tensorflow 进行深度学习](#index.html)
2. [要求](#Requirements.html)
3. [1.1 简介 - 深度学习和人工神经网络](#1.1%20Introduction%20-%20Deep%20Learning%20and%20ANN.html)
4. [1.1.1 感知机和 Adaline](#1.1.1%20Perceptron%20and%20Adaline.html)
5. [1.1.2 MLP 和 MNIST](#1.1.2%20MLP%20and%20MNIST.html)
6. [2.1 简介 - Theano](#2.1%20Introduction%20-%20Theano.html)
7. [2.2 简介 - Tensorflow](#2.2%20Introduction%20-%20Tensorflow.html)
8. [2.3 Keras 简介](#2.3%20Introduction%20to%20Keras.html)
9. [2.3.1 Keras 后端](#2.3.1%20%20Keras%20Backend.html)
10. [3.0 - MNIST 数据集](#3.0%20-%20MNIST%20Dataset.html)
11. [3.1 隐藏层表示和嵌入](#3.1%20Hidden%20Layer%20Representation%20and%20Embeddings.html)
12. [4.1 卷积神经网络](#4.1%20Convolutional%20Neural%20Networks.html)
13. [4.2. MNIST CNN](#4.2.%20MNIST%20CNN.html)
14. [4.3 CIFAR10 CNN](#4.3%20CIFAR10%20CNN.html)
15. [4.4 深度卷积神经网络](#4.4%20Deep%20Convolutional%20Neural%20Networks.html)
16. [5.1 超参数调优](#5.1%20HyperParameter%20Tuning.html)
17. [5.3 迁移学习与微调](5.3%20Transfer%20Learning%20%26%20Fine-Tuning.html)
18. [5.3.1 Keras 与 TF 集成](#5.3.1%20Keras%20and%20TF%20Integration.html)
19. [6.1. 自动编码器和嵌入](#6.1.%20AutoEncoders%20and%20Embeddings.html)
20. [6.2 NLP 与深度学习](#6.2%20NLP%20and%20Deep%20Learning.html)
21. [7.1 RNN 和 LSTM](#7.1%20RNN%20and%20LSTM.html)
22. [7.2 用于句子生成的 LSTM](#7.2%20LSTM%20for%20Sentence%20Generation.html)
23. [8.1 自定义层](#8.1%20Custom%20Layer.html)
24. [8.2 多模态网络](#8.2%20Multi-Modal%20Networks.html)
25. [结论](#Conclusions.html)

# 使用 Keras 和 Tensorflow 进行深度学习

![](5114be51.jpg)

# 作者：Valerio Maggio

### FBK/MPBA 博士后数据科学家

## 联系方式：

| ![](twitter_small.png)[@leriomaggio](http://twitter.com/leriomaggio) || ![](gplus_small.png)[+ValerioMaggio](http://plus.google.com/+ValerioMaggio) |

| --- | --- |

| ![](linkedin_small.png)[valeriomaggio](it.linkedin.com/in/valeriomaggio) || ![](gmail_small.png)[vmaggio\_at\_fbk\_dot\_eu](mailto:vmaggio@fbk.eu) |

```
git clone https://github.com/leriomaggio/deep-learning-keras-tensorflow.git
```

* * *

## 第一部分：简介

- 人工神经网络简介
  - 感知机和 MLP
  - 纯 Python 朴素实现
  - 快速前向传播、SGD、反向传播
- 深度学习框架简介
  - Theano 简介
  - Tensorflow 简介
  - Keras 简介
    - 概述和主要特性
    - `core` 层概述
    - 多层感知机和全连接层
      - 使用 `keras.models.Sequential` 和 `Dense` 的示例
    - Keras 后端

## 第二部分：监督学习

- 全连接网络和嵌入
  - MNIST 数据集简介
  - 隐藏层表示和嵌入
- 卷积神经网络
  - 卷积滤波器的含义
    - ImageNet 中的示例
  - 可视化卷积神经网络
  - 高级 CNN
    - Dropout
    - MaxPooling
    - 批量归一化
  - 实践：MNIST 数据集
    - 全连接层和 MNIST
    - CNN 和 MNIST
  - 使用 Keras 的深度卷积神经网络（参考：`keras.applications`）
    - VGG16
    - VGG19
    - ResNet50
- 迁移学习和微调
- 超参数优化

## 第三部分：无监督学习

- 自动编码器和嵌入
- 自动编码器和 MNIST
  - 使用 `keras.datasets` 的 word2vec 和 doc2vec (gensim)
  - word2vec 和 CNN

## 第四部分：循环神经网络

- Keras 中的循环神经网络
  - `SimpleRNN`、`LSTM`、`GRU`
- 用于句子生成的 LSTM

## 第五部分：附加材料

- Keras 中的自定义层
- 使用 Keras 的多模态网络拓扑

# 要求

本教程需要以下软件包：

- Python 3.5 版本
  - Python 3.4 也应该可以
  - 可能 Python 2.7 也可以，但 `谁知道呢`？:P
- `numpy` 1.10 或更高版本：[http://www.numpy.org/](http://www.numpy.org/)
- `scipy` 0.16 或更高版本：[http://www.scipy.org/](http://www.scipy.org/)
- `matplotlib` 1.4 或更高版本：[http://matplotlib.org/](http://matplotlib.org/)
- `pandas` 0.16 或更高版本：[http://pandas.pydata.org](http://pandas.pydata.org)
- `scikit-learn` 0.15 或更高版本：[http://scikit-learn.org](http://scikit-learn.org)
- `keras` 2.0 或更高版本：[http://keras.io](http://keras.io)
- `tensorflow` 1.0 或更高版本：[https://www.tensorflow.org](https://www.tensorflow.org)
- `ipython`/`jupyter` 4.0 或更高版本，支持笔记本

（可选但推荐）：

- `pyyaml`
- `hdf5` 和 `h5py`（如果在 Keras 中使用模型保存/加载函数则需要）
- **NVIDIA cuDNN** 如果您的机器上有 NVIDIA GPU。https://developer.nvidia.com/rdp/cudnn-download

获取（大部分）这些软件包的最简单方法是使用 Continuum 的 [Anaconda](http://www.continuum.io/downloads) 等一站式安装程序。这些适用于多种架构。

* * *

### Python 版本

我目前在 **Anaconda** 上使用 **Python 3** 运行本教程

```
!python --version
```

```
Python 3.5.2
```

* * *

## 设置环境

在此仓库中，为 Linux 和 OSX 系统提供了使用 `conda` 重新创建虚拟环境的文件，分别是 `deep-learning.yml` 和 `deep-learning-osx.yml`。

要重新创建虚拟环境（以 Linux 为例）：

```
conda env create -f deep-learning.yml
```

对于 OSX，只需相应更改文件名即可。

### 关于安装带 GPU 支持的 Theano 的说明

**注意**：只有在 *pip 安装* `theano` 后，在启用 GPU 支持时出现错误时，才阅读本节！

自版本 `0.9` 起，Theano 在稳定版中引入了 [`libgpuarray`](http://deeplearning.net/software/libgpuarray)（之前仅在 *开发* 版本中可用）。

`libgpuarray` 的目标（*来自文档*）是创建一个通用的 GPU ndarray（n 维数组），可供所有项目重复使用，尽可能具有未来兼容性，同时保持易于使用以满足简单需求/快速测试。

以下是我整理的一些有用提示（希望如此），用于在（Ubuntu）Linux 上正确安装和配置带 **GPU** 支持的 `theano`：

1) \[如果您使用 Anaconda\] `conda install theano pygpu` 应该就足够了！

有时建议使用 `conda-forge` 渠道安装 `pygpu`：

`conda install -c conda-forge pygpu`

2) \[适用于 Anaconda Python 或官方 CPython\]

- 从源代码安装 `libgpuarray`：[逐步安装 libgpuarray 用户库](http://deeplearning.net/software/libgpuarray/installation.html#step-by-step-install-user-library)
- 然后，从源代码安装 `pygpu`：（在同一源代码文件夹中）`python setup.py build && python setup.py install`
- `pip install theano`。

安装 **Theano** 后：

```
echo "[global]
device = cuda
floatX = float32

[lib]
cnmem = 1.0" > ~/.theanorc
```

### 安装 Tensorflow

截至目前，`tensorflow` 有两个不同的包，分别是 `tensorflow` 和 `tensorflow-gpu`，分别用于安装仅支持 CPU 或带 GPU 支持的框架。

