
也涉及交互项）。为解决此问题，Goldstein, Kapelner, Bleich, and Pitkin 提出了个体条件期望（ICE）图的概念。ICE 图显示每个观测值中响应与感兴趣预测变量之间的估计关系。因此，感兴趣预测变量的 PD 图可以通过对所有观测值的相应 ICE 图求平均得到。

如 [Goldstein et al., 2015] 所述，当各个曲线的截距范围很大并因此相互重叠时，模型中的异质性可能难以辨别。出于此原因，Goldstein, Kapelner, Bleich, and Pitkin 建议对 ICE 图进行居中处理，以生成居中 ICE 图（简称 c-ICE 图）。他们还建议其他修改，例如导数 ICE 图（简称 d-ICE 图），以进一步探索交互效应的存在。居中 ICE 图是通过将 ICE 曲线上下移动（从每条曲线中减去第一个值）获得的，这实际上将它们在起始处“捏合”在一起。

## 6.2.4 软件

PD 图和 ICE 图（及其许多变体）已在多个 R 包中实现。从历史上看，PD 图最初仅在特定的基于树的集成包中实现，例如 randomForest [Breiman et al., 2018] 和 gbm。然而，它们随后在 pdp 包中普遍可用，随后是 iml 和 ingredients 等包；这些包也支持 ICE 图；R 包 ICEbox [Goldstein et al., 2017] 提供了 ICE 图的原始实现及其多种变体，例如 c-ICE 和 d-ICE 图。PD 图和 ICE 图也已在 scikit-learn 的检查模块中提供，分别从版本 0.22.0 和 0.24.0 开始。

## 6.2.5 示例：预测房价

使用 Ames 房价袋装树集成模型，我将展示如何手动以及使用 pdp 包构建 PD 图和 ICE 曲线。首先，让我们为地上方形面积（Gr_Liv_Area）构建一个 PD 图，它是根据图 6.1（第 207 页）中的基于置换的 VI 分数排名靠前的预测变量之一。

第一步是创建用于构建图表的点网格。对于连续变量，使用足够细的百分位数网格即可，如下例所示。然后，我只需遍历每个网格点并 1) 复制训练数据，2) 将副本中 Gr_Liv_Area 的所有值替换为当前网格值，3) 对修改后的训练数据副本进行评分并将预测结果平均。最后，我只需将网格点与 for 循环中获得的平均预测结果绘制在一起。结果如图 6.2 所示，显示地上方形面积与预测售价之间存在相对单调递增的关系。

```r
x.grid <- quantile(ames.trn$Gr_Liv_Area, probs = 1:30 / 31)
pd <- numeric(length(x.grid))
for (i in seq_along(x.grid)) {
  temp <- ames.trn # temporary copy of data
  temp[["Gr_Liv_Area"]] <- x.grid[i]
  pd[i] <- mean(predict(ames.bag, newdata = temp))
}
```

```r
# PD plot for above grade square footage (Figure 6.2)
plot(x.grid, pd, type = "l", xlab = "Above grade square footage",
ylab = "Partial dependence", las = 1)
rug(x.grid) # add rug plot to x-axis
```

![](img/2c227bfb3620dc3d159fa5e6598afa30_228_0.png)

### 图 6.2：袋装树集成模型中售价对地上方形面积的部分依赖。

虽然查看响应对单个特征（即主效应）的部分依赖很有信息量，但同时查看对两个或三个预测变量^a（即交互效应）的依赖通常也很有用。幸运的是，修改上述 for 循环以适应多个预测变量相当简单；然而，这是一个展示使用简单数据处理操作计算部分依赖的替代方法的好机会，如果你在 SQL 或 Spark 中工作，这种方法可能更高效。

本质上，我们可以使用交叉连接将所有修改后的训练副本生成在一个堆叠的数据框中，对其进行一次评分，然后将预测结果聚合为部分依赖值。下面是使用基础 R 的示例，但将其转换为 data.table [Dowle and Srinivasan, 2021]、dplyr [Wickham et al., 2021b]、SparkR [Venkataraman et al., 2016]、sparklyr [Luraschi et al., 2021] 或任何其他可以执行简单交叉连接的语言应该相当简单——前提是你能将生成的笛卡尔积保存在内存中！（在 Spark 中完成此操作的示例在第 7.9.5 节中提供。）

为了说明，我将构建售价对地上方形面积和一楼方形面积的部分依赖。我仍然需要构建用于绘图的点网格；这里，我将使用 expand.grid() 对每个特征的百分位数进行笛卡尔积运算。

```r
x1.grid <- quantile(ames.trn$Gr_Liv_Area, probs = 1:30 / 31)
x2.grid <- quantile(ames.trn$First_Flr_SF, probs = 1:30 / 31)
df1 <- expand.grid("Gr_Liv_Area" = x1.grid,
                  "First_Flr_SF" = x2.grid) # Cartesian product
```

在下一步中，我对绘图值网格（df1）和移除了绘图特征的原始训练数据（df2）^b 执行交叉连接：

```r
df2 <- subset(ames.trn, select = -c(Gr_Liv_Area, First_Flr_SF))
# Perform a cross-join between the two data sets
pd <- merge(df1, df2, all = TRUE) # Cartesian product
dim(pd) # print dimensions
#> [1] 1845900 81
```

然后，我只需对数据进行评分，并通过计算每个网格点内的平均预测值来聚合，如下例所示：

```r
pd$yhat <- predict(ames.bag, newdata = pd) # might take a few minutes!
pd <- aggregate(yhat ~ Gr_Liv_Area + First_Flr_SF, data = pd,
                FUN = mean)
```

下面的代码片段使用内置的 lattice 包构建带有等高线的数据伪彩色分层图；结果如图 6.3 所示。在这里，你可以看到两个特征对预测售价的联合效应。

b 请小心，因为生成的数据集是笛卡尔积，可能非常大！

```r
library(lattice)
```

```r
# PD plot for above grade and first floor square footage
levelplot(yhat ~ Gr_Liv_Area * First_Flr_SF, data = pd,
          contour = TRUE, col = "white", scales = list(tck = c(1, 0)),
          col.regions = hcl.colors(100, palette = "viridis"))
```

![](img/2c227bfb3620dc3d159fa5e6598afa30_230_0.png)

### 图 6.3：袋装树集成模型中售价对地上方形面积和一楼方形面积的部分依赖。

在训练数据区域之外的区域从 PD 图（和 ICE 图）中得出结论是不明智的。Greenwell [2017] 描述了两种降低 PD 图中外推风险的方法：地毯图（如我在图 6.2 中使用的）和凸包（可用于双变量图，如图 6.3）。

构建 ICE 曲线同样简单；只需跳过聚合步骤并绘制每条单独的曲线即可。在下面的示例中，我将使用 pdp 包构建 c-ICE 曲线，以显示学习样本中每个观测值的地上方形面积对售价的部分依赖。没有必要为每个样本构建一条曲线，尤其是当你有数千个（或更多）数据点时；这里，我将只绘制 500 条曲线的随机样本。我将使用与图 6.2（第 212 页）中的 PD 图相同的百分位数来构建图表，通过在 partial() 调用中使用 quantiles 和 probs 参数；请注意，partial() 的默认值是在预测变量值范围内使用均匀间隔的点网格。

结果如图 6.4 所示；红线显示每个地上方形面积的平均 c-ICE 值（即居中部分依赖）。c-ICE 曲线中的异质性表明 Gr_Liv_Area 与至少一个其他特征之间存在潜在的交互效应。c-ICE 曲线还表明训练集中大多数房屋存在相对单调递增的关系，但你可以看到底部的几条曲线偏离了这一总体模式。

```r
ice <- partial(ames.bag, pred.var = "Gr_Liv_Area", ice = TRUE,
               center = TRUE, quantiles = TRUE, probs = 1:30 / 31)
set.seed(1123) # for reproducibility
samp <- sample.int(nrow(ames.trn), size = 500) # sample 500 homes
autoplot(ice[ice$yhat.id %in% samp, ], alpha = 0.1) +
  ylab("Conditional expectation")
```

![](img/2c227bfb3620dc3d159fa5e6598afa30_231_0.png)

### 图 6.4：使用 Ames 房价袋装树集成模型的地上方形面积的 500 条 c-ICE 曲线的随机样本。这些曲线表明样本中大多数房屋存在相对单调递增的关系。500 条 c-ICE 曲线的平均值以红色显示。

## 6.2.6 示例：Edgar Anderson 的鸢尾花数据

作为分类示例，我将考虑 R 的 datasets 包中 Edgar Anderson 的鸢尾花数据。iris 数据框包含三种鸢尾花（setosa、versicolor 和 virginica）各 50 朵花的萼片长度、萼片宽度、花瓣长度和花瓣宽度（厘米）。下面，我使用 randomForest 包将袋装树集成模型拟合到数据上：
