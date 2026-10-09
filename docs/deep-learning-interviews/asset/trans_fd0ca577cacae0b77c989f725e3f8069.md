

. 在现有功能之上创建一个顺序模块。

```python
import torchvision.models as models
res_model = models.resnet34(pretrained=True)
class ResNetBottom(torch.nn.Module):
    def __init__(self, original_model):
        super(ResNetBottom, self).__init__()
        self.features = [???]
    def forward(self, x):
        x = [???]
        x = x.view(x.size(0), -1)
        return x
```

![](img/574135cb1d7125b50cf484d943cdd676_232_0.png)

### SOL-168 / CH.SOL-7.12

- 变换被整合到深度学习中，以便对表示为张量的图像应用一个或多个操作。训练和推理期间通常会使用不同的变换。例如，在训练期间，我们可以使用变换来增强数据集；而在推理期间，我们的变换可能仅限于图像归一化。PyTorch 允许在训练或推理期间使用 `transforms`。第 5 行中 `test_trans` 的目的是归一化数据。
- 第 14 行中的参数 `requires_grad` 被设置为 False，因为在推理期间，梯度的计算是多余的。
- 第 11 行中 `f.cpu()` 的目的是将分配在 GPU 上的张量移动到 CPU。如果我们希望对驻留在 CPU 之外的 Tensor 应用 Python numpy 包中的基于 CPU 的方法，可能需要这样做。
- 第 23 行中的 `detach()` 返回一个新创建的张量，而不影响当前张量。它还将输出从当前计算图中分离出来，因此不会对该特定变量进行梯度反向传播。
- 第 23 行中 `numpy()[0]` 的目的是将变量（数组）转换为兼容 numpy 的变量，并获取数组的第一个元素。

## 7.3.2 CNN 的微调

### SOL-169 / CH.SOL-7.13

预训练 ImageNet CNN 的微调（FT）术语指的是通过在新目标数据集上重新训练 CNN 的一个或多个权重的方法，该目标数据集可能与 ImageNet 数据集相似，也可能不相似。

### SOL-170 / CH.SOL-7.14

这三种方法如下：
1. 在目标数据集上替换并重新训练 ImageNet 预训练 CNN 的 **仅分类器**（通常是全连接层）。
2. 在目标数据集上微调 ImageNet 预训练 CNN 的 **所有层**。
3. 在目标数据集上微调 ImageNet 预训练 CNN 的 **部分层**。

### SOL-171 / CH.SOL-7.15

1. 类别必须用数字表示。代码 (7.1) 中提供了一种这样的选项。

```
1    'MEL':0,'NV':1,'BCC':2,'AKIEC':3,'BKL':4,'DF':5, 'VASC': 6
```
代码 7.1：七种皮肤病变类别。

2. 代码 (7.2) 中提供了几种可能的数据增强方法。通常通过试错法可以找到目标数据集的最佳增强方法。然而，AutoAugment 等方法可能使手动选择增强方法变得多余。

```python
1  self.transforms = []
2  if rotate:
3      self.transforms.append(RandomRotate())
4  if flip:
5      self.transforms.append(RandomFlip())
6  if brightness != 0:
7      self.transforms.append(PILBrightness())
8  if contrast != 0:
9      self.transforms.append(PILContrast())
10 if colorbalance != 0:
11     self.transforms.append(PILColorBalance())
12 if sharpness != 0:
13     self.transforms.append(PILSharpness())
```
代码 7.2：数据增强的伪代码。

3. 与以全连接层结束的 ResNet CNN 不同，ImageNet 预训练的 DPN CNN 家族（在本例中为 pretrainedmodels.dpn107）以一个 Conv2d 层结束，因此，如果希望将类别数从 1000 类（ImageNet）改变为我们的皮肤病变分类问题（7 类），则必须相应地调整。代码 (7.3) 中的第 7 行展示了这种惯用做法。

```python
import torch
```

```python
class Dpn107Finetune (nn.Module):
    def __init__ (self, num_classes:int, net_kwargs):
        super().__init__()
        self.net=pretrainedmodels.dpn107(**net_kwargs)
        self.net.__name__=str(self.net)
        self.net.classifier=torch.nn.Conv2d(2688,
        num_classes,kernel_size=1)
        print(self.net)
```
代码 7.3：将 ImageNet 预训练的 DPN CNN 家族从 1000 类改为 7 类。

## 7.3.3 神经风格迁移

### SOL-172 / CH.SOL-7.16
*这些图像包括：一张内容图像、一张风格图像，以及最后一张组合图像。*

### SOL-173 / CH.SOL-7.17
*论文中提出的算法建议如何使用 CNN 将第一张图像的内容与第二张图像的风格结合，以生成第三张风格化图像。*

### SOL-174 / CH.SOL-7.18
*答案如下：*
1. *训练管道使用由风格损失和内容损失的加权平均组成的组合损失。*
2. *利用不同层级的不同 CNN 层来捕获精细的风格细节以及较大的风格特征。*

### SOL-175 / CH.SOL-7.19
- 内容损失是均方误差（MSE），计算为内容图像和风格图像最后卷积层的 CNN 激活值之间的差值。
- 风格损失将多个层的损失聚合在一起：对于每一层，获得该层激活值的 Gram 矩阵（见 7.2）（针对风格图像和组合图像）。然后，与内容损失一样，计算 Gram 矩阵的 MSE。

# 第 8 章
## 深度学习

> *重要的是权重，而非实验的数量*。
> — 艾萨克·牛顿。

## 目录

- **简介**
- **问题**
    - 交叉验证
        - 交叉验证方法
        - K 折交叉验证
        - 分层抽样
        - 留一法交叉验证 (LOOCV)
    - 卷积和相关
        - 卷积算子
        - 相关算子
        - 填充和步长
        - 核和滤波器
        - Python 中的卷积和相关
        - 可分离卷积
    - 相似度度量
        - 图像、文本相似度。
        - 杰卡德相似度
        - 库拉伯莱克距离
        - MinHash
- **感知机**
    - 单层感知机
    - 多层感知机
    - 感知机中的激活函数
    - 感知机中的反向传播
    - 感知机理论
    - 学习逻辑门
- **激活函数（整流）**
    - Sigmoid
    - Tanh
    - ReLU
    - Swish
- **性能指标**
    - 混淆矩阵、精确率、召回率
    - ROC-AUC
- **神经网络层、拓扑结构、块**
    - CNN 算术
    - Dropout
    - 卷积层
    - 池化层
    - 最大池化
    - 批归一化、高斯 PDF
    - 高斯分布
    - BN
    - CNN 设计理论
    - CNN 残差块
- **训练、超参数**
    - 超参数优化
    - 标签和偏差
    - 验证曲线 ACC
    - 验证曲线 Loss
- **推理**
    - 优化、损失
        - 随机梯度下降，SGD
        - 动量
        - 范数，L1，L2

# 解决方案

- **交叉验证**
    - 交叉验证方法
    - K 折交叉验证
    - 分层抽样
    - 留一法交叉验证 (LOOCV)
- **卷积和相关**
    - 卷积算子
    - 相关算子
    - 填充和步长
    - 核和滤波器
    - Python 中的卷积和相关
    - 可分离卷积
- **相似度度量**
    - 图像、文本相似度。
    - 杰卡德相似度。
    - 库拉伯莱克距离
    - MinHash
- **感知机**
    - 单层感知机
    - 多层感知机
    - 感知机中的激活函数
    - 感知机中的反向传播
    - 感知机理论
    - 学习逻辑门
- **激活函数（整流）**
    - Sigmoid
    - Tanh
    - ReLU
    - Swish
- **性能指标**
    - 混淆矩阵、精确率、召回率
    - ROC-AUC
- **神经网络层、拓扑结构、块**
    - CNN 算术
    - Dropout
    - 卷积层
    - 池化层
    - 最大池化
    - 批归一化、高斯 PDF
    - 高斯分布
    - BN
    - CNN 设计理论
    - CNN 残差块
- **训练、超参数**
    - 超参数优化
    - 标签和偏差
    - 验证曲线 ACC
    - 验证曲线 Loss
    - 推理
- **优化、损失**
    - 随机梯度下降，SGD
    - 动量
    - 范数，L1，L2

