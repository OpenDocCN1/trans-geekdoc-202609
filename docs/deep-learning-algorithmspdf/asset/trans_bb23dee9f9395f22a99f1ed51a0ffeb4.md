
16.04 Linux 服务器配备 3.40 GHz i7-3770 CPU（16 GB 内存）和 GTX 1070 GPU（8 GB 显存）。每类 100 个样本被划分为 80 个训练样本和 20 个测试样本。与传统的分类方法相比，深度学习方法的数据预处理要简单得多。本文的网络输入为 RGB 颜色图像。所有 `value` 均除以 255。

**Training Algorithm**

在反向传播阶段，模型参数使用随机梯度下降（SGD）算法进行训练，优化目标为类别交叉熵损失函数。SGD 可表示为：

```
(3)
```

其中 `sensitivity` 表示灵敏度，`multiplicative bias` 表示乘性偏置，`³` 表示层的权重更新，`learning rate` 表示学习率。`+ #` 

本书版权归 Arcler 所有

![Image 848](index-190_1.jpg)

![Image 849](index-190_2.jpg)

![Image 850](index-190_3.png)

![Image 851](index-190_4.png)

![Image 852](index-190_5.png)

Deep Learning Algorithms

164

(4)

其中 `݂` 是 `݆ ݂`。

`݆`

在一些初步训练实验之后，基学习率设为 0.001，并且在每个 epoch 之后逐渐衰减。衰减率为 10\_

动量为 0.9。图 4 展示了 ResNet26 在 40 个 epoch 后的训练过程。

**Figure 4**

本书版权归 Arcler 所有

![Image 853](index-191_1.jpg)

![Image 854](index-191_2.png)

![Image 855](index-191_3.png)

![Image 856](index-191_4.png)

Deep Learning Algorithms

165

与更大的模型相比，ResNet26 在 SGD 优化过程中收敛快且稳健，能够避免过拟合或陷入局部最小值。

**RESNET26 ON FLAVIA DATASET**

为展示拟议的 ResNet26 模型的有效性，已在公开的 Flavia 叶片数据集上进行了一系列实验。部分样本如图 6 所示。我们随机选取 80% 的数据用于训练，20% 用于测试。

`value` 除以数据的最大值后，再减去数据的均值。

训练算法与应用于 BJFU100 数据集的算法完全相同。图 7 展示了 ResNet26 模型的训练过程。

epochs.

测试集的每个模型准确率通过 10‑fold 跨折验证估计，如图 8 可视化。ResNet18、ResNet34 和 ResNet50 的测试准确率分别为 99.44%、98.95% 和 98.60%。拟议

to 0.21%。表 1 汇总了我们的结果以及以往在 Flavia 叶片数据集上发表的结果。拟议的 ResNet26 模型相较于最佳方法提升了 0.28%。

**Figure 6**

本书版权归 Arcler 所有

![Image 857](index-192_1.jpg)

![Image 858](index-192_2.png)

![Image 859](index-192_3.png)

![Image 860](index-192_4.png)

Deep Learning Algorithms

166

**Figure 7**

**CONCLUSION**

首款移动设备获取了包含 10,000 张 100 种植物物种图像的 BJFU100 数据集，为进一步的植物识别研究提供了数据基石。我们继续通过更广泛的物种覆盖和季节变化来扩展 BJFU100 数据集。该数据集面向学术界开放，可在 http://pan.baidu.com/s/1jILsypS 下载。本文还研究了深度学习方法，自动发现分类所需的特征表示，实现统一的端到端管道用于在自然环境中识别植物。拟议的 ResNet26 模型在测试集上达到 91.78% 的准确率，表明深度学习是大规模自然环境下植物分类的有前途的技术。

未来工作中，BJFU100 数据库将进一步扩展至更多生命周期阶段的植物种类以及更细致的标注。

深度学习模型预测、昆虫检测、病害分割等。

本书版权归 Arcler 所有

![Image 861](index-193_1.jpg)

![Image 862](index-193_2.png)

![Image 863](index-193_3.png)

![Image 864](index-193_4.png)

![Image 865](index-193_5.png)

**Figure 8**

首款移动设备获取了包含 10,000 张 100 种植物物种图像的 BJFU100 数据集，为进一步的植物识别研究提供了数据基石。我们继续通过更广泛的物种覆盖和季节变化来扩展 BJFU100 数据集。该数据集面向学术界开放，可在 http://pan.baidu.com/s/1jILsypS 下载。本文还研究了深度学习方法，自动发现分类所需的特征表示，实现统一的端到端管道用于在自然环境中识别植物。拟议的 ResNet26 模型在测试集上达到 91.78% 的准确率，表明深度学习是大规模自然环境下植物分类的有前途的技术。

未来工作中，BJFU100 数据库将进一步扩展至更多生命周期阶段的植物种类以及更细致的标注。

深度学习模型预测、昆虫检测、病害分割等。

