
### 表 28.9：合并回归。

```
. regress return beta
```

| 来源 | SS | df | MS |
|---|---|---|---|
| 模型 | .000084304 | 1 | .000084304 |
| 残差 | 24.2017921 | 8,844 | .002736521 |
| 总计 | 24.2018765 | 8,845 | .002736221 |

观测数 = 8,846; F(1, 8844) = 0.03; Prob > F = 0.8607; R-squared = 0.0000; Adj R-squared = -0.0001; Root MSE = .05231

| return | 系数 | 标准误 | t | P>\|t\| | [95% 置信区间] |
|---|---|---|---|---|---|
| beta | .0004806 | .0027382 | 0.18 | 0.861 | -.004887 | .0058482 |
| _cons | .0018154 | .0030781 | 0.59 | 0.555 | -.0042184 | .0078492 |

### 表 28.10：合并回归模型的 Ramsey RESET 检验。

```
. ovtest
```

Ramsey RESET 检验使用 return 的拟合值的幂
Ho: 模型没有遗漏变量
F(3, 8841) = 1.36
Prob > F = 0.2521

模型的设定忽略了样本中的任何未观测异质性。

为了检验 RE 模型中随机效应的显著性，我们发现 LM 统计量（=1.54）在表 28.12 中在 10.72% 水平上显著。鉴于此结果，随机效应具有边际显著性。

F(1728, 7116) 的 0.05 临界值为 1.064（或使用 F 检验打印的概率），因此所有固定效应联合为零的原假设被拒绝。固定效应高度显著。

DWH 检验结果表明，原假设在 0.011 的显著性水平上被拒绝，这意味着随机效应与模型中包含的解释变量之间存在同期相关性。因此 RE 参数估计不一致。鉴于此，FE 模型是适当的设定，因为 RE 模型参数估计可能不一致。

### 表 28.11：随机效应（RE）模型。

```
. xtreg return beta
```

随机效应 GLS 回归
分组变量: firm_ident

观测数 = 8,846
组数 = 1,729

R-sq:
  within = 0.0012
  between = 0.0001
  overall = 0.0000

每组观测数:
  min = 1
  avg = 5.1
  max = 11

corr(u_i, X) = 0 (assumed)

Wald chi2(1) = 2.80; Prob > chi2 = 0.0944

| return | 系数 | 标准误 | z | P>\|z\| | [95% 置信区间] |
|---|---|---|---|---|---|
| beta | -.0054027 | .0032305 | -1.67 | 0.094 | -.0117344 | .0009289 |
| _cons | .0063386 | .0036912 | 1.72 | 0.086 | -.000896 | .0135733 |

sigma_u = .02854326; sigma_e = .05077864; rho = .24010397 (由于 u_i 的方差比例)

### 表 28.12：随机效应的 LM 检验。

```
. xttest0
```

Breusch 和 Pagan 随机效应的拉格朗日乘子检验

return[firm_ident,t] = Xb + u[firm_ident] + e[firm_ident,t]
```

估计结果：

|  | Var | sd = sqrt(Var) |
|---|---|---|
| return | .0027362 | .0523089 |
| e | .0025785 | .0507786 |
| u | .0008147 | .0285433 |

检验：Var(u) = 0
chibar2(01) = 1.54
Prob > chibar2 = 0.1072

### 表 28.13：固定效应估计。

```
. xtreg return beta, fe
```

固定效应（within）回归
分组变量: firm_ident

R-sq:
  within = 0.0012
  between = 0.0001
  overall = 0.0000

corr(u_i, Xb) = -0.0971

观测数 = 8,846
组数 = 1,729

每组观测数:
  min = 1
  avg = 5.1
  max = 11

F(1,7116) = 8.33; Prob > F = 0.0039

| return | 系数 | 标准误 | t | P>\|t\| | [95% 置信区间] |
|---|---|---|---|---|---|
| beta | -.0118795 | .0041161 | -2.89 | 0.004 | -.0199484 | -.0038107 |
| _cons | .0154809 | .0045828 | 3.38 | 0.001 | .0064973 | .0244645 |

sigma_u = .04144764; sigma_e = .05077864; rho = .39985014 (由于 u_i 的方差比例)

F 检验所有 u_i=0: F(1728, 7116) = 1.31; Prob > F = 0.0000

```
. est sto FE
```

### 表 28.14：RE 与 FE 的 DWH 检验。

```
. hausman FE RE
```

系数

|  | (b) FE | (B) RE | (b-B) Difference | sqrt(diag(V_b-V_B)) S.E. |
|---|---|---|---|---|
| beta | -.0118795 | -.0054027 | -.0064768 | .0025508 |

b = 在 Ho 和 Ha 下一致；由 xtreg 得到
B = 在 Ha 下不一致，在 Ho 下有效；由 xtreg 得到

检验：Ho：系数差异不系统

chi2(1) = (b-B)'[(V_b-V_B)^(-1)](b-B) = 6.45
Prob>chi2 = 0.0111

## 28.14 摘要与结论

本章介绍了 DWH 设定检验并提供了其应用的 IV 和面板数据示例。DWH 检验比较替代的参数估计，可以用于辨别内生性问题（遗漏变量、测量误差/变量误差和同时性）、错误的功能形式以及滞后因变量中的同期相关性——序列相关模型、检验模型的替代估计量以及检验替代理论模型。提供了实证应用，说明了 DWH 检验在比较 LS、IV、FE、RE 和 GMM 估计量中的使用。在计量经济学分析中使用 DWH 检验可以获得很多收益而损失很少。

## 参考文献

- Ahn, S. C. and Low, S. (1996). 具有合并截面-时间序列数据的回归模型的 Hausman 检验的重新表述. Journal of Econometrics, 71(1-2), 309-319.
- Amini, S., Delgado, M. S., Henderson, D. J. and Parmeter, C. F. (2012). 固定 vs 随机：四十年后的 Hausman 检验. In Badi H. Baltagi, et al., (eds.), Essays in Honor of Jerry Hausman. Emerald Publishing Limited.
- Arellano, M. (1993). 关于面板数据中相关效应的检验. Journal of Econometrics, 59, 87-97.
- Basmann, R. L. (1960). 关于广义经典线性可识别性检验统计量的有限样本分布. Journal of the American Statistical Association, 55, 650-59.
- Brooks, C. (2014). 金融计量经济学导论, 3rd ed. Cambridge University Press.
- Cameron, A. C. and Trivedi, P. K. (2005). 微观计量经济学：方法与应用, Cambridge University Press.
- Chermak, J. M. and Patrick, R. H. (2001). 可耗竭资源理论的微观计量经济学检验. Journal of Environmental Economics and Management, 42(1), 82-103.
- Dastoor, D. K. (2005). 关于基于广义逆的某些渐近检验统计量的任意性. Econometrics Journal, 8, 292-305.
- Davidson, R. and MacKinnon, J. G. (1987). 隐含备择假设与检验统计量的局部功效. Econometrica, 55(6), 1305-1329.
- Davidson, R. and MacKinnon, J. G. (1984a). 基于人工线性回归的模型设定检验. International Economic Review, 25, 485-502.
- Davidson, R. and MacKinnon, J. G. (1984b). Logit 和 Probit 模型的便捷设定检验. Journal of Econometrics, 25, 241-262.
- Davidson, R. and MacKinnon, J. (1989). 使用人工回归检验一致性. Econometric Theory, 5(3), 363-384.
- Davidson, R. and Zinde-Walsh, V. (2017). 设定检验的进展. Canadian Journal of Economics, 50(5), 1595-1631.
- Dehon, C., Gassner, M. and Verardi, V. (2009). 检测回归分析中影响性离群值的 Hausman 型检验. Economics Letters, 105, 64-67.
- Durbin, J. (1954). 变量中的误差. Review of the International Statistical Institute, 22, 23-32.
- Fama, E. F. and MacBeth, J. D. (1973). 风险、收益与均衡：实证检验. Journal of Political Economy, 81(3), 607-636.
- Frondel, M. and Vance, C. (2010). 固定、随机还是介于两者之间？面板数据估计量的 Hausman 设定检验变体. Economics Letters, 107, 327-329.
- Fuller, W. A. and Battese, G. E. (1973). 具有交叉误差结构的线性模型估计的变换. Journal of the American Statistical Association, 68, 626-632.
- Fuller, W. A. and Battese, G. E. (1974). 具有交叉误差结构的线性模型的估计. Journal of Econometrics, 2, 67-78.
- Greene, W. H. (2018). 计量经济学分析, 8th ed. Prentice Hall: New Jersey.
- Hausman, J. A. (1978). 计量经济学中的设定检验. Econometrica, 46, 1251-1276.
- Hausman, J. A. and McFadden, D. L. (1984). 多项 Logit 模型的设定检验. Econometrica, 52, 1219-1240.
- Hausman, J. A. and Taylor, W. E. (1981). 广义设定检验. Economics Letters, 8, 239-245.
- Holly, A. (1982). 对 Hausman 设定检验的评注. Econometrica, 49, 749-759.
- Holly, A. (1987). 设定检验：概述. In T.F. Bewley (ed.), Advances in Economics and Econometrics: Theory and Applications. Vol 1, pp. 59-97, Cambridge University Press.
- Hui-shyong, C. and Lee, C. F. (1977). 使用合并时间序列和截面数据检验财务分析中的企业和时间效应. Journal of Financial and Quantitative Analysis, 12(3), 457-471.
- Lee, C. F. (1973). 变量误差估计程序及其在资本资产定价模型中的应用. Ph.D. dissertation (State University of New York at Buffalo).
- Lee, C. F., Gupta, M. C., Chen, H. Y. and Lee, A. C. (2011). 不确定性下的最优支付比率与灵活性假说：理论与经验证据. Journal of Corporate Finance, 17, 483-501.
- Liviatan, N. (1963). 基于重访储蓄研究的永久收入假说检验. In C. Christ (ed.), Measurement in Economics. Stanford: Stanford University Press.
- MacKinnon, James G. (1992). 模型设定检验与人工回归. Journal of Economic Literature, 30, 102-146.
- Nakamura, A. and Nakamura, M. (1981). 关于 Durbin、Wu 和 Hausman 提出的若干设定误差检验之间的关系. Econometrica, 49(6), 1583-1588.
- Newey, W. (1985). 广义矩估计设定检验. Journal of Econometrics, 29, 229-256.
- Pace, R. K. and LeSage, J. P. (2008). 空间 Hausman 检验. Economics Letters, 101: 282-284.
- Pesaran, M. Hashem and Richard J. Smith (1990). 线性单方程模型中估计与正交性检验的统一方法. Journal of Econometrics, 44, 41-66.
- Ramsey, J. B. (1969). 经典线性平方分析中的设定误差检验. Journal of the Royal Statistical Society, Series B, 31, 350-371.
- Ramsey, J. B. (1974). 通过设定误差检验进行经典模型选择. In P. Zarembka (ed.), Frontiers of Econometrics. New York: Academic Press.
- Ramsey, J. B. and Schmidt, P. (1976). 设定误差检验中 OLS 和 BLUS 残差使用的进一步结果. Journal of the American Statistical Association, 71, 389-390.
- Ruud, P. (1989). 计量经济学中的设定检验. Econometric Reviews, 3, 211-242.
