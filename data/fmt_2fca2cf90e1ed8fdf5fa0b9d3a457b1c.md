
要在 TensorBoard 中查看生成的数据，请打开浏览器到 `http://localhost:6006`。如果单击页面顶部的 HISTOGRAMS 链接，你可以查看张量 `t1` 到 `t4`。图 4-3 显示了 `t1` 的直方图是什么样的。

![FIGURE 4-3: A TensorBoard histogram plots the elements of a tensor.](img/9788126592555-fg0403.png)

FIGURE 4-3: TensorBoard 直方图绘制张量的元素。

与 `t1` 到 `t4` 不同，`t5` 只有一个元素。应用程序通过调用 `tf.summary.scalar` 为 `t5` 生成数据，你可以通过单击页面顶部的 SCALARS 链接在 TensorBoard 中查看此数据。结果并不特别有趣，因为应用程序只执行了一次会话。第 5 章 解释了如何使用多个步骤执行会话并在 TensorBoard 中查看结果数据。

## Training

本章内容

![check](img/check.png)**TensorFlow 中的训练应用程序**

![check](img/check.png)**创建变量和占位符**

![check](img/check.png)**使用优化器最小化损失**

![check](img/check.png)**将数据集拆分为批次**

在互联网之前，像我这样的老派人通过互相交谈来娱乐自己。一个令人兴奋的游戏是 20 个问题，其中一名玩家想一个物体，另一名玩家提问以确定物体是什么。提问者最多只能问 20 个是非问题，一个典型的游戏过程如下：

*   Q: 它比面包盒大吗？
*   A: 是的。
*   Q: 它能移动吗？
*   A: 是的。
*   Q: 它是动物吗？
*   A: 不。
*   Q: 它靠轮子移动吗？
*   A: 不。
*   Q: （叹气）它是邪恶的机器人，Matt？又是吗？
*   A: 就是它！你赢了！

在本章中，我解释了 20 个问题游戏如何与监督机器学习中使用的训练方法相似。

### TensorFlow 中的训练

在 20 个问题游戏中，提问者从一个猜测开始，并随着每个答案不断完善自己的理解。这与监督机器学习中使用的训练方法相似。应用程序从对所需系统的一般想法或模型开始。应用程序将其模型与实验数据进行比较，确定它们之间的差异，并反复完善模型以减少差异。

总体训练过程很容易理解，但使用 TensorFlow 实现训练并不容易。该过程涉及六个步骤：

1.  **构建一般模型的数学表达式。**
2.  **声明在训练过程中要更新的变量。**
3.  **获得损失的表达式，即模型与观察值之间的差异。**
4.  **使用步骤 3 中的损失创建 `Optimizer` 并调用其 `minimize` 方法。**
5.  **（可选）配置会话的 `run` 方法的第二个参数，以将数据批次馈送到会话中。**
6.  **通过调用会话的 `run` 方法执行会话。**

根据 [`StackOverflow.com`](http://StackOverflow.com) 上的问题判断，许多开发人员难以理解如何执行这些步骤。本章解释了此训练过程，然后提供了示例代码，演示了如何在 TensorFlow 应用程序中实现这些步骤。

### 制定模型

正如 20 个问题游戏从做出猜测开始一样，机器学习从形成系统的初始数学模型开始。多种因素决定了该模型的性质，包括系统的复杂性、输入数据的结构以及问题的性质。图像数据需要与语音数据不同的模型。分类问题需要与预测问题不同类型的模型。

本书重点介绍两种数学建模方法。第一种方法是用形状近似一组数据点。例如，如果一个系统由二维点组成，你可以通过用二维直线近似系统来预测未来点。直线由方程 y = mx + b 确定，因此该方程充当一般模型。

第二种方法涉及创建人工神经网络，或 ANN。虽然受生物现象启发，但每个 ANN 都代表一种数学关系。第 7 章 介绍了这一令人兴奋的话题并解释了如何用代码构建 ANN。

无论你是用形状还是神经网络对系统进行建模，都需要不断完善模型，直到它尽可能接近观察到的数据。这种完善涉及更新模型的 参数，例如 *m* 和 *b* 在 ![images](img/eq05001.png)<m:math xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mrow><m:mi mathvariant="normal">y</m:mi><m:mo>=</m:mo><m:mi mathvariant="normal">mx</m:mi><m:mo>+</m:mo><m:mi mathvariant="normal">b</m:mi></m:mrow></m:math> 中。在 TensorFlow 应用程序中，这些可训练参数都是 `Variable` 类的实例。

![tip](img/tip.png)当你与客户交谈时，尽量不要使用 *guess* 这样的术语，例如“哎呀，我们所有的猜测都完全偏离了目标！” 首选术语是 *initial estimate*，例如“初始估计被证明不准确，但后续的训练运行将带来更好的结果。”

### 查看变量

乍一看，变量与张量有很多共同点。两者都将数据存储在多维数组中，并且都可以用 TensorFlow 操作进行处理。

但张量可以用作多种用途，而大多数变量只有一个目的：在训练期间存储要更新的数据。随着训练的进行，变量的值会发生变化，希望每次变化都能使模型更接近所需系统。

变量还有另外三个重要特征：

*   变量在会话的连续执行之间保持其值。
*   变量必须由执行的会话特别初始化。
*   变量是 `Variable` 类的实例，而不是 `Tensor` 类。

最后一点很重要。在处理变量时，你需要调用一组新的方法和函数。以下各节解释了如何创建和初始化变量。

#### 创建变量

应用程序可以通过调用 `tf.Variable` 创建变量，其第一个参数设置变量的初始值。例如，以下代码创建了一个名为 `variableA` 的变量并将其初始值设置为名为 `tensorA` 的张量：

```python
tensorA = tf.constant([1.5, 2.5, 3.5])
```

`variableA = tf.Variable(tensorA)`

变量的职责是在训练期间保存要更新的数据。许多应用在初始化变量时并不使用常量值，而是使用随机值。下面的代码创建了一个名为 `variableB` 的变量，并将其初始值设置为正态分布张量：

`variableB = tf.Variable(tf.random_normal([3]))`

`tf.Variable` 接受一个名为 `trainable` 的布尔参数。如果将此参数设为 `True`，变量就可以通过训练进行更新。如果将其设为 `False`，变量就不能通过训练进行更新。

#### 初始化变量

变量与张量之间一个重要的区别是，你需要执行特殊操作来初始化变量。也就是说，在训练变量之前，你需要创建一个初始化操作并在会话中执行它。如果应用程序尝试使用未初始化的变量，TensorFlow 会抛出错误：Attempting to use uninitialized value….

TensorFlow 提供了三个创建初始化变量操作的函数。表 5-1 列出了它们并提供了每个函数的描述。

TABLE 5-1 变量初始化函数

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

### 确定损失

训练会优化模型变量，以最小化模型与观测数据之间的差异。机器学习文献通常将这种差异称为 *cost function*。TensorFlow 的文档将其称为 *loss*。

例如，如果你用一条直线对一组点进行建模，模型的表达式为 y = mx + b。当然，直线上的点不会完全匹配观测数据 y[obs]。如果有 *N* 个点，可以用以下表达式表示损失：

![images](img/eq05002.png)<m:math xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mrow><m:mi>l</m:mi><m:mi>o</m:mi><m:mi>s</m:mi><m:mi>s</m:mi><m:mo>=</m:mo><m:mfrac><m:mn>1</m:mn><m:mi>N</m:mi></m:mfrac><m:mstyle displaystyle="true"><m:munderover><m:mo>&#8721;</m:mo><m:mrow><m:mi>i</m:mi><m:mo>=</m:mo><m:mn>0</m:mn></m:mrow><m:mrow><m:mi>N</m:mi><m:mo>&#45;</m:mo><m:mn>1</m:mn></m:mrow></m:munderover><m:mrow><m:msup><m:mrow><m:mrow><m:mo>(</m:mo><m:mrow><m:msub><m:mi>y</m:mi><m:mrow><m:mi>o</m:mi><m:mi>b</m:mi><m:mi>s</m:mi></m:mrow></m:msub><m:mo>&#45;</m:mo><m:mrow><m:mo>(</m:mo><m:mrow><m:mi>m</m:mi><m:mi>x</m:mi><m:mo>+</m:mo><m:mi>b</m:mi></m:mrow><m:mo>)</m:mo></m:mrow></m:mrow><m:mo>)</m:mo></m:mrow></m:mrow><m:mn>2</m:mn></m:msup></m:mrow></m:mstyle></m:mrow></m:math>

在 TensorFlow 应用程序中，可以用以下代码表达模型和损失：

```
m = tf.Variable(tf.random_normal([]))
b = tf.Variable(tf.random_normal([]))
model = tf.add(tf.multiply(x, m), b)
loss = tf.reduce_mean(tf.pow(model - y, 2))
```

这种计算损失的方法称为 *mean squared error*，它是众多方法之一——最大似然估计和对数似然估计也很流行。第 6 章 讨论了统计回归以及计算损失的不同方法。

如果你的模型包含神经网络，就无法用简单方程计算损失。前馈网络需要像反向传播这样的特殊算法，而循环网络则依赖于通过时间的反向传播（BPTT）。我在 第 7 章 中讨论了神经网络和反向传播。我在 第 9 章 中介绍了 BPTT。

![remember](img/remember.png)计算损失没有唯一正确的方法。唯一的要求是，每次损失的减少都必须意味着模型更接近观测数据。通过降低损失来改进模型的过程称为 *optimization*。

### 使用优化最小化损失

在形成损失表达式之后，下一步是通过更新模型变量来最小化损失。此过程称为 *optimization*，TensorFlow 为此目的支持多种算法。选择合适的算法对于编写机器学习应用程序至关重要。

每种优化方法在 `tf.train` 包中都由一个类表示。四种流行的优化类是 `GradientDescentOptimizer`、`MomentumOptimizer`、`AdagradOptimizer` 和 `AdamOptimizer` 类。以下各节将介绍这些类中的每一个，从 `Optimizer` 类开始，它是 TensorFlow 优化类的基类。

#### Optimizer 类

你不能直接在代码中访问 `Optimizer` 类；应用程序需要实例化其子类之一。但 `Optimizer` 类至关重要，因为它定义了至关重要的 `minimize` 方法：

`minimize(loss, global_step=None, var_list=None, gate_gradients=1, aggregation_method=None, colocate_gradients_with_ops=False, name=None, grad_loss=None)`

唯一必需的参数是第一个参数，它标识损失。默认情况下，`minimize` 可以访问图中的每个可训练变量。应用程序可以通过设置 `var_list` 参数来选择要优化的特定变量。

`minimize` 返回一个操作，可以由会话的 `run` 方法执行。每次执行都会执行两个步骤：

1. **计算更新目标变量的值。**
2. **用第 1 步计算的值更新目标变量。**

正如你可能不会用第一个问题就赢得 20 Questions 一样，你可能也不会通过一次调用 `minimize` 就优化模型。大多数应用程序都在循环中执行优化，下面的代码展示了优化循环的大致样子：

```
#### Create the optimizer and obtain the operation
optimizer = tf.train.GradientDescentOptimizer(learn_rate)
optimizer_op = minimize(loss)

#### Execute the minimization operation in a session
with tf.Session() as sess:
    for step in range(num_steps):
        sess.run(optimizer_op)
```

如果优化器达到合适的最小值，它就已 *converged* 到最小值。如果它未能达到最小值，优化器就已 *diverged*。

每次调用会话的 `run` 方法都会通过更新变量来最小化损失。应用程序通过创建 `Optimizer` 的子类来控制更新方式。本文讨论了四种流行的 `Optimizer` 子类：`GradientDescentOptimizer`、`MomentumOptimizer`、`AdagradOptimizer` 和 `AdamOptimizer`。

![technicalstuff](img/technicalstuff.png)下面的讨论变得非常技术化，如果你刚开始学习机器学习，其实不需要知道这些数学知识。然而，选择合适的优化器会对应用程序的性能产生重大影响。此外，如果你正在面试一份高薪的 TensorFlow 工作，你应该能够解释为什么你更喜欢 `AdamOptimizer` 而不是 `GradientDescentOptimizer`。

#### GradientDescentOptimizer

`GradientDescentOptimizer` 是机器学习中使用最简单、最常见的优化器之一。如果你查看在线示例代码或机器学习教材，你很可能会经常遇到此优化器。

尽管很受欢迎，但很少有专家推荐使用 `GradientDescentOptimizer` 而不是其他替代方案。要了解原因，你需要理解它用于执行优化的算法。在本讨论中，我将介绍梯度下降的理论，然后解释如何在代码中创建和使用 `GradientDescentOptimizer`。

##### 梯度下降算法

`GradientDescentOptimizer` 使用梯度下降算法最小化损失，该算法依赖于一个关键的数学事实：在某一点上，函数沿其负梯度方向下降最快。

如果你学过微积分，你就知道函数在某一点的导数等于函数在该点的斜率。也就是说，如果 `f(x)` 可微，其关于 *x* 的导数记为 `f'(x)`，而在点 *a* 处的斜率记为 `f'(a)`。图 5-1 显示了函数导数的样子。

![FIGURE 5-1: The derivative at a point equals the slope of the curve at that point.](img/9788126592555-fg0501.png)

FIGURE 5-1: The derivative at a point equals the slope of the curve at that point.

具有多个变量的函数有多个导数。以 `f(x, y)` 为例，它有关于 *x* 的导数和关于 *y* 的导数。这些是 *偏导数*，用以下记号表示：
