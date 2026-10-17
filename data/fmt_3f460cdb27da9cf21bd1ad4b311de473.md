
- `node c` 接收两个值 `6` 和 `4` 作为输入，在对这些值相乘后，它给出 `24` 作为输出结果。同时，`node d` 也接收两个值 `6` 和 `4` 执行加法操作，并给出 `10` 作为输出结果。

- 最后，`node e` 接收 `node c` 和 `node d` 的输出作为输入，并执行加法操作，给出 `34` 作为输出结果。`node e` 的输出可以是最终输出，也可以是后续节点的输入。

![](img/image-6ud.jpg)

### 图 1.9

由于数据流图使用有向图，计算方向由箭头指示。让我们逐步理解图的操作：

- 在左侧，我们可以看到两个圆圈 `a` 和 `b` 代表两个输入 `input1` 和 `input2`。这些输入可以来自其他图，也可以是原始输入。

## TensorFlow 中的数据流图

在 TensorFlow 中，程序的执行分为两个步骤：

1. 设计数据流图

2. 执行设计的/定义的图

在第一步中，我们为操作设计架构。我们并不计算任何值，或者说，在定义操作时，我们不会得到这些操作结果的任何输出值。如果我们再次查看图，加法操作被执行了，但这两个输入 `X` 和 `Y` 并不会产生结果 `X + Y`。因此，在 TensorFlow 中，当我们对任何输入进行加法或乘法时，我们并没有显式地进行加或或乘，而是设计了这些操作。

为了获得结果，我们必须遵循第二步，即运行图。每个节点将包含所需的操作和张量（tensor）值。这可以总结为：在 TensorFlow 中，我们首先设计所需的操作，然后在第二步中执行设计的图。我们稍后会讨论图的执行。首先，让我们熟悉图的设计。

### 图的设计

让我们在 TensorFlow 中构建第一个图。我们将使用图 1.10 所示的图作为示例：

![](img/image-qh4ryl5t.jpg) 图 1.10

以下是该图在 TensorFlow 中的代码：

```python
import tensorflow as tf
a = tf.constant(6, name="input1")
b = tf.constant(4, name="input2")
c = tf.add(a, b, name="add_c")
d = tf.multiply(a, b, name="multiply_d")
e = tf.add(c, d, name="add_e")
```

好的，让我们逐行理解这段代码。

首先，

```python
import tensorflow as tf
```

这是为程序导入 TensorFlow 库的标准方式，并命名为 `tf` 以方便使用。

接下来，

```python
a = tf.constant(6, name="input1")
b = tf.constant(4, name="input2")
```

在这两行中，我们定义了两个输入 `a` 和 `b`。在这里，我们使用了该图中第一个 TensorFlow 操作 `tf.constant()`。该操作接收单个值，并将相同的值作为输出传递给下一层节点进行进一步计算。TensorFlow 操作将输入值转换为 `Tensor`。我们还为每个操作定义了名称，这将有助于可视化图的设计。我们将在讨论 TensorBoard（TensorFlow 的可视化工具）时了解更多可视化。我们也可以不写名称写代码。

现在，

```python
c = tf.add(a, b, name="add_c")
d = tf.multiply(a, b, name="multiply_d")
```

在这两行中，我们又使用了两个 TensorFlow 操作，一个是 `tf.add()`，另一个是 `tf.multiply()`。首先，`tf.add()` 将接收两个输入并将两个输入的加和作为输出。其次，`tf.multiply()` 将接收两个输入并给出两个输入的乘积作为输出。在这里，我们只为节点定义操作，TensorFlow 会通过定义节点之间的连接自动将一个节点的输出传输到另一个节点。我们不需要考虑边。

最后，

```python
e = tf.add(c, d, name="add_e")
```

这是上述图的最后一个节点。与节点 `c` 类似，节点 `e` 也接收两个输入并使用 `tf.add()` 操作相加这些输入，并将此加法的结果作为输出。

记住，我们之前讨论过 TensorFlow 使用两个步骤来完全执行程序。这是设计过程，或者说是定义过程。当我们把这些行放入 Jupyter Notebook 或 Python 文件中时，它不会返回任何值。为了得到结果，我们必须使用以下代码行。首先定义 session，然后在 session 中运行最后一个节点。我们稍后会了解。

## TensorFlow 操作

我们使用了一些 TensorFlow 操作来理解数据流图。让我们熟悉 TensorFlow 中一些基础的数学操作。

```python
import tensorflow as tf
import numpy as np
a = np.array([6, 2])
b = np.array([1, 4])
c = tf.multiply(a, b)
sess = tf.Session()
sess.run(c)
```

在这个示例中，我们使用了 `tf.multiply()` 操作。当我们运行这段代码时，将得到一个 NumPy 数组作为输出，`array([ 8, ...`。我们也可以提供输入的数据类型，例如 `a = np.array([6, 2], dtype=np.int32)`，或者使用浮点数据类型，因此输出也会提到数据类型。那么，这个示例中有什么新内容呢？在这个示例中，我们使用 NumPy 手动初始化了张量。这展示了 NumPy 和 TensorFlow 之间的兼容性。

为什么我们使用 NumPy 来初始化张量对象？TensorFlow 有多种数据类型选项，如 `float32`、`int32` 等，但在某些情况下（例如复数），使用 TensorFlow 初始化会稍微困难一些，因此 NumPy 让我们的工作变得更简单。这表明 TensorFlow 中的数据类型与 NumPy 高度相关，或者简单来说是基于 NumPy 的数据类型。我们可以在终端输入 `tf.int64 == np.int64` 来验证这一观点，并将得到输出 `True`。我们也可以将 NumPy 数组作为 TensorFlow 的输入。

### 张量对象的形状

张量（Tensor）被定义为具有相同数据类型的数组。这意味着定义一个张量对象，我们需要每个维度的值和数据类型。形状（shape）描述了维度的数量以及每个维度的长度。张可以是列表、元组或 ND 矩阵。

让我们理解张量：

```python
import tensorflow as tf
tensor_object = tf.constant(1, shape=[2, 3])
print(tensor_object)
```

执行时，它将返回 `Tensor("Const:0", shape=(2, 3),` 输出。这告诉我们节点名为 `Const: 0` 以及其值，`tensor_object` 的形状为 `[2, 3]`，数据类型为 `int32`。在 TensorFlow 中，张量的形状可以分为两种：静态形状和动态形状。

### 静态形状

静态形状定义为初始化张量对象时确定的形状，或者在执行某些操作获取新张量对象后由 TensorFlow 推出的形状。它通常是列表或元组。TensorFlow 尝试在操作过程中推断 `z` 张量对象的形状，但当使用未知维度的 placeholder（动态尺寸）时，这会变得困难。

### 动态形状

我们可以说动态形状是在运行时确定的形状。让我们通过一个例子来理解：

```python
import tensorflow as tf
var1 = tf.placeholder(tf.float32, shape=[6])
print(var1.get_shape())
```

执行后，它将返回 `(6,)` 作为输出。这是静态形状，输出表示向量的长度。现在，让我们在其他操作中使用 `var1`。

```python
var2, idx = tf.unique(var1)
print(var2.get_shape())
```

返回 `(None,)` 作为输出。这意味着向量 `var2` 的长度是未知的。由于 `var1` 是未知的且 `var2` 依赖于它，因此长度也是未知的。

```python
sess = tf.Session()
print(sess.run(var2, feed_dict={var1: [1, 2, 2, 3, 3, 3]}))
print(sess.run(tf.shape(var2), feed_dict={var1: [1, 2, 2, 3, 3, 3]}))
```

它将返回 `(6,)` 和 `(3,)` 作为输出。我们可以可以看到 `var2` 的维度发生了变化。

### TensorFlow 中的 Session

Session 可以被定义为一个控制数学操作执行和张量值求值环境（计算图）的对象。我们也可以将其理解为将计算图放置在不同机器（如 CPU 或 GPU）上并提供执行过程。它有助于存储变量的当前值。

我们主要有两种方式启动 Session：

1. `sess = tf.Session()`，`sess.run()`，`sess.close()`

2. `with tf.Session() as sess: sess.run()`

Session 在执行图时使用资源。如果不再需要，释放这些资源是非常重要的。如果我们使用第一种方法，则必须显式关闭 Session。第二种方法作为上下文管理器，因此 Session 在退出 `with` 语句后会自动关闭。另一种方法是交互式 Session（Interactive session），它将自己变为默认 Session，因此在调试或在 IPython 中编写时非常有用。上述方法被广泛使用。以下是交互 Session 的示例：

```python
import tensorflow as tf
sess = tf.InteractiveSession()
a = tf.constant(5.0)
b = tf.constant(6.0)
c = a * b
## 我们可以直接使用 ‘c.eval()' 而不需要传递 ‘sess’
print(c.eval())
sess.close()
```

Session 与交互 Session 的区别在于交互 Session 将自己变为默认 Session，这样我们就可以不显式地调用 `run()` 或 `eval()` 了。

## 创建 TensorFlow 图

到为止，我们已经讨论了每个 TensorFlow 操作都是图中的一个节点。但我们还没有显式地创建过任何图。那么，这是如何实现的呢？当我们导入 `TensorFlow` 库时，它会自动创建一个图并将其赋值为默认图。每当我们使用任何 `TensorFlow` 操作时，它都会自动成为默认图的一个节点。让我们创建一个名为 `g_new` 的新图。

### 创建新图

我们可以使用以下代码行创建一个新图。

```python
import tensorflow as tf
g_new = tf.Graph()
```

使用上面的行，我们创建了一个新图。我们可以检查在导入 `TensorFlow` 库后是否创建了默认图，也可以检查是否创建了新图。

```python
import tensorflow as tf
g_new = tf.Graph()
print(g_new)
print(tf.get_default_graph())
```

当我们在 Jupyter Notebook 或 Python 文件中运行这段代码时，我们可以看到以下输出：

`object at 0x7fb2687bf050>`

`object at 0x7fb2a4b64e90>`

这证实了新图和默认图都已创建。

### 节点关联

正如我们讨论过的，当我们使用新的 `TensorFlow` 操作并赋值给变量时，该变量会被自动分配到默认图中，直到我们显式地将该操作分配到目标图中。我们可以通过检查节点与图的关联来验证我们的参数。

```python
import tensorflow as tf
g_new = tf.Graph()
var_a = tf.constant(10)
print(var_a.graph is tf.get_default_graph())
print(var_a.graph is g_new)
```

在这个示例中，`var_a.graph` 是一个属性，用于检查哪个节点连接到哪个图。当我们在笔记本中运行上述代码时，将得到两个布尔值 `True` 和 `False`。此结果显示节点 `var_a` 与默认图关联，而不是与 `g_new`。

### 使用上下文管理器处理图

那么我们如何将操作分配给新图呢？让我们来看这段代码。

```python
import tensorflow as tf
g_new = tf.Graph()
with g_new.as_default():
    a = tf.add(1, 2)
sess = tf.Session(graph=g_new)
sess.run(a)
```

当我们运行这段代码时，我们将得到输出。我们可以看到通过使用 `graph_name.as_default()` 函数访问新图。

```python
with g_new.as_default():
```

这一行充当了上下文管理器。上下文管理器可以定义为决定何时执行 `with` 语句函数的对象。简单来说，我们可以将其理解为控制 `with` 语句函数下方代码块所有进入和退出语句的管理器。

```python
sess = tf.Session(graph=g_new)
```

`Session` 运行还需要所创建的图的名称。否则，它将始终运行默认图。

### 处理多个图

让我们看另一个关于默认图和新图的示例。

```python
import tensorflow as tf
g_new = tf.Graph()
default_graph = tf.reduce_sum([3, 4])
with g_new.as_default():
    new_graph = tf.reduce_sum([4, 5])
sess = tf.Session()
print(sess.run(default_graph))
sess = tf.Session(graph=g_new)
print(sess.run(new_graph))
```

输出：`7` 和 `20`。

在上面的示例中，第一个打印 语句将打印默认图的输出，第二个打印 语句将打印新图的输出。我们可以看到，在不传递图时它会产生默认图的输出，但在传递图时它会产生输出。让我们看看使用多个图的正确方法。

```python
import tensorflow as tf
graph_1 = tf.get_default_graph()
graph_2 = tf.Graph()
## 现在将每个图设置为默认并在其中分配操作。
default_graph = tf.reduce_sum([3, 4])
with graph_2.as_default():
    new_graph = tf.reduce_prod([4, 5])
```

通过这种方式 `graph_1` 和 `graph_2` 将创建。使用多个图，我们可以将一个模型的输出用于另一个模型。

### Fetch（获取）

我们已经讨论过如何通过在 Fetches 中传递节点来获取每个节点的输出。Fetches 可以定义为一种有助于查找所需输出的技术。我们可以在 `sess.run()` 中放入多个节点，它将返回相应的输出。

```python
import tensorflow as tf
a1 = tf.constant([6, 4, 2], name="input")
a2 = tf.reduce_sum(a1, name="sum_b")
a3 = tf.reduce_prod(a1, name="product_c")
a4 = tf.multiply(a2, a3, name="multiply_d")
sess = tf.Session()
print(sess.run([a2, a3, a4]))
```

当我们运行这段代码时，它将返回输出 `[12, 48, 576]`。如果我们只放入，它将只返回 `a2` 的值。

### TensorFlow 中的 Feeding

Feeding 是 TensorFlow 提供的一种机制，有助于覆盖或替换图中张量的值。它使用 `feed_dict` 参数来替换值，该参数接受字典对象作为输入。字典对象的数据类型与被替换的值类型应该是相同的。

让我们通过例子来看看如何使用馈 机制。

```python
import tensorflow as tf
value1 = tf.reduce_mean([6, 4, 2])
value2 = tf.reduce_mean([1, 8, 6])
value3 = tf.add(value1, value2)
sess = tf.Session()
Replace_value = {value1: 10}
print(sess.run(value3, feed_dict=Replace_value))
```

当我们运行这段代码时，它将返回 15 作为输出。

## 占位符 (Placeholders)

到为止，我们直接向操作中提供输入，或者使用操作来创建输入。但 TensorFlow 提供了另一种提供输入的方法。这可以通过 `placeholder` 实现。占位符名称本身将其定义为一个空张量对象，它在初始化期间没有任何值，但在图的执行过程中可以为其喂入输入数据。

### 为什么使用占位符比常量（constants）更好？
