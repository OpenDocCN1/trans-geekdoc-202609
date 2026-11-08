
$P\\left( - z < \\frac{f - p}{\\sqrt{\\left. p\\left( 1 - p \\right)\\slash N \\right.}} < z \\right) = c.$<mml:math><mml:mi>P</mml:mi><mml:mo>(</mml:mo><mml:mo>&#8722;</mml:mo><mml:mi>z</mml:mi><mml:mo>&#60;</mml:mo><mml:mfrac><mml:mrow><mml:mi>f</mml:mi><mml:mo>&#8722;</mml:mo><mml:mi>p</mml:mi></mml:mrow><mml:mrow><mml:msqrt><mml:mrow><mml:mi>p</mml:mi><mml:mo>(</mml:mo><mml:mn>1</mml:mn><mml:mo>&#8722;</mml:mo><mml:mi>p</mml:mi><mml:mo>)</mml:mo><mml:mo>&#8725;</mml:mo><mml:mi>N</mml:mi></mml:mrow></mml:msqrt></mml:mrow></mml:mfrac><mml:mo>&#60;</mml:mo><mml:mi>z</mml:mi><mml:mo>)</mml:mo><mml:mo>=</mml:mo><mml:mi>c</mml:mi><mml:mo>.</mml:mo></mml:math>

![Equation](images/F000066si9.png)

现在这里是寻找置信限的步骤。给定一个特定的置信度 `c`，请查阅 [表 5.1](#Ch005_165-207_B9780443158889000066.xhtml#t0010) 获取对应的 `z` 值。使用该表时，你首先需要用 1 减去 `c`，然后将结果除以二，因此当 `c` = 90% 时，你使用表中 5% 的条目。可以对中间的置信水平使用线性插值。然后将前述表达式中的不等式写成等式并求逆，以求出 `p` 的表达式。

最后一步涉及求解一个二次方程。虽然不难做，但它导致置信限的表达式相当难看：

$\\left. p = \\left( {f + \\frac{z^{2}}{2N} \\pm z\\sqrt{\\frac{f}{N} - \\frac{f^{2}}{N} + \\frac{z^{2}}{4N^{2}}}} \\right)/{\\left( {1 + \\frac{z^{2}}{N}} \\right).} \\right.$<mml:math><mml:mi>p</mml:mi><mml:mo>=</mml:mo><mml:msp1/><mml:mrow><mml:mo stretchy="true">(</mml:mo><mml:mrow><mml:mi>f</mml:mi><mml:mo>+</mml:mo><mml:mfrac><mml:mrow><mml:msup><mml:mrow><mml:mi>z</mml:mi></mml:mrow><mml:mn>2</mml:mn></mml:msup></mml:mrow><mml:mrow><mml:mn>2</mml:mn><mml:mi>N</mml:mi></mml:mrow></mml:mfrac><mml:mo>&#177;</mml:mo><mml:mi>z</mml:mi><mml:msqrt><mml:mrow><mml:mfrac><mml:mi>f</mml:mi><mml:mi>N</mml:mi></mml:mfrac><mml:mo>&#8722;</mml:mo><mml:mfrac><mml:mrow><mml:msup><mml:mrow><mml:mi>f</mml:mi></mml:mrow><mml:mn>2</mml:mn></mml:msup></mml:mrow><mml:mi>N</mml:mi></mml:mfrac><mml:mo>+</mml:mo><mml:mfrac><mml:mrow><mml:msup><mml:mrow><mml:mi>z</mml:mi></mml:mrow><mml:mn>2</mml:mn></mml:msup></mml:mrow><mml:mrow><mml:mn>4</mml:mn><mml:msup><mml:mrow><mml:mi>N</mml:mi></mml:mrow><mml:mn>2</mml:mn></mml:msup></mml:mrow></mml:mfrac></mml:mrow></mml:msqrt></mml:mrow><mml:mo stretchy="true">)</mml:mo></mml:mrow><mml:mo stretchy="true">/</mml:mo><mml:mrow><mml:mrow><mml:mo stretchy="true">(</mml:mo><mml:mrow><mml:mn>1</mml:mn><mml:mo>+</mml:mo><mml:mfrac><mml:mrow><mml:msup><mml:mrow><mml:mi>z</mml:mi></mml:mrow><mml:mn>2</mml:mn></mml:msup></mml:mrow><mml:mi>N</mml:mi></mml:mfrac></mml:mrow><mml:mo stretchy="true">)</mml:mo></mml:mrow><mml:mo>.</mml:mo></mml:mrow></mml:math>

![Equation](images/F000066si10.png)

此表达式中的 ± 给出了 `p` 的两个值，表示置信边界的上界和下界。虽然公式看起来很复杂，但在具体情况下并不难计算。

该结果可用于获得前面给出的数值示例中的值。设 `f` = 75%，`N` = 1000，且 `c` = 80%（因此 `z` = 1.28）时，`p` 的区间为 \[0.732, 0.767\]，而 `N` = 100 时在相同置信水平下为 \[0.691, 0.801\]。请注意，正态分布假设仅在 `N` 较大时有效（例如，`N` >100）。因此 `f` = 75% 且 `N` = 10 时的置信限为 \[0.549, 0.881\]——但这些结果应谨慎对待。

## 5.3 交叉验证

现在考虑当用于训练和测试的数据量有限时该怎么办。保留方法为测试保留一定数量的数据，并使用剩余数据进行训练（如果需要，还会为验证预留一部分）。在实践中，通常将三分之一的数据留出用于测试，并使用剩余的三分之二进行训练。

当然，你可能运气不好；用于训练（或测试）的样本可能不具有代表性。一般来说，你无法判断一个样本是否具有代表性。但有一个简单的检查可能值得做——完整数据集中每个类别都应在训练集和测试集中以大致正确的比例表示。如果不幸的是，训练集中遗漏了某个类别的所有示例，你几乎不能期望从该数据学习到的分类器对该类别的示例表现良好。情况会因该类别必然在测试集中过度代表而变得更糟，因为它的实例一个也没有进入训练集！相反，你应确保随机抽样的方式保证每个类别在训练集和测试集中都得到适当表示。此过程称为 *分层*，我们可能会称之为 *分层保留*。虽然通常非常值得做，但分层仅提供防止训练集和测试集表示不均的原始保障。

更一般的方法是通过使用不同的随机样本多次重复整个过程来减轻由为保留选择的特定样本引起的任何偏差。在每次迭代中，约有一定比例——例如三分之二——的数据被随机选出来进行训练，可能采用分层，而剩余部分用于测试。不同迭代的误差率取平均值以得出总体误差率。这就是 *重复保留* 的误差率估计方法。

在单次保留程序中，你可能会考虑交换测试数据和训练数据的角色——即在测试数据上训练系统，并在训练数据上测试它——并对两个结果取平均，从而减少训练集和测试集表示不均的影响。不幸的是，这只有在训练和测试数据之间为 50:50 分割时才真正合理，而这通常不是理想的；即使以牺牲测试数据为代价，使用超过一半的数据进行训练也是更好的。然而，一个简单的变体构成了重要统计技术的基础，该技术称为 *交叉验证*。在交叉验证中，你决定数据的一个固定数量的 *折*，或分区。假设我们使用三个。然后数据被分成三个大致相等的分区；每个分区轮流用于测试，其余部分用于训练。也就是说，使用三分之二进行训练，三分之一进行测试，并重复该过程三次，以便最终每个实例都恰好使用一次进行测试。这称为 *三折交叉验证*，如果同时采用分层（通常如此），则称为 *分层三折交叉验证*。

预测学习技术在给定单个固定数据样本时的误差率的标准方法是使用分层 10 折交叉验证。数据被随机分成 10 部分，其中类别的比例与完整数据集中大致相同。每个部分轮流被保留，学习方案在剩余的九分之十上训练；然后在其保留集上计算其误差率。因此学习过程在不同的训练集上总共执行 10 次（每个训练集有很多共同之处）。最后，将 10 个误差估计值取平均以得出总体误差估计值。
