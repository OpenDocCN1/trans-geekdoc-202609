
$P(\\left\\{ \\mathit{yellow\\ yellow\\ yellow} \\right\\}\\text{∣}H) = 3! \\times \\frac{0.75^{3}}{3!} \\times \\frac{0.25^{0}}{0!} = \\frac{27}{64}.$<mml:math><mml:mi>P</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mo>{</mml:mo><mml:mi mathvariant="italic">yellow yellow yellow</mml:mi><mml:mo>}</mml:mo><mml:mtext mathvariant="normal">&#8739;</mml:mtext><mml:mi>H</mml:mi><mml:mo stretchy="false">)</mml:mo><mml:mo>=</mml:mo><mml:mn>3</mml:mn><mml:mo>!</mml:mo><mml:mo>&#215;</mml:mo><mml:mfrac><mml:mrow><mml:msup><mml:mrow><mml:mn>0.75</mml:mn></mml:mrow><mml:mrow><mml:mn>3</mml:mn></mml:mrow></mml:msup></mml:mrow><mml:mrow><mml:mn>3</mml:mn><mml:mo>!</mml:mo></mml:mrow></mml:mfrac><mml:mo>&#215;</mml:mo><mml:mfrac><mml:mrow><mml:msup><mml:mrow><mml:mn>0.25</mml:mn></mml:mrow><mml:mrow><mml:mn>0</mml:mn></mml:mrow></mml:msup></mml:mrow><mml:mrow><mml:mn>0</mml:mn><mml:mo>!</mml:mo></mml:mrow></mml:mfrac><mml:mo>=</mml:mo><mml:mfrac><mml:mrow><mml:mn>27</mml:mn></mml:mrow><mml:mrow><mml:mn>64</mml:mn></mml:mrow></mml:mfrac><mml:mrow><mml:mo>.</mml:mo></mml:mrow></mml:math>

![方程](images/F000054si28.png)

其他三个及其概率为

$P(\\left\\{ \\mathit{blue\\ blue\\ blue} \\right\\}\\text{∣}H) = \\frac{1}{64}$<mml:math><mml:mi>P</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mo>{</mml:mo><mml:mi mathvariant="italic">blue blue blue</mml:mi><mml:mo>}</mml:mo><mml:mtext mathvariant="normal">&#8739;</mml:mtext><mml:mi>H</mml:mi><mml:mo stretchy="false">)</mml:mo><mml:mo>=</mml:mo><mml:mfrac><mml:mrow><mml:mn>1</mml:mn></mml:mrow><mml:mrow><mml:mn>64</mml:mn></mml:mrow></mml:mfrac></mml:math>

![方程](images/F000054si29.png)

$P(\\left\\{ \\mathit{yellow\\ yellow\\ blue} \\right\\}\\text{∣}H) = \\frac{27}{64}$<mml:math><mml:mi>P</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mo>{</mml:mo><mml:mi mathvariant="italic">yellow yellow blue</mml:mi><mml:mo>}</mml:mo><mml:mtext mathvariant="normal">&#8739;</mml:mtext><mml:mi>H</mml:mi><mml:mo stretchy="false">)</mml:mo><mml:mo>=</mml:mo><mml:mfrac><mml:mrow><mml:mn>27</mml:mn></mml:mrow><mml:mrow><mml:mn>64</mml:mn></mml:mrow></mml:mfrac></mml:math>

![方程](images/F000054si30.png)

$P(\\left\\{ \\mathit{yellow\\ blue\\ blue} \\right\\}\\text{∣}H) = \\frac{9}{64}$<mml:math><mml:mi>P</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mo>{</mml:mo><mml:mi mathvariant="italic">yellow blue blue</mml:mi><mml:mo>}</mml:mo><mml:mtext mathvariant="normal">&#8739;</mml:mtext><mml:mi>H</mml:mi><mml:mo stretchy="false">)</mml:mo><mml:mo>=</mml:mo><mml:mfrac><mml:mrow><mml:mn>9</mml:mn></mml:mrow><mml:mrow><mml:mn>64</mml:mn></mml:mrow></mml:mfrac></mml:math>

![方程](images/F000054si31.png)

`E` 对应于最后一种情况（请记住，在词袋中顺序无关紧要）；因此它由 *黄绿色* 文档模型生成的概率为 9/64，即 14%。假设另一个类别，即 *非常蓝绿色* 文档（称为 `H`′<mml:math><mml:mi>H</mml:mi><mml:mo accent="false">&#8242;</mml:mo></mml:math>![方程](images/F000054si32.png)），其 `P`(`yellow` |`H`′<mml:math><mml:mi>H</mml:mi><mml:mo accent="false">&#8242;</mml:mo></mml:math>![方程](images/F000054si33.png)) = 10% 且 `P`(`blue` |`H`′<mml:math><mml:mi>H</mml:mi><mml:mo accent="false">&#8242;</mml:mo></mml:math>![方程](images/F000054si34.png)) = 90%。该模型生成 `E` 的概率为 24%。

如果只有这两个类别，这是否意味着 `E` 属于 *非常蓝绿色* 文档类别？不一定。前面给出的贝叶斯规则指出，你必须考虑每个假设的先验概率。如果已知事实上 *非常蓝绿色* 文档比 *黄绿色* 文档稀有两倍，这就足以抵消 14%–24% 的差异，并使平衡倾向于 *黄绿色* 类别。

概率公式中的阶乘实际上不需要计算，因为——对每个类别都相同——它们在归一化过程中会被抵消。然而，公式仍然涉及将许多小的概率相乘，这很快就会产生极小的数字，导致在大文档上出现下溢。这个问题可以通过使用概率的对数而不是概率本身来避免。

在多项式朴素贝叶斯公式中，文档的类别不仅由其中出现的词决定，还由这些词出现的次数决定。一般来说，它在文档分类方面比普通的朴素贝叶斯模型表现更好，尤其是在词典规模较大时。

### 备注

朴素贝叶斯提供了一种简单的方法，具有清晰的语义，用于表示、使用和学习概率知识。它可以取得令人印象深刻的结果。人们经常发现，朴素贝叶斯在许多数据集上与更复杂的分类器不相上下，甚至表现更好。道理是，总是先尝试简单的方法。反复地，人们最终在长期挣扎后，使用复杂的学习方案取得了良好的结果，却后来发现像 `1R` 和朴素贝叶斯这样简单的方法做得一样好，甚至更好。其在分类问题中有效的主要原因是，最大化分类准确率不需要特别精确的概率估计；只要正确类别获得最大概率就足够了。

然而，也有许多数据集朴素贝叶斯表现不佳，很容易看出原因。因为在给定类别的情况下，属性被视为独立，冗余属性的添加会扭曲学习过程。例如，如果你在天气数据中加入一个与 `temperature` 具有相同值的新的属性，`temperature` 属性的影响就会被放大；其所有概率都会被平方，从而在决策中产生很大的影响。如果你加入 10 个这样的属性，决策实际上将仅基于 `temperature`。属性之间的依赖关系不可避免地降低了朴素贝叶斯辨别实际情况的能力。然而，通过在决策过程中使用属性的子集，可以缓解这种情况，仔细选择使用哪些属性。[第6章](#Ch006_209-259_B9780443158889000078.xhtml#Ch006_209-259_B9780443158889000078)，“准备：数据预处理和探索性数据分析，”展示了如何操作。

数值属性的正态分布假设是我们在此所表述的朴素贝叶斯的另一个限制。许多特征根本不是正态分布的。然而，没有什么可以阻止我们使用其他分布；正态分布并没有什么神奇之处。如果你知道某个特定属性可能遵循其他分布，可以改用该分布的标准估计程序。如果你怀疑它不是正态分布但不知道实际分布，则有“核密度估计”程序，不假设属性值的任何特定分布。另一种可能性是先对数据进行离散化。

朴素贝叶斯是一个非常简单的概率模型，我们在 [第13章](#Ch014_485-514_B9780443158889000145.xhtml#Ch014_485-514_B9780443158889000145)，“概率方法：基础，” 和 [第14章](#Ch015_516-570_B9780443158889000157.xhtml#Ch015_516-570_B9780443158889000157)，“高级概率方法。” 中考察了更复杂的模型。

## 4.3 分而治之：构建决策树
