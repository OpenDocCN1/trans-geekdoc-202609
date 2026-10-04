

每个人都知道机器学习是一个快速发展、令人兴奋的领域，适合聪明、有远见的人，而每个人都知道统计学是一个枯燥、死板的领域，适合喜欢 Muzak 的人。因此，新手可能会觉得在一本关于机器学习的书中看到统计分析章节很奇怪。

但机器学习和统计学有很多共同点。事实上，它们的最终目标相同：用数学关系来建模现实世界系统。机器学习大量依赖统计方法，本章介绍了在 TensorFlow 开发中发挥关键作用的三种方法：线性回归、多项式回归和逻辑回归。此外，本章中的示例代码巩固了 TensorFlow 应用程序执行训练的方式。

## 使用回归分析系统

统计学家使用的一种最有效工具是回归。*回归*通过衡量其变量之间的关系来分析系统。TensorFlow 为此分析提供了许多功能，本章重点介绍四种回归类型：

*   **线性回归：**将一条直线拟合到数据集中的点
*   **多项式回归**：将多项式拟合到数据集中的点
*   **二元逻辑回归：**将点分类到两个类别之一
*   **多元逻辑回归：**将点分类到多个类别之一

以下各节将探讨这些简单操作。

## 线性回归：拟合数据直线

在你祖父的阁楼里翻找时，你发现了一本品相完好的《Commander Warpspeed's Journey into Space!》首刊。这本稀有漫画书可能价值数千美元，所以你决定把它卖掉。但你应该要价多少呢？

在线搜索提供了 40 个售价，范围从不到 5,000 美元到超过 10,000 美元。[图 6-1](#11_9788126592555-ch06.xhtml#c06-fig-0001) 在图表上说明了这些价格。

![FIGURE 6-1: The comic book’s value increases over time.](images/9788126592555-fg0601.png)

[FIGURE 6-1:](#11_9788126592555-ch06.xhtml#rc06-fig-0001) The comic book’s value increases over time.

计算平均售价很容易，但你想知道价格是上涨还是下跌，以及上涨或下跌的幅度。为了找到一个合适的售价，你决定用一条线来近似你的数据，该线表示漫画书价格随时间的变化。这个过程称为*线性回归*，[图 6-1](#11_9788126592555-ch06.xhtml#c06-fig-0001) 中的虚线灰线标识了漫画书价格的总体趋势。

TensorFlow 训练的第一步涉及为模型选择初始表达式（参见 [Chapter 5](#09_9788126592555-ch05.xhtml)）。对于线性回归，这个决定很容易。模型是一条线，其方程为 ![images](images/eq06001.png)<m:math xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mrow><m:mi>y</m:mi><m:mo>=</m:mo><m:mi>m</m:mi><m:mi>x</m:mi><m:mo>+</m:mo><m:mi>b</m:mi></m:mrow></m:math>，其中 *m* 是线的斜率，*b* 是 *y-截距*（当 *x* 等于 0 时的 *y* 值）。线性回归的目标是确定 *m* 和 *b*，以便由此产生的线最好地近似（或拟合）点集。

损失也很容易计算。如果图表包含点 (*x, y*)，系统与模型之间的差异为 ![images](images/eq06002.png)<m:math xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mrow><m:mi>y</m:mi><m:mo>&#45;</m:mo><m:mrow><m:mo>(</m:mo><m:mrow><m:mi>m</m:mi><m:mi>x</m:mi><m:mo>+</m:mo><m:mi>b</m:mi></m:mrow><m:mo>)</m:mo></m:mrow></m:mrow></m:math>*.*

在机器学习应用中，损失值应始终具有相同的符号。你可以通过计算每个点的误差平方并取误差值的平均值来确保所有损失值都是正值。如果有 *N* 个点，可以使用以下方程计算损失：

![images](images/eq06003.png)<m:math xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mrow><m:mi>l</m:mi><m:mi>o</m:mi><m:mi>s</m:mi><m:mi>s</m:mi><m:mo>=</m:mo><m:mfrac><m:mn>1</m:mn><m:mi>N</m:mi></m:mfrac><m:mstyle displaystyle="true"><m:munderover><m:mo>&#8721;</m:mo><m:mrow><m:mi>i</m:mi><m:mo>=</m:mo><m:mn>0</m:mn></m:mrow><m:mrow><m:mi>N</m:mi><m:mo>&#45;</m:mo><m:mn>1</m:mn></m:mrow></m:munderover><m:mrow><m:msup><m:mrow><m:mrow><m:mo>(</m:mo><m:mrow><m:mi>y</m:mi><m:mo>&#45;</m:mo><m:mrow><m:mo>(</m:mo><m:mrow><m:mi>m</m:mi><m:mi>x</m:mi><m:mo>+</m:mo><m:mi>b</m:mi></m:mrow><m:mo>)</m:mo></m:mrow></m:mrow><m:mo>)</m:mo></m:mrow></m:mrow><m:mn>2</m:mn></m:msup></m:mrow></m:mstyle></m:mrow></m:math>

这种计算损失的方法称为*均方误差*，或 MSE。在 TensorFlow 中，你可以通过调用 `reduce_mean` 函数来计算它。以下代码展示了如何使用此函数：

```
model = tf.add(tf.multiply(m, x), b)
loss = tf.reduce_mean(tf.pow(model - y, 2))
```

获得损失表达式后，下一步是创建优化器以最小化损失。随着优化器的工作，它将更新变量 `m` 和 `b`，从而获得一条最能近似漫画书价格随时间变化的线。

为此演示，以下代码创建了一个优化器，将其学习率设置为 0.1，并调用其 `minimize` 方法：

```
optimizer = tf.train.GradientDescentOptimizer(0.1)
opt_op = optimizer.minimize(loss)
```

`minimize` 返回一个操作，你可以将其用作会话 `run` 方法的第一个参数（参见 [Chapter 5](#09_9788126592555-ch05.xhtml)）。请注意，你必须重复调用 `run` 以确保训练收敛到 *`m`* 和 *`b`* 的合适值。

在 `ch6` 文件夹中，`lin_regression.py` 包含演示如何在 TensorFlow 中执行线性回归的代码。 [Listing 6-1](#11_9788126592555-ch06.xhtml#c06-fea-0001) 介绍了该代码。

[LISTING 6-1](#11_9788126592555-ch06.xhtml#rc06-fea-0001) Linear Regression

```
# Random input values
N = 40
x = tf.random_normal([N])
m_real = tf.truncated_normal([N], mean=2.0)
b_real = tf.truncated_normal([N], mean=3.0)
y = m_real * x + b_real

# Variables
m = tf.Variable(tf.random_normal([]))
b = tf.Variable(tf.random_normal([]))

# Compute model and loss
model = tf.add(tf.multiply(x, m), b)
loss = tf.reduce_mean(tf.pow(model - y, 2))

# Create optimizer
learn_rate = 0.1
num_epochs = 200
num_batches = N
optimizer = tf.train.GradientDescentOptimizer(learn_rate).minimize(loss)

# Initialize variables
init = tf.global_variables_initializer()

# Launch session
with tf.Session() as sess:
    sess.run(init)

    # Perform training
    for epoch in range(num_epochs):
        for batch in range(num_batches):
            sess.run(optimizer)

    # Display results
    print('m = ', sess.run(m))
    print('b = ', sess.run(b))
```

该模块将批次数量设置为输入点数量。训练过程执行 200 个 epoch，每个 epoch 执行 40 次训练步骤。

## 多项式回归：拟合数据多项式

你可以很容易地将线性回归的方法扩展到多项式。也就是说，将多项式拟合到一组点集的过程与拟合直线所使用的过程基本相同。

为此演示，我解释了如何用三次多项式近似数据。你可以用以下方程表示每个三次多项式：

![images](images/eq06004.png)<m:math xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mrow><m:mi>y</m:mi><m:mo>=</m:mo><m:mi>a</m:mi><m:msup><m:mi>x</m:mi><m:mn>3</m:mn></m:msup><m:mo>+</m:mo><m:mi>b</m:mi><m:msup><m:mi>x</m:mi><m:mn>2</m:mn></m:msup><m:mo>+</m:mo><m:mi>c</m:mi><m:mi>x</m:mi><m:mo>+</m:mo><m:mi>d</m:mi></m:mrow></m:math>

