

1. **数据准备：搭建“课堂”**

标记的数据集就像是我们模型的教科书和模拟考试。我们将这个数据集分为两个关键部分。[Figure 3-5](#c03.xhtml#c03-fig-0005) 直观地展示了训练数据和测试数据之间的划分。

* **训练集：** 这是模型用来学习的主要“学习材料”。它是数据中最大的部分。

* **测试集：** 这是一个保留下来的“期末考试”，用于评估模型的学习泛化得如何。它包含模型在训练期间*未见过*的数据。这对于确保模型不仅仅是死记硬背训练数据至关重要（稍后将详细介绍）。

**示例：** 对于我们的客户支持工单分类，我们可能有 10,000 个标记的工单。我们可能会使用 8,000 个进行训练，并保留 2,000 个用于测试。

![Figure 3-5: An illustration of how a labeled dataset is split into a larger training set for the model to learn from and a smaller testing set to evaluate its performance on unseen data. (Source: Kaggle).](images/c03f005.png)

**Figure 3-5:** An illustration of how a labeled dataset is split into a larger training set for the model to learn from and a smaller testing set to evaluate its performance on unseen data. (*Source*: Kaggle).

2. **模型选择：选择合适的“学习风格”**

就像不同的学生通过不同的方法（视觉、听觉、动觉）学习效果最好一样，不同的机器学习算法也更适合不同类型的数据和任务。算法的选择取决于我们是预测连续值（例如客户的生命周期价值）还是类别值（例如我们的工单类型）。

**常见算法（以及产品经理可能遇到它们的场景）：**

* **线性回归：** 用于预测*连续*值。*例如*：根据房屋的大小、位置和卧室数量预测房价。或者，预测客户在明年会花费多少。

* **逻辑回归：** 用于预测*类别*值（即某物属于哪个类别）。*例如*：预测客户是否会点击广告（是/否）或交易是否欺诈（欺诈/非欺诈）。我们的客户支持工单分类就是一个很好的例子。

* **决策树：** 这些创建一个类似树的决策结构来对数据进行分类。*例如*：一个帮助确定是否应批准贷款申请的流程图。它们通常易于解释。[Figure 3-6](#c03.xhtml#c03-fig-0006) 展示了决策树模型如何通过一系列基于特征的问题分支来得出预测。

* **神经网络（包括深度学习）：** 这些是更复杂的模型，受人类大脑启发，可以学习非常复杂的模式。*例如*：图像识别、自然语言处理以及涉及复杂非结构化数据的其他任务。

* **随机森林：** 这些结合多个决策树以提高准确性并减少过拟合。*例如*：通过询问一组专家而不是仅依赖一位专家来做出决策。用于客户流失预测和欺诈检测等任务。

* **梯度提升：** 一种强大的技术，它按顺序构建模型，每个新模型纠正前一个模型犯下的错误。常用于获胜的 Kaggle 竞赛以及信用评分或个性化推荐等现实世界应用。

![Figure 3-6: An example of how decision trees can solve Machine Learning problems.](images/c03f006.png)

**Figure 3-6:** An example of how decision trees can solve Machine Learning problems.

3. **模型训练：“学习”过程**

模型训练过程涉及几个关键组件，它们共同作用，帮助算法从标记数据中学习并随时间改进其预测。

这就是奇迹发生的地方。算法接收训练数据，并迭代调整其内部参数（模型的“旋钮和旋钮”），以最小化其预测与实际标签之间的误差。

* **损失函数：** 这是一个数学函数，用于量化模型预测有多“错误”。它就像一个记分员，告诉模型它做得如何。不同的算法使用不同的损失函数。

* **优化算法：** 这是模型用来调整其内部参数以*最小化*损失函数的过程。可以将其视为模型学习和提高性能的策略。一种常见的优化算法是*梯度下降*，它就像滚球下山以找到最低点（最小损失）。梯度下降的一个关键设置是学习率，你可以将其视为模型在尝试最小化误差时所采取的步长。学习率的选择对训练效率有显著影响，如[Figure 3-7](#c03.xhtml#c03-fig-0007)所示。如果速率太低，模型学习得非常慢；如果速率太高，它可能会错过最优点并无法找到最佳解决方案。

![Figure 3-7: An illustration of gradient descent and the impact of the learning rate. The goal is to find the “Just right” learning rate that allows the model to find the point of minimum error efficiently, without taking too many small steps (“Too low”) or overshooting the target (“Too high”).](images/c03f007.png)

**Figure 3-7:** An illustration of gradient descent and the impact of the learning rate. The goal is to find the “Just right” learning rate that allows the model to find the point of minimum error efficiently, without taking too many small steps (“Too low”) or overshooting the target (“Too high”).

* **示例：** 在我们的客户支持工单场景中，模型最初可能会预测包含“密码”一词的工单是“账单问题”。如果正确标签是“技术问题”，损失函数将指示错误。然后优化算法会稍微调整模型的参数，使其*更*有可能在未来将类似的工单分类为“技术问题”。

4. **模型评估：“期末考试”**

模型训练完成后，我们需要查看它在未见数据上的表现。这就是测试集的作用。作为产品经理，理解关键评估指标对于解读模型的“期末考试”分数并决定它是否准备好投入现实世界非常重要。

如何衡量“正确”与“错误”预测之间的关系，最好通过*混淆矩阵*来理解，它为每个结果（真阳性、假阳性、假阴性、真阴性）提供原始计数。从这些计数中，我们得出更有洞察力的指标。

下表详细说明了分类问题中最重要的指标。

| METRIC || KEY QUESTION IT ANSWERS || PM IMPLICATION AND WHEN TO PRIORITIZE |
| --- | --- | --- |
| Accuracy || “Overall, what percentage of predictions did the model get right?” || A good high-level summary, but it can be misleading if your data is imbalanced (e.g., 99% of transactions are not fraud). |
| Precision || “Of all the times the model predicted 'positive,' how often was it correct?” || Prioritize this when the cost of a **False Positive** is high. You want to avoid bothering users or creating unnecessary work (e.g., flagging a legitimate email as spam). |
| Recall || “Of all the actual 'positive' cases, how many did the model find?” || Prioritize this when the cost of a **False Negative** is high. You want to avoid missing important events (e.g., failing to detect a fraudulent transaction or a medical disease). |

