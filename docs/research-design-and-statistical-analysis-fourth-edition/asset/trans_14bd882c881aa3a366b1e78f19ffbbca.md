

## 761 选定练习答案

## 第 14 章

14.1 (a) 固定效应：P；随机效应：W, O

| 来源 | | |
| --- | --- | --- |
| W | $\sigma_W^2 + 4\sigma_{WO}^2 + 20\sigma_W^2$ |
| P | $\sigma_P^2 + 10\sigma_{PO}^2 + \sigma_{WPO}^2 + 50\sigma_P^2$ |
| O | $\sigma_O^2 + 4\sigma_{WO}^2 + 40\sigma_O^2$ |
| WP | $\sigma_{WP}^2 + 5\sigma_{WP}^2$ |
| WO | $\sigma_{WO}^2 + 4\sigma_{WO}^2$ |
| PO | $\sigma_{PO}^2 + \sigma_{WPO}^2 + 10\sigma_{PO}^2$ |
| WPO | $\sigma_{WPO}^2$ |

$F_1' = \frac{\frac{MS_P}{(MS_{PO} + MS_{WP} - MS_{WPO})}{640 + 330 - 320}}}{\frac{\frac{(MS_{PO} + MS_{WP} - MS_{WPO})^2}{MS_{PO}^2} + \frac{MS_{WP}^2}{(w-1)(p-1)}}{\frac{(MS_{WPO})^2}{(w-1)(p-1)(o-1)} + \frac{650^2 \cdot 330^2 \cdot 332^2}{12 + 27 + 108}}} = 10.8$
分母自由度为 $df'_{error}$

因此 $p=0.37$。我们拒绝程序没有影响的零假设。

- (c) 对 WP 相对于 $F_{27,108} = MS_{WP}/MS_{WPO} = 1.03, p=.44$ 进行检验。假设 $\sigma_{WP}^2=0$，可以针对 $MS_{WPO}$ 对 P 进行检验。结果为 $F_{3,12} = 4.078, p < .05$。同样，我们拒绝它。

(14.a) summary(aov_car(data,y, A*B+Error(S/A/B)),anova_list(correction("none")))
单变量 Type III 重复测量方差分析 球形性

| | 平和 | DF | 误差平方 | DF | F 值 | Pr(>F) |
| --- | --- | --- | --- | --- | --- | --- |
| (截距) | 811.220 | 1 | 36.467 | 4 | 88.979 | 0.0007042 | *** |
| A | 112.13 | 1 | 14.867 | 4 | 30.1704 | 0.0053535 | ** |
| B | 9.80 | 2 | 2.533 | 8 | 15.4537 | 0.0017801 | ** |
| A:B | 4.07 | 2 | 18.933 | 8 | 0.8592 | 0.059148 | |

注意每个项的误差分别是 SA，对于 A 是 SB，对于 AB 是 SAB。R 语言输出显示了每个项的 $S_{error}$；除以相应的 $df$ (denDf) 即可每个项的 $MS$。

(b) summary(aov_car(data=dot,mean=A+Error(S)))
单变量 Type III 重复测量方差分析 球形性

| | 平和 | DF | 误差平方 | DF | F 值 | Pr(>F) |
| --- | --- | --- | --- | --- | --- | --- |
| (截距) | 270.400 | 1 | 12.1556 | 4 | 88.98 | 0.0007042 | *** |
| A | 37.378 | 1 | 4.9556 | 4 | 30.17 | 0.0053535 | ** |

## 762 选定练习答案

注意 A 和 SA（误差）的平方和是部分 (a) 中值的的三分之一，因为每个“分数”都是原始数据中三个分数的平均值。

| 来源 | EMS |
|---|---|
| S | $\sigma_e^2 + a\sigma_{SB}^2 + ab\sigma_B^2$ |
| A | $\sigma_e^2 + a\sigma_{SAB}^2 + b\sigma_{SA}^2 + n\sigma_{AB}^2$ |
| B | $\sigma_e^2 + a\sigma_{AB}^2 + na\sigma_B^2$ |
| SA | $\sigma_e^2 + a\sigma_{SAB}^2 + b\sigma_B^2$ |
| SB | $\sigma_e^2 + a\sigma_{SB}^2$ |
| AB | $\sigma_e^2 + a\sigma_{SAB}^2 + n\sigma_{AB}^2$ |
| SAB | $\sigma_e^2 + a\sigma_{SAB}^2$ |

- (d) 当 B 是随机的，我们需要对 A 进行准 F 检验。$F_1^A = \frac{MS_A}{MS_{SA} + MS_{AB} - MS_{SAB}} = 33.136$。根据方程 14.8，$df_{error} = 84，$p = .035$。
- (e) 对 B 的水平进行平均并将数据处理为每个参与者只有 $a$ 个分数，忽略了 B 为随机效应时对均 的变异。因此，这种方法会导致第一类错误率膨胀。我们需要在两种假设下估计方差：

| A 固定 | B 随机 |
|---|---|
| S | $(MS_S - MS_{SAB})/ab = 16.000$ | $(MS_S - MS_{SAB})/ab = 16.000$ |
| A | $(a-1)(MS_A - MS_{AB})/ab = 53$ | $(a-1)(MS_A - MS_{SA} - MS_{SAB})/abn = .08$ |
| B | $(b-1)(MS_B - MS_{AB})/ab = 1.04$ | $MS_{SA} - MS_{SAB}/b = 2.80$ |
| SA | $MS_{SA} - MS_{SAB}/b = 2.80$ | $MS_{SA} - MS_{SAB}/b = 2.80$ |
| SB | $(MS_{SB} - MS_{SAB})/a = 7.33$ | $(MS_{SB} - MS_{SAB})/a = 7.33$ |
| AB | $(a-1)(b-1)(MS_{AB} - MS_{SAB})/abn = 1.813$ | $MS_{AB} - MS_{SAB}/n = 27.20$ |
| SAB | $MS_{SAB} = 10.00$ | $MS_{SAB} = 10.00$ |

- ($\alpha$) $\omega_G^2(A) = \sigma_e^2 / (\sigma_e^2 + a\sigma_{AB}^2 + n\sigma_{AB}^2) = .015$
- (b) 现在在分母下估计 B 和 AB。$\omega_G^2(A) = .002$。
- 14.7 (a) > summary(ao_ev=data,"S","Y",between=c("A"),within=c("B")) 对以下变量对比：A 单变量 Type III 重复测量方差分析 球形性

| 平和和 | DF | 误差平方 | den DF | F 值 | Pr(>F) |
| --- | --- | --- | --- | --- | --- | --- |
| (截距) | 8800.2 | 1 | 66.222 | 4 | 531.570 | 2.09e-05 | *** |
| A | 490.0 | 1 | 66.222 | 4 | 29.6510 | 0.000524 | *** |
| B | 447.4 | 2 | 16.444 | 8 | 108.878 | 1.579e-06 | *** |
| A:B | 14.8 | 2 | 16.444 | 8 | 3.5946 | 0.076952 |

## 763 选定练习答案

(b) > summary(ov_ez(data="S","Y",between=c("A"),within=c("B"))) 对以下变量对比：A 单变量 Type III 重复测量方差分析 假设球形性

| 平和和 | num Df | 误差平方 | Den F | F 值 | Pr(>F) |
| --- | --- | --- | --- | --- | --- | --- |
| (截距) | 8800.2 | 1 | 66.222 | 4 | 531.570 | 2.09e-05 | *** |
| A | 490.9 | 1 | 66.222 | 4 | 29.6510 | 0.000524 | *** |
| B | 447.4 | 2 | 16.444 | 8 | 108.878 | 1.579e-06 | *** |
| A:B | 14.8 | 2 | 16.444 | 8 | 3.5946 | 0.076952 |

SS(MA) 和 AS(MA) 的大小是部分 (a) 中的三分分之一，因为每个单元格只有一个“分数”而不是三个。F(A) 是相同的。

- (c) 使用 A = 1 过滤用例，并使用 A = 2。然后在每组集合上运行带有因子 B 的重复测量方差分析；结果将具有 SS(SB/A) 作为 B 的误差。$SS_{SB/A1} = 3.111，$SS_{SB/A2} = 13.333$，相加得到 16.44，$SS_{SB/A}$ 来自部分 14.9。

14.9 Source df

| 来源 | EMS |
|---|---|
| A | $\sigma_e^2 + a\sigma_{SAB}^2 + b\sigma_B^2$ |
| S/A | $\sigma_e^2 + a\sigma_{SAB}^2$ |
| B | $\sigma_e^2 + a\sigma_{AB}^2 + na\sigma_B^2$ |
| SB/A | $\sigma_e^2 + a\sigma_{SB}^2$ |

- (b) 对 A 进行准 F 检验。$F_1' = \frac{MS_A}{MS_{SA} + MS_{AB} - MS_{SAB}} = 22.426$。误差 $df=4.97，$p=.005$。

## 14.11 (a) Source df

| 来源 | df | EMS |
|---|---|
| Between-participants | 71 | |
| X (学校类型) | 1 | $\sigma_e^2 + a\sigma_{XA} + 720\sigma_X^2$ |
| A (年龄) | 2 | $\sigma_e^2 + a\sigma_{XA} + 480\sigma_A^2$ |
| XA | 2 | $\sigma_e^2 + a\sigma_{XA} + 240\sigma_{XA}^2$ |
| S/XA | 66 | $\sigma_e^2 + 25\sigma_{S/XA}$ |
| Within-participants | 72 | |
| T (任务) | 1 | $\sigma_e^2 + a\sigma_{XA} + 720\sigma_T^2$ |
| XT | 1 | $\sigma_e^2 + a\sigma_{XA} + 480\sigma_{XT}^2$ |
| AT | 2 | $\sigma_e^2 + a\sigma_{XA} + 240\sigma_{AT}^2$ |
| XAT | 2 | $\sigma_e^2 + a\sigma_{XA} + 240\sigma_{XAT}^2$ |
| S/XA | 66 | $\sigma_e^2 + 25\sigma_{S/XA}$ |

## 14.3 选定练习答案

## 14.13 (a) https://i.imgur.com/53d31502f4ff3b1c97d65a_784.png

## 14.17 (a) 如果我们考虑这种差分作为因变量的双因素设计，那么问题 14.16(b) 中 $DV^*$Format 的 F 值等于单变量检验中 Format 的 F 值。我们得到 11.75。然后我们使用方程 8 计算 Cohen 的 $f = \sqrt{(1/64)*10} = .41$，根据 Cohen 的指南这是一个大效应。在每个格式下减去 IVT-SVT，我们在*文本*处得到 -3.75，在*网页*处得到 8.281。交互对比是

