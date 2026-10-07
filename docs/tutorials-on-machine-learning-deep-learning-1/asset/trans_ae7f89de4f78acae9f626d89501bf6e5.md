

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_223_0.png)

**神经元**：信号进入神经元后会发生几件事。

- A. 第一件事，也是**第一步**，是将变量的相应权重相加，即所有**输入值**的**加权和**。
- B. 其次，对这个**加权和**应用一个**激活函数**。
- 基本上，*激活函数*是一个分配给*神经元*或这*整个层*的函数，并应用于它的加权和上。
- **激活函数**决定了它是否**需要向下一个神经元**（或层）**传递信号**，即取决于**激活函数**，*神经元*将可以传递信号，也可以不传递信号。
- C. 这就是**第三步**中恰发生的事情。**神经元**将该**信号**传递给链下游的**下一个神经元**。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_223_1.png)

这就是你如何获得输入值和权重。在神经元中发生的是求和以及对加权和应用激活函数，然后将其传递下去，这在**整个神经网络中不断重复**，这取决于你的神经网络有多**大**、你有多少个**神经元**以及多少个**突触**。

# 笔记：

- 归一化（Normalization）是机器学习中常用的一种数据准备技术。将数据集中的列转换为相同比例的过程称为归一化。并不是每个数据集都需要为了机器学习归一化。只有当特征的范围不同时才需要这样做。
- 最小-最大值缩放（归一化）：从每列的最大值中减去最小值，并除以范围。每个新列的最小值为 0，最大值为 1。
- 标准化缩放（Standardization Scaling）：“标准化”一词指的是将变量中心化为零并将方差标准化为 1 的过程。方法是减去每个观测值的平均值并除以标准差。
- 归一化和标准化：归一化和标准化不是一回事。有趣的是，标准化要求将均值设置为零，标准差设置为一。机器学习中的归一化是将数据转换到 [0,1] 范围或任何其他将数据转换到单位尺度的过程。

EPOCH（周期）：epoch 是机器学习中的一个单位，表示学习算法已完成。数据集通常被分成批（batch）（特别是当数据量很大时）。有些人使用迭代（iteration）一词，并倾向于将通过模型的一个批数据视为迭代。

- 如果批次大小等于训练数据集的大小，那么 epoch 的数量就是迭代次数。由于实际原因，通常并非如此。许多模型创建时会有多个 epoch。数据集大小为 d、epoch 数为 e、迭代次数为 i 和批次大小为 b 之间的一般关系为 de=i。

## 8.1.4 激活函数

我们讨论了单个神经元的结构，它有一些输入。突触有一些权重，然后它将权重相加，然后应用激活函数。在第 3 步中，它将信号传递给下一个神经元（传递/不传递的决定取决于激活函数）。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_224_0.png)

激活函数的类型：我们将观察四种不同类型的激活函数。激活函数的类型更多，但这些是比较流行的。

- [1] 阈值函数（Threshold Function）：在 x 轴上，你有输入的加权和。在 y 轴上，从 0 到 1。它基本上是一种“是-否”类型的函数。
- 如果值小于 0，则阈值函数通过。
- 如果值大于或等于 0，则阈值函数通过。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_224_1.png)

- [2] Sigmoid 函数（Sigmoid Function）：它是一种用于逻辑回归的函数。
- 该函数的优点是它是平滑的（与阈值函数不同）。它是一个非常平滑的进展。因此，任何低于它的值实际上都趋于 0。
- 对于正值，它趋于 1。
- Sigmoid 函数在人工神经网络（ANN）的末层（输出层）中非常有用。特别是当你试图预测概率时。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_224_2.png)

- [3] 整流函数（Rectifier Function）：整流函数是人工神经网络中最常用的网络之一。它一直到 0（负值），然后从那里随着输入值的增加逐渐进展（正值）。我们在这一部分使用这种函数。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_225_0.png)

- [4] 双曲正切函数（Hyperbolic Tangent Function）：它与 sigmoid 函数非常相似，但这里的双曲正切函数在 0 以下运行到大约 1，并从 0 到（负值）。

在以下论文中阅读更多：你会发现为什么整流函数是是如此有价值的函数，它是如此流行。目前我们并不真的需要知道所有的事情。我们将开始越来越多地使用它们。当你对实践方面感到熟悉时，你可以参考这篇论文，然后你就能吸收这些知识，它们会非常有意义。

# 延伸阅读：

深度稀疏整流网络
![](img/0aa092657a6eb1b9f2dd65bbb79055a3_225_1.png)

由 Xavier Glorot 等人写
（注：原文为 By Xavier Glorot et al.）

（注：由于原文文本中包含大量未翻译的英文，此处已根据要求翻译了中文内容）
-
[link](https://example.org)(https://example.org)
- 这里的 process of transforming the columns in a dataset to the same scale is referred to as 归一化。
- Normalization and standardization: Normalization and standardization are not the same things. Standardization, interestingly, requires setting the mean to zero and the standard deviation to one. Normalization in machine learning is the process of transforming data into the range [0,1] or any range other transforming data onto the unit scale.

EPOCH: An epoch is a unit in machine learning and indicates the learning algorithm has completes. Datasets are usually grouped into batches (especially when the amount of data is large). Some people use the term iteration and prefer to run one batch through the model as an iteration.

- If the batch size is while training dataset then the number of epochs is number of iterations. For practical reasons, this is usually not the case. Many models are created with more than one epoch. The general relation between dataset size is d, number of epochs is e, number of iterations is i and batch size b would be de=i.

## 8.1.4 THE ACTIVATION FUNCTION

We talked about the structure of one neuron, it has some inputs coming in. Synapses got some weights then it adds up the weights and then apply the activation function. In step 3, it passes the signal to the next neuron (the decision of pass/no-pass comes from the activation function).

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_224_0.png)

Types of activation Function: We are going to look at four different types of activation functions. There are more types of activation function but these are the popular ones.

- [1] Threshold Function: On the x axis you have the weighted sum of inputs. In the y axis, goes from 0 to 1. It is basically kind of, yes-no type of function.
- If the value is less than zero then the threshold function passes on.
- If the value is more than zero or equal to zero then threshold function passes on.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_224_1.png)

- [2] Sigmoid Function: It's a function which is used in logistic regression.
- The benefit of this function is that it is smooth (unlike threshold function). It's just nice and smooth progression. So anything below it actually tends to 0.
- And it approaches 1 for +ve.
- Sigmoid function is very useful in the final layer (the output layer) of ANN. Especially when you're trying to predict probabilities.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_224_2.png)

- [3] Rectifier Function: Rectifier function is one of most used networks in artificial neural. It goes all the way to zero (-ve) and then from there gradually progresses as input value increases (+ve). We use this function in this section.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_225_0.png)

- [4] Hyperbolic Tangent Function: It's very similar to sigmoid function but here the hyperbolic tangent function goes below 0 to approximately 1 and go from 0 to (-ve).

Read more in the following paper: you find out exactly why rectifier function is such a valuable function, it's so popularly used. For now we don't really need to know all of things. We're just going to start using them more and more. And when you feel comfortable with the practical side of things then you can refer to this paper and then you will be able to soak in that knowledge and it will make much sense.

# Additional Reading:

Deep sparse rectifier networks
![](img/0aa092657a6eb1b9f2dd65bbb79055a3_225_1.png)

By Xavier Glorot et al.
[/content] (抱歉，在之前的处理中出现了逻辑重复错误，以下是为您提供干净的最终翻译结果：)

[content]
![](img/0aa092657a6eb1b9f2dd65bbb79055a3_223_0.png)

**神经元**：信号进入神经元后会发生几件事。

- A. 第一件事，也是**第一步**，是将变量的相应权重相加，即所有**输入值**的**加权和**。
- B. 其次，对这个**加权和**应用一个**激活函数**。
- 基本上，*激活函数*是一个分配给*神经元*或这*整个层*的函数，并应用于它的加权和上。
- **激活函数**决定了它是否**向下一个神经元**（或层）**传递信号**，即取决于**激活函数**，*神经元*将可以传递信号，也可以不传递信号。
- C. 这就是**第三步**中恰发生的事情。**神经元**将该**信号**传递给链下游的**下一个神经元**。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_223_1.png)

这就是你如何获得输入值和权重。在神经元中发生的是求和以及对加权和应用激活函数，然后将其传递下去，这在**整个神经网络中不断重复**，这取决于你的神经网络有多**大**、你有多少个**神经元**以及多少个**突触**。

# 笔记：

- 归一化（Normalization）是机器学习中常用的一种数据准备技术。将数据集中的列转换为相同比例的过程称为归一化。并不是每个数据集都需要为了机器学习归一化。只有当特征的范围不同时才需要这样做。
- 最小-最大值缩放（归一化）：从每列的最大值中减去最小值，并除以范围。每个新列的最小值为 0，最大值为 1。
- 标准化缩放（Standardization Scaling）：“标准化”一词指的是将变量中心化为零并将方差标准化为 1 的过程。方法是减去每个观测值的平均值并除以标准差。
- 归一化和标准化：归一化和标准化不是一回事。有趣的是，标准化要求将均值设置为零，标准差设置为一。机器学习中的归一化是将数据转换到 [0,1] 范围或任何其他将数据转换到单位尺度的过程。

EPOCH（周期）：epoch 是机器学习中的一个单位，表示学习算法已完成。数据集通常被分成批（batch）（特别是当数据量很大时）。有些人使用迭代（iteration）一词，并倾向于将通过模型的一个批数据视为迭代。

- 如果批次大小等于训练数据集的大小，那么 epoch 的数量就是迭代次数。由于实际原因，通常并非如此。许多模型创建时会有多个 epoch。数据集大小为 d、epoch 数为 e、迭代次数为 i 和批次大小为 b 之间的一般关系为 de=i。

## 8.1.4 激活函数

我们讨论了单个神经元的结构，它有一些输入进入。突触有一些权重，然后它将权重相加，然后应用激活函数。在第 3 步中，它将信号传递给下一个神经元（传递/不传递的决定取决于激活函数）。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_224_0.png)

激活函数的类型：我们将观察四种不同类型的激活函数。激活函数的类型更多，但这些是比较流行的。

- [1] 阈值函数（Threshold Function）：在 x 轴上，你有输入的加权和。在 y 轴上，从 0 到 1。它基本上是一种“是-否”类型的函数。
- 如果值小于 0，则阈值函数通过。
- 如果值大于或等于 0，则阈值函数通过。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_224_1.png)

- [2] Sigmoid 函数（Sigmoid Function）：它是一种用于逻辑回归的函数。
- 该函数的优点是它是平滑的（与阈值函数不同）。它是一个非常平滑的进展。因此，任何低于它的值实际上都趋于 0。
- 对于正值，它趋于 1。
- Sigmoid 函数在人工神经网络（ANN）的末层（输出层）中非常有用。特别是当你试图预测概率时。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_224_2.png)

- [3] 整流函数（Rectifier Function）：整流函数是人工神经网络中最常用的网络之一。它一直到 0（负值），然后从那里随着输入值的增加逐渐进展（正值）。我们在这一部分使用这种函数。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_225_0.png)

- [4] 双曲正切函数（Hyperbolic Tangent Function）：它与 sigmoid 函数非常相似，但这里的双曲正切函数在 0 以下运行到大约 1，并从 0 到（负值）。

在以下论文中阅读更多：你会发现为什么整流函数是是如此有价值的函数，它是如此流行。目前我们并不真的需要知道所有的事情。我们将开始越来越多地使用它们。当你对实践方面感到熟悉时，你可以参考这篇论文，然后你就能吸收这些知识，它们会非常有意义。

# 延伸阅读：

深度稀疏整流网络
![](img/0aa092657a6eb1b9f2dd65bbb79055a3_225_1.png)

由 Xavier Glorot 等人写
