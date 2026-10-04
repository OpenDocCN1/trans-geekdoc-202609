

`mat_b = tf.constant([[6, 4, 1], [3, 7, 2]])`

`mat_prod = tf.matmul(mat_a, mat_b)`

# Execute the operations

```python
with tf.Session() as sess:
    print("Sum: %f" % sess.run(total))
    print("Quotient: %f" % sess.run(quot))
    print("Difference: ", sess.run(diff))
    print("Element-wise product: ", sess.run(prod))
    print("Dot product: ", sess.run(dot))
    print("Matrix product: ", sess.run(mat_prod))
```

大部分代码应该看起来很熟悉。该应用程序创建并操作常量张量、随机张量、向量和矩阵。为了处理向量，应用程序使用 `tf.multiply` 执行逐元素乘法，然后使用 `tf.tensordot` 计算两个向量的点积。

代码的最后一部分值得解释。应用程序创建一个名为 `sess` 的 `Session` 并对每个要执行的运算调用其 `run` 方法。要理解会话是什么以及它们如何工作，你需要熟悉图。下一章将探讨会话和图相关主题。

# Chapter 4

# Executing Graphs in Sessions

IN THIS CHAPTER

![check](images/check.png) **Creating graphs and accessing their data**

![check](images/check.png) **Serializing data from a graph into a GraphDef**

![check](images/check.png) **Creating and launching sessions**

![check](images/check.png) **Printing messages to the log**

![check](images/check.png) **Visualizing summary data with TensorBoard**

上一章介绍了大量创建、转换和处理张量的函数。这些函数大多数返回一个张量，这可能会让你认为函数在被调用时立即执行其操作。这就是 Python 函数通常的工作方式，但这不是 TensorFlow 函数的工作方式。

当应用程序执行创建、转换或处理张量的 TensorFlow 函数时，该函数并不执行其操作。相反，它将操作存储在称为 *graph* 的数据结构中。图可以容纳许多操作，并且它们在应用程序在会话中执行图之前不会被执行。当会话执行图时，它会按顺序执行图的操作。

将操作存储在图中的好处是图可以导出到文件或在远程系统上启动。缺点是图往往会让 TensorFlow 新手感到困惑。在撰写本章时，我的目标是通过对图和会话的完整解释来减少这种困惑。

## Forming Graphs

如果一个操作返回一个张量，则一个操作可以将输出馈送到另一个操作。为了演示此过程，以下代码将加法操作的结果馈送到乘法操作。

```python
c = tf.add(a, b)
e = tf.multiply(c, d)
```

[Figure 4-1](#08_9788126592555-ch04.xhtml#c04-fig-0001) 说明了这些嵌套操作及其张量之间的关系。

![FIGURE 4-1: The addition operation receives the result of multiplication.](images/9788126592555-fg0401.png)

[FIGURE 4-1:](#08_9788126592555-ch04.xhtml#rc04-fig-0001) The addition operation receives the result of multiplication.

在 [Figure 4-1](#08_9788126592555-ch04.xhtml#c04-fig-0001) 中，每个圆圈标识一个张量或操作，每个线条传输张量数据。数学家和计算机科学家将这种节点和边的结构称为 *graph*。图的圆圈称为 *nodes*，直线称为 *edges*。

当应用程序执行创建张量或操作的功能时，TensorFlow 将数据结构添加到名为 `Graph` 的容器结构中。`Graph` 不能嵌套，并且一次只能有一个 `Graph` 处于活动状态。应用程序可以通过调用 `get_default_graph` 来访问其默认 `Graph`。以下代码展示了如何使用它：

```python
graph = tf.get_default_graph()
```

应用程序可以通过调用不带参数的构造函数来创建新的 `Graph`。然后应用程序可以通过调用 `Graph` 的 `as_default` 方法将 `Graph` 设置为默认 `Graph`。以下代码演示了其工作原理：

```python
newgraph = tf.Graph()
with newgraph.as_default():
    …
```

调用 `as_default` 后，TensorFlow 将把新张量和操作添加到 `newgraph` 而不是原始 `Graph`。

`Graph` 类提供了许多访问和修改图内容的方法。此讨论将这些方法分为两类：

* **Accessing graph data:** Reading a graph's containers and elements
* **Creating `GraphDef`s:** Serializing a graph into a protocol buffer

### Accessing graph data

图将其元素存储在一组命名集合中。[Table 4-1](#08_9788126592555-ch04.xhtml#c04-tbl-0001) 介绍了 `Graph` 类访问和更新这些集合的方法。

[TABLE 4-1](#08_9788126592555-ch04.xhtml#rc04-tbl-0001) Accessing Graph Data

| **Method** | | **Description** |
| --- | --- | --- |
| `get_tensor_by_name(name)` | | Returns the tensor with the given name |
| --- | --- | --- |
| `get_operation_by_name(name)` | | Returns the operation with the given name |
| `get_operations()` | | Returns a list containing the graph's operations |
| `get_all_collection_keys()` | | Returns a list of the graph's collections |
| `get_collection(name, scope=None)` | | Returns a list of values in the given collection |
| `add_to_collection(name, value)` | | Adds the value to the container, can be accessed with name |
| `add_to_collections(name, value)` | | Adds the value to the containers, can be accessed with name |

前三种方法使访问当前图中的张量和操作变得容易。每种方法返回一个包含所需元素的列表，以下代码演示了如何使用它们：

```python
a = tf.constant(2.5, name='first_val')
b = tf.constant(4.5, name='second_val')
sum = a + b;
print(tf.get_default_graph().get_operations())
print(tf.get_default_graph().get_tensor_by_name('first_val:0'))
```

第一个 `print` 语句调用 `get_operations` 以获取图的运算列表。打印结果如下：

```
[<tf.Operation 'first_val' type=Const>,
 <tf.Operation 'second_val' type=Const>,
 <tf.Operation 'add' type=Add>]
```

第二个 `print` 语句使用 `name:index` 格式访问第一个张量。在这种情况下，张量的名称为 `first_val`，索引为 0。TensorFlow 打印以下结果：

```
("first_val:0", shape=(), dtype=float32)
```

图可以保存的不只是张量和操作。这些附加信息存储在称为图 *collections* 的一组列表中。与字典一样，你可以使用称为 *keys* 的标识符访问集合的元素。[Table 4-2](#08_9788126592555-ch04.xhtml#c04-tbl-0002) 介绍了图集合的不同键。

[TABLE 4-2](#08_9788126592555-ch04.xhtml#c04-tbl-0002) Graph Collection Keys

| **Collection Key** | | **Description** |
| --- | --- | --- |
| `GLOBAL_VARIABLES` | | All variables used in the application |
| --- | --- | --- |
| `LOCAL_VARIABLES` | | Variables local to this machine |
| `MODEL_VARIABLES` | | Variables used in the model |
| `TRAINABLE_VARIABLES` | | Variables capable of being trained by an optimizer |
| `MOVING_AVERAGE_VARIABLES` | | Variables that maintain moving averages |
| `SUMMARIES` | | Tensor summaries |
| `QUEUE_RUNNERS` | | QueueRunners that provide input data |
| `REGULARIZATION_LOSSES` | | Losses produced by regularization |

这些集合中的大多数存储与变量相关的数据，我将在 [Chapter 5](#09_9788126592555-ch05.xhtml) 中介绍。现在，重要的是要知道图提供了对张量、运算符和其他类型数据的访问。

### Creating GraphDefs

许多应用程序需要从其他 TensorFlow 应用程序访问图。`as_graph_def` 方法使这成为可能。此方法返回 `Graph` 的序列化形式，称为 `GraphDef`。

