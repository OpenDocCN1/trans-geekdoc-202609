
`mae = mean_absolute_error(yt, y_pred_cv)`

`print(f"R-squared: {r2:.3f}")`

`print(f"RMSE: {mse:.3f}")`

`print(f"MAE: {mae:.3f}")`

`plt.scatter(yt, y_pred_cv)`

`plt.plot([yt.min(), yt.max()], [yt.min(), yt.max()], r='--', label='Ideal Fit')`

`plt.axhline(`

`    0, color='orange', linestyle='--', label='Zero Line')`

`plt.xlabel('Actual')`

`plt.ylabel('Predicted')`

`plt.title('Linear Regression Fitted Results')`

`plt.legend()`

`plt.show()`

> 初始化一个不带截距的 `LinearRegression` 模型
> 将 `LinearRegression` 模型拟合到转换后的数据
> 针对数量超过 30 的社区创建交叉验证拆分
> 执行交叉验证预测
> 计算 R-squared、均方根误差和平均绝对误差评估指标以分析模型性能
> 创建实际值 vs 预测值的散点图
> 在图中绘制一条橙色虚线，作为理想拟合的参考

![](image_link_placeholder)

# 构建并优化你的模型

运行代码后，我们得到了目标值，并能立即注意到一些负值。由于基准模型并不要求完美，平均绝对误差（MAE）相当高：

```text
prediction range: {-34929.0, 12649.0}
R-squared: 0.320
RMSE: 17197.3
MAE: 12568.3
```

显然，拟合效果并不理想，如图 7.11 所示，我们还注意到某些预测值偏离了理想线。事实上，某些预测值低于虚线（虚线代表零）：

![](image_link_placeholder)

> 图 7.11 结果图

预测低于或等于零的预测值占比约为 0.5%：

```text
(y_pred_cv <= 0).sum() / len(y_pred_cv)
0.005187867050741
```

现在我们继续定位正向离群值的行：

```python
print(np.where(y_pred_cv > 100000))
```

我们收到了两个案例：5509 和 8307：

```text
array([5509, 8307])
```

我们还查询了负向离群值：

```python
print(np.where(y_pred_cv < -25000))
```

这里我们得到了一个案例，182：

```text
array([182])
```

在 7.15 中，我们定义了一个可以帮助我们检查离群值的函数。对于每个预测变量，该函数会打印系数以及系数与该特征值相乘的结果，从而明确每个特征对预测的贡献。

# 列表 7.15 系数检查

```python
def report_case(model, data, feature_names, case_name):
    case_values = data[case_name] * model.coef_
    coef_values = case_values
    for feature_name, case_values, coef_values in zip(feature_names, case_values, coef_values):
        print(f"{feature_name:50s}: " + 
              f"{case_values:10.2f} = " + 
              f"{coef_values:0.2f}")
        print("-" * 80)
        print("*" * 66 + f"{np.sum(coef_values):+0.2f}")
```

> 从数据数组中提取指定案例的特征值
> 通过将特征值与相应的系数相乘，计算每个特征的系数值
> 循环并打印特征名称、其值以及对应的系数
> 打印该案例计算出的系数值之和

一旦我们的检查函数就绪，我们就可以开始检查案例 8307，它代表了一个预测值过大的离群值案例：

# 构建并优化你的模型 277

```python
report_case(model=lm,
    data=Xt,
    feature_names=column_transform.get_feature_names_out(),
    case_no=8307)
```

以下是 8307 的结果，显而易见，导致预测成为离群值的额外贡献是由卧室数量引起的（这暗示该属性可能是一个旅舍）。这个高值将最终预测值向上推了：

- onehot_encoding_room_type_home/apt ( 1.00 ) : -8295.89
- onehot_encoding_room_type_Hotel_room ( 0.00 ) : -0.00
- onehot_encoding_room_type_Private ( 0.00 ) : -0.00
- onehot_encoding_room_type_shared ( 0.00 ) : -0.00
- ordinal_encoding_neighbourhood_more_than_30 ( 12.00 ) : +549.07
- ordinal_encoding_type_of_accommodation ( 29649.71 ) : +2655.26
- numeric_minimum_nights ( 1.00 ) : -268.05
- numeric_number_of_reviews ( 0.00 ) : -0.00
- numeric_number_days_last_review ( -1.00 ) : -0.66
- numeric_reviews_per_month ( -1.00 ) : -179.50
- numeric_calculated_host_listings_count ( 15.00 ) : +1470.92
- numeric_availability_365 ( 354.00 ) : +16503.11
- numeric_score ( 0.00 ) : -549.07
- numeric_number_of_reviews_ltm ( 0.00 ) : +0.00
- numeric_number_of_bedrooms ( 18.00 ) : +31867.67
- numeric_number_of_beds ( 18.00 ) : +31283.70
- numeric_number_of_baths ( 2.00 ) : -1787.41
- numeric_imperial_palace_distance ( 22790.84 ) : -859.33
- numeric_nearest_convenience_store ( 149.84 ) : +549.07
- numeric_nearest_train_station ( 545.08 ) : -1043.20
- numeric_nearest_bus_station ( 324.04 ) : -266.55
- numeric_nearest_subway ( 221.93 ) : -17.29
- binary_is_new ( 0.00 ) : -0.00
- binary_is_studio ( 0.00 ) : +0.00
- binary_has_shared_bath ( 0.00 ) : -0.00
- binary_has_half_bath ( 0.00 ) : -0.00
- +131400.95

类似问题的原因是每个特征都是以线性方式建模的。特征的预测贡献是无界的，不会随着特征值的增加或减少而产生最大或最小限制。通常情况下，在模型中引入非线性和交互作用可以缓解此类问题。让我们检查唯一的负值离群值：

```python
report_case(model=lm,
    data=Xt,
    feature_names=column_transform.get_feature_names_out(),
    case_no=182)
```

在这里，问题体现在最小天数的数值上，该值再次太高了，拉低了估计值。事实上，一些房源是作为工工人或学生的住宿，而不仅仅是短期居住。模型确实太简单了，无法捕捉到这些细微差别，如果引入非线性和交互作用本会有帮助的：

```python
- onehot_encoding_room_type_home/apt ( 0.00 ) : -0.00
- onehot_encoding_room_type_hotel_room ( 0.00 ) : -0.00
- onehot_encoding_room_type_Private_room ( 1.00 ) : -11573.6
- onehot_encoding_room_type_Shared_room ( 0.00 ) : -0.00
- ordinal_encoding_neighbour_more_than_30 ( 6.00 ) : -22.24
- ordinal_encoding_type_of_accommodation ( 34.00 ) : +1664.59
- target_encoding_coordinates ( 27178.66 ) : +24343.02
- numeric_minimum_nights ( 120.00 ) : -32166.38
- numeric_number_of_reviews ( 122.00 ) : -1241.88
- numeric_days_since_review ( 132.00 ) : +87.20
- numeric_review_per_month ( 1.33 ) : +2238.41
- numeric_calculated_host_listings_count ( 4.00 ) : +592.25
- numeric_availability_365 ( 0.00 ) : +0.00
- numeric_score ( 4.98 ) : -2069.92
- numeric_number_of_reviews_ltm ( 4.00 ) : -18.33
- numeric_number_of_reviews_ltm_ratio ( 0.03 ) : +54.17
- numeric_number_of_bedrooms ( 1.00 ) : +3570.20
- numeric_number_of_beds ( 0.00 ) : -0.00
- numeric_imperial_palace_distance ( 32506.70 ) : -12252.79
- numeric_nearest_convenience_store ( 5020.81 ) : +18397.51
- numeric_nearest_train_station ( 5689.32 ) : -10888.44
- numeric_nearest_airport ( 31138.11 ) : -76.76
- numeric_nearest_host_station ( 4999.17 ) : -4317.76
- numeric_nearest_subway ( 16976.69 ) : -1322.52
- binary_is_new ( 0.00 ) : -0.00
- binary_is_studio ( 0.00 ) : +0.00
- binary_has_shared_bath ( 0.00 ) : -0.00
- binary_has_half_bath ( 0.00 ) : -0.00
- -31209.99
```

结论，我们的基准模型表明，成功解决 Airbnb 数据集提出的问题需要更好的拟合，以处理正值预测（预测值理上应该是正的）并表示非线性关系和交互作用（大量的卧室表示是一个旅舍，大量的最小天数表示是针对季节性游客的住宿）。在下一节中，我们将解决所有问题。

我们的基准模型表明，成功解决 Airbnb 数据集提出的问题需要更好的拟合，以处理正值预测（预测值理上应该是正的）并表示非线性关系和交互作用（大量的卧室表示是一个旅舍，大量的最小天数表示是针对季节性游客的住宿）。在下一节中，我们将解决所有问题。

# 构建并优化你的模型 281

在下面的小节中，我们将使用贝叶斯优化来优化 XGBoost 解决方案，以在我们的问题上获得最佳性能。

## 7.2.5 优化你的模型

由于 XGBoost 在这个问题上表现良好，我们将花一些时间来精炼参数，并测试不同的提升（boosting）方法和目标函数。我们将使用上一章介绍的贝叶斯优化器 `Optuna`，因为它可以高效地探索 GBDT 超参数搜索空间，并根据之前实验的结果，在短的轮次内自适应地选择要评估的下一组超参数。

如果你的系统中没有 `Optuna`，可以在 shell 或 notebook 单元格中执行命令 `pip install optuna` 进行安装。

代码列表 17 使用 `Optuna` 对我们之前测试过的 XGBoost 回归器进行超参数优化，以找到在东京 Airbnb 数据集上使模型 MAE（平均绝对误差）最小的最优超参数。该列表的核心是目标函数，它使用 `trial.suggest_...` 方法向 `Optuna` 建议不同的超参数值。特别是，它测试了 `gbtree`（梯度提升树）和 `gblinear`。该提升器使用线性模型作为其基础学习器，结合了 L1 和 L2 正化，而不是使用决策树。关于目标函数，它测试了平方误差（squared error）、gamma 目标和 Tweedie 目标（后者融合了 gamma 分布和 Poisson 分布的特点）。在选择提升器或参数时，它会进行修改和添加以适应 `gblinear` 提升器或 Tweedie 的要求。最后，它根据每次测试建议的超参数创建一个 XGBoost 回归器，并执行交叉验证以评估 MAE。该过程将重复指定的试验次数（在本例中为 60 次）。优化完成后，将打印出实现的最佳 MAE 和对应的最佳超参数。

# 代码列表 17 优化 XGBoost 回归器

```python
import optuna

def objective(trial):
    params = {
        'booster': trial.suggest_categorical(
            'booster',
            ['gbtree', 'gblinear']
        ),
        'objective': trial.suggest_categorical(
            'objective',
            ['reg:squarederror', 'reg:gamma', 'reg:tweedie']
        ),
        'n_estimators': trial.suggest_int(
            'n_estimators', 100, 1000
        )
```

# 使用 Optuna 库定义优化目标函数

# 包含用于优化超参数的字典，包括提升器类型、目标函数等

```python
'learning_rate': trial.suggest_float(
  'learning_rate', 0.01, 1.0, log=True
),
'subsample': trial.suggest_float(
  'subsample', 0.3, 1.0
),
'colsample_bytree': trial.suggest_float(
  'colsample_bytree', 0.3, 1.0
),
'max_depth': trial.suggest_int('max_depth', 1, 7),
'min_child_weight': trial.suggest_int('min_child_weight', 1, 7),
'reg_lambda': trial.suggest_float(
  'reg_lambda', 1e-9, 100.0, log=True
),
'reg_alpha': trial.suggest_float(
  'reg_alpha', 1e-9, 100.0, log=True)
)
```

# 根据提升器类型调整超参数

```python
if params['booster'] == 'gblinear':
  keys_to_remove = {
    'colsample_bytree', 'max_depth',
    'min_child_weight', 'subsample'
  }
  params = {
    key:value for key, value in params.items()
    if key not in keys_to_remove
  }
```

# 为 tweedie 目标建议额外参数 'tweedie_variance_power'

```python
if params['objective'] == 'reg:tweedie':
  # 必须在范围 [1, 2) 之间
  params['tweedie_variance_power'] = trial.suggest_float(
    'tweedie_variance_power', 1.01, 1.99
  )
```

# 使用建议的超参数初始化 XGBoost 回归器

```python
xgb = XGBRegressor(**params)
pipeline = Pipeline(
  ['processing'
)
```
