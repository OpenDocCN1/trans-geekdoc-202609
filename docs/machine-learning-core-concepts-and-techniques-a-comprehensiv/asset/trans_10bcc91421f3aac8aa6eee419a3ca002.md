

数据集随后被压缩成树状结构（`FP-tree`），其中每个节点代表交易中的一个商品，而路径则代表一起购买的商品集合。交易中经常共同出现的商品在树中共享分支。

## Mining the FP-Tree

一旦构建了 `FP-tree`，该算法就会递归地从树中挖掘频繁项集，而无需生成候选项集。

从最不频繁的项目开始，该算法探索条件 `FP-trees`（仅包含特定项目的交易的原始树的子集）以提取频繁模式。

### Example

考虑一个超市场景，其目标是找到“面包和黄油”或“牛奶和鸡蛋”之类的频繁项集。`FP-Growth` 会首先基于所有交易构建一个 `FP-tree`，其中“牛奶”和“面包”等频繁项目出现在根部附近，并与其它频繁项目共享分支。一旦树构建完成，算法就可以高效地探索所有频繁项集，而无需反复扫描数据集。

### Advantages of FP-Growth

* Efficiency: `FP-Growth` 比 `Apriori` 快得多，尤其是在大型数据集上，因为它避免了昂贵的候选项集生成并减少了数据库扫描次数。
* Compact Representation: 通过使用 `FP-tree`，`FP-Growth` 将数据集压缩成一个更小的结构，使其更容易处理大量数据。
* Scalability: `FP-Growth` 可扩展，可以处理具有大量交易和项目的庞大而复杂的数据集。

### Disadvantages

* Memory Usage: 构建 `FP-tree` 可能需要大量内存，尤其是在非常大的数据集或具有高维度的数据集（许多唯一项目）上。
* Complexity: 虽然 `FP-Growth` 比 `Apriori` 更高效，但其实现更复杂，并且对于某些数据集构建 `FP-tree` 可能并不简单。

### Real-World Application

`FP-Growth` 在市场篮子分析中被广泛使用，零售商寻求了解客户的购买习惯。例如，它可用于发现购买“尿布”的客户通常也会购买“婴儿湿巾”。这一见解可以带来更好的产品摆放或有针对性的促销。它还可用于推荐系统，例如根据过去的购买或经常一起购买的商品来推荐产品。

***

### Comparison: Apriori vs. FP-Growth

| Feature | Apriori | FP-Growth |
| --- | --- | --- |
| Approach | Generates candidate itemset and tests them iteratively | Uses a compressed FP-tree structure to mine frequent itemset directly |
| Efficiency | Slower due to repeated database scans | Faster due to compact tree structure and fewer database scans |
| Memory Usage | Generally lower memory usage | Can be memory-intensive if the FP-tree is large |
| Simplicity | Simple to implement | More complex to implement |
| Performance on Large Datasets | Performs poorly on large datasets | Performs well on large datasets |

***

### Conclusion

无监督学习技术如聚类、降维和关联规则学习是在没有显式标签的情况下发现数据中模式和见解的基本工具。每种技术都有不同的用途，从在数据中寻找组（聚类）、减少复杂性（降维）到识别变量之间的关系（关联规则学习）。这些方法在营销到生物学等各行各业和领域中被广泛使用，提供有价值的见解，可推动决策和战略。

# Chapter 8: Neural Networks and Deep Learning

神经网络和深度学习是现代人工智能（AI）和机器学习的核心。它们受人类大脑的结构和功能启发，由相互连接的节点（或神经元）层组成，这些节点处理输入数据以生成有意义的输出。在本章中，我们将探讨神经网络的基础概念，包括感知器和多层感知器（MLPs）、反向传播、卷积神经网络（CNNs）以及循环神经网络（RNNs）和长短期记忆（LSTM）网络。每种网络在解决各种现实世界任务中都发挥着关键作用，从图像识别到自然语言处理。

***

## 1. Perceptron’s and Multi-layer Perceptron’s (MLPs)

### Perceptron’s

感知器是最简单的神经网络类型，由单个神经元组成。它接收一组输入，对这些输入应用权重，求和，然后将结果通过激活函数以产生输出。感知器主要用于二元分类问题，其目标是将输入数据分配为两个可能的标签之一。

感知器组件：
1. Inputs: 感知器接收多个输入特征，`x1,x2,…,xn` `x_1, x_2, \dots, x_n` `x1​,x2​,…,xn​`。
2. Weights: 每个输入都有一个相关权重 `w1,w2,…,wn` `w_1, w_2, \dots, w_n` `w1​,w2​,…,wn​`，它决定输入的重要性。
3. Bias: 添加一个偏置项以移动激活函数，使其更灵活。
4. Activation Function: 感知器将输入的加权和通过激活函数（如阶跃函数）传递以产生二元输出。

Example: 考虑一个简单的感知器，用于将电子邮件分类为垃圾邮件或非垃圾邮件。输入可以是诸如特定关键词（“free”、“offer”）的存在或电子邮件长度等特征。感知器使用这些特征来决定电子邮件是否应被分类为垃圾邮件。

然而，感知器存在局限性，尤其是在处理线性不可分数据（如 XOR 问题）时。这就是多层感知器（MLPs）发挥作用的地方。

### Multi-layer Perceptron’s (MLPs)

MLPs 是一种前馈神经网络，由多个神经元层组成：输入层、一个或多个隐藏层和输出层。MLPs 通过引入非线性和允许更复杂的决策边界克服了单层感知器的局限性。

Architecture:
* Input Layer: 接收输入数据的第一层。
* Hidden Layers: 这些层包含应用权重和激活函数以转换输入的神经元。MLPs 通常使用 `RLU`（修正线性单元）激活函数来引入非线性。
* Output Layer: 最终层产生网络的输出。对于二元分类，这可以是具有 sigmoid 激活函数的单个神经元；对于多类分类，通常使用 `SoftMax`。

Example: `MLP` 可用于根据年龄、体重和血糖水平等特征预测患者是否患有糖尿病。输入层接收这些特征，隐藏层学习数据中的复杂模式，输出层预测糖尿病的可能性。

MLPs 的优点：
* 可以处理非线性关系。
* 适用于回归和分类问题。

缺点：
* 需要大量数据集和计算能力。
* 如果未正确正则化（例如使用 dropout 或 L2 正则化），容易过拟合。

***

## 2. Backpropagation

反向传播是神经网络学习的核心。它是一种用于根据预测输出与实际输出之间的误差更新网络中神经元权重的算法。目标是最小化该误差，通常通过损失函数衡量（例如回归的均方误差或分类的交叉熵损失）。

### How Backpropagation Works:

1. Forward Pass:
   * 输入数据逐层通过网络，每个神经元应用其权重和激活函数以产生输出。
2. Loss Calculation:

