
当我们使用`constant`时，它的值会被复制到图中。假设我们初始化了一个大型全 1 或全零矩阵作为常量操作，例如`initialize_ones = np.ones((3000, 3000))`。此操作不仅向图中添加了一个单独的操作，还将 900 万个常量元素复制到图中。因此，每当加载图时，常量值就会被复制。这导致图的加载变得缓慢且昂贵。我们可以通过打印图的 protobuf（协议缓冲区）来检查该参数。

让我们通过一个例子来理解这一点。

```python
import tensorflow as tf
constant_value = tf.constant([6, 4, 2], name="constant_value")
print(tf.get_default_graph().as_graph_def())
```

当运行这段代码时，它将返回如图所示的输出。现在当我们在 notebook 中多次运行代码时，字典的数量不断增加。这表明常量的值在加载图时会被复制。占位符初始化的是单个操作，它在`session.run()`内部执行。在之后，不再需要的资源将通过关闭 session 释放，因此，它不会在图中复制张量对象。

![](img/image-3ld4eoqm.jpg) 图 1.13

占位符对数据大小非常灵活。我们可以初始化输入的大小，也可以提及`None`。当我们把`None`值作为形状参数传递时，它允许占位符接受任何大小的数据。占位符中的数据类型也应该初始化，以避免任何匹配错误。占位符一旦初始化，必须喂入输入数据，否则会抛出异常。使用喂入机制（Feeding mechanism）向占位符中提供数据。

让我们通过一个例子来理解占位符的使用。

```python
import tensorflow as tf
import numpy as np
x_matrix = np.random.randn(3, 1)
m_matrix = np.random.randn(3, 3)
x = tf.placeholder(tf.float32, shape=(3, 1))
m = tf.placeholder(tf.float32, shape=(3, 3))
c = tf.ones((3,1))
mx = tf.matmul(m, x)
y = mx + c
value = tf.reduce_mean(y)
sess = tf.Session()
sess.run(value, feed_dict={x: x_matrix, m: m_matrix})
```

在上面的示例中，我们实现了方程`y = mx + c`。最初，我们使用 NumPy 定义了两个矩阵和一个向量的值。我们将两个输入`x`和`m`初始化为占位符，它们最终在执行过程中被填充。

## 变量 (Variables)

到目前为止，我们一直使用常量作为输入，这很有趣。现在，让我们讨论变量，另一个非常重要的张量对象。

在优化或学习过程中，变量起着关键性的作用。在此类过程中，不同类型的参数和超参数需要连续且正确地调整，直到它们找到适应模型的最佳值。在每次迭代中，它的值都会不断更新。在讨论占位符时，我们讨论了使用常量操作的缺点。变量也可以作为常量操作的替代。在涉及更多数据的地方应该使用变量，因为它们需要更多内存。变量单独存储，通常它们不会被复制。

### 如何创建变量

当我们实例化类的实例时会声明变量。常量使用小写的`c`，而在`Variable`中使用大写的`V`。这种差异产生是因为`tf.constant`是一个操作，而`tf.Variable`是一个类，因为它提供了多个一个函数。

可以使用 TensorFlow 操作创建变量：

```python
import tensorflow as tf
var = tf.Variable(10, name="create_variable")
value1 = tf.multiply(2, var)
value2 = tf.reduce_max(5, var)
```

好了，现在我们将讨论如何初始化变量。

正如我们上面讨论的，变量的状态或简单来说，变量的值由 session 处理。要使用变量，首先我们必须初始化它们，它们将在`session run`中执行。通常，初始化是通过使用`tf.global_variables_initializer()`完成的，之后内存会被分配给变量。

```python
import tensorflow as tf
x = tf.Variable(tf.truncated_normal([2, 1], mean=5.0, stddev=1.0))
m = tf.Variable(tf.random_normal([2, 2], stddev=0.1))
c = tf.Variable(tf.ones([2, 1]))

mx = tf.matmul(m, x);
y = tf.add(mx, c)

initializer = tf.global_variables_initializer()
sess = tf.Session()
sess.run(initializer)
print(sess.run(y))
sess.close()
```

在这个示例中，我们计算了方程`y = mx + c`的值。运行这段代码时，它将返回`[[0.4051047], [0.507525]]`作为输出。注意，`sess.run(initializer)`用于初始化变量，它并不获取任何值。

让我们来看另一个例子。

```python
import tensorflow as tf
variable1 = tf.Variable(2)
constant1 = tf.constant(2)
new_variable = tf.multiply(variable1, constant1)
update_variable = tf.assign(variable1, new_variable)
initialize_variable = tf.global_variables_initializer()
sess = tf.Session()
sess.run(initialize_variable)
print(sess.run(variable1))
for i in range(2):
    sess.run(update_variable)
    print(sess.run(variable1))
```

在这个示例中，`variable1`被创建为变量标量值，`constant1`是常量标量值，`new_variable`在相乘`variable1`后返回输出。在下一步中，`tf.assign()`更新了`variable1`的值。运行这段代码时，它返回 4 和 8 作为输出。这表明`variable1`在每次迭代中不断改变其值。

到目前为止，我们讨论了变量的全局初始化。让我们通过一个例子来理解自定义初始化。

```python
import tensorflow as tf
variable1 = tf.Variable(6)
variable2 = tf.Variable([6, 4])
variable3 = tf.Variable(tf.truncated_normal([2, 2]))
```

在这个示例中，`variable1`被创建为变量标量值，`variable2`被创建为变量向量，`variable3`被创建为 2x2 大的随机变量对象。

要初始化自定义变量，我们使用`tf.variables_initializer()`并传入需要初始化的变量列表。

```python
initialize_variable_1_and_2 = tf.variables_initializer([variable1, variable2], name="initialize_1_and_2")
with tf.Session() as sess:
    sess.run(initialize_variable_1_and_2)
```

我们也可以使用逐个初始化每个变量：

```python
variable3 = tf.Variable(tf.truncated_normal([2, 2]))
sess = tf.Session()
sess.run(variable3.initializer)
print(sess.run(variable3))
```

这段代码将返回一个 2x2 大的随机值矩阵。

## 给变量赋值

TensorFlow 提供了一种为变量进行赋值的技巧。我们可以使用`Variable.assign()`函数来改变变量的值。让我们通过几个示例来熟悉这个函数。

```python
import tensorflow as tf
a = tf.Variable(4)
a.assign(6)
with tf.Session() as sess:
    sess.run(a.initializer)
    print(sess.run(a))
```

当我们运行这段代码时，它将返回 4 作为输出，这意味着`a.assign(6)`没有生效。为了让此操作生效，`Variable.assign()`应该始终在 session 中运行。

```python
import tensorflow as tf
a = tf.Variable(4)
assign_to_a = a.assign(6)
with tf.Session() as sess:
    sess.run(assign_to_a)
    print(sess.run(a))
```

现在执行后，这段代码将返回输出。注意，在此代码中`a`仍然没有初始化，它之所以能工作是因为是由`assign()`操作完成的。事实上，如果我们分析初始化操作，可以认为初始化操作实现的内容与此`assign`操作所做的相同。思考，初始化操作也将变量的初始值赋值给变量本身。

让我们看另一个示例。

```python
import tensorflow as tf
var = tf.Variable(4)
var_plus_2 = var.assign(var + 2)
initializer = tf.global_variables_initializer()
with tf.Session() as sess:
    sess.run(initializer)
    print(sess.run(var_plus_2))
    print(sess.run(var_plus_2))
```

这段代码的输出是 6。在这个示例中，如果我们在不初始化`var`的情况下在`sess.run()`中放入`var_plus_2`，将会报错，因为`var_plus_2`的值依赖于`var`。因此，`var`需要先初始化。

为了对变量进行加减法，TensorFlow 提供了如`tf.Variable.assign_add()`等操作。注意，`tf.Variable.assign_add()`和`tf.Variable.assign_sub()`方法不会初始化变量，因为这些操作的输出需要变量的初始值作为输入。在每个 Session 中，数据是保持分离的。假设我们在图中创建了一个变量，现在我们在不同的 Sessions 下执行图，那么每个 session 都可以有不同的变量值。让我们通过示例来理解这一点。

```python
import tensorflow as tf
a = tf.Variable(4)
sess1 = tf.Session()
sess2 = tf.Session()
sess1.run(a.initializer)
sess2.run(a.initializer)
print sess1.run(a.assign_add(1))
print sess2.run(a.assign_add(2))
print sess1.run(a.assign_sub(10))
print sess2.run(a.assign_sub(2))
sess1.close()
sess2.close()
```

当我们运行这段代码时，它将返回输出 -5，我们可以看到变量`a`在不同的 session 下不同的值。

## 名称作用域 (Name scopes)

到目前为止，我们讨论了 TensorFlow 图的基本概念和实现。目前，我们讨论的是节点较少、张量对象较小的计算图，但在为实际应用构建模型时，我们必须处理具有数百个节点和数百万参数的大型图。在处理大型且复杂的图时，我们倾向于使用唯一标识对节点进行分级分组。因此，这有助于通过分块观察来管理大型图。TensorFlow 这种名为名称作用域（name scopes）的机制，有助于管理大型图。名称作用域易于使用，并在 TensorBoard 可视化时提供良好的洞察。通过名称作用域，我们可以将节点排列成块。当我们使用 TensorBoard 时，我们可以看到所有封装在各自作用域名称中的操作。我们可以通过实现这一行`with`来开始使用名称作用域。

让我们通过示例来理解名称作用域。

```python
import tensorflow as tf
with tf.name_scope("1st_scope"):
    a = tf.multiply(6, 4, name="multiply1")
    b = tf.add(a, 6, name="add1")
    with tf.name_scope("2nd_scope"):
        c = tf.multiply(4, 5, name="multiply2")
        d = tf.add(c, 10, name="add2")
        e = tf.div(b, d, name="output")
sess = tf.Session()
writer = tf.summary.FileWriter("output")
sess.run(e)
writer.close()
```

`with tf.name_scope("1st_scope"):`

这一行创建了名为`1st_scope`的第一个框，相应的操作被分组在该名称作用域下。

`with`

这一行创建了名为（此处）的第二个框，相应的操作被分组在该名称作用域下。

当我们运行这段代码时，它将返回 1 作为输出。让我们用 TensorBoard 可视化图。图 1.14 和 1.15 代表 TensorBoard 中所示的图：

![](img/image-uje4tc1g.jpg)

图 1.14

当我们查看 TensorBoard 图时，它不会显示每个操作。此图显示节点被分组在`1st_scope`中，当双击两个名称作用域框中的加号 (`+`) 图标时，它会展开并类似于图：

![](img/image-4iimvpr1.jpg)

图 1.15

在前面的图中，我们可以很容易看到单独的操作。让我们看名称作用域的另一个示例。

```python
import tensorflow as tf
import numpy as np
g = tf.Graph()
with g.as_default():
    input_1 = tf.placeholder(tf.float32, shape=None, name="input_1")
    input_2 = tf.placeholder(tf.float32, shape=None, name="input_2")
    const = tf.constant(4, name="constant")
    with tf.name_scope("Chain"):
        with tf.name_scope("LayerA"):
            LA_sub = tf.subtract(input_1, const)
            LA_output = tf.div(input_1, LA_sub)
        with tf.name_scope("LayerB"):
            LB_sub = tf.subtract(input_2, const)
            LB_output = tf.div(input_2, LB_sub)
        with tf.name_scope("LayerC"):
            LC_max = tf.add(LA_output, LB_output)
            LC_output = tf.multiply(LC_max, const)
        with tf.name_scope("LayerD"):
                LD_max = tf.add(LC_output, LB_output)
                LD_output = tf.multiply(LD_max, const)
        output = tf.add(LC_output, LD_output)
var_1 = np.array([8])
var_2 = np.array([6])
initialize_operation = tf.global_variables_initializer()
sess = tf.Session(graph=g)
sess.run(initialize_operation)
writer = tf.summary.FileWriter("output", graph=g)
print(sess.run(output, feed_dict={input_1: var_1, input_2: var_2}))
writer.close()
```

当我们运行这段代码时，它将返回输出。图展示了之前示例的高级概览。当我们点击名为 chain 的名称作用域中的加号 (`+`) 图标时，它将显示出排列两层的四个名称作用域。LayerA 和 LayerB 组成第一层。LayerA 和 LayerB 的输出传递给下一层的 LayerC 和 LayerD。最后，最后一个节点使用第二层的输出作为输入。这个示例为我们提供了另一种可视化图的方法。在图中我们可以看到第一层名称作用域的颜色是相同的，第二层也可以观察到类似的情况。
