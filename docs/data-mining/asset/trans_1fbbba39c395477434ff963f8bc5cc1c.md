
假设你不想生成保证对训练集中所有实例都给出正确分类的完美规则，而是更愿意生成“合理”的规则，避免对训练集过拟合，从而在新测试实例上表现更好的机会更大。你如何决定哪些规则值得采用？你如何判断继续向规则添加条件以排除少数顽固的错误类型实例变得适得其反，同时排除越来越多正确类型的实例？

让我们看几个可能的规则示例——有些好有些坏——针对[表 1.1](#Ch001_3-42_B9780443158889000029.xhtml#t0010)中的隐形眼镜问题。首先考虑规则

```
If astigmatism = yes and tear production rate = normal then recommendation = hard.
```

该规则对其覆盖的六个案例中有四个结果正确；因此其成功率为 4/6。假设我们添加一个额外条件使规则成为“完美”的：

```
If astigmatism = yes and tear production rate = normal and age = young then recommendation = hard.
```

这将准确率提高到 2/2。哪个规则更好？第二个规则在训练数据上更准确，但只覆盖了两个案例，而第一个规则覆盖了六个。可能是第二个版本只是对训练数据过拟合。对于实用的规则学习器，我们需要一种有原则的方法来选择合适的规则版本，最好能最大化未来测试数据的准确率。

假设我们将训练数据分成两部分，我们称之为 `growing set` 和 `pruning set`。`growing set` 用于使用基本覆盖算法形成规则。然后从规则中删除一个测试，并通过在 `pruning set` 上尝试截断后的规则来评估其效果，看看它是否比原始规则表现更好。此剪枝过程重复进行，直到无法通过删除更多测试来改进规则为止。整个过程对每个类别重复，得到每个类别的最佳规则，并通过在 `pruning set` 上评估规则来确定总体最佳规则。然后将该规则添加到规则集，删除其覆盖的实例——从 `growing set` 和 `pruning set` 两者中删除——并重复该过程。

为什么不在构建规则的同时进行剪枝，而不是先构建完整规则然后再丢弃部分？也就是说，为什么不预剪枝而是后剪枝？正如剪枝决策树时通常最好先将树生长到最大尺寸然后再剪枝一样，对于规则而言通常最好先制作一个完美规则然后再剪枝它。谁知道呢，添加最后一个条件可能会使规则变得非常好，如果我们采用激进的预剪枝策略，我们可能永远不会注意到这种情况。

`growing set` 和 `pruning set` 必须分开至关重要，因为在用于形成规则的相同数据上评估规则会产生误导。这会导致严重错误，因为会偏好过拟合的规则。通常训练集被分割，使得三分之二的实例用于 `growing`，三分之一用于 `pruning`。当然，其缺点是学习仅来自 `growing set` 中的实例，因此算法可能会遗漏重要规则，因为某些关键实例被分配到了 `pruning set`。此外，错误的规则可能会被偏好，因为 `pruning set` 只包含三分之一的数据，可能并不完全具有代表性。通过在算法的每个周期、每次规则最终选定后重新将训练数据分割为 `growing set` 和 `pruning set`，可以缓解这些影响。

使用单独的剪枝集进行剪枝的想法，适用于决策树和规则集，被称为 `reduced-error pruning`。前面描述的变体在规则生长后立即剪枝规则，被称为 `incremental reduced-error pruning`。另一种可能性是先构建完整的未剪枝规则集，然后通过丢弃单个测试对其进行剪枝。然而，这种方法要慢得多。

当然，基于 `pruning set` 评估规则价值的方法有很多种。一种简单的度量是考虑如果该规则是规则集中唯一的规则，在封闭世界假设下，它区分预测类别与其他类别的能力如何。假设它在覆盖的 `t` 个实例中正确 `p` 个，而该类别共有 `P` 个实例，总实例数为 `T`。它未覆盖的实例包括 `N`–`n`<mml:math><mml:mi>N</mml:mi><mml:mi>&#8211;</mml:mi><mml:mi>n</mml:mi></mml:math>![Equation](images/F000236si43.png) 个负例，其中 `n` = `t`–`p`<mml:math><mml:mi>n</mml:mi><mml:mo>=</mml:mo><mml:mi>t</mml:mi><mml:mi>&#8211;</mml:mi><mml:mi>p</mml:mi></mml:math>![Equation](images/F000236si44.png) 是规则覆盖的负例数量，而 `N` = `T`–`P`<mml:math><mml:mi>N</mml:mi><mml:mo>=</mml:mo><mml:mi>T</mml:mi><mml:mi>&#8211;</mml:mi><mml:mi>P</mml:mi></mml:math>![Equation](images/F000236si45.png) 是负例总数。因此总共规则在 `p` + (`N`–`n`)<mml:math><mml:mi>p</mml:mi><mml:mo>+</mml:mo><mml:mo stretchy="false">(</mml:mo><mml:mi>N</mml:mi><mml:mi>&#8211;</mml:mi><mml:mi mathvariant="italic">n</mml:mi><mml:mo stretchy="false">)</mml:mo></mml:math>![Equation](images/F000236si46.png) 个实例上做出正确决策，因此其总体成功率为

\[`p`+(`N`–`n`)\]/*T*.<mml:math><mml:mo>\[</mml:mo><mml:mi>p</mml:mi><mml:mo>+</mml:mo><mml:mo>(</mml:mo><mml:mi>N</mml:mi><mml:mi mathvariant="normal">&#8211;</mml:mi><mml:mi>n</mml:mi><mml:mo>)</mml:mo><mml:mo>\]</mml:mo><mml:mo>&#8725;</mml:mo><mml:mi>T</mml:mi><mml:mo>.</mml:mo></mml:math>

![Equation](images/F000236si47.png)

该量在测试集上评估，已被用于在使用 `reduced-error pruning` 时评估规则的成功率。

该度量受到批评，因为它将负例的未覆盖视为与正例的覆盖同等重要，而在评估的规则最终将与其他许多规则一起使用时，这是不现实的。例如，一个规则在总覆盖 3000 个实例中正确 `p` = 2000<mml:math><mml:mi>p</mml:mi><mml:mo>=</mml:mo><mml:mn>2000</mml:mn></mml:math>![Equation](images/F000236si48.png) 个实例（即错误 `n` = 1000<mml:math><mml:mi>n</mml:mi><mml:mo>=</mml:mo><mml:mn>1000</mml:mn></mml:math>![Equation](images/F000236si49.png) 个），被认为比另一个规则更成功，后者在总覆盖 1001 个实例中正确 `p` = 1000<mml:math><mml:mi>p</mml:mi><mml:mo>=</mml:mo><mml:mn>1000</mml:mn></mml:math>![Equation](images/F000236si50.png) 个实例（即错误 `n` = 1<mml:math><mml:mi>n</mml:mi><mml:mo>=</mml:mo><mml:mn>1</mml:mn></mml:math>![Equation](images/F000236si51.png) 个），因为 \[`p` + (`N`–`n`)\]/*T*<mml:math><mml:mo stretchy="false">\[</mml:mo><mml:mi>p</mml:mi><mml:mo>+</mml:mo><mml:mo stretchy="false">(</mml:mo><mml:mi>N</mml:mi><mml:mi>&#8211;</mml:mi><mml:mi>n</mml:mi><mml:mo stretchy="false">)</mml:mo><mml:mo>/</mml:mo><mml:mi>T</mml:mi></mml:math>![Equation](images/F000236si52.png) 在第一种情况下是 \[1000 + `N`\]/*T*<mml:math><mml:mo stretchy="false">\[</mml:mo><mml:mn>1000</mml:mn><mml:mo>+</mml:mo><mml:mi>N</mml:mi><mml:mo stretchy="false">\]</mml:mo><mml:mo>/</mml:mo><mml:mi>T</mml:mi></mml:math>![Equation](images/F000236si53.png)，而在第二种情况下只有 \[999 + `N`\]/*T*<mml:math><mml:mo stretchy="false">\[</mml:mo><mml:mn>999</mml:mn><mml:mo>+</mml:mo><mml:mi>N</mml:mi><mml:mo stretchy="false">\]</mml:mo><mml:mo>/</mml:mo><mml:mi>T</mml:mi></mml:math>![Equation](images/F000236si54.png)。这违反直觉；第一个规则明显比第二个规则预测性更差，因为它有 33.3% 的错误概率，而第二个只有 0.1%。
