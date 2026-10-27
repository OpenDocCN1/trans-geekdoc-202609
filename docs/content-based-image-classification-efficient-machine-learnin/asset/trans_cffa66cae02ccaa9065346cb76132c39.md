
- 3. Das, R., Thepade, S. and Ghosh, S., 2016. 基于标准化多视角特征的内容型图像识别框架. *ETRI Journal*, 38 (1): 174–184.
- 4. Liu, C., 2013. 一种新的指静脉特征提取算法. In IEEE 第六届图像与信号处理国际会议 (CISP), pp. 395–399.
- 5. Ramírez-Ortegón, M. A. and Rojas, R., 2010. 基于局部灰度强度方差的历史文档二值化的无监督评估方法. In Proceedings of the International Conference on Pattern Recognition, pp. 2029–2032.
- 6. Yanli, Y. and Zhenxing, Z., 2012. 一种用于 QR 图像的新颖局部阈值二值化方法. In IET International Conference on Automatic Control and Artificial Intelligence (ACAI), pp. 224–227.
- 7. Shaikh, S. H., Maiti, A. K. and Chaki, N., 2013. 一种使用迭代划分的新图像二值化方法. *Machine Vision and Applications*, 24 (2): 337–350.

## 7. 基于内容特征提取：纹理成分

### 7.1 引言

在图像中以具有某种随机性的重复结构形式出现的常见属性称为 *纹理*。重复模式的基本组成部分被指定为基本原语或 *纹素*。基本原语使用放置规则或均匀性来形成重复模式。在某些图像中，区域的定义特征对于正确分析可能很重要。在纹理分析的帮助下，可以从颜色或强度的空间排列中进行特征提取。一些直方图分布可以具有不同的纹理表示，这可以作为提取不同特征的工具。因此，纹理的存在以重复模式的形式出现，如图 7.1 所示。

![](img/2bc397c57b3b49c1ff177a21ce3b8fc5_150_0.png)

**图 7.1**  
示例纹理模式。  
**来源：** https://upload.wikimedia.org/wikipedia/commons/a/a9/ArtificialTexture.png (根据知识共享许可)。

强度和颜色的变化导致了纹理的形成。纹理对应于定性术语，即在物理层面上粗糙度、均匀性和平滑度。根据原语的大小，纹理分为微纹理和宏观纹理。对象的宏观纹理或粗糙度由原语的大元素定义，而微纹理由较小的纹理形成。纹理元素的方向性被称为方向性。本章介绍了两种利用图像纹理内容进行特征提取的方法，即使用 Linde-Buzo-Gray (LBG) 算法的矢量量化 (VQ) 码本表示进行特征提取，以及通过灰度共生矩阵 (GLCM) 进行特征提取。这些技术提高了基于内容图像分类的速率。在我们的方法中，我们通过使用 LBG 算法从生成的聚类中计算码向量来生成特征。这样生成的码本大小远小于图像尺寸，并用作基于内容图像分类的特征向量。在 GLCM 的情况下，计算每个图像的特征向量时考虑了所有参数即能量、对比度、熵和相关性的均值和标准差。这为每个图像生成 8 个特征大小，该大小与图像尺寸无关，并且具有相当小的占用空间。

### 7.2 使用 Linde-Buzo-Gray (LBG) 算法的矢量量化码本表示进行特征提取

图像的统计颜色分布已由矢量量化 (VQ) 码本 [1] 描述。该技术应用于四个不同的公共数据集，用于从测试图像中提取特征。数据集为 Wang 数据集、OT-Scene 数据集、Corel 数据集和 Caltech 数据集。为了应用矢量量化创建作为特征向量的码本，从测试图像中提取了红色 (R)、绿色 (G) 和蓝色 (B) 等颜色分量。通过矢量量化将 *k* 维欧几里得空间映射到有限子集。码本的表示由有限集 *CB* 完成，如公式 7.1 所示。

$$CB = \{C_i \mid i = 1, 2, \ldots, N\}$$

(7.1)

其中 Ci = (ci1, ci2, ...., cik) 是码向量，N 是码本的大小。

遵循 Linde-Buzo-Gray (LBG) 算法生成码向量。首先，将图像划分为不重叠的块并转换为训练向量 Xi = (xi1, xi2, ... , xik)。训练集中每个训练向量的维度固定为 12。训练向量由 2 × 2 相邻像素的红色、绿色和蓝色分量组成。从此，整个训练集的质心被计算为第一个码向量。此外，通过在质心上加减常数误差生成两个试验码向量 v1 和 v2。计算每个训练向量与试验向量的接近程度，并根据训练向量与 v1 和 v2 的接近程度形成两个聚类，如图 7.2 所示。

![](img/2bc397c57b3b49c1ff177a21ce3b8fc5_151_0.png)

**图 7.2**  
Linde-Buzo-Gray (LBG) 算法的实现。

这通过从两个新形成的聚类中计算两个质心来创建大小为 2 的码本，从而产生两个码向量。上述过程使用质心重复以生成所需的码本大小，本例中为 16。

从四个公共数据集中提取的特征使用四种不同的分类器进行测试，即 K 近邻 (KNN)、Ripple-Down Rule (RIDOR)、人工神经网络 (ANN) 和支持向量机 (SVM)。结果见表 7.1。

**表 7.1**  
使用矢量量化进行特征提取时，使用四个不同公共数据集和四个不同分类器的分类性能

| 数据集 | 指标 | KNN | RIDOR | ANN | SVM |
|---|---|---:|---:|---:|---:|
| Wang | 精确率 | 0.900 | 0.900 | 0.928 | 0.888 |
| Wang | 召回率 | 0.890 | 0.900 | 0.925 | 0.869 |
| Wang | 误判率 | 0.042 | 0.039 | 0.038 | 0.043 |
| Wang | F1 分数 | 0.884 | 0.900 | 0.925 | 0.862 |
| OT-Scene | 精确率 | 0.923 | 0.922 | 0.937 | 0.860 |
| OT-Scene | 召回率 | 0.919 | 0.922 | 0.936 | 0.860 |
| OT-Scene | 误判率 | 0.038 | 0.039 | 0.036 | 0.044 |
| OT-Scene | F1 分数 | 0.923 | 0.922 | 0.937 | 0.856 |
| Corel | 精确率 | 0.703 | 0.713 | 0.820 | 0.545 |
| Corel | 召回率 | 0.658 | 0.668 | 0.819 | 0.499 |
| Corel | 误判率 | 0.057 | 0.073 | 0.046 | 0.091 |
| Corel | F1 分数 | 0.700 | 0.660 | 0.819 | 0.468 |
| Caltech | 精确率 | 0.725 | 0.781 | 0.863 | 0.714 |
| Caltech | 召回率 | 0.725 | 0.777 | 0.864 | 0.712 |
| Caltech | 误判率 | 0.057 | 0.053 | 0.042 | 0.066 |
| Caltech | F1 分数 | 0.707 | 0.778 | 0.862 | 0.714 |

> **观察：** 四个数据集均在 ANN 分类器上获得最大分类结果。

### 7.3 代码示例 (MATLAB®)

```matlab
%% Read an Image
i=imread('path\imagefile');

%% Separate the Color Components
r=i(:,:,1); % red component
[m n p]=size(r); % dimension of red component
g=i(:,:,2); % green component
[x y z]=size(g); % dimension of green component
b=i(:,:,3); % blue component
[j k l]=size(b); % dimension of blue component

%% Computing Trial Code Vector
Thr=mean2(r);
meanr1=Thr+1; % Trial code vector 1 for red component
meanr2=Thr-1; % Trial code vector 2 for red component
Thg=mean2(g);
meang1=Thg+1; % Trial code vector 1 for green component
meang2=Thg-1; % Trial code vector 2 for green component
Thb=mean2(b);
meanb1=Thb+1; % Trial code vector 1 for blue component
meanb2=Thb-1; % Trial code vector 2 for blue component

%% Sample Code for Codebook Representation from Red Component
for a1=1:m
for a2=1:n
sub1=abs(meanr1-r(a1,a2));
sub2=abs(meanr2-r(a1,a2));
if sub1>sub2
c1=c1+1;
arr1(c1,1)=r(a1,a2);
end
if sub1<=sub2
c2=c2+1;
arr2(c2,1)=r(a1,a2);
end
end
end
```
