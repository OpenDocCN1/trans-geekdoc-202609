
我们不在此书中证明等周不等式（定理 5.1.4 和 5.1.5）；本章的文献注释列出了这些结果的若干已知证明。

## 5.1.3 球面上集合的膨胀

等周不等式导致了一个显著且违反直觉的结果：如果集合 $A$ 在面积上覆盖了球面至少一半，那么它的 $\varepsilon$-邻域 $A_\varepsilon$ 将覆盖球面的大部分。我们将陈述并证明这一“膨胀”现象，然后尝试直观地解释它。为了根据定理 5.1.3 简化问题，我们将使用半径为 $\sqrt{n}$ 的球面，而不是单位球面。

**引理 5.1.6（膨胀）。** 设 $A$ 是球面 $\sqrt{n}S^{n-1}$ 的一个子集，并设 $\sigma$ 表示该球面上的归一化面积。若 $\sigma(A) \ge 1/2$，那么，⁶ 对每个 $t \ge 0$，$\sigma(A_t) \ge 1 - 2\exp(-ct^2)$。

*证明* 考虑由第一个坐标定义的半球：$H := \{x \in \sqrt{n}S^{n-1} : x_1 \le 0\}$。

由假设，$\sigma(A) \ge 1/2 = \sigma(H)$，因此等周不等式（定理 5.1.5）蕴含 $\sigma(A_t) \ge \sigma(H_t)$。(5.1)

半球 $H$ 的邻域 $H_t$ 是一个球冠，我们可以直接计算它的面积。不过，改用定理 3.4.5 更容易，它指出随机向量 $X \sim \mathrm{Unif}(\sqrt{n}S^{n-1})$ 是次高斯的，且 $\|X\|_{\psi_2} \le C$。由于 $\sigma$ 是球面上的均匀概率测度，故 $\sigma(H_t) = \mathbb{P}\{X \in H_t\}$。

现在，邻域的定义蕴含 $H_t \supset \{x \in \sqrt{n}S^{n-1} : x_1 \le t/\sqrt{2}\}$。(5.2)

（请验证这一点——画个图会有帮助。）因此 $\sigma(H_t) \ge \mathbb{P}\{X_1 \le t/\sqrt{2}\} \ge 1 - 2\exp(-ct^2)$。

最后一个不等式成立，是因为 $\|X_1\|_{\psi_2} \le \|X\|_{\psi_2} \le C$。由 (5.1)，引理得证。

**注 5.1.7（一个更剧烈的膨胀）。** 引理 5.1.6 中面积的 $1/2$ 值是任意的，可以用任何常数代替，甚至可以用一个指数小量代替！在练习 5.3 中验证这一点。

⁶ 这里集合 $A$ 的邻域 $A_t$ 的定义与之前相同，即 $A_t := \{x \in \sqrt{n}S^{n-1} : \exists y \in A \ \text{使得}\ \|x-y\|_2 \le t\}$。

## 5.2.2 汉明立方体

基于等周的方法也适用于汉明立方体上的集中性：

$(\{0,1\}^n, d, \mathbb{P})$,

（回顾定义 4.2.14），其中 $d(x,y)$ 是归一化汉明距离，衡量二进制串 $x$ 和 $y$ 的位不同的比例：

$d(x,y) = \frac{1}{n} |\{i : x_i \ne y_i\}|$。

测度 $\mathbb{P}$ 是立方体上的均匀概率测度：

对任意 $A \subset \{0,1\}^n$，$\mathbb{P}(A) = |A| / 2^n$。

### 定理 5.2.5（汉明立方体上的集中性）

考虑随机向量 $X \sim \mathrm{Unif}\{0,1\}^n$。（因此 $X$ 的坐标是独立的 $\mathrm{Ber}(1/2)$ 随机变量。）则对任意函数 $f : \{0,1\}^n \to \mathbb{R}$，我们有

$\|f(X) - \mathbb{E}f(X)\|_{\psi_2} \le C \|f\|_{\mathrm{Lip}} / \sqrt{n}$。(5.6)

该结果可由汉明立方体上的等周不等式推出，其极小化集已知为汉明球——即关于汉明距离的单点邻域。（试着推导一下！）

## 5.2.3 对称群

对称群 $S_n$ 也有类似的结果成立，$S_n$ 是 $n$ 个符号 $\{1,\ldots,n\}$ 的所有 $n!$ 个置换构成的集合。我们可以把对称群看作一个度量测度空间

$(S_n, d, \mathbb{P})$。

这里 $d(\pi,\rho)$ 是归一化汉明距离——即排列 $\pi$ 和 $\rho$ 在不同符号上所占的比例：

$d(\pi,\rho) = \frac{1}{n} |\{i : \pi(i) \ne \rho(i)\}|$。

测度 $\mathbb{P}$ 是 $S_n$ 上的均匀概率测度，即对任意 $A \subset S_n$，$\mathbb{P}(A) = |A| / n!$。

### 定理 5.2.6（对称群上的集中性）

考虑随机置换 $X \sim \mathrm{Unif}(S_n)$ 和函数 $f : S_n \to \mathbb{R}$。则集中不等式 (5.6) 成立。

对任意 $u$，$u^\mathrm{T}(aI_n - X)u \ge 0$ 意味着 $aI_n - X \succeq 0$，从而 $X \preceq aI_n$。类似论证给出 $X \succeq -aI_n$，同时也证明了相反方向（把它写出来！）。（d）通过考虑 $g - f$，我们可以假设 $f = 0$。若 $\|X\| \le a$，则 $X$ 的所有特征值满足 $|\lambda_i| \le a$（由 (4.10)），根据假设这意味着 $g(\lambda_i) \ge 0$。因此，按定义，$g(X)$ 的特征值 $g(\lambda_i)$ 非负，所以 $g(X) \succeq 0$。□

**注 5.4.5**（算子范数作为矩阵的“绝对值”）。（5.12）看起来眼熟吗？它是关于绝对值的基本事实的矩阵版本：对 $x \in \mathbb{R}$，$|x| \le a \iff -a \le x \le a$。这使得算子范数 $\|\cdot\|$ 成为绝对值 $|\cdot|$ 的自然矩阵版本，也正是它出现在矩阵 Bernstein 不等式 5.4.1 中的原因。

**注 5.4.6**（矩阵单调性）。我们能否将迹单调性（命题 5.4.4(b)）加强为矩阵单调性，即对任意非递减函数 $f : \mathbb{R} \to \mathbb{R}$，有 $X \preceq Y \implies f(X) \preceq f(Y)$？(5.13) 若 $X$ 和 $Y$ 可交换，答案是肯定的——但一般来说不行（练习 5.17）。然而，某些函数，如 $[0,\infty)$ 上的 $1/x$ 和 $\log x$，是*矩阵单调的*，这意味着 (5.13) 对不可交换矩阵也成立：$0 \preceq X \preceq Y \implies X^{-1} \succeq Y^{-1} \succeq 0$，且当 $X$ 可逆时，$\log X \preceq \log Y$。请在练习 5.18 中验证这一点。

## 5.4.2 迹不等式

到目前为止，将标量概念推广到矩阵一直相当顺利，但这并非总能成功。我们已在注 5.4.6 中看到，非交换性（$AB \ne BA$）如何导致标量性质对矩阵失效。另一个例子是：恒等式 $e^{x+y}=e^x e^y$ 对标量成立，但在练习 5.19 中，你将找到 $n \times n$ 对称矩阵 $X$ 和 $Y$，使得 $e^{X+Y} \ne e^X e^Y$。这很不幸，因为恒等式 $e^{x+y}=e^x e^y$ 对我们处理随机变量和的集中性至关重要：它让我们把和的矩生成函数 $\mathbb{E}\exp(\lambda S)$ 拆成指数函数的乘积，见 (2.6)。然而，对于缺失的恒等式 $e^{X+Y}=e^X e^Y$，存在有用的替代品。我们在此不加证明地陈述其中两个；它们属于丰富的*迹不等式*族。

**定理 5.4.7**（Golden-Thompson 不等式）。对任意 $n \times n$ 对称矩阵 $A$ 和 $B$，我们有 $\mathrm{tr}(e^{A+B}) \le \mathrm{tr}(e^A e^B)$。遗憾的是，Golden-Thompson 不等式对三个或更多矩阵不成立：一般来说，不等式 $\mathrm{tr}(e^{A+B+C}) \le \mathrm{tr}(e^A e^B e^C)$ 可能失效。

由于 $e^{\lambda S}$ 的特征值均为正，$e^{\lambda S}$ 的最大特征值受所有特征值之和（即 $e^{\lambda S}$ 的迹）的约束，由此得到

$E \le \mathbb{E}\,\mathrm{tr}\,e^{\lambda S}$.

### 第 2 步：应用 Lieb 不等式

为了准备应用 Lieb 不等式（引理 5.4.9），让我们从和 $S$ 中分离出最后一项：

$E \le \mathbb{E}\,\mathrm{tr}\,\exp\left[\sum_{i=1}^{N-1} \lambda X_i + \lambda X_N\right]$.

对 $(X_i)_{i=1}^{N-1}$ 取条件，并将引理 5.4.9 应用于固定矩阵 $H := \sum_{i=1}^{N-1} \lambda X_i$ 和随机矩阵 $Z := \lambda X_N$。我们得到

$E \le \mathbb{E}\,\mathrm{tr}\,\exp\left[\sum_{i=1}^{N-1} \lambda X_i + \log \mathbb{E}\,e^{\lambda X_N}\right]$.

（更具体地说，我们先对条件期望应用引理 5.4.9，然后利用全期望公式对两边取期望。）

我们以类似方式继续：从和 $\sum_{i=1}^{N-1} \lambda X_i$ 中分离出下一项 $\lambda X_{N-1}$，并再次对 $Z = \lambda X_{N-1}$ 应用引理 5.4.9。重复 $N$ 次，我们得到

$E \le \mathrm{tr}\,\exp\left[\sum_{i=1}^{N} \log \mathbb{E}\,e^{\lambda X_i}\right]$. (5.16)

### 第 3 步：各项的矩生成函数（MGF）

剩下要界定每一项 $X_i$ 的矩阵值矩生成函数 $\mathbb{E}\,e^{\lambda X_i}$。这是一项标准任务，论证过程与标量情形类似。

### 引理 5.4.10（矩生成函数）

*设 $X$ 是一个 $n \times n$ 对称零均值随机矩阵，且几乎必然地有 $||X|| \le K$。则*

$\mathbb{E}\,\exp(\lambda X) \preceq \exp\big(g(\lambda)\,\mathbb{E}\,X^2\big)\quad \text{其中}\quad g(\lambda)=\frac{\lambda^2/2}{1-|\lambda|K/3},$

*只要* $|\lambda| < 3/K$。

*证明* 首先，注意我们可以用（标量）指数函数的泰勒展开的前几项来界定它，如下：

$e^{z} \le 1 + z + \frac{1}{1-|z|/3}\,\frac{z^2}{2},\quad \text{若 }|z|<3.$

（为得到此不等式，写出 $e^{z}=1+z+z^2\cdot\sum_{p=2}^{\infty}z^{p-2}/p!$ 并使用界 $p!\ge 2\cdot3^{p-2}$。）接下来，将此不等式应用于 $z=\lambda x$。若 $|x|\le K$ 且 $|\lambda|<3/K$，则得到

$e^{\lambda x} \le 1 + \lambda x + g(\lambda)x^2,$

其中 $g(\lambda)$ 是引理陈述中的函数。
