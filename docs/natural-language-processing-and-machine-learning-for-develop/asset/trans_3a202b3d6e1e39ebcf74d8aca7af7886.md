
-   [反向误差传播](https://en.wikipedia.org/wiki/Backpropagation)从输出层开始，向左移动到输入层，涉及三个超参数。这些超参数在机器学习框架中负责“重工作”：它们计算神经网络中边缘权重的更新。

-   [损失函数](https://en.wikipedia.org/wiki/Loss_function)是多维欧几里得空间中的函数。例如，MSE [损失函数](https://en.wikipedia.org/wiki/Loss_function)是一个凸 [损失函数](https://en.wikipedia.org/wiki/Loss_function)，这意味着它像一个“碗”，因此具有全局最小值。通常，目标是最小化MSE函数以最小化成本，从而提高模型的准确率（但这并不适用于其他 [损失函数](https://en.wikipedia.org/wiki/Loss_function)）。然而，有时一个局部最小值会被认为“足够好”，而不是寻找全局最小值：你必须做出这个决定（即这不是纯粹程序化的决定）。

-   对于大型数据集，[损失函数](https://en.wikipedia.org/wiki/Loss_function)往往非常复杂，这对于在数据集中检测潜在模式是必要的。另一个 [损失函数](https://en.wikipedia.org/wiki/Loss_function) 是交叉熵函数，它涉及最大化似然函数（与MSE形成对比）。请在线搜索（如维基百科）以获取关于 [损失函数](https://en.wikipedia.org/wiki/Loss_function) 的更多详细信息。

### **优化器超参数**

一个 [优化器](https://en.wikipedia.org/wiki/Optimization_algorithm) 是在与 [损失函数](https://en.wikipedia.org/wiki/Loss_function) 一起选择的算法，其目的是在训练阶段收敛到 [损失函数](https://en.wikipedia.org/wiki/Loss_function) 的最小值（参阅上一节关于局部最小值的注释）。不同的 [优化器](https://en.wikipedia.org/wiki/Optimization_algorithm) 对训练过程中新近似值的计算方式做出不同的假设。一些 [优化器](https://en.wikipedia.org/wiki/Optimization_algorithm) 只使用最近的近似值，而其他 [优化器](https://en.wikipedia.org/wiki/Optimization_algorithm) 使用“滚动平均”，考虑多个之前的近似值。

已知的 [优化器](https://en.wikipedia.org/wiki/Optimization_algorithm) 包括 SGD、RMSprop、Adagrad、Adadelta 和 Adam。请在线搜索以了解这些 [优化器](https://en.wikipedia.org/wiki/Optimization_algorithm) 的优势和权衡。

### **学习率超参数**

[学习率](https://en.wikipedia.org/wiki/Learning_rate) 是一个小数，通常在 0.001 到 0.05 之间，它影响在训练过程中计算下一个近似值时加到当前近似值的数值大小。[学习率](https://en.wikipedia.org/wiki/Learning_rate) 具有类似“节流”效果：如果值过大，新近似值可能会“超调”最优点；如果值过小，训练时间会显著增加。可以类比于你在客机上，距离机场 100 英里时，飞机速度会随着接近机场而减慢，这对应于在神经网络中降低 [学习率](https://en.wikipedia.org/wiki/Learning_rate)。

### **丢弃率超参数**

[丢弃率](https://en.wikipedia.org/wiki/Dropout_(machine_learning)) 是第八个超参数，取值范围是 0 到 1，通常在 0.2 到 0.5 之间。将该小数乘以 100，即可确定每次前向传播中随机忽略的神经元百分比。例如，若丢弃率为 0.2，则每次前向传播中会随机选择并忽略 20% 的神经元。每当神经网络处理新数据点时，会重新随机选择一组神经元。注意，神经元并未从网络中删除：它们仍然存在，在前向传播中忽略它们的效果是“稀疏”神经网络。在 TF 2 中，[Keras tf.keras.layers.Dropout](https://www.tensorflow.org/api_docs/python/tf/keras/layers/Dropout) 类负责实现神经网络的“稀疏”操作。

除了上述超参数，你还可以指定其他超参数，但它们是可选的，不是理解人工神经网络（ANNs）所必需的。

### **什么是反向误差传播？**

神经网络通常以从左到右的方式绘制，最左侧是输入层。每层的输出成为下一层的输入。前向传播（forward propagation）指向输入层供给数值，并向前通过隐藏层到达输出层。输出层包含前向传播的结果（估计的数值）。

关键点：[反向误差传播](https://en.wikipedia.org/wiki/Backpropagation) 涉及计算用于更新神经网络边缘权重的数值。更新过程从输出层开始，并以从右到左的方向进行，以更新相邻层之间的边缘权重。此过程通过减小输出层估计值与真实值之间的损失（在监督学习中）来训练神经网络。该过程会对数据集的训练部分中每个数据点重复执行。

前一段未解释 [损失函数](https://en.wikipedia.org/wiki/Loss_function) 是什么或如何选择：因为 [损失函数](https://en.wikipedia.org/wiki/Loss_function)、[优化器](https://en.wikipedia.org/wiki/Optimization_algorithm) 和 [学习率](https://en.wikipedia.org/wiki/Learning_rate) 是前文已讨论的超参数。然而，两个常用的 [损失函数](https://en.wikipedia.org/wiki/Loss_function) 是 MSE 和交叉熵；常用的 [优化器](https://en.wikipedia.org/wiki/Optimization_algorithm) 是 Adam 优化器（以及 SGD、RMSprop 和其他）；常见的 [学习率](https://en.wikipedia.org/wiki/Learning_rate) 值为 0.01。

以上是神经网络的理论基础及各种超参数的目的。下一节讨论逻辑回归，尽管其名称如此，它仍是机器学习中广为人知的分类算法。

### **什么是逻辑回归？**

尽管名称如此，逻辑回归是一个二分类的分类器和线性模型。逻辑回归使用多个自变量，并利用 sigmoid 函数计算概率。它本质上是将 sigmoid 激活函数应用于线性回归，从而实现二分类。

逻辑回归在多个领域都有用，包括机器学习、医学领域以及社会科学。它可用于根据患者观察到的特征预测其患特定疾病的风险。其他使用逻辑回归的领域包括工程、营销和经济学。

逻辑回归是二项式（两种可能结果），而多类逻辑回归（三种或更多结果）将逻辑回归推广至多类问题。例如，假设数据集包含属于类 A 或类 B 的数据。如果你给出一个新数据点，逻辑回归预测该点属于类 A 还是类 B。相比之下，线性回归预测一个数值，例如下一日的股票价格。

### **设定阈值**

[阈值](https://en.wikipedia.org/wiki/Threshold) 是一个数值，用于判断数据点属于类 A 还是类 B。例如，通过/不通过的阈值可能是 0.70。加州驾驶理论考试通过的阈值为 0.85。

另一个例子：如果 p = 0.5 是“切断”概率，则我们可以将概率 > 0.5 的数据点分配为类 A，将概率 <= 0.5 的数据点分配为类 B。由于只有两类，我们就拥有了一个分类器。

类似但略有不同的场景是抛掷一枚公平的硬币。我们知道正面（我们称之为类 A）的概率为 50%，反面（我们称之为类 B）的概率也为 50%。如果我们有一个包含标记结果的数据集，那么我们预期大约 50% 的数据点属于类 A，50% 属于类 B。

