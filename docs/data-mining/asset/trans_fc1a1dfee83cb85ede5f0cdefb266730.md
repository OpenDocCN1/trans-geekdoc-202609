
`K2` 算法用于学习贝叶斯网络由 [Cooper 和 Herskovits (1992)](#References_705-736_B978044315888900025X.xhtml#fur111) 引入。贝叶斯评分指标由 [Heckerman 等 (1995)](#References_705-736_B978044315888900025X.xhtml#fur259) 涵盖。[Friedman、Geiger 和 Goldszmidt (1997)](#References_705-736_B978044315888900025X.xhtml#fur198) 引入了树增强朴素贝叶斯算法并同时描述了多网络。[Grossman 和 Domingos (2004)](#References_705-736_B978044315888900025X.xhtml#fur236) 展示了如何使用条件似然对网络进行评分。[Guo 和 Greiner (2004)](#References_705-736_B978044315888900025X.xhtml#fur239) 提出了贝叶斯网络分类器评分指标的广泛比较。[Bouckaert (1995)](#References_705-736_B978044315888900025X.xhtml#fur55) 描述了子网络的平均。`AODEs` 由 [Webb、Boughton 和 Wang (2005)](#References_705-736_B978044315888900025X.xhtml#fur555) 描述，而 `AnDEs` 由 [Webb 等 (2012)](#References_705-736_B978044315888900025X.xhtml#fur556) 描述。`AD trees` 由 [Moore 和 Lee (1998)](#References_705-736_B978044315888900025X.xhtml#fur403) 引入并分析——同 Andrew Moore，其关于 `kD-trees` 和球树的著作在 [第 4.10 节](#Ch004_91-164_B9780443158889000054_a.xhtml#s0200) 中提到。[Komarek 和 Moore (2000)](#References_705-736_B978044315888900025X.xhtml#fur326) 引入了用于增量学习的 `AD trees`，对于具有许多属性的数据集也更高效。

`AutoClass` 程序由 [Cheeseman 和 Stutz (1995)](#References_705-736_B978044315888900025X.xhtml#fur91) 描述。已产生两种实现：原始研究实现，使用 `LISP`（“list processing”）编程语言编写，以及后续的公共实现，使用 `C` 编写，速度快 10 到 20 倍，但限制稍多——仅对数值属性实现了正态分布模型。`DensiTrees` 由 [Bouckaert (2010)](#References_705-736_B978044315888900025X.xhtml#fur57) 开发。

核密度估计是一种有效且概念上简单的概率模型。[Epanechnikov (1969)](#References_705-736_B978044315888900025X.xhtml#fur160) 证明了在均方误差度量下 `Epanechnikov` 核的最优性。[Jones、Marron 和 Sheather (1996)](#References_705-736_B978044315888900025X.xhtml#fur297) 建议使用所谓的“plug-in”估计来选择核带宽。[Duda 和 Hart (1973)](#References_705-736_B978044315888900025X.xhtml#fur148) 和 [Bishop (2006)](#References_705-736_B978044315888900025X.xhtml#fur44) 从理论上证明，随着数据量的增长，核密度估计会收敛到真实分布。

## 13.5 练习

*   13.1 最大似然估计使似然函数 `L`(`θ`; `x[1]`, `x[2]`, …, `x[n]`)<mml:math><mml:mi>L</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mi>&#952;</mml:mi><mml:mi>;</mml:mi><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mn>1</mml:mn></mml:mrow></mml:msub><mml:mo>,</mml:mo><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mn>2</mml:mn></mml:mrow></mml:msub><mml:mo>,</mml:mo><mml:mo>&#8230;</mml:mo><mml:mo>,</mml:mo><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mi>n</mml:mi></mml:mrow></mml:msub><mml:mo stretchy="false">)</mml:mo></mml:math>![方程](images/F000145si87.png) 相对于 _____ 最大化。

    1.  A. 数据 `x[1]`, `x[2]`, …, `x[n]`<mml:math><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mn>1</mml:mn></mml:mrow></mml:msub><mml:mo>,</mml:mo><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mn>2</mml:mn></mml:mrow></mml:msub><mml:mo>,</mml:mo><mml:mo>&#8230;</mml:mo><mml:mo>,</mml:mo><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mi>n</mml:mi></mml:mrow></mml:msub></mml:math>![方程](images/F000145si88.png)

    2.  B. 参数 `θ`<mml:math><mml:mi mathvariant="normal">&#952;</mml:mi></mml:math>![方程](images/F000145si89.png)

*   13.2 最大化似然函数等价于最小化对数似然函数。

    1.  A. 真

    2.  B. 假

*   13.3 贝叶斯网络被绘制为节点的网络，每个属性一个节点，其中网络是一个 _____。

    1.  A. 二部图

    2.  B. 完全图

    3.  C. 有向无环图

    4.  D. 最小权重生成树

*   13.4 考虑 [图 13.3](#Ch014_485-514_B9780443158889000145.xhtml#f0020) 中的图。（忽略框，它表示节点 `x[6]`<mml:math><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mn>6</mml:mn></mml:mrow></mml:msub></mml:math>![方程](images/F000145si90.png) 的马尔可夫毯。）

    1.  1. 写下此贝叶斯网络模型的联合分布。（请记住 $P(A_{1},A_{2},\\ldots,A_{n}) = \\prod\\limits_{i = 1}^{n}{P(A_{i}\\text{∣}{Parents}(A_{i}))},$<mml:math><mml:mi>P</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:msub><mml:mrow><mml:mi>A</mml:mi></mml:mrow><mml:mrow><mml:mn>1</mml:mn></mml:mrow></mml:msub><mml:mo>,</mml:mo><mml:msub><mml:mrow><mml:mi>A</mml:mi></mml:mrow><mml:mrow><mml:mn>2</mml:mn></mml:mrow></mml:msub><mml:mo>,</mml:mo><mml:mo>&#8230;</mml:mo><mml:mo>,</mml:mo><mml:msub><mml:mrow><mml:mi>A</mml:mi></mml:mrow><mml:mrow><mml:mi>n</mml:mi></mml:mrow></mml:msub><mml:mo stretchy="false">)</mml:mo><mml:mo>=</mml:mo><mml:munderover><mml:mo>&#8719;</mml:mo><mml:mrow><mml:mi>i</mml:mi><mml:mo>=</mml:mo><mml:mn>1</mml:mn></mml:mrow><mml:mrow><mml:mi>n</mml:mi></mml:mrow></mml:munderover><mml:mrow><mml:mi>P</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:msub><mml:mrow><mml:mi>A</mml:mi></mml:mrow><mml:mrow><mml:mi>i</mml:mi></mml:mrow></mml:msub><mml:mtext mathvariant="normal">&#8739;</mml:mtext><mml:mi mathvariant="normal">Parents</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:msub><mml:mrow><mml:mi>A</mml:mi></mml:mrow><mml:mrow><mml:mi>i</mml:mi></mml:mrow></mml:msub><mml:mo stretchy="false">)</mml:mo><mml:mo stretchy="false">)</mml:mo></mml:mrow><mml:mo>,</mml:mo></mml:math>![方程](images/F000145si91.png) 对所有贝叶斯网络成立。）

    2.  2. 节点 `x[9]`<mml:math><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mn>9</mml:mn></mml:mrow></mml:msub></mml:math>![方程](images/F000145si92.png) 的条件概率表中共有多少行？假设所有变量都是二元的，取值在 {0, 1}<mml:math><mml:mo stretchy="false">{</mml:mo><mml:mn>0,1</mml:mn><mml:mo stretchy="false">}</mml:mo></mml:math>![方程](images/F000145si93.png) 中。

    3.  3. `x[3]`<mml:math><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mn>3</mml:mn></mml:mrow></mml:msub></mml:math>![方程](images/F000145si94.png) 的马尔可夫毯中包含哪些节点？

    4.  4. `x[5]`<mml:math><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mn>5</mml:mn></mml:mrow></mml:msub></mml:math>![方程](images/F000145si95.png) 的马尔可夫毯中包含哪些节点？

*   13.5 为学生在数据挖掘课程中获得的成绩设计一个贝叶斯网络。

    1.  1. 你的模型中的节点/变量是什么？

    2.  2. DAG 结构是什么？

    3.  3. 你的 DAG 中的条件独立性是否与你对世界的直觉相符？

*   13.6 在我设计的一个掷骰子游戏中，目标是从几次掷骰中获得较高的总和。首先，玩家掷一次骰子。如果掷骰结果为偶数和/或玩家年龄最多为 7 岁，他们会再次掷骰子。如果他们年龄大于 7 岁，且前两次掷骰都为偶数，玩家会第三次掷骰子。玩家的得分是所有掷骰结果的总和。我们假设 10% 的人口年龄最多为 7 岁。骰子是标准的，即六面且无偏。
