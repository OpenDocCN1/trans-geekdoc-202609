
**例 8.3.5**（半空间）。\(\mathbb{R}^n\) 中的半空间是如下形式的集合
\[
\{x : \langle a, x\rangle \le b\}
\]
其中 \(a\in\mathbb{R}^n\)，\(b\in\mathbb{R}\)。设 \(\mathcal{F}\) 是 \(\mathbb{R}^n\) 中所有半空间的指示函数类。则
\[
\operatorname{VC}(\mathcal{F}) = n+1.
\]

**注 8.3.6**（VC 维与参数数量）。函数类的 VC 维通常与参数数量大致匹配——例如，\(\mathbb{R}^n\) 中的半空间由 \(n+1\) 个参数定义，这与它们的 VC 维匹配（参见例 8.3.5）。这不是一条硬性规则，而是一个有用的启发式方法。

## 8.3.2 Pajor 引理

假设定义域 \(\Omega\) 是有限的，由 \(n\) 个点组成。那么 \(\Omega\) 上的任何布尔函数类 \(\mathcal{F}\) 也是有限的，并且
\[
2^{\operatorname{VC}(\mathcal{F})} \le |\mathcal{F}| \le 2^n. \tag{8.27}
\]
（为什么？）上界通常是松散的——大多数函数类的大小更接近下界。这并不那么显然。为了给这一结果做准备，我们首先证明被 \(\mathcal{F}\) 打散的 \(\Omega\) 的子集与 \(\mathcal{F}\) 中的函数一样多。

**引理 8.3.7**（Pajor 引理）。*设 \(\mathcal{F}\) 是有限集 \(\Omega\) 上的布尔函数类。则*
\[
|\mathcal{F}| \le \left|\{\Lambda\subseteq\Omega : \Lambda \text{ 被 } \mathcal{F} \text{ 打散}}\right|.
\]
*我们在右边的计数中包含空集 \(\Lambda=\emptyset\)。*

在证明之前，让我们用例 8.3.4 来说明这个结果。这里，\(|\mathcal{F}|=4\)，并且有六个子集 \(\Lambda\) 被 \(\mathcal{F}\) 打散，即 \(\{1\},\{2\},\{3\},\{1,2\},\{1,3\}\) 和 \(\{2,3\}\)。（请检查！）因此 Pajor 引理中的不等式为 \(4\le6\)。

*引理 8.3.7 的证明。* 我们对 \(\Omega\) 的基数进行归纳。\(|\Omega|=1\) 的情形是平凡的，因为我们在计数中包含了空集。假设引理对任意 \(n\) 点集 \(\Omega\) 成立，我们来证明对 \(|\Omega|=n+1\) 的 \(\Omega\) 成立。从集合 \(\Omega\) 中切掉一个（任意的）点，我们可以将其表示为
\[
\Omega=\Omega_0\cup\{x_0\}, \quad \text{其中 } |\Omega_0|=n.
\]
类 \(\mathcal{F}\) 于是自然分成两个子类
\[
\mathcal{F}_0:=\{f\in\mathcal{F}: f(x_0)=0\} \quad\text{和}\quad \mathcal{F}_1:=\{f\in\mathcal{F}: f(x_0)=1\}.
\]
由归纳假设，计数函数
\[
S(\mathcal{F}) = \left|\{\Lambda\subseteq\Omega : \Lambda \text{ 被 } \mathcal{F} \text{ 打散}}\right|
\]
满足
\[
S(\mathcal{F}_0)\ge|\mathcal{F}_0| \quad\text{且}\quad S(\mathcal{F}_1)\ge|\mathcal{F}_1|. \tag{8.28}
\]
此处，为了正确使用归纳假设，我们将 \(\mathcal{F}_0\) 和 \(\mathcal{F}_1\) 中的函数限制到 \(n\) 点集 \(\Omega_0\) 上。

为了完成证明，我们只需检验
\[
S(\mathcal{F}) \ge S(\mathcal{F}_0)+S(\mathcal{F}_1), \tag{8.29}
\]
因为这样 (8.28) 将给出 \(S(\mathcal{F})\ge|\mathcal{F}_0|+|\mathcal{F}_1|=|\mathcal{F}|\)，这正是所需的。

不等式 (8.29) 可能看起来是平凡的。任何被 \(\mathcal{F}_0\) 或 \(\mathcal{F}_1\) 打散的集合 \(\Lambda\) 都会自动被更大的类 \(\mathcal{F}\) 打散，因此被 \(S(\mathcal{F}_0)\) 或 \(S(\mathcal{F}_1)\) 计数的每个集合 \(\Lambda\) 也自动被 \(S(\mathcal{F})\) 计数。然而，问题在于重复计数。假设同一个集合 \(\Lambda\) 同时被 \(\mathcal{F}_0\) 和 \(\mathcal{F}_1\) 打散。计数函数 \(S(\mathcal{F})\) 不会将 \(\Lambda\) 计数两次。但是，\(S(\mathcal{F})\) 会计数一个不同的集合，这个集合既没有被 \(S(\mathcal{F}_0)\) 计数，也没有被 \(S(\mathcal{F}_1)\) 计数——即 \(\Lambda\cup\{x_0\}\)。稍加思考就会发现，这个集合确实被 \(\mathcal{F}\) 打散。（请检查！）这建立了不等式 (8.29)，并完成了 Pajor 引理的证明。

让我们来说明 Pajor 引理证明中的关键点：

**例 8.3.8。** 让我们再次回到例 8.3.4。按照 Pajor 引理的证明，我们从 \(\Omega=\{1,2,3\}\) 中切掉 \(x_0=3\)，得到 \(\Omega_0=\{1,2\}\)。类 \(\mathcal{F}=\{001,010,100,111\}\) 于是分成两个子类
\[
\mathcal{F}_0=\{010,100\} \quad\text{和}\quad \mathcal{F}_1=\{001,111\}.
\]
被 \(\mathcal{F}_0\) 打散的集合 \(\Lambda\) 恰好有两个，即 \(\{1\}\) 和 \(\{2\}\)，并且**同样的**集合也被 \(\mathcal{F}_1\) 打散，使得 \(S(\mathcal{F}_0)=S(\mathcal{F}_1)=2\)。当然，同样的两个集合也被 \(\mathcal{F}\) 打散，但我们需要两个更多的打散集合来使关键不等式 (8.29) 中的 \(S(\mathcal{F})\ge4\) 成立。下面是我们构造它们的方法：将 \(x_0=3\) 附加到已经计数的子集 \(\Lambda\) 上。得到的集合 \(\{1,3\}\) 和 \(\{2,3\}\) 也被 \(\mathcal{F}\) 打散，而我们还没有对它们进行计数。现在至少有**四个**被 \(\mathcal{F}\) 打散的集合，使得关键不等式 (8.29) 成立。

## 8.3.3 Sauer–Shelah 引理

我们现在推出一个关于函数类基数的显著上界，用 VC 维表示：

**引理 8.3.9（Sauer–Shelah 引理）。** *设 \(\mathcal{F}\) 是 \(n\) 点集 \(\Omega\) 上的布尔函数类。则*
\[
|\mathcal{F}| \le \sum_{k=0}^{d} \binom{n}{k} \le \left(\frac{en}{d}\right)^d
\]
其中 \(d=\operatorname{VC}(\mathcal{F})\)。

*证明。* Pajor 引理说明 \(|\mathcal{F}|\) 以被 \(\mathcal{F}\) 打散的 \(\Omega\) 的子集 \(\Lambda\) 的数目为上界。根据 VC 维的定义，每个这样的集合 \(\Lambda\) 的基数以 \(d=\operatorname{VC}(\mathcal{F})\) 为上界。因此
\[
|\mathcal{F}| \le \left|\{\Lambda\subseteq\Omega: |\Lambda|\le d\}\right| = \sum_{k=0}^{d} \binom{n}{k},
\]
因为右边的和给出了一个 \(n\) 元集合中基数至多为 \(d\) 的子集的总数。这证明了 Sauer–Shelah 引理的第一个不等式。第二个不等式由我们在练习 0.6 中证明的二项式和的界得出。

Pajor 引理和 Sauer–Shelah 引理通常都是紧的（尝试练习 8.19）。

## 8.3.4 增长函数

Sauer–Shelah 引理假设定义域 \(\Omega\) 是有限的。那么像 \(\Omega=\mathbb{R}^n\) 这样的无限定义域上的函数类 \(\mathcal{F}\) 呢？通常用增长函数来度量 \(\mathcal{F}\) 的复杂度是很方便的：

**定义 8.3.10**（增长函数）。设 \(\mathcal{F}\) 是定义域 \(\Omega\) 上的布尔函数类。\(\mathcal{F}\) 的增长函数定义为将 \(\mathcal{F}\) 中所有函数限制到 \(n\) 个元素的子集上所能得到的函数的最大数量：
\[
\Pi_{\mathcal{F}}(n) = \sup\left\{\left|\mathcal{F}\right|_{\Lambda} : \Lambda\subseteq\Omega,\ |\Lambda|=n\right\}.
\]

这样看来，\(\mathcal{F}\) 的 VC 维可以看作使得 \(\Pi_{\mathcal{F}}(d)=2^d\) 的最大 \(d\)。增长函数的直接界为
\[
2^d \le \Pi_{\mathcal{F}}(n) \le \left(\frac{en}{d}\right)^d \quad\text{对所有 } n\ge d, \tag{8.30}
\]
如果 \(d=\operatorname{VC}(\mathcal{F})<\infty\)。下界是 (8.27) 的重述，上界由 Sauer–Shelah 引理（引理 8.3.9）得出。

为了看出增长函数如何有用，让我们从 (8.30) 推导 VC 维关于自然运算的稳定性。

**命题 8.3.11**（VC 稳定性）。设 \(\mathcal{F}\) 和 \(\mathcal{G}\) 是同一定义域上的两个布尔函数类。设
\[
\mathcal{F}\wedge\mathcal{G} = \{f\wedge g : f\in\mathcal{F},\ g\in\mathcal{G}\}
\]
其中 \(f\wedge g\) 表示函数 \(f\) 和 \(g\) 的逐点最小值。则
\[
\operatorname{VC}(\mathcal{F}\wedge\mathcal{G}) \le 10\max\bigl(\operatorname{VC}(\mathcal{F}),\operatorname{VC}(\mathcal{G})\bigr).
\]
对于逐点最大值 \(\vee\)，同样成立。

*证明。* 用反证法，假设 \(n := \operatorname{VC}(\mathcal{F}\wedge\mathcal{G}) > 10d\)，其中 \(d=\max(\operatorname{VC}(\mathcal{F}),\operatorname{VC}(\mathcal{G}))\)。则
\[
2^n \le \Pi_{\mathcal{F}\wedge\mathcal{G}}(n) \le \Pi_{\mathcal{F}}(n)\cdot\Pi_{\mathcal{G}}(n) \le \left(\frac{en}{d}\right)^{2d}.
\]
（第一个和最后一个界由 (8.30) 得出，中间那个界根据定义应当是清楚的。）然而，简单的计算表明，当 \(n>10d\) 时，\(2^n > (en/d)^{2d}\)。矛盾。

命题 8.3.11 可以推广到组合函数类的任何特定方式——尝试练习 8.21。当我们希望在不直接计算 VC 维的情况下限制它时，这会很有用，例如在这个例子中：

**例 8.3.12**（条带）。\(\mathbb{R}^n\) 中的条带是如下形式的集合
\[
\{x : |\langle a,x\rangle-b|\le c\} \qquad\text{其中 } a\in\mathbb{R}^n,\ b,c\in\mathbb{R},
\]
见图 8.7。设 \(\mathcal{F}\) 是条带的指示函数类。例 8.3.5 给出
\[
\operatorname{VC}(\mathcal{F}) \le 10(n+1) \le 20n.
\]
确实，每个条带可以表示为两个半空间 \(\{x : \langle a,x\rangle-b\le c\}\) 和 \(\{x : \langle a,x\rangle-b\ge -c\}\) 的交集。因此每个条带的指示函数是两个半空间的指示函数的逐点最小值。现在应用 VC 稳定性性质（命题 8.3.11）和例 8.3.5 的结果。

![图 8.7](img/b122213aed28c1888de83a894123323e_242_0.png)

**图 8.7** \(\mathbb{R}^2\) 中的四个不同条带。

为了更深入地练习增长函数，请展示一个令人惊叹的二分法——这个函数既可以多项式增长，也可以指数增长（练习 8.20），并计算并集的 VC 维（练习 8.22）。

## 8.3.5 通过 VC 维估计覆盖数

覆盖数通常随维度指数增长（例如参见 (4.17)）。现在，让我们通过用 VC 维替换代数维度来改进这一经验法则——这可以为我们节省很多。

设 \(\mathcal{F}\) 是某个定义域 \(\Omega\) 上的布尔函数类，并设 \(\mu\) 是 \(\Omega\) 上的任意概率测度。定义函数之间的距离
\[
d(f,g)=\|f-g\|_{L^2(\mu)} = \left(\mathbb{E}(f-g)(X)^2\right)^{1/2}, \tag{8.31}
\]
其中 \(X\) 是一个分布为 \(\mu\) 的随机变量。（如果你没有学过测度论，只需取一个取值于 \(\Omega\) 的任意随机变量 \(X\)，并将 \(\mu\) 视为 \(X\) 的分布的名称。）

现在让我们来界定类 \(\mathcal{F}\) 关于度量 (8.31) 的覆盖数 \(\mathcal{N}(\mathcal{F},L^2(\mu),\epsilon)\)：
