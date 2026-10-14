
## 附录 A
进一步阅读
和资源

### A.1 竞争性编程

有许多优秀的资源可用于学习算法。我强烈推荐 Steven Halim 的 *竞争性编程* 书籍，此外还有 Steven Skiena 的经典著作 *算法设计手册* 以及 Thomas H. Cormen 等人的 *算法导论*。

有一些很棒的编程挑战网站，其中一些列在这里：

- LeetCode: https://leetcode.com
- TopCoder: https://www.topcoder.com
- CodeForces: https://codeforces.com
- HackerRank: https://www.hackerrank.com
- GeeksForGeeks: https://www.geeksforgeeks.org
- uVAOnlineJudge: https://onlinejudge.org

我希望这些资源能帮助你在成为一名竞争性程序员的旅程中。

### A.2 推荐书籍

掌握机器学习需要对基础有扎实的理解。新的机器学习算法是通过在基础之上构建或将新趋势与经典成果相结合而设计的。本节重点介绍了任何希望在该领域取得进步的人都必须阅读的一些关键机器学习书籍。图 A.1 中总结的书籍从理论到应用不等，涵盖统计学、机器学习、优化、信息论、算法和数据结构等主题。

![](img/325742126d3ff007c6c385f4ffb5c3be_304_0.png)

### 图 A.1 推荐书籍

在你迈向机器学习精通的旅程中，我强烈推荐以下书籍，如图 A.1 所示：

- Kevin Murphy, *机器学习：概率观点*, MIT Press, 2012
- Christopher Bishop, *模式识别与机器学习*, Springer, 2011
- David MacKay, *信息论、推断与学习算法*, Cambridge University Press, 2003
- Steven Skiena, *算法设计手册*, Springer, 2011
- Thomas Cormen, Charles Leiserson, Ronald Rivest, and Clifford Stein, *算法导论*, MIT Press, 2009
- Steven Halim, *竞争性编程*, lulu, 2013
- Francois Chollet, *Python 深度学习*, Manning Publications, 2017
- Trevor Hastie, Robert Tibshirani, and Jerome Friedman, *统计学习基础：数据挖掘、推断与预测*, Springer, 2016
- Stephen Boyd and Lieven Vandenberghe, *凸优化*, Cambridge University Press, 2004
- Thomas Cover and Joy A. Thomas, *信息论基础*, Wiley, 1991

### A.3 研究会议

机器学习领域正在迅速发展，保持最新研究动态的最佳方式是通过审阅会议论文。本节总结了机器学习、计算机视觉、自然语言处理和理论计算机科学领域顶级会议。

## 附录 B
### 练习答案

### 2.1 推导多元高斯分布的完整条件分布 $p(x_A|x_B)$，其中 $A$ 和 $B$ 是联合高斯随机变量 $x_1$, $x_2$, ..., $x_n$ 的子集。

让我们将向量 $x$ 分成两个子集 $x_A$ 和 $x_B$，然后我们可以以块形式写下均值和协方差矩阵：

$$\mu = \begin{pmatrix} \mu_A \\ \mu_B \end{pmatrix}$$

$$\Sigma = \begin{pmatrix} \Sigma_{AA} & \Sigma_{AB} \\ \Sigma_{BA} & \Sigma_{BB} \end{pmatrix}$$

为了计算条件分布，我们得到以下结果：

$p(x_A|x_B) = N\left(x_A|\mu_A + \Sigma_{AB}\Sigma_{BB}^{-1}(x_B - \mu_B), \Sigma_{AA} - \Sigma_{AB}\Sigma_{BB}^{-1}\Sigma_{BA}\right)$

$p(x_B|x_A) = N\left(x_B|\mu_B + \Sigma_{BA}\Sigma_{AA}^{-1}(x_A - \mu_A), \Sigma_{BB} - \Sigma_{BA}\Sigma_{AA}^{-1}\Sigma_{AB}\right)$

### 2.2 推导多元高斯分布的边缘分布 $p(x_A)$ 和 $p(x_B)$，其中 $A$ 和 $B$ 是联合高斯随机变量 $x_1$, $x_2$, ..., $x_n$ 的子集。

让我们将向量 $x$ 分成两个子集 $x_A$ 和 $x_B$，然后我们可以以块形式写下均值和协方差矩阵：

$$\mu = \begin{pmatrix} \mu_A \\ \mu_B \end{pmatrix}$$

$$\Sigma = \begin{pmatrix} \Sigma_{AA} & \Sigma_{AB} \\ \Sigma_{BA} & \Sigma_{BB} \end{pmatrix}$$

为了计算边缘分布，我们只需从均值和协方差中读取相应的行和列：

$$p(x_A) = \int N(x|\mu,\Sigma)dx_B = N(x_A|\mu_A,\Sigma_{AA})$$

$$p(x_B) = \int N(x|\mu,\Sigma)dx_B = N(x_B|\mu_B,\Sigma_{BB})$$

### 2.3 设 $y \sim N(\mu, \Sigma)$，其中 $\Sigma = LL^{\mathsf T}$。证明你可以按如下方式获取样本 $y$：$x \sim N(0, I)$；$y = Lx + \mu$。

设 $y = Lx + \mu$。则，$E[y]= LE[x]+\mu = 0+\mu = \mu$。类似地，$\operatorname{cov}(y)= L \operatorname{cov}(x)L^{\mathsf T} + 0 = LIL^{\mathsf T}=LL^{\mathsf T}=\Sigma$。由于 $y$ 是高斯随机变量的仿射变换，$y$ 也是高斯分布的，即 $y \sim N(\mu, \Sigma)$。

### 3.1 计算两个一元高斯分布之间的 KL 散度：$p(x) \sim N(\mu_1,\sigma_1^2)$ 和 $q(x) \sim N(\mu_2,\sigma_2^2)$。

$$KL(p||q) = - \int p(x)\log q(x)dx + \int p(x)\log p(x)dx$$

$$= \frac{1}{2}\log\left(2\pi\sigma_2^2\right)+\frac{\sigma_1^2+(\mu_1-\mu_2)^2}{2\sigma_2^2} - \frac{1}{2}\left(1+\log 2\pi\sigma_1^2\right)$$

$$= \log\frac{\sigma_2}{\sigma_1}+\frac{\sigma_1^2+(\mu_1-\mu_2)^2}{2\sigma_2^2}-\frac{1}{2}$$

### 3.2 计算伯努利分布的 $E[X],\operatorname{Var}(X)$，和 $H(X)$。

伯努利分布定义为 $p(x)=p^x(1-p)^{1-x}$，其中 $x\in\{0,1\}$。根据均值、方差和熵的定义，我们可以计算以下量：

$$E[X] = \sum_{x\in\{0,1\}} p_x(x)x = p_x(0)\times0 + p_x(1)\times1 = p$$

$$\operatorname{var}(X) = E[X^2]-E[X]^2 = \sum_{x\in\{0,1\}} p_x(x)x^2 - p^2 = p_x(0)\times0^2 + p_x(1)\times1^2 - p^2 = p(1-p)$$

$$H(X) = - \sum_{x\in\{0,1\}} p_x(x)\log p_x(x) = -p_x(0)\log p_x(0)-p_x(1)\log p_x(1) = -(1-p)\log(1-p)-p\log p$$

### 3.3 推导 Beta$(a,b)$ 分布的均值、众数和方差。

Beta 分布在区间 $[0,1]$ 上有支撑，定义如下：

$$\operatorname{Beta}(x\mid a,b)=\frac{\Gamma(a+b)}{\Gamma(a)\Gamma(b)}x^{a-1}(1-x)^{b-1}$$

Beta 分布的均值、众数和方差的表达式如下：

$$E[X]=\frac{a}{a+b}\qquad \operatorname{mode}[X]=\frac{a-1}{a+b-2}\qquad \operatorname{VAR}(X)=\frac{ab}{(a+b)^2(a+b+1)}$$

### 4.1 证明以下二项式恒等式：$C(n,k)=C(n-1,k-1)+C(n-1,k)$。

我们将使用代数证明。根据定义，展开左边，我们有以下内容：

$$\begin{aligned}
\binom{n-1}{k-1}+\binom{n-1}{k}
&=\frac{(n-1)!}{(n-k)!\,(k-1)!}+\frac{(n-1)!}{(n-k-1)!\,k!}\\
&=\frac{(n-1)!}{(n-k-1)!\,(k-1)!}\left(\frac{1}{n-k}+\frac{1}{k}\right)\\
&=\frac{n!}{(n-k)!\,k!}\\
&=\binom{n}{k}
\end{aligned}$$

### 4.2 推导 Gibbs 不等式 $H(p,q)\ge H(q)$，其中 $H(p,q)=-\sum p(x)\log q(x)$ 是交叉熵，$H(q)=-\sum q(x)\log q(x)$ 是熵。

首先，我们证明 KL 散度是非负的：

$$\begin{aligned}
-KL(p\|q)&=-\sum_x p(x)\log\frac{p(x)}{q(x)}\,dx=\sum_x p(x)\log\frac{q(x)}{p(x)}\,dx\\
&\le \log\sum_x p(x)\frac{q(x)}{p(x)}\,dx=\log\sum_x q(x)\\
&\le \log 1=0
\end{aligned}$$

利用之前推导出的性质，我们可以写出 Gibbs 不等式如下：

$$\begin{aligned}
KL(p\|q)&\ge 0\\
\sum_x p(x)\log p(x)-\sum_x p(x)\log q(x)&\ge 0\\
-H(p)+H(p,q)&\ge 0\\
H(p,q)&\ge H(p)
\end{aligned}$$

### 4.3 使用 $f(x)=\log(x)$ 的 Jensen 不等式证明 AM $\ge$ GM 不等式。

由于 $f(x)=\log(x)$ 是一个凹函数，我们可以写出 Jensen 不等式如下：

$f(E[x]) \ge E[f(x)]$
$\log(E[x]) \ge E[\log(x)]$
$\log\left(\frac{x_1+\cdots+x_n}{n}\right) \ge \frac{\log x_1+\cdots+\log x_n}{n}$
$\log\left(\frac{x_1+\cdots+x_n}{n}\right) \ge \log(x_1\times\cdots\times x_n)^{1/n}$
$AM \ge GM$

### 4.4 证明 $I(X;Y)=H(X)-H(X|Y)=H(Y)-H(Y|X)$。

根据互信息定义，我们有以下内容：

$I(X;Y)=\sum_x\sum_y p(x,y)\log\frac{p(x,y)}{p(x)p(y)}$
$=E_{p(x,y)}\left[\log\frac{p(x|y)}{p(x)}\right]=E_{p(x,y)}\left[\log\frac{p(y|x)}{p(y)}\right]$
$=H(X)-H(X|Y)$
$=H(Y)-H(Y|X)$

### 5.1 给定数据点 $y\in\mathbb{R}^d$ 和超平面 $\theta\cdot x+\theta_0=0$，计算点到超平面的欧几里得距离。

设 $x$ 是超平面上的一个点——换句话说，确保它满足方程 $\theta\cdot x+\theta_0=0$。为了找到点到超平面的欧几里得距离，我们构造向量 $y-x$ 并将其投影到垂直于平面的唯一向量上。因此，我们有以下内容：

$d=\|\operatorname{proj}_\theta(y-x)\|$
$=\left\|\frac{(y-x)\cdot\theta}{\theta\cdot\theta}\theta\right\|=\left|y\cdot\theta-x\cdot\theta\right|\frac{\|\theta\|}{\|\theta\|^2}$
$=\frac{|y\cdot\theta-x\cdot\theta|}{\|\theta\|}=\frac{|y\cdot\theta+\theta_0|}{\|\theta\|}$

### 5.2 给定原线性规划 (LP) $\min c^T x$ 约束条件 $Ax<=b$, $x>=0$，写出 LP 的对偶形式。

原 LP 中的每个变量对应于对偶 LP 中的一个约束，反之亦然。原问题是最小化问题，因此对偶问题是最大化问题。原问题的约束是小于或等于，因此对偶变量是大于或
