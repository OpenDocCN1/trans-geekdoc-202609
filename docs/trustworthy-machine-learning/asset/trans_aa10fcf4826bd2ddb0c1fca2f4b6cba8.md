
标签与受保护属性之间的独立性对应于它们的联合概率等于各自边缘概率的乘积。这个乘积概率出现在权重公式的分子中，而实际观察到的联合概率出现在分母中：

`w_j = p_Y(y_j) p_Z(z_j) / p_{Y,Z}(y_j, z_j).`

公式10.8

训练数据中需要受保护属性来学习模型，但它们不必成为模型或部署数据的一部分。

与数据增强和重新加权不改变历史护理管理决策所获得的训练数据不同，其他方法会改变这些数据。一种仅适用于统计均等和“人皆平等”世界观、称为“massaging”的简单方法，将非特权群体成员的不利标签翻转为有利标签，并将特权群体成员的有利标签翻转为不利标签。18 所选的数据点是那些最接近决策边界且置信度较低的点。Massaging 不需要在部署数据中包含受保护属性。

另一种方法，公平分数转换器（fair score transformer），处理的是（校准后的）连续分数标签 `S = p_{Y|X}(Y = fav | x)`，而不是二元标签。19 它被表述为一个优化问题：在约束统计均等差异、平均几率差异或其他你选择的群组公平度量的绝对值较小的同时，找到与原始分数 S 交叉熵较小的变换后分数 S′，即 `H(S || S′)`。你可以将预处理后的分数以权重形式转换回二元标签，以馈送给标准训练算法。你可以用“所见即所得”的世界观来使用公平分数转换器，因为它假设随后在预处理数据集上训练的分类器是称职的，因此它所产生的预处理分数能够很好地近似训练后的模型所预测的分数。尽管有一些预处理方法会同时改变标签和（结构化或半结构化）特征，20 公平分数转换器证明了你只需要改变标签。它可以处理未附带受保护属性的部署数据。

数据增强、重新加权、massaging 和公平分数转换器各有其适用领域。在不同的公平性度量和数据集特征下，有些方法比其他方法表现更好。你需要尝试不同的方法，看看在 Sospital 数据上的效果。

## 10.5.2 处理中

处理中的偏见缓解算法表述起来很直接，但实际优化往往更难。其表述如下：采用一个现有的基于风险最小化的监督学习算法，例如（重复方程7.4）：

```
f̂(·) = arg min_{f ∈ F} 1/n Σ_{j=1}^n L(y_j, f(x_j)) + λJ(f)
```

公式10.9

并使用公平性度量对其正则化或约束。算法可以是逻辑回归，正则化器可以是统计均等差异，这时你得到的就是“偏见消除器”（prejudice remover）。²¹ 更近期的公平学习算法适用范围更广，允许任何标准风险最小化算法以及覆盖不同类型公平性的一系列群组公平度量作为约束。²² 一个近期的处理中算法使用因果公平项对目标函数进行正则化。在强可忽略性假设下（记得第8章中提到这些假设是没有未测量的混淆因素且存在重叠），正则化器是一个类似平均处理效应的项 `J = E[Y | do(z = 1), X] − E[Y | do(z = 0), X]`。²³

一旦训练完成，所得模型可用于新的未见过的 Sospital 成员。这些处理中算法不要求部署数据包含受保护属性。它们的关键在于构造缓解偏见的正则化项或约束，使目标函数能够通过优化算法可处理地最小化。

## 10.5.3 处理后

如果你遇到的情况是 Sospital 护理管理模型已经训练完成，而且你无法更改它或触碰训练数据（例如，你从供应商那里购买一个预训练模型以集成到你的流程中），那么你唯一的选择就是使用后处理来缓解不希望的偏见。你只能改变输出预测 Ŷ 以满足你根据世界观所期望的群组公平度量（即，将“接受护理管理”的预测标签翻转为“不接受护理管理”，反之亦然）。如果你有一些带标签的验证数据，你可以采用“所见即所得”的世界观进行后处理。你总是可以采用“人皆平等”的世界观进行后处理，无论有无验证数据。

²¹Toshihiro Kamishima, Shotaro Akaho, Hideki Asoh, and Jun Sakuma. “Fairness-Aware Classifier with Prejudice Remover Regularizer.” In: Proceedings of the Joint European Conference on Machine Learning and Knowledge Discovery in Databases. Bristol, England, UK, Sep. 2012, pp. 35–50. ²²Alekh Agarwal, Alina Beygelzimer, Miroslav Dudík, John Langford, and Hanna Wallach. “A Reductions Approach to Fair Classification.” In: Proceedings of the International Conference on Machine Learning. Stockholm, Sweden, Jul. 2018, pp. 60–69. L. Elisa Celis, Lingxiao Huang, Vijay Keswani, and Nishanth K. Vishnoi. “Classification with Fairness Constraints: A Meta-Algorithm with Provable Guarantees.” In: Proceedings of the ACM Conference on Fairness, Accountability, and Transparency. Atlanta, Georgia, USA, Jan. 2019, pp. 319–328. Ching-Yao Chuang and Youssef Mroueh. “Fair Mixup: Fairness via Interpolation.” In: Proceedings of the International Conference on Learning Representations. May 2021. ²³Pietro G. Di Stefano, James M. Hickey, and Vlasios Vasileiou. “Counterfactual Fairness: Removing Direct Effects Through Regularization.” arXiv:2002.10774, 2020.

构造空间中的准确性和公平性。27 你可以通过使用数据增强预处理方法来逼近构造空间测试集。

表10.2 主要偏见缓解算法的特征。

| 算法 | 类别 | 公平性 | 部署数据中的受保护属性 |
|---|---|---|---|
| 数据增强 | 预处理 | 反事实 | 是 |
| 重新加权 | 预处理 | 独立性 | 否 |
| massaging | 预处理 | 独立性 | 否 |
| 公平分数转换器 | 预处理、后处理 | 独立性、分离性 | 否 |
| 偏见消除器 | 处理中 | 独立性 | 否 |
| 近期处理中算法 | 处理中 | 独立性、分离性、充分性 | 否 |
| 因果正则化器 | 处理中 | 反事实 | 否 |
| 群组公平后处理 | 后处理 | 独立性、分离性 | 是 |
| 个体与群组公平后处理 | 后处理 | 反事实、独立性、分离性 | 是 |

在你的 Sospital 问题中，你几乎拥有完全的灵活性，因为你确实控制着训练数据和模型训练，专注于独立性和“人皆平等”世界观，并且能够在部署数据中加入 Sospital 成员的受保护属性。尝试所有方法，但最好从公平分数转换器预处理开始。

## 10.6 其他考虑

在结束本章之前，让我们考虑几个其他问题。第一个问题在 Sospital 护理管理用例中没有出现，但在其他用例中可能会出现。Sospital 问题本身适用于直接分配决策中的公平性，但这不是唯一的可能性。还存在表征或服务质量方面的危害，例如搜索结果中的偏见。例如，职业形象搜索可能只返回白人，与非裔美国人社区中常见人名相关的网页搜索结果可能附带刑事辩护律师的广告，而用于语言翻译或查询理解的自然语言处理算法可能会自动将医生与男性关联、将护士与女性关联。一些用于分配公平的偏见缓解算法可用于表征公平，但不同的技术可能更合适。

27Michael Wick, Swetasudha Panda, and Jean-Baptiste Tristan. “Unlocking Fairness: A Trade-Off Revisited.” In: Advances in Neural Information Processing Systems 32 (Dec. 2019), pp. 8783–8792. Kit T. Rodolfa, Hemank Lamba, and Rayid Ghani. “Empirical Observation of Negligible Trade-Offs in Machine Learning for Public Policy.” In: Nature Machine Intelligence 3 (Oct. 2021), pp. 896–904.
