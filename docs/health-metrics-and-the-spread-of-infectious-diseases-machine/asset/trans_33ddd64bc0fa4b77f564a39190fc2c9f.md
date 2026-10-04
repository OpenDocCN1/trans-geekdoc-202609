
控制计划，通过将资源导向最需要的地区，从而减轻疾病负担。

## 坦桑尼亚的疟疾热点地区
1985–1994

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_280_0.png)

**图 16.2** 该地图显示了坦桑尼亚疟疾病例的分布情况，点的大小和颜色代表了阳性病例的数量。该地图突出了疟疾发病率高的地区，为公共卫生干预提供了宝贵的信息。

## 16.3 示例：模拟疟疾传播动力学

在本示例中，我们将使用来自**疟疾地图项目（Malaria Atlas Project）**的尼日利亚疟疾阳性病例数据，利用简单的数学模型来评估传播动力学。我们将使用机器学习来预测未来趋势。

为了说明建模预测预测过程我们将使用 `{caret}` 包，该包为训练和评估机器学习模型提供了统一的接口。我们将训练一个随机森林模型，根据历史数据预测疟疾传播的未来趋势。

```
niger_cases <- nigeria_data %%
group_by(year_start) %%
reframe(positive = sum(positive)) %%
rename(year = year_start) %%
drop_na() %%
select(year, positive)
```

Time Model: A Case Study of Rufiji and Ifakara Health and Demographic Surveillance Sites in Rural Tanzania," *Malaria Journal* 15, no. 1 (2016年5月): 257, doi:10.1186/s12936-016-1311-9。

示例：模拟疟疾传播动力学

```
head(nigeria_cases)
# # A tibble: 6 x 2
#   year positive
#   <int>  <dbl>
# 1 1985 873
# 2 1987 7
# 3 1988 1276
# 4 1989 134
# 5 1990 352
# 6 1992 92
```

使用折线图可视化尼日利亚疟疾传播的动力学，显示随时间变化的感染病例数。

```
nigeria_cases %>%
ggplot() +
  geom_line(aes(x = year, y = positive),
            color = "navy",
            linetype = "solid") +
  labs(title = "Malaria Transmission Dynamics in Nigeria",
       subtitle = "1985年至2018年的23年间",
       x = "Time(Year)",
       y = "Number of Infected Cases") +
  theme_minimal()
```

## 尼日利亚的疟疾传播动力学
1985年至2018年的23年间

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_281_0.png)

图16.3 该图表显示了1985年至2018年尼日利亚疟疾传播的动力学。蓝线代表随时间变化的感染病例数，突出了这一期间疟疾发病率的波动。

264 疟疾案例

## 16.3.1 使用 caret 进行建模

为了训练一个机器学习模型来预测疟疾传播的未来趋势，我们将使用原始数据的80%来训练模型，并用20%进行测试。然后，我们将使用均方根误差（RMSE）评估其性能。

{caret} 包为R语言中的训练和评估机器学习模型提供了统一的接口（第8章）。它支持广泛的算法并提供了超参数调优、交叉验证和模型评估的工具。

```
# 加载库并检查冲突
library(caret)
conflicted::conflicts_prefer(dplyr::lag)
```

### 16.3.1.1 特征工程

创建滞后变量以捕捉疟疾传播的时间动力学。对于时间序列预测，创建代表目标变量过去值的变量是有帮助的。这允许模型从以前的值中学习。

```
# 创建滞后特征（例如，前年的数据）
nigeria_cases <- nigeria_cases %%
arrange(year) %%
mutate(lag_1 = lag(positive, 1),
       lag_2 = lag(positive, 2),
       lag_3 = lag(positive, 3)) %%
drop_na()
```

```
head(nigeria_cases)
# A tibble: 6 x 5
#   year positive lag_1 lag_2 lag_3
#   <int>    dbl   <dbl> <dbl> <dbl>
# 1  1989    134    1276     7  873
# 2  1990    352    134  1276     7
# 3  1992     92    352  134  1276
# 4  1996    331      92    352  134
# 5  1998     98    331    352    92
# 6  1999     36      98    331    92
```

使用 caret 包中的 `createDataPartition()` 函数创建训练数据和测试数据的划分。

```
set.seed(123)
train_index <- createDataPartition(nigeria_cases$positive,
                                   p = 0.8, list = FALSE)
train <- nigeria_cases[train_index, ]
test <- nigeria_cases[-train_index, ]
```

### 16.3.1.2 模型选择与训练（参数校准）

定义用于研究疟疾动力学的特定机器学习模型。在这种情况下，我们将使用时间和以及滞后病例的数量来预测感染病例的数量。

# 示例：模拟疟疾传播动力学 265

我们将使用 {caret} 包中的 `train()` 函数来训练模型。一个合适的模型将会是？列出可以用于此任务的模型：

- 随机森林 (`rf`)
- 梯度提升 (`gbm`)
- 支持向量机 (`svm`)
- 神经网络 (`mtnet`) - 等

在 `method` 参数中，指定要使用的模型（例如，用于随机森林的 `rf`）。`trControl` 参数指定了用于超参数调优的交叉验证方法，`tuneGrid` 参数定义了用于调优的超参数网格。

```
# 定义带有5折交叉验证的训练控制
train_control <- trainControl(method = "cv",
                              number = 5)

# 定义 mtry 的调优网格
tuning_grid <- expand.grid(mtry = c(1, 2, 3))

# 训练随机森林模型
set.seed(123)
rf_model <- train(
  positive ~ lag_1 + lag_2 + lag_3,
  data = train,
  method = "rf",
  trControl = train_control,
  tuneGrid = tuning_grid,
  ntree = 500) # 树的数量
```

参数校准通过 train 函数使用交叉验证自动完成。

### 16.3.1.3 模型评估

在观测数据上测试模型将显示其在估计感染病例方面的表现。

# 在测试数据进行预测
nigeria_cases$pred <- predict(rf_model, newdata = nigeria_cases)

```
nigeria_cases %>%
ggplot() +
  geom_line(aes(x = year, y = positive),
            color = "navy",
            linetype = "solid") +
  geom_line(aes(x = year, y = pred),
            color = "darkred",
            linetype = "dashed") +
  labs(title = "Malaria Transmission Dynamics in Nigeria",
       subtitle = "Observed vs Predicted - Random Forest",
       x = "Year",
       y = "Number of Infected Cases") +
  theme_minimal()
```

## 尼日利亚的疟疾阳性病例

观测与预测 - 随机森林

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_284_0.png)

**图 16.4** 该图显示了使用随机森林模型生成的尼日利亚疟疾病例观测与预测。蓝线代表观测病例，红线代表预测病例。

为了评估模型预测未来趋势的能力，我们在测试数据上预测感染病例并计算均方根误差（RMSE）。

```
# 计算 RMSE
rmse <- sqrt((test$positive - test$pred)^2)
cat("RMSE:", rmse, "
")
# RMSE: 247.3936
```

均方根误差（RMSE）为 247.3936 表示预测值与实际值之间的平均差异。较低的 RMSE 值表示模型性能越好。

输出显示模型的预测似乎是平稳或下降的，而观测病例显示出剧烈波动。这种不匹配表明当前的模型设置可能无法有效捕捉该数据集中的疟疾传播动力学。
