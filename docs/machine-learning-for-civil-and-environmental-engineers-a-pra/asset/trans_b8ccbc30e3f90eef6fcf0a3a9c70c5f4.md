

# 设置实际值和预测值向量
predicted<-rf.mod$predicted
actual<-rf.mod$y
```

```
# 应用误差指标 (MAE, RMSE, MSE)
Metrics::mae(actual,predicted) [1] 221.5164
Metrics::rmse(actual,predicted) [1] 765.9959
Metrics::mse(actual,predicted) [1] 586749.7
```

```
# 选择用于模型评估的函数
ACC1<- (100- (mean( abs( (actual - predicted) / predicted)) * 100))
MAE1<- (mean(abs(actual-predicted)))
MSE1<- (sqrt(mean((actual-predicted)^2)))
ACC1
[1] 91.28963
MAE1
[1] 221.5164
MSE1
[1] 765.9959
```

```
# 绘制所有变量的直方图。
names<-names(data)
classes<-sapply(data,class)
for(name in names[classes == 'numeric']) {
+ dev.new()
+ hist(data[,name])
+ }
```

```
# 绘制单个变量的直方图。
hist(data$N.Test...kN.)
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_338_0.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_338_1.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_338_2.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_339_0.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_339_1.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_339_2.png)

```
# 绘制相关矩阵
# 我们从 Spearman 系数开始
m=cor(data, method = "spearman")
corrplot(m, method = "circle")
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_339_3.png)

### Pearson 系数

```
n=cor(data, method = "pearson")
corrplot (n, method ="color",type = "upper",order ="hclust",addCoef.col = "black",
tl.col = "black",tl.srt = 45, diag = FALSE)
```

| | fy.MPa. | L.mm. | t.mm. | D.mm. | N.Test.W. |
|---|---|---|---|---|---|
| fc.MPa. | 0.04 | -0.13 | -0.02 | 0.04 | 0.15 |
| fy.MPa. | | 0.25 | 0.07 | 0.14 | |
| L.mm. | | | 0.2 | 0.11 | |
| t.mm. | | | | 0.54 | |
| D.mm. | | | | | |

```
# 绘制实际值与预测值对比图
plot(x=predicted, y= actual,
+   xlab='Predicted Values',
+   ylab='Actual Values',
+   main='Predicted vs. Actual Values',
+   abline(a=0, b=1))
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_340_0.png)

## 示例 3 [R, 聚类]: 火灾暴露钢筋混凝土柱的分组

本章的最后一个示例将重新探讨我们经过验证的 144 根火灾暴露钢筋混凝土柱数据库。如您现在所知，该数据集具有以下特征：柱宽 W (mm)、钢筋配筋率 r (mm)、柱长 L (mm)、混凝土抗压强度 fc (MPa)、钢材屈服强度 fy (MPa)、通过有效长度系数表示的约束条件、钢筋保护层厚度 C (mm)、主轴方向施加荷载的偏心距 ex (mm)、施加荷载大小 P (kN) 以及耐火极限 FR (min)。我们将在 R 中使用 K-Means 算法。

R 代码如下。

```
# 读取包并导入数据
install.packages ("factoextra")
library (factoextra)
library (ggplot2)
data=read.csv('C:/Fire-exposed RC columns.csv')
data
str(data)
```

```
> data<-read.csv('C:/Fire-exposed RC columns.csv')
> str(data)
```

'data.frame':144 obs. of  10 variables:
$ W..mm.   : int  400 300 300 300 300 300 300 300 300 400 300 ...
$ r....    : num  1.23 1.13 1.13 0.89 0.89 2.18 2.18 2.18 1.01 1.13 ...
$ L..m.    : num  3.9 3.9 3.9 3.9 2.1 3.9 2.1 3.9 3.9 2.1 ...
$ fc..MPa. : int  30 31 33 34 29 29 26 35 30 27 ...
$ fy..MPa. : int  576 493 493 576 576 576 591 576 576 493 ...
$ K        : num  1 1 1 1 1 1 1 1 1 ...
$ C..mm.   : int  25 25 35 25 25 40 25 25 25 35 ...
$ ex..mm.  : int  20 20 20 0 0 20 0 20 20 0 ...
$ P...kN.  : int  1680 300 283 950 1270 425 878 304 1650 620 ...
$ Fire.Resistance...min.: int  34 60 60 61 63 66 69 69 93 97 ...

```
> class(data)
[1] "data.frame"
```

```
# 缩放数据
> datascale<-scale(data)
```

```
# 距离
> data<-dist(data)
```

```
# 计算聚类数量
> fviz_nbclust (datascale,kmeans,method = "wss")+
+ labs(subtitle = "Elbow method")
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_341_0.png)

```
# 应用 K-means
> km.out<-kmeans (datascale,centers = 4, nstart = 100)
> print (km.out)
```

K-均值聚类，包含 4 个簇，大小分别为 41、52、21、30

簇均值：

| 簇 | W..mm. | r.... | L..m. | fc..MPa. | fy..MPa. | K | C..mm. | ex..mm. | P...kN. | Fire.Resistance...min. |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | -0.58816748 | 0.3632995 | 1.0970154 | -0.6069824 | 0.17061466 | 0.8754232 | -0.2627539 | 0.7231413 | -0.6074518 | -0.8570342 |
| 2 | 0.14500064 | 0.2378114 | -0.5394692 | -0.2836764 | 0.04889508 | -0.8493650 | 0.8523465 | -0.3422011 | -0.1753219 | 0.7594055 |
| 3 | -0.05081353 | -1.5800615 | -0.6040576 | -0.6289227 | 1.33564901 | 1.0005561 | -1.7558265 | -0.1419463 | -0.5347535 | -0.6370031 |
| 4 | 0.58806392 | 0.1973272 | -0.1413342 | 1.7614943 | -1.25287914 | -0.4245683 | 0.1107749 | -0.2957821 | 1.5084029 | 0.3008794 |

聚类向量：
[1] 3 3 3 3 3 1 3 3 3 3 3 3 3 3 3 3 3 3 3 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2
[37] 2 2 2 2 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1
[73] 1 1 1 1 1 1 1 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2
[109] 2 3 4 4 4 4 4 4 4 4 4 4 4 1 4 4 4 2 4 4 4 4 4 2 4 2 4 4 4 4 4 4 4 4 4 4

```
Within cluster sum of squares by cluster:
[1] 198.33392 293.37002 57.86415 119.49425
(between_SS / total_SS = 53.2 %)
```

```
Available components:
[1] "cluster" "centers" "totss" "withinss"
[5] "tot.withinss" "betweenss" "size" "iter"
[9] "ifault"
> km.cluster<-km.out$cluster
> fviz_cluster(list(data=datascale,cluster=km.cluster))
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_342_0.png)

## 6.3 结论

本章介绍了使用两种方法构建和应用机器学习模型，一种是无需编码的方法，另一种是基于编码的方法。在第一种方法中，用户遵循预先构建的在线或软件平台，输入数据并构建与所调查现象相关的机器学习解决方案。在第二种方法中，用户转而使用 Python 或 R 编程语言编写脚本代码，然后执行这些脚本来构建机器学习模型并检验机器学习分析的结果。本书迄今已介绍了一系列针对不同问题和项目的示例，希望这些示例能够帮助您练习和可视化我们所涵盖的不同机器学习算法、平台和语言。我们将在未来章节中重新探讨上述列出的某些平台和语言，以挖掘更多功能和选项，这些功能和选项可能进一步展示机器学习的潜力，并激发您对该领域的兴趣。

## 定义

- **代码库** 一组可在不同问题中反复使用的预构建模块和代码的集合。
- **基于编码的机器学习** 用户编写或编程可执行脚本来运行机器学习分析。
- **无需编码的机器学习** 一个具有直观图形界面的在线门户或软件，用于运行机器学习分析。
- **相对紧凑度** 定义为与具有相同体积的最紧凑形状的体积表面积比。

## 章节蓝图

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_343_0.png)

## 问题与练习

- 6.1 无需编码和基于编码的机器学习各有什么优缺点？
- 6.2 列出四种编程语言。
- 6.3 列出 DataRobot 和 Exploratory 中实现的两种监督学习算法和两种非监督学习算法。
- 6.4 重复示例 2。[Exploratory, 回归]，但以冷却负载为目标。将您的分析与以加热负载为目标时的分析进行比较。
- 6.5 使用所有平台重复任何由无需编码平台覆盖的示例。比较并评论您的分析结果。
- 6.6 DataRobot 和 Clarifai 在计算机视觉能力方面的主要区别是什么？
- 6.7 比较 1995–1999 年和 2022 年车辆的燃油消耗。您可以使用 Open Canada 提供的数据集 [7]。
- 6.8 重新探讨第 3 章，并在示例 1 [DataRobot, 分类] 中尝试不同的特征选择方法。
- 6.9 鉴于对数据操纵的讨论（见第 3 章），将示例 2。[DataRobot, 回归] 转换为分类问题。

## 参考文献

- 1 BigML. (2022). About. BigML.com. https://bigml.com (访问日期：2022 年 7 月 6 日)。
- 2 Liu, J.-C.-C., Huang, L., Tian, Z., and Ye, H. (2021). 基于知识增强的数据驱动模型，用于量化 PP 纤维在防止超高性能混凝土剥落方面的有效性. Constr. Build. Mater. 299: 123946. doi: 10.1016/j.conbuildmat.2021.123946.
- 3 Liu, J.C., Huang, L., Chen, Z., and Ye, H. (2021). 混合纤维增强超高性能混凝土爆裂剥落诊断的人工智能方法比较研究. Int. J. Civ. Eng. doi: 10.1007/s40999-021-00689-7.
- 4 Liu, J.C. and Zhang, Z. (2021). 基于机器学习的加热混凝土爆裂剥落预测方法. Arch. Civ. Mech. Eng. 20. doi: 10.1007/s43452-020-00135-w.
- 5 Liu, J.C. and Zhang, Z. (2020). 基于人工神经网络的加热钢纤维增强混凝土爆裂剥落预测. J. Adv. Concr. Technol. doi: 10.3151/jact.18.227.
- 6 Liu, J.C. and Zhang, Z. (2020). 加热条件下 PP 纤维增强混凝土爆裂剥落的神经网络模型. J. Build. Eng. doi: 10.1016/j.jobe.2020.101472.
- 7 Open.Canada.ca. (2022). 燃油消耗等级 - 开放政府门户. https://open.canada.ca/data/en/dataset/98fla129-f628-4ce4-b24d-6f16bf24dd64#wb-auto-6 (访问日期：2022 年 7 月 27 日)。
- 8 Open.Canada.ca. (2022). 桥梁状况 - 开放政府门户. https://open.canada.ca/data/en/dataset/37a472f6-b7ea-4a41-9d4b-64a0c8e5025a (访问日期：2022 年 7 月 27 日)。
- 9 Exploratory. (2022). About. https://exploratory.io/about (访问日期：2022 年 7 月 6 日)。
- 10 Tsanas, A. and Xifara, A. (2012). 使用统计机器学习工具对住宅建筑能源性能进行准确定量估计. Energy Build. doi: 10.1016/j.enbuild.2012.03.003.
- 11 Sathishkumar, V.E., Shin, C., and Cho, Y. (2021). 面向智慧城市中数据分析启用型工业建筑的高效能耗预测模型. Build. Res. Inf. 49 (1): 127–143.
- 12 Python (2022). Python 源码发布 | python.org. https://www.python.org/downloads/source (访问日期：2022 年 7 月 5 日)。
- 13 Pypi. (2022) PyPI · Python 软件包索引. https://pypi.org (访问日期：2022 年 7 月 5 日)。
- 14 Keras. (2022) Keras：Python 深度学习 API. https://keras.io (访问日期：2022 年 7 月 5 日)。
- 15 Matplotlib. (2022). Matplotlib —— 使用 Python 进行可视化. https://matplotlib.org (访问日期：2022 年 7 月 5 日)。
- 16 NumPy. (2022). NumPy. https://numpy.org/install (访问日期：2022 年 7 月 5 日)。
- 17 Pandas. (2022). 安装 — pandas 1.4.3 文档. https://pandas.pydata.org/docs/getting_started/install.html#install (访问日期：2022 年 7 月 5 日)。
- 18 scikit-learn. (2022). 安装 scikit-learn — scikit-learn 1.1.1 文档. https://scikit-learn.org/stable/install.html#install-official-release (访问日期：2022 年 7 月 5 日)。
- 19 TensorFlow. (2022). 使用 pip 安装 TensorFlow. https://www.tensorflow.org/install/pip (访问日期：2022 年 7 月 7 日)。
- 20 Jupyter. (2022). Project Jupyter | 主页. https://jupyter.org (访问日期：2022 年 7 月 7 日)。
- 21 RStudio. (2022). RStudio | 面向数据科学团队的开源及专业软件 - rstudio. https://www.rstudio.com (访问日期：2022 年 7 月 7 日)。

