

## Jetson TX2

Jetson TX2 是 NVIDIA 提供的专门用于高效 AI 计算的嵌入式设备。Jetson TX2 重量轻、结构紧凑，因此适合部署在无人机、公共场所等。它还预装了 TensorRT，这是 TensorFlow 的一个运行时。你可以在安装 TensorFlow 之前使用 Jetson 并安装 Ubuntu、CUDA 和 CUDNN。克隆 https://github.com/jetsonhacks/installTensorFlowTX2 并在命令提示符中输入以下命令。

- 1. 首先，借助以下代码安装前提条件：
  ./installPrerequisites.sh
- 2. 现在，使用以下代码克隆 TensorFlow：
  ./cloneTensorFlow
- 3. 接下来，使用以下代码设置所需的环境变量：
  ./setTensorFlowEV
- 4. 现在我们将使用以下代码构建 TensorFlow：
  ./buildTensorFlow.sh
- 5. 现在我们将使用以下代码将包处理为 wheel 文件：
  ./packageTensorFlow.sh
- 6. 现在我们将使用以下代码安装 TensorFlow：
  `pip install $HOME/tensorflow-1.0.1-cp27-cp27mu-linux_aarch64.whl`

通过这些步骤，我们可以在 Jetson TX2 上安装 TensorFlow。

## Android

任何应用都可以使用 TensorFlow，构建的细节可以在 https://www.tensorflow.org/mobile/android_build 查找到。关于 tree/ 的官方示例可以在 https://github.com/tensorflow/tensorflow/tree/master/tensorflow/examples/android 找到。假设读者具有 Android 编程经验，在 Android 设备上实现 TensorFlow 的步骤如下：

- 使用第 3 节“图像检索”中涵盖的步骤将 TensorFlow 模型导出为 .pb 文件。
- 构建作为二进制文件的 .so 和 .jar 文件。
- 编辑 gradle 文件以启用库的加载。
- 加载并运行 Android 应用文件。

## iPhone

Apple 使用 CoreML 框架将机器学习集成到 iPhone 应用程序中。Apple 提供了一个标准模型列表，可以直接集成到应用程序中。你可以使用 TensorFlow 训练自定义深度学习模型并在 iPhone 上使用它们。为了部署自定义模型，你必须将 TensorFlow 转换为 CoreML 框架模型。Google 发布了 https://github.com/tf-coreml/tf-coreml 用于将 TensorFlow 模型转换为 CoreML 模型。可以使用以下代码安装 TForeML：

```
pip install -U tf-coreml
```

可以使用以下代码导出模型：

```python
import tfcoreml as tf_converter
tf_converter.convert(tf_model_path='tf_model_path.pb',
                    mlmodel_path='mlmodel_path.mlmodel',
                    output_feature_names=['softmax:0'],
                    input_name_shape_dict={'input:0': [1, 227, 227, 3]})
```

导出的模型可以被 iPhone 用于预测。

## 总结

在本章中，我们学习了如何在各种平台和设备上部署训练好的深度学习模型。我们涵盖了步骤，以及关于在这些平台上获得最佳性能的指南。我们看到了 MobileNets 的优点，它以较小的精度为代价减少了推理时间。

## 你可能感兴趣的其他书籍

如果你喜欢这本书，你可能对 Packt 出出的其他书籍感兴趣：

![](img/48c861eac4dc634fbf2a09fdbe884beb_293_0.png)

## TensorFlow 1.x 深度学习食谱

Antonio Gulli, Amita Kapoor

ISBN: 978-1-78829-359-4

- 安装 TensorFlow 并将其用于 CPU 和 GPU 操作
- 实现 DNN 并应用它们解决不同的 AI 驱动问题
- 利用 TensorFlow 利用不同的数据集（如 MNIST、CIFAR-10 和 Youtube8m），并学习如何在代码中访问和使用它们。
- 使用 TensorBoard 理解神经网络架构，优化学习过程，并窥探神经网络的内部。
- 使用不同的回归技术解决预测和分类问题。
- 在 TensorFlow 中构建单层和多层感知器。

## 你可能感兴趣的其他书籍

![](img/48c861eac4dc634fbf2a09fdbe884beb_294_0.png)

## 使用 Keras 进行深度学习

Antonio Gulli, Sujit Pal

ISBN: 978-1-78712-842-2

- 使用反向传播算法逐步优化大型神经网络上的函数
- 微调神经网络以提高结果质量
- 使用深度学习进行图像和音频处理
- 使用递归张量网络 (RNTNs) 在特殊情况下优于标准词嵌入
- 识别适用于循环神经网络 (RNN) 解决方案的问题
- 探索实现自动编码器所需的流程
- 使用强化学习演化深度神经网络

## 发表评论 - 让其他读者知道你的想法

请通过在你购买书籍的网站上发表评论，与其他分享你对这本书的看法。如果你是从 Amazon 购买的手籍，请在该书的 Amazon 页面上给我们留下诚恳的评论。这至关重要，因为其他潜在读者可以查看并使用你的无偏意见做出购买决策，我们可以了解客户对我们产品的看法，我们的作者也可以看到他们与 Packt 合作创作的作品的反馈。这只需要你花几分钟时间，但对其他潜在客户、我们的作者和 Packt 来说非常有价值。感谢！

## 索引

# 3

3D 卷积网络 240
3D 模型
从照片创建 213

# A

- 激活 215
激活函数
关于 7
双曲正切函数 9
修正的线性单元 (ReLU) 10
smoid 8
实际激活的层 216
对抗样本 89
对抗损失 229, 230
仿射变换 65
AlexNet 模型 58
算法
定位 112
物体定位，滑动窗口 112
回归 115
Amazon Machine Images (AMI) 266
Amazon Web Services (AWS) 25, 266, 271
Android 277
动画字符
创建 212, 213
近似最近邻 oh yeah (ANNO)
关于 99
优点 100
人工神经网络 (ANN)
关于 6, 11
反向传播 14
批归一化 13
交叉熵 12
dropout 15
L1 正则化 14
L2 正则化 14
独热编码 12
随机梯度下降 (SGD)
空洞卷积 136
注意力机制 240
注意力机制
关于 96
基于注意力的图像字幕
注意力网络
注意力 196
注意力技术 70
属性
关于 70
通道偏移 67
翻转 70
归一化 70
随机裁剪 67
旋转 70
倾斜 70
白化 70
缩放 70
编码器
平均池化 215
AWS 深度学习 (DL) 266

# B

混合 209
自夸 252
瓶颈特征
训练 71, 72
瓶颈层 101

# C

加拿大高级研究协会 
字幕
从图像检索 191
字符 182
CIFAR 数据集 54, 55
云机器引擎 275
云
Amazon Web Services (AWS) 266, 268, 271
Google Cloud Platform (GCP) 275
CNN 特征 253
COCO物体检测挑战 109
上下文中的物体 (COCO) 109
竞赛 57
计算机断扫描 (CT) 131
计算机统一设备架构 (COCO) 266
条件 GAN 229
条件随机场 (CRF) 141
关于 18
用于链接图像 186
用于链接文本 186
连接层
训练，作为卷积层 113
内容损失 214, 215, 216, 217, 218
基于内容的图像检索 (CBIR)
关于 94
自动编码器，用于图像去噪 102
高效检索 98
几何验证 95
局部敏感哈希 (LSH) 94
多索引哈希 94
查询扩展 95
相关性反馈 98
构建流水线 95
上下文流 242
卷积实现
滑动窗口 114
卷积神经网络 (CNN)
关于 17, 240
卷积 17
最大池化 18
交叉熵 12
CUDA 深度神经网络 (CUDNN)
关于 28
用于下载 208
CUDA 库
用于下载 27

# D

数据
准备 67, 68
数据集 133
关于 181, 239
数据增强 70
增强 69
COCO物体检测挑战 109
评估，使用的指标 110
探索 108
ImageDataset 109
交并比 (IoU) 110
平均平均精度 111
PASCAL 挑战 109
解码器 101
反卷积 137
深度学习模型
关于 58
AlexNet 模型 58
-DenseNet 模型 65, 66
Google Inclusion-V3 模型 60, 62, 63
Microsoft ResNet-50 模型 63
MobileNets 262
参数 264
性能 261
量化 262
空间变换网络 765
SqueezeNet 模型 63, 64
VGG-16 模型 59
深度学习
关于 6
激活函数 7
人工神经网络 (ANN) 11

