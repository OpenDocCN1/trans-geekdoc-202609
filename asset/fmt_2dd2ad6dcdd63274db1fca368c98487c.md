
- (d) 使用 `G*Power`，我们输入 `f = .1`，分子 `df = 3`，`groups = `，`alpha = .05` 且 `power = .8`。结果为 `N = 109`，或每个指令条件下 `274` 人。

# 第 15 章

## 15.1
选择 `A = 1`（或 `2` 或 `3`）的案例，然后以 `B` 为固定因子运行受试者间方差分析。

| 来源 | df | MS |
|---|---|---|
| `B/A1` | 1,808,925.00 | 4 | 452,231.00 |
| `B/A2` | 623,512.15 | 4 | 155,788.04 |
| `B/A3` | 695,324.34 | 4 | 173,831.09 |

通过相加平方和（`SS`），我们得到 `3,127,761.5`，这与表 `15.3` 显示的 `$SS_{B/A}$` 匹配。通过平均均方（`MS`），我们得到 `260,646.71`，这与表 `15.3` 显示的 `$MS_{B/A}$` 匹配。

| 来源 | df | MS |
|---|---|---|
| `S` | 19 | `$\sigma^2_1+50\sigma^2_2$` |
| `M` | 4 | `$\sigma^2_2+20\sigma_{Items/M}/10\sigma^2_{SM}+200\theta^2_M$` |
| `Items/M` | 45 | `$\sigma^2_2+20\sigma^2_{Items/M}$` |
| `SM` | 76 | `$\sigma^2_2+10\sigma^2_{SM}$` |
| `SItems/M` | 855 | `$\sigma^2_2$` |

`T` 的主效应通过准 `F = $MS_{Items/M} / (MS_{SM} - MS_{Items/M})$` 测量。分子 `df = 4`，分母 `df = $(MS_{Items/M} - MS_{Items/M})^2 / (MS_{Items/M} / 45 + MS_{SM} / 76 + MS_{Items/M} / 855)$`.

```
> aov_out<-summary(aov(data,-R*V*Items:(R*V)))
> aov_out
id Df Sum Sq Value F Pr(F)
R 9 14.91 1.661 .1371
R 1 0.41 0.41 .52495
V 1 34.44 34.44 .7808 ***
id:R 9 9.34 1.04 .41033
id:V 10 10.70 1.19 .30937
R:V 1 8.41 8.41 .00428 **
id:R 9 11.35 1.26 .26143
R:Items 16 40.00 2.50 .00206 **
Residuals 144 143.63 .000
```

# 选练习练习答案

受试者（`S = id`）和项目（`Items`）是随机变量。注意 `R`、`V` 和 `RV` 交互作用的误差项在输出中。我们需要准 `F`。对于 `R`，误差项为 `$MS_{S} + MS_{Items/M} = 2.541$`，当 `S=id`；对于 `V`，它是 `$MS_{V} + MS_{Items/M} = 2.692$`；对于 `RV`，它是 `$MS_{RV} + MS_{Items/M} = 2.763$`。误差 `df` 遵循公式 `14.7`：对于 `V` 为 `12`；对于 `RV` 为 `13`。因此 `$F_R = 12.794 (p=.003)$`；`$F_V = 3.042 (p=.004)$`。

# 15.7
## (a) 来源

| 来源 | df |
|---|---|
| `C` | 2 | `$\sigma^2_2+10\sigma_{SC}^2+20\sigma_{CIF}^2+200\sigma_C^2$` |
| `F` | 1 | `$\sigma^2_2+15\sigma_{SF}^2+60\sigma_{SIF}^2+300\sigma_F^2$` |
| `CF` | 2 | `$\sigma^2_2+5\sigma_{SCF}^2+1000\sigma_{CF}^2$` |
| `S` | 19 | `$\sigma^2_2+10\sigma_{SC}^2$` |
| `SC` | 38 | `$\sigma^2_2+20\sigma_{SCF}^2$` |
| `SF` | 19 | `$\sigma^2_2+30\sigma_{SIF}^2$` |
| `SCF` | 38 | `$\sigma^2_2+40\sigma_{SCF}^2$` |
| `I/F` | 85 | `$\sigma^2_2+60\sigma_{CIF}^2$` |
| `SI/F` | 152 | `$\sigma^2_2+80\sigma_{SM}^2$` |
| `SCI/F` | 304 | `$\sigma^2_2+100\sigma_{CF}^2$` |

## (b)
`C` 的误差项为 `$MS_{SC} + MS_{SCF/F}$`。`F` 的误差项为 `$MS_{SF} + MS_{SIF/F}$`。`CF` 的误差项为 `$MS_{SCF} + MS_{CF/F}$`。对于 `R`，误差项，`$MS_{S} + MS_{Items/M} = 2.541$`，`S=id`；对于 `V`，`$MS_{V} + MS_{Items/M} = 2.692$`；对于 `RV`，`$MS_{RV} + MS_{Items/M} = 2.763$`。误差 `df` 遵循公式 `14.7`：对于 `V` 为 `12`；对于 `RV` 为 `13`。因此 `$F_R = 12.794 (p=.003)$`；`$F_V = 3.042 (p=.004)$`。

# 15.9
## (a)
差异 `$SS_A = 79$`，`$SS_C = 166$`，`$SS_{resid} = 29$`。`$SS_{B/A} = 3127761.5 / 12 = 260646.71$`。`$MS_{B/A} = 260646.71$`。

# 15.11
## (a) 来源

| 来源 | df | 误差 |
|---|---|---|
| `Type (T)` | 3 | |
| `Row (R)` | 3 | |
| `Valence (V)` | 3 | |
| `R/V` | 6 | |
| `R/S` | 6 | |
| `V/S` | 6 | |
| `R/V/S` | 9 | |

# 15.13
## (a) 来源

# EMS 选定练习 770 答案

| 来源 | df | 误差项 |
|---|---|---|
| `SB/C` | 42 | `$\sigma_e^2 + 3\sigma_{SB/C}^2$` |
| `AB` | 2 | `$\sigma_e^2 + 44\sigma_{AB}^2$` 残差 |
| `ABC` | 2 | `$\sigma_e^2 + 22\sigma_{ABC}^2$` 残差 |
| 残差 (`SAB/C`) | 84 | |

`16.5 > summary(aov(data-LongForm,y-(GROUP/id)*(A/B)))`

| DF | 组和 | 均方 |
|---|---|---|
| `GROUP` | 1 | 1910 | 1910 |
| `A` | 2 | 15202 | 7601 |
| `GROUP:id` | 14 | 6858 | 490 |
| `A:B` | 12 | 6705 | 559 |
| `GROUP:A` | 2 | 519 | 259 |
| `GROUP:A:B` | 12 | 7614 | 634 |
| `GROUP:id:A` | 28 | 5819 | 208 |
| `GROUP:id:A:B` | 168 | 71774 | 427 |

`A =` 歧义性（固定）；`B =` 项目（随机）；`GROUP =` 语言组（固定）；`id =` 受试者（随机）

| 来源 | EMS | 误差项 |
|---|---|---|
| `GROUP` | `$\sigma_e^2 + ab\sigma_{Group} + n\sigma_{BxGroup/A}^2 + nab\sigma_{nabilGroup}^2$` | `$MS_{S/Group} + MS_{BxGroup/A} - M_{residual}$` |
| `S/GROUP` | `$\sigma_e^2 + ab\sigma_{S/Group}$` | |
| `A` | `$\sigma_e^2 + n\sigma_{B/A}^2 + b\sigma_{SA/Group}^2 + nb\sigma_{ilA}^2$` | `$MS_{S/Group} + MS_{SA/Group} - M_{residual}$` |
| `B/A` | `$\sigma_e^2 + n\sigma_{B/A}^2$` | |
| `AxGroup` | `$\sigma_e^2 + n\sigma_{BxGroup/A} + b\sigma_{SA/Group}^2 + nbl\sigma_{AxGroup}^2$` | `$MS_{SA/Group} + MS_{BxGroup/A} - M_{residual}$` |
| `BxGroup/A` | `$\sigma_e^2 + n\sigma_{BxGroup/A}^2$` | |
| `SA/GROUP` | `$\sigma_e^2 + b\sigma_{SA/Group}^2$` | |
| 残差 | `$\sigma_e^2$` | |

误差项的 `df` 遵循公式 `14.7`：对于 `Group = 9.39`，对于 `A = 2.348`，对于 `AxGroup = 4.762`

| df | MS | F | p |
|---|---|---|---|
| `GROUP` | 1 | 1910 | | .13 |
| `S/Group` | 14 | 490 | | | |
| `A` | 2 | 7601 | 22.399 | .03 |
| `B/A` | 12 | 559 | | | |
| `AxGroup` | 2 | 259 | 0.625 | .57 |
| `BxGroup/A` | 12 | 634 | | | |
| `SA/GROUP` | 28 | 208 | | | |
| 残差 | 168 | 427 | | | |

# 16.7
## (a)
```
> summary(aov(data=LongFormA,Y-id*A+Error(id/A)))
```
误差: `id`

Df 组和 均方

`id` 19 | 928.7 | 48.88

误差: `id:A`

Df 组和 均方

`A` 3 | 633 | 211.10

`id:A` 57 | 4757 | 83.46

## (b)
```
> summary(aov(data=LongFormB,Y-B*Group+Error(id/B))) #忽略了 A
```
误差: `id`

Df 组和 均方 F Pr>F)

`Group` 3 | 155.7 | 51.90 | 1.074 | 0.388

残差 16 | 773.0 | 48.31

误差: `id:B`

Df 组和 均方 F Pr>F)

`B` 3 | 158 | 52.60 | 0.637 | 0.595

`B:Group` 9 | 1270 | 141.08 | 1.709 | 0.113

残差 48 | 3963 | 82.56

将这些分析合并，`BCR = SS_{GA} - SS_B = SS_{GB} - SS_A = 1270 - 633 = 636`。组针对 `S/G` 进行检验。情况 `(A)` 的检验劣于 `WSR`；在 `(a)` 中，`SA` 是 `B`、`BCR` 和 `WSR` 的合集。

| 来源 df SS MS F p |
|---|---|---|---|---|---|
| `Group (G)` | 3 | 155.7 | 51.9 | 1.074 | .388 |
| `S/G` | 16 | 773.0 | 48.31 | | | |
| `Situation (A)` | 3 | 633 | 211.1 | 2.557 | |
| `Blocks (B)` | 3 | 158 | 52.6 | 0.637 | .595 |
| `BCR` | 6 | 636 | 128.1 | .284 |
| `WSR` | 48 | 3963 | 85.56 | | |

尽管在该例中，`SA` 是一个 `B`、`BCR` 和 `WSR` 的合集，但由于 `A` 的显著性，情况 `(A)` 的检验劣于 `WSR`；在 `(a)` 中，`SA` 是一个 `B`、`BCR` 和 `WSR` 的合集。

# 第 17 章

## 17.1
(b) `0.60`。 (c) `\hat{Y} = 0.00`。 (d) `.384`。 (e) `\hat{Y} = 0.19`。 (f) `.384`。

# 第 18 章

## 18.1
(a) `.212`。 (b) `.216`。 (c) `.00`。 (d) `.09`。 (e) `.30`。

## 774 道练习题答案

## 第19章

## 19.1
(a)
```
> summary(lm(dat$final~dat$pretest))
```
```
Call:
lm(formula = dat$final ~ dat$pretest)
```
Residuals:

| Min | 1Q | 3Q | Max |
| :--- | :--- | :--- | :--- | :--- |
| -19.764 | -8.663 | 1.503 | 7.753 | 14.236 |

Coefficients:

| Estimate | Std. Error | t value | Pr<|t| |
| :--- | :--- | :--- | :--- |
| (Intercept) | -36.0832 | 27.2951 | -1.322 | 0.20470 |
| dat$pretest | 3.5465 | 0.8421 | 4.212 | 0.000662 *** |

Signif. codes: 0 **** 0.001 *** 0.01 ** 0.05 * .1 ' 1

Residual standard error: 10.64 on 16 degrees of freedom

Multiple R-squared: 0.5258, Adjusted R-squared: 0.4961

F-statistic: 17.14 on 1 and 16, p-value: 0.000662

+ (b) `Final = -36.08 + 3.55pretest`

`SE(b) = 27.30`, `SE(b) = .84`.

+ (c)
```
> new.data.frame(frame = c(24,37))
> predict(regout, new, interval="confidence")
```
| fit | lwr | upr |
| :--- | :--- | :--- |
| 1.493202 | 33.22850 | 64.7355 |
| 2.951639 | 85.1701 | 105.1018 |

+ CI for pretest = 24, `[33.28, 64.76]`; for pretest = 37, `[85.17, 105.102]`.

(d) 在 `pretest = 37` 处的估计可能更准确。因为它更接近 `pretest` 分数的平均值（即 `32.3`），因此它的杠率（leverage）较小，标准误差也较小。

+ (e)
```
> predict(regout, new, interval="prediction")
```
| fit | lwr | upr |
| :--- | :--- | :--- |
| 1.493202 | 21.55106 | 76.51299 |

+ Prediction interval for pretest = 24, `[21.55, 76.51]`.

## 19.3
(a) `CI = 131.87 + 1.712`, `z = 34.2`, `SE(b) = .202`, and `SE(b) = 10.05`.

对于 `age = 30`, `CI` 是 `[174.51, 191.89]`;对于 `age = 50`, `CI` 是 `[212.76, 222.14]`.

+ 50 岁者的区间更窄（因此估计值更有可能接近总体平均值），因为 50 岁比 30 更接近平均年龄（`43.898`），因此标准误差更小。

(d) 预测区间为 `[115.20, 251.23]`。

+ 19.5 使用 `b = r sy / sx`，我们发现大学毕业生 (`CG`) 的斜率为 `.599`，而无大学学位人员 (`ND`) 的斜率为 `.799`。每年的工作年限对应大学毕业生增加 `$600 ($599 x $1,000)`，而无大学学位人员则增加约 `$800`。

(b) 我们可以使用 `t` 统计量（见表 `19.1`）测试差异是否显著：`$t = \frac{b_{CG} - b_{ND}}{SE(b_{CG} - b_{ND})}$`，其中 `$s_e^2 = \frac{1}{\frac{1}{SS_{CG}} + \frac{1}{SS_{ND}}}$`

`$SS_{resid} = \frac{(1-t_{CG}^2)SS_{CG} + (1-t_{ND}^2)SS_{ND}}{3996} = \frac{578585.6 + 548506.95}{3996} = N_{CG} + N_{ND} - 4$`

`280.70`使得 `$s_e = 16.75，$t(3996) = -2.38, p < .02$`。无学位人员每年的工作薪资收入显著*大于*大学毕业生。

(c) 所以这里我们面临这样一种情况：大学毕业者的相关性显著大于无学位人员，尽管无学位人员的斜率显著大于大学毕业生。这种表而悖论的原因是大学毕业者的工作年限变异性更大。在这里，未标准化的回归系数说明了一个问题，而标准化回归系数（相关系数）说明了另一个问题。理解这种区别至关重要。
