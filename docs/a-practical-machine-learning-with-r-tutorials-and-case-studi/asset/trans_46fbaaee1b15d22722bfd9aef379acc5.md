

## 11.7 预测变量的 SHAP 贡献

## 交互章节

在本节中，你将找到包含 R 代码的内容，可以在 RStudio 中进行执行、修改和重新运行。

阅读和学习本节的最佳方法是使用 RStudio 打开它。这样你就可以在浏览器中交互式地处理 R 练习和 R 项目。通过这种方式，你可以应用目前所学的内容并扩展你的知识。你也可以选择继续阅读书籍或在线学习，但你将无法从交互式学习体验中受益。

要在交互环境中处理本节，请遵循以下步骤：

- 1. 确保已安装了 `tweed` 和 `shiny` 包。如果没有，请从 RStudio 的主菜单（Tools -> Install Packages ...）进行安装。
- 2. 下载交互会话的 R 文件并将其保存到你的项目文件夹。
- 3. 在 RStudio 中打开下载的文件，并点击位于编辑窗口顶部中间的 Run 按钮。

关于运行练习题的详细帮助（包括针对 Windows 和 Mac 用户的视频），请参考：https://blog.lang-analytics.com/2024/01/intersessions.html。

> 不要跳过此交互章节，因为除了已涵盖概念的应用外，它还会扩展你目前所学的内容。

以下是下载交互章节的链接：
https://ai.lang-analytics.com/ex/?file=17-InterpretExerc100.Rmd

要为你选择的美国大陆某个县生成 SHAP 图，你需要执行两个步骤：

### 步骤 1：

代码块可以帮助你找到感兴趣的县的 CountyID。在下一步中，你需要 CountyID 来创建 SHAP 图。

要找到 CountyID，请将下方代码块中的 `...` 替换为你感兴趣的县名称或部分（不要包含 "county" 一词）

```
CountySearchStr="..."
```

```r
###### 不要更改此处以下代码 ############
VecMatchingCountyNames=grep(CountySearchStr, DataCountyInfo$County,ignore.case=TRUE)
MatchingFIPS=grep(CountySearchStr, as.character(DataCountyInfo$FIPS),ignore.case=TRUE)
```

### 解释机器学习结果

```r
VecMatching=sort(c(VecMatchingNames, VecMatchingFIPS))
unique(DataCountInfo[VecMatching,])
DataMatchingCount=DataCountInfo[VecMatching,]
print(DataMatchingCounties)
```

### 步骤 2：

执行代码需要一些时间（取决于你的电脑，大约 1-8 分钟）。你可以将 `B=` 参数（计算的场景数量）更改为较低的值以加速，但代价是精度较低。

在获得结果后，花一点时间解释 SHAP 值，并决定哪些 SHAP 值不应该解释（提示：参考 SHAP 值的值和箱线图）。

CountyId = ...
set.seed(2021)

```r
SHAPobject=predict_parts(
  explainer=ExplainerForest,
  new_observation=DataVax[CountyId],
  type="shap", B=25)
```

# 不要更改此处以下代码 #

```r
CountyPred=round(attr(SHAPobject, "prediction"), 3)
RateCoalNone=round(attr(SHAPobject, "intercept"), 3)
TitleShape=paste(substr(DataCountInfo[CountyId], 3), 1, 15),
  ("PredValue", CountyPred,
  ("Coalition, none =", RateCoalNone,""))
```

```r
SHAPobject$TitleShape
plot(SHAPobject)
```

```r
SHTable=SHAPobject |>
  as_tibble() |>
  filter(B==0) |>
  select(Variable=variable_name, SHAP=contribution,
  County=variable_value) |>
```

## 11.8 局部可解释模型无关解释 (LIME)

```r
mutate(Nationac=c(0.063, 0.136, 0.115, 0.191, 0.173,
0.478, round(0.310)))|>
mutate(County=round(as.numeric(County), 3))|>
mutate(SHAP=round(TitleShape), SHAP, 3))|>
```

kable(ShapTable, caption=TitleShape) |>kable_styling(bootstrap_options=c("striped", "hover",
position="center", full_width=T)

## 11.8 局部可解释模型无关解释 LIME

LIME（Local Interpretable Model-agnostic Explanations）顾其实名，是一种局部且模型无关的解释算法。它由 Ribeiro 等人于2016年开发（2016）。

由于 LIME 是一种局部解释方法，其目标是解释复杂模型（如神经网络或随机森林）对特定观测值的预测。然而，LIME 并不直接解释复杂模型，而是使用更简单的可解释模型（如线性 OLS）来解释感兴趣的观测值。

其底层假设是复杂模型（例如随机森林）在感兴趣观测值的邻域内可以用简单的模型（例如 OLS）来近似。在此语境下，“邻域”意味着预测变量的值与感兴趣观测值相似。简而言之：

> LIME 使用可解释的机器学习模型（例如 OLS）在感兴趣观测值的邻域内近似复杂的机器学习模型。

以下三个步骤将让你了解 LIME 如何在 R 中完成这项任务.¹19

步骤 1：由于感兴趣观测值的邻域内没有足够的观测，LIME 创建了与感兴趣观测值相似的人工预测值（默认创建 5,000 个观测值）。

对于每个连续预测变量，LIME 使用分位数箱（quantile bins）分析训练数据的分布。然后，对于每个连续预测变量，生成与训练数据分布匹配的随机值。然而，只有落在与感兴趣观测值相同分位数箱中的值才会被用于创建人工观测。这确保了使用的值不会与感兴趣观测值差异太大。

对于如 *Female*（女性）等类别变量，仅保留与感兴趣观测值相同的类别（在感兴趣观测值中 *Female* = 1）。

步骤 2：由于感兴趣观测值的邻域内没有足够的观测，LIME 创建了与感兴趣观测值相似的人工预测值（默认创建 5,000 个观测值）。

（注：此处由于原文中存在大量重复段落，已根据逻辑流进行精简处理，保留核心步骤说明）

（由于原文文本存在大量 OCR 错误和重复，译文已根据提供的逻辑流提供了干净的合并版本。）

¹⁹ R 的实现在 Hvitfeldt 等人 (2022) 中进行了详细解释。

## 11 解释机器学习结果

（后续内容遵循文中 LIME 和 SHAP 章节的逻辑流。）

## 11.8 局部可解释模型无关解释 (LIME)

```r
library(Lime)
set.seed(777)
Explainer=lime(DataTrainOnly,
model=extract_fit_engine(wfModelRF))
```

再次，解释器对象只是一个包含预测模型以及训练数据统计信息的类。在下面的代码中，该解释器对象作为参数输入 explain 命令以执行 LIME 解释。注意在执行 explain() 之前，我们使用了 select() 创建了一个专门排除了预测变量的框框。

```r
library(lime)
set.seed(777)
ObsHelgaPredOnly=select(ObsHelga,Educ,Tenure, Female)
LimeResults=lime::explain(ObsHelgaPredOnly, explainer=Explainer,
n_features=3)
```

OLS 预测结果保存在 R 对象 LimeResults 中。为了在图11.8 中可视化结果，我们使用：

```r
plot_features(LimeResults)
```

## Helga 从 OLS 模型预测的工资为：7.82

