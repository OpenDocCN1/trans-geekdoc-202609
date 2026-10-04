

`test_labels = test_frame['income_bracket'].apply(lambda x: '>50K' in x)`

`test_fn = tf.estimator.inputs.pandas_input_fn(`
` x=test_frame, y=test_labels,`
` num_epochs=1, shuffle=False)`

`metrics = classifier.evaluate(test_fn)`

`# Display metrics`

`print('\nEvaluation metrics:')`

`for key, value in metrics.items():`
` print(key, ': ', value)`

在执行此模块之前，您需要在当前目录中放置 `adult.data` 和 `adult.test` 文件。您还需要安装 pandas 数据分析包。

该模块首先为人口普查数据中的每个字段创建一个特征列。然后它创建了三个交叉列：一个将 `education` 和 `occupation` 列组合在一起，一个将 `native_country` 和 `occupation` 列组合在一起，一个将 `workclass` 和 `occupation` 列组合在一起。

创建交叉列后，该模块创建了一组用于 DNN 分类器的特征列。您不能将分类列馈送到神经网络，因此该模块通过调用 `tf.feature_column.indicator_column` 将分类列转换为密集列。

接下来，该模块创建了一个 `DNNCombinedLinearClassifier` 并为其提供了两组特征列。也就是说，它将交叉列定向到线性分类器，将密集列定向到 DNN。`dnn_hidden_units` 参数将神经网络配置为具有两个隐藏层：一个有 120 个节点，一个有 60 个节点。

创建分类器后，该模块调用其 `train` 和 `evaluate` 方法。为了训练分类器，该模块从 `adult.data` 读取字段并将 `DataFrame` 转换为数据集。训练过程包括 500 个 epoch，每个训练步骤都在包含 100 个数据点的随机批次上操作。

为了测试分类器，该模块将字段从 `adult.test` 读取到 `DataFrame` 中并将 `DataFrame` 转换为数据集。然后它打印 `evaluate` 返回的 dict 中包含的每个指标。在我的系统上，该模块显示以下结果：

`accuracy : 0.802285`
`accuracy_baseline : 0.763774`
`auc : 0.87448`
`auc_precision_recall : 0.710498`
`average_loss : 0.511923`
`label/mean : 0.236226`
`loss : 65.1142`
`prediction/mean : 0.336511`
`global_step : 195360`

在此列表中，`auc` 代表“曲线下面积”。该指标对于分类器很常见，因为它衡量分类器做出成功预测与不成功预测的可能性。

## 在集群中运行 Estimator

[第 11 章](#17_9788126592555-ch11.xhtml) 介绍了分布式 TensorFlow 应用程序，其中涉及作业、任务和服务器。您可以在分布式应用程序中运行 estimator，但您需要告诉 TensorFlow 关于集群以及运行 estimator 的服务器分配的任务。

您可以通过设置描述集群和服务器任务的 `TF_CONFIG` 变量来提供此信息。具体来说，您需要将 `TF_CONFIG` 设置为包含三个字段的 JSON（JavaScript Object Notation）对象：

* `cluster`: 集群的描述
* `task`: 节点的任务
* `job`: 作业的参数

您可以通过提供 `ClusterSpec` 实例的参数来设置第一个字段。如果您已有现有的 `ClusterSpec`，您可以通过调用其 `as_cluster_def` 方法获得合适的描述。

`task` 字段标识设置了 `TF_CONFIG` 的节点分配的任务。此字段本身有三个字段：

* `type`: 任务的类型（`worker`、`master` 或 `ps`）
* `index`: 作业内任务的索引
* `trial`: 要运行的试验的字符串标识符，以 `'1'` 开头

`TF_CONFIG` 的 `job` 字段描述节点的作业。分布式应用程序通常通过命令行参数接收此信息，因此您可以忽略此字段。以下代码向您展示了如何设置此变量：

```
TF_CONFIG = {
 'cluster': {'ps': ['host1:123'],
 'worker': ['host2:456']},
 'task': {
 'type': 'worker',
 'index': 0,
 'trial': '1'
 }
}
```

在这种情况下，集群有两个作业和两个任务。分配给具有此 `TF_CONFIG` 变量的节点的任务的索引为 `0`，类型为 `worker`。在这种情况下，集群有一个具有任务类型的作业，但这并不总是如此。您可以为作业分配任何名称，但任务的类型必须是 `worker`、`master` 或 `ps`。

## 访问实验

为了简化在分布式环境中执行 estimator 的过程，TensorFlow 提供了 `Experiment` 类。要在代码中使用 `Experiment`，您需要执行三个步骤：

1. **创建 estimator。**
2. **使用步骤 1 中创建的 estimator 构造 `tf.contrib.learn.Experiment` 的实例。**
3. **通过调用 `tf.contrib.learn.learn_runner.run` 启动实验。**

本讨论介绍了这些步骤并演示了如何使用实验对 MNIST 图像进行分类。[第 13 章](#19_9788126592555-ch13.xhtml) 介绍了在云中启动实验的应用程序。

### 创建实验

每个实验都需要一个 estimator 和训练与评估函数。您可以通过调用其构造函数创建 `tf.contrib.learn.Experiment`，其参数列在 [表 12-3](#18_9788126592555-ch12.xhtml#c12-tbl-0003) 中。

[TABLE 12-3](#18_9788126592555-ch12.xhtml#rc12-tbl-0003) Experiment 构造函数的参数

| **Parameter** || **Default** || **Description** |
| --- | --- | --- |
| `estimator` || `--` || Estimator to be launched by the experiment |
| --- | --- | --- |
| `train_input_fn` || `--` || Function that returns training features and labels |
| `eval_input_fn` || `--` || Function that returns evaluation features and labels |
| `eval_metrics` || `None` || Evaluation metrics to monitor |
| `train_steps` || `None` || Number of training steps |
| `eval_steps` || `None` || Number of evaluation steps |
| `eval_hooks` || `None` || Session hooks to pass to the estimator |
| `eval_delay_secs` || `120` || Number of seconds to wait before evaluating |
| `continuous_eval_throttle_secs` || `60` || Number of seconds to wait after the start of evaluation before re-evaluating |
| `min_eval_frequency` || `None` || Minimum number of steps between evaluations |
| `delay_workers_by_global_step` || `False` || Bool that specifies whether to delay training workers by global step instead of time |
| `export_strategies` || `None` || Export strategies |
| `train_steps_per_iteration` || `None` || Number of training steps in each training-evaluation iteration |
| `checkpoint_and_export` || `False` || Bool that specifies whether to save checkpoints and exports during training |

构造函数的最重要的参数是第一个，它标识实验将执行的 estimator。第二和第三个参数标识实验应用于训练和评估 estimator 的函数。

`train_steps` 参数标识训练过程中要执行的步骤数。如果您未设置此参数，estimator 的训练将无限期继续。`eval_steps` 参数指定测试期间应执行的步骤数。如果您未设置此参数，测试将一直继续，直到有输入数据可用。

### 实验类的方法

创建 `Experiment` 后，您可以访问其方法。[表 12-4](#18_9788126592555-ch12.xhtml#c12-tbl-0004) 列出了这些方法并提供了每个方法的描述。

[TABLE 12-4](#18_9788126592555-ch12.xhtml#rc12-tbl-0004) Experiment 类的方法

| **Method** || **Description** |
| --- | --- |
| `train(delay_secs=None)` || Train the estimator with training data |
| --- | --- |
| `evaluate(delay_secs=None, name=None)` || Evaluate the estimator with test data |
| `train_and_evaluate()` || Train and evaluate the estimator |

