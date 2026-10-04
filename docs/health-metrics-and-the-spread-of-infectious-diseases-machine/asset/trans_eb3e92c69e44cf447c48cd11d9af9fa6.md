

## 102
## 机器学习应用技术

例如，未标准化的年份数据可能会主导模型的决策过程，导致结果产生偏差。通过对数据进行缩放和中心化，我们可以确保所有特征对模型的预测做出平等的贡献。

我们可以创建包含更多步骤的更复杂的配方，例如，我们将使用一个步骤将位置变量（亚洲、全球）编码为数值向量，并使用第二个步骤对所有预测变量进行归化（或标准化）。

```
rec1 <- recipe(dalys_rabies ~ ~
```

一旦创建了配方，我们就可以使用 `prep()` 函数将其应用于数据，该函数会估计转换所需的参数并将它们应用于数据。然后，为了检查结果，我们使用 `juice()` 函数来提取处理后的数据。

```
rec1 %>%
prep() %>%
juice() %>%
select(1, 2, 5) %>%
head()
# A tibble: 6 x 3
# year dx_rabies dalys_rabies
# dbl      dbl      dbl
# 1 -1.61      2.12   33.1
# 2 -1.17      1.79   30.7
# 3 -1.50      2.02   32.3
# 4 -1.06      1.76   30.5
# 5 -0.847     1.40   27.9
# 6 -0.738     1.23   26.8
```

训练后的数据也可以在新数据上进行测试，在这种情况下，我们使用 `bake()` 函数在测试集上测试。

```
rec1 %>%
prep() %>%
bake(new_data = test) %>%
select(1, 2, 5) %>%
head()
# A tibble: 6 x 3
# year dx_rabies dalys_rabies
# dbl      dbl      dbl
# 1 -1.39      1.94   31.9
# 2 -0.521     0.870   24.5
# 3 -0.412     0.743   23.7
# 4 0.131      0.375   20.7
# 5 -0.738     0.255   20.7
# 6 -0.521     0.043   19.3
```

DALYs 往往汇总了各种健康影响，并可能具有高度偏态的分布。这种偏态源于几个因素：离群值的存在、所测量健康状况的性质以及数据本身的分布。为了处理数据的偏态性，我们可以应用：

- 对数变换：$log(DALY s + 1)$
- 平方根变换：$\sqrt{DALY s}$
- Yeo-Johnson 变换，这是 Box-Cox 变换的推广，可以同时处理正值和负值：((DALY s + 1)^p - 1)/p$。

让我们将 **Yeo-Johnson 变换**应用于响应变量（`dalys-rabies`），并观察分布如何随不同的 $\lambda$ 值而变化。这是一个可以使用机器学习算法进行调优的步骤。

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_121_0.png)

(a) Log10

(b) Yeo-Johnson p=-2

(c) Log10

图 7.3 响应变量变换

让我们使用 `step_YeoJohnson()` 函数创建第三个配方。

```
rec2 <- rec1 %>%
# 对响应变量应用 Yeo-Johnson 变换
step_YeoJohnson(dalys_rabies)
rec2 %>%
prep() %>%
juice() %>%
select(1, 2, 5) %>%
head()
# # a table: 6 x 3
# year dx_rabies dalys_rabies
# dbl <dbl
# 1 -1.06 2.12 5.97
# 2 -1.17 1.79 5.78
# 3 -1.50 2.02 5.91
# 4 -1.06 1.76 5.77
# 5 -0.847 1.40 5.54
# 6 -0.738 1.23 5.44
```

### 7.4.3 相关性、多共线性与过拟合

需要注意的是，我们没有对这些数据应用任何**相关性**选择步骤。过滤掉高度预测的预测变量（例如相关性大于 80% 的变量）以避免多共线性，可能会排除关键变量。另一方面，在模型中包含所有可能的协变量往往会产生不合理的符号或不稳定的系数，以及过拟合。

> Kyle J. Foreman et al., “Modeling Cases of Death: An Integrated Approach Using CODEM,” Population Health Metrics 10, no. 1 (January 2012): 1, doi:10.1186/1478-7954-10-1.

当多个预测变量相关，但它们对分析都至关重要时（例如：狂犬病引起的死亡、总死亡人数和所有原因的总 DALYs），应用过滤相关变量的步骤可能会产生问题。克服这种偏误的一种方法是使用正则化技术，如岭回归（Ridge Regression）或 Lasso 回归，这通常是处理多共线性的最佳方法。或者，主成分分析（PCA）可以在保留大部分方差的同时减少维度。这些方法确保所有预测变量都包含在模型中而不产生多共性的负影响。

### 7.4.4 模型规范

下一步是概述模型规范。可以使用多种模型。我们从随机森林开始。这种类型通常是因为算法的特性，它能够从原始数据创建多个自助样本（带放回的随机采样）。每个自助样本都用于训练一棵决策树。

### 7.4.5 模型 1：随机森林

狂犬病死亡与预测变量之间可能存在复杂的关系。随机森林能够捕捉预测变量与目标变量之间的非线性关系。

此外，它还能处理多共线性、缺失数据，提供变量重要性，并且是一种集成学习方法，这意味着它们通过组合单个决策树的预测来产生更准确、更稳定的预测。

在我们简化的情况下，该模型将对数据进行带放回的随机采样。在 {tidymodels} 中我们可以选择不同类型的引擎，对于随机森林，可以使用 random forest、ranger 等其他。这些引擎之间的区别在于估计时所使用的特定计算类型。

```
rf_mod <- rand_forest(mtry = tune(),
                              trees = tune(),
                              min_n = tune(),
                              mode = "regression",
                              engine = "ranger")
```

```
wkf <- workflow(preprocessor = rec,
                    spec = rf_mod)
```

```
rf_res <- tune_grid(object = wkf,
                               resamples = folds,
                               grid = 5,
                               control = control_grid(save_pred = TRUE))
```

```
show_best(rf_res, metric = "rmse") %>%
              select(-n, -std_err)
```

```
#> A tibble: 5 x 4
#> mtry trees min_n .estimate
#> <int> <int> <int> <dbl>
```

