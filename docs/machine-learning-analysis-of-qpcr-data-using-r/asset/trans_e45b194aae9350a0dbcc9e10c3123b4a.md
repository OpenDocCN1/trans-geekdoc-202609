

## 第三章
### 机器学习在 maxRatio qPCR 分析中的应用

### 使用期望最大化方法过滤 maxRatio

与拟合点法一样，maxRatio 也需要建立一个阈值来区分反应性（阳性）和非反应性（阴性）反应（样本）。如前文所述，该阈值是通过将一组阴性样本的 MR 值的标准差乘以 5–10 来确定的（Shain 和 Clemens，2008）。乘数的标度由操作者选择。然而，最近人们尝试通过提供客观的样本分离来改进该程序。在此背景下，程序的客观性意味着操作者无需选择一个数值——统计方法将根据手头的数据选择最佳参数。理论上，这种客观方法将提供一种针对当前 qPCR 检测的分析工具，能够补偿样本基质中可能的抑制剂、所用化学试剂的性能以及热循环仪的异常行为。与拟合点法不同，maxRatio 允许使用多个阈值将样本分层到特定子类（例如，弱阳性样本）中。

面向数据设定阈值的第一个尝试是实现期望最大化（EM）算法（Marongiu 等，2016a）。EM 算法识别样本分布中的峰，然后确定一个截断值将它们分开（Dempster 等，1977）。以下清单将描述这一过程：

```
Listing 3.1
set.seed(15)
opar <- par("mar")
negative_mr <- runif(50, 0, 0.099)
negative_fcn <- runif(50, 1, 40)
positive_mr <- c(runif(30, 0.2, 0.5), runif(20, 0.4, 0.5))
positive_fcn <- c(runif(30, 25, 40), runif(20, 10, 25))
uncertain_mr <- runif(10, 0.099, 0.2)
uncertain_fcn <- runif(10, 25, 40)
layout(matrix(c(1,2),nrow=1), widths=c(4,1))
par(mar=c(5.1, 4.1, 4.1, 0))
plot(negative_fcn, negative_mr, ylim=c(0,0.5), xlim=c(0,41), cex=1.5,
    xlab=expression(bold("FCN")), ylab=expression(bold("MR")))
points(positive_fcn, positive_mr, pch=16, cex=1.5)
points(uncertain_fcn, uncertain_mr, pch=16, cex=1.5, col="grey")
legend("topleft", legend = c("Positives", "Negatives", "Uncertains"), pch = c(16, 1, 16),
col=c("black", "black", "grey"), cex=0.8)
par(mar=c(5.1, 0.2, 4.1, 2))
d <- density(c(negative_mr, uncertain_mr, positive_mr))
plot(d$x, d$y, ylim=c(0,0.5), type="", yaxs="n", xaxs="n", main=NA, ylab=NA, xlab=NA)
par(mar=opar)
```

图 3.1 显示样本密度有两个主峰，一个对应阳性样本，一个对应阴性样本。EM 算法在这两个峰之间建立最佳截断值。具体而言，使用 mixtools 库构建参数分布的混合模型。模型摘要提供了描述两个重叠分布（阳性样本和阴性样本）的参数特征。还可以绘制这些总体的密度图。

![](img/7ea01e6937e09d043e45c73fff9eaed3_87_0.png)

图 3.1. 样本密度的识别。阴性（○）和阳性（●）样本组在 MR/FCN 空间中以不同方式分层。这种分离并非绝对，且在这两组之间往往存在一些样本（●），它们可以被界定为不确定。密度图分析（右图）表明 MR 值的分布呈双峰分布；因此，在两个峰之间放置一个截断值将能够区分这两个主要总体。左图中的插图显示了由 EM 算法生成的密度图。在此情况下，横坐标标签“数据”代表“MR”。

```
Listing 3.1 (continuation)
library(mixtools)
df <- data.frame(MR=c(negative_mr, uncertain_mr, positive_mr),
FCN=c(negative_fcn, uncertain_fcn, positive_fcn))
model = normalmixEM((x = df$MR))
plot(model, which=2)
```

```text
> summary(model)
summary of normalmixEM object:
```

|      | 成分 1     | 成分 2    |
|------|------------|-----------|
| lambda | 0.4532318 | 0.546768 |
| mu    | 0.0538644  | 0.345513 |
| sigma | 0.0291171 | 0.114604 |

估计处的对数似然：81.04961

```text
> model$mu[1]   # Mean of negative population
[1] 0.05386439
> model$sigma[1] # SD of negative population
[1] 0.02911713
> model$mu[2]   # Mean of positive population
[1] 0.345513
> model$sigma[2] # SD of positive population
[1] 0.1146038
```

标准差可用作两个总体之间的阈值。可选地，可以应用一个乘数来更好地区分数据（Marongiu 等，2016a）——然而，由于操作者选择乘数的大小，这种方法引入了进一步的主观步骤。问题在于，很多时候，实际数据中包含一些在低 FCN 处 MR 值出现尖峰的样本。可以更新前面的清单以考虑这种情况：

```
Listing 3.2
spike_mr <- runif(10, 0, 0.3)
spike_fcn <- runif(10, 1, 10)
df <- data.frame(MR=c(negative_mr, uncertain_mr, positive_mr, spike_mr),
FCN=c(negative_fcn, uncertain_fcn, positive_fcn, spike_fcn),
GROUP=c(rep("negative", length(negative_mr)),
rep("uncertain", length(uncertain_mr)),
rep("positive", length(positive_mr)), rep("spike", length(spike_mr))))
plot(df$MR[df$GROUP=="negative"] ~ df$FCN[df$GROUP=="negative"], ylim=c(0,0.5), xlim=c(0,41),
    cex=1.5, xlab=expression(bold("FCN")), ylab=expression(bold("MR")))
points(df$MR[df$GROUP=="positive"] ~ df$FCN[df$GROUP=="positive"], pch=16, cex=1.5)
points(df$MR[df$GROUP=="uncertain"] ~ df$FCN[df$GROUP=="uncertain"], pch=16, cex=1.5,
    col="grey")
points(df$MR[df$GROUP=="spike"] ~ df$FCN[df$GROUP=="spike"], pch=15, cex=1.5, col="gray40")
legend("topleft", legend = c("Positives", "Negatives", "Uncertains", "Early spike"),
    pch = c(16, 1, 16, 15), col=c("black", "black", "grey", "gray40"))
```

对数据的目视检查（图 3.2A）显示，在 FCN = 10 处样本分布存在差异。这种分割显然首先是由于本例数据的生成方式所致，但真实数据集也存在类似的不连续性（Marongiu 等，2016a；Marongiu 等，2021a）——并且该数据的设计就包含了这种分割。FCN = 10 可用于进一步对反应进行分层：低于此值的样本将有一个 MR 阈值，而高于此值的样本则应用由 EM 推导出的阈值。

```
Listing 3.2 (continuation)
TH_mr <- model$sigma[2]
early_TH_fcn <- 10
early_TH_mr <- max(df$MR[(df$MR > cut_off) & (df$FCN < early_TH_fcn)])
plot(df$MR[(df$FCN < early_TH_fcn) & (df$MR <= early_TH_mr)] ~
    df$FCN[(df$FCN < early_TH_fcn) & (df$MR <= early_TH_mr)],
    ylim=c(0,0.5), xlim=c(0,41), cex=1.5, xlab=expression(bold("FCN")),
    ylab=expression(bold("MR")))
points(df$MR[(df$FCN >= early_TH_fcn) & (df$MR < TH_mr)] ~
    df$FCN[(df$FCN >= early_TH_fcn) & (df$MR < TH_mr)], pch=1, cex=1.5)
points(df$MR[(df$FCN >= early_TH_fcn) & (df$MR >= TH_mr)] ~
    df$FCN[(df$FCN >= early_TH_fcn) & (df$MR >= TH_mr)], pch=16, cex=1.5)
segments(0, early_TH_mr, early_TH_fcn, early_TH_mr, col="red", lwd=2, lty=2)
segments(early_TH_fcn, early_TH_mr, early_TH_fcn, cut_off, col="red", lwd=2, lty=2)
segments(early_TH_fcn, cut_off, max(df$FCN), cut_off, col="red", lwd=2, lty=2)
legend("topleft", legend = c("Positives", "Negatives"), pch = c(16, 1))
```

图 3.2B 显示了样本如何根据其 MR 和 FCN 值进行分类，而无需事先知道其反应性。其思路是，操作者在 qPCR 检测后无需通过目视检查反应来确定它们是阳性还是阴性；算法将自动完成这一工作。

每天都在进行筛查。如果有一种程序可以省去其中大部分反应，那对操作者来说将是一种改进，而 maxRatio 的价值也将变得显而易见。

然而，EM 过滤 maxRatio 的方法存在一些缺点：

- FCN 阈值的选择仍然是主观的。
- 使用两个 MR 阈值（和一个 FCN 阈值）既令人困惑又不优雅。
- 进一步子类（如弱阳性）的定义设计起来很复杂，而且仍然是主观的。

### 使用支持向量机过滤 maxRatio

支持向量机（SVM）是监督学习模型，作为机器学习算法的一部分，用于分类和回归分析。SVM 是由 Vladimir Vapnik 和他的同事于 1960 年代至 1990 年代在 AT&T 贝尔实验室开发的（Cortes 和 Vapnik，1995）。本质上，SVM 在被称为项目或元素的样本组之间找到一条分隔线（“最大间隔超平面”或简称为超平面）。线性可分的组是不重叠的组。SVM 算法在组之间找到分离程度最大的超平面，这意味着从一个组中被重新分类到另一个组的元素数量最少。SVM 不使用每组的所有元素，而是使用最接近超平面的元素子集，这降低了过程的复杂性和计算要求。当组不是线性可分时，SVM 应用“间隔”：允许超平面附近的一些元素聚集到相对的一组中。可以被“错误分类”的样本比例由代价参数 C 定义，该参数对应围绕超平面的间隔宽度。下一节将更详细地描述 SVM 算法。

为了使用前一节中的示例，根据 EM 推导出的阈值分层的样本将被分配到 A 组或 B 组。这种初始分类指定了术语“监督”：操作者通过为每个元素分配标签来监督该过程；然后，机器将基于某种算法改进分类。监督学习方法与“无监督”模型（如神经网络和层次聚类）相对立，后者不需要任何

