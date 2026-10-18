

**Example 5.7** 考虑一个亚洲看涨期权，参数为 `S₀ = 10, K = 8, r = 0.05, σ = 0.3`，且 `T = 1`。在 Black–Scholes 框架下，`σ(S̃ₘ⁽ⁱ⁾) ≡ σ` 在 `[5.11](#c05.xhtml#c05-disp-0073)` 中对 `m = 0, …, M − 1` 和 `i = 1, …, n = 100, 000` 成立。我们使用上面讨论的两种离散化方案，通过取不同的 `M ∈ {10, 100, 1000}` 来估计该亚洲看涨期权的当前价格。我们将首先在 [Programme 5.19](#c05.xhtml#c05-gra-00019) 中通过 Python 编写亚洲看涨期权模拟的代码，并在 [Programme 5.20](#c05.xhtml#c05-gra-00020) 中通过 `R` 编写。请注意，为了在此示例中公平比较两种方案，我们还通过标准蒙特卡罗方法为每个候选 `M` 值计算一个“精确”价格，作为比较的基准。读者可以自行验证，通过在程序中选择更大的 `M` 和 `n` 值，可知所讨论的连续算术平均亚洲期权的“精确”理论价格落在 `2.19 ± 0.01` 的范围内。

![](images/c05-gra-0024.png)![](images/c05-gra-0025.png)

为了比较两种离散化方法的性能，考虑 `Ŝₘ⁽ⁱ⁾ − Sₘ⁽ⁱ⁾` 的直方图，其中 `i = 1, …, 10⁵`，每个 `Ŝₘ⁽ⁱ⁾` 由相应的数值方案模拟得到，而每个 `Sₘ⁽ⁱ⁾` 则如 [Example 5.6](#c05.xhtml#c05-fea-0026) 中所述生成。结果在 [Programme 5.19](#c05.xhtml#c05-gra-00019) 中通过 Python 报告（或在 [Programme 5.20](#c05.xhtml#c05-gra-00020) 中通过 `R` 报告）。

![](images/c05-gra-0026.png)![](images/c05-gra-0027.png)![](images/c05-gra-0028.png)

从 [Figures 5.6](#c05.xhtml#c05-fig-0006) 通过 Python 和 [5.7](#c05.xhtml#c05-fig-0007) 通过 `R` 可以看出，当 `M = 10, 100, 1000` 时，Milstein 方案所有直方图的范围远小于 Euler–Maruyama 方案，并且随着 `M` 从 10 增加到 1,000，Euler–Maruyama 与 Milstein 两个范围的比值变大（从约 6.5 增加到约 105）。正如理论所预测的那样，当离散化步数 `M` 增加时，Milstein 方案对亚洲看涨期权价格的近似远优于 Euler–Maruyama 方案。[Table 5.3](#c05.xhtml#c05-tbl-0003) 总结了使用 Python 和 `R` 得到的近似亚洲看涨期权价格，所有近似值都收敛到约 2.19 的真实值。

作为 Black–Scholes 模型的推广，*常数弹性方差*（CEV）模型类在金融行业也很普遍，至少在 2007–2008 年信贷危机之前，用于股票和商品定价等各种目的。这些模型最初由 *John Cox* 在 [\[6\]](#c05.xhtml#c05-bib-0006) 中提出，能够以更灵活的方式捕捉随机波动率和杠杆效应。特别是，通过将基础资产的波动率与其价格水平相关联，得到的 *隐含波动率微笑* ![FIGURE 5.6 The histograms of the sample of modifying above upper S with caret Subscript upper M Superscript left-parenthesis i right-parenthesis Baseline minus upper S Subscript upper M Superscript left-parenthesis i right-parenthesis for i equals 1 comma 2 comma ellipsis comma n for Euler–Maruyama (left) and Milstein (right) schemes at the terminal time upper T via Python, generated in Programme 5.21.](images/c05f006.png)

