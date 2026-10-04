

TensorFlow 日志基于常规 Python 日志，许多 `tf.logging` 函数与 Python 的 `Logger` 类的方法相同。

TensorFlow 支持五种日志级别。按严重程度排序，分别是 `DEBUG`、`INFO`、`WARN`、`ERROR` 和 `FATAL`。

要启用日志，应用程序需要调用 `tf.logging.set_verbosity`，并指定应记录的最低严重级别。

默认情况下，TensorFlow 将日志消息写入标准输出。截至本文撰写时，TensorFlow 日志不支持将消息写入日志文件。

对于每个日志级别，`tf.logging` 都提供了一个名称相似的函数，用于在该级别写入日志消息。例如，以下代码启用 INFO 消息（以及更严重的消息），然后写入一条显示 `output` 值的 INFO 消息：

```
tf.logging.set_verbosity(tf.logging.INFO)
```

```
with tf.Session() as sess:
 output = sess.run(…)
 tf.logging.info('Output: %f', output)
```

如果 `output` 的值为 5.5，`tf.logging.info` 将向标准输出打印以下消息：

`INFO:tensorflow:Output: 5.5`

[表 4-3](#08_9788126592555-ch04.xhtml#c04-tbl-0003) 列出了 `set_verbosity`、`info` 以及 `tf.logging` 提供的其他函数。

[TABLE 4-3](#08_9788126592555-ch04.xhtml#rc04-tbl-0003) 摘要数据函数

| **函数** || **描述** |
| --- | --- |
| `set_verbosity(level)` || 启用给定严重级别及更高严重级别的消息日志记录 |
| --- | --- |
| `debug(msg, *args, **kwargs)` || 在 DEBUG 严重级别记录消息 |
| `info(msg, *args, **kwargs)` || 在 INFO 严重级别记录消息 |
| `warn(msg, *args, **kwargs)` || 在 WARN 严重级别记录消息 |
| `error(msg, *args, **kwargs)` || 在 ERROR 严重级别记录消息 |
| `fatal(msg, *args, **kwargs)` || 在 FATAL 严重级别记录消息 |
| `flush()` || 强制日志操作完成 |
| `log(level, msg, *args, **kwargs)` || 在给定严重级别记录消息 |
| `log_if(level, msg, condition, *args)` || 如果条件为真，则在给定严重级别记录消息 |
| `log_first_n(level, msg, n, *args)` || 最多 *n* 次在给定严重级别记录消息 |
| `log_every_n(level, msg, n, *args)` || 每 *n* 次在给定严重级别记录一次消息 |

最后三个函数使得可以控制何时将消息写入日志。`log_if` 的第三个参数定义了一个条件，用于确定何时应记录消息。以下代码在 `output` 大于 0 时记录其值：

`tf.logging.log_if(tf.logging.INFO, 'Output: %f', (output > 0), output)`

`log_first_n` 和 `log_every_n` 的第三个参数是一个整数，用于确定执行频率。在 `log_first_n` 中，该值设置函数最多向日志写入消息的次数。在 `log_every_n` 中，该值指示函数每被调用 *N* 次记录一次消息。

## 使用 TensorBoard 可视化数据

日志对于监控简单数据是足够的，但在许多情况下，开发人员需要跟踪大型、复杂的数据集。实际应用可能启动会话数百次或数千次，日志不足以监控每次执行时数据的变化。

好消息是，您的 TensorFlow 安装包含 TensorBoard。此强大的实用程序读取应用程序的数据并在网页中显示它。[图 4-2](#08_9788126592555-ch04.xhtml#c04-fig-0002) 展示了 TensorBoard 页面在 Chrome 浏览器中的外观。

![图 4-2：TensorFlow 可以显示应用程序的许多方面，包括其图的<|message|>。](images/9788126592555-fg0402.png)

[图 4-2：](#08_9788126592555-ch04.xhtml#rc04-fig-0002) TensorFlow 可以显示应用程序的许多方面，包括其图的 fiy。

坏消息是 TensorBoard 需要一种称为 *摘要数据* 的特殊格式数据，并且生成这种数据并不容易。

### 运行 TensorBoard

当您安装 TensorFlow 时，安装程序会将 TensorBoard 实用程序放置在顶级脚本目录中。如果您无法从命令行执行 `tensorboard` 命令，请将此目录添加到系统的 PATH 变量中。

`tensorboard` 命令接受一些标志，包括以下内容：

* `--logdir DIR`：包含摘要数据的目录
* `--host HOST`：标识网页 URL 的主机部分
* `--port PORT`：标识网页 URL 的端口

默认情况下，TensorBoard 的 IP 地址为 127.0.0.1，可作为 `localhost` 访问。TensorBoard 的默认端口为 `6006`。因此，TensorBoard 的默认 URL 为 `http://localhost:6006`。

`--logdir` 标志是必需的，因此您无法在没有数据的情况下启动 TensorBoard。您必须将此标志设置为包含一种特殊文件的文件夹，即 *事件文件*。该文件包含 TensorBoard 进行可视化所需的摘要数据。如果文件位于名为 output 的目录中，则以下命令指示 TensorBoard 读取事件文件：

```
tensorboard --logdir=output
```

### 生成摘要数据

此时，您应该了解如何创建数学运算并在会话中执行它们。本讨论介绍了一种称为 *摘要运算* 的新型运算。这类似于其他 TensorFlow 运算，但当会话执行摘要运算时，结果是一个包含摘要数据的协议缓冲区。应用程序可以将此缓冲区写入文件中，其内容可通过 TensorBoard 显示。

TensorBoard 可以说明许多不同类型的数据，每种类型对应于 `tf.summary` 的一个函数。[表 4-4](#08_9788126592555-ch04.xhtml#c04-tbl-0004) 列出了其中六个可用函数。

[TABLE 4-4](#08_9788126592555-ch04.xhtml#rc04-tbl-0004) 摘要数据函数

| **函数** || **描述** |
| --- | --- |
| `scalar(name, tensor, collections=None)` || 创建一个提供标量数据的摘要运算 |
| --- | --- |
| `histogram(name, values, collections=None)` || 创建一个提供直方图数据的摘要运算 |
| `audio(name, tensor, sample_rate, max_outputs=3, collections=None)` || 创建一个提供音频源数据的摘要运算 |
| `image(name, tensor, max_outputs=3, collections=None)` || 创建一个提供图像数据的摘要运算 |
| `merge(inputs, collections=None, name=None)` || 将指定的摘要运算合并为一个摘要运算 |
| `merge_all(key= tf.GraphKeys.SUMMARIES)` || 将摘要运算合并为一个摘要运算 |

在这些函数中，最受欢迎的两个是 `scalar` 和 `histogram`。`scalar` 为在多次会话执行中变化的单个值生成摘要数据。`histogram` 为在会话执行中变化的值集生成数据。`image` 函数生成与图像和图像分析相关的数据。[第 8 章](#13_9788126592555-ch08.xhtml) 详细讨论了图像。

在我看来，了解摘要数据的最佳方式是查看示例代码。以下代码执行三个任务：

* `tf.summary.scalar` 生成提供标量数据的运算。
* `tf.summary.merge_all` 将它们合并为一个运算。
* `sess.run` 执行合并的摘要运算。

```
# Add two scalars
a = tf.constant(2.5)
b = tf.constant(4.5)
total = a + b;
```

```
# Create operations that generate summary data
tf.summary.scalar("a", a)
tf.summary.scalar("b", b)
tf.summary.scalar("total", total)
```

```
# Merge the operations into a single operation
merged_op = tf.summary.merge_all()
```

```
with tf.Session() as sess:
 _, summary = sess.run([sum, merged_op])
```

