
## 自动调优搜索选项

`Number of evaluations per iteration` 指定一次迭代中的调优评估次数。此选项仅在搜索方法为 `Genetic algorithm` 或 `Bayesian` 时可用。默认值是 10。取值范围为 2 到 2,147,483,647。

`Maximum number of evaluations` 指定调优评估的最大次数。此选项仅在搜索方法为 `Genetic algorithm` 或 `Bayesian` 时可用。默认值是 50。取值范围为 3 到 2,147,483,647。

`Maximum number of iterations` 指定调优迭代的最大次数。此选项仅在搜索方法为 `Genetic algorithm` 或 `Bayesian` 时可用。默认值是 5。取值范围为 1 到 2,147,483,647。

`Sample size` 指定样本大小。此选项仅在搜索方法为 `Random` 或 `Latin hypercube sample` 时可用。默认值是 50。取值范围为 2 到 2,147,483,647。

自动调优搜索还关联了一些通用选项。

`Validation method` 指定用于查找目标值的验证方法。如果您的数据已分区，则使用该分区。`Validation method`、`Validation data proportion` 和 `Cross validation number of folds` 全部将被忽略。

`Partition` 指定使用分区验证方法。使用分区时，您指定用于将观测值随机分配到各个角色的比例。

`Validation data proportion` 指定用于 `Partition` 验证方法的数据比例。默认值是 0.3。

`K-fold cross validation` 指定使用交叉验证方法。在交叉验证中，每次模型评估需要 k 次训练执行（在 k-1 个数据折上）和 k 次评分执行（在一个保留折上）。这会使评估时间大约增加 k 倍。

`Cross validation number of folds` 指定交叉验证过程中分区折的数量（上面定义的 k）。可能的值范围为 2 到 20。默认值是 5。

## 目标函数选项

`Nominal target objective function` 指定为名义目标调优参数而优化的目标函数。可能的值为 `average squared error`、`area under the curve`、`F1 score`、`F0.5 score`、`gamma`、`Gini coefficient`、`Kolmogorov-Smirnov statistic`、`multi-class log loss`、`misclassification rate`、`root average squared error` 和 `Tau`。默认值是 `misclassification rate`。

`Interval target objective function` 指定为区间目标调优参数而优化的目标函数。可能的值为 `average squared error`、`mean absolute error`、`mean square logarithmic error`、`root average squared error`、`root mean absolute error` 和 `root mean square logarithmic error`。默认值是 `average squared error`。

`Maximum time (minutes)` 指定优化调优器的最大时间（分钟）。

`Maximum training time for single model (in minutes)` 指定单个模型训练的最大时间（分钟）。如果留空（默认值），则没有最大时间限制。

![图 1.1 部分 JMP 帮助选项](Images/Image733.png)

# Demo 8.2：使用森林建模二元目标

在本演示中，您向课程 3 流程中添加一个 `Forest` 节点。您构建一个默认的森林模型，更改一些设置，并将该模型与其他流程中的模型进行比较。

1. 在流程中，右键单击 `Variable Selection` 节点并选择 `Add child node` → `Supervised Learning` → `Forest`。

![图 1.1 部分 JMP Help Options](Images/Image1229.png)

2. 将森林的所有属性保持为默认值。运行 `Forest` 节点。

3. 打开该节点的結果。

4. 单击 `Assessment` 选项卡。

![图 1.1 部分 JMP Help Options](Images/Image1237.png)

`Fit Statistics` 表显示在 `VALIDATE` 分区上的平均平方误差为 0.0571。

此性能再次相当不错，比早期演示中调优的决策树更好（但不如梯度提升模型那么好）。但再次尝试通过更改一些默认设置来改进森林性能。

5. 关闭结果窗口。

6. 随机森林是由许多决策树组成的集合，因此树木数量对 resulting 模型准确性会产生显著影响。将 `Number of trees` 从 100 减少到 50。

通常，使用更多的树往往会提高森林的性能。然而，随着树木数量的增加，改进程度会下降。换句话说，在某个时间点，从学习更多树木中获得的预测性能提升将低于学习这些额外树木的计算时间成本。

7. 如果您对计算时间没有顾虑，树木越多，从袋外预测中获得的估计就越好（可靠）。您可以使用 `OOB` 错误率来确定树木数量。

在 `Tree-splitting Options` 属性下，将 `Class Target Criterion` 从 `Information gain ratio` 改为 `Entropy`。

`Information gain ratio` 是纯度的度量。而 `Entropy` 则是杂度的度量（相反）。`Entropy` 控制决策树如何决定分割数据。它影响决策树如何绘制其边界。

8. 将 `Maximum depth` 从 20 减少到 12。

9. 将 `Minimum leaf count` 从 5 增加到 15。

随机森林中的决策树通过让它们生长到较大的深度（默认最大深度为 20）和小叶大小（默认每个节点观测值的最小数量为 5）而被过度训练。这种方法的思想是，平均大量过度训练树的预测概率比使用单棵精细调优的决策树更稳健。

10. 将 `Number of interval bins` 从 20 增加到 100。

11. 清除选项 `Use default number of inputs to consider per split` 的复选框，该选项默认是可用输入数量的平方根。将此参数设置为 7（输入数的一半）。

这是随机森林的另一个关键方面：为每个节点考虑多少变量进行分割（即所有变量的随机子集，而不是考虑所有变量）。这可能会减少对最具影响力变量的偏向，并允许获得更具泛化能力的模型。您可以在多次训练运行中手动更改此选项。

![图 1.1 部分 JMP Help Options](Images/Image1244.png)

12. 运行 `Forest` 节点。

13. 打开该节点的結果。

14. 单击 `Assessment` 选项卡。

![图 1.1 部分 JMP Help Options](Images/Image12511.png)

调优后森林模型在 `VALIDATE` 分区上的平均平方误差为 0.0565。此拟合统计量比使用默认设置的第一個模型略好。

15. 关闭结果窗口。

16. 运行整个流程并查看模型比较的结果。

![图 1.1 部分 JMP Help Options](Images/Image1258.png)

基于默认的 `KS`，梯度提升模型现在是流程的冠军模型。森林是紧随其后的第二名模型。

17. 关闭结果窗口。

![图 1.1 部分 JMP Help Options](Images/Image889.png)

![图 1.1 部分 JMP Help Options](Images/Image1026.png)

## 练习：构建森林模型

1. 使用 `Autotune` 功能构建一个森林。在流程中 `Variable Selection` 节点下方添加一个 `Forest` 节点。使用 `Autotune` 功能。探索选择 `Autotune` 时可用的设置。

注意：此练习可能需要运行数分钟。

2. 为冠军模型选择了哪些标准？

- `Number of trees`
- `Number of variables per split`
- `Number of bins`
- `Maximum number of branches`
- `Maximum depth`

3. 自动调优的森林与流程中的其他模型相比如何，特别是与演示中构建的森林模型相比？请考虑拟合统计量平均平方误差进行此比较。

![图 1.1 部分 JMP Help Options](Images/Image1034.png)

## 树集成模型的优缺点
