
31. 将剪贴板上的名称替换为高亮显示的名称，点击运行图标执行代码。

32. 代码运行成功后，查看 `结果`。

![image](img/f0279-01.jpg)

会创建一个输出评分表。

33. 点击 `输出数据` 选项卡，查看评分表及其中的分数。

![image](img/f0279-02.jpg)

34. 再次进入左上角的应用程序菜单（![image](img/Line.jpg)），点击 `构建模型` 返回到模型工作室。

![image](img/EndOfDemo.jpg)

## 梯度提升决策树与其他基于树模型的比较

梯度提升算法类似于标准提升，但在每次迭代时，目标是前一个决策树模型的残差。

每次迭代计算树的准确率。

后续样本会根据之前的不准确性进行调整。

模型是（通常）简单树的加权线性组合。

核心思想是构建新的基学习器，使其与整个集成的负梯度函数的负梯度最大化相关。

梯度提升可以表示为：

**梯度提升 = 梯度下降 + 提升**

下面的表格 8.1（第 8 章）是三种树基模型的快速比较。每种模型都有优缺点。总体而言，集成学习非常强大，没有哪种模型在所有情况下都最佳。

## 调优梯度提升模型

你需要调整多个参数，以便正确地训练你的梯度提升模型。

**Table 8.1: Comparison of Tree-Based Models**

| Models | Advantages | Disadvantages |
| --- | --- | --- |
| Decision Tree | Easy to understand, interpret, and implement, extremely fast to train | Highly unstable, not powerful enough to handle complex data |
| Forest | More stable and robust because of "wisdom of the crowd" approach, fast to train, easier to tune, highly generalizable model, less prone to overfit | Very difficult in model interpretability and explainability |
| Gradient Boosting | High performing, effectively capture complex nonlinear function dependencies, solves interval target distributions other than normal | Slow to train due to sequential nature, a small change in the feature set or training set can create drastic changes in the model, not easy to understand predictions |

**Figure 8.18: Tree-Splitting Options for Tuning a Gradient Boosting Model**

![image](img/f0281-01.jpg)

There are a few tree-specific parameters that affect each individual tree in the model and are represented in Figure 8.18. This includes tree-splitting options like maximum number of branches, maximum depth, minimum leaf size, number of inputs to consider per split, and so on. You are already familiar with all of them. (See the discussion in the previous chapters.)

For example, a larger number of inputs to consider per split can lead to overfitting. Few other options are related to tree complexity, which controls whether interactions are fitted: a tree complexity of one (single decision stump; two terminal nodes) fits an additive model, a tree complexity of two fits a model with up to two-way interactions, and so on.

The sequential model-fitting process builds on trees fitted previously, and increasingly focuses on the hardest observations to predict. Accordingly, there are several boosting parameters that affect the boosting operation in a gradient boosting model such as the number of trees, the learning rate, the subsample rate, L1 and L2 regularizations, and so on. They are represented in Figure 8.19.

Our primary focus of discussion in this section revolves around the boosting hyperparameters.

**Figure 8.19: Boosting Options for Tuning a Gradient Boosting Model**

![image](img/f0281-02.jpg)

### Tuning Parameters Manually

Hyperparameter tuning is choosing a set of optimal hyperparameters for a learning algorithm. A hyperparameter is a model argument whose value is set before the learning process begins. Experienced modelers prefer to tune these hyperparameters manually. Another option is to use the SAS Viya autotuning feature that is discussed later.

#### Number of Trees

The number of trees represents the number of sequential trees to be modeled in gradient boosting. Most implementations of gradient boosting are configured by default with a relatively moderate number of trees, such as hundreds or thousands, although this number is data dependent. Usually, the higher the number of trees, the better to learn the data. However, adding a lot of trees can slow down the training process considerably.

Gradient boosting is fairly robust at a higher number of trees, but it can still overfit at a point. Recall that each new tree attempts to model and correct for the errors made by the sequence of previous trees, and therefore, the model reaches a point of diminishing returns. Hence, this should be tuned using a validation data for a particular learning rate (discussed ahead). In order to find the optimal number of trees, you can also use early stopping.

Parameter tuning of the number of trees in a forest is summarized in Figure 8.20.

#### Learning Rate

The learning rate scales the contribution of each tree. Gradient boosting starts with an initial estimate, which is updated using the output of each subsequent tree. The learning parameter controls the magnitude of this change in the estimates.

Lower values of the learning rate generally make the model robust to the specific characteristics of the tree and thus allow it to generalize well. A low learning rate would require more trees to model all the relations. A low learning rate is more precise, but calculating the gradient is time-consuming, so it is computationally expensive.

**Figure 8.20: Tuning the Number of Trees**

![image](img/f0282-01.jpg)

**Figure 8.21: Tuning the Learning Rate**

![image](img/f0283-01.jpg)

**Figure 8.22: A Good Learning Rate!**

![image](img/f0283-02.jpg)

Learning rate tuning in a gradient boosting model is summarized in Figure 8.21. Figure 8.22 further explains the trade-off between setting a high and low learning rate.

Setting the learning rate too high yields great progress in decreasing the error function in the first few iterations, but at a risk of diverging later in the training process. On the other hand, setting the learning rate too small can result in very long training times. A "good" learning rate is a balance between the two and is problem specific.

#### Trade-off Between Learning Rate and Number of Trees

By now you are aware that the learning rate shrinks the contribution of each tree as it is added to the model. Decreasing (slowing) the learning rate increases the number of trees required, and in general a smaller learning rate (and larger number of trees) is therefore preferred. The usual approach is to estimate the optimal number of trees and the learning rate with an independent test set or with cross validation, using reduction in the loss function as the measure of success. The trade-off between learning rate and number of trees is illustrated in Figure 8.23.

**Figure 8.23: Learning Rate Versus Number of Trees**

![image](img/f0284-01.jpg)

Friedman (1999) commented on the trade-off between the number of trees (M) and the learning rate (λ):

> "The λ‑M trade-off is clearly evident; smaller values of l give rise to larger optimal M-values. They also provide higher accuracy, with a diminishing return for λ < 0.125. The misclassification error rate is very flat for M > 200, so that optimal M-values for it are unstable. … the qualitative nature of these results is fairly universal."
>
> – Friedman 1999

He suggests to first set a large value for the number of trees, and then tune the shrinkage parameter to achieve the best results. Studies in the paper preferred a shrinkage value of 0.1, a number of trees in the range 100 to 500, and the number of terminal nodes in a tree between 2 and 8.

#### How does the shrinkage (learning rate) affect overfitting?

Presented in Figure 8.24 are the learning error curves for gradient boosting models with different shrinkage (λ) parameters using the sinc(x) data referred previously. The left graph shows the performance on the training data, whereas the right graph shows the performance on the validation data.

Observe that the training set error is substantially dropping, but the speed of this improvement heavily depends on the shrinkage parameter λ. The validation-error hyperparameter M, corresponding to the error minima of each of the models, is highlighted with circles. You can see that increasing the shrinkage leads to both finding a better hyperparameter M minima and to improving the generalization of the model. The latter corresponds to the fact that shrunk models have a flatter plateau beyond their error minima, and it takes them many more iterations to initiate overfitting. Yet, it also means that these models naturally take longer to learn. Hence, a high learning rate commonly results in overfitting (Natekin and Knoll 2013).

**Figure 8.24: Effect of Learning Rate on Overfitting**

![image](img/f0285-01.jpg)

**Image source:**

- Natekin and Knoll (2013)的梯度提升机器，一个综述。Front. Neurorobot. 7:21. doi: 10.3389/fnbot.2013.00021

#### Subsample Rate

`Subsample rate` 设置用于通过随机抽样对拟合单个基学习者所使用的样本分数。Friedman (1999) 发现几乎所有子抽样百分比都优于所谓的确定性提升（子抽样率=1）：

> "… 最佳采样分数 … 大约是 40%（f=0.4） … 然而，仅在每次迭代中对 30% 或甚至 20% 的数据进行抽样，就会相对于不抽样数据带来显著改进，相应的计算速度加快 3 倍和 5 倍。"
>
> – Friedman 1999

- 当数据量（以数据点 N 的数量）不在实际考虑范围内时，将默认值设置为 0.5 会给出合理的结果。如果对最佳子抽样率感兴趣，可以通过比较不同参数值下的预测性能来估计它。
- 较小的子抽样率通常会产生更多样化的树木，从而形成更强健且更通用的集成模型。但也应考虑减小样本量对模型估计的影响。如果子抽样率过低，可能会因自由度不足而导致模型拟合不佳。

**Figure 8.25: 调整子抽样率**

![image](img/f0286-01.jpg)

总体而言，用于拟合基学习者的数据越多，估计会更准确，前提是使用了足够的数据。因此，当有大量数据可用时，可能需要在每个基学习者使用的观测数量与其准确性提升之间进行权衡。

有时，使用更多基学习者、每个使用较小的子抽样率来达到所需准确度，可能比使用较少但更精心拟合的基学习者（子抽样率较高）更高效。

梯度提升的子抽样率调参总结在 Figure 8.25。

#### L1 和 L2 正则化

衰减参数控制惩罚项的相对重要性。惩罚项过大会导致模型欠拟合数据。

两个正则化项对权重的影响不同：`L2` 正则化鼓励权重较小，而 `L1` 正则化鼓励稀疏性，即使权重趋于 0。这在回归模型中有帮助，因为需要进行特征选择；但在决策树中，特征在树构建时已被选择，将其权重置 0 可能并无帮助。因此，可以设置高 `L2` 与低（或 0）`L1`。`L1` 正则化可视为对不具预测性特征更具攻击性，但也可能考虑同时使用两者：一些 `L1` 用于惩罚不具预测性特征，`L2` 用于进一步惩罚大叶子得分而不至于过于严苛。

梯度提升的 `L1` 和 `L2` 正则化调参总结在 Figure 8.26。

**Figure 8.26: 调整 L1 和 L2 正则化**

![image](img/f0287-01.jpg)

### 自动调参 (Autotuning)

自动调参指定是否对梯度提升的任何参数进行自动调参。自动调参会自动选择超参数的最优值。你可以决定对哪些超参数进行调参。Figure 8.27 列出了可自动调参的梯度提升超参数。

如果选择 **Perform Autotuning**，则可用的选项如下：

- **L1 正则化**：指定是否对 `L1` 正则化进行自动调参。
- **L2 正则化**：指定是否对 `L2` 正则化进行自动调参。
- **Learning Rate**：指定是否对学习率进行自动调参。
- **Maximum Depth**：指定是否对最大树深度（即节点生成代数）进行自动调参。
- **Minimum Leaf Size**：指定是否对最小叶子大小进行自动调参。

**Figure 8.27: 梯度提升的可自动调参数**

![image](img/f0287-02.jpg)

- **Interval Bins 数量**：指定是否对区间桶的数量进行自动调参。
- **Inputs per Split 数量**：指定是否对每次分割的输入数量进行自动调参。
- **Number of Trees**：指定是否对增强序列中的树木数量进行自动调参。

> 当启用早停止且存在验证分区时，若选中 **Number of Trees**，则不会进行自动调参。

![image](img/Demo.jpg) **Demo 8.2: 修改并自动调参梯度提升模型**

在这次演示中，你将尝试改进之前创建的默认梯度提升模型，通过调节特定参数。你将继续在保险 _part 数据集上操作，并尝试 **Gradient Boosting** 节点中的一些选项。

1. 确保在 Model Studio 中打开 **Insurance_ClassTree** 项目，并在 **GradBoost** pipeline 上工作。

2. 右键单击 **Data** 节点，选择 **Add child node** ![image](img/Arrow.jpg) **Supervised Learning** ![image](img/Arrow.jpg) **Gradient Boosting**。将此 **Gradient Boosting** 节点重命名为 **GB Tuned**。你的管道应如下所示：

   ![image](img/f0289-01.jpg)

3. 按照以下方式修改一些增强选项：将 **Number of trees** 从 100 改为 25，**Learning rate** 从 0.1 改为 0.3，**Subsample rate** 从 0.5 改为 1。

   ![image](img/f0289-02.jpg)

   目标是使用更少的树木和更大的步长，使所有树都使用全部数据，这正好是确定性梯度提升模型的特点。

4. 展开 **Tree-splitting Options**，将 **Maximum depth** 从 4 改为 6，**Number of interval bins** 从 50 改为 200。

   ![image](img/f0289-03.jpg)

5. 使用滑块关闭 **Perform Early Stopping**。

   ![image](img/f0290-01.jpg)

   考虑到树木数量很少，这也是合理的。

6. 点击 **Run Pipeline** 按钮。

7. 打开 **GB Tuned** 节点的结果，最大化 **Error Plot**。将 **View Chart** 切换为 **Misclassification Rate**。

   ![image](img/f0290-02.jpg)

   随着每个决策树的增加，误分类率在下降。因此，你可以尝试稍微增加树木的数量。

8. 关闭 **GB Tuned** 节点的结果。

9. 打开 **Model Comparison** 节点的结果。

   ![image](img/f0290-03.jpg)

   两个模型性能相当。然而，**GB Default** 模型的 Youden 统计量（KS）略高于 **GB Tuned** 模型。可以进一步观察其他拟合指标，如 ROC、lift、ASE 等。使用较少但更深的树木并利用全部数据似乎是一个有希望的选择。

你可以进一步修改属性并搜索更高的性能收益。不过，我们将使用 SAS Viya 中的自动调参功能。

10. 右键单击“数据”节点并选择“添加子节点” ![image](img/Arrow.jpg) 监督学习 ![image](img/Arrow.jpg) 梯度提升。将此“梯度提升”节点重命名为“自动调制 GB”。您的管道应如下所示。

![image](img/f0291-01.jpg)

11. 展开“自动调制”属性，并使用滑块按钮将其设置为“On”。

![image](img/f0291-02.jpg)

请注意，`L1` 和 `L2` 正则化、学习率、最大深度、最小叶子大小、区间桶数、每次分割的输入数、树的数量以及抽样率均可自动调制。默认情况下，除最小叶子大小外，其余均设置为“On”。您可以展开每个项并更改其自动调制属性。但目前无需进行任何更改。

12. 单击“运行管道”按钮。

![image](img/f0292-01.jpg)

自动调制会生成一个包含 81 棵树的梯度提升模型，远多于手动调制的模型（25 棵树）。树的数量由早期停止准则决定。请注意，已启用了早期停止，因此即使在自动调制窗口中选择了树的数量，也不会进行树的自动调制。

13. 最小化错误图。观察其他超参数的最佳值会很有趣。

14. 关注“最佳自动调制配置”表格。

![image](img/f0292-02.jpg)

自动调制的最佳配置显示的参数值如下：默认采用遗传算法作为自动调制搜索方法。该最佳配置建议采用 17 个输入进行每次分割的考虑，采用随机（非确定性）梯度提升模型，抽样率为 83%，学习率为 0.1031，`L1` 正则化为 7.6401，`L2` 正则化为 1.7069。在多次迭代的搜索过程中，该配置的 K-S 值为 0.4866。

15. 关闭“GB 自动调制”节点的结果窗口。

16. 打开“模型比较”节点的结果窗口。

![image](img/f0293-01.jpg)

有趣的是，这三个模型在可调参数方面差异很大，但它们的性能并没有相差甚远。自动调制的梯度提升模型在几乎所有性能指标（包括 K-S（Youden）和 MISC）上均表现出色。

![image](img/f0293-02.jpg)

自动调制的梯度提升模型的树数少于默认模型，但多于手动训练的模型。抽样率高于默认模型，而手动训练模型未应用任何抽样。在每次分割时，考虑的输入数量很小。

所有三个梯度提升模型的最小叶子大小均较小。较小的叶子通常更容易捕获训练数据中的噪声，这一属性与最大深度直接相关。不过，您可以尝试多种叶子大小或自动调制，以找到最适合您用例的设置。

因此，没有一种单一的配方能够保证梯度提升模型既准确又高效。它高度依赖于数据，实验才是关键！

17. 关闭“模型比较”节点的结果窗口。

![image](img/EndOfDemo.jpg)

## Quiz

1. 梯度提升模型算法的第一步是什么？

   a. 为前一棵树的残差拟合，并最小化损失函数。
   b. 创建一个基线树。
   c. 重复多次拟合若干棵树，次数固定。
   d. 聚合一系列树，构建一个单一函数用于预测新观测的目标值。

2. 如果目标是名义型且有三个类别，且您对梯度提升进行了 100 次迭代（树的数量=100），则会创建多少棵树？

   a. 100
   b. 200
   c. 300
   d. 400

3. 提升方法比单棵决策树更不易过拟合，如果一棵决策树能够较好地拟合数据，则提升方法通常能够进一步提升拟合效果。

   a. True
   b. False

4. 在 Gradient Boosting 节点中，“Perform Early Stopping”属性指定是否在模型开始过拟合时停止训练。当连续 N 次迭代的相对误差（Stagnation）低于阈值（Tolerance）时，训练停止。如果没有验证数据分割，则无法使用早期停止。

   a. True
   b. False

5. 下列哪项陈述是 FALSE 的？

   a. 在 SAS Viya 中，提升涉及对带有放回抽样的随机数据子集进行拟合。
   b. 提升机可适用于决策树之外的任何预测模型。
   c. 梯度提升算法本质上是决策树的加权线性组合。
   d. 以上都不是

6. 请查看下面两张使用相同训练数据（包含原始特征）的梯度提升错误图，分别使用不同学习率。

   ![image](img/f0295-01.jpg)

   下列哪些陈述是 TRUE？（多选）

   a. 完全相反（先增后减）的日志损失模式不可能出现。
   b. 最好使用验证数据来选择合适的模型。
   c. 降低学习率通常是一个良好的起点。
   d. 进行特征工程后再构建梯度提升模型是一个好主意。

7. 对于下列超参数，哪些的更高值更好？

   a. 最大深度
   b. 每次分割的输入数
   c. 最小叶子大小
   d. 树的数量
   e. 超参数的最优值是问题特定的

8. 随机梯度提升与普通梯度提升在下列哪些方面不同？

   a. 为聚合使用的抽样数据不同。
   b. 每次迭代都使用相同的训练数据。
   c. 在每次迭代中，随机抽取一份训练数据子集用于拟合基学习器并计算当前迭代的模型更新。
   d. 以上都不是

**Answers**

| 1. b | 2. c | 3. True | 4. True | 5. a | 6. b, c, and d | 7. e | 8. c |

---

考虑一种情况，你拥有有限量的目标人群标记数据。然而，你拥有来自相似人群或旧领域的大量标记数据，如 `Figure 9.2` (`#Chapter09.xhtml#ch09fig02`) 所示。显然，输入和目标定义在两组数据中是相同的。

转移学习通过添加辅助数据来增强训练数据，并尝试降低那些与原始训练数据不具代表性的观测的影响。原始训练数据通常来自目标人群，从而难以获取。

在辅助人群中的一些观测与目标人群相似，因此可以用于训练。但那些与目标人群不同的观测则与建模无关，因此需要识别它们并减少其影响。

为了简化，你可以将与目标人群相似的辅助观测称为“朋友”，将其他辅助观测称为“外星人”。`Figure 9.3` (`#Chapter09.xhtml#ch09fig03`) 将它们表现为朋友和外星人。

梯度提升（Gradient boosting）试图识别并降低外星人的影响。一部分原始训练数据被保留为测试数据，用于公正评估。

**Figure 9.2: Transfer Learning**

![image](img/f0298-01.jpg)

**Figure 9.3: Friends and Aliens**

![image](img/f0298-02.jpg)

**Figure 9.4: Identify and Down-Weight Aliens**

![image](img/f0299-01.jpg)

## Transfer Learning Using the GRADBOOST Procedure

`PROC GRADBOOST` 试图识别并降低外星人的影响。`TRANSFERLEARN` 语句允许你使用辅助数据（添加到训练数据中）来训练梯度提升模型。为防止模型过度偏向辅助数据，`GRADBOOST` 过程会对与训练数据不相似的辅助观测进行下权重。

```
PROC GRADBOOST < options >;
CROSSVALIDATION < options >;
ID variables;
INPUT variables< / options >;
OUTPUT OUT=CAS-libref.data-table< option>;
PARTITION partition-option;
TARGET variable< / LEVEL=NOMINAL | INTERVAL >;
TRANSFERLEARN variable< / options >;
```

The `PROC GRADBOOST` statement invokes the procedure.

`CROSSVALIDATION` 语句执行 k 折交叉验证，以求得平均估计验证误差。如果指定了 `AUTOTUNE` 语句或 `PARTITION` 语句，则不能指定此语句。

`ID` 语句列出一个或多个变量，这些变量将从输入数据表复制到由 `OUT=` 选项指定的输出数据表，以及 `SAVESTATE` 语句中的 `RSTORE=` 选项指定的数据表。

`INPUT` 语句命名输入变量，这些变量具有共同选项。可以多次指定 `INPUT` 语句。

`OUTPUT` 语句创建一个输出数据表，包含 `PROC GRADBOOST` 运行的结果。

`PARTITION` 语句指定如何将输入数据集逻辑性地划分为用于模型训练、验证和测试的不相交子集。

`TARGET` 语句命名 `PROC GRADBOOST` 预测的变量。

`TRANSFERLEARN` 语句命名一个变量，其值指示观测是属于训练数据还是辅助数据。值在 0 到 1 之间表示训练数据，值大于等于 1 表示辅助数据。值为缺失或负数的观测将被忽略。

可以指定以下选项：

*   **BURN=number**  
    指定在对辅助数据中的任何观测进行下权重之前创建的树木数量。默认情况下，`BURN=0`。

*   **SHRINKAGE=number**  
    指定应用于对辅助数据进行下权重的加权因子的数值，该数值必须在 0 和 1 之间（不包括边界）。默认情况下，`SHRINKAGE=0.9`。

*   **TRIMMING=number**  
    指定在训练数据的梯度分布中，超过该数值的部分之后，辅助观测将被下权重的分数。该数值必须大于 0 且小于等于 1/2。默认情况下，`TRIMMING=0.01`。

> 要在 `GRADBOOST` 过程中使用转移学习，你必须将训练数据和辅助数据拼接起来，并在 `PROC GRADBOOST` 语句的 `DATA=` 选项中指定拼接后的数据表。为了区分两类数据，你必须创建一个指示变量。

### 演示场景

模拟数据用于展示使用 `GRADBOOST` 过程实现转移学习的应用。`DATA` 步骤生成了三个数据集：一个包含训练数据（朋友和外星人都包含）的数据集，一个不包含外星人的数据集，以及一个第三个数据集，其中测试观测从训练数据中被保留出来。Train、Test 和 NoAlien 三个数据集分别包含 6000、1000 和 4000 个观测，它们都包含以下列：

*   `X1` || (正态分布输入变量) |
*   `X2` || (正态分布输入变量) |
*   `Y` || (二元目标变量，编码为 1 或 -1) |
*   `constantZero` || (单元变量，所有值均为 0) |
*   `dataRole` || (数据角色指示器，编码为 -1、0、1 或 2，分别表示测试数据、目标人群、朋友和外星人) |

想法是运行三次梯度提升。请记住，`TRANSFERLEARN` 语句指定标识辅助观测的变量。

这三个数据集在 `Figure 9.5` (`#Chapter09.xhtml#ch09fig05`) 中以图示形式呈现。

第一个梯度提升模型在包含目标人群训练数据以及辅助数据（朋友和外星人都包含）的训练数据上运行，如 `Figure 9.6` (`#Chapter09.xhtml#ch09fig06`) 所示。`TRANSFERLEARN` 语句指定 `dataRole` 为指示观测是属于训练数据（`dataRole=0`）还是辅助数据（`dataRole=1,2`）的变量。

第二个梯度提升模型在包含目标人群训练数据以及朋友和外星人都包含的辅助数据上的训练数据上运行，如 `Figure 9.7` (`#Chapter09.xhtml#ch09fig07`) 所示。`TRANSFERLEARN` 语句指定 `constantZero` 为变量。当该变量在所有观测中均为 0 时，不进行转移学习。此处不使用 `dataRole` 变量。

第三个梯度提升模型在 NoAlien 数据集上运行，该数据集包含目标人群和仅包含朋友的辅助数据，如 `Figure 9.8` (`#Chapter09.xhtml#ch09fig08`) 所示。`TRANSFERLEARN` 语句指定 `constantZero` 为变量，其值（`constantZero=0`）不指示观测是属于训练数据还是辅助数据。此处也不使用 `dataRole` 变量。

即将进行的演示将实现这三个模型。

**Figure 9.8: Model 3: Without Aliens**

![image](img/f0302-02.jpg)

![image](img/Demo.jpg) **Demo 9.1: Transfer Learning Using Gradient Boosting**

此演示两次运行 `PROC GRADBOOST`，均不使用转移学习：一次使用所有数据，一次不使用外星人。所有模型均使用未包含在训练数据中的目标人群数据进行评估。包含转移学习的模型应提供比不包含转移学习的模型更好的拟合，但不如移除外星人人口的模型效果好。

1. 进入“应用程序”菜单 ![image](img/Line.jpg) 的左上角。

2. 点击“开发 SAS 代码”以在 SAS Studio 中启动。

3. 点击左侧窗格中的“Snippets”图标。在“My Snippets”下的“VBBF”下，双击或拖放“Transfer Learning Code”到画布上。

![image](img/f0303-01.jpg)

程序将在代码编辑器窗口中打开。

- [创建名为 `mycas` 的 `caslib` 后，接下来创建一个本地库 `local`。然后使用三个 `DATA` 步骤在内存中创建新数据集并保存。]
- `libname mycas cas;`
- `libname local '/home/student/casuser/VBBF';`
- `data mycas.TL_train;`
- `set local.TL_train;`
- `run;`
- `data mycas.TL_noAlien;`
- `set local.TL_noAlien;`
- `run;`
- `data mycas.TL_test;`
- `set local.TL_test;`
- `run;`
- 4. `运行此程序部分。`
- 5. `返回代码选项卡。`
- 程序的下一部分使用宏调用 `GRADBOOST` 过程两次：第一次用于训练模型，第二次用于在测试数据上应用模型并输出拟合统计信息。
- `%macro runProc(data=, auxVar=, outfit=);`
- `proc gradboost data=&data. outmodel=mycas.model seed=3331333;`
- `input x: /level=interval;`
- `target y /level=nominal;`
- `transferLearn &auxVar. / burn=10;`
- `run;`
- `proc gradboost data=mycas.TL_test inmodel=mycas.model;`
- `output out=mycas.score;`
- `ods output FitStatistics=&outfit.;`
- `run;`
- `%mend;`
- `%runProc(data=mycas.TL_train, auxVar=datarole, outfit=fit_train);`
- `%runProc(data=mycas.TL_train, auxVar=constantZero, outfit=fit_noTransfer);`
- `%runProc(data=mycas.TL_noAlien, auxVar=constantZero, outfit=fit_noAlien);`
- 用于控制观测下权重的因子由 `TRANSFERLEARN` 语句中的 `SHRINKAGE=` 选项控制。默认使用 `SHRINKAGE=0.9`。为了判断观测是否相似，`GRADBOOST` 过程为每个观测计算梯度。辅助数据中的观测如果与训练数据相似，则其梯度位于训练数据梯度的低或高量位。
- `TRIMMING=` 选项在 `TRANSFERLEARN` 语句中控制训练梯度之外的观测下权重的比例。默认 `TRIMMING=0.01`。
- `GRADBOOST` 过程在 `BURN=` 选项指定的 10 棵树之后才开始对辅助观测进行下权重。
- 6. `运行此程序部分，结果选项卡打开。`
- ![image](img/f0304-01.jpg)
- 将生成六组梯度提升结果：一组使用转移学习、一组不使用转移学习、一组不包含外星人观测。每组都在测试数据上运行以进行公正评估。
- 7. `返回代码选项卡。`
- 程序的下一部分将三个模型的均方误差 (ASE) 合并到一个表中，然后根据树的数量绘制每个模型的 ASE 曲线。
- `%macro extractFit(data=, infit=);`
- `data &data.;`
- `set &infit.;`
- `keep trees ase;`
- `rename ase = &data._ase;`
- `run;`
- `%mend;`
- `%extractFit(data=train, infit=fit_train);`
- `%extractFit(data=noTransfer, infit=fit_noTransfer);`
- `%extractFit(data=noAlien, infit=fit_noAlien);`
- `data result;`
- `merge train noTransfer noAlien;`
- `by trees;`
- `run;`
- `proc template;`
- `define statgraph transferLearning;`
- `begingraph;`
- `layout overlay;`
- `scatterplot y=train_ase x=trees / markerattrs=(color=blue) name='with' legendlabel="With Transfer Learning";`
- `scatterplot y=noTransfer_ase x=trees / markerattrs=(color=red) name='without' legendlabel="Without Transfer Learning";`
- `scatterplot y=noAlien_ase x=trees / markerattrs=(color=brown) name='noAliens' legendlabel="Without Aliens";`
- `discretelegend 'without' 'with' 'noAliens';`
- `endlayout;`
- `endgraph;`
- `end;`
- `run;`
- `proc sgrender data=result template=transferLearning;`
- `run;`
- 8. `运行程序的最后部分。`
- ![image](img/f0306-01.jpg)
- 图表显示三个模型的 ASE 与树数关系：使用转移学习的拟合优于不使用转移学习，但不如完全移除外星人观测的数据时的拟合效果好。由于在此示例中，下权重从第 11 棵树开始，因此转移学习拟合在前 10 棵树上与不使用转移学习的拟合相同。
- 9. `关闭转移学习代码窗口。`
- 10. `不要关闭 SAS Studio，因为您将在下一个演示中继续使用它。`
- ![image](img/EndOfDemo.jpg)

### Transfer Learning 和自动调优

您可以对已训练好的梯度提升模型进行自动调优。

本样本程序使用 SAS 提供的 `Sampsio` 库中的 `HMEQ` 数据集，该数据集包含 5,960 名抵押贷款申请人的观测。变量 `Bad` 表示客户是否偿还贷款或违约。

默认情况下，自动调优从模型训练动作的默认超参数设置开始，除非显式设置。这些默认值作为基准模型，用于后续比较。可以通过直接设置参数值，或在调用 `tune` 动作时使用 `tuningParameters initValue` 选项来实现。

```
proc cas noqueue;
autotune.tuneGradientBoostTree result=r /
trainOptions={
table={name='HMEQ', vars={'CLAGE', 'DEBTINC', 'LOAN',
'MORTDUE', 'VALUE', 'REASON', 'JOB', 'bad'}},
inputs={'CLAGE', 'DEBTINC', 'LOAN', 'MORTDUE',
'VALUE', 'REASON', 'JOB'},
target='bad',
nominals={'REASON', 'JOB', 'bad'},
casOut={name='gbt_hmeq_model', replace=true}
nbins=55
}
tunerOptions={seed=3791538}
;
print r;
run;
quit;
```

另一种写法：

```
proc cas noqueue;
autotune.tuneGradientBoostTree result=r /
trainOptions={
table={name='HMEQ', vars={'CLAGE', 'DEBTINC', 'LOAN',
'MORTDUE', 'VALUE', 'REASON', 'JOB', 'bad'}},
inputs={'CLAGE', 'DEBTINC', 'LOAN', 'MORTDUE', 'VALUE',
'REASON', 'JOB'},
target='bad',
nominals={'REASON', 'JOB', 'bad'},
casOut={name='gbt_hmeq_model', replace=true}
}
tunerOptions={seed=3791538}
tuningParameters = {
{name="nBins", initValue=55}
};
;
print r;
run;
quit;
```

还有 `historyTable` 和 `lookupTable` 选项：

- `historyTable={history_table}` 指定 `autotune` 动作创建的 CAS 表，其中包含所有评估历史数据点。
- `lookupTable={lookup_table}` 指定 `autotune` 动作用于评估查找的 CAS 表。
- `lookupTable` 确保不重复配置，并允许从 `lookupTable` 选择之前调优作业的最佳模型作为初始模型，避免重新训练。

## 梯度提升泊松和 Tweedie 回归树

在 SAS Viya 梯度提升算法中，目标函数的默认分布为二元目标的 `BINARY`、类别目标的 `MULTINOMIAL`、区间目标的 `GAUSSIAN`。但在实际操作中，并非所有区间目标都服从正态分布。当观测的分布属于指数家族时，可以使用相应的广义线性模型分布函数。此外，还可以使用非正态分布构建梯度提升回归模型。图 9.9 展示了除正态分布之外常用的分布。

区间目标的属性（或 `GRADBOOST` 语句中的 `DISTRIBUTION=` 选项）决定在寻找节点划分时优化的目标度量。可能的取值为 `Normal`、`Poisson` 和 `Tweedie`。二元或类别目标的分布分别为二元或多项，相应地。

梯度提升可以视为具有相同底层分布的广义线性模型的扩展，但能够实现更好的预测。更多细节请参见 Friedman, 2001。

> Gradient boosting is a primary predictive modeling algorithm for tree-based models. If you want to specify some uncommon distributions to build a single regression tree, you can build a gradient boosting model with ntree=1 and DISTRIBUTION= option.

### 泊松分布

泊松分布常用于分析计数数据，其中因变量为非负整数（0、1、2、3 等）。在许多方面，泊松分布是计数数据的基准分布，就像正态分布是连续数据的基准分布一样。泊松分布也可用于建模事件的速率或发生频率。此类结果在医学、生物学、社会科学、农业、工程和商业等领域中普遍存在。`OFFSET=` 选项可用于对给定暴露度调整后的速率进行建模。保险建模者通常会分别构建频率和严重性模型，然后将两者结合。很多时候，计数数据的零值过多，无法使用标准泊松分布，此时必须使用零膨胀泊松分布或 Tweedie 分布。

**Figure 9.9: Objective Function Distribution**

![image](img/f0308-01.jpg)

### Tweedie 分布

Tweedie 分布族并不像指数族中的某些分布那样广为人知，尽管它们在保险、微生物学和基因组学等许多领域中被广泛使用。Tweedie 分布是指数分散族的一个特例，其方差等于 φμ^p，其中 μ 是均值，φ 是分散参数，p 是在 Tweedie (1984) 中发现的指数参数（参考链接 Tweedie (1984)）。当 p 在 0 到 1 之间时，该分布未定义。Tweedie 分布可简化为许多其他著名分布。例如：

- 当 p 为 0 时，分布为正态分布；
- 当 p 为 1 时，分布为泊松分布；
- 当 p 为 2 时，分布为伽玛分布；
- 当 p 为 3 时，分布为倒高斯分布；
- 当 1 < p < 2 时，分布为复合泊松-伽玛混合分布，可定义伽玛尺度参数；
- 当 p > 1 时，均值为正值。

最有趣的范围是 1 到 2 之间，在此范围内 Tweedie 分布逐渐失去 0 的质量，随着从泊松分布向伽玛分布转变。此情况下，Tweedie 随机变量可从复合泊松分布（参考链接 Smyth 1996）生成。这是在 `PROC GRADBOOST` 中的 `TWEEDIE` 分布，默认 `POWER=p` 为 1.5。在 Model Studio 中，Tweedie 功率参数指定在选择 Tweedie 作为区间目标分布时使用的功率参数。

![image](img/Demo.jpg) **Demo 9.2: Building a Gradient Tree-Boosted Tweedie Compound Poisson Model**

此演示使用 `DISTRIBUTION` 选项在 bigPVA 数据上运行 `PROC GRADBOOST`，构建一个针对美国退伍军人协会慈善捐赠数据的梯度提升 Tweedie 复合泊松模型。该数据反映了邮寄募捐活动的结果。

**注意**：您也可以在 Model Studio 中使用梯度提升节点（区间目标分布属性）和 GLM 节点（目标概率分布和链接函数属性）运行本演示。

1. 确保您在 SAS Studio – Develop SAS Code 应用程序中。

2. 单击左侧窗格中的 Snippets 图标。在 My Snippets ![image](img/Arrow.jpg) VBBF 下，双击或拖放 Tweedie Gradient Boosting Code 到画布上。

![image](img/f0310-01.jpg)

程序打开在代码编辑器窗口中。

首先，创建名为 `mycas` 的 `caslib`。随后创建名为 `local` 的本地库。然后使用 `DATA` 步骤创建新数据集并将其保存在内存中。

```
/* 定义库并加载数据 */
libname mycas cas;
libname local '/home/student/casuser/VBBF';
data mycas.bigpva;
    set local.bigpva;
run;
```

3. 运行程序的这部分。

4. 继续在 Code 标签页上执行代码。

接下来的程序部分列出所有变量、为区间和名义输入创建宏变量，并通过绘图探索目标分布。

```
/* 列出变量 */
proc contents data=mycas.bigpva out=contents(keep=name type);
run;

/* 为区间输入创建宏变量 */
proc sql; select name into: interval separated by " "
from work.contents
where type=1 and name not in("TARGET_B" "TARGET_D" "TARGET_D_with0" "StatusCatStarAll");
quit; %put &interval;

/* 为名义输入创建宏变量 */
proc sql; select name into: nominal separated by " "
from work.contents
where (type=2 or name = "StatusCatStarAll") and name ne "ID";
quit;
%put &nominal;

/* 探索数据 */
proc univariate data=mycas.bigpva;
    var Target_D Target_D_with0;
    histogram Target_D Target_D_with0;
run;
```

运行这部分后，Results 标签页会打开。

数据表包含 100,000 行以上、29 列。表中包含三个可能的目标变量（一种二元和两个区间变量）、一个 ID 变量以及 25 个潜在输入变量，这些变量涵盖受访者的 PVA 促销、历史和人口学数据。`TARGET_B` 是二元标志位，用于指示受访者是否响应呼吁，而 `TARGET_D` 则表示捐赠金额。`TARGET_D` 与 `TARGET_Dwith0` 的区别在于两者的正值相等；在 `TARGET_D` 中，0 值被替换为缺失（.），演示中使用该变量。两个候选输入变量包含缺失值，但树基模型能够很好地处理缺失值。

**注意**：尝试在 `GiftCntAll` 变量上使用 `DISTRIBUTION=POISSON` 建立梯度提升模型也很有趣。

![image](img/f0312-01.jpg)
![image](img/f0312-02.jpg)

`Target_D` 没有 0 值，而是缺失值。数据呈右偏分布。在传统回归建模中，常用对数变换来 regularize（平稳）右偏数据。

![image](img/f0313-01.jpg)
![image](img/f0313-02.jpg)

`Target_D_with0` 包含 0 值而非缺失值。其分布更右偏，可能呈零膨胀。使用高斯分布目标的提升模型在这类数据上表现不佳，因为在寻找节点分裂时会遇到困难。

5. 返回 Code 标签页。

接下来的程序部分运行一个使用 Tweedie 分布的提升模型，以及一个使用 Tweedie 分布的传统广义线性模型。

```
/* 提升模型与 Tweedie 分布 */
ods noproctitle;
proc gradboost data=mycas.bigpva distribution=tweedie;
    target Target_D_with0 / level=interval;
    input &interval / level=interval;
    input &nominal / level=nominal;
    ods output FitStatistics=Work._Gradboost_FitStats_;
    score out=mycas.GB_Tweedie copyvars=(_all_);
run;

/* 广义线性模型与 Tweedie 分布 */
ods noproctitle;
ods graphics / imagemap=on;
proc genmod data=MYCAS.BIGPVA;
    class &nominal / param=glm;
    model Target_D_with0= &interval &nominal /
        dist=tweedie(p=1.5) link=log;
    ods output FitStatistics=Work._GenMod_FitStats_;
    output out=work.Genmod_Tweedie pred=pred_ resraw=r_;
run;

/* 使 GenMod residuals 与 GradBoost residuals 可比较 */
data GenMod_Tweedie;
set Genmod_Tweedie;
r_=-r_;
run;
```

The `GENMOD` 程序适用于多种统计模型。采用 Tweedie 分布和 `log` 链接函数的广义线性模型用于比较梯度提升模型。Tweedie 功率参数 `p` 设置为 `1.5` 以使模型可比较。Tweedie 分布的支持范围为非负值，并且可以在零处有离散质量，这使其适用于模拟零值与正值混合的响应。Tweedie 分布属于指数族，因而便于在广义线性模型框架中使用。

7. 运行本程序部分。不要查看结果。

8. 保持在 `Code` 选项卡上运行程序。

程序的下一部分用于绘制两个模型的残差对实际值的图。

```
/* 为两个模型绘制残差对实际值的图 */
ods graphics / reset width=6.4in height=4.8in imagemap;
title 'Plot of Residuals by Actuals: Gradient Boosting Distribution=Tweedie';
proc sgplot data=mycas.GB_tweedie;
    scatter x=Target_D_with0 y=_Residual_ /;
    xaxis grid;
    yaxis grid;
run;

title 'Plot of Residuals by Actuals: Generalized Linear Model Distribution=Tweedie';
proc sgplot data=work.GenMod_Tweedie;
    scatter x=Target_D_with0 y=r_;
    xaxis grid;
    yaxis grid;
run;
```

9. 运行本程序部分。结果选项卡会打开。

![image](img/f0315-01.jpg)
![image](img/f0315-02.jpg)

已为两个模型生成残差对实际值的图。Tweedie 回归模型中存在若干异常大的残差，尤其是在捐赠金额较小且接近零时。两个模型均低估了目标值，尤其是在捐赠金额较大时。

10. 点击 `Code` 选项卡返回程序。

下一部分用于绘制两个模型的预测值对实际值的图。

```
/* 为两个模型绘制预测值对实际值的图 */
title 'Plot of Predicted by Actuals to plot by Actuals: Gradient Boosting Distribution=Tweedie';
proc sgplot data=mycas.GB_tweedie;
    scatter x=Target_D_with0 y=P_Target_D_with0 /;
    series x=Target_D_with0 y=Target_D_with0 /
        lineattrs=(color=red); *reference line;
    xaxis grid;
    yaxis grid;
run;

title 'Plot of Predicted by Actuals: Generalized Linear Model Distribution=Tweedie';
proc sgplot data=work.GenMod_Tweedie;
    where pred_ between 0 and 200;
    scatter x=Target_D_with0 y=pred_ /;
    series x=Target_D_with0 y=Target_D_with0 /
        lineattrs=(color=red); *reference line;
    xaxis grid;
    yaxis grid;
run;

ods graphics / reset;
```

11. 运行本程序部分。结果选项卡会打开。

![image](img/f0316-01.jpg)
![image](img/f0317-01.jpg)

梯度提升模型的拟合优度优于广义线性模型。这可能是因为树基模型相对于参数模型具有明显的优势。

当捐赠金额较低时，梯度提升模型的残差较小；但在捐赠金额较高时，残差更分散。相反，广义线性模型在捐赠金额较低和较高时的残差均较高。

12. 点击 `Code` 选项卡返回程序的最后一部分，用于计算平均平方误差以比较模型。

```
/* 评估模型拟合 */
title "ASE";
proc sql;
select sum(_Residual_**2)/count(*) as GradBoost_Tweedie
    from mycas.GB_Tweedie;
select sum(r_**2)/count(*) as GenMod_Tweedie
    from work.GenMod_Tweedie;
quit;
title;
```

13. 运行本程序部分。结果选项卡会打开。

![image](img/f0317-02.jpg)

梯度提升模型（使用 Tweedie 分布）的平均平方误差优于广义线性模型（使用 Tweedie 分布）。

调整 Tweedie 的功率参数可以进一步提升模型。

14. 关闭 Tweedie 梯度提升 `Code` 选项卡。

15. 从应用程序菜单中选择 `Build Models` 以关闭 SAS Studio 并返回模型工作区。

![image](img/EndOfDemo.jpg)

## SAS 梯度提升使用开源技术

在本书 earlier，您看到过 SAS Viya 的 Python 与 R 集成（参见 第 7 章）。“开放”一词在 图 9.10 中表示 SAS 的分析能力可以通过多种编程语言访问——不仅限于 SAS，还包括 Python、R、Lua、Java 或 RESTful API。这种集成使得各种背景和经验的分析团队能够协作，以新颖方式解决复杂问题。

本节讨论在开源语言中以编程方式访问并执行 SAS 分析的示例。为保持一致性，主要聚焦于通过 Python（流行的通用脚本语言）通过 API 调用 SAS。SAS 提供基础开源包 SWAT（Scripting Wrapper for Analytics Transfer），该包可在 GitHub 上获取，用于与 SAS Viya 进行交互。SWAT 包提供与 SAS Viya 的接口。

基础 SAS 提供一个 Java 对象，可用于将多种外部语言（包括 Python）集成。这使得 SAS 过程可以从开源工具中调用。SAS Jupyter 核心为 SAS 数据处理和分析能力带入 Jupyter Notebook，使得用户能够在 Notebook 中利用 SAS 的数据处理与分析能力。通过开源方式使用 SAS，可简化未曾使用 SAS 的用户的迁移。通过存储过程或 API 从其他编程接口调用 SAS，是开源程序员访问 SAS 的简便方式。

**图 9.10: SAS Viya 与开源软件的集成**

![image](img/f0318-01.jpg)

这种开放性使得数据科学家能够在其选择的语言和界面中编写代码，同时使 SAS 能够将开源应用扩展为高生产力并能够处理任意数据量。

![image](img/Demo.jpg) **演示 9.3：使用 Python 训练和评分 SAS 梯度提升模型**

本演示在 Jupyter Notebook 中使用 Python 脚本运行 SAS 梯度提升模型。`gbtreeTrain` 和 `gbTreeScore` 动作集中的决策树动作用于保险数据上，用于训练和评分梯度提升模型。

1. 最小化 SAS Viya 选项卡。

2. 在 Windows 操作系统中：启动 ![image](img/Arrow.jpg) Anaconda3（64 位） ![image](img/Arrow.jpg) Jupyter Notebook（Anaconda3）。

3. Jupyter Notebook 启动。请确保处于 Files 选项卡，并且已上传一个笔记本文件。

![image](img/f0319-01.jpg)

4. 双击 `SAS_GradBoost_Py_Jupyter.ipynb` 打开用于在 SAS Viya 中执行梯度提升分析的 Python 脚本。

![image](img/f0319-02.jpg)

或者，选择 New 然后选择 Python 3。

![image](img/f0319-03.jpg)

从数据文件夹中复制 `SAS_GradBoost` Python 脚本文件的内容。

![image](img/f0320-01.jpg)

5. 运行下面的 Python 代码。

您可以逐行运行代码单元，也可以一次性运行整个笔记本。

![image](img/f0320-02.jpg)

### Python 代码用于 SAS 梯度提升

导入用于本示例的 SAS Scripting Wrapper (SWAT) for Analytics Transfer 库：

![image](img/f0320-03.jpg)

指定连接到 SAS Viya CAS 会话的 CAS 主机名称和端口号：

![image](img/f0320-04.jpg)

注意 `8777` 是 CAS 服务器监控进程所需的端口，客户端（如 Python REST 接口）使用该端口通过 REST HTTP 请求与 CAS 交互。更多细节请参阅 SAS Viya 3.5 for Linux: Deployment Guide 文档。

加载分析数据到 CAS：

![image](img/f0320-05.jpg)

返回表格信息：

![image](img/f0321-01.jpg)

该表格包含 19,357 条观测数据和 50 个变量。

---

- [费曼学习法](https://wiki.example.org/feynmans_learning_method)的灵感源于诺贝尔物理奖获得者 **Richard Feynman**。

1. 运用费曼技巧，你只需花上 `20 min` 就能深入理解知识点，而且记忆深刻，*难以遗忘*。
