
构建 SOM 的第一步是初始化权重向量。从那里，你随机选择一个样本向量，并在权重向量图中搜索，找到哪个权重最能代表该样本。由于每个权重向量都有一个位置，因此靠近它的权重也是它的邻居。被选中的权重将获得奖励，使其变得更像随机选择的样本向量。除了这种奖励，该权重的邻居也会获得奖励，使其变得更像被选中的样本向量。从这一步开始，我们增加 `t` 的值，因为邻居的数量以及每个权重可以学习的量会随着时间减少。这个过程会重复多次，通常超过 1000 次。

在颜色的情况下，程序会首先从样本数组中选择一种颜色（例如绿色），然后搜索权重找到包含最绿色的位置。从那里，该权重周围的颜色将变得更绿。然后选择另一种颜色（如红色），继续该过程。这些过程是：

## A. 初始化权重

这里是初始化权重向量图的三种不同方法的截图。我们应该首先提到这里的调色板。在下面的 `Java` 程序中，显示了 6 种强度的红、蓝、绿，这实际上并不影响视觉体验。权重的实际值是浮点数，因此它们的范围比图 7 中显示的六个值大。

![](img/e1ab17402154bec3fa9a7873fe3ee232_71_0.png)

图 8：权重值。

初始化权重向量有多种方法。你可以看到的第一种是给每个权重向量的数据赋予随机值。左上方显示了一个具有随机红、蓝、绿值的像素屏幕。不幸的是，根据 Kohonen 的算法（Kohonen, 1997）计算 SOM 计算开销非常大，因此有一些权重初始化变体，以确保你已知不相似的样本离得很远。这样你只需要较少的迭代就能生成良好的映射，并节省一些时间。

除了随机初始化外，我们在这里还另外两种初始化权重的方法。这种方法仅仅是将红、蓝、绿、黑放在四个角，并让它们向中心逐渐淡出。另一种方法是让红、绿、蓝彼此之间以及与中心的距离相等。

# 机器学习算法类型 47

## B. 获取最佳匹配单元 (BMU)

这是一个非常简单的步骤，只需遍历所有权重向量，计算每个权重到所选样本向量的距离。距离最短的权重就是胜者。如果有多个权重距离相同，则在距离最短的权重中随机选择一个获胜者。确定其数学含义有多种不同的方法。最常用的方法是使用欧几得距离：

```
\sum_{i=0}^{n} x_i^2
```

其中 `x[i]` 是样本中第 `i` 个数据成员的值，`n` 是样本向量的维度数。

在颜色的情况下，如果我们选择了绿色，我们可以将值看作 3D 点，每个点都是一个轴。浅绿色 (3,6,3) 比位于 (0,6,0) 的红色更接近绿色。

浅绿 = Sqrt(3-0)^2+(6-6)^2+(3-0)^2 = 4.24

红色 = Sqrt(6-0)^2+(0-6)^2+(0-0)^2 = 8.49

因此绿色现在是最佳匹配单元，但计算距离并比较距离的操作是在整个映射上进行的，距离样本向量最短的权重即为胜者，也是 BMU。为了在该部分优化速度，`Java` 程序在这一部分没有计算平方根。

## C. 缩放邻居

### 1. 确定邻居

缩放邻居权重实际上有两个部分：确定哪些权重被视为邻居，以及每个权重可以变得多像样本向量。获胜权重的邻居可以使用许多不同的方法确定。是一些同心正方形，另一些六边形，我选择使用高斯函数，将每个值大于零的点都视为邻居。

如前所述，邻居的数量随着时间的推移而减少。这样做是为了让样本首先移动到它们可能所在的区域，然后它们竞争位置。这个过程类似于粗调后进行精调。用于减少影响半径的函数并不重要，只要它在减少即可，我们只是使用了一个线性函数。

![](img/e1ab17402154bec3fa9a7873fe3ee232_73_0.png)

`f := (x, y) → e^{-6.6666666667 sqrt{x^2+y^2}}`

**图 9**：邻居确定的图。

图 8 显示了所使用的函数。随着时间的推移，基底向中心移动，因此邻居减少。初始半径设置得很高，接近映射的宽度或高度。

### 2. 学习

缩放邻居的第二部分是学习函数。获胜权重被奖励变得更像样本向量。邻居也会变得更像样本向量。这种学习过程的一个属性是，邻居离获胜权重越远，学习得就越少。这可以设置为任何你想要的。我选择使用高斯分布。该函数将返回一个介于 0 和 1 之间的值，每个邻居随后使用参数方程进行更改：

当前颜色*(1-`t`) + 样本向量*`t`

因此在第一次迭代中，最佳匹配单元的 `t` 为 1，因此该权重在该过程结束后具有与随机样本相同的值。就像邻居的数量会减少一样，权重可以学习的量也会随着时间而减少。在第一次迭代中，获胜权重变为样本，`t` 的完整范围为 0 到 1。随着时间的推移，获胜权重变得稍微像样本，`t` 的最大值减小。权重可以学习的速率会下降。为了视觉化表示这一点，在之前的图中，权重可以学习的量等于它们所在位置的高度。随着时间的推移，高度会降低，而基底会缩小。

因此，一旦确定了胜者，就会找到该权重的邻居，每个邻居以及获胜权重在内都会变得更像样本。

## 机器学习算法类型

## 确定 SOM 的质量

图 9 是程序使用 500 次迭代生成的另一个 SOM 示例。从乍看，你会注意到相似的颜色聚集在一起。然而，事实并非总是如此，正如你看到的，有些颜色被与它们完全不像的颜色所包围。对于颜色来说，这一点可能很容易指出，因为我们熟悉它；但如果我们使用更抽象的数据，我们该如何知道两个实体彼此靠近是意味着它们相似，还是仅仅是因为运气不好才在那里呢？

有一种非常简单的方法可以显示相似性在哪里，在哪里不存在。为了计算这一点，我们遍历所有权重

# 使用 Python 进行 50 软计算与机器学习

并确定邻居之间的相似性。这是通过计算权重向量与其每个邻居之间的距离来实现的。通过这些距离的平均值为该位置分配颜色。该过程位于 `Screen.java` 中，命名为 `public update_bw()`。

如果平均距离很大，说明周围的权重差异很大，则为权重位置分配深色。如果平均距离较小，则分配较浅的颜色。因此，在斑块中心颜色相同的区域，由于所有邻居的颜色相同，那里应该是白色的。在斑块之间存在相似性的区域，它们不应该是白色，而是浅灰色。在斑块物理上接近但完全不相似的区域，应该是黑色的。见下方的图 8

![](img/e1ab17402154bec3fa9a7873fe3ee232_75_0.png)

**图 11：** 权重颜色分配示例。

如上所示，黑色通道显示了地图上的颜色在物理上可能接近，但在权重实际值方面它们彼此非常不同。斑块之间的浅灰色区域代表真实的相似性。在上面的图片中，右下角的黑色被与其不相似的颜色包围。观察黑白相似性可以发现，黑色与其他颜色不相似，因为有黑色线条代表这两种颜色之间没有相似性。此外，在顶角有粉红色，附近是浅绿色，它们在现实中并不接近，但在彩色的 SOM（自组织映射）上是相邻的。观察黑白 SOM，它通过在两种颜色之间插入黑色清楚地显示了它们并不非常相似。

通过使用这些平均距离来制作黑白地图，我们实际上可以通过简单地相加这些平均值为每个 SOM 分配一个值，该值决定了图像表示样本相似性的优劣。

## 机器学习算法的类型

# SOM 的优点与缺点

自组织映射（SOM）具有以下优点：

- SOM 可能是最优点的一点是它们非常易于理解。它非常简单：如果它们靠在一起并且有灰色连接它们，那么它们就是相似的；如果它们之间有黑色沟槽，那么它们就是不同的。与多维缩放（Multidimensional Scaling）或 N-land 不同，人们可以迅速学会如何有效地使用它们。
- 另一个很棒的一点是它们工作效果非常好。正如我向你展示的，它们能很好地分类数据，然后很容易对其质量进行评估，因此你实际上可以计算地图有多好以及对象之间的相似性有多强。

这些是缺点：

- SOM 的一个问题是获取正确的数据。遗憾的是，你需要每个样本每个成员的每个维度的取值来生成地图。有时这仅仅是不可行的，而且获取所有这些数据通常非常困难，这是使用 SOM 的一个局限性特征，通常被称为“数据缺失”。
- 另一个问题是每个 SOM 都是不同的，并在样本向量之间发现不同的相似性。SOM 组织样本数据，使得在最终结果中样本通常被相似的样本包围，然而相似的样本并不总是相邻。如果你有很多种不同的紫色，并不总是能得到一个包含所有紫色的单一大聚类，有时聚类会被分裂，产生两组紫色。通过颜色我们可以看出两个聚类看起来完全不相关。因此，需要构建许多地图才能得到一张最终的优质地图。
- SOM 的最后一个主要问题是它们的计算开销很大，这是一个很大的缺点，因为随着数据维度的增加，降维可视化技术变得越来越重要，但遗憾的是时间也随之增加。为了计算那张黑白地图，用于计算距离的邻居越多，得到的相似地图越好，但算法需要计算的距离数量呈指数级增长。

## 参考文献

- 1. Allix, N. M. (2003, April). Epistemology And Knowledge Management Concepts And Practices. Journal of Knowledge Management Practice.
- 2. Alpaydin, E. (2004). Introduction to Machine Learning. Massachusetts, USA: MIT Press.
- 3. Anderson, J. R. (1995). Learning and Memory. Wiley, New York, USA.
- 4. Anil Mathur, G. P. (1999). Socialization influences on preparation for later life. Journal of Marketing Practice: Applied Marketing Science , 5 (6,7,8), 163 - 176.
- 5. Ashby, W. R. (1960). Design of a Brain, The Origin of Adaptive Behaviour. John Wiley and Son.
- 6. Batista, G. & C. (2003). An Analysis of Four Data Treatment Methods for Supervised Learning. Applied Artificial Intelligence , 17, 519-533.
- 7. Bishop, C. M. (1995). Neural Networks for Pattern Recognition. Oxford, England: Oxford University Press.
- 8. Bishop, C. M. (2006). Pattern Recognition and Machine Learning (Information Science and Statistics). New York, New York: Springer Science and Business Media.
- 9. Block H, D. (1961). The Perceptron: A Model of Brain Functioning. 34 (1), 123-135.
- 10. Carling, A. (1992). Introducing Neural Networks.
- 11. D. Michie, J. (1994). Fundamentals of Neural Networks.
- 12. Faustett, R. (1994). Machine Learning.
- 13. Forsyth, R. S. (1990). The strange story of the Perceptron. Artificial Intelligence , 4 (3), 147-155.
- 14. Friedberg, A. (1958). A learning machine.
- 15. Gahramani, Z. (2008). Unsupervised learning algorithms are designed to extract structure from data.
- 16. Gillies, D. (1996). Self-Organizing Maps.

 Machine Learning
- 17. Haykin, S. (1994). Neural Networks: A Comprehensive Foundation.
- 18. Hodge, V. A. (2004). A Survey of Outlier Methodologies. Artificial Intelligence Review , 22 (2), 85-126.
- 19. Holland, J. (1980). Adaptive Algorithms.
- 20. Hunt, E. B. (1996). Experiment in Induction.
- 21. Ian H. Witten, E. F. (2005). Data Mining Practical Machine Learning and Techniques (Second edition ed.).
- 22. Jaime G. Carbonell, R. (1983). A Historical and Methodological Analysis. Association for the Advancement of Artificial Intelligence , 4 (3), 1-10.
- 23. Kohonen, T. (1997). Self-Organizing Maps.
- 24. Luis Gonzalez, L. (2005). Unified dual for bi-class SVM approaches. Pattern Recognition , 38 (10), 1772-1774.
- 25. McCulloch, W. S. (1943). A logical calculus of the ideas immanent in nervous activity. Bull. Biophysics , 115-133.
- 26. Mitchell, T. M. (2006). The Discipline of Machine Learning. Machine Learning Department technical report CMU-ML-06-108, Carnegie Mellon University.
- 27. Mooney, R. J. (2000). Language in Logic. In L. N. Science, Learning for Semantic Interpretation: Scaling without Dumbing Down (pp. 219-234). Springer Berlin / Heidelberg.
- 28. Mostow, D. (1983). Transforming declarative advice into effective procedures in I.. S. Michalalski, Tioga Press.
- 29. Nilsson, N. J. (1982). Principles of Artificial Intelligence (Symbolic Computation / Artificial Intelligence). Springer.
- 30. Oltean, M. (2005). Evolving Evolutionary Algorithms Using Linear Genetic Programming, 13 (3), 387-4.
- 31. Orlitsky, A., Santhanam, N., Viswanathan, K., & Zhang, J. (2005). Convergence of profile based estimators. Proceedings of International Symposium on Information Theory. Proceedings. International Symposium on, pp. 1843 - 1847. Adelaide, Australia: IEEE.
- 32. Patterson, D. (1996). Artificial Neural Networks. Singapore: Prentice

## 基于 Python 的软计算与机器学习

- 33. R. S. Michalski, T. J. (1983). 从观察中学习：概念性聚类。TIOGA Publishing Co.
- 34. Rajesh P. N. Rao, B. A. (2002). 大脑的概率模型。MIT Press。
- 35. Rashevsky, N. (1948). 数学生物物理：生物学的物理-数学基础。芝加哥：大学大学出版社。
- 36. Richard O. Duda, P. E. (2000). 模式分类（第2版）。
- 37. Richard S. Sutton, A. G. (1998). 强化学习。MIT Press。
- 38. Ripley, B. (1996). 模式识别与神经网络。Cambridge University Press。
- 39. Rosenblatt, F. (1958). 感机：一种用于大脑信息存储和组织的概率模型。心理学评论, 65 (6), 386-408。
- 40. Russell, S. J. (2003). 人工智能：一种现代方法（第2版）。美国新泽西州上河市：Prentice Hall。
- 41. Ryszard S. Michalski, J. G. (1955). 机器学习：一种人工智能方法（第一卷）。Morgan Kaufmann。
- 42. Ryszard S. Michalski, J. G. (1955). 机器学习：一种人工智能方法。
- 43. Selfridge, O. G. (1959). 狂热主义：一种学习范式。思维过程的机械化。H.M.S.O., 伦敦。伦敦。
- 44. Sleeman, D. H. (1983). 为智能CAI 推断学生模型。机器学习。Tioga Press, s: ACM Press。
