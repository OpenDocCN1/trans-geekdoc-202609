
```
if job_name == 'j1' and task_num == 0:
  …
elif job_name == 'j1' and task_num == 1:
  …
```

在定义集群时，你可以创建任意数量的 `jobs` 和 `tasks`。但许多分布式 TensorFlow 应用只有两个 `jobs`：

* **参数服务器 (`ps`):** 存储应用程序的变量
* **工作副本 (`worker`):** 执行应用程序的计算，包括更新变量的处理

你可以用如下代码在集群规范中定义这些 `jobs`：

```
spec = tf.train.ClusterSpec({'ps': [..], 'worker': [..]})
```

本节介绍参数服务器和 `worker`，并展示如何在代码中创建它们。

### 参数服务器

在分布式应用中，TensorFlow 认识到在同一设备上同名的变量代表相同的数据。也就是说，如果 Tasks X 和 Y 都操作名为 `weight_var` 的变量，TensorFlow 就理解它们应该访问同一个 `weight_var` 变量。这些任务在不同的进程中运行，因此 TensorFlow 会在进程之间复制变量。

*参数服务器*（PS）充当存储、保存和检索变量的中央位置。在许多应用中，PS 任务只需声明变量，然后在应用程序完成前阻塞即可。为了演示这一点，以下代码定义了一个参数服务器，它声明了两个变量 `weights` 和 `biases`，然后在应用程序完成前阻塞。

```
server = tf.train.Server(cluster, job_name='ps', task_index=0)
if job_name == 'ps':
  weights = tf.Variable(…)
  biases = tf.Variable(…)
  server.join()
```

参数服务器声明 `weights` 和 `biases` 之后，其他任务可以访问这些变量并按需更新它们。`join` 方法告诉服务器无限期阻塞。

### Workers

一般来说，执行计算的任何 `job` 都被视为 *worker job*。`worker job` 中的每个任务称为 *worker replica* 或简称 *worker*。为了执行其计算，每个 `worker` 都需要创建并启动一个 `session`。

这就产生了一个问题：你不能在分布式应用中创建常规 `session`。你需要在适当的 `server` 进程中运行每个 `session`。要理解如何在 `server` 中运行 `session`，你需要熟悉 `server targets`。

正如 Web 服务器使用 HTTP 进行通信一样，TensorFlow 服务器使用 gRPC 进行通信。每个服务器都有一个由其主机和端口决定的 gRPC 地址。例如，如果你配置一个服务器执行地址为 `localhost:123` 的任务，则服务器的 gRPC 地址将如下所示：

```
grpc://localhost:123
```

此 gRPC 地址称为服务器的 *target*。你可以通过 `Server` 实例的 `target` 属性访问此 `target`。

要创建在服务器内部运行的 `session`，你需要将 `tf.Session` 的第一个参数设置为服务器的 `target`。以下代码创建了一个 `Server`，然后创建了一个连接到它的 `session`：

```
server = tf.train.Server(spec, job_name='worker', task_index=1)
with tf.Session(server.target) as sess:
  …
```

这里有一个问题：如果分布式应用中的 `worker` 需要访问相同变量数据，变量如何初始化？参数服务器不能初始化其变量，因为它不运行 `session`。但如果每个 `worker` 单独初始化变量，TensorFlow 就无法在进程之间复制数据。

答案是其中一个 `worker` 需要处理初始化，而其他 `worker` 需要等待初始化完成。处理初始化的 `worker` 称为 *chief*。你可以通过调用 `tf.train.MonitoredTrainingSession` 在 `session` 中分配 `chief` 的操作。

#### Workers and monitored sessions

第 5 章 介绍了 `session hooks` 的有趣主题，并解释了如何将 `hooks` 与 `MonitoredSession` 关联。你可以通过调用一个名为 `tf.train.MonitoredTrainingSession` 的函数为分布式应用配置 `MonitoredSession`：

```
MonitoredTrainingSession(master='', is_chief=True, checkpoint_dir=None, scaffold=None, hooks=None, chief_only_hooks=None, save_checkpoint_secs=600, save_summaries_steps=USE_DEFAULT, save_summaries_secs=USE_DEFAULT, config=None, stop_grace_period_secs=120, log_step_count_steps=100)
```

此函数看起来像一个类构造函数，但它返回一个 `MonitoredSession`，而不是 `MonitoredTrainingSession`。如果 `worker` 以 `is_chief` 设置为 `True` 调用此函数，`MonitoredSession` 将在启动时执行 `session` 的初始化。因此，只有 一个 `worker`（`chief`）应以 `is_chief` 设置为 `True` 调用此函数。当其他 `worker` 调用此函数时，返回的 `MonitoredSession` 将等待 `chief` 的 `session` 完成初始化。

第一个参数 `master` 与 `Session` 构造函数中的 `target` 参数具有相同的目的。也就是说，它标识 intended 运行 `session` 的 `worker` 的 gRPC 位置，例如 `grpc://localhost:123`。

`MonitoredTrainingSession` 函数接受通用 `session hooks`（`hooks`）和 intended 用于 `chief session` 的 `session hooks`（`chief_only_hooks`）。此外，该函数接受用于设置检查点和生成摘要数据的参数。通过设置这些参数，你无需创建 `CheckpointSaverHook` 或 `SummarySaverHook`。

### 运行一个简单的集群

`ch11/cluster.py` 模块中的代码提供了一个分布式 TensorFlow 应用的简单示例。该模块不执行任何机器学习，但演示了一组 `worker` 任务如何协同努力来更新一个变量。

具体来说，该应用程序创建了四个 `worker` 并用它们来近似 *π*。这种近似涉及将函数 `y = (1 + x²)^(-1)` 在 `x` 从 0 到 1 运行时下方矩形的面积相加，并将总和乘以 4。在 图 11-1 中，图形将函数下方的面积划分为 30 个区域。

![FIGURE 11-1: An application can approximate π by splitting the area under the function into rectangles and adding the areas together.](img/9788126592555-fg1101.png)

FIGURE 11-1: An application can approximate *π* by splitting the area under the function into rectangles and adding the areas together.

`ch11/cluster.py` 模块生成四个 `worker` 来执行近似。列表 11-1 展示了代码。

#### LISTING 11-1 Approximating Pi in a Distributed Application

```
#### Session hook to print output
class OutputHook(tf.train.SessionRunHook):

  def before_run(self, run_context):
    return tf.train.SessionRunArgs(pi_var)

  def after_run(self, run_context, run_values):
    print('Pi approximation:', run_values.results)

#### Define a cluster with two jobs and five tasks
spec = tf.train.ClusterSpec({'worker':
  ['localhost:31415', 'localhost:31416', 'localhost:31417', 'localhost:31418']})

#### Perform task-dependent operations
flags = tf.flags
flags.DEFINE_string('task', '', '')
if not flags.FLAGS.task:

  # Launch the worker processes
  subprocess.Popen('python cluster.py --task=0', stderr=subprocess.STDOUT)
  subprocess.Popen('python cluster.py --task=1', stderr=subprocess.STDOUT)
```

```python
subprocess.Popen('python cluster.py --task=2', stderr=subprocess.STDOUT)

subprocess.Popen('python cluster.py --task=3', stderr=subprocess.STDOUT)


else:
    N = 10
    num_workers = float(spec.num_tasks('worker') - 1)
    delta_x = float(1)/float(N * num_workers)
    task_index = int(flags.FLAGS.task)

    # Create server
    server = tf.train.Server(spec, job_name='worker', task_index=task_index)

    with tf.device('/job:worker/task:0'):
        pi_var = tf.Variable(0., dtype=tf.float32)

    with tf.device('/job:worker/task:1'):
        for i in range(N):
            x_i = delta_x * (i * num_workers + 0.5)
            pi_var += 4 * delta_x/(1 + x_i * x_i)

    with tf.device('/job:worker/task:2'):
        for i in range(N):
            x_i = delta_x * (i * num_workers + 1.5)
            pi_var += 4 * delta_x/(1 + x_i * x_i)

    with tf.device('/job:worker/task:3'):
        for i in range(N):
            x_i = delta_x * (i * num_workers + 2.5)
            pi_var += 4 * delta_x/(1 + x_i * x_i)

    # Launch session
    output_hook = OutputHook()
    with tf.train.MonitoredTrainingSession(master='grpc://localhost:31415',
                                           is_chief=(task_index == 0), chief_only_hooks=[output_hook]) as sess:
        sess.run(pi_var)
```

该模块定义了一个 `ClusterSpec` 并启动了四个进程——每个 `worker` 一个。每个 `worker` 进程接收一个不同的参数来标识其任务编号。`worker` 使用该任务编号来创建并启动一个服务器，其网络地址由 `ClusterSpec` 确定。

该模块调用 `tf.device` 将代码分配给四个 `worker`。第一个 `worker` 声明并初始化 `pi_var` 变量。其余 `worker` 通过将函数 `y = (1 + x²)^(-1)` 下方十个矩形区域的面积相加来更新 `pi_var` 的值。

每个 `worker` 都调用 `tf.train.MonitoredTrainingSession` 并将其目标设置为第一个 `worker` 的地址。首席 `worker` 是任务索引为 0 的 `worker`，并且该 `worker` 的会话最先执行并初始化应用程序的变量。初始化完成后，其他 `worker` 执行会话并更新 `pi_var`。

为了显示输出，该模块将会话与一个 `OutputHook` 关联。此会话钩子在会话执行完成后打印 `pi_var` 的值。该模块将会话钩子与函数的 `chief_only_hooks` 参数关联，因此钩子仅适用于首席 `worker` 的会话。

## 第 12 章

## 使用 Estimator 开发应用程序

本章内容

![check](img/check.png) **使用 estimator 执行机器学习算法**

![check](img/check.png) **定义特征和特征列**

![check](img/check.png) **在实践中使用预构建的 estimator**

![check](img/check.png) **使用宽深度学习分析复杂数据集**

从根本上说，使用统计回归进行机器学习的过程与使用神经网络的过程非常相似（参见 第 7 章）：加载数据、训练模型并测试结果。不幸的是，在 TensorFlow 中执行统计回归所需的代码与创建神经网络所需的代码大不相同。

为了简化开发和测试，TensorFlow 提供了 Estimator 框架。`tf.estimator` 包包含通过一组通用方法分析数据的模块。例如，执行线性回归的 estimator 类（`LinearRegressor`）与执行深度神经网络回归的类（`DNNRegressor`）具有相同的方法。

你可以通过为自己的 estimator 编码来利用这种通用性。也就是说，如果你将自定义机器学习算法打包为 estimator，其他开发者将无需费力即可训练和测试你的应用程序。

### 介绍 Estimator

`tf.estimator` 包提供了分析数据的各种类，包括 `LinearClassifier` 和 `DNNClassifier`。这些类都扩展了 `Estimator` 类，其方法使得以算法无关的方式执行机器学习成为可能。

在本书中，我使用术语 *estimator* 指代 `Estimator` 类及其子类的实例。一般来说，使用 estimator 的过程包含六个步骤：

1. **将数据加载到数据集。**
2. **创建特征列，将数据集的字段与名称和数据类型关联。**
3. **使用特征列创建 estimator 类的实例。**
4. **使用训练数据训练 estimator。**
5. **使用测试数据评估 estimator 的性能并检查结果。**
6. **将 estimator 用于实际预测或分类。**

步骤 3 取决于你感兴趣的 estimator 类型。你可以通过调用 `Estimator` 类的三个基本方法 `train`、`evaluate` 和 `predict` 来执行步骤 4、5 和 6。一旦你理解了这些方法，你就会对 estimator 有一个扎实的理解。

### 训练 Estimator

在将数据加载到数据集并创建 estimator 之后，下一步是开始训练。每个 estimator 都支持 `train` 方法：

`train(input_fn, hooks=None, steps=None, max_steps=None)`

`input_fn` 参数标识一个提供训练数据作为元组的函数。此元组包含两个数据元素：特征和标签。特征标识单个、完整的观测，例如 N 维空间中点的 N 个坐标。标签标识对应特征的类别，例如如果点代表成功则为 1，如果点代表失败则为 0。

为了标识特征，`input_fn` 提供一个将字符串与张量关联的字典。每个字符串标识张量中的数据。为演示如何设置 `input_fn`，以下函数提供了三个特征——每个点维度一个。

```python
def train_func():
    features = {
        'x-coords': tf.constant([[0.1], [0.2]]),
        'y-coords': tf.constant([[0.5], [0.6]]),
        'z-coords': tf.constant([[1.0], [1.1]])
    }
    labels = tf.constant([[0], [1]])
    return features, labels
```
