

## k-Nearest Neighbor (kNN)
`k-Nearest Neighbor (kNN)` 是一种依赖于与其他对象相似度的基于对象的学习。与其他对象相近的对象被称为“邻居”。当放置一个新对象时，会确定模型中每个案例的距离。通过这种分组，案例会被指定给与其最相似的最近邻居并被放入其组中。`kNN` 方法还能够持续计算目标值。

对于连续变量，距离可以使用三种距离度量来计算，即 `Euclidean`、`Manhattan` 或 `Minkowski` 距离。而对于分类变量，则使用 `Hamming` 距离。`Euclidean` 和 `Hamming` 距离在下面的方程中给出。

(6.5)${Euclidean\, Distance} = \\ \\sqrt{\\sum\\limits\_{i = 1}^{k}\\left( {x\_{i} - y\_{i}} \\right)2}$ (6.6)${Hamming\, Distance} = \\ D\_{H =}\\sum\_{i = 1}^{k}\\left| {x\_{i} - y\_{i}} \\right|$ 

其中 `i` 指的是值分别为 1、2、3 … .`k` 的最近邻居。`x` 和 `y` 指的是变量。

`kNN` 的示意图如下所示 [Figure 6.5](#bodymatter-006.xhtml#b_9783110648195-006_fig_005)，其中令 `k` 的值为 3，因此新数据点将因最近距离而位于类别 1。

![Figure 6.5: kNN representation.](graphic/converted/b_9783110648195-006_fig_005.png)

Figure 6.5: kNN representation.

## Decision Tree (DT)
`Decision Tree (DT)` 也属于监督 ML 技术的一个类别。`DT` 的主要目的是准备一个训练模型，通过实施从训练数据中推导出的学习决策规则来帮助预测目标变量。其结构类似于流程图，由叶节点、内部节点和分支组成 ([Figure 6.6](#bodymatter-006.xhtml#b_9783110648195-006_fig_006))。对任何记录的预测总是从根节点开始。从多个变量中选择一个根变量时，使用的方法之一是信息增益。信息增益进一步衡量变量的不确定性，这被称为熵 ([Safavian and Landgrebe, 1991](#bodymatter-006.xhtml#b_9783110648195-006_ref_085))。熵和信息增益的数学方程如下所示。

![Figure 6.6: Basic structure of decision tree.](graphic/converted/b_9783110648195-006_fig_006.png)

Figure 6.6: Basic structure of decision tree.

(6.7)*H* = *E*(*S*) = ∑*I* = 1*C* − *p**i**l**o**g*2*p**i* 

其中 `pi` 指的是 `ith` 类的概率。

## Random Forest (RF)
`Random Forest (RF)` 是由 Tin Kam Ho 引入的另一种监督 ML 算法。`RF` 构建了类似森林的结构，其中包含多个决策树，独立向量被平均分配，单个树为最受投票的输入类 `x` 分配值 1（单位） ([Figure 6.7](#bodymatter-006.xhtml#b_9783110648195-006_fig_007))。`RF` 中的树越多，预测越准确 ([Breiman, 2001](#bodymatter-006.xhtml#b_9783110648195-006_ref_009))。设 `h(x|θ[1])`、`h(x|θ[2])`、…、`h(x|θ[k])` 为具有参数 `θk` 和随机向量 `θ` 的 `k` 个分类器的数量。那么第 `k` 个决策树分类器的方程为

(6.8)*h**k*(*x*)  = *h*(*x*|*θ**k*) 
![Figure 6.7: Random forest representation using decision trees.](graphic/converted/b_9783110648195-006_fig_007.png)

Figure 6.7: Random forest representation using decision trees.

## Linear Discriminant Analysis (LDA)
`Linear Discriminant Analysis (LDA)` 算法被描述为一种用于预处理和模式分类问题的降维方法。其主要目的是通过将变量从多维空间转移到较小维空间来减少维度。它类似于主成分分析 (`PCA`) 算法，但使用的是标记数据 (Zhao et al., 1998)。`LDA` 输出分类(`y`) 是使用判别函数给出的，并在 ([Figure 6.8](#bodymatter-006.xhtml#b_9783110648195-006_fig_008)) 中说明。

![Figure 6.8: LDA process to maximize component axes between two classes.](graphic/converted/b_9783110648195-006_fig_008.png)

Figure 6.8: LDA process to maximize component axes between two classes.

(6.9) ${Dk}\\left( x \\right) = x^{\\ast}\\left( \\frac{muk}{{sig}a^{2}} \\right) - \\left( \\frac{muk}{{sig}a^{2}} \\right){+ ln}\\left( {Plk} \\right)$ 

其中 `Dk(x)` 指的是类别 `k` 的判别函数，变量 `Plk`、`sigma^2` 和 `muk` 是从给定数据计算得出的变量值。

## Logistic Regression (LR)
`Logistic Regression (LR)` 是统计学领域常用的另一种监督 ML 技术。`LR` 的名称源自称为逻辑函数的函数 ([Cook, 1977](#bodymatter-006.xhtml#b_9783110648195-006_ref_019))。为了给出二元输出（0 或 1），该算法使用 `x` 输入值与系数值的线性组合。逻辑回归的方程如下：

(6.10)*y*\=*e*^∧(*b*0 + *b*1^(*x*))/(1+*e*^∧(*b*0 + *b*1 \* *x*)) 

其中输出由 `y` 表示，`b0` 指截距词，`b1` 指系数，`x` 指输入变量。逻辑回归的曲线如下图所示 ([Figure 6.9](#bodymatter-006.xhtml#b_9783110648195-006_fig_009))。

![Figure 6.9: Logistic regression curve.](graphic/converted/b_9783110648195-006_fig_009.png)

Figure 6.9: Logistic regression curve.

## Gaussian Process
`Gaussian Process` 被定义为解决回归和分类两个问题的算法。该算法在监督学习中非常有用，因为它可以给出其自身不确定性的估计。它是一种随机过程，仅在有限变量集上工作 ([Rasmussen, 2003](#bodymatter-006.xhtml#b_9783110648195-006_ref_079))。满足高斯过程的方程如下。

(6.11)$E\\left( {{exp}\\left( {i\\sum\\limits\_{l - 1}^{k}s\_{l}X\_{t\_{l}}} \\right)} \\right) = {exp}\\,\\left( \\left. {- \\frac{1}{2}\\,\\sum\\limits\_{lj}{\\sigma\_{l\_{j}}s\_{l}s\_{j + i}\\,\_{\\sum\\limits\_{l}{\\mu\_{l}s\_{l}}}}} \\right) \\right.\\,$ 

其中 `t[1]`、`t[2]`、… ..、`t[k]` 是有限变量，`μ[l]` 是变量的均值，`σ[l[j]]` 是协方差，其中 `σ[jj]` > 0 且 `s[1]`、`s[2]`、… …、`s[k]` € R。高斯过程的曲线在下图中给出 ([Figure 6.10](#bodymatter-006.xhtml#b_9783110648195-006_fig_010))。

![Figure 6.10: Gaussian process curve.](graphic/converted/b_9783110648195-006_fig_010.png)

Figure 6.10: Gaussian process curve.

## Ensemble Learning
`Ensemble Learning`，也称为元算法，将多个机器学习算法合并为一个准确的模型，以便减少 boosting、bagging 或 stacking。该算法基本上分为两类——顺序集成方法和并行集成方法 ([Dietterich, 2002](#bodymatter-006.xhtml#b_9783110648195-006_ref_023))。使用许多常见的集成类型，例如 Bootstrap 聚合、Boosting、贝叶斯最优分类器等。集成的一种类型，即贝叶斯最优分类器，由以下方程表示。

(6.12)*y* = *a**r**g**m**a**x*[*c*[*j*] ∈ *C*]∑[*h*[*i*] ∈ *H*]*P*(*c*[*j*]|*h*[*i*])*P*(*T*|*h*[*i*])*P*(*h*[*i*]) 

其中 `y` 是被预测的输出标签，`C` 是可能结果的组，`H` 是假设空间，`P` 指似然，`T` 指用于训练的数据。集成学习的框图在 ([Figure 6.11](#bodymatter-006.xhtml#b_9783110648195-006_fig_011)) 中给出。

![Figure 6.11: Block diagram of ensemble learning.](graphic/converted/b_9783110648195-006_fig_011.png)

Figure 6.11: Block diagram of ensemble learning.

