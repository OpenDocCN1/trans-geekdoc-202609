

## 10.3 决策树

有关运行练习的详细帮助（包括针对 Windows 和 Mac 用户的视频），请参阅：https://blog.lang-analytics.com/2024/01/interactsessions.html

**请不要跳过这个交互部分**，因为它提供了所有已涵盖概念的应用，并将进一步扩展你目前为止所学到的知识。

以下是下载交互部分的链接：
https://ai.lang-analytics.com/exec/?file=15-TreeBasedExerc100.Rmd

在交互式项目中，你可以更改 `set.seed()` 中的参数来创建不同的训练和测试数据，并观察基于测试数据的 `confusion matrix`（混淆矩阵）以及相关指标如何变化。你还可以观察*决策树*结构的变化，因为通过下面的代码块，你将为生成的*决策树*生成图形化表示形式。

要创建新的*决策树*，你只需要更改 `set.seed()` 命令中的参数并执行代码。我们推荐以下步骤：

- **步骤 1：** 保持 `set.seed(7777)` 不变并执行代码。
- **步骤 2：** 截屏或使用手机拍摄测试数据的*混淆矩阵*以及*决策树*结构的图形化表示图。
- **步骤 3：** 将 `set.seed()` 的值更改为你喜欢的任何值，并返回步骤 2。

根据你的需要反复重复 **步骤 2** 和 **步骤 3** 并保存结果。完成后，对比截图或照片中的结果。你可能会发现，混淆矩阵和指标没有发生太大变化，而*决策树*的结构发生了显著变化。

```
set.seed(777)
Split7525=initial_split(Titanic, strata=Survived)
DataTrain=training(Split7525)
DataTest-Titanic=testing(Split7525)

RecipeTitanic=recipe(decision_tree(tree_depth=3), data=DataTrain) |>
ModelDesignDecisionTree=decision_tree(tree="rpart") |>
  set_engine("rpart") |>
  set_mode("classification")
```

```
WfModelTitanic=workflow() |>
```

```
add_model(ModelDesignTree) |>
add_recipe(RecipeTitanic) |>
fit(DataTrain)
```

DataTestWithPred=augment(WfModelTitanic, new_data=DataTest)

# 为了可读性，我们交换了正负类，
# 将 TRUE 设置为正类。

```
library(tidymverse)
DataTestWithPred=mutate(DataTestWithPred,
  Survived=fct_relevel(Survived,"TRUE","FALSE"),
  .pred_class=fct_relevel(pred_class,"TRUE","FALSE"))
```

```
library(rpart.plot)
rpart.plot(extract_fit_engine(WfModelTitanic),
  yes.text="YES",no.text="NO",roundint=FALSE)
```

con_mat(DataTestWithPred,truth=Survived,estimate=pred_class)
metricSetTitanic=metric_set(accuracy, sensitivity, specificity)
metricSetTitanic(DataTestWithPred,truth-Survived,estimate=pred_class)

```

总结来说，解释决策树是简单且直接的。然而，决策树结构对微小变化如此敏感，这是使用决策树解决现实世界问题的主要障碍。想象一个不负责任的研究人员，不断更改 `set.seed()` 的值，直到决策树的结构反映出他们想要看到的结果。

既然决策树的可解释性存在缺陷，而且它们的预测质量虽然并不但会被其他机器学习模型超越，我们为什么在本章中介绍决策树呢？

原因是组合多个决策树提供了非常强大的预测质量。相同或不同类型机器学习模型的组合被称为集成（ensemble）。

将许多决策树组合为一个集成正是随机森林（Random Forest）和提升树（Boosting Trees）模型的功能。我们将在后续章节中介绍这些集成模型。

## 10.4 随机森林

随机森林是一种用于分类和回归任务的集成模型。随机森林由许多（有时是数百或数千）略有不同的决策树组成。在创建这些决策树时，涉及到随机性。因此名为随机森林。

由于随机森林中的决策树略有不同，它们产生的预测结果也略有不同。随机森林模型的预测计算为所有不同决策树预测结果的聚合。

- 在回归情况下，随机森林的预测是通过其决策树的平均预测值计算的。
- 在二分类情况下，由大多数决策树预测的类别将是随机森林的预测类别。有时，这被称为针对特定类别的“决策树投票”。

### 10.4.1 随机森林的原理

尽管随机森林内部的每个决策树并不适合预测（弱学习器），但其理念是决策树的聚合会带来良好的预测质量。

弱学习器组合可以产生强大预测的观点，类似于 Galton (1907) 描述的“群体智慧”（Wisdom of Crowds）现象：

在英国参加牲畜和禽类展览的访客对一头牛的重量进行了猜测。尽管大多数访客的预测有误，但惊讶的是，所有预测的平均值与牛的实际重量非常接近。

为了产生不同的预测，随机森林中的决策树必须具有多样性——类似于 Galton 牲畜禽类展览中多样化的访客。问题是：

随机森林模型如何确保决策树是（略微）不同的？

随机森林采用了两种策略来确保多样性：

**随机空间方法（Random Subspace Method）：** 每当创建一个决策树时，随机森林模型并不考虑所有的特征，而是考虑特征的随机子集。因此，例如，如果我们有七个特征，每个决策树只考虑随机选择的特征。这限制了单个树的预测质量，但增加了树之间的多样性。

**自助法（Bagging）：** 每当创建一个决策树时，随机森林模型使用不同的训练数据集。这些不同的训练数据集是从原始数据中有放回地采样，直到新的训练数据集与原始数据集相同。这种过程被称为自助法（Bootstrapping）。

### 自助法与袋外数据

下表显示了一个训练数据集以及从其派生的两个自助样本：

| ID | Name | Sex | Age | Bootstrap Sample 1 ID | Name | Sex | Age | Bootstrap Sample 2 ID | Name | Sex | Age |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | Adam | m | 22 | 7 | Gert | m | 18 | 6 | Fiona | f | 87 |
| 2 | Bertha | f | 54 | 7 | Gert | m | 18 | 3 | Carlos | m | 32 |
| 3 | Carlos | m | 32 | 7 | Carlos | m | 32 | 5 | Ernst | f | 32 |
| 4 | Dora | f | 21 | 6 | Fiona | f | 87 | 4 | Dora | f | 21 |
| 5 | Ernst | m | 32 | 2 | Bertha | f | 54 | 6 | Fiona | f | 87 |
| 6 | Gert | f | 87 | 2 | Gert | f | 87 | 1 | Adam | m | 22 |
| 7 | Gert | m | 18 | 2 | Bertha | f | 32 | | | | |

假设这两个自助样本用于构建决策树 1 和决策树 2，我们看到自助样本 1 包含了 Bertha、Carlos 和 Gert 的观测值。同时，Adam、Dora 和 Ernst 不在这个数据集中。Adam、Dora 和 Ernst 的观测值未用于训练决策树 1。由于这些观测值不在决策树 1 的“袋”中，因此它们被称为袋外数据（Out-of-Bag data）。

**袋外（OOB）数据**非常有用，因为它们可以用于验证。之后，它们从未被用于训练相关的决策树。OOB 观测值的数量也相当大，因为落在 OOB 数据中的观测值期望值是训练数据集的三个之一。

作为一个练习，寻找决策树 2 的 OOB 数据。

