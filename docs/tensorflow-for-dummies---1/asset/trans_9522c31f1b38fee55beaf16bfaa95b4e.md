

你可以通过调用前面 “[将操作分配给设备](#17_9788126592555-ch11.xhtml#c11-sec-0014)” 部分中讨论的 `tf.device` 函数，将代码与特定任务关联起来。例如，以下代码仅在 Job `j1` 的 Task 0 上执行：

```
with tf.device('/job:j1/task:0'):
  const_a = tf.constant(3.6)
  const_b = tf.constant(1.2)
  total = const_a + const_b
```

你也可以使用 `if` 语句对代码进行分区：

```
if job_name == 'j1' and task_num == 0:
  …
elif job_name == 'j1' and task_num == 1:
  …
```

在定义集群时，你可以创建任意数量的 jobs 和 tasks。但许多分布式 TensorFlow 应用只有两个 jobs：

* **参数服务器 (`ps`):** 存储应用程序的变量
* **工作副本 (`worker`):** 执行应用程序的计算，包括更新变量的处理

你可以用如下代码在集群规范中定义这些 jobs：

```
spec = tf.train.ClusterSpec({'ps': [..], 'worker': [..]})
```

本节介绍参数服务器和 worker，并展示如何在代码中创建它们。

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

一般来说，执行计算的任何 job 都被视为 *worker job*。worker job 中的每个任务称为 *worker replica* 或简称 *worker*。为了执行其计算，每个 worker 都需要创建并启动一个 session。

这就产生了一个问题：你不能在分布式应用中创建常规 session。你需要在适当的 server 进程中运行每个 session。要理解如何在 server 中运行 session，你需要熟悉 server targets。

正如 Web 服务器使用 HTTP 进行通信一样，TensorFlow 服务器使用 gRPC 进行通信。每个服务器都有一个由其主机和端口决定的 gRPC 地址。例如，如果你配置一个服务器执行地址为 localhost:123 的任务，则服务器的 gRPC 地址将如下所示：

```
grpc://localhost:123
```

此 gRPC 地址称为服务器的 *target*。你可以通过 `Server` 实例的 `target` 属性访问此 target。

要创建在服务器内部运行的 session，你需要将 `tf.Session` 的第一个参数设置为服务器的 target。以下代码创建了一个 `Server`，然后创建了一个连接到它的 session：

```
server = tf.train.Server(spec, job_name='worker', task_index=1)
with tf.Session(server.target) as sess:
  …
```

这里有一个问题：如果分布式应用中的 worker 需要访问相同变量数据，变量如何初始化？参数服务器不能初始化其变量，因为它不运行 session。但如果每个 worker 单独初始化变量，TensorFlow 就无法在进程之间复制数据。

答案是其中一个 worker 需要处理初始化，而其他 worker 需要等待初始化完成。处理初始化的 worker 称为 *chief*。你可以通过调用 `tf.train.MonitoredTrainingSession` 在 session 中分配 chief 的操作。

#### Workers and monitored sessions

[第 5 章](#09_9788126592555-ch05.xhtml) 介绍了 session hooks 的有趣主题，并解释了如何将 hooks 与 `MonitoredSession` 关联。你可以通过调用一个名为 `tf.train.MonitoredTrainingSession` 的函数为分布式应用配置 `MonitoredSession`：

```
MonitoredTrainingSession(master='', is_chief=True, checkpoint_dir=None, scaffold=None, hooks=None, chief_only_hooks=None, save_checkpoint_secs=600, save_summaries_steps=USE_DEFAULT, save_summaries_secs=USE_DEFAULT, config=None, stop_grace_period_secs=120, log_step_count_steps=100)
```

此函数看起来像一个类构造函数，但它返回一个 `MonitoredSession`，而不是 `MonitoredTrainingSession`。如果 worker 以 `is_chief` 设置为 `True` 调用此函数，`MonitoredSession` 将在启动时执行 session 的初始化。因此，只有 一个 worker（chief）应以 `is_chief` 设置为 `True` 调用此函数。当其他 worker 调用此函数时，返回的 `MonitoredSession` 将等待 chief 的 session 完成初始化。

第一个参数 `master` 与 `Session` 构造函数中的 `target` 参数具有相同的目的。也就是说，它标识 intended 运行 session 的 worker 的 gRPC 位置，例如 `grpc://localhost:123`。

`MonitoredTrainingSession` 函数接受通用 session hooks（`hooks`）和 intended 用于 chief session 的 session hooks（`chief_only_hooks`）。此外，该函数接受用于设置检查点和生成摘要数据的参数。通过设置这些参数，你无需创建 `CheckpointSaverHook` 或 `SummarySaverHook`。

### 运行一个简单的集群

`ch11/cluster.py` 模块中的代码提供了一个分布式 TensorFlow 应用的简单示例。该模块不执行任何机器学习，但演示了一组 worker 任务如何协同努力来更新一个变量。

具体来说，该应用程序创建了四个 worker 并用它们来近似 *π*。这种近似涉及将函数 y = (1 + x²)^(\-1) 在 x 从 0 到 1 运行时下方矩形的面积相加，并将总和乘以 4。在 [图 11-1](#17_9788126592555-ch11.xhtml#c11-fig-0001) 中，图形将函数下方的面积划分为 30 个区域。

![FIGURE 11-1: An application can approximate π by splitting the area under the function into rectangles and adding the areas together.](images/9788126592555-fg1101.png)

[FIGURE 11-1:](#17_9788126592555-ch11.xhtml#rc11-fig-0001) An application can approximate *π* by splitting the area under the function into rectangles and adding the areas together.

`ch11/cluster.py` 模块生成四个 worker 来执行近似。[列表 11-1](#17_9788126592555-ch11.xhtml#c11-fea-0001) 展示了代码。

[LISTING 11-1](#17_9788126592555-ch11.xhtml#rc11-fea-0001) Approximating Pi in a Distributed Application

```
# Session hook to print output
class OutputHook(tf.train.SessionRunHook):

  def before_run(self, run_context):
    return tf.train.SessionRunArgs(pi_var)

  def after_run(self, run_context, run_values):
    print('Pi approximation:', run_values.results)

# Define a cluster with two jobs and five tasks
spec = tf.train.ClusterSpec({'worker':
  ['localhost:31415', 'localhost:31416', 'localhost:31417', 'localhost:31418']})

# Perform task-dependent operations
flags = tf.flags
flags.DEFINE_string('task', '', '')
if not flags.FLAGS.task:

  # Launch the worker processes
  subprocess.Popen('python cluster.py --task=0', stderr=subprocess.STDOUT)
  subprocess.Popen('python cluster.py --task=1', stderr=subprocess.STDOUT)
```

