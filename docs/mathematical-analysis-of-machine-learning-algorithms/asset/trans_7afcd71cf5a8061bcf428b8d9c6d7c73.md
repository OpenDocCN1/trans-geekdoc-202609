
由于近似经验风险最小化器满足

$$\phi(\hat{w},\mathcal{S}_n)\leq \epsilon',$$

我们得到

$$(1-\gamma)\phi(\hat{w},\mathcal{D})\leq \epsilon' + \epsilon_n^\gamma(\delta,\mathcal{G},\mathcal{D}).$$

这给出了 $\gamma=0.5$ 时的期望界。

我们用下面的例子来说明推论 3.22。

### 例 3.23

考虑第 3.5 节的例子。我们考虑 $\phi(w,z)$ 的修改定义，

$$\phi(w,z)=\mathbf{1}(f(w,x)\ne y)-\mathbf{1}(f(w_*,x)\ne y),$$

并且函数 $\phi'_j(z)=\phi_j(z)-\mathbf{1}(f(w_*,x)\ne y)$，其中 $\phi_j(z)$ 在第 3.5 节中定义，形成了 $\{\phi(w,z):w\in[0,1]\}$ 的 $\epsilon$-下包络覆盖。例 3.20 表明，对于该覆盖，定理 3.21 的条件对 $\epsilon\leq\epsilon_0$ 成立，其中 $c_0^2=c_0(p)\epsilon_0$，$c_1=c_1(p)$。我们也可以取 $b=2$。取 $\gamma=0.5$，$\epsilon=\epsilon_0=2/n$，$\epsilon'=0$，结合 $N_{LB}(\epsilon,\mathcal{G},L_1(\mathcal{D}))\leq(n+2)/2$，我们得到

$$\epsilon_n^\gamma(\delta/2,\mathcal{G},\mathcal{D})=O\left(\frac{\ln(n/\delta)}{n}\right).$$

还要注意 $\mathbb{E}_{(X,Y)\sim\mathcal{D}}\mathbf{1}(f(w_*,X)\ne Y)=1-p$，我们由推论 3.22 得到以至少 $1-\delta$ 的概率，

$$\mathbb{E}_{(X,Y)\sim\mathcal{D}}\mathbf{1}(f(\hat{w},X)\ne Y)\leq(1-p)+O\left(\frac{\ln(n/\delta)}{n}\right).$$

这表明 ERM 方法的泛化误差以 $O(\ln n/n)$ 的速率收敛到贝叶斯误差。当 $p\in(0.5,1)$ 时，该结果比第 3.5 节中的结果具有更好的收敛速率。速率 $O(\ln n / n)$ 可以使用一种称为“peeling”的稍加精细的技术改进为 $O(1/n)$。我们将其留作练习。

### 例 3.24

一般而言，对于具有 $d$ 个实值参数的有界参数函数类（例如定义在 $\mathbb{R}^d$ 的紧子集上的线性模型 $f(w,x)=w^\top x$），我们期望熵（更多细节见第 5.2 节）表现如下

$$\ln N_{LB}(\epsilon,\mathcal{G},L_1(\mathcal{D}))=O(d\ln(1/\epsilon)).$$

假设方差条件 (3.16) 成立。则它意味着在适当调参 $c_0$ 和 $c_1$ 下成立 (3.14)。通过优化 $c_0$ 和 $c_1$ 之间的权衡，可以证明推论 3.22 中的泛化界意味着收敛速率

$$\mathbb{E}_{\mathcal{D}}L(f(\hat{w},X),Y)\leq\mathbb{E}_{\mathcal{D}}L(f(w_*,X),Y)+O\left(\left(\frac{\ln(n^d/\delta)}{n}\right)^{1/(2-\beta)}\right).$$

### 例 3.25

考虑参数最小二乘回归问题，其中函数类 $\mathcal{F}$ 为凸或非凸但可实现。例 3.18 表明方差条件在 $f_{\mathrm{opt}}(x) \in \mathcal{F}$ 时成立。例 3.24 显示，使用推论 3.22，我们得到以至少 $1-\delta$ 的概率，$$\mathbb{E}_{\mathcal{D}} L(\hat{f}(X), Y) \le \mathbb{E}_{\mathcal{D}} L(f_{\mathrm{opt}}(X), Y) + O\left(\frac{M^2 \ln(n^d/\delta)}{n}\right),$$ 其中 $\hat{f}$ 是 $\mathcal{F}$ 中使用最小二乘损失的经验风险最小化器。

然而，如果函数类 $\mathcal{F}$ 是非凸的，则当模型设定错误时（即当 $f_*(x)=\mathbb{E}[y|x] \notin \mathcal{F}$ 时），方差条件相对于 $f_{\mathrm{opt}}$ 不成立。这意味着与 $f_{\mathrm{opt}}$ 竞争时的收敛速率为 $O(1/\sqrt{n})$。事实上，即使对于只有两个函数的问题，最小二乘问题的最坏情况下也可以得到不超过 $O(1/\sqrt{n})$ 的收敛。例如，我们可以假设 $f_*(X)=0$，并假设 $Y \sim N(0,1)$。考虑 $\mathcal{F}=\{f_1,f_2\}$，其中 $f_{\mathrm{opt}}(X)=f_1(X)=-1$ 且 $f_2(X)=1+1/\sqrt{n}$。那么在 $n$ 个观测下，ERM 将以常数概率选择 $f_2$，这意味着测试损失比最优函数 $f_{\mathrm{opt}}=f_1$ 差 $\Omega(1/\sqrt{n})$（另见命题 8.12）。这说明了凸函数类对最小二乘回归的重要性。

对于核方法等非参数函数类，我们通常期望熵随 $1/\epsilon$ 多项式增长，即 $$\ln N_{LB}(\epsilon,\mathcal{G},L_1(\mathcal{D})) = O(1/\epsilon^q)$$ 对于某个 $q>0$（见第 5 章）。另一种看待非参数模型的方式是，非参数模型的“有效维度”取决于逼近尺度 $\epsilon$，并且当 $\epsilon \to 0$ 时以 $d \approx 1/\epsilon^q$ 增长。

### 例 3.26

设 $\mathcal{G}$ 为单调函数类 $[0,1] \to [0,1]$。则 $\mathcal{G}$ 的下包络熵满足 $\ln N_{LB}(\epsilon,\mathcal{G},L_1(\mathcal{D})) = O(1/\epsilon)$。

在非参数函数的情况下，推论 3.22 可能不是紧的。它可以通过使用一种称为“chaining”的技术来改进，该技术需要使用 $L_2(\mathcal{D})$ 包络数（见定义 3.27），而不是这里考虑的 $L_1$ 下包络数。在本书中，我们只在第 4 章解释 $L_2$ 经验覆盖数的 chaining 技术。关于 $L_2$ 包络数的类似分析可在 van der Vaart and Wellner (1996) 中找到。

## 3.7 一般包络数

在某些应用中，我们感兴趣的是双边一致收敛，它界定误差 $$\sup_{w\in\Omega} |\phi(w,\mathcal{S}_n) - \phi(w,\mathcal{D})|.$$ 为了得到这样的均匀收敛结果，我们可以采用如下定义的双边包络覆盖。

### 定义 3.27（包络数）

设 $\mathcal{G} = \{\phi(w,\cdot): w \in \Omega\}$ 为实值函数类，配备伪度量 $d$。我们称

$$\mathcal{G}(\epsilon) = \{[\phi_1^L(z), \phi_1^U(z)], \dots, [\phi_N^L(z), \phi_N^U(z)]\}$$

在度量 $d$ 下是 $\mathcal{G}$ 的 $\epsilon$-包络，如果对所有 $w \in \Omega$，存在 $j = j(w)$ 使得 $\forall z$

$$\phi_j^L(z) \le \phi(w,z) \le \phi_j^U(z), \qquad d(\phi_j^L, \phi_j^U) \le \epsilon.$$

$\epsilon$-包络数是此类 $\mathcal{G}(\epsilon)$ 的最小基数 $N_{\square}(\epsilon, \mathcal{G}, d)$。量 $\ln N_{\square}(\epsilon, \mathcal{G}, d)$ 称为 $\epsilon$ 包络熵。

特别地，给定分布 $\mathcal{D}$ 和 $p \ge 1$，我们在函数空间中定义 $L_p$ 半范数

$$\|f - f'\|_{L_p(\mathcal{D})} = [\mathbb{E}_{Z \sim \mathcal{D}}|f(Z) - f'(Z)|^p]^{1/p}. \tag{3.19}$$

它诱导出伪度量，记为 $d = L_p(\mathcal{D})$，相应的包络数为 $N_{\square}(\epsilon, \mathcal{G}, L_p(\mathcal{D}))$。

对于 $p = \infty$，$L_{\infty}(\mathcal{D})$-半范数定义为本质上确界半范数，它导致伪度量

$$d(f,f') = \inf \{\omega: \Pr_{\mathcal{D}}[|f(Z) - f'(Z)| \le \omega] = 1\}.$$

然而，当 $p = \infty$ 时，使用 $L_{\infty}$ 包络数不如使用等价的 $L_{\infty}$ 覆盖数概念更常规（见命题 4.3）。

我们有下包络数与不同范数的包络数之间的以下关系。

### 命题 3.28

我们有对所有 $p \ge 1$，

$$N_{LB}(\epsilon, \mathcal{G}, L_1(\mathcal{D})) \le N_{\square}(\epsilon, \mathcal{G}, L_1(\mathcal{D})) \le N_{\square}(\epsilon, \mathcal{G}, L_p(\mathcal{D})).$$

命题 3.28 意味着定理 3.14 也对 $L_p(\mathcal{D})$ 包络数（$p \ge 1$）成立。在方差条件下，定理 3.21 也对 $L_p(\mathcal{D})$ 包络数（$p \ge 1$）成立。由此可知，定理 3.14 和定理 3.21 对所有 $N_{\square}(\epsilon, \mathcal{G}, L_p(\mathcal{D}))$，其中 $p \ge 1$，均适用。然而，对于 $p \ge 2$，可以使用 chaining 技术导出比定理 3.21 更好的均匀收敛界。我们不会在本书记述包络数的此类精细分析，因为包络数在机器学习文献中不如经验和一致覆盖数常用。因此，我们只在第 4 章导出 $L_2$-一致覆盖数的 chaining 分析的后果。利用 Bernstein 不等式对包络数的分析将是类似的。

我们还有包络数的以下性质，可用于导出函数类复合的包络数。

### 命题 3.29

考虑函数类 $\mathcal{F}$ 和 $\mathcal{G}$。对于任意实数 $\alpha$ 和 $\beta$，定义函数类
