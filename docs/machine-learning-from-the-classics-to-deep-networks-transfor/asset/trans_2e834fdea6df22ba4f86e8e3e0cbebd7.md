
$p(\mathbf{\theta}|\mathbf{\alpha}) = \prod\limits_{k = 0}^{K - 1}\mathcal{N}(\theta_{k}|0,\alpha_{k}^{- 1})$

![Equation](images/B9780443292385000196/si79.png)(13.23)

$p(\mathbf{\alpha}) = \prod\limits_{k = 0}^{K - 1}{\text{Gamma}}(\alpha_{k}|a,b)$

![Equation](images/B9780443292385000196/si80.png)(13.24)

和

$p(\beta) = \text{Gamma}(\beta|c, d)$

![Equation](images/B9780443292385000196/si81.png)(13.25)

请注意，先验的上述选择表明了我们想要在指数族分布的框架内“玩”这个游戏的意愿。先验 $p(\mathbf{\alpha})$ 是公式 [(13.23)](#Chp013_635-716_B9780443292385000196.xhtml#deq30) 的共轭先验（参见第 [12](#Chp012_583-634_B9780443292385000184.xhtml) 章）。此外，如果我们将 $\mathbf{\theta}$ 视为固定，公式 [(13.25)](#Chp013_635-716_B9780443292385000196.xhtml#deq32) 将是公式 [(13.22)](#Chp013_635-716_B9780443292385000196.xhtml#deq29) 的共轭先验。[图 13.2](#Chp013_635-716_B9780443292385000196.xhtml#f0015) 提供了我们模型中涉及的各个变量之间依赖关系的图形化表示。箭头表示条件依赖。图形模型将在第 [15](#Chp015_755-803_B9780443292385000214.xhtml) 章中以正式方式进行探讨。请注意，这种模型在所涉及参数之间的依赖关系中形成了各个层级的*层次结构*。

![Figure 13.2 A graphical illustration of the dependencies among the various variables involved in the model of linear regression. The red circle indicates the random variable that is observed, gray circles indicate hidden random variables, and squares correspond to deterministic parameters. The direction of each arrow indicates the direction of the dependence between the connected variables. The red box indicates that the above dependencies hold for all N time instants.](images/B9780443292385000196/gr002.jpg)

[图 13.2](#Chp013_635-716_B9780443292385000196.xhtml#cf0455) 线性回归模型中涉及的各个变量之间依赖关系的图形化说明。红圈表示被观测的随机变量，灰圈表示隐藏随机变量，方框对应确定性参数。每个箭头的方向表示相连变量之间依赖关系的方向。红框表示上述依赖关系对所有 $N$ 个时刻均成立。

这种层次结构的概念正是我们所谓的*分层贝叶斯建模*的核心。每个涉及的概率密度函数（PDF）都用特定的（超）参数来表示。由于这些参数的值未知，它们也被视为随机变量，其先验用一组新的超参数来表示。它们每一个又依次被视为一个随机变量，并关联一个新的先验，称为*超先验*。这种基本原理可以扩展以构建不同层级的层次结构。通常，在层次结构的最高层，相应的（未知）超参数由用户根据经验赋值；例如，整体模型对其具体值可能相对不敏感，这使得相应的选择成为一项相当容易的工作。

我们当前的任务包含以 $\mathbf{\theta}$、$\mathbf{\alpha}$ 和 $\beta$ 形式分组的参数类隐变量，且不涉及其他未观测变量。观测集现在由 $\mathbf{y}$ 给出。此外，请注意后验 $p(\mathbf{\theta}, \mathbf{\alpha}, \beta|\mathbf{y})$ 在解析上是不可处理的。我们将求助于变分贝叶斯 EM 算法来获得上述后验 PDF 的估计。

使用均场近似，我们假设后验的近似（为了符号方便，已省略对 $\mathbf{y}$ 的依赖）分解为

$q(\mathbf{\theta}, \mathbf{\alpha}, \beta) = q_{\mathbf{\theta}}(\mathbf{\theta})q_{\mathbf{\alpha}}(\mathbf{\alpha})q_{\beta}(\beta)$

![Equation](images/B9780443292385000196/si84.png)(13.26)
