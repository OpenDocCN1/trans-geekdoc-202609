
`train(x, y, method = ‘rf’, preProcess = NULL,..., weights = NULL,metric = ifelse(is.factor(y), ‘Accuracy’, ‘RMSE’), maximize = ifelse(metric %in% c(‘RMSE’, ‘logLoss’), FALSE, TRUE), trControl = trainControl(), tuneGrid = NULL, tuneLength = 3)`

[表 5.7](#13_Chapter05.xhtml#tab5.7) 显示了 `train` 函数的各个参数的描述。

### 3. `expand.grid()`
这是一个用于微调机器学习算法某些超参数的高级函数。`expand.grid()` 函数内部的参数根据模型而变化。[¹](#13_Chapter05.xhtml#ch5-r-fn1)

## 表 5.6 | `trainControl()` 函数参数列表 (Anon, 2019, 2020, 2021; Source: https://www.rdocumentation.org/)

| 参数 | 定义 |
|---|---|
| `method` | 重采样方法：‘boot, ‘boot632, ‘cv’, ‘repeatedcv’, ‘LOOCV’, ‘LGOCV’（用于重复的训练/测试分割），‘none’（仅将一个模型拟合到整个训练集），‘oob’（仅适用于随机森林、袋装树、袋装 earth、袋装灵活判别分析或条件树森林模型），‘adaptive_cv’、‘adaptive_boot’ 或 ‘adaptive_LGOCV’ |
| `number` | 表示折数或重采样迭代次数 |
| `repeats` | 仅用于重复 k 折交叉验证：要计算的完整折集合的数量 |
| `verboseIter` | 用于打印训练日志的逻辑值。 |
| `returnData` | 用于保存数据的逻辑值 |
| `returnResamp` | 一个字符字符串，指示应保存多少重采样汇总指标。值可以是‘final、‘all 或 ‘none’ |
| `savePredictions` | 指示应保存每个重采样的保留预测的多少。值可以是‘all、‘final’ 或 ‘none’。也可以使用逻辑值，转换为‘all’（对于 true）或 ‘none’（对于 false）。‘final’ 保存最优调参的预测。 |
| `P` | 用于留组交叉验证：训练百分比 |
| `search` | ‘grid’ 或 ‘random’，描述调参网格的确定方式。 |
| `initialWindow, horizon, fixed-Window` | 创建时间切片的可能参数 |
| `classProbs` | 一个逻辑值；在每次重采样中是否应为分类模型计算类别概率（连同预测值）？ |
| `summaryFunction` | 用于计算重采样间性能指标的函数。函数的参数应与 defaultSummary 中的相同。 |
| `selectionFunction` | 用于选择最优调参的函数。可以是函数名称或函数本身。有关详细信息和其他选项，请参阅 best。 |
| `preProcOptions` | 要传递给 preProcess 的选项列表。预处理的类型（例如，中心化、缩放等）通过 train 中的 preProc 选项传入。 |
| `sampling` | 描述重采样后进行的额外采样类型的单个字符值（通常用于解决类别不平衡）。值包括‘none’、‘down’、‘up’、‘smote’ 或 ‘rose’。后两个值分别需要 DMwR 和 ROSE 包。此参数也可以是列表以便于自定义采样，详细信息可在 caret 包网站的采样（下方链接）中找到。 |
| `index` | 具有每个重采样迭代元素的列表。每个列表元素是对应于该迭代中用于训练的行整数向量。 |
| `indexOut` | 一个列表（与 index 长度相同），指定每个重采样保留的数据（以整数表示）。如果为 NULL，则使用不包含在 index 中的唯一样本集。 |
| `indexFinal` | 一个可选的整数向量，指示重采样后用于拟合最终模型的样本。如果为 NULL，则使用整个数据集。 |
| `timingSamps` | 将用于测量预测样本时间的训练集样本数（零表示不应估计预测时间。 |
| `predictionBounds` | 一个逻辑值或长度为 2 的数值向量（仅回归）。如果为逻辑值，预测可以被限制在训练集结果的范围内。例如，值 c(TRUE, FALSE) 仅限制预测的下端。如果为数值，可以使用特定边界。例如，如果为 c(10, NA)，低于 10 的值将被预测为 10（上侧无约束）。 |
| `seeds` | 一组可选的整数，将在每次重采样迭代时用于设置种子。当模型并行运行时很有用。NA 值将阻止在工作进程中设置种子，而 NULL 值将使用一组随机整数设置种子。或者，可以使用列表。列表应有 B+1 个元素，其中 B 是重采样次数，除非 method 为 ‘boot632’，此时 B 为重采样次数加 1。列表的前 B 个元素应为长度为 M 的整数向量，其中 M 为正在评估的模型数。列表的最后一个元素只需要一个整数（用于最终模型）。 |
| `adaptive` | 当 method 为 ‘adaptive_cv、‘adaptive_boot 或 ‘adaptive_LGOCV’ 时使用的列表。 |
| `trim` | 一个逻辑值。如果为 TRUE，object$finalModel 中的最终模型可能会删除对象的某些组件以减小保存对象的大小。predict 方法仍可工作，但模型的某些其他功能可能无法使用。修剪仅在已实现此功能的模型中进行。 |
| `allowParallel` | 如果已加载并可用的并行后端，函数是否应使用它？ |

## 表 5.7 | 训练函数参数列表 (Anon 2019, 2020, 2021; Source: https://www.rdocumentation.org/)

| 参数 | 描述 |
|---|---|
| `x` | 一个对象，其中样本在行中，特征在列中。这可以是简单的矩阵、数据框或任何其他类型（例如稀疏矩阵）。 |
| `y` | 一个包含每个样本结果的数值或因子向量。 |
| `weights` | 案例权重的数值向量。此参数仅影响允许案例权重的模型。 |
| `…` | 传递给分类或回归例程的参数（如 randomForest）。如果在此处传递调参的值，将会出错。 |
| `preProcess` | 定义预测变量数据预处理的字符串向量。当前可能性包括‘BoxCox’、‘YeoJohnson、‘expoTrans、‘center、‘scale’、‘range’、‘knnImpute、‘bagImpute、‘medianImpute’、‘pca’、‘ica 和 ‘spatialSign’。默认无预处理。有关程序及如何调整，请参阅 preProcess 和 trainControl。预处理代码仅设计用于 x 为简单矩阵或数据框时。 |
| `metric` | 指定将用于选择最优模型的汇总指标的字符串。默认情况下，可能的值为回归的‘RMSE’和‘Rsquared’以及分类的‘Accuracy’和‘Kappa’。如果使用自定义性能指标（通过 trainControl 中的 summaryFunction 参数），metric 的值应与其中一个参数匹配。如果不匹配，将发出警告并使用 summaryFunction 给出的第一个指标。（注意：如果给出，此参数必须命名。） |
| `maximize` | 一个逻辑值：指标应最大化还是最小化？ |
| `trControl` | 定义此函数行为的值列表。参阅 trainControl 和 http://topepo.github.io/caret/training.html#custom。（注意：如果给出，此参数必须命名。） |
| `tuneGrid` | 包含可能调参值的数据框。列名与调参参数相同。使用 getModelInfo 获取每个模型的调参参数列表，或参阅 http://topepo.github.io/caret/available-models.html。（注意：如果给出，此参数必须命名。） |
