
基于深度迁移学习的高光谱图像分类过程如图 7 所示。

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_198_0.png)

图 7. 基于深度迁移学习的高光谱图像分类过程。

## 5. 最优邻域去噪方法

为了降低初始分类结果中的椒盐噪声，本文提出了一种基于八邻域模式标签的最优邻域去噪方法。利用最优邻域去噪方法对高光谱图像的初始分类结果进行再处理。在该方法中，以高光谱图像分类标签数据作为输入，将中心像素标签与其八邻域像素的标签进行比较。

若用 L(i,j) 表示高光谱图像中中心像素 P(i,j) 的分类结果标签，则中心像素 P(i,j) 及其八邻域像素的类别标签如图 8 所示。

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_199_0.png)

图 8. 中心像素及其八邻域像素的类别标签。

如图 8 所示，基于对高光谱图像所有像素标签的遍历，将一个中心像素 P_(i,j) 的类别标签 L_(i,j) 与其八邻域像素的类别标签组合成一个 3×3 矩阵。将 3×3 矩阵转换为 1×9 一维向量。然后计算九个标签的众数 M 以及众数标签的数量 m。阈值设为 N（0 ≤ N ≤ 9），且不需要分类的高光谱图像像素标签设为 0。当满足以下条件时，中心像素被认为是有噪声的：中心像素的类别标签 L_(i,j) 不等于九个像素标签的众数，众数标签不为 0，且众数标签的数量 m ≥ N。由于标签 0 表示像素不需要分类，因此排除值为 0 的众数标签以避免边缘误判。如果中心像素 P_(i,j) 被确认有噪声，则用八邻域像素的众数标签替换它。阈值 N 的初始值通常设为 5。当中心像素标签 L_(i,j) 不等于九个像素的众数标签时，众数标签不为 0，且众数标签的数量 m ≥ 5，中心像素被认为是有噪声的。阈值 N 可根据实际情况进行修改。如果阈值过大，去噪效果可能不明显；如果阈值过小，实际信息可能被误判为噪声。

最优邻域去噪过程的伪代码如下所示：

```
Input: The classification result dataset X of the hyperspectral image, the label of 0 for the pixels that do not need to be classified, and the threshold N=5
Output: The noise-reduced classification result data set X of the hyperspectral image and classified image with noise reduction.
Load classification result dataset X
for i=1; i< X.shape[0]; i++
for j=1; j<X.shape[1]; j++
loop traversing each pixel label L_(i,j)
Transforming the 3×3 matrix composed of the central pixel label L_(i,j) and its eight neighborhood pixel labels into a 1×9 one-dimensional vector
Calculating the mode M and its number m of central pixel label and the eight neighborhood pixels labels.
if the class label L_(i,j) of the central pixel is not equal to the mode number M of the nine labels
if the mode label is not 0 and the number of the mode label is m≥N
The central pixel P_(i,j) is noise
Replace the central pixel label L_(i,j) with the mode label M to remove the noise
end if
end if
Update the hyperspectral image classification result label L_(i,j) of each pixel P_(i,j)
end loop L_(i,j)
end for
end for
```

## 6. 实验与分析

### 6.1. 数据集

为了验证本文提出的<|message|>方法，实验在具有相似特征的数据集上进行。所选数据集包括 Indian Pines 数据集、Salinas 数据集、Pavia University 数据集和 Pavia Center 数据集。Indian Pines 数据集和 Salinas 数据集均由 AVIRIS 传感器获取。两个数据集校正后的光谱维度分别为 200 和 204，非常接近。真实地物划分为 16 类 [44]。Pavia University 数据集和 Pavia Center 数据集由 ROSIS 传感器采集。这两个数据集校正后的光谱维度分别为 103 和 102，真实地物划分为九类 [45]。数据集可从网站获取 (http://www.ehu.eus/ccwintco/index.php?title=Hyperspectral_Remote_Sensing_Scenes)。

Indian Pines 数据集与 Salinas 数据集相似，Pavia University 数据集与 Pavia Center 数据集相似。此外，前两个数据集的样本量小于后两个数据集。因此，在迁移学习方法中，Salinas 数据集和 Pavia Center 数据集用作源数据集，而 Indian Pines 数据集和 Pavia University 数据集用作相应的目标数据集。首先，从在 Salinas 数据集和 Pavia Center 数据集上的训练中获得并验证浅层网络的结构和参数。然后将获得的结构和参数迁移到样本量相对较小的 Indian Pines 数据集和 Pavia University 数据集。最后对网络的结构和参数进行微调。

Indian Pines 数据集与 Pavia University 数据集之间存在很大差异，可充分验证所提出的分类方法。Indian Pines 数据集样本量小，主要反映植被信息，包括种类丰富且多为规则块状分布，光谱信息丰富且空间分辨率低。Pavia University 数据集图像尺寸大，主要反映城市景观的景观信息。虽然种类较少，但目标形状不规则，空间分辨率高。

### 6.2. 实验与结果分析

### 6.2.1. 降维方法实验

为了测试所提出方法在高光谱图像降维和去噪方面的有效性，对 IM、IM_SPE 方法以及叠加最优邻域去噪方法后的 IM_DN、IM_SPE_DN 方法的分类性能进行了测试，并与基于光谱信息的 CNN 分类方法 SPE [46]、基于空间信息的 CNN 分类方法 PCA1、PCA 第一主成分 [47]、基于光谱信息与空间信息第一主成分融合的 CNN 分类方法 PCA1_SPE 以及基于 PCA 光谱信息前三个主成分的 CNN 分类方法 PCA3 [48] 进行了比较。我们使用 OA、AA 和 Kappa 系数来评估不同方法的性能。

(1) Indian pines 数据集实验

Indian pines 数据集上的分类性能如表 1 所示。从表 1 可以看出，对于 Indian pines 数据集，PCA1_SPE、PCA3、IM 和 IM_SPE 分类方法提供了最佳的分类精度。此外，IM 和 IM_SPE 方法的 OA、AA 和 Kappa 系数优于 SPE、PCA1、PCA1_SPE 和 PCA3 方法，这表明基于信息测度的分类方法（IM 和 IM_SPE）比基于光谱信息的分类方法（SPE）和基于 PCA 的分类方法（PCA1、PCA1_SPE 和 PCA3）性能更好。在所有分类方法中，IM_DN 和 IM_SPE_DN 方法具有最佳的 OA、AA 和 Kappa 系数，这是由于基于降维的
