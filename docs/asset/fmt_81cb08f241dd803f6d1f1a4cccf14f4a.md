
| `delay_workers_by_global_step` || `False` || Bool that specifies whether to delay training workers by global step instead of time |
| `export_strategies` || `None` || Export strategies |
| `train_steps_per_iteration` || `None` || Number of training steps in each training-evaluation iteration |
| `checkpoint_and_export` || `False` || Bool that specifies whether to save checkpoints and exports during training |

### 构造函数

构造函数的最重要的参数是第一个，它标识实验将执行的 estimator。第二和第三个参数标识实验应用于训练和评估 estimator 的函数。

`train_steps` 参数标识训练过程中要执行的步骤数。如果您未设置此参数，estimator 的训练将无限期继续。`eval_steps` 参数指定测试期间应执行的步骤数。如果您未设置此参数，测试将一直继续，直到有输入数据可用。

### 实验类的方法

创建 `Experiment` 后，您可以访问其方法。表 12-4 列出了这些方法并提供了每个方法的描述。

TABLE 12-4 Experiment 类的方法

| **Method** || **Description** |
| --- | --- |
| `train(delay_secs=None)` || Train the estimator with training data |
| --- | --- |
| `evaluate(delay_secs=None, name=None)` || Evaluate the estimator with test data |
| `train_and_evaluate()` || Train and evaluate the estimator |
| `test()` || 训练、评估并导出一步 |
| `continuous_eval(delay_secs=None, throttle_delay_secs=None, evaluate_checkpoint_only_once=True, continuous_eval_predicate_fn=None, name='continuous')` || 持续评估估计器 |
| `continuous_eval_on_train_data( delay_secs=None, throttle_delay_secs=None, continuous_eval_predicate_fn=None, name='continuous_on_train_data')` || 使用训练数据持续评估估计器 |
| `continuous_train_and_eval(*args, **kwargs)` || 交替进行训练和评估 |
| `extend_train_hooks(additional_hooks)` || 为训练关联额外的会话钩子 |
| `reset_export_strategies(new_export_strategies=None)` || 关联新的导出策略 |
| `run_std_server()` || 启动 TensorFlow 服务器并加入服务线程 |

前四种方法使用和理解起来都很直接。`train` 方法将无限期继续，除非你在构造函数中设置了 `train_steps` 参数。`evaluate` 将持续测试直到其输入耗尽或达到 `eval_steps` 参数为止。在这两种方法中，你可以通过设置 `delay_secs` 参数来指定实验应等待多长时间。

`continuous_eval` 和 `continuous_eval_on_train_data` 方法都执行重复评估。你可以通过将 `continuous_eval_predicate_fn` 分配给合适的函数来控制评估是否继续。该函数接收前一次评估的结果并确定是否应继续评估。

`continuous_train_and_eval` 方法为实验性，随时可能更改。这会遍历训练和评估，你可以使用构造函数的 `train_steps_per_iteration` 参数设置每次训练的步数。

### 运行实验

你可以通过调用 `tf.contrib.learn.learn_runner.run` 来训练和/或评估实验。该函数接受四个参数：

* `experiment_fn`: 返回实验的函数
* `schedule`: 要调用的实验方法
* `run_config`: 提供配置设置的 `RunConfig`
* `hparams`: 提供实验额外数据的 `HParams`

要调用此函数，你需要将第一个参数分配给一个接收两个参数的函数：一个 `RunConfig` 和一个 `HParams`。该函数必须返回一个 `Experiment`。

每个估计器构造函数都有一个 `config` 参数，可接受 `tf.contrib.learn.RunConfig` 实例。`run` 方法的 `run_config` 参数接受相同类型的 `RunConfig`。请记住，`model_dir` 字段告诉实验将其输出存储在何处。

你可以使用 `tf.contrib.training.HParams` 的实例将数据传递给 `experiment_fn` 函数。构造函数接受一个或多个用逗号分隔的键值对。以下代码展示了如何创建 `HParams` 实例：

```
hparams = tf.contrib.training.HParams(learning_rate=0.01, hidden_units=[10, 20])
```

`schedul`e 参数标识应调用哪个实验方法。你可以通过设置 `RunConfig` 的 `model_dir` 字段来控制方法返回值应存储的位置。

### 将理论付诸实践

`ch12/experiment.py` 模块中的代码演示了如何创建和启动实验。该实验使用类似于 `ch12/dnn_class.py` 中估计器的 `DNNClassifier` 分析 MNIST 数据。 Listing 12-4 展示了代码。

LISTING 12-4 使用实验对 MNIST 图像进行分类

```
#### Set parameters
batch_size = 80
image_dim = 28
hparams = tf.contrib.training.HParams(
 num_labels=10,
 batch_size=80,
 num_steps=8000,
 hidden_layers=[128, 32])

#### Function to parse MNIST TFRecords
def parser(record):
 features = tf.parse_single_example(record,
 features={
 'images': tf.FixedLenFeature([], tf.string),
 'labels': tf.FixedLenFeature([], tf.int64),
 })
 image = tf.decode_raw(features['images'], tf.uint8)
 image.set_shape([image_dim * image_dim])
 image = tf.cast(image, tf.float32) * (1. / 255) - 0.5
 label = features['labels']
 return image, label

#### Create the DNNClassifier
def create_estimator(hidden_layers, num_labels, conf):
 column = tf.feature_column.numeric_column('pixels',
 shape=[image_dim * image_dim])
 return tf.estimator.DNNClassifier(hidden_layers, [column],
 n_classes=num_labels, config=conf)

#### Train the estimator
def train_func():
 dataset = tf.data.TFRecordDataset('mnist_train.tfrecords')
 dataset = dataset.map(parser).repeat().batch(batch_size)
 image, label = dataset.make_one_shot_iterator().get_next()
 return {'pixels': image}, label

#### Test the estimator
def test_func():
 dataset = tf.data.TFRecordDataset('mnist_test.tfrecords')
 dataset = dataset.map(parser).batch(batch_size)
 image, label = dataset.make_one_shot_iterator().get_next()
 return {'pixels': image}, label

#### Create experiment
def create_experiment(conf, params):
 return tf.contrib.learn.Experiment(
 estimator=create_estimator(params.hidden_layers,
 params.num_labels, conf),
 train_input_fn=train_func,
 eval_input_fn=test_func,
 train_steps=params.num_steps)

#### Run experiment
run_config = tf.contrib.learn.RunConfig(model_dir='experiment_output')
tf.contrib.learn.learn_runner.run(
 experiment_fn=create_experiment,
 run_config=run_config,
 schedule='train_and_evaluate',
 hparams=hparams
)
```

该模块首先创建了一个包含批大小、标签数量、训练步数和隐藏层数量的 `HParams`。该模块还创建了一个标识实验输出应存储目录的 `RunConfig`。

当模块调用 `tf.contrib.learn.learn_runner.run` 时，它提供了 `HParams` 实例、`RunConfig` 实例以及返回 `Experiment` 的函数。该函数使用三个函数调用 `Experiment` 构造函数：

* `create_estimator`: 使用实验的配置设置创建 `DNNClassifier`
* `train_func`: 为 `DNNClassifier` 提供训练数据和标签
* `test_func`: 为 `DNNClassifier` 提供测试数据和标签

模块将 `tf.contrib.learn.learn_runner.run` 的 `schedule` 参数设置为 `train_and_evaluate`。这会调用实验的 `train_and_evaluate` 函数，该函数训练并测试实验的估计器。

# 第 13 章

# 在 Google Cloud Platform (GCP) 上运行应用程序

本章内容

![check](img/check.png)**为 Google Cloud Platform (GCP) 开发项目**

![check](img/check.png)**使用 GCP 工具**

![check](img/check.png)**访问 Google Cloud Storage (GCS)**

![check](img/check.png)**在 GCP 中打包和运行 TensorFlow 应用程序**

在技术世界的成功故事中，没有什么比 Google 的崛起更引人注目的了。自 2004 年首次公开募股以来，Google 建立了一个遍布全球的庞大计算架构。每个拥有互联网连接的人都知道如何在 [`google.com`](http://www.google.com) 上搜索信息并在 [`youtube.com`](http://youtube.com) 上观看媒体。Google 的技术变得如此流行，以至于动词 google 已进入 Merrian-Webster 词典。

虽然 Google 的技术在全球闻名，但 Google Compute Platform (GCP) 并没有那么知名。这很遗憾，因为 GCP 让像你我这样的开发者能够利用 Google 的庞大资源，其中包括数 TB 的分布式存储和高速处理器集群。

我喜欢使用 GCP，因为我的应用程序可以访问 Google 的技术，其中包括 Google 地图、Gmail、YouTube 和 AdSense。本章重点介绍 Google 的机器学习（ML）引擎，它让你能够在 Google Cloud Platform 中执行 `TensorFlow` 应用程序。

## 概述

好消息是，你可以通过将应用程序部署到 Google 的机器学习（ML）引擎来大幅减少机器学习所需的时间。坏消息是，配置和部署应用程序的过程并不容易。涉及五个步骤：

1. **为 Google Cloud Platform（GCP）创建一个项目并将其配置为使用 Cloud Machine Learning API。**
2. **安装 Cloud 软件开发工具包（SDK）。**
3. **将你的 TensorFlow 应用程序结构化为一个包。**
4. **将你的包和处理数据上传到 Google Cloud Storage。**
5. **使用 Cloud SDK 执行训练或预测作业。**

在撰写本章时，我假设你从未听说过 GCP。因此，在我解释如何部署应用程序之前，我先介绍 Cloud 软件开发工具包（SDK）和 Cloud Storage，并解释如何创建一个 GCP 项目。

## 使用 GCP 项目

如果你想利用 GCP 的功能，第一步是创建一个项目。该项目充当你开发工作的中央容器，其中包含所有元数据和配置文件。在你执行代码或启动 Web 应用程序之前，需要将文件上传到你的项目。同样，如果你想要访问特殊功能，需要通过项目提出请求。

要构建可访问 ML Engine 的 GCP 项目，你需要执行三个步骤：

1. **在 Google Developer Console 中创建一个项目。**
2. **为项目启用计费。**
3. **启用项目以访问机器学习引擎。**

![tip](img/tip.png)本书示例代码中的 `ch13` 目录包含两个文件夹：`cloud_mnist` 和 `cluster_mnist`。这些文件夹包含可部署到 ML Engine 的包，但它们不是 GCP 项目。GCP 项目驻留在云中，因此如果你想跟随本章的开发，你需要自行创建和配置一个 GCP 项目。

### 创建新项目

任何拥有有效电子邮件地址的人都可以免费创建 GCP 项目而无需任何费用或义务。该过程涉及五个步骤：

1. **访问 Cloud Console，网址为** [`https://console.cloud.google.com`](https://console.cloud.google.com)**。**
2. **如果这是你第一次访问控制台，请提供联系电子邮件地址和密码。**
3. **在上方的水平栏中，点击 Select a Project。**
4. **在 Select 对话框中，点击右侧的加号按钮。**
5. **在 New Project 页面中，输入项目名称并点击 Create 按钮。**

在使用 GCP 时，你需要理解项目名称和 ID 之间的区别。项目的名称由开发者选择，控制台使用它来显示当前项目。

相比之下，项目的 ID 由 GCP 根据项目名称选择，并且在 GCP 的所有项目中唯一标识该项目。如果你想上传代码或更改项目的配置，你将需要通过其 ID 访问你的项目。因此，了解你的项目的 ID 是一个好主意。

### 计费

机器学习是一种强大的功能，但与 TensorFlow 不同，它不是免费的。Google 对机器学习的费用取决于三个因素：操作类型（训练或预测）、持续时间以及你的位置：

* 训练：美国每小时每个训练单元 0.49 美元，欧洲和亚洲 0.54 美元
* 预测：美国每千次预测 0.10 美元，外加每小时 0.40 美元；欧洲和亚洲每千次预测 0.11 美元，外加每小时 0.44 美元

Google 在你使用 ML Engine 之后收取费用，而不是预先收取。但你需要在使用引擎之前确定付款方式，你可以通过将项目与计费账户关联来配置此项：

1. **访问 Cloud Console 中的项目页面。**
2. **打开左上角的菜单（三条水平线）并选择 Billing 选项。**
3. **点击标题为 Add billing account 的按钮。**
4. **输入你的联系信息和计费信息。**

在页面底部，有一个按钮可让你设置自动付款，这将授权 Google 在使用资源时从账户中提取资金。

### 访问机器学习引擎

在为你的项目设置计费账户后，你可以访问付费功能，如 ML Engine。要启用此功能，请打开项目页面左上角的菜单并选择 APIs & Services。这将打开 APIs & Services 页面，该页面标识项目可以访问的功能。
