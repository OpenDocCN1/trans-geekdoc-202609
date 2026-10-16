
![](img/d94e4cd766940d79abed0bc6ba4e4344_316_0.png)

并且它有一个目标值为

```
In [51]:

digits.target[0]

Out[51]:

0
```

数据集有两种形式。一种（digits.images）适用于显示目的；我刚才就是用它。另一种（digits.data）适用于学习使用。这种形式是 64 × 64 图像中信息的扁平化行。

现在我们可以构建我们的学习问题。

```
In [52]:

classifier_parade = \
{ 'LogReg(1)' : linear_model.LogisticRegression(max_iter=1000),
  'LogReg(2)' : linear_model.SGDClassifier(loss='log',
                            max_iter=1000),

  'QDA' : discriminant_analysis.QuadraticDiscriminantAnalysis(),
  'LDA' : discriminant_analysis.LinearDiscriminantAnalysis(),
  'GNB' : naive_bayes.GaussianNB(),

  'SVC(1)' : svm.SVC(kernel="linear"),
  'SVC(2)' : svm.LinearSVC(),

  'DTC' : tree.DecisionTreeClassifier(),
  '5NN-C' : neighbors.KNeighborsClassifier(),
  '10NN-C' : neighbors.KNeighborsClassifier(n_neighbors=10)}
```

```
baseline = dummy.DummyClassifier(strategy="uniform")

base_score = skms.cross_val_score(baseline,
    digits.data, digits.target==1,
    cv=10,
    scoring='average_precision',
    n_jobs=-1)
```

我们使用交叉验证在 digits 数据集上评估我们的解决方案。

In [53]:

```
fig, ax = plt.subplots(figsize=(6,4))
ax.plot(base_score, label='base')
for name, model in classifier_parade.items():
    cv_scores = skms.cross_val_score(model,
        digits.data, digits.target,
        cv=10,
        scoring='f1_macro',
        n_jobs=-1) # all CPUs
    my_lbl = "{} ({:.3f})".format(name, cv_scores.mean())
    ax.plot(cv_scores, label=my_lbl, marker=next(markers))
ax.set_ylim(0.0, 1.1)
ax.set_xlabel('Fold')
ax.set_ylabel('Accuracy')
ax.legend(loc='lower center', ncol=2);
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_317_0.png)

坦白说，这里发生的事情实在太多，很难简要概括。尽管如此，仍有一些总体趋势。你可以看到，经典方法逻辑回归与非常现代的方法 SVCs 竞争得相当不错。而我们极其简单的最近邻方法表现甚至更好。将不同分类器在不同指标上进行比较是很好的练习。你可能也对比较这些方法在 digits 上的资源利用感兴趣。

## 8.8 章末

### 8.8.1 摘要

我们现在已向分类工具箱中添加了多种方法。决策树是高度灵活的模型，可找到空间中的共同区域。逻辑回归和判别分析变体使用数据的不同概率模型为类别分配似然。支持向量分类器直接寻找类别之间的线性分离。加上朴素贝叶斯和最近邻，我们有八种不同的分类器可以使用。

我们如何选择？有时外部因素决定了我们的选择。决策树通常可被人类阅读。逻辑回归模型可以解释为基于变量值的对数几率变化。SVCs？SVCs 并不能以相同的方式进行解释。我们可以使用它们，但它们内部的黑箱有很多东西。现在，即使我们知道需要使用 DT 来理解，我们仍可能拟合其他模型，以查看 DT 的性能与其它酷孩子相比如何。

### 8.8.2 注释

存在“没有一种方法可以统治一切（并且在黑暗中束缚它们）”的想法被称为没有免费午餐定理。我更喜欢“没有一枚魔戒定理”，但可惜，他们没有征求托尔金或我的意见。

## 决策树

虽然我们谈到决策树导致一个类别，但我们也可以询问叶节点处的概率分布。然后，如果我们愿意，可以掷硬币来获得与每个叶节点处所见相似的分布。如果我们不想，我们不必做出具体的决定。

回答中途测验题：“随着最大深度的增加，我们是在走向过拟合还是欠拟合？”答案是过拟合。

树的一些特征并非 DT 的根本特征——它们只是事情的现状。例如，我们可以允许决策基于特征的函数做出。举例来说，这将允许非平行或非垂直的值分割。不要在 x > 5 上分割，我们可以在 2x + 3 > 5 上分割：我们现在有一个偏轴比较。我们也可以允许类似“颜色是否在 {red, blue, green}?”（否）的比较。我们可以用一系列二元问题来捕捉这种关系：是红色吗？（否），是绿色吗？（否），是蓝色吗？（否）。但这会以细分可能本来就数据稀少区域为代价。表达力与冗长性之间存在权衡，不同作者对此意见不一。我采取务实的方法：如果认为需要花哨的技术，就试试——然后进行交叉验证。

如果你碰巧是一位更高级的读者正在阅读本书，你可能对一篇最近（2015 年）的论文感兴趣：*Efficient non-greedy optimization of decision trees* 由 Norouzi 和朋友撰写。我在本章中描述的树构建方法都是*greedy*：它们采取看起来最好的单个步骤。但当然，没有整体地图，单个步骤可能会让你走偏。那篇论文描述了一种非贪婪的构建树的方法。

## SVCs

我们将在第 13 章中更多地讨论 SVM 的一些最酷的方面。简要地说，我们通过引入一个*kernel*从 SVC 移动到 SVM。为了让你度过难关，我会提到 `sklearn` 有一个接口到 `liblinear`，这是一个非常强大的程序，用于计算 SVCs（线性 SVM）以及逻辑回归模型。至少，要像上面使用的一样作为标准 SVC 运行，你会像这样进行调用：`svm.LinearSVC(loss='hinge')`。`LinearSVC` 在处理大型数据集（大于约 10,000 个示例）时有一些不错的好处。

`SVC` 和 `NuSVC` 在内部使用另一个程序，`libsvm`。`libsvm` 是机器学习社区中我们拥有的最接近 SVCs 和 SVMs 的*de facto* 标准实现。当谈到 `NuSVC` 时，人们经常犯的错误是就*training errors*谈论 *ν*。*ν* 与*margin errors*相关。*ν is not* 直接与训练误差相关。如果你想自己看看，请阅读 Scholkopf 的 *New Support Vector Algorithms* 第 1225–1226 页。

试图让 `LinearSVC` 和 `SVC` 和 `NuSVC` 产生相同的边界是相当困难的。`libsvm` 和 `liblinear` 在数学和计算角度上做的事情略有不同。至少，`LinearSVC` 在执行*regularization*时会包含 +1 技巧列。此外，`LinearSVC` 和 `SVC` 在底层默认值之上放置了自己的默认值。如果你想进行比较，请准备好深入挖掘。这些可能会让你入门：

- https://stackoverflow.com/a/23507404/221602
- https://stackoverflow.com/q/33843981/221602
- https://stackoverflow.com/q/35076586/221602

## 逻辑回归

数学清晰度有时可能相当晦涩。例如，以下方程 $\frac{1}{1+e^{-x}} = \frac{e^{x}}{1+e^{x}}$ 导致了两种看起来相当不同的写出逻辑函数的方式。进而，这可能导致表达逻辑回归的不同方式。祝好运。

逻辑回归的假设与线性回归的假设密切相关，除了线性关系是在目标类别的对数几率与输入特征之间。否则，我们仍然需要误差表现良好，并且需要避免特征中的冗余。详见第 10 章。

我们还没有真正解决*如何*逻辑回归工作的。我们解释了对数几率并从中构建了一个类似线性回归的模型，但是什么让它运转？寻找答案的经典方法——最佳系数——称为*iteratively reweighted least squares*（IRLS）。基本上，它遵循经典线性回归的相同方法，但必须多次重复该过程。该过程最终等价于*Newton’s Method*：如果我在山上，朝着我穿过 *x* 轴的地方瞄准，通过指向下坡并根据斜率的陡峭程度朝它迈出一步。Newton’s Method 被称为二阶方法，因为我们需要在函数中找到极值点——它处于峰值或谷值——为此我们需要找到将我们带到该点的斜率。所以，我们有点需要斜率的斜率——因此“二阶”或如果你熟悉的话“二阶导数”。另一大类方法称为*Gradient Descent*，基本上说：让自己朝下坡方向瞄准并迈出小步。

`statsmodels` 方法我们也在上面使用，使用了老式的 IRLS 技术。我们可以在 `sklearn` 中以几种方式执行逻辑回归。`liblinear` 使用一种非常花哨的 Newton’s Method 版本，称为 Trust Region Newton’s Method。那是 `LogisticRegression` 的默认调用。`SGDClassifier` 使用一种快速的梯度下降版本，在每次下坡时并不处理*all* 的数据。`LogisticRegression` 的 `saga` 参数使用一个——惊喜！——SAGA 方法，其表现类似于 SGD，但也会记住之前步骤的一些历史。梯度下降在每一步都使用所有数据，而随机梯度下降在每一步使用一些或仅一个示例，SAGA 在使用仅部分数据进行每一步的同时记住一些步骤的历史。

更令人不安的是，你可能已经注意到我们没有讨论逻辑回归中的偏差和方差的作用。我们将在第 15 章重新审视这个问题。

## 判别分析方法

冒犯我统计学家朋友的风险，我草率地忽略了一些关于方差的细节。实际上，我们讨论的是总体方差或有偏样本方差。处理有偏性有几种不同的方法；最常见的是除以 *n* − 1 而不是 *n*。

我必须感谢 StackOverflow 的一位成员 *whuber*，他的一条评论和图形引起了我对探索协方差的图形方法的注意。你可以在这里看到它：https://stats.stackexchange.com/a/182090/1704。追踪这些想法让我找到 Hayes 于 2011 年发表的一篇文章，题为“A Geometrical Interpretation of an Alternative Formula for the Sample Covariance。”

有许多方法可以将不同方法相互关联。例如，一种称为*Nearest Shrunken Centroids*（NSC）的技术与 DLDA 相关：如果对数据进行中心化和标准化然后执行 NSC，你应该得到的结果等价于正则化（平滑）DLDA 的一种形式。参见 Hastie 和朋友的 *Elements of Statistical Learning*，第二版，第 651 页。正如始终一样，可能存在数学和实现差异，阻止你实现完全等价。作为说明，`sklearn` 当前（截至 2019 年 5 月）的 `NearestCentroids` 实现并未完全考虑距离度量，并且不会完全解决这个问题。

如果你熟悉朴素贝叶斯，并想知道为什么它被称为线性方法，原因在于对于*discrete*——技术上是*multinomial*——朴素贝叶斯，创建的边界是线性的。然而，对于*continuous*——技术上是 Gaussian——朴素贝叶斯，如本章所述，边界不是线性的。
