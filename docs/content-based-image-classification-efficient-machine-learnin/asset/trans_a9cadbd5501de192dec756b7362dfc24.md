
(B)—作为来自图像的块。此后，用于特征提取的颜色团的计算在 RGB 颜色空间中采用 Wang 数据集进行。

逐步特征提取指南如下：

- 颜色团计算始于对各个颜色分量的灰度值进行近似，以形成对应分量的灰度值的不相交子集。
- 接下来是对强度值进行逻辑分区，形成众多颜色团的子划分，这涉及为每个 R、G 和 B 颜色分量进行多个阶段的颜色箱形成。
- 分区数量的增加以 2 的倍数形式制定，如图 3.4 所示。
- 分区在 2 到 32 的范围内进行评估，以确定特征向量提取合适的团数量。
- 特征提取的五个阶段分别命名为 2 个颜色团的 BTC、4 个颜色团的 BTC、8 个颜色团的 BTC、16 个颜色团的 BTC 和 32 个颜色团的 BTC。
- 每个颜色团中特定分区的全部灰度值都与该分区灰度值的均值进行比较。
- 该过程最终创建两个不同的强度组，分别具有大于均值阈值的值和小于均值阈值的值。
- 计算对应团的平均上强度和平均下强度值。

因此，可以从特定团中计算出两个不同的高强度和低强度特征值。这使得特征向量的数量是所选颜色团数量的两倍（图 3.2）。

![](img/2bc397c57b3b49c1ff177a21ce3b8fc5_57_0.png)

图 3.2
每个颜色的颜色团分布及特征向量 (fv)。

## 3.4 代码示例（MATLAB®）

```matlab
#Read an image
i=imread('path\imagefile');
#Separate the color components
i1=i(:,:,1); #red component
[m n p]=size(i1); #dimension of red component
i3=i(:,:,2); #green component
[x y z]=size(i3); #dimension of green component
i6=i(:,:,3); #blue component
[j k l]=size(i6); #dimension of blue component

#Computing the means of different color clumps for red component
for a1 = 1:m #for loop for row/column iteration of red component
for a2 = 1:n
if i1(a1,a2)>=0 && i1(a1,a2)<32 #specifying the first clump range
c1=c1+1;
s1=s1+i1(a1,a2); #summing up intensity values of first clump
end
end
end
if c1~=0
TavR1 = s1/c1; #calculating mean threshold for clump
else
TavR1=0; #mean threshold 0 if no intensity values fall in clump range
end
for a3 = 1:m #for loop for row/column iteration of red component
for a4 = 1:n
if i1(a3,a4)>=32 && i1(a3,a4)< 64 #specifying the second clump range
c2=c2+1; #summing up intensity values of second clump
s2=s2+i1(a3,a4);
end
end
end
if c2~=0
TavR2 = s2/c2; #calculating mean threshold for clump
else
TavR2 = 0; #mean threshold 0 if no intensity values fall in clump range
end
for a5 = 1:m #for loop for row/column iteration of red component
for a6 = 1:n
if i1(a5,a6)>=64 && i1(a5,a6)< 96 #specifying the third clump range
c3=c3+1;
s3=s3+i1(a5,a6); #summing up intensity values of third clump
end
end
end
if c3~=0
TavR3 = s3/c3; #calculating mean threshold for clump
else
TavR3 = 0; #mean threshold 0 if no intensity values fall in clump range
end
for a7 = 1:m #for loop for row/column iteration of red component
for a8 = 1:n
if i1(a7,a8)>=96 && i1(a7,a8)< 128 #specifying the fourth clump range
c4=c4+1;
s4=s4+i1(a7,a8); #summing up intensity values of fourth clump
end
end
end
if c4~=0
TavR4 = s4/c4; #calculating mean threshold for clump
else
TavR4=0; #mean threshold 0 if no intensity values fall in clump range
end

#Feature Vector Extraction from color clumps
for a25=1:m
for a26=1:n
if i1(a25,a26)>=TavR1 #finding intensity values higher than mean threshold
c13=c13+1;
s13=s13+i1(a25,a26); #summing up high-intensity values
end
end
end
if c13~=0
upR1=s13/c13; #calculating mean high intensity as feature vector
else
upR1=0;
end
for a27=1:m
for a28=1:n
if i1(a27,a28)<TavR1 #finding intensity values lower than mean threshold
c14=c14+1;
s14=s14+i1(a27,a28); #summing up low-intensity values
end
end
end
if c14~=0
loR1=s14/c14; #calculating mean low intensity as feature vector
else
loR1=0;
end
```

## 3.5 编程练习

前面的代码示例用于为红色分量设计 16 个团。请参考示例完成以下任务：

- 为绿色和蓝色分量设计团来计算均值
- 生成维度为 4、8、16、32 和 64 的特征向量

分类性能的比较结果显示，在所述方法中使用 16 个团时 Precision 和 Recall 值最大。这为每个颜色分量提供了维度为 32 的特征向量，三种颜色分量总计为 96，用于形成与图像尺寸无关的特征向量。

表 3.1 中结果的初步比较采用了名为误分类率（MR）和 F1 分数 的指标。颜色团的数量用 N 表示，Wang 数据集被视为使用 KNN 分类器进行分类的测试平台。

实验观察如下：

- MR 随 N 增加至 16 而下降，F1 分数随之上升。
- 记录的最低 MR 为 N = 16 时的 0.050，随后的最高 F1 分数为 0.728。
- 两个观察结果表明，在强度值的 N = 16 子集之前分类性能更高。
- N 进一步提升至 N = 32 时，F1 分数下降至 0.56，MR 上升至 0.099。
- 因此，工作中设计的团数量限制为 16。

此后，计算各种指标的平均值，以观察使用四种不同分类器——即 KNN、Ripple-Down Rule（RIDOR）、人工神经网络（ANN）和支持向量机（SVM）——对来自四个不同公共数据集的颜色团特征提取所使用的分区 N = 16 进行分类时的 Precision、Recall、MR 和 F1-Score。

## 表 3.1 使用 KNN 分类器分类时不同颜色团子集（N）值的误分类率（MR）和 F1 分数比较

| 类别 | 颜色团 N=2 误分类率 | 颜色团 N=2 F1 分数 | 颜色团 N=4 误分类率 | 颜色团 N=4 F1 分数 | 颜色团 N=8 误分类率 | 颜色团 N=8 F1 分数 | 颜色团 N=16 误分类率 | 颜色团 N=16 F1 分数 | 颜色团 N=32 误分类率 | 颜色团 N=32 F1 分数 |
|---|---|---|---|---|---|---|---|---|---|---|
| 部落 | 0.08 | 0.65 | 0.08 | 0.69 | 0.07 | 0.73 | 0.06 | 0.75 | 0.12 | 0.42 |
| 海滩 | 0.08 | 0.6 | 0.08 | 0.61 | 0.08 | 0.56 | 0.08 | 0.59 | 0.16 | 0.4 |
| 哥特式 | 0.13 | 0.42 | 0.14 | 0.46 | 0.14 | 0.44 | 0.13 | 0.48 | 0.17 | 0.13 |
| 建筑结构 | 0.1 | 0.54 | 0.07 | 0.68 | 0.08 | 0.66 | 0.05 | 0.78 | 0.12 | 0.45 |
| 公交车 | 0 | 1 | 0 | 1 | 0 | 0.99 | 0 | 1 | 0 | 1 |
| 恐龙 | 0.06 | 0.72 | 0.05 | 0.76 | 0.05 | 0.79 | 0.07 | 0.7 | 0.09 | 0.58 |
| 大象 | 0.02 | 0.91 | 0.01 | 0.94 | 0.02 | 0.91 | 0.02 | 0.93 | 0.03 | 0.85 |
| 玫瑰 | 0.02 | 0.91 | 0.02 | 0.92 | 0.01 | 0.96 | 0.02 | 0.9 | 0.04 | 0.81 |
| 马 | 0.13 | 0.37 | 0.1 | 0.47 | 0.1 | 0.51 | 0.11 | 0.43 | 0.15 | 0.38 |
| 山脉 | 0.08 | 0.69 | 0.05 | 0.72 | 0.05 | 0.72 | 0.05 | 0.72 | 0.11 | 0.58 |
| 平均值 | 0.07 | 0.681 | 0.06 | 0.725 | 0.06 | 0.727 | 0.059 | 0.728 | 0.099 | 0.56 |

[观察：N = 16 时 KNN 分类器的 F1 分数最高，MR 最低。]

## 表 3.2

使用 BTC 与颜色团进行特征提取时，使用四个不同公共数据集和四个不同分类器的分类性能

| 数据集 | 指标 | KNN | RIDOR | ANN | SVM |
|---|---|---:|---:|---:|---:|
| Wang | 精确率 | 0.741 | 0.654 | 0.914 | 0.715 |
|  | 召回率 | 0.737 | 0.657 | 0.913 | 0.727 |
|  | 误分类率 | 0.059 | 0.079 | 0.038 | 0.066 |
|  | F1 分数 | 0.728 | 0.655 | 0.913 | 0.717 |
| OT-Scene | 精确率 | 0.461 | 0.368 | 0.484 | 0.501 |
|  | 召回率 | 0.45 | 0.36 | 0.479 | 0.494 |
|  | 误分类率 | 0.096 | 0.1 | 0.091 | 0.09 |
|  | F1 分数 | 0.446 | 0.361 | 0.481 | 0.495 |
| Corel | 精确率 | 0.596 | 0.512 | 0.656 | 0.653 |
|  | 召回率 | 0.581 | 0.519 | 0.664 | 0.65 |
|  | 误分类率 | 0.08 | 0.083 | 0.078 | 0.079 |
|  | F1 分数 | 0.584 | 0.515 | 0.658 | 0.637 |
| Caltech | 精确率 | 0.516 | 0.491 | 0.565 | 0.475 |
|  | 召回率 | 0.553 | 0.489 | 0.574 | 0.557 |
|  | 误分类率 | 0.091 | 0.09 | 0.081 | 0.09 |
|  | F1 分数 | 0.484 | 0.489 | 0.568 | 0.484 |

比较结果见表 3.2。

## 3.6 用于基于内容的图像分类的排序块截断编码特征提取

图像处理算法认为噪声会以很大程度污染图像数据，从而对图像数据产生不利影响。大量文献已引入各种降噪技术以减少噪声对图像数据的影响。一种流行技术是分箱方法，该方法广泛用于平滑数据集中排序值的数据 [8]。分箱方法对数据集中值进行排序的逐步功能如下：

- 排序值被划分为箱。
- 通过考虑相邻值来计算排序值的平均值，以对每个箱进行局部平滑。局部平滑对于降噪至关重要。
- 特定箱的对应平均值可用于替换该箱中的每个值。

