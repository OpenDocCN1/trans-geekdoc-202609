
## Median :5.155 tr2:10

## Mean :5.073

## 3rd Qu.:5.530

## Max. :6.310

它向我们展示了连续的重量变量和一个具有 3 个层级的分类变量，每组有 10 个测量值。

在步骤 2 中，我们使用 `lm()` 函数构建模型，该函数接受 R 公式语法，将要建模的对象（重量）与我们想要使用的变量以及用于查找变量的数据对象放在一起。对结果使用 `summary()` 向我们展示了大量信息：

```
## Call:
## lm(formula = weight - group, data = PlantGrowth)
##
## Residuals:
## Min           1Q      Median      3Q        Max
## -1.0710     -0.4180   -0.0060   0.2627    1.3690
## Coefficients:
##             Estimate. Error t value Pr(|t|)
## (Intercept)   5.0320    0.1971    25.527   <2e-16 ***
## groupprt1   -0.3710    0.2788   -1.331    0.1944
## groupprt2    0.4940    0.2788    1.772     0.0877 
## --
## --
## Signif. codes: 0 '****' 0.001 ***'
##
## Residual standard error: 0.533 on 18 degrees of freedom
## Multiple R-squared: 0.263
## Adjusted R-squared: 0.209
## F-statistic: 4.84 on 1 and 18 DF
```

![](img/dd0d7d9aaacf496c4d1d0e31d83783b3_126_0.png)

![](img/dd0d7d9aaacf496c4d1d0e31d83783b3_126_1.png)

我展示的下一张图（使用 `which=5`）是库克距离图，它显示了拟合值的变化，并有助于识别输入数据中的离群值。任何值远大于其他值的数据点都表明该值对模型的拟合可能产生了某种不当的影响，应该仔细检查。

# 使用线性模型比较两组的均值

![](img/dd0d7d9aaacf496c4d1d0e31d83783b3_127_0.png)

这就是我们构建和诊断线性模型对象的方法。

# 使用线性方法比较两组的均值

t检验是一种统计方法，用于帮助我们判断两组均值之间是否可能存在差异。t检验是生物信息学中最广泛使用的测试，通常在应用时不考虑检验假设是否成立，且可以在不加批判的情况下进行解释。通过构建线性模型来学习如何进行t检验，你将能够测试假设是否成立，因为拟合良好的模型意味着对假设的良好良好。t检验是线性模型的一种特例，因为它可以被构建为一个具有二分类预测变量的线性回归问题。

在线性模型中，我们尝试拟合一个线性方程，描述响应输出变量（因变量）与一个或多个预测输入变量（自变量）之间的关系。在t检验的情况下，我们有一个二分类预测变量，它代表正在比较的两组。

假设我们想要比较在两种不同处理（测试组 B 和对照组 A）下生长的植物的平均干重。我们可以建立一个线性模型，其中响应变量是重量，预测变量是代表处理情况的二分类变量。线性模型方程可以写如下：

```
$dryWeight = \beta_0 + \beta_1 \cdot treatment + \epsilon$
```

其中 $\beta_0$ 是截距，$\beta_1$ 是与二分类预测变量 $treatment$ 相关的系数，$\epsilon$ 是误差项。

通过检验系数 $\beta_1$ 是否可能为零，可以从该线性模型推导出t检验。如果它不为，则有表明两种处理之间的平均干重存在显著差异。

## 准备工作

我们将使用 `rbioinfocookbook` 包中提供的 `PlantGrowth` 数据的修改版本。我们还会使用 `dplyr`。

## 如何操作...

我们通过构建线性模型并解释其输出来进行t检验。请遵循以下步骤：

- 1. 加载数据并检查：
```
library(rbioinfocookbook)
summary(plant_growth_two)
```
- 2. 构建线性模型：
```
model_1 <- lm(weight - group, data = plant_growth_two)
summary(model_1)
```
- 3. 手动计算组差异：
```
library(dplyr)
group_means <- plant_growth_two |>
group_by(group) |>
summarize(mean_wt = mean(weight))
```
`group_means`
`difference_in_means <- group_means$mean_wt[1] - group_means$mean_wt[2]`
`difference_in_means`

这几步就是我们需要的全部。

# 运行原理...

第一步向我们明确，从 `rbioinfocookbook` 加载的数据中只有两个处理组。`summary()` 函数显示每组有十个测量值。注意，t检验不能在多于两组的数据上进行。如果你尝试对具有更多组的数据进行此类评估，其解释将会失效。

# 使用线性模型比较两组的均值

第二步构建模型的方式与我们在 `Modeling` 数据中通过线性模型配方看到的方式相同。代码几乎相同，但对输出的解释是关键，所以让我们来看看：

```
## Call:
## lm(formula = weight ~ group, data = plant_growth_two)
## Residuals:
## Min 1Q Median 3Q Max
## -0.862 -0.410 -0.006 0.280 1.078
## Coefficients:
## Estimate Std. Error t Pr(>t|)
## (Intercept) 5.0320 0.1637 30.742 <2e-16 ***
## groupB -0.4940 0.2315 -2.134 0.0469 *
## Signific. codes: 0 **** * 0.001 ** 0.01 * 0.05 . . ' 1
## Residual standard error: 0.6234 on 27 degrees of freedom
## Multiple R-squared: 0.2641, Adjusted R-squared: 0.2096
## F-statistic: 4.846 on 2 and 27 DF,
```
（注：此处原文翻译部分存在大量逻辑重复和乱码，译文已尽可能保持核心逻辑的连贯，但根据指令要求保留了原始结构）

响应变量（因变量）与一个或预测预测变量。

通过检验系数 $\beta_1$ 是否可能为零，可以从该线性模型推导出t检验。如果它不为，则有表明两种处理之间的平均干重存在显著差异。

（注：此处原文翻译部分存在大量逻辑重复和乱码，译文已尽可能保持核心逻辑的连贯，但根据指令要求保留了原始结构）

# 使用线性模型轻松进行统计检验

我们在第 2 步中正是这样做的，使用 `mult` 包通过 `glht()` 进行一般线性模型假设检验。与内置的 `TukeyHSD()` 相比，该函数在设计和可以获得的对比结果方面更加灵活，但也稍微复杂一些。基础情况非常直观。`linf()` 选项仅接受待测试项目的规范，而 `mcp()` 函数有助于根据文本描述生成比较（在这里变量 `group` 应该通过 Tukey 进行分析）。输出如下：

```
## 一般线性假设的同步检验
## 均值的多次比较：Tukey 对比
## Fit: lm(formula = weight - group, data = PlantGrowth)
## 线性假设:
##
| Estimate | Std. Error | t value | Pr(|t|) |
| :--- | :--- | :--- | :--- |
| trtl1 ctrl == 0 | -0.3710 | 0.2788 | -1.331 | 0.3909 |
| trt2 ctrl == 0 | 0.4940 | 0.2788 | 1.772 | 0.1980 |
| trt2 trtl == 0 | 0.8650 | 0.2788 | 3.103 | 0.0121 * |
##
## 显著性代码: 0 '0.001 *** 0.01 ** 0.05 ' * .1 . * 1
## (报告的是调整后的 p 值 - 单步法)
```

通过打印摘要（summary），我们可以看到显式写出的对比（例如 `ctrl1` 和 `trtl1` 之间差异为零的概率）。结论是，没有证据表明任何处理与对照组不同，但我们观察到的 `trtl1` 和 `trt2` 之间的差异大约有 1.2% 的概率随机发生，因此被认为是显著的。

就是这样！这就是执行得当的线性模型以及随后的 ANOVA，并使用 Tukey 事后检验来确定差异的过程。

# 还有更多……

在第 1 步中，我们生成了一个模型，R 决定了基准应该是什么。如果我们愿意，可以使用 `relevel(1)` 函数和 `ref` 选项进行指定，如下所示：

```r
df <- PlantGrowth
df$group<- relevel(df$group, ref="trt2")
model_2 <- lm(weight - group , data = df,)
summary(model_2)
```

在 `summary()` 输出中，我们可以看到所有的比较都是基于那个新基准进行的。我们不使用这种方法来生成所有比较，因为这样很繁琐且会产生多次比较错误。`multcomp` 包更加整洁，为不同类型的比较提供了许多选项，并对多假设检验的 p 值进行了修正。

# 使用线性模型和 ANOVA 比较多个变量中的多个组

双因素方差分析（Two-way ANOVA）是一种用于分析两个分类独立变量（也称为因素）对连续依赖变量的影响的统计方法。这两个独立变量可以是固的，也可以是随机的。

双因素方差分析的主要目的是检查两个独立变量之间是否存在显著的交互作用，并确定每个独立变量对依赖变量的主效应。

该分析涉及计算每个效应及其交互作用的平方和，并将这些值与其各自的自由度进行比较以获得 F 比率。然后将 F 比率与 F 分布的临界值进行比较，以确定这些效应在统计学上是否显著。

在“使用线性模型和 ANOVA 比较单变量中的多个组”配方中看到的单因素 ANOVA 基础是线性模型，通过评估该模型，我们可以帮助确保满足检验的假设。

## 准备工作

我们将再次使用 `mult` 包和 `rbioinf` 包中一个名为 `compost` 的合成表达数据集。注意，目的不是寻找单个的差异表达基因，而是评估基因的整体表达水平是否受到重复（Replicate）或处理（Treatment）的影响。

## 如何操作……

该方法与单因素 ANOVA 为相似，但增加了潜在交互作用的复杂性并有更显式的比较：

- 1. 对新数据进行汇总并建模：
```r
library(rbioinfcookbook)
summary(expression)
model_1 <- lm(Expression ~ Treatment + Replicate, data = expression)
summary(model_1)
```
执行 Tukey 事后检验：
```r
library(multcomp)
tested <- glht(model_1,
linfct = mcp(Replicate = "Tukey",
Treatment = "Tukey"))
summary(tested)
```
将测试输出与绘图对比：
```r
library(ggplot2)
ggplot(expression) +
aes(Treatment, Expression) +
geom_boxplot() +
geom_jitter(aes(colour = Replicate))
```
这就是完成一个简单的 ANOVA 所需的所有工作。然而，这里的解释比单因素方法更困难，让我们来看它们：

## 它是如何工作的……

第 1 步现在是一个非常熟悉的模型创建步骤。通过在公式中使用 `+` 加上第二个变量来详细说明。如果你正在检查或想建模变量间的交互，则需要更复杂的公式。`summary(expression)` 显示我们有六个基因、三个处理和三个重复。接下来的 `summary(model_1)` 显示 `Treatment` 对表达可能有影响，尽管还不清楚具体是什么。此外，p 值是模型级的值，虽然存在显著系数，但还不清楚是哪些：

```
## Call:
## lm(formula = Expression - Treatment + Replicate, data = expression)
##
## Residuals:
## Min 1Q Median 3Q Max
n -3.9665 -1.7154 -0.0843 1.7505 5.0958
##
## Coefficients:
| Estimate | Std. Error | t | Pr(|t|) |
| :--- | :--- | :--- | :--- |
| (Intercept) | 4.8093 | 0.7081 | 6.792 | 1.39e-08 *** |
| TreatmentDrugA | 2.3096 | 0.7757 | 2.978 | 0.00451 ** |
| TreatmentDrugB | 1.6672 | 0.7757 | 2.149 | 0.03657 * |
| Replicate2 | 0.3843 | 0.7757 | 0.495 | 0.62250 |
```

# 线性模型中变量间交互作用的测试与处理

直观的。我们要记住，大型交互模型有时会非常复杂，需要我们咨询统计学家的，但这里的方法对于初级分析和引导后续的问题是有帮助的。

## 准备工作

在这个食谱中，我们将使用来自 `rbioinfocookbook` 的植物产量大小数据集 `compost`，以及 `dplyr` 和 `ggplot2` 软件包。

## 如何操作...

测试交互作用要要的第一步是绘图。然后，我们可以开始建模：

- 1. 检查潜在的交互作用：
```
library(rbioinfocookbook)
summary(compost)
interaction.plot(compost$compost, compost$supplement,
compost$size,
  xlab="Compost Type", ylab="Size", trace.label = 
"Supplement"
)
```
- 2. 添加一个显式的交互列：
```
compost_int <- dplyr::mutate(compost,
compost_supp = interaction(compost, supplement)
)
```
- 3. 将交互作用作为一个单独变量进行建模：
```
model_1 <- lm(size ~ compost_supp, data=compost_int)
summary(model_1)
library(multcomp)
tested <- glht(model_1,
linfct = mcp(compost_supp = "Tukey")
)
summary(tested)
```
- 4. 创建一个表：

通过这些步骤，我们有一种相当直观的方法来检查和建模交互变量。

## 工作原理...

在第 1 步中，我们用 `summary()` 检查数据以熟悉它。然后，我们使用 `interaction.plot()` 函数创建一个交互图，该函数接受向量作为输入而不是整个数据框。我们必须在列名上使用 `$` 子集。图 5.6 中生成的图显示了连接数据中各组均值的线。当这些线交叉时，我们可以怀疑存在交互作用：

![](img/dd0d7d9aaacf496c4d1d0e31d83783b3_138_0.png)

图 5.6 - 交互作用图

我们必须开始对该交互作用进行建模。虽然可以在 `lm( ) 步骤中通过函数语法指定交互作用，但解释可能会变得困难，实现可能会变得复杂。你可能需要统计学家的输入，而他们可能并不容易获得。相反，我们采用了一种简单但功能较弱的方法。在第 2 步中，我们使用 `interaction()` 函数和 `mutate()` 创建了一个 `compost_supp` 列，描述了肥料和补充剂之间的交互作用。然后，在第 3 步中，直接在模型中使用新列。来自 `glht()` 函数的事后检验列出了所有可能的两两交互作用，正如 `compost_supp` 列描述的那样。

# 线性模型中变量间交互作用的测试与处理 117

输出如下：

```
## Simultaneous Tests for General Linear Hypotheses
##
## Multiple Comparisons of Means: Tukey Contrasts
##
## Fit: lm(formula = size - compost_supp, data = compost_int)
##
## Linear Hypotheses:
##
Std. Error t value Pr(|t|)                               Estimate
## John Innes #2.Formula X1           John Innes #1.Formula X1 ====
```
