
正如我们在前一张图表中所见，预测值与真实值紧密对齐。它们几乎与标记完美预测的对角线重合。

## 使用 H2O 进行 AutoML

我们继续考察复杂的 AutoML 框架。与 FLAML 一样，H2O 也是强大开源平台的首选之一。H2O[11](#chap08.xhtml#footnote-063) 提供了一个与 FLAML 类似的界面，允许在指定限制（如时间预算或固定迭代次数）内测试各种前沿算法。

H2O 网站 `https://docs.h2o.ai/h2o/latest-stable/h2o-docs/automl.html` 上的描述如下：

> 尽管 H2O 让非专家也能轻松尝试机器学习，但要生成高性能的机器学习模型，仍然需要相当多的数据科学知识和背景。为了让机器学习软件真正让非专家也能使用，我们设计了一个易于使用的界面，自动化了训练大量候选模型的过程。H2O 的 AutoML 对于高级用户也是一个有用的工具，它提供了一个简单的封装函数，执行大量与建模相关的任务——这些任务通常需要编写许多代码行——并腾出他们的时间，专注于数据科学流程的其他方面，如数据预处理、特征工程和模型部署。

让我们评估该框架，以验证这些说法的准确性。安装后，我们从初始化阶段开始：

```
!pip3 install -q h2o
```

```
import h2o
from h2o.automl import H2OAutoML
```

该代码在本地初始化一个 `H2O` 实例并准备建模数据：

```
h2o.init()
```

`H2O` 启动一个（本地）服务器来运行实验。这是因为 `H2O` 需要在运行任何机器学习实验之前建立这个本地服务器，该服务器在 `H2O` 初始化时会自动启动：

```
Checking whether there is an H2O instance running at http://localhost:54321..... not found.
Attempting to start a local H2O server...
Starting server
Server is running at http://127.0.0.1:54321
Connecting to H2O server at http://127.0.0.1:54321 ... successful.
```

此步骤确保 `H2O` 服务器实例正在运行，以便高效地跨可用系统资源分配计算。

唯一的前提是通过将预测目标标记为 `target` 并将 Pandas `DataFrame` 转换为 `H2O` 容器来格式化数据：

```
df['target'] = df['Close'].shift(-ahead)
df.dropna(inplace=True)
# 'df' : pandas DataFrame with the target variable named 'target'
h2o_df = h2o.H2OFrame(df)
```

```
Parse progress: |████████████████████████████████████████████████████████████████| (done) 100%
```

然后，该 `H2O` 容器通过 `h2o_df.split_frame()` 函数划分为训练集和测试集。与 AutoML 引擎随后执行的大量过程相比，此任务只需极少的工作量：

```
# Split the data into train and test sets
train, test = h2o_df.split_frame(ratios=[.8], seed=42)

# Identify predictors and response
x = train.columns
y = "target"
x.remove(y)

# Run AutoML for x base models (limited here for speed)
aml = H2OAutoML(max_models=5, seed=1)
```

此 `H2OAutoML()` 命令按以下规范执行 `H2O` 引擎：

*   `max_models=5`：将基础模型数量限制为 5 个，确保快速执行。当然，可以增加此数字以探索更广泛的模型范围。
*   `seed=1`：设置随机种子以保证可复现性，确保多次运行的结果保持一致。

以下代码 `aml.train()` 使用以下参数启动训练过程：

*   `x`：特征列（自变量）。
*   `y`：目标列（因变量）。
*   `training_frame=train`：用于训练的数据集。

```
aml.train(x=x, y=y, training_frame=train)
```

该过程首先通过消除对预测无用的常数列来进行特征选择：

```
06:24:28.549: _train param, Dropping unused columns: [DX-Y.NYB_Volume]
██████████████████████████████████████████████████████| (done) 100%
```

经过几轮尝试后，随机森林回归器 `H2ORandomForestEstimator` 脱颖而出，成为最佳候选模型：

```
Model Details
=============
H2ORandomForestEstimator : Distributed Random Forest
Model Key: DRF_1_AutoML_1_20240226_62057
```

随后，引擎评估最佳模型：

```
ModelMetricsRegression: drf
** Reported on cross-validation data. **
MSE: 0.002954176243244988
RMSE: 0.05435233429435196
MAE: 0.04027944498639655
```

与我们早期使用 FLAML AutoML 引擎的尝试（`RMSE: 0.07`）相比，这一误差量级（`RMSE: 0.05`）代表了一个进步。

此外，`H2O` 报告强调了每个特征的重要性。值得注意的是，在 OHLC 之后，最重要的特征是在我们初步的相关性图探索中被识别为高度相关的特征，具体为 TIP Inflation Protected 和 LQD Corporate Bonds：

```
Variable importance:
| variable || relative_importance || scaled_importance || percentage |
| --- | --- | --- | --- |
| Close || 10857.5126953 || 1.0 || 0.2762052 |
| --- | --- | --- | --- |
| Low || 5061.9379883 || 0.4662152 || 0.1287711 |
| High || 4167.9204102 || 0.3838743 || 0.1060281 |
| Open || 3686.7221680 || 0.3395549 || 0.0937868 |
| TIP_Open || 1184.7832031 || 0.1091211 || 0.0301398 |
| TIP_High || 1182.2382812 || 0.1088867 || 0.0300751 |
| LQD_Open || 725.5785522 || 0.0668273 || 0.0184581 |
| TIP_Close || 583.2502441 || 0.0537186 || 0.0148374 |
| LQD_Close || 552.1102905 || 0.0508505 || 0.0140452 |
```

表 8.1：特征重要性

此外，查看排行榜可以让我们识别出尝试中表现最好的模型：

```
# View the AutoML Leaderboard
aml.leaderboard
```

一个非常有趣的选项是利用排行榜上的顶尖候选模型创建一个集成算法（元学习器），组合这些领先算法，从而可能进一步提高准确性：

```
# Get model ids for all models in the AutoML Leaderboard
model_ids = list(aml.leaderboard['model_id'].as_data_frame().iloc[:,0])

# Get the "All Models" Stacked Ensemble model
se = h2o.get_model([mid for mid in model_ids if "StackedEnsemble_AllModels" in mid][0])

# Get the Stacked Ensemble metalearner model
metalearner = se.metalearner()
```

调查集成元学习器（或组合器）算法内的变量重要性，揭示了每个基础学习器对整体集成的贡献程度。本质上，`H2O` 根据模型的性能能力智能地融合模型。随后，我们使用 `RMSE` 指标评估集成的误差量级：

```
# Evaluate the classifier on the test data
print('RMSE = ',np.sqrt(mean_squared_error(pred_df.values,test_df['target'].values)))
```

```
RMSE = 0.0496
```

该分数超过了排行榜顶尖模型的分数，这符合预期：集成策略通常优于寻找单一最佳候选模型，正如第 7 章《交易的高级机器学习模型》所见。与最佳单一模型（`RMSE` 从 0.05 降至 0.04）相比，该组合带来了约 0.04 的 `RMSE` 损失降低，标志着 20% 的改进；与 FLAML 的性能（`RMSE` 约为 0.07）相比，改进幅度更大，而后者已被视为一项重大成就。

虽然我们没有明确提及，但 AutoML 平台在训练期间会执行超参数优化，在后台微调模型以提高其性能。由于这一步骤在实现最佳结果中起着关键作用，我们现在将回顾其重要性，以及用于系统探索超参数空间的不同技术。

### 超参数优化
