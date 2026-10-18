

![Remember](images/remember.png)如果你使用的是用于测试的自举外部示例，你会发现测试样本的大小可能各不相同，这取决于样本内唯一示例的数量，可能约占原始样本内大小的三分之一。这段简单的 Python 代码片段演示了如何随机模拟一定数量的自举：

```
import numpy as np
n = 1000
results = list()
for j in range(10000):
    chosen = np.random.randint(0, n, size=n)
    results.append(len(np.unique(chosen)) / n)
avg_oob = 1 - np.mean(results)
print(f"Avg out-of-boostrap: {avg_oob*100:0.3}%")
```

该代码创建大量试验，每个试验都进行有放回抽样（这意味着一个案例可以在样本中被多次重复使用），然后计算每次抽样中唯一示例的数量以及作为外部样本被遗漏的案例比例。最后，通过所有试验对被遗漏样本的比例进行平均。运行此实验可能需要一些时间，且由于抽样的随机性，你的结果可能会有所不同。以下是一些代表性输出：Out-of-boostrap: 36.8 %

## 通过交叉验证进行优化

能够有效验证机器学习假设，可进一步优化你选择的算法。以下各部分将帮助你了解如何优化交叉验证解决方案。

### 预测性能的来源

如前几部分所述，算法提供了数据中的大部分预测性能，前提是它能够从数据中检测信号，并拟合预测函数的真实函数形式，而不会过拟合并产生大量估计方差。并非每个机器学习算法都最适合你的数据，也没有单一算法能适用于每个问题。找到适合特定问题的算法取决于你。

预测性能的第二个来源是数据本身，当对其进行适当转换和选择以增强所选算法的学习能力时。[第 11 章](#c11.xhtml)讨论了数据转换和选择的问题。

预测性能的最终来源在于对算法 `hyper-parameters` 进行微调，这些是你在学习发生之前设置（配置）且不会从数据中学习到的参数。它们的作用在于 *先验地* 定义一个假设，而其他参数则 *后验地*（基于观察或经验的推理或知识）* 指定它*，在算法与数据交互后，并通过优化过程发现某些参数值在获得良好预测方面效果更好。并非所有机器学习算法都需要大量超参数调优，但一些最复杂的算法确实需要，尽管这些算法开箱即用，但找到正确的控制杆可能会对预测的正确性产生巨大影响。即使超参数不是从数据中学习的，你在决定超参数时也应该考虑你正在处理的数据，并且应该基于交叉验证和对可能性的仔细评估来做出选择。

![Remember](images/remember.png)复杂的机器学习算法，即那些最容易受到估计方差影响的算法，提供了大量以大量参数形式表达的选择。对它们进行调整，使其或多或少地适应正在学习的数据。有时，过度调整超参数甚至可能导致算法从数据中检测到虚假信号。如果你基于某个固定参考（如测试集或重复的交叉验证方案）过度操纵超参数，那么超参数本身就成为一个未被检测到的方差来源。

### 探索超参数空间

超参数可能形成的值组合使得决定在哪里寻找优化变得困难。如在讨论梯度下降时所述，优化空间可能包含表现更好或更差的值组合。即使你找到了一个好的组合，也不能保证它是最佳选择。（这是在最小化误差时陷入局部最小值的问题，该问题在 [第 8 章](#c08.xhtml) 讨论梯度下降的问题时有所描述。）

作为解决此问题的实用方法，验证应用于特定数据的算法的超参数的最佳方式是通过交叉验证测试所有超参数，并选择最佳组合。这种方法称为网格搜索（grid-search，其 Scikit-learn 实现见：[`https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GridSearchCV.html`](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GridSearchCV.html)），它具有无可争议的优势，允许你系统地采样可能输入到算法中的值范围，并发现一般最小值何时出现。另一方面，网格搜索也有严重缺点，因为它计算密集（你可以在现代多核计算机上轻松并行执行此任务）且非常耗时。此外，系统且密集的测试会增加出错的可能性，因为数据集中存在的噪声可能导致一些良好但虚假的验证结果。网格搜索有一些替代方案。与其测试所有内容，不如尝试以下方法：

*   通过计算量大且数学复杂的非线性优化技术（如 Nelder-Mead 方法）引导探索可能的超参数值空间

*   使用贝叶斯方法（通过利用之前的结果来最小化测试次数）

*   使用随机搜索。

![Tip](images/tip.png)贝叶斯优化虽然概念复杂，但在 Scikit-learn 兼容的包 Scikit-optimize 中有实现（你可以在 [`https://scikit-optimize.github.io/stable/`](https://scikit-optimize.github.io/stable/) 找到它）。你只需要安装该包并使用一个 Scikit-learn 超参数搜索包装器，例如 `BayesSearchCV`，它与 Scikit-learn 中网格搜索和随机搜索具有相同的命令语法：[`https://scikit-optimize.github.io/stable/auto_examples/sklearn-gridsearchcv-replacement.html`](https://scikit-optimize.github.io/stable/auto_examples/sklearn-gridsearchcv-replacement.html)。

令人惊讶的是，随机搜索（random-search，[`https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.RandomizedSearchCV.html`](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.RandomizedSearchCV.html））效果非常好，易于理解，而且不仅仅基于盲目运气，尽管它起初可能看起来如此。事实上，该技术的主要观点是，如果你选择足够多的随机测试，你就有足够的可能性找到正确的参数，而无需在测试表现相近的略有不同组合上浪费精力。

[第 9-5 图](#c09.xhtml#c09-fig-0005) 中显示的图形表示解释了为什么随机搜索效果良好。系统探索虽然有用，但倾向于测试每个组合，如果某些参数不影响结果，这将变成能量的浪费。随机搜索测试的组合较少，但覆盖了每个超参数的更广范围，如果（如经常发生的情况）某些参数比其他参数更重要，这种策略证明是有效的。

![FIGURE 9-5: Comparing grid-search to random-search.](images/9781119724018-fg0905.png)

[FIGURE 9-5:](#c09.xhtml#rc09-fig-0005) Comparing grid-search to random-search.

![Tip](images/tip.png)为了使随机搜索表现良好，你应该进行 15 到最多 60 次测试。如果网格搜索需要更多实验，那么采用随机搜索是有意义的。

### 选择相关特征

