
我们的近似值，且当 ρ = 1 时，它给出了零偏误的准确结果。如果相关性变弱并趋近于零，真实（模拟）偏误与我们的近似值之间的差距就会打开。这是因为对于回报的短时间序列（T = 60），噪声（测量误差的方差 σ²/(Tσ_f²) ≈ 0.0073）相比信号（真实参数的方差 σ_β² = 0.0202）相当大。对于更长的时间序列，即测量误差更小从而信噪比更大，我们的近似值将给出比此处显示更好的结果。完全忽略相关性，使用 Richardson 和 Wu 的结果（9.8.16），我们可以在零相关情况下得到偏误的准确值。即使在测量误差较大的情况下，他们的公式也能给出准确的结果。然而，在误差之间引入相关性会对偏误产生显著影响，以至于忽略它们不再能对偏误做出合理的预测。这在图 98.3 中可以清楚地看到，随着相关性强度的增加，真实偏误与 Richardson 和 Wu 的预测之间的差距逐渐打开。相关性在实际资产定价检验中的重要性已在图 98.2 中显现，其中偏误因相关性而大幅被抑制。25 个 Fama–French 投资组合误差项中存在正相关性的趋势已在上文指出。将平均相关性定义为平均协方差与平均方差之比，ρ̄ := σ̄_ij / σ̄_i = 0.2804 清楚地表明了 25 个 Fama–French 投资组合特异性回报中存在相当强的正相关性的趋势。¹³

¹³ Kim (1995) 也发现了大约 0.3 的平均相关性，适用于按 25 个投资组合分组的 NYSE/AMEX 证券。最近，Pollet 和 Wilson (2010) 发现 CRSP 中 500 只最大证券之间的平均相关性为 0.237。

## 98.4 结论

我们研究横截面相关特异性误差对使用两阶段回归方法得到的定价模型因子风险溢价估计的影响。资产回报中的横截面相关特异性误差会导致第二阶段横截面回归中用作解释变量的资产贝塔值的测量误差相关。众所周知，不相关的测量误差会导致回归 OLS 斜率估计的向下偏误。在两阶段回归方法中，第二阶段回归中的斜率估计用作定价模型因子风险溢价的估计。使用泰勒近似，我们推导出在存在微小但可能相关的测量误差的情况下斜率估计量的偏误的解析表达式。虽然我们的结果与已知的事实一致，即更大的测量误差会导致斜率估计中更强的衰减偏误，但它揭示了新的效应，即测量误差中的正相关性会降低偏误。一个直观的解释是，在存在正相关性的情况下，解释变量中的误差倾向于朝同一方向变化，从而更像是平移而非扰动解释变量。我们表明，在定价检验中通常使用的资产经验回报中发现的横截面相关性对因子风险溢价估计的偏误有实质性影响。事实上，使用以经验回报中发现的相关性为参数的模拟，我们发现我们对偏误的分析预测与作为模拟平均值确定的实际（真实）偏误之间具有良好的一致性。然而，忽略相关性会导致对偏误的严重高估。因此，我们的结果不仅有助于更好地从定性上理解相关性的影响，而且与基于经验数据的模拟结果显示出非常好的定量一致性。

## 参考文献

- R. J. Bianchi, M. E. Drew, and T. Whittaker (2016). 资产定价模型的预测表现：来自澳大利亚证券交易所的证据. Review of Pacific Basin Financial Markets and Policies, 19, 1650023.
- F. Black, M. C. Jensen, and M. Scholes (1972). 资本资产定价模型：一些实证检验. In M.C. Jensen (ed.), 资本市场理论研究, New York: Praeger.
- G. Connor and R. A. Korajczyk (1988). 平衡 APT 中的风险与回报：一种新检验方法的应用. Journal of Financial Economics, 21, 255-289.
- G. Connor and R. A. Korajczyk (1991). 美国共同基金的属性、行为与表现. Review of Quantitative Finance and Accounting, 1, 5-26.
- G. Connor and R. A. Korajczyk (2010). 资产回报的因子模型. In Encyclopedia of Quantitative Finance, R. Cont (ed.). Chichester: Wiley.
- J. Durbin (1954). 变量中的误差. Review of the International Statistical Institute, 22, 23-32.
- E. F. Fama and K. R. French (2004). 资本资产定价模型：理论与证据. Journal of Economic Perspectives, 18, 25-46.
- E. F. Fama and K. R. French (2015). 五因子资产定价模型. Journal of Financial Economics, 116, 1-22.
- E. F. Fama and J. MacBeth (1973). 风险、回报与均衡：实证检验. Journal of Political Economy, 71, 607-636.
- W. H. Green (2011). 计量经济学分析 7th International ed., New York: Pearson.
- R. Jagannathan, G. Skoulakis, and Z. Wang (2010). 证券回报横截面的分析. In Y. Ait-Sahalia and L. Hansen (eds.), Handbook of Financial Econometrics: Applications. Amsterdam: Elsevier. pp. 73-114.

## 两阶段回归检验中的横截面相关测量误差

- M. C. Jensen (1968). 1945–1964 年期间共同基金的表现. The Journal of Finance, 23, 389–416.
- M. C. Jensen (1972). 资本市场：理论与证据. The Bell Journal of Economics and Management Science, 3, 357–398.
- R. Kan, C. Robotti, and J. Shanken (2013). 定价模型表现与两阶段横截面回归方法. The Journal of Finance, 68, 2617–2649.
- D. Kim (1995). 预期回报横截面中的变量误差问题. The Journal of Finance, 50, 1605–1634.
- D. Kim (2010). 资产定价检验中变量误差问题相关议题. In C. Lee and J. Lee (eds.), Handbook of Quantitative Finance and Risk Management, New York: Springer, pp. 1091–1108.
- S. Kim and G. Skoulakis (2018). 使用大横截面的事后风险溢价估计与资产定价检验：回归校准方法. Journal of Econometrics, 204, 159–188.
- J. Lintner (1965). 风险资产的估值与股票投资组合和资本预算中风险投资的选择. Review of Economics and Statistics, 47, 13–37.
- R. H. Litzenberger and K. Ramaswamy (1979). 个人税收和股息对资本资产价格的影响：理论与实证证据. Journal of Financial Economics, 7, 163–196.
- J. M. Pollet and M. Wilson (2010). 平均相关性与股票市场回报. Journal of Financial Economics, 96, 364–380.
- D. H. Richardson and D. Wu (1970). 变量误差模型中的最小二乘与分组方法估计量. Journal of the American Statistical Association, 65, 724–748.
- T. Schlueter and S. Sievers (2014). 市场贝塔的决定因素：公司特定会计数据与市场状况的影响. Review of Quantitative Finance and Accounting, 42, 535–570.
- J. Shanken (1992). 关于贝塔定价模型的估计. Review of Financial Studies, 5, 1–33.
- W. F. Sharpe (1964). 资本资产价格：在风险条件下的市场均衡理论. The Journal of Finance, 19, 425–442.
- K. C. J. Wie, C. F. Lee, and A. H. Chen (1991). 套利定价理论的多元回归检验：工具变量方法. Review of Quantitative Finance and Accounting, 1, 191–208.

## 附录 98A：斜率估计量的泰勒展开

这里给出了 (98.8) 的推导细节，即 OLS 斜率估计量 (98.7) 的期望值。我们重写 OLS 估计量

```
\hat{\gamma}_1 = \frac{\hat{\beta}' \bar{r}}{\hat{\beta}' \hat{\beta}} = f(\hat{\beta}, \bar{r})
```

作为向量 \hat{\beta} := \beta + u 的函数，其中 \beta' := (\beta_1 - \bar{\beta}, ..., \beta_N - \bar{\beta}) 且 u' := (u_1 - \bar{u}, ..., u_N - \bar{u})，以及 \bar{r} := E(r) + v，其中 E(r)' := (E(r_1) - \bar{E}(r), ..., E(r_N) - \bar{E}(r)) 且 v' = (v_1 - \bar{v}, ..., v_N - \bar{v})。请注意，E(r) 和 \beta 是（已知或未知）参数的向量，而 u 和 v 是向量
