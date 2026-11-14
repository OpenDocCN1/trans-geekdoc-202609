
由于[练习 17.5](#Chp017_329-360_B9780443218576000217.xhtml#enun0035)中讨论的广义**普适性** [[Wiki](https://en.wikipedia.org/wiki/Zeta_function_universality)]，不等式 ⩾ `ρ` 变为等式：包含原点且未被轨道穿过的最大圆，其半径恰好等于 `ρ`。

我们已经知道，如果 `P` 是全体素数集且 `σ` < 1，则不存在空洞。根据黎曼假设，如果 0.5 < `σ` < 1，原点处的空洞缩减为单元素集；如果 `σ` = 0.5，则缩减为空集。**广义黎曼假设** [[Wiki](https://en.wikipedia.org/wiki/Generalized_Riemann_hypothesis)] 声称，无论**狄利克雷特征** `χ`(·) [[Wiki](https://en.wikipedia.org/wiki/Dirichlet_character)] 如何，这均成立。但如果我们将 `P` 设为**孪生素数** [[Wiki](https://en.wikipedia.org/wiki/Twin_prime)] 集合呢？那么，如果 `σ` = 1，公式 [(17.9)](#Chp017_329-360_B9780443218576000217.xhtml#deq12) 中的乘积收敛，因此当 `σ` = 1 时，存在一个包含原点且 `ρ` > 0 的空洞。这种收敛性是**布伦定理** [[Wiki](https://en.wikipedia.org/wiki/Brun%27s_theorem)] 的直接推论：即孪生素数倒数之和收敛。我未研究 `σ` < 1 的情况。

我现在讨论两个已知满足 [(17.9)](#Chp017_329-360_B9780443218576000217.xhtml#deq12) 的案例。两者均展示了**加性数论** [[Wiki](https://en.wikipedia.org/wiki/Additive_number_theory)] 的方法。思路是考察两个（或更多）整数集合 `A` 和 `B`，然后检查 `A + B` 中整数的稠密度。最著名的例子是**哥德巴赫猜想** [[Wiki](https://en.wikipedia.org/wiki/Goldbach%27s_conjecture)]：它断言，如果 `A = B` 是全体素数集，则 `A + B`（定义为所有满足 `a ∈ A`、`b ∈ B` 的整数 `a + b` 的集合）覆盖所有大于 2 的正偶数。第二个著名例子是 `A = B` 为平方整数集合时。该问题被称为**平方和** [[Wiki](https://en.wikipedia.org/wiki/Gauss_circle_problem)]。此时得到的 `A + B` 过大，不具备我们这里的研究价值。一个更广义的版本是高次幂之和，称为**华林问题** [[Wiki](https://en.wikipedia.org/wiki/Waring%27s_problem)]。如果 `A = B` 是正立方数集合，或 `A` 是正立方数集合而 `B` 是平方数集合，则 `A + B` 足够小，从而得出有趣的结果。现在让我们研究这些热门案例。

### 17.3.2.1 两个立方数之和，或古巴素数

设 `P` 为大于 2 且为两个立方数之和的素数集合。它们被称为**古巴素数** [[Wiki](https://en.wikipedia.org/wiki/Cuban_prime)]，并在 OEIS 整数序列列表中作为条目 [A334520](https://oeis.org/A334520) 和 [A002407](https://oeis.org/A002407) 出现。这些素数形式为 `3*x² + 3*x + 1`，其中 `x` 为正整数。因为古巴素数比平方整数少得多，所以如果 `σ > 0.5`，我们有 `∏[p ∈ P](1 + p^(-σ))^(-1) < ∞`。因此，如果 `σ > 0.5` 且无论 `χ` 如何，相关的 `L[P](z, χ)` 轨道在原点处有一个空洞，半径 > 0（不是单点或空集）。简而言之，如果 `σ > 0.5`，`L[P](z, χ)` 永远不会太接近零。这与标准黎曼 zeta 函数 `ζ(z)` 形成鲜明对比，后者仅当 `σ > 1` 时才具有严格正半径的空洞。

人们推测存在无限多个古巴素数。对于形式为 `x³ + 2*y³` 的素数，相关证明于 2001 年发表，见 [[12]](#Chp017_329-360_B9780443218576000217.xhtml#br0060)。

### 17.3.2.2 与椭圆曲线相关的素数

现在，设 `P = {p[1], p[2], …}` 为形式为 `x³ + y²` 的素数集合，按升序排列。这些素数比形式为 `x² + y²` 的素数少得多，但比形式为 `x³ + y³` 的素数（即古巴素数）多得多。此处 `x, y` 为正整数。注意，如果 `p ∈ P`，则对某些整数 `x ≤ 0`、`y ≥ 0` 有 `y² = x³ + p`。这是**椭圆曲线** [[Wiki](https://en.wikipedia.org/wiki/Elliptic_curve)] 的方程。

当 `n` 足够大时，小于 `n` 且形式为 `x³ + y²` 的正整数个数少于 `n^(5/6)`。我们不知道其中有多少是素数，但知道素数个数必定少于该值。因此 `p[k]` 渐近地大于 `k^(6/5)`。详见 [练习 17.6](#Chp017_329-360_B9780443218576000217.xhtml#enun0040)，基于发布在[此处](https://mathoverflow.net/questions/364559/general-asymptotic-result-in-additive-combinatorics-sums-of-sets)的一个通用求和公式。然后，利用公式 [(17.6)](#Chp017_329-360_B9780443218576000217.xhtml#deq7)，我们得到

```latex
\rho = |L_{P}(z,\chi)| \geqslant \prod\limits_{k = 1}^{\infty}\frac{1}{1 + p_{k}^{\sigma}} \geqslant \prod\limits_{k = 1}^{\infty}\frac{1}{1 + k^{6\sigma/5}}.
```
(17.10)

无论函数 `χ`(·) 如何，公式 [(17.10)](#Chp017_329-360_B9780443218576000217.xhtml#deq13) 中最右边的乘积在 `6*σ/5 > 1`（即 `$\sigma > \frac{5}{6}$`）时（绝对）收敛。因此，不仅当 `$\sigma > \frac{5}{6}$` 时 `L[P](z, χ)` 没有零点，而且存在一个以原点为中心、半径为 `ρ > 0` 的圆（空洞），轨道永不穿越。
