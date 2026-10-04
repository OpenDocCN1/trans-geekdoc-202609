

`variableA = tf.Variable(tensorA)`

变量的职责是在训练期间保存要更新的数据。许多应用在初始化变量时并不使用常量值，而是使用随机值。下面的代码创建了一个名为 `variableB` 的变量，并将其初始值设置为正态分布张量：

`variableB = tf.Variable(tf.random_normal([3]))`

`tf.Variable` 接受一个名为 `trainable` 的布尔参数。如果将此参数设为 `True`，变量就可以通过训练进行更新。如果将其设为 `False`，变量就不能通过训练进行更新。

### 初始化变量

变量与张量之间一个重要的区别是，你需要执行特殊操作来初始化变量。也就是说，在训练变量之前，你需要创建一个初始化操作并在会话中执行它。如果应用程序尝试使用未初始化的变量，TensorFlow 会抛出错误：Attempting to use uninitialized value….

TensorFlow 提供了三个创建初始化变量操作的函数。 [表 5-1](#09_9788126592555-ch05.xhtml#c05-tbl-0001) 列出了它们并提供了每个函数的描述。

[TABLE 5-1](#09_9788126592555-ch05.xhtml#rc05-tbl-0001) 变量初始化函数

| **Function** || **Description** |

| --- | --- |

| `variable_initializer(var_list, name='init')` || 返回一个初始化给定列表中变量的操作 |

| --- | --- |

| `local_variables_initializer()` || 返回一个初始化所有局部变量的操作 |

| `global_variables_initializer()` || 返回一个初始化所有全局变量的操作 |

应用程序通常调用 `global_variables_initializer`，因为它会创建一个初始化会话中每个全局变量的操作。下面的代码展示了如何调用此函数：

```
init = tf.global_variables_initializer()

...

with tf.Session() as sess:
    sess.run(init)
```

应用程序可以通过调用 `is_variable_initialized` 并传入变量的名称来检查变量是否已初始化。

## 确定损失

训练会优化模型变量，以最小化模型与观测数据之间的差异。机器学习文献通常将这种差异称为 *cost function*。TensorFlow 的文档将其称为 *loss*。

例如，如果你用一条直线对一组点进行建模，模型的表达式为 y = mx + b。当然，直线上的点不会完全匹配观测数据 y[obs]。如果有 *N* 个点，可以用以下表达式表示损失：

![images](images/eq05002.png)<m:math xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mrow><m:mi>l</m:mi><m:mi>o</m:mi><m:mi>s</m:mi><m:mi>s</m:mi><m:mo>=</m:mo><m:mfrac><m:mn>1</m:mn><m:mi>N</m:mi></m:mfrac><m:mstyle displaystyle="true"><m:munderover><m:mo>&#8721;</m:mo><m:mrow><m:mi>i</m:mi><m:mo>=</m:mo><m:mn>0</m:mn></m:mrow><m:mrow><m:mi>N</m:mi><m:mo>&#45;</m:mo><m:mn>1</m:mn></m:mrow></m:munderover><m:mrow><m:msup><m:mrow><m:mrow><m:mo>(</m:mo><m:mrow><m:msub><m:mi>y</m:mi><m:mrow><m:mi>o</m:mi><m:mi>b</m:mi><m:mi>s</m:mi></m:mrow></m:msub><m:mo>&#45;</m:mo><m:mrow><m:mo>(</m:mo><m:mrow><m:mi>m</m:mi><m:mi>x</m:mi><m:mo>+</m:mo><m:mi>b</m:mi></m:mrow><m:mo>)</m:mo></m:mrow></m:mrow><m:mo>)</m:mo></m:mrow></m:mrow><m:mn>2</m:mn></m:msup></m:mrow></m:mstyle></m:mrow></m:math>

在 TensorFlow 应用程序中，可以用以下代码表达模型和损失：

```
m = tf.Variable(tf.random_normal([]))
b = tf.Variable(tf.random_normal([]))
model = tf.add(tf.multiply(x, m), b)
loss = tf.reduce_mean(tf.pow(model - y, 2))
```

这种计算损失的方法称为 *mean squared error*，它是众多方法之一——最大似然估计和对数似然估计也很流行。 [第 6 章](#11_9788126592555-ch06.xhtml) 讨论了统计回归以及计算损失的不同方法。

如果你的模型包含神经网络，就无法用简单方程计算损失。前馈网络需要像反向传播这样的特殊算法，而循环网络则依赖于通过时间的反向传播（BPTT）。我在 [第 7 章](#12_9788126592555-ch07.xhtml) 中讨论了神经网络和反向传播。我在 [第 9 章](#14_9788126592555-ch09.xhtml) 中介绍了 BPTT。

![remember](images/remember.png)计算损失没有唯一正确的方法。唯一的要求是，每次损失的减少都必须意味着模型更接近观测数据。通过降低损失来改进模型的过程称为 *optimization*。

## 使用优化最小化损失

在形成损失表达式之后，下一步是通过更新模型变量来最小化损失。此过程称为 *optimization*，TensorFlow 为此目的支持多种算法。选择合适的算法对于编写机器学习应用程序至关重要。

每种优化方法在 `tf.train` 包中都由一个类表示。四种流行的优化类是 `GradientDescentOptimizer`、`MomentumOptimizer`、`AdagradOptimizer` 和 `AdamOptimizer` 类。以下各节将介绍这些类中的每一个，从 `Optimizer` 类开始，它是 TensorFlow 优化类的基类。

### Optimizer 类

你不能直接在代码中访问 `Optimizer` 类；应用程序需要实例化其子类之一。但 `Optimizer` 类至关重要，因为它定义了至关重要的 `minimize` 方法：

`minimize(loss, global_step=None, var_list=None, gate_gradients=1, aggregation_method=None, colocate_gradients_with_ops=False, name=None, grad_loss=None)`

唯一必需的参数是第一个参数，它标识损失。默认情况下，`minimize` 可以访问图中的每个可训练变量。应用程序可以通过设置 `var_list` 参数来选择要优化的特定变量。

`minimize` 返回一个操作，可以由会话的 `run` 方法执行。每次执行都会执行两个步骤：

1. **计算更新目标变量的值。**
2. **用第 1 步计算的值更新目标变量。**

正如你可能不会用第一个问题就赢得 20 Questions 一样，你可能也不会通过一次调用 `minimize` 就优化模型。大多数应用程序都在循环中执行优化，下面的代码展示了优化循环的大致样子：

```
# Create the optimizer and obtain the operation
optimizer = tf.train.GradientDescentOptimizer(learn_rate)
optimizer_op = minimize(loss)

# Execute the minimization operation in a session
with tf.Session() as sess:
    for step in range(num_steps):
        sess.run(optimizer_op)
```

如果优化器达到合适的最小值，它就已 *converged* 到最小值。如果它未能达到最小值，优化器就已 *diverged*。

每次调用会话的 `run` 方法都会通过更新变量来最小化损失。应用程序通过创建 `Optimizer` 的子类来控制更新方式。本文讨论了四种流行的 `Optimizer` 子类：`GradientDescentOptimizer`、`MomentumOptimizer`、`AdagradOptimizer` 和 `AdamOptimizer`。

![technicalstuff](images/technicalstuff.png)下面的讨论变得非常技术化，如果你刚开始学习机器学习，其实不需要知道这些数学知识。然而，选择合适的优化器会对应用程序的性能产生重大影响。此外，如果你正在面试一份高薪的 TensorFlow 工作，你应该能够解释为什么你更喜欢 `AdamOptimizer` 而不是 `GradientDescentOptimizer`。

### GradientDescentOptimizer

`GradientDescentOptimizer` 是机器学习中使用最简单、最常见的优化器之一。如果你查看在线示例代码或机器学习教材，你很可能会经常遇到此优化器。

