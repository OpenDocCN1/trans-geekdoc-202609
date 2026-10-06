

## 324 解释机器学习结果

```r
PercYoung25, PercOld65,
PercFoodSt, Population) |
mutate(Population=frequency_weights(Population))
```

```r
set.seed(2021)
Split85=DataVx | initial_split(prop=0.85,
                               strata=PercVacFull,
                               breaks=3)
```

DataTrain=training(Split85)
DataTest=testing(Split85)

回想一下第 10.4.2 节，Population（人口）并不是一个预测变量。相反，我们使用美国每个县的人口对该县的观测值进行加。这就是为什么变量 `Population` 被标记为 `frequency_weights`。

在 R 代码中，我们创建了配方（recipe）、模型设计，将两者都加入工作流（workflow），并使用训练数据拟合工作流：

```r
set.seed(2021)
RecipeVax=recipe(PercVacFull ~ ., data=DataTrain)
library(parallel)
ModelDesignRandFor=random_forest(min_n=5, mtry=2, trees=2000) |
  set_engine("ranger", num.threads=detectCores()) |
  set_mode("regression")
```

```r
wfModelVax=workflow() |
  add_model(ModelDesignRandFor) |
  add_recipe(RecipeVax) |
  fit(DataTrain)
```

上述，我们使用并行处理来加速创建拟合的随机森林工作流的过程。我们将线程数设置为 `num.threads=detectCores()`，这决定了计算机拥有多少个核心。

接下来，我们为 SHAP 值构建解释器对象（explainer object）。正如第 11.5 节所示，`explainer` 包与其他解释性包一样，在所谓的“解释器对象”中存储关于待分析模型、训练数据集以及相应方法方法的额外信息。然后，该解释器对象被用作实际分析命令的输入。

### 11.7 预测变量的 SHAP 贡献

在 R 代码中，我们使用 `explainer` 包中的 `explain_tidymodels` 命令，它允许我们直接从 `wfModelVax 工作 工作流创建解释器对象。`explain_tidymodels()` 命令要求分配给 `data` 参数的训练数据。这就是为什么我们首先使用 `select()` 来创建一个仅包含预测变量的数据框。结果变量 `PercVacFull`（某县完全接种成年人的比例）通过 `outcome` 参数提供，且 `verbose=FALSE` 抑制了消息。

现在，一切都准备就绪，可以使用 `predict_parts()` 命令计算一个观测值的 SHAP 值。在下方的交互部分中，你可以创建并解释几乎任何县的 SHAP 值，但目前我们保留并选择了洛杉矶县。在数据框中，洛杉矶的 `CountyID=133`，这意味着洛杉矶的观测值是数据集的第 133 行。

图 11.7 中的图表显示条形表示相应预测变量的 SHAP 值，垂直轴上的标签表示预测变量在洛杉矶的值。重叠的条形表示 25 种场景（预测变量的随机排序）的 SHAP 值的分布。你可以在下方找到生成图 11.7 的 R 代码：

```r
set.seed(2021)
CountyID=133
SHAPobject<-predict_parts(
  explainer=ExplainerRandForest,
  new_observation=DataVx[CountyID],
  type="shap", B=25)

plot(SHAPobject)
```

我们使用参数 `new_observation=DataVx[CountyID]` 为洛杉矶的观测值创建 SHAP 值。此外，我们创建的解释器对象赋值给参数 `explainer=` 以及参数 `B=25`。

## 11 解释机器学习结果

洛杉矶 (PredVac LA = 0.696, Coalition: none= 0.507)

![](img/f240d44919f5add983daf6c38e4fe3_342_0.png)

图 11.7 加州洛杉矶的 SHAP 值

我们只想使用 25 种场景（在 $2^7 = 128$ 种可能的排序中选择预测变量的不同排序）。

*洛杉矶*的 SHAP 值和预测变量的值在图 11.7 中可视化，并在表 11.1 的 *SHAP* 和 *County* 列中显示。我们还在 *Nation* 列中添加了预测变量的美国数值。这些值没有被用于创建 *SHAP* 值，但它们将有助于稍后解释 SHAP 值。

正如第 11.2 节所示，随机森林模型对洛杉矶县的预测值 ($PredVac_{LA}=0.696$) 与 Coalition $(none=0.507)$ 之间的差异等于所有 SHAP 值的和：

¹²Kuhn and Slice (2022). 详情见节 18.5。
¹³值从 SHAP 对象提取：`SHAPobject %>% as_tibble() %>% filter(row==0) %>% select(shap, County, variable=variable)`。
¹十四该值从 SHAP 对象提取：`round(attr(SHAPobject, "prediction"),3)`。
¹⁵该值从 SHAP 对象提取：`round(round(attr(SHAPobject, "intercept")),3)`。注意，该值不等于国家接种率，因为 Coalition: none 是从训练数据的平均值计算得出的，而不是所有数据。此外，平均 SHAP 计算没有根据县的人口进行加权。

### 11.7 预测变量的 SHAP 贡献

**表 11.1** 洛杉矶 (PredVac LA=0.696, Coalition: none=0.507 )

| 变量 | SHAP | County | Nation |
| :--- | :--- | :--- | :--- |
| PercAsian | 0.074 | 0.144 | 0.063 |
| PercBlack | 0.001 | 0.078 | 0.136 |
| PercFoodSt | 0.011 | 0.011 | 0.087 |
| PercHisp | -0.001 | 0.085 | 0.175 |
| PercOld65 | -0.011 | 0.196 | 0.116 |
| PercRep | 0.011 | 0.277 | 0.278 |
| PercYoung25 | -0.069 | 0.313 | 0.095 |

