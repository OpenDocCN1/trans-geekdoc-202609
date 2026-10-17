

```
nn_check = MLPGradientCheck(n_output=10, 
                            n_features=X_train.shape[1], 
                            n_hidden=10, 
                            l2=0.0, 
                            l1=0.0, 
                            epochs=10, 
                            eta=0.001,
                            alpha=0.0,
                            decrease_const=0.0,
                            minibatches=1, 
                            random_state=1)
```

```
nn_check.fit(X_train[:5], y_train[:5], print_progress=False)
```

```
Ok: 2.56712936241e-10
Ok: 2.94603251069e-10
Ok: 2.37615620231e-10
Ok: 2.43469423226e-10
Ok: 3.37872073158e-10
Ok: 3.63466384861e-10
Ok: 2.22472120785e-10
Ok: 2.33163708438e-10
Ok: 3.44653686551e-10
Ok: 2.17161707211e-10
```

```
<__main__.MLPGradientCheck at 0x10a13ab70>
```

# 2.1 简介 - Theano

## Theano

### 语言中的语言

处理权重矩阵和梯度可能很棘手，有时并不简单。Theano 是处理向量、矩阵和高维张量代数的优秀框架。本教程大部分内容将涉及 Theano，但 TensorFlow 是另一个能够为复杂代数提供惊人抽象的优秀框架。有关 TensorFlow 的更多内容将在后续章节中介绍。

```
import theano
import theano.tensor as T
```

### 符号变量

Theano 有自己的变量和函数，定义如下

```
x = T.scalar()
```

```
x
```

```
<TensorType(float64, scalar)>
```

变量可以用于表达式

```
y = 3*(x**2) + 1
```

`y` 现在是一个表达式

结果也是符号的

```
type(y)
y.shape
```

```
Shape.0
```

#### 打印

正如我们即将看到的，在处理 Theano 时，普通打印不是最佳选择

```
print(y)
```

```
Elemwise{add,no_inplace}.0
```

```
theano.pprint(y)
```

```
'((TensorConstant{3} * (<TensorType(float64, scalar)> ** TensorConstant{2})) + TensorConstant{1})'
```

```
theano.printing.debugprint(y)
```

```
Elemwise{add,no_inplace} [id A] ''   
 |Elemwise{mul,no_inplace} [id B] ''   
 | |TensorConstant{3} [id C]
 | |Elemwise{pow,no_inplace} [id D] ''   
 |   |<TensorType(float64, scalar)> [id E]
 |   |TensorConstant{2} [id F]
 |TensorConstant{1} [id G]
```

### 计算表达式

提供一个将变量映射到值的 `dict`

```
y.eval({x: 2})
```

```
array(13.0)
```

或者编译一个函数

```
f = theano.function([x], y)
```

```
f(2)
```

```
array(13.0)
```

### 其他张量类型

```
X = T.vector()
X = T.matrix()
X = T.tensor3()
X = T.tensor4()
```

### 自动微分

*   梯度是免费的！

```
x = T.scalar()
y = T.log(x)
```

```
gradient = T.grad(y, x)
print(gradient)
print(gradient.eval({x: 2}))
print((2 * gradient))
```

```
Elemwise{true_div}.0
0.5
Elemwise{mul,no_inplace}.0
```

### 共享变量

*   符号 + 存储

```
import numpy as np
x = theano.shared(np.zeros((2, 3), dtype=theano.config.floatX))
```

```
x
```

```
<TensorType(float64, matrix)>
```

我们可以获取和设置变量的值

```
values = x.get_value()
print(values.shape)
print(values)
```

```
(2, 3)
[[ 0.  0.  0.]
 [ 4.  4.  4.]]
```

```
x.set_value(values)
```

共享变量也可以用于表达式

```
(x + 2) ** 2
```

```
Elemwise{pow,no_inplace}.0
```

它们的值在计算时用作输入

```
((x + 2) ** 2).eval()
```

```
array([[ 4.,  4.,  4.],
       [ 4.,  4.,  4.]])
```

```
theano.function([], (x + 2) ** 2)()
```

```
array([[ 4.,  4.,  4.],
       [ 4.,  4.,  4.]])
```

### 更新

*   存储函数计算结果

*   将共享变量映射到新值的 `dict`

```
count = theano.shared(0)
new_count = count + 1
updates = {count: new_count}

f = theano.function([], count, updates=updates)
```

```
f()
```

```
array(0)
```

```
f()
```

```
array(1)
```

```
f()
```

```
array(2)
```

# 2.2 简介 - Tensorflow

![](tensorflow_head.png)

## Tensorflow

> **TensorFlow** ([https://www.tensorflow.org/](https://www.tensorflow.org/)) 是由 Google Brain 团队在 Google 的机器学习智能研究组织内开发的软件库，用于进行机器学习和深度神经网络研究。

> TensorFlow 结合了编译优化技术的计算代数，使许多难以计算的数学表达式的计算变得容易。

### Tensorflow 主要特性

*   定义、优化和高效计算涉及多维数组（张量）的数学表达式。

*   对 `深度神经网络` 和机器学习技术的编程支持。

*   透明使用 GPU 计算，自动管理和优化相同的内存和使用的数据。您可以编写相同的代码并在 CPU 或 GPU 上运行。更具体地说，TensorFlow 将确定计算的哪些部分应移动到 GPU。

*   跨机器和大型数据集的计算高可扩展性。

> TensorFlow 支持 Python 和 C++，但 `Python API` 支持更好，也更容易学习。

### 非常初步的示例

```
# A simple calculation in Python
x = 1
y = x + 10
print(y)
```

```
11
```

```
import tensorflow as tf
```

```
# The ~same simple calculation in Tensorflow
x = tf.constant(1, name='x')
y = tf.Variable(x+10, name='y')
print(y)
```

```
<tf.Variable 'y:0' shape=() dtype=int32_ref>
```

**含义**：当计算变量 `y` 时，取常量 `x` 的值并加上 `10`

### 会话和模型

要实际计算变量 `y` 的值并计算表达式，我们需要**初始化**变量，然后创建一个**会话**，实际计算在其中进行

```
model = tf.global_variables_initializer()  # model is used by convention
```

```
with tf.Session() as session:
    session.run(model)
    print(session.run(y))
```

```
11
```

### 数据流图

*   (**IDEA**) \_机器学习应用程序是复杂数学表达式重复计算的结果，因此我们可以使用**数据流图**来描述此计算

*   **数据流图**：一个图，其中：

    *   每个节点表示数学操作的*实例*

        *   `multiply`、`add`、`divide`

    *   每条边是执行操作的多维数据集（`张量`）。

### Tensorflow 图模型

*   **节点**：在 TensorFlow 中，每个节点表示操作的实例化。

    *   每个操作有输入（`>= 2`）和输出 `>= 0`。

*   **边**：在 TensorFlow 中，有两种类型的边：

    *   数据边：它们是数据结构（`张量`）的载体，其中一个操作（来自一个节点）的输出成为另一个操作的输入。

    *   依赖边：这些边表示两个节点之间的*控制依赖*（即“先发生”关系）。

        *   假设我们有两个节点 `A` 和 `B` 以及一条连接 `A` 到 `B` 的依赖边。这意味着 `B` 只有在 `A` 中的操作结束后才会开始其操作。

### Tensorflow 图模型（续）

*   **操作**：这表示一个抽象计算，例如添加或乘以矩阵。

    *   一个操作管理张量，并且可以是多态的：相同的操作可以操作不同的张量元素类型。

        *   例如，两个 int32 张量的加法，两个 float 张量的加法，等等。

*   **内核**：这表示该操作的具体实现。

    *   内核定义了操作在特定设备上的实现。

        *   例如，一个 `add matrix` 操作可以有 CPU 实现和 GPU 实现。

### Tensorflow 图模型会话

**会话**：当客户端程序需要与 TensorFlow 运行时系统建立通信时，必须创建一个会话。

