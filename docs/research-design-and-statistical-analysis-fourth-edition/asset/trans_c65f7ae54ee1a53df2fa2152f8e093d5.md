

# 多元回归简介 551

## 20.5 使用软件进行多元回归和交叉验证

使用软件进行多元回归与第 17.6.6 节详细介绍的双变量回归方法类似。在 SPSS 中，只需将额外的预测变量添加到自变量列表中即可。在 R 中，额外的预测变量包含在 `lm` 函数的回归方程中，并在它们之间用 `+` 号连接；`reg_out <- lm(data = dat, Y ~ X1 + X2)`；截距和部分斜率参数的置信区间可以使用 `{stats}` 包中的 `confint` 函数获得，该函数接受回归输出作为输入：`confint(reg_out)`。

交叉验证涉及几个步骤，可以在 R 中快速完成：

- 1. 通过随机采样某百分比的案例并保存样本案例编号来识别数据训练集。R{base}` 中的 `sample` 函数是一个好用的工具。如果你有 126 个案例并想对其采样 25%，则 `train.index <- sample(seq(1:126), 32)` 将从 1 到 126 的集中随机存储 32 个整数。
- 2. 将这些案例分配到训练集，`train.set <- datcv(train.index)`，并将剩余案例完成测试集，`test.set <- datcv(train.index)`。
- 3. 对所有预测变量运行回归并查看结果：`model.cv <- lm(tc ~ ., data = train.set)`。此时，你可以使用 `{stats}` 中的 `step` 函数对这些预测变量进行逐步回归（第 21 章），尽管这不是交叉验证的必要部分。如果你包含了此步骤，请务必存储结果：`model.cv <- step(model.cv, scope = lower(Y ~ 1), upper = lm(Y ~), direction = "both")`。`scope` 参数指定了考虑的模型范围，其中 `Y ~ 1` 表示带有截距的模型，`Y ~` 表示包含所有预测变量的模型。
- 4. 使用训练案例生成的模型计算并存储测试案例的 Y 值（第 19.3 节）：`predictions.cv <- predict(model.cv, test.set)`。
- 5. 最后，计算预测值和观测值的 $R^2$：`cor(predictions.cv, test.set)^2`。R 中额外的交叉验证方法由 Rooij 和 Witten (2020) 描述。

在 SPSS 中，交叉验证不是自动化的，但可以通过以下步骤轻松实现：

- 1. 使用 Data 下拉菜单中的 `Select Cases` 选项随机选择案例样本，然后点击 `Random sample size` 单选按钮。
- 2. 在选定的样本（即训练集）上运行回归。
- 3. 使用 `Transform` 菜单通过在 `Numeric Expression` 中输入你得到的回归方程来计算新变量 Y。不要点击 OK，而是点击底部的 `If...` 栏并选择 `Case satisfies condition` 单选按钮，然后在方框中输入 "filter=0"。这将仅对不在训练集的案例计算 Y 的预测值。
- 4. 最后，选择所有案例并计算观测 Y 值与新预测 Y 值 之间相关性的平方；这将是测试案例的 $R^2$。

## 552 研究设计与统计分析

## 20.6 TC 的多元回归分析

我们已经识别并讨论了回归方程的组成部分，并解释了如何使用软件生成分析。现在我们使用第 20.2 节中给出的初步分析数据来说明计算过程。20.7 展示了 TC 对年龄和 BMI 回归的 R 输出。拆解图 20.7 所示的分析：

- 1. 系数面板中的 `Estimate`（估计值）列提供了 Y 截距 ($b_0$) 以及 $X_1, X_2, b_1$ 和 $b_2$ 的未标准化回归系数（或部分斜率系数）的最小二法估计值。这些条目表明最小二法回归方程包含了年龄和 BMI 作为预测变量：$\hat{Y} = 92.239 + 1.737X_1 + 1.474X_2$。
- 2. 方程 20.9 的图显示在图 20.8 中，数据点；残差由连接每个数据点与其预测值的线表示。我们现在拥有的不是通过双变量回归得到的回归线，而是一个二维回归平面。如果 BMI 保持不变，年龄变化一个单位对应于预测 TC 增加 1.737 单位。同样，如果年龄保持不变，变化一个单位对应于预测 TC 增加 1.474 单位。

```
> tc.age.bmi<-lm(data,tc~age+bmi)
> summary(tc.age.bmi)
```

```
Call:
lm(formula = tc ~ age + bmi, data = dat)

Residuals:
Min Median Max
-107.7090 -19.146 -2.168 20.492 114.959

Coefficients:
Estimate Std. Error t value Pr(>|t|)
(Intercept) 92.2387 16.9214 5.451 1.65e-07 ***
age 1.7370 0.2372 7.322 8.12e-12 ***
bmi 1.4739 0.5400 2.730 0.00698 **

Signif. codes: 0 **** 0.001 *** 0.01 ** 0.05 * 1

Residual standard error: 33.6 on 178 degrees of freedom
Multiple R-squared: 0.2723, Adjusted R-squared: 0.2642
F-statistic: 33.31 on 2 and 178 DF, p-value: 5.154e-13
```

图 20.7 65 岁及以下且 BMI 为 40 或更低的女性 TC 与年龄及 BMI 回归的 R 输出。

![](img/53d3130502f4ff3b15cbe3697d6e8c5a_573_0.png)

- 将这些系数与初步分析中发现的多元和双变量系数进行比较：在 20.2 节中，*age* 的系数为 1.812，*BMI* 的系数为 1.934。多元与双变量系数之间的差异是因为 *age* 和 *BMI* 相关（$r=.12$），所以当调整每个预测变量时，多元回归系数会变化。
- 2. 在图 20.7 输出底部，我们看到多元相关系数 *Multiple R-squared* 为 .272。这意味着方程 20.9 预测的 TC 值与样本中的实际 TC 值之间的相关性为 $\sqrt{.272}=.522。多元判定有时被称为判定系数，它告诉我们回归解释了方差的比例。标准误差 33.6 衡量了回归预测 TC 的效果。

 如果总体模型为 $Y_i = \beta_0 + \beta_1X_1 + \beta_2X_2 + \dots + \beta_pX_p + \varepsilon_i$，标准误差提供了 $\varepsilon$ 标准差的估计。
- 4. 图 20.9 所示的 R ANOVA 表允许我们计算胆醇水平的总平方和，276,210。我们还看到它可以被分为两个部分：回归解释的平方和 $SS_{regression}$ 等于 *age* 和 BMI 的平方和，以及未解释的平方和 $SS_{residual}$，其中：

```
SS_{regression} = \sum(Y_i - \hat{Y}_i)^2 = R^2SS_Y = 75,221$
```

以及

```
$SS_{residual} = \sum(Y_i - \hat{Y}_i)^2 = (1-R^2)SS_Y = 200,989$
```

> > anova(tc.age.bmi)
Analysis of Variance Table

| Response: tc | D Sq Mean Sq F value Pr(>F) | | |
|---|---|---|---|---|---|
| age | 1 | 66808 | 66808 | 59.1664 | 9.512e-13 | *** |
| bmi | 1 | 8413 | 8413 | 7.4053 | 0.00698 | ** |
| Residuals | 178 | 200989 | | | 1129 | |

