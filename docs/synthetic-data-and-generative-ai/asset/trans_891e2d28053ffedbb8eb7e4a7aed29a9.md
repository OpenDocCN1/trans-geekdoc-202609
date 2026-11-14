
对于其他具有已知`收敛轴` [[Wiki](https://en.wikipedia.org/wiki/Dirichlet_series#Abscissa_of_convergence)] `σ < 1`![Image](images/B9780443218576000217/si9.png) 的 Dirichlet-`L` 函数，请参阅 [[16]](#Chp017_329-360_B9780443218576000217.xhtml#br0080) 中的文章“模椭圆曲线”，第 14–18 页。有趣的是，通过考察级数而非乘积，也证明了 `σ > 5/6`![Image](images/B9780443218576000217/si173.png) 时的（条件）收敛性。形如 `x³ + y²`![Image](images/B9780443218576000217/si161.png) 的素数列在[整数序列百科全书](https://oeis.org/)中，条目为 [A066649](https://oeis.org/A066649)。相关条目包括 [A022549](https://oeis.org/A022549)、[A055393](https://oeis.org/A055393)、[A173795](https://oeis.org/A173795) 和 [A123364](https://oeis.org/A123364)。

`注。` 椭圆曲线理论现在是数论中的一个热门话题。它们被用于 `费马大定理` [[Wiki](https://en.wikipedia.org/wiki/Fermat%27s_Last_Theorem)] 的证明中。该证明于 1995 年发表，距离它首次被猜测已过去 350 多年。该定理指出，如果 `n > 2`![Image](images/B9780443218576000217/si175.png)，则 `x^(n) + y^(n) = z^(n)`![Image](images/B9780443218576000217/si174.png) 在整数中没有非平凡解。

### 17.3.2.3 解析延拓、收敛性与函数方程

如果 `欧拉乘积` 仅在 `σ > 1`![Image](images/B9780443218576000217/si19.png) 时收敛，你需要找到一个延拓到 `σ > 0.5`![Image](images/B9780443218576000217/si115.png) 的方法，以评估当 `0.5 < σ < 1`![Image](images/B9780443218576000217/si90.png) 时 `L[P](z, χ)`![Image](images/B9780443218576000217/si107.png) 是否有零点。一种方法是获得一个 `解析延拓` [[Wiki](https://en.wikipedia.org/wiki/Analytic_continuation)]，至少延拓到 `σ = 0.5`![Image](images/B9780443218576000217/si53.png)。如果 `χ(·)`![Image](images/B9780443218576000217/si4.png) 是常数且等于 1，尝试使用由公式 [(17.4)](#Chp017_329-360_B9780443218576000217.xhtml#deq5) 定义的交错 Dirichlet 级数 `η[P](z, χ)`![Image](images/B9780443218576000217/si88.png)，而不是欧拉乘积，来计算 `L[P](z, χ)`![Image](images/B9780443218576000217/si107.png)。它可能在更大的域上收敛。如果解析延拓满足标准的 `Dirichlet 函数方程` [[Wiki](https://en.wikipedia.org/wiki/Functional_equation_\(L-function\))]，且 `z[0] = σ + i t`![Image](images/B9780443218576000217/si176.png) 是一个满足 `0 < σ < 1`![Image](images/B9780443218576000217/si177.png) 的零点，则 `1 - z[0]`![Image](images/B9780443218576000217/si178.png) 也是一个零点。因此在这种情况下，如果不存在满足 `0.5 < σ < 1`![Image](images/B9780443218576000217/si90.png) 的零点，则任何满足 `0 < σ < 1`![Image](images/B9780443218576000217/si177.png) 的可能零点必须有 `σ = 0.5`![Image](images/B9780443218576000217/si53.png)。当函数方程存在时，可以使用 `指数和` 来导出，例如 $\sum_{k = 1}^{\infty}\exp( - \pi k^{2}y)$![Image](images/B9780443218576000217/si179.png)。请参阅 [[4]](#Chp017_329-360_B9780443218576000217.xhtml#br0020) 中的第 4.1 节（第 71 页）。

如果对于某个 `σ[0]`![Image](images/B9780443218576000217/si104.png) Dirichlet 级数收敛，则它对所有满足 `ℜ(z) = σ > σ[0]`![Image](images/B9780443218576000217/si180.png) 的 `z` 都收敛。由公式 [(17.5)](#Chp017_329-360_B9780443218576000217.xhtml#deq6) 定义的 `η[P]`![Image](images/B9780443218576000217/si181.png) 级数的 `条件收敛轴` 记为 `σ[c]`![Image](images/B9780443218576000217/si182.png)。它是满足以下条件的最小值

```
\sum\limits_{k = 1}^{\infty}{( - 1)}^{k + 1}\chi(k)k^{- \sigma_{c}} < \infty.
```

![Image](images/B9780443218576000217/si183.png)(17.11)

`绝对收敛轴`，记为 `σ[a]`![Image](images/B9780443218576000217/si184.png)，是满足以下条件的最小值

```
\sum\limits_{k = 1}^{\infty}|\chi(k)|k^{- \sigma_{a}} < \infty.
```

![Image](images/B9780443218576000217/si185.png)

注意 `χ(k) ∈ {-1, 0, +1}`![Image](images/B9780443218576000217/si186.png)。只有当 `k` 无法表示为 `P` 中元素的乘积时，它才等于 0。当 `P` 不是完整的素数集合时，就会发生这种情况。类似的论证可用于获得 `L[P]`![Image](images/B9780443218576000217/si187.png) 级数的收敛轴，或用于研究乘积的收敛性。例如，对于公式 [(17.4)](#Chp017_329-360_B9780443218576000217.xhtml#deq5) 中的乘积，条件收敛等价于级数 `∑[p ∈ P] χ(p) p^(-σ)`![Image](images/B9780443218576000217/si188.png) 的收敛。特别地，对于 `χ = χ[4]`![Image](images/B9780443218576000217/si16.png)，即第 [17.2.2](#Chp017_329-360_B9780443218576000217.xhtml#s0045) 节开头介绍的 `模 4 Dirichlet 特征`，`L[P](z, χ)`![Image](images/B9780443218576000217/si107.png) 的级数具有 `σ[c] = 0`![Image](images/B9780443218576000217/si189.png)，因为 `χ[4]`![Image](images/B9780443218576000217/si1.png) 是周期性的，因此公式 [(17.11)](#Chp017_329-360_B9780443218576000217.xhtml#deq14) 中的级数是交错的。

### 17.3.2.4 混合 Dirichlet–Taylor 级数

`欧拉乘积` 的一个有趣推广，令 `χ(p) = x^(ν(p))`![Image](images/B9780443218576000217/si190.png)，如下所示：

```
L_{P}(z,x,\nu) = \prod\limits_{p \in P}\frac{1}{1 - x^{\nu(p)}p^{- z}} = \sum\limits_{k = 1}^{\infty}\varphi(k)x^{\Omega_{\nu}(k)}k^{- z},
```

![Image](images/B9780443218576000217/si191.png)

其中 `ν(p)`![Image](images/B9780443218576000217/si192.png) 定义在素数 `p ∈ P`![Image](images/B9780443218576000217/si165.png) 上。如果利用 `P` 中的素数对 `k` 进行唯一分解为 `k = p[1]^(a[1]) p[2]^(a[2]) p[3]^(a[3]) ...`![Image](images/B9780443218576000217/si193.png)，则 `Ω[ν](k) = a[1] ν(p[1]) + a[2] ν(p[2]) + ...`![Image](images/B9780443218576000217/si194.png)，其中后者求和实际上是有限的。这里 `a[i]`![Image](images/B9780443218576000217/si36.png) 为整数 ⩾0。如果 `k` 无法在 `P` 中分解，例如 `P` 不包含所有素数整数，则 `φ(k) = Ω[ν](k) = 0`![Image](images/B9780443218576000217/si195.png)，否则 `φ(k) = 1`![Image](images/B9780443218576000217/si196.png)。注意 `Ω[ν](·)`![Image](images/B9780443218576000217/si197.png) 是定义在 `Q = Q[P]`![Image](images/B9780443218576000217/si198.png) 上的函数，即由 `P` 生成的乘法群，包含 `P` 中元素的所有乘积组合（包括 1）。事实上，`Ω[ν](·)`![Image](images/B9780443218576000217/si197.png) 推广了 `Omega 函数` [[Wiki](https://en.wikipedia.org/wiki/Prime_omega_function)]。如果 `Q[P]`![Image](images/B9780443218576000217/si199.png) 的元素按（递增顺序）记为 `q[1], q[2]`![Image](images/B9780443218576000217/si200.png)，依此类推，则以下符号更灵活：

```
L_{P}(z,x,\nu) = \prod\limits_{p \in P}\frac{1}{1 - x^{\nu(p)}p^{- z}} = \sum\limits_{k = 1}^{\infty}x^{\Omega_{\nu}(q_{k})}q_{k}^{- z}.
```

![Image](images/B9780443218576000217/si201.png)(17.12)
