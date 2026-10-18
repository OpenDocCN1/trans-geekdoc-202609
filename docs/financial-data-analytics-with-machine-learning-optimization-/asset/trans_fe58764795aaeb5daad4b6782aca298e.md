

1. 在节点 1（根节点）中，共有 `n = 680` 个案例。其中，32 个属于组 1（视为损失）。由于大多数属于组 0，因此组标签被分类为 `yval=0`，组 0 和组 1 的百分比分别以括号给出：分别为 `0.952941176 = 648 / 680` 和 `0.047058824 = 32 / 680`。

2. 在节点 2（左分支）中，拆分条件为 `d$ln_MV9.478`。共有 `n = 647` 个案例，其中 3 个来自根节点（节点 1）的组 1，组标签为 `yval=0`；同样，各自的百分比为 `0.995363215 = 644 / 647` 和 `0.004636785 = 3 / 647`。

3. 在节点 3（右分支）中，`n = 33`。有 4 个案例来自根节点的组 0，组标签为 `yval=1`；在此，各组的百分比为 `0.121212121 = 4 / 33` 和 `0.878787879 = 29 / 33`。

此输出实际上意味着，我们可以根据仅一个简单的条件 `ln_MV < 9.478` 来预测或分类某只股票是否为蓝筹股。由于本示例中的分类树非常简单，我们实际上可以绘制观测值：请参阅 [图 13.9](#c13.xhtml#c13-fig-0009) 中的完整图表。

![FIGURE 13.9 Plot of ln\_MV versus HSI, with the horizontal line ln\_MV equals 9.478 representing the classification rule.](images/c13f009.png)

[图 13.9](#c13.xhtml#R_c13-fig-0009) `ln_MV` 与 `HSI` 的图表，其中水平线 `ln_MV = 9.478` 表示分类规则。

可以轻松找到此分类树的交叉列表；请参阅 [程序 13.7](#c13.xhtml#c13-sec-3007)（Python）和 [程序 13.8](#c13.xhtml#c13-sec-3008)（**R**）。从输出中可以看出，有 3 只蓝筹股被误分类为非蓝筹股，而 4 只非蓝筹股被误分类为蓝筹股。

## II. 鸢尾花数据集：

回顾 [第 10.4.3 节](#c10.xhtml#c10-sec-0008) 中的鸢尾花数据集。在此，我们构建分类树来对鸢尾花的物种进行分类；请参阅 [程序 13.9](#c13.xhtml#c13-sec-3009)（Python）和 [程序 13.10](#c13.xhtml#c13-sec-3010)（**R**）。

![FIGURE 13.10 Classification tree for the iris flower dataset.](images/c13f010.png)

[图 13.10](#c13.xhtml#R_c13-fig-0010) 鸢尾花数据集的分类树。

从 [图 13.10](#c13.xhtml#c13-fig-0010) 显示的输出中，分类规则及其相应的质量度量如下：

1. R1：如果 `Petal.Length < 2.45`，则物种 = `setosa`（50/0/0）。

2. R2：如果 `Petal.Length >= 2.45` 且 `Petal.width < 1.75`，则物种 = `versicolor`（0/49/5）；

3. R3：如果 `Petal.Length >= 2.45` 且 `Petal.width >= 1.75`，则物种 = `virginica`（0/1/45）。

尽管 Python 和 **R** 生成的两棵分类树看起来相似，但 Python 构建了一棵更大的树。实际上，构建分类树涉及其他超参数，包括 `minsplit`，它指定节点中必须存在的观测值的最小数量才能尝试拆分，以及 `maxdepth`，它设置最终树的最大深度（根节点计为深度 0）。

由于两棵分类树都相对简单，且规则主要取决于两个变量，我们可以再次绘制观测值以作说明。请参阅 [程序 13.11](#c13.xhtml#c13-sec-3011)（Python）和 [程序 13.12](#c13.xhtml#c13-sec-3012)（**R**）。

从 [图 13.11](#c13.xhtml#c13-fig-0011) 中，我们可以清楚地看到这些分类规则的工作原理。最后，我们可以通过 Python ([程序 13.13](#c13.xhtml#c13-sec-3013)) 和 **R** ([程序 13.14](#c13.xhtml#c13-sec-3014)) 生成交叉列表。

![FIGURE 13.11 Plot of Petal.Length versus Petal.width, with the horizontal lines Petal width equals 1.65 and 1.75, and the vertical lines Petal Length equals 2.45 and 4.95 representing the classification rules.](images/c13f011.png)

[图 13.11](#c13.xhtml#R_c13-fig-0011) `Petal.Length` 与 `Petal.width` 的图表，其中水平线 `Petal.width = 1.65` 和 `1.75`，以及垂直线 `Petal.Length = 2.45` 和 `4.95` 表示分类规则。

从通过 [程序 13.13](#c13.xhtml#c13-sec-3013) 由 Python 生成的表中，有 3 个 versicolor 物种被误分类为 virginica 物种，错误率为 3/150 = 2%。另一方面，通过 [程序 13.14](#c13.xhtml#c13-sec-3014) 由 **R** 生成的表显示错误率为 (1+5)/150 = 4%，其中 5 个 virginica 物种被误分类为 versicolor 物种，1 个 versicolor 物种被误分类为 virginica 物种。Python 和 **R** 之间的错误率差异是由于其对应树的深度不同。

## 13.8 回归树

