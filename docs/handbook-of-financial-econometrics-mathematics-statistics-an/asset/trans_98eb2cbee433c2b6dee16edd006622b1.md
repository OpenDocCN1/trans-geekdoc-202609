
由 Levy (1972) 和 Levhari 和 Levy (1977) 提出。本研究考察的 ex post 关系基于绩效度量及其风险代理的估计量的抽样分布，而 Levy (1972) 和 Levhari 和 Levy (1977) 则以 ex ante 参数来研究该关系，而未具体考虑估计量中的样本变异。此外，他们的结果确定了 n 期间 Treynor（或 Sharpe）度量与其单期间风险度量之间的关系，随着投资期限长度的变化而变化。相比之下，我们考察了估计的 m 期间绩效度量与其 m 期间估计风险代理之间的 m 期间相关性。该 m 期间相关性可以用单期间市场状况（R_f 和 μ）和不同的投资期限来解释。因此，他们的研究和我们的分析考察了两种不同的关系。12 然而，我们分析的结果加强了对该重要关系在 ex post 方面的理解。

总之，在实证研究中检验估计 Treynor 度量与估计系统风险之间的关系时，应使用较短的观察期和较大的样本量。

需要注意的是，估计的 Treynor 度量是 ex ante Treynor 度量的有偏估计量，如方程 (68.9)13 所示：

$$E\left(\frac{\bar{R}-R_f}{\hat{\beta}}\right)=\left(\frac{\mu-R_f}{\beta}\right)e_{\beta},\qquad(68.9)$$

$$e_{\beta}=\frac{\beta}{k\sqrt{2\pi}\left(m^*\sigma_{\hat{\beta}}+\beta\right)}$$

$$\times\sum_{i=0}^{\infty}\left[\left(\frac{-\sigma_{\hat{\beta}}}{m^*\sigma_{\hat{\beta}}+\beta}\right)^{i}\sum_{j=0}^{i}\binom{i}{j}(-m^*)^{(i-j)}2^{(j+1)/2}\Gamma\left(\frac{j+1}{2}\right)m^{j}\right],\qquad(68.10)$$

12 Levy (1972) 和 Levhari 和 Levy (1977) 的结果由 dTm/dβ 和 dSm/dσ 决定，其中 Tm 和 Sm 分别为 m 期间 Treynor 和 Sharpe 度量，而 β 和 σ 为单期间风险度量。此外，他们考察了 m 期间 Sharpe（或 Treynor）度量与其单期间风险度量之间 ex ante 关系的方向，而我们的分析则研究了估计的 m 期间绩效度量与估计的 m 期间风险代理之间 m 期间关联的程度。因此，我们的分析应被视为对他们分析的补充结果，而非替代结果，以理解投资期限对绩效度量与其风险代理之间关系的影响。

13 参见附录 (68B) 的推导。

$m^* = (a' + b'),\; a' = \frac{a - \beta}{\sigma_{\hat\beta}},\; b' = \frac{b - \beta}{\sigma_{\hat\beta}},$

and

$m_j = \int_{a'}^{b'} \frac{x^{[(j+1)/2]-1} e^{-x/2}}{\Gamma[(j+1)/2]\,2^{(j+1)/2}} dx = \text{a chi-square probability (integral)}.$

与估计 Treynor 度量的期望值相关的偏差因子 $e_\beta$ 取决于共同基金（或投资组合）的系统风险值。偏差因子会因不同共同基金（或投资组合）相关的不同系统风险而在不同共同基金（或投资组合）之间变化。因此，使用有偏估计 $(\bar{R} - R_f)/\hat\beta$ 对 Treynor 度量进行共同基金绩效排名，并不会构成 ex ante Treynor 度量 $(\mu - R_f)/\beta$ 的无偏排名。此外，两个估计 Treynor 度量之间的绝对差异也会受到偏差因子 $e_\beta$ 的影响。注意 $[(\bar{R} - R_f)/\hat\beta]/e_\beta$ 不能用作 ex ante Treynor 度量的无偏估计，因为 $e_\beta$ 涉及未知参数。

上述分析适用于具有正贝塔系数的任何单个证券和投资组合。因此，它也适用于有效投资组合。换句话说，对于有效投资组合，估计 Treynor 度量与 $\hat\beta$ 之间的关系为估计 Sharpe 度量与其估计风险度量之间的关系提供了直接的推广。接下来将探讨这一结果。对于有效投资组合，总风险 ($S^2$) 等于贝塔系数平方乘以市场回报的方差 ($S_M^2$)。这是因为非系统风险被分散掉了，即

$S^2 = \hat\beta^2 S_M^2,\quad \hat\beta > 0.\tag{68.11}$

基于有效投资组合中由 (11) 描述的关系，很容易证明方程 (68.5) 和 (68.6) 分别变为 Chen 和 Lee (1981) (CL) 的方程 (68.5) 和 (68.9)，$^{14}$ 即，遵循 (68.5) 和 (68.6)，我们有

(a) β⁺C − 1 = E( β̂ ) E( 1/ β̂ ) − 1

= E( S/S_M ) E( 1/( S/S_M ) ) − 1,  使用 (68.11)

= E( S ) E( 1/S ) − 1 = d,  它在脚注 7 中定义，

(b) σ²_T = Var( ( R̄ − R_f )/ β̂ ) = Var( ( R̄ − R_f )/( S/S_M ) ) = S²_M σ²_sp,

(c) σ²_β = Var( β̂ ) = Var( S/S_M ) = σ²_S / S²_M.

将 (a)、(b) 和 (c) 代入 (68.5) 和 (68.6) 得到

Cov( ( R̄ − R_f )/ β̂ , β̂ ) = Cov( ( R̄ − R_f )/ S , S ), 这是 CL’s (1981) equation (68.5),

(68.12)

ρ( ( R̄ − R_f )/ β̂ , β̂ ) = ρ( ( R̄ − R_f )/ S , S ), 这是 CL’s (1981) equation (68.6).

(68.13)

Similarly, it can be shown that for efficient portfolios, equations (68.7) and (68.8) are equal to CL’s (1981) equations (68.16) and (68.17), respectively. Therefore, the relationship between the estimated Sharpe’s measure and its estimated risk proxy is a special case of the relationship between the estimated Treynor’s measure and the estimated systematic risk, β̂.

估计 Jensen 度量与其估计风险代理之间的实证关系接下来将被考察。

## 68.3 估计 Jensen 度量与其估计风险代理之间的实证关系

遵循 Heinen (1969) 和本文中定义的定义，估计 Jensen 度量与其估计风险代理之间的协方差可以定义为

Cov( α̂_i , β̂_i ) = − X̄_M σ²_i / Σ_{t=1}^n ( X_Mt − X̄_M )²,  (68.14)

X_Mt = R_Mt − R_f,   X̄_M = R̄_M − R_f.  (68.15)

其中“*”表示 m 期间参数或估计。 (68.16) 中的 m 期间 Cov*(α̂_i, β̂_i) 的表达式与方程 (68.7) 中 Cov[(R̂*_i − R*_f)/β*, β̂*] 相似。因此，与估计 Treynor 度量和 Sharpe 度量相关的关系分析和结论可以推广到包括估计 Jensen 度量与其估计风险代理之间的关联。

如果估计的 Jensen 度量 α̂_i 与估计的系统风险 β̂_i 显著相关，则用于检验有效市场假说的残差回报（ε̂_it）的估计将是有偏的。残差回报由以下公式估计

```
ε̂_it = (R_it − R_f) − α̂_i − β̂_i (R_Mt − R_f). (68.17)
```

根据上述结论，在 R_f 小于预期市场回报（μ）的期间，α̂_i 与 β̂_i 呈负相关。然后，α̂_i 与 β̂_i 之间的负相关意味着贝塔系数较低的证券被有利地评估为具有较高的非市场回报（或截距项）α̂_i。因此，使用方程 (68.17) 会导致残差回报被低估。这一结果可以很容易地证明如下：设 α̂'_i 为 β̂_i 与 α̂_i 负相关时的非市场回报估计，则 α_i 被有利评估意味着 α̂'_i 大于 α_i 的真实估计，记为 α̂*_i。那么可以写成

```
α̂'_i = α̂*_i + δ_i,   δ_i > 0. (68.18)
```

使用方程 (68.17) 和 (68.18) 得到方程

```
ε̂'_it = ε̂*_it − δ_i,   δ_i > 0, (68.19)
```

其中 ε̂'_it = (R_it − R_f) − α̂'_i − β̂_i(R_Mt − R_f) 且 ε̂*_it = (R_it − R_f) − α̂*_i − β̂_i(R_Mt − R_f)。方程 (68.19) 表明 ε̂'_it 小于 ε̂*_it。换句话说，如果非市场回报被有利评估，则残差回报会被低估。这意味着估计的平均残差回报和估计的累计平均残差回报将向下有偏。另一方面，高贝塔证券被不利地评估为具有较低的非市场回报。非市场回报的不利评估反过来会导致估计的平均残差回报和估计的累计平均残差回报被高估。¹⁶ 然而，在 α̂_i 与 β̂_i 呈正相关的期间（参见第 68.4 节）

¹⁶ 如果估计的截距项与估计的贝塔系数显著相关，则该分析对市场模型成立。
