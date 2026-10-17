
``` 
#> 13 1.75e-05 0 14
#> 14 4.06e-07 0 15
#> 15 3.94e-07 0 15
#> 16 3.03e-08 0 15
#> 17 5.87e-09 0 15
#> 18 9.43e-10 0 15
#> 19 3.48e-10 0 15
#> 20 2.19e-10 0 15
```

为了提取特定值的模型，我们可以使用`coef()`函数，并指定要使用的λ和γ值。

```r
coef_l0 <- coef(mod_l0, lambda = 1.75475e-03, gamma = 0)
```

不幸的是，这个输出不包含变量名，因此我们手动添加它们。

```r
rownames(coef_l0) <- c("Intercept", colnames(x))
coef_l0
#> 16 x 1 sparse Matrix of class "dgCMatrix"
#>
#> Intercept 4.63847
#> AGE 0.00379
#> SEXFemale -0.03130
#> RACEOther Hispanic .
#> RACENon-Hispanic White .
#> RACENon-Hispanic Black 0.03753
#> RACEOther Race .
#> EDUCATIONNHS .
#> EDUCATIONMoreThanHS .
#> INCOME -0.00535
#> SMOKEQuitSmoke .
#> SMOKEStillSmoke .
#> LEAD .
#> BMI_CAT25<BMI<30 .
#> BMI_CATBMI>=30 0.02760
#> ALCYes .
```

如果我们想要包含带有L0和L2范数项的惩罚，可以将惩罚参数改为`penalty = "L0L2"`，并指定要测试的γ值数量。

```r
mod_l0l2 <- L0Learn.fit(x, y, penalty = "L0L2",
                        loss = "SquaredError",
                        nLambda = 20, nGamma = 10)
```

**L0Learn**包还包含一个使用交叉验证来选择这些参数的函数。不幸的是，它没有提供指定自定义折数的选项。相反，我们使用`nFolds`参数来指定运行5折交叉验证。这个函数还允许我们指定一定数量的λ和γ值，或者我们可以使用默认数量。绘制结果会显示每个模型的估计均方误差和误差条，以及相应的支持大小。

```r
cv_l0l2 = L0Learn.cvfit(x, y, loss = "SquaredError",
                        nFolds = 5, penalty = "L0L2")
plot(cv_l0l2)
```

![](img/58a554e865d49ca347d9a3f76f8f0812_265_0.png)

返回的结果存储在`cvMeans`中。这是一个矩阵列表——每个γ值对应一个矩阵。为了将这些结果提取为更易于管理的形式，我们使用`sapply()`函数将每个矩阵转换为数值向量，并创建一个结果矩阵。该矩阵的列对应于所使用的10个γ值，而该矩阵的每一列对应于为该特定γ值选择的100个λ值。我们使用`which()`函数来找出哪一个具有最低的估计均方误差。

```r
cv_res <- sapply(cv_l0l2$cvMeans, as.numeric)
min_ind <- which(cv_res == min(cv_res), arr.ind = TRUE)
min_ind
#>   row col
#> [1,] 11 10
```

然后，我们可以通过结果中返回的拟合对象提取相应的γ和λ值。

```r
gamma_min <- cv_l0l2$fit$gamma[[min_ind[2]]]
lambda_min <- cv_l0l2$fit$lambda[[min_ind[2]]][min_ind[1]]
```

我们使用`coef()`函数对交叉验证对象`cv_l0l2`来找到该模型的估计系数。

```r
cv_coef_l0 <- coef(cv_l0l2, gamma = gamma_min, lambda = lambda_min)
rownames(cv_coef_l0) <- c("Intercept", colnames(x))
cv_coef_l0
#> 16 x 1 sparse Matrix of class "dgCMatrix"
#>
#> Intercept      4.61671
#> AGE            0.00382
#> SEXFemale      .
#> RACEOther Hispanic .
#> RACENon-Hispanic White .
#> RACENon-Hispanic Black 0.04216
#> RACEOther Race .
#> EDUCATIONNHS .
#> EDUCATIONMoreThanHS .
#> INCOME .
#> SMOKEQuitSmoke .
#> SMOKEStillSmoke .
#> LEAD .
#> BMI_CAT25<BMI<30 .
#> BMI_CATBMI>=30 .
#> ALCYes .
```

最后，我们使用`predict()`函数对`cv_l0l2`来评估我们最终的模型。为此，我们需要指定λ和γ以及我们的数据`x`。这个模型比上一节中的模型稀疏得多，但我们在训练数据上的均方误差略高。

```r
pred_l0l2 <- predict(cv_l0l2, gamma = gamma_min,
                     lambda = lambda_min, newx = x)
mean((nhanes$SBP - exp(pred_l0l2))^2)
#> [1] 275
```

## 15.4 练习

在这些练习中，我们使用来自[第14章](#)的nyts数据。我们关注的结果是某人是否使用任何烟草产品。

1. 创建一个新变量`tobacco_use`，表示过去30天内任何烟草使用情况（包括电子烟、香烟和/或雪茄）。然后，创建一个新的数据框`nyts_sub`，其中包含这个新列以及以下列：地点、年龄、性别、种族、是否认同LGBT群体、过去一年的成绩、感知到的香烟使用、感知到的电子烟使用、心理困扰和家庭富裕程度。

2. 创建一个与`tobacco_use`列对应的结果向量`y`，以及一个包含所有其他协变量的模型矩阵`x`。

3. 使用5折交叉验证拟合L1（套索）、L2（岭）和L0（最佳子集）惩罚回归模型。创建一个包含所有模型对应系数的数据框。务必更新损失函数以反映我们的二元结果。

4. 报告这三个模型在训练数据上的AUC和准确率。

![](img/58a554e865d49ca347d9a3f76f8f0812_268_0.png)

Taylor & Francis

Taylor & Francis Group

http://taylorandfrancis.com

## 案例研究：预测结核病风险

在本章中，我们使用**HDSinRdata**包中第6章看到的`tb_diagnosis`数据集。这些数据包含了南非农村和乌干达城市的1,762名患者的信息，这些患者因结核病相关症状到卫生诊所就诊，并接受了Xpert MTB/RIF结核病检测（Baik et al. 2020）。我们的目标是进行与Baik et al. (2020)类似的回归分析，并利用这些数据推导出一个风险模型，用于在等待Xpert结果期间筛选患者进行治疗。与Baik et al. (2020)不同，我们不将分析局限于简单的整数风险评分模型。

```r
library(tidyverse)
library(HDSinRdata)
library(gt)
library(gtsummary)
library(glmnet)
library(pROC)
```

与Baik et al. (2020)类似，我们使用南非农村的数据来推导风险模型，并使用乌干达城市的数据作为留出验证集。此外，我们将南非的数据按70/30的比例划分为训练集和测试集。

```r
# data from package
data(tb_diagnosis)

# training data
tb_southafrica <- tb_diagnosis %>%
  filter(country == "South Africa") %>%
  select(-country) %>%
  na.omit()

# validation data
tb_uganda <- tb_diagnosis %>%
  filter(country == "Uganda") %>%
  select(-country) %>%
  na.omit()

# train/test split
train_index <- sample(1:nrow(tb_southafrica),
                      0.70*nrow(tb_southafrica),
                      replace = FALSE)

tb_train <- tb_southafrica[train_index,]
tb_test <- tb_southafrica[-train_index,]
```

下表显示了按结核病诊断分层的数据。我们观察到，两组之间的数据非常平衡，并且我们在观察到的临床和人口统计学变量的分布中看到了关键差异。例如，那些血液结果确认为结核病的患者通常表现出更多症状，并且更有可能症状持续超过两周。

```r
tbl_summary(tb_southafrica, by = tb,
            label = list(age_group ~ "Age",
                         hiv_pos ~ "HIV Positive",
                         diabetes ~ "Diabetes",
                         ever_smoke ~ "Ever Smoked",
                         past_tb ~ "Past TB Diagnosis",
                         male ~ "Male",
                         hs_less ~ "< HS Education",
                         two_weeks_symp ~ "Symptoms for Two Weeks",
                         num_symptoms ~ "Number of TB Symptoms")) %>%
  modify_spanning_header(c("stat_1", "stat_2") ~ "**TB Diagnosis**") %>%
  as_gt()
```

| 特征 | 结核病诊断 |  |
|---|---|---|
|  | **0, N = 705** | **1, N = 702** |
| 年龄 |  |  |
| [55,99) | 170 (24%) | 102 (15%) |
| [15,25) | 121 (17%) | 85 (12%) |
| [25,35) | 120 (17%) | 166 (24%) |
| [35,45) | 136 (19%) | 202 (29%) |
| [45,55) | 158 (22%) | 147 (21%) |
| HIV阳性 |  |  |
| 0 | 519 (74%) | 331 (47%) |

