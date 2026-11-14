

## 表 11.1

| 方法 | 参数 | N | 胜率% | 值 | 结果 |
|--------|-------|---|------|-------|--------|
| Dirichlet4 | 3 | 70 | 49.65% | 0.4715 | 失败 |
| Logistic | 0.181517 | 115 | 49.82% | 0.539 | 通过 |
| Logistic | 0.72 | 254 | 49.37% | 1.1905 | 通过 |
| Python | 0 | 220 | 49.71% | 1.0311 | 通过 |
| Python | 1 | 150 | 50.03% | 0.7031 | 通过 |
| Python | 2 | 279 | 49.46% | 1.3077 | 通过 |
| Python | 4 | 365 | 50.81% | 1.7108 | 失败 |
| Python | 100 | 386 | 49.10% | 1.8092 | 失败 |
| Python | 200 | 922 | 52.29% | 4.3214 | 失败 |
| Python | 500 | 258 | 49.67% | 1.2093 | 通过 |
| SQRT | (2,5) | 146 | 49.63% | 0.6843 | 通过 |
| SQRT | (90,91) | 1236 | 53.07% | 5.7932 | 失败 |

![表 11.1](images/B9780443218576000151/t0010.png)

## 图 11.1

![图 11.1 L(z,χ) 在 σ = 1/2 处的轨道，其中 0 < t < 200 且 χ = χ4（左图）与伪随机 χ（右图）的对比。](images/B9780443218576000151/gr001.jpg)

图 11.1 `L(z,χ)` 在 `σ = 1/2` 处的轨道，其中 `0 < t < 200` 且 `χ = χ4`（左）与伪随机 `χ`（右）的对比。

## 讨论

如果公式 [(11.1)](#Chp011_203-228_B9780443218576000151.xhtml#deq1) 中的欧拉乘积对于某个 `σ` > `σ`[0]![Image](images/B9780443218576000151/si69.png) 收敛，那么当 `σ` > `σ`[0]![Image](images/B9780443218576000151/si69.png) 时，它等于其级数展开，它对所有 `σ` > `σ`[0]![Image](images/B9780443218576000151/si69.png) 收敛，且当 `σ` > `σ`[0]![Image](images/B9780443218576000151/si69.png) 时 `L(z, χ)`![Image](images/B9780443218576000151/si61.png) 满足 GRH。当 `σ` < 1![Image](images/B9780443218576000151/si70.png) 时，收敛是 `conditional` [[维基百科](https://en.wikipedia.org/wiki/Conditional_convergence)]，这使问题变得更加困难。另一个如果 `$\sigma > \frac{1}{2}$`![Image](images/B9780443218576000151/si66.png) 就平凡满足 GRH 的例子是：当 `χ(·)`![Image](images/B9780443218576000151/si2.png) 是一个随机变量，对于素数 `p` 有 `$P[\chi(p) = 1] = P[\chi(p) = -1] = \frac{1}{2}$`![Image](images/B9780443218576000151/si71.png)。在这种情况下，收敛意味着 `L(z, χ)`![Image](images/B9780443218576000151/si61.png) 具有有限期望（由公式 [(11.2)](#Chp011_203-228_B9780443218576000151.xhtml#deq2) 证明），且具有有限方差。这个函数 `χ(·)`![Image](images/B9780443218576000151/si2.png) 称为 `random Rademacher multiplicative function`，见 [[7]](#Chp011_203-228_B9780443218576000151.xhtml#br0035)。这里 `χ(p)`![Image](images/B9780443218576000151/si12.png) 在全体素数集合上独立同分布，并通过公式 `χ(ab) = χ(a)χ(b)`![Image](images/B9780443218576000151/si4.png) 将定义推广到所有严格正整数。

因此，如果我们能找到一个“足够好”的伪随机但确定性函数 `χ(·)`![Image](images/B9780443218576000151/si2.png)，使得欧拉乘积在 `σ` > `σ`[0]![Image](images/B9780443218576000151/si69.png) 时收敛，其中某个 `σ`[0] < 1![Image](images/B9780443218576000151/si72.png)，该函数 `χ(·)`![Image](images/B9780443218576000151/si2.png) 在素数上具有足够的随机性（像其姊妹函数——真正的随机版本一样）以保证乘积收敛，那么这将是证明 GRH 道路上的一个重大里程碑。乘积的收敛将意味着：

*   `L(z, χ)`![Image](images/B9780443218576000151/si61.png) 是 `analytic` [[维基百科](https://en.wikipedia.org/wiki/Analytic_function)]（解析的），因为乘积等于其级数展开，后者平凡地满足 `Cauchy–Riemann equations` [[维基百科](https://en.wikipedia.org/wiki/Cauchy%E2%80%93Riemann_equations)]（柯西-黎曼方程），
*   如果 `σ` > `σ`[0]![Image](images/B9780443218576000151/si69.png)，`L(z, χ)`![Image](images/B9780443218576000151/si61.png) 没有零点，因为乘积没有零点。

正如所讨论的，存在“不那么好”的例子；“足够好”意味着 `L(z, χ)`![Image](images/B9780443218576000151/si61.png) 满足一个 `Dirichlet functional equation` [[维基百科](https://en.wikipedia.org/wiki/Functional_equation_\(L-function\))]。通常，“足够好”意味着 `L(z, χ)`![Image](images/B9780443218576000151/si61.png) 是一个 `Dirichlet-L function` [[维基百科](https://en.wikipedia.org/wiki/Dirichlet_L-function)]。除了 `Riemann zeta function`（黎曼 zeta 函数）中 `χ(p) = 1`![Image](images/B9780443218576000151/si73.png) 是平凡 `Dirichlet character`（狄利克雷特征）的情况外，最基本的例子是当 `χ = χ4`![Image](images/B9780443218576000151/si74.png) 是模 4 的非平凡 `Dirichlet character modulo` [[维基百科](https://en.wikipedia.org/wiki/Dirichlet_character)] 时。这个例子在 [图 11.1](#Chp011_203-228_B9780443218576000151.xhtml#f0010) 中展示，其中 `σ = 1/2`![Image](images/B9780443218576000151/si75.png)（左图），并与右图中一个不那么好的例子形成对比，右图对应一个伪随机序列 `{χ(p_k)}`![Image](images/B9780443218576000151/si68.png)。`χ4`![Image](images/B9780443218576000151/si76.png) 例子在 [表 11.1](#Chp011_203-228_B9780443218576000151.xhtml#t0010) 中被称为 `Dirichlet4`。注意，对于 `σ = 1/2`![Image](images/B9780443218576000151/si75.png)，`L(z, χ4)`![Image](images/B9780443218576000151/si77.png) 像黎曼 zeta 函数一样有无限多个零点，尽管它的零点不同：看 [图 11.1](#Chp011_203-228_B9780443218576000151.xhtml#f0010) 左图就很明显。（推测的）无零点区域是当 `1/2 < σ < 1`![Image](images/B9780443218576000151/si78.png) 时。

我甚至计算了 `L(z, χ4)`![Image](images/B9780443218576000151/si77.png) 在 `z = σ = 0.99`![Image](images/B9780443218576000151/si79.png) 时的欧拉乘积。它很好地收敛到正确值，没有缺乏收敛性时典型的发散振荡，与使用公式 [(11.1)](#Chp011_203-228_B9780443218576000151.xhtml#deq1) 中级数展开计算出的值一致。这意味着该乘积至少对所有满足 `σ = ℜ(z) ≥ 0.99`![Image](images/B9780443218576000151/si80.png) 的 `z` 收敛。因此，如果 `σ ≥ 0.99`![Image](images/B9780443218576000151/si81.png)，`L(z, χ4)`![Image](images/B9780443218576000151/si77.png) 没有零点。如果能在理论上证明相关收敛性（目前仅有经验证据支持），这将比已知的最佳结果（无零点如果 `σ ≥ 1`![Image](images/B9780443218576000151/si82.png)）是一个巨大的里程碑。收敛意味着序列 `{χ4(p_k)}`![Image](images/B9780443218576000151/si83.png) 在素数 `p1, p2`![Image](images/B9780443218576000151/si84.png) 等上足够随机。也就是说，序列中 +1 和 −1 之间的间隙永远不会增长得太大（即相同值的连续段只能以有限速度增长），并且尽管存在已知的 `Chebyshev's bias` [[维基百科](https://en.wikipedia.org/wiki/Chebyshev%27s_bias)]，+1 和 −1 的比例仍足够快地趋向 `1/2`![Image](images/B9780443218576000151/si9.png)。当序列使用越来越多项时，比例最终收敛到 `1/2`![Image](images/B9780443218576000151/si9.png) 这一事实，是 `Dirichlet's theorem` [[维基百科](https://en.wikipedia.org/wiki/Dirichlet%27s_theorem_on_arithmetic_progressions)]（狄利克雷定理）的结果。这就是我们距离证明 GRH 有多近——或者你可以说有多远。

