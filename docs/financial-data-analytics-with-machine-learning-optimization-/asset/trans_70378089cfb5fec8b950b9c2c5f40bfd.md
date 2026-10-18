

1.  *折叠* `Z` *\-统计量* 对每个可能数字：(4.7) `Z_{i, folded} = |AP_i - EP_i| / sqrt(EP_i * (1 - EP_i) / n) d→ N⁺(sqrt(2/π), 1 - 2/π)` 对于 `i = 1, ..., K`，其中 `N⁺` 表示 *折叠正态分布*。

2.  *卡方拟合优度检验统计量* 对所有可能数字一次性进行：(4.8) `Σ_{i=1}^{K} (n * AP_i - n * EP_i)² / (n * EP_i) d→ χ²_{K-1}`。

折叠正态分布在 `[0, ∞)` 上的密度，记为 `N⁺(μ, σ²)`，由以下公式给出：

```
f(x) = 1 / sqrt(2πσ²) * exp(-(x - μ)² / (2σ²)) + 1 / sqrt(2πσ²) * exp(-(x + μ)² / (2σ²)), 0 ≤ x < ∞.
```

根据中心极限定理，由于 `sqrt(n) * (AP_i - EP_i) / sqrt(EP_i * (1 - EP_i)) d→ N(0, 1)`，折叠正态密度可以在 Python 中使用 `2*norm.pdf(x)` 计算，在 `R` 中使用 `2*dnorm(x)` 计算，分别如此。在卡方拟合优度检验中，[表 4.4](#c04.xhtml#c04-tbl-0004) 是与本福德定律符合程度相关的建议 `p`-值临界水平列表。

[**表 4.4**](#c04.xhtml#R_c04-tbl-0004) 卡方拟合优度检验的“建议五位数检验” `p`-值标准。

| Range | Conformity |
| --- | --- |
| 0.1 to 1 | Close |
| 0.05 to 0.1 | Acceptable |
| 0.01 to 0.05 | Marginally acceptable |
| 0 to 0.01 | Not acceptable |

![](images/c04-gra-0004.png) ![](images/c04-gra-0005.png)

