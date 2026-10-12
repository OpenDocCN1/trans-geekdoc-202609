

## 7.3.3 图像清洗

典型的伽马射线簇射不会覆盖整个相机。在图像清洗步骤中，会选取一部分可能包含切伦科夫信号的像素。该选择基于提取步骤中获得的图像值，假设包含信号的像素比仅包含噪声的像素更亮。此外，正如簇射发展所显示的那样，信号像素在到达时间方面也需要是相关的。完整的图像清洗通常由以下步骤的某种组合构成：

1.  选择电荷高于特定阈值的像素
2.  移除选中邻居像素数少于给定值的像素
3.  如果相邻于已选中像素，则选择电荷高于第二个（较低）阈值的像素
4.  移除在相似时间到达的选中邻居像素数少于给定值的像素

作为该步骤的结果，不太可能包含切伦科夫信号的像素被丢弃，后续分析步骤仅聚焦于图像的选中部分。[图 7.5](#9783110785951_015782.xhtml#b_9783110785968-007_fig_005) 通过在完整（光子计数）图像上构建掩码，展示了信号像素的选择。

![Fig. 7.5: Zoomed-in view of a recorded Cherenkov image showing pixels in the vicinity of the Cherenkov signal. Out of the full image, a subset of pixels with high photon counts is selected (white border).](graphic/b_9783110785968-007_fig_005.png)

**图 7.5：** 已记录切伦科夫图像的局部放大视图，显示切伦科夫信号附近的像素。从完整图像中，选取了一部分光子计数高的像素（白色边框）。

## 7.3.4 图像参数化

与强子主粒子产生的簇射图像相比（强子主粒子构成了伽马射线数据分析中的主要本底类别），伽马射线产生的簇射图像相当均匀，呈单团块状，并沿簇射方向拉长。为了参数化这些特性，迈克尔·希拉斯在为第一台成像大气切伦科夫望远镜（IACT）——惠普尔望远镜 [[199]](#9783110785951_034588.xhtml#b_9783110785968-011_ref_199) 工作时，引入了一组特征。他最初的参数集随着时间的推移得到了扩展。然而，经典参数集仍在常规使用，并被认为是在基于现代机器学习的分析中也最重要的特征。希拉斯参数可通过对二维图像执行主成分分析来计算。设 `x[i]` 和 `y[i]` 为焦平面上相机第 `i` 个像素的坐标，`w[i]` 为该像素的光子数，`𝒞` 为图像清洗选出的像素集合。第一个希拉斯参数仅仅是权重之和：

![Fig. 7.6: The classical Hillas features calculated for a simulated gamma-ray event in the FACT camera.](graphic/b_9783110785968-007_fig_006.png)

**图 7.6：** FACT 相机中模拟伽马射线事件计算出的经典希拉斯特征。

![](graphic/b_9783110785968-007_ingr_018.png)

我们首先通过计算各坐标的加权平均值来计算簇射的*重心*（cog）：

![](graphic/b_9783110785968-007_ingr_019.png)

并平移到以重心为原点的坐标系

![](graphic/b_9783110785968-007_ingr_020.png)

现在我们需要计算像素坐标的加权协方差矩阵：

![](graphic/b_9783110785968-007_ingr_021.png)

并相应地计算 `Cov(x, x)` 和 `Cov(y, y)`，从而得到 2 × 2 协方差矩阵 `V`。

作为最后一步，我们计算 `V` 的特征值和特征向量。设 `λ[0]` 为较大的特征值，`λ[1]` 为较小的特征值。我们随后按如下方式计算希拉斯参数长度和宽度：

![](graphic/b_9783110785968-007_ingr_022.png)

它们分别对应于光分布主成分方向上的标准差。

主成分相对于 `x` 轴的旋转角通过对应的特征向量 `v[0]` 获得，通常称为 `δ`：

![](graphic/b_9783110785968-007_ingr_023.png)

特别是对于估计簇射方向，沿主成分计算偏度和峰度很有帮助。通常，也会在旋转后的坐标系中对到达时间执行线性回归。清单 7.1 展示了一个计算希拉斯参数的简化 Python 函数。

**清单 7.1：** 给定像素坐标和图像计算希拉斯参数的简化 Python 代码。该代码不处理 size = 0 或 width = 0 等边缘情况，也不计算主轴方向上的高阶矩。改编自 ctapipe [[296]](#9783110785951_034588.xhtml#b_9783110785968-011_ref_296)。

```python
import numpy as np

def hillas(pixel_x, pixel_y, image):
    '''Calculate hillas parameters'''
    size = np.sum(image)

    cog_x = np.average(pixel_x, weights=image)
    cog_y = np.average(pixel_y, weights=image)
    
    delta_x = pixel_x - cog_x
    delta_y = pixel_y - cog_y
    
    cov = np.cov(delta_x, delta_y, aweights=image)
    
    # eigh assumes a hermitian matrix (here real and symmetric)
    # and guarantees the order of the eigenvalues
    eig_vals, eig_vecs = np.linalg.eigh(cov)
    width, length = np.sqrt(eig_vals)
    
    delta = np.arctan(eig_vecs[1, 1] / eig_vecs[0, 1])
    
    return size, cog_x, cog_y, length, width, delta
```

可以计算描述图像形态的附加特征。这包括选中像素集合中的像素组数量、相机边缘处的光量比例，以及图像某些区域的光量相对于 size 的比例，例如椭圆内的光量比例，该椭圆的半长轴为长度和宽度，如[图 7.6](#9783110785951_015782.xhtml#b_9783110785968-007_fig_006)所示。

## 7.4 通过数据摘要监测望远镜

*Sebastian Buschjäger*

