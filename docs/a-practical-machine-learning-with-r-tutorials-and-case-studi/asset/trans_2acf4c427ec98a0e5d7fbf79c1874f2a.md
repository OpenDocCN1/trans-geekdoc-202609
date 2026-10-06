

# 10 基于树的模型 — 自举法（Bootstrapping）详解

我们从下载数据、选择结果变量和预测变量开始，稍后我们将使用它们对观测值加权。

```r
library(rio); library(tidymodels); library(xgboost)
DataVax<-import("https://ai.lang-analytics.com/DataVax.rds") |
  select(PercVacFull, PercCep,
  Percasian, PercBlack, PercHish,
  PercYoung25, PercOld65,
  PercFoodSt, Population) |
  mutate(Population=Frequency_weights(Population))
```

由于我们需要调整 XGBoost 算法的一些超参数，我们再次使用了第 6.6 节中的 10 步调优模板：

## 第一步 - 生成训练和测试数据：训练和测试数据如下：

```r
set.seed(2021)
Split85<-initial_split(DataVax, prop=0.85, strata=PercVacFull,
breaks=3)
```

```r
DataTrain<-training(Split85)
DataTest<-testing(Split85)
```

## 第二步 - 创建配方（Recipe）：下面的配方确定了结果变量 (PercVacFull) 并选择所有其他变量作为预测变量，这排除了 Population，因为该变量在加载数据和选择变量时已设置为 `frequency_weights()`：

```r
RecipeVax<-recipe(PercVacFull, data=DataTrain)
```

## 第三步 - 创建模型设计：模型设计使用 `tree()` 命令选择了一个梯度提升机器学习模型。XGBoost 算法位于 `set_engine()` 命令中，参数为 `xgboost`。由于我们预测的是连续变量（接种率），因此 `set_mode()` 设置为回归（regression）。

```r
ModelDesignBoostTrees<-boost_tree(trees=tune(), tree_depth=tune()) |
  set_engine("xgboost") |
  set_mode("regression")
```

对于 `boost_tree()` 命令，我们设置了两个超参数进行调优。超参数决定决策树的数量，而超参数 `tree_depth` 指定了每棵决策树的层数。

## 10.5 提升树算法（Boosting Trees Algorithms）

### 第四步 - 将配方和模型设计添加到工作流（Workflow）：与之前一样，我们将配方和模型设计添加到工作流中：

```r
WfModelVax=workflow()
add_model(ModelDesignBoostTrees)
add_recipe(RecipeVax)
add_case_weights(Population)
```

工作模型末尾的注释 `add_case_weights(Population)` 确保了观测值（美国县级）根据其人口进行加权。

步骤 1-4 已经为背景做了准备。下面，你可以执行来自 10 步调优模板的第 5-10 步的代码块。

在第五步中，是在参数网格（parameter grid）中尝试的超参数值。我们鼓励你尝试这些值。

在第六步中，选择了十折进行交叉验证（Cross-Validation）。你可以将 `v=10` 改为较小的值以加速调优过程。

第七步调优工作流模型。注意 `doParallel::register()` 命令执行的是并行调优。在使用之前，必须安装 `doParallel` 包，否则 R 将抛出错误。调优完成后，`autoplot` 将可视化所有所选超参数组合的交叉验证性能。

在第八步中，选择在交叉验证折中表现最好的超参数，并将它们用于第九步中的最终模型。

该最佳模型将在第十步在测试数据上进行评估。

将代码加载到 RStudio 后（请此本节开头的信息框），我们建议在不进行任何更改的情况下在浏览器中运行文档。之后，评估 `autoplot()` 生成的图表，相应地更改第五步中的超参数值并执行代码块。

```r
# Step 5 - 创建超参数网格
set.seed(2021)
ParGridVax=expand.grid(tree_depth=c(1, 2, 5, 10, 15),
trees=c(5, 10, 15, 50, 100))
```

```r
# Step 6 - 为交叉验证创建重采样
FoldsVax=vfold_cv(v=10, strata=PercVacFull, breaks=5)
```

```r
# Step 7 - 调优工作流并训练所有模型：
# 确保已安装 doParallel 包！！
doParallel::registerdoParallel()
```

```r
set.seed(2021)
StartTime=Sys.time()
TuneResultsVax=tune_grid(WfModelVax,
  resamples=FolsVax,
  grid=ParGridVax,
  metrics=metric_set(mae))
Runtime=Sys.time()-StartTime
```

```r
# 可视化调优结果
print("TUNING RESULTS:")
aplot(TuneResultsVax)
```

```r
# Step 8 - 提取在交叉验证折中表现最好的超参数
Bestax=select_best(TuneResultsVax, metric="mae")
```

```r
# Step 9 - 确定化并训练最佳模型：
set.seed(2021)
BestWfVax=finalize_workflow(WfModelVax, Bestax) %>%
fit(DataTrain))
```

```r
# Step 10 - 根据测试数据评估预测质量：
DataTestWithPred=augment(BestWfVax, new_data=DataTest)
MetricsTest=metrics(DataTestWithPred, truth=PercVacFull, estimate=.pred)
```

```r
# 打印调优时间
print("TUNING TIME:")
print(Runtime)
```

```r
# 调优出的最佳参数
print("BEST PARAMETERS:")
print(Bestax)
```

```r
# 打印最佳模型的指标
print("TESTING METRICS:")
print(MetricsTest)
```

当你在不更改代码的情况下运行上述代码块时，你的结果将与下面所示。

- **决策树**具有很高的教育价值，因为其图形化表示提供了一种直观的方法来查看哪些变量影响了预测。
- 作为独立模型，决策树不应用于解决现实世界的问题。原因如下：
    - 虽然大多数决策树规则具有相当的可解释性，但某些规则可能并不符合逻辑。与决策树原本良好的可解释性相比，这是一个严重的缺点。
    - 决策树的结构对超参数（如树深）的变化非常敏感。由于结构不稳定性，解释工作将变得困难且不可信。
    - 决策树是弱学习器，从这个角度来说，其他机器学习模型通常更好。
- 尽管决策树是弱学习器，但将许多决策树集成到随机森林或提升树模型中通常可以产生极佳的预测结果。
- **随机森林**模型是回归和分类任务的良好选择。当怀疑数据中存在非线性或预测变量之间的相互作用时，更是如此。
- 对于具有许多预测变量的复杂模型，深度学习模型（如神经网络）可能是更好的选择，并且在运行随机森林之外还需要运行这些模型作为对比，以评估它们是否表现更好。
- 如果运行随机森林模型时计算时间是一个问题，提升树算法（如 xgboost）可能是更好的选择。例如，XGBoost 的运行速度比随机森林快，且其预测质量与随机森林相似且往往更优。

