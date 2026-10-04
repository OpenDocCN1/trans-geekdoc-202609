

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

该模块定义了一个 `ClusterSpec` 并启动了四个进程——每个 worker 一个。每个 worker 进程接收一个不同的参数来标识其任务编号。worker 使用该任务编号来创建并启动一个服务器，其网络地址由 `ClusterSpec` 确定。

该模块调用 `tf.device` 将代码分配给四个 worker。第一个 worker 声明并初始化 `pi_var` 变量。其余 worker 通过将函数 y = (1 + x²)^(-1) 下方十个矩形区域的面积相加来更新 `pi_var` 的值。

每个 worker 都调用 `tf.train.MonitoredTrainingSession` 并将其目标设置为第一个 worker 的地址。首席 worker 是任务索引为 0 的 worker，并且该 worker 的会话最先执行并初始化应用程序的变量。初始化完成后，其他 worker 执行会话并更新 `pi_var`。

为了显示输出，该模块将会话与一个 `OutputHook` 关联。此会话钩子在会话执行完成后打印 `pi_var` 的值。该模块将会话钩子与函数的 `chief_only_hooks` 参数关联，因此钩子仅适用于首席 worker 的会话。

# 第 12 章

# 使用 Estimator 开发应用程序

本章内容

![check](images/check.png) **使用 estimator 执行机器学习算法**

![check](images/check.png) **定义特征和特征列**

![check](images/check.png) **在实践中使用预构建的 estimator**

![check](images/check.png) **使用宽深度学习分析复杂数据集**

从根本上说，使用统计回归进行机器学习的过程与使用神经网络的过程非常相似（参见 [第 7 章](#12_9788126592555-ch07.xhtml)）：加载数据、训练模型并测试结果。不幸的是，在 TensorFlow 中执行统计回归所需的代码与创建神经网络所需的代码大不相同。

为了简化开发和测试，TensorFlow 提供了 Estimator 框架。`tf.estimator` 包包含通过一组通用方法分析数据的模块。例如，执行线性回归的 estimator 类（`LinearRegressor`）与执行深度神经网络回归的类（`DNNRegressor`）具有相同的方法。

你可以通过为自己的 estimator 编码来利用这种通用性。也就是说，如果你将自定义机器学习算法打包为 estimator，其他开发者将无需费力即可训练和测试你的应用程序。

## 介绍 Estimator

`tf.estimator` 包提供了分析数据的各种类，包括 `LinearClassifier` 和 `DNNClassifier`。这些类都扩展了 `Estimator` 类，其方法使得以算法无关的方式执行机器学习成为可能。

在本书中，我使用术语 *estimator* 指代 `Estimator` 类及其子类的实例。一般来说，使用 estimator 的过程包含六个步骤：

1. **将数据加载到数据集。**
2. **创建特征列，将数据集的字段与名称和数据类型关联。**
3. **使用特征列创建 estimator 类的实例。**
4. **使用训练数据训练 estimator。**
5. **使用测试数据评估 estimator 的性能并检查结果。**
6. **将 estimator 用于实际预测或分类。**

步骤 3 取决于你感兴趣的 estimator 类型。你可以通过调用 `Estimator` 类的三个基本方法 `train`、`evaluate` 和 `predict` 来执行步骤 4、5 和 6。一旦你理解了这些方法，你就会对 estimator 有一个扎实的理解。

## 训练 Estimator

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

这组特征由两个点组成：(0.1, 0.5, 1.0) 和 (0.2, 0.6, 1.1)。但由于数据的结构方式，代码可能看起来令人困惑。函数不是一次返回一个点，而是将所有 x 坐标放在第一个特征中，所有 y 坐标放在第二个特征中，所有 z 坐标放在第三个特征中。

`input_fn` 返回的元组的第二部分是包含标签的张量。如果 estimator 的目的是分类，则标签代表类别。在前面的示例代码中，第一个点的标签为 0，第二个点的标签为 1。

查看这段代码时，你可能会想知道名称 `x-coords`、`y-coords` 和 `z-coords` 从何而来。当你调用 estimator 的构造函数时，你需要为每个特征提供一个 *特征列*。特征列将名称，例如 `x-coords`，与特征中提供的数据类型关联。我将在即将到来的 “[使用特征列](#18_9788126592555-ch12.xhtml#c12-sec-0008)” 部分讨论特征列这一迷人的主题。

默认情况下，estimator 会一直训练直到损失接近于零。但你可以通过设置 `steps` 参数或 `max_steps` 参数来控制训练步数。区别在于 `steps` 参数是增量的，因此如果你现在想执行 30 步训练，后面再执行 20 步训练，你可以先调用 `train` 并将 `steps` 设为 30。稍后，你可以调用 `train` 并将 `steps` 设为 20。

你可以通过将 `hooks` 参数设置为会话钩子的列表来监控训练过程。[第 5 章](#09_9788126592555-ch05.xhtml) 解释了会话钩子如何使监控会话执行成为可能。

## 测试 Estimator

