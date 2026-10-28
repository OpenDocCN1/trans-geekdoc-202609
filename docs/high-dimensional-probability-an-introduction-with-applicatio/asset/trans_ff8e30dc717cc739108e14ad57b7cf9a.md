
代入 (9.32)，我们得到

$$\beta \sum_{i\ge 2} \|h_{I_i}\|_2 \ge \alpha \|h_{I_{0,1}}\|_2.$$ (9.33)

### 第 3 步：求和。

接下来，我们像在练习 9.25 中那样对左边的和进行估计。 根据 $I_i$ 的定义，$h_{I_i}$ 的每个分量在绝对值上都被 $h_{I_{i-1}}$ 的分量的平均值所限制，即对于 $i \ge 2$，被 $\frac{1}{\lambda_s}\|h_{I_{i-1}}\|_1$ 所限制。因此

$$\|h_{I_i}\|_2 \le \frac{1}{\sqrt{\lambda_s}}\|h_{I_{i-1}}\|_1.$$

求和得到

$$\sum_{i\ge2}\|h_{I_i}\|_2 \le \frac{1}{\sqrt{\lambda_s}}\sum_{i\ge1}\|h_{I_i}\|_1 = \frac{1}{\sqrt{\lambda_s}}\|h_{I_0^c}\|_1 \le \frac{1}{\sqrt{\lambda_s}}\|h_{I_0}\|_1 \quad\text{(by Lemma 9.5.2)}$$ 

$$\le \frac{1}{\sqrt{\lambda}}\|h_{I_0}\|_2 \le \frac{1}{\sqrt{\lambda}}\|h_{I_{0,1}}\|_2.$$

将其代入 (9.33) 我们得出

$$\frac{\beta}{\sqrt{\lambda}}\|h_{I_{0,1}}\|_2 \ge \alpha \|h_{I_{0,1}}\|_2.$$

但这意味着 $h_{I_{0,1}} = 0$，因为根据假设 $\beta/\sqrt{\lambda} < \alpha$。并且由于 $I_{0,1}$ 包含 $h$ 的最大分量，所以必有 $h = 0$。$\square$

虽然我们不知道如何构造满足 RIP 且参数良好的确定性矩阵 $A$，但我们可以证明随机矩阵以高概率满足它：

### 定理 9.5.7（随机矩阵满足 RIP）。

*考虑一个 $m \times n$ 矩阵 $A$，其行 $A_i$ 独立、同质且次高斯。假设*

$$m \ge C K^4 s \log(en/s).$$

*其中 $K = \max_i \|A_i\|_{\psi_2}$。那么，以至少 $1 - 2\exp(-c m / K^4)$ 的概率，随机矩阵 $A$ 满足 RIP，参数为 $\alpha = 0.9\sqrt{m}$，$\beta = 1.1\sqrt{m}$ 和 $s$。*

*证明* 我们需要对所有 $m \times s$ 子矩阵 $A_I$ 检查 (9.31)。首先固定 $I$。根据定理 4.6.1，我们得到

$$0.9\sqrt{m} \le s_s(A_I) \le s_1(A_I) \le 1.1\sqrt{m}$$ (9.34)

以至少 $1 - 2\exp(-2c m / K^4)$ 的概率成立（令 $t = \sqrt{2c m}/K^2$ 并利用关于 $m$ 的假设，选择常数 $c$ 和 $C$ 适当）。利用 (0.6) 中的界 $\binom{n}{s} \le \exp(s \log(en/s))$ 以及关于 $m$ 的假设。证明完毕。

我们刚刚学习了精确恢复的另一种方法：

*定理 9.5.1 的第二证明*  根据定理 9.5.7，$A$ 满足 RIP，参数为 $\alpha = 0.9\sqrt{m}$，$\beta = 1.1\sqrt{m}$ 和 $3s$。因此，$\lambda = 2$ 时的定理 9.5.6 保证了精确恢复。所以定理 9.5.1 成立——而且我们甚至得到了练习 9.5.4 中的对数改进！

为了练习，证明随机投影满足 RIP（练习 9.33）。

## 9.6 随机矩阵对一般范数的偏差

让我们将矩阵偏差不等式（定理 9.1.1）推广，使其适用于任意范数——而不仅仅是欧几里得范数。实际上，我们甚至不需要范数为非负——只要齐次性和三角不等式就足够了。

### 定义 9.6.1（允许范数取负值）。

实值函数 $f$ 在线性向量空间 $V$ 上称为：

- *正齐次* 如果对所有 $\alpha \ge 0$ 和 $x \in V$ 有 $f(\alpha x)=\alpha f(x)$；
- *次可加* 如果对所有 $x,y \in V$ 有 $f(x+y) \le f(x)+f(y)$。

### 例 9.6.2。

这些函数是正齐次且次可加的：

- (a) 任意 *范数*；
- (b) 任意实值线性函数（称为 *线性泛函*）；
- (c) 特别地，对于任意固定向量 $y \in \mathbb{R}^m$，函数 $f(x)=\langle x,y\rangle$；
- (d) 任意有界集合 $S \subset \mathbb{R}^n$ 的 *支撑函数*，定义为

$$f(x) := \sup_{y\in S}\langle x,y\rangle, \quad x \in \mathbb{R}^m.$$ (9.35)

（验证这个！）。

这里有一个适用于所有范数（甚至正齐次、次可加函数）的定理 9.1.1 的版本，但有一个权衡——它仅适用于高斯矩阵：

### 定理 9.6.3（一般矩阵偏差不等式）。

*设 $A$ 为 $m \times n$ 随机矩阵，其元素独立同分布为 $N(0,1)$。设 $f : \mathbb{R}^m \to \mathbb{R}$ 为有界、正齐次且次可加的函数，且 $b \in \mathbb{R}$ 满足*

$$f(x) \le b\|x\|_2 \quad \text{for all } x \in \mathbb{R}^n.$$ (9.36)

*则对于任意子集 $T \subset \mathbb{R}^n$，*

$$\mathbb{E}\sup_{x\in T}\big|f(Ax)-\mathbb{E}f(Ax)\big| \le C b \gamma(T),$$

*其中 $\gamma(T)$ 为高斯复杂度（参见第 7.5.3 节）。*

正如第 9.1 节中一样，一旦我们证明随机过程

$$Z_x := f(Ax) - \mathbb{E} f(Ax)\tag{9.37}$$

具有次高斯增量。定理 9.6.3 将立即由 Talagrand 比较不等式得出。让我们现在来做：

### 定理 9.6.4（次高斯增量）。

*设 $A$ 为 $m\times n$ 高斯随机矩阵，其元素独立同分布为 $N(0,1)$，且 $f : \mathbb{R}^m \to \mathbb{R}$ 为满足 (9.36) 的正齐次且次可加函数。则随机过程 (9.2) 具有次高斯增量：*

$$\|Z_x - Z_y\|_{\psi_2} \le C b \|x - y\|_2 \quad \text{for all } x, y \in \mathbb{R}^n.\tag{9.38}$$

*定理 9.6.4 的证明*  在不失一般性的情况下，我们可以假设 $b = 1$。（为什么？）就像定理 9.1.2 的证明中一样，首先假设

$$\|x\|_2 = \|y\|_2 = 1.$$

在这种情况下，(9.38) 中的不等式变为

$$\|f(Ax) - f(Ay)\|_{\psi_2} \le C \|x - y\|_2.\tag{9.39}$$

### 第 1 步：创建独立性。

考虑向量

$$u := \frac{x + y}{2}, \quad v := \frac{x - y}{2}.\tag{9.40}$$

则 $x = u + v$ 且 $y = u - v$，因此

$$Ax = Au + Av, \quad Ay = Au - Av$$

（见图 9.8）。由于 $u$ 和 $v$ 正交（验证！），高斯随机

![](img/b122213aed28c1888de83a894123323e_291_0.png)

**图 9.8** 由 $x, y$ 创建一对正交向量 $u, v$。

向量 $Au$ 和 $Av$ 独立（回顾练习 3.20）。

### 第 2 步：使用高斯集中。

设条件 $a := Au$ 并研究

$$f(Ax) = f(a + Av).$$

由独立性，$a + Av$ 是一个高斯随机向量，可以写成

$$a + Av = a + \|v\|_2 g, \quad \text{where} \quad g \sim N(0, I_m)$$

（再次由练习 3.20）。我们断言函数

$$z \mapsto f(a + \|v\|_2 z)$$

关于 $\mathbb{R}^m$ 上的欧几里得范数是 Lipschitz 的，且 Lipschitz 常数被 $\|v\|_2$ 所限制。为了验证这一点，固定任意 $t, s \in \mathbb{R}^m$ 并利用 $f$ 的次可加性（练习 9.34 的形式）得到

$$f(a + \|v\|_2 t) - f(a + \|v\|_2 s) \le f(\|v\|_2 t - \|v\|_2 s)$$ $$= \|v\|_2 f(t - s) \quad \text{(by positive homogeneity)}$$ $$\le \|v\|_2 \|t - s\|_2 \quad \text{(using (9.36) with $b = 1$)},$$

证明了我们的断言。

高斯空间中的集中（定理 5.2.3）然后给出

$$\|f(a + Av) - \mathbb{E}_a f(a + Av)\|_{\psi_2(a)} \le C \|v\|_2, \tag{9.41}$$

其中下标“a”提醒我们这些界对于条件分布成立，且 $a = Au$ 固定。

### 第 3 步：去掉条件。

由于随机向量 $a - Av$ 与 $a + Av$ 有相同的分布（为什么？），它满足相同的界：

$$\|f(a - Av) - \mathbb{E}_a f(a - Av)\|_{\psi_2(a)} \le C \|v\|_2, \tag{9.42}$$

用 (9.42) 减去 (9.41)，利用三角不等式以及期望相同这一事实；得到

$$\|f(a + Av) - f(a - Av)\|_{\psi_2(a)} \le 2C \|v\|_2.$$

该界对任意固定的 $a = Au$ 条件成立。因此，它对原始分布也成立：

$$\|f(a + Av) - f(a - Av)\|_{\psi_2} \le 2C \|v\|_2.$$

（为什么？）通过 (9.40) 回到 $x, y$ 表示，我们得到期望的不等式 (9.39)。

我们证明了该定理对任意单位向量 $x, y$ 成立。要推广到一般情况，按定理 9.1.2 证明中的第 4 步进行论证（验证！）。$\square$

### 注释 9.6.5。

是否定理 9.6.3 对一般次高斯矩阵 $A$ 成立仍是一个开放问题。

为了练习，尝试练习 9.35 和 9.36 以得到定理 9.6.3 的各向异性和高概率版本。

![](img/b122213aed28c1888de83a894123323e_294_0.png)

![](img/b122213aed28c1888de83a894123323e_294_1.png)

图 9.9 8 维立方体（左）和 10^4 个高斯点（右）的随机投影到平面上

### 定理 9.7.2（Dvoretzky-Milman 定理）。

设 $A$ 为 $m \times n$ 高斯随机矩阵，其元素独立同分布为 $N(0,1)$，且 $T \subset \mathbb{R}^n$ 为有界集。则以下结论以至少 0.99 的概率成立：

$$r_- B_2^m \subset \operatorname{conv}(AT) \subset r_+ B_2^m \tag{9.45}$$

其中 $B_2^m$ 表示 $\mathbb{R}^m$ 中的单位欧几里得球，且

$$r_\pm = w(T) \pm C\sqrt{m}\,\operatorname{rad}(T).$$

左包含仅在 $r_-$ 非负时成立；右包含始终成立。

证明  让我们将双边 Chevet 不等式（定理 9.7.1）表示为以下形式：

$$\mathbb{E}\sup_{y\in S}\Big|\sup_{x\in T}\langle Ax,y\rangle - w(T)\|y\|_2\Big| \le C\gamma(S)\operatorname{rad}(T),$$

其中 $T \subset \mathbb{R}^n$ 且 $S \subset \mathbb{R}^m$。（要得到这个，只需将定理应用于 $A^\top$ 并交换 $T$ 和 $S$。）

设 $S$ 为球面 $S^{m-1}$；其高斯复杂度满足 $\gamma(S) \le \sqrt{m}$。那么，根据 Markov 不等式，以下结论以至少 0.99 的概率成立：

$$\Big|\sup_{x\in T}\langle Ax,y\rangle - w(T)\Big| \le C\sqrt{m}\,\operatorname{rad}(T)\quad\text{for every }y\in S^{m-1}.$$

根据三角不等式和 $r_\pm$ 的定义，这意味着

$$r_- \le \sup_{x\in T}\langle Ax,y\rangle \le r_+\quad\text{for every }y\in S^{m-1}.$$

将 $\sup_{x\in T}\langle Ax,y\rangle$ 重写为 $\sup_{x\in AT}\langle x,y\rangle$ 并利用齐次性，我们得到

$$r_-\|y\|_2 \le \sup_{x\in AT}\langle x,y\rangle \le r_+\|y\|_2\quad\text{for every }y\in \mathbb{R}^m.$$

根据对偶性，这与 $(9.45)$ 相同（尝试练习 9.40 来详细阐述对偶性论证）。
