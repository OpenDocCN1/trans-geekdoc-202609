

![FIGURE 7-4: Each input entering a node has an associated weight.](images/9788126592555-fg0704.png)

[图 7-4：](#12_9788126592555-ch07.xhtml#rc07-fig-0004) 每个进入节点的输入都有一个关联的权重。

要确定输入的总体效应，节点将每个输入乘以其权重并将乘积相加。然后将其与阈值进行比较。如果总和大于阈值，节点产生的输出值等于 1。否则，输出值为 0。

在数学上，权重表示为 `w[i]`，其中 *i* 表示第 *i* 个输入的权重。因此，节点的运算可以用以下关系表示：

![images](images/eq07002.png)<m:math xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mrow><m:mi>y</m:mi><m:mo>=</m:mo><m:mrow><m:mo>{</m:mo><m:mrow><m:mtable><m:mtr><m:mtd><m:mrow><m:mn>1</m:mn><m:mi mathvariant="normal">&#160;if&#160;</m:mi><m:mstyle displaystyle="true"><m:munder><m:mo>&#8721;</m:mo><m:mi>i</m:mi></m:munder><m:mrow><m:msub><m:mi>w</m:mi><m:mi>i</m:mi></m:msub><m:msub><m:mi>x</m:mi><m:mi>i</m:mi></m:msub><m:mo>&#8805;</m:mo><m:mi mathvariant="normal">&#160;threshold</m:mi></m:mrow></m:mstyle></m:mrow></m:mtd></m:mtr><m:mtr><m:mtd><m:mrow><m:mn>0</m:mn><m:mi mathvariant="normal">&#160;otherwise</m:mi></m:mrow></m:mtd></m:mtr></m:mtable></m:mrow></m:mrow></m:mrow></m:math> 

例如，假设 `x[i] = {3.5, -1.0, 2.5, -0.5}` 且 `w[i] = {0.6, 1.2, 0.9, -0.2}`。加权输入的总和可以计算如下：

![images](images/eq07003.png)<m:math xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mrow><m:mstyle displaystyle="true"><m:munder><m:mo>&#8721;</m:mo><m:mi>i</m:mi></m:munder><m:mrow><m:msub><m:mi>w</m:mi><m:mi>i</m:mi></m:msub><m:msub><m:mi>x</m:mi><m:mi>i</m:mi></m:msub><m:mo>=</m:mo><m:mn>3.5</m:mn><m:mrow><m:mo>(</m:mo><m:mrow><m:mn>0.6</m:mn></m:mrow><m:mo>)</m:mo></m:mrow><m:mo>&#45;</m:mo><m:mn>1.0</m:mn><m:mrow><m:mo>(</m:mo><m:mrow><m:mn>1.2</m:mn></m:mrow><m:mo>)</m:mo></m:mrow><m:mo>+</m:mo><m:mn>2.5</m:mn><m:mrow><m:mo>(</m:mo><m:mrow><m:mn>0.9</m:mn></m:mrow><m:mo>)</m:mo></m:mrow><m:mo>&#45;</m:mo><m:mn>0.5</m:mn><m:mrow><m:mo>(</m:mo><m:mrow><m:mo>&#45;</m:mo><m:mn>0.2</m:mn></m:mrow><m:mo>)</m:mo></m:mrow><m:mo>=</m:mo><m:mn>3.25</m:mn></m:mrow></m:mstyle></m:mrow></m:math> 

如果感知器的阈值值为 4.0，节点将产生 0 而不是 1 的输出。

权重在机器学习中发挥着至关重要的作用，因为它们使应用程序能够更新神经网络的行为。随着应用程序执行训练，它会更新权重以改进模型。

### 偏置

当节点的输入加权和超过给定阈值时，节点会激活。换句话说，当加权和与阈值的差值大于零时，它会产生正输出。

与其处理阈值，开发人员经常用一个称为 *偏置* 的常数输入来代替它。 [图 7-5](#12_9788126592555-ch07.xhtml#c07-fig-0005) 显示了添加偏置后的简单神经网络的样子。

![FIGURE 7-5: This node has a constant input called the bias.](images/9788126592555-fg0705.png)

[图 7-5：](#12_9788126592555-ch07.xhtml#rc07-fig-0005) 该节点有一个称为偏置的常数输入。

偏置与其他输入一样接收权重。因此，将偏置的值设为 1 是有意义的，这就是为什么左侧最低的节点被设为 +1。

本书假设每个感知器都有一个偏置，这相当于说阈值等于零。当我使用 *输入* 或 *输入数据* 等术语时，你应假定包含偏置值。因此，当其输入的加权和大于零时，感知器会产生正输出。

### 激活函数

你可以用以下关系计算节点的输出：

![images](images/eq07004.png)<m:math xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mrow><m:mi>y</m:mi><m:mo>=</m:mo><m:mrow><m:mo>{</m:mo><m:mrow><m:mtable><m:mtr><m:mtd><m:mrow><m:mn>1</m:mn><m:mi mathvariant="normal">&#160;if&#160;</m:mi><m:mstyle displaystyle="true"><m:munder><m:mo>&#8721;</m:mo><m:mi>i</m:mi></m:munder><m:mrow><m:msub><m:mi>w</m:mi><m:mi>i</m:mi></m:msub><m:msub><m:mi>x</m:mi><m:mi>i</m:mi></m:msub><m:mo>&#8805;</m:mo><m:mi mathvariant="normal">&#160;threshold</m:mi></m:mrow></m:mstyle></m:mrow></m:mtd></m:mtr><m:mtr><m:mtd><m:mrow><m:mn>0</m:mn><m:mi mathvariant="normal">&#160;otherwise</m:mi></m:mrow></m:mtd></m:mtr></m:mtable></m:mrow></m:mrow></m:mrow></m:math> 

以下方程使用更紧凑的记法表达了相同的关系：

![images](images/eq07005.png)<m:math xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mrow><m:mi>y</m:mi><m:mo>=</m:mo><m:mi>u</m:mi><m:mrow><m:mo>(</m:mo><m:mrow><m:mstyle displaystyle="true"><m:munder><m:mo>&#8721;</m:mo><m:mi>i</m:mi></m:munder><m:mrow><m:msub><m:mi>w</m:mi><m:mi>i</m:mi></m:msub><m:msub><m:mi>x</m:mi><m:mi>i</m:mi></m:msub></m:mrow></m:mstyle></m:mrow><m:mo>)</m:mo></m:mrow></m:mrow></m:math> 

这里，`u(x)` 被称为 *单位阶跃函数*。如果其输入大于 0，则返回 1，否则返回 0。

单位阶跃函数易于理解，但不适用于机器学习。计算机科学家设计了许多更合适的用于产生感知器输出的函数，它们被称为 *激活函数*。

节点的激活函数接受节点的输入加权和并产生单个输出值。在 TensorFlow 中，激活函数接受一个值张量并返回包含输出值的张量。 [表 7-1](#12_9788126592555-ch07.xhtml#c07-tbl-0001) 列出了 TensorFlow 支持的七种激活函数。

[表 7-1](#12_9788126592555-ch07.xhtml#rc07-tbl-0001) 激活函数

| **激活函数** || **描述** |

| --- | --- |

| `tf.nn.relu(input, name=None)` || 如果为正则返回输入值，否则返回 0 |

| --- | --- |

| `tf.nn.relu6(input, name=None)` || 如果为正则返回输入值，最高为 6。否则返回 0 |

| `tf.nn.crelu(input, name=None)` || 返回一个连接的张量，将输入的正负部分分开 |

| `tf.nn.elu(input, name=None)` || 如果为正则返回输入值，否则返回输入的指数 |

| `tf.nn.sigmoid(input, name=None)` || 返回 1/(1 + exp(-x)) |

| `tf.nn.tanh(input, name=None)` || 返回 tanh(x) |

| `tf.nn.softsign(input, name=None)` || 返回 x/(abs(x) + 1) |

我喜欢将这些函数分为两类：整流器和分类器。区别很简单：如果节点的输出标识一个类别，则将其激活函数设为分类器。否则，将节点的激活函数设为整流器。

#### 整流函数

在电子电路中，整流器接受输入信号，如果输入为正，则传输相等的输出信号。如果输入信号为负，整流器传输零输出。

整流线性单元函数，或 ReLU，执行类似的操作。它如果为正则返回输入，否则返回 0。换句话说，ReLU 函数返回输入和 0 的最大值。

在 TensorFlow 中，应用程序可以通过调用 `tf.nn.relu` 执行 ReLU 操作。 [图 7-6](#12_9788126592555-ch07.xhtml#c07-fig-0006) 说明了该函数在一段输入值范围内的输出。

![FIGURE 7-6: The rectified linear unit function (ReLU) only passes positive values.](images/9788126592555-fg0706.png)

[图 7-6：](#12_9788126592555-ch07.xhtml#rc07-fig-0006) 整流线性单元函数（ReLU）只通过正值。

`tf.nn.relu6` 与 `tf.nn.relu` 类似，但将最大输出限制为 6。这种限制降低了节点对大输入过度反应的可能性。 [图 7-7](#12_9788126592555-ch07.xhtml#c07-fig-0007) 说明了 `tf.nn.relu6` 的行为。

