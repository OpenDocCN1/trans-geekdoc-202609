

```python
... print(np.sqrt(mean_score), params)

6369.0579127153 {'max_features': 2, 'n_estimators': 3}
55627.16173107252 {'max_features': 2, 'n_estimators': 10}
53384.5766737289 {'max_features': 2, 'n_estimators': 30}
60965.99185953019 {'max_features': 4, 'n_estimators': 3}
52740.98245828583 {'max_features': 4, 'n_estimators': 10}
50377.34440953019 {'max_features': 4, 'n_estimators': 30}
58063.3477332748 {'max_features': 6, 'n_estimators': 3}
52006.1355997137 {'max_features': 6, 'n_estimators': 10}
50146.4659453085 {'max_features': 6, 'n_estimators': 30}
57869.25408027614 {'max_features': 8, 'n_estimators': 3}
51711.09443360957 {'max_features': 8, 'n_estimators': 10}
49682.2354594235 {'max_features': 8, 'n_estimators': 30}
62095.08888990504 {'bootstrap': False, 'max_features': 2, 'n_estimators': 3}
54658.14438490074 {'bootstrap': False, 'max_features': 2, 'n_estimators': 10}
59470.39594730654 {'bootstrap': False, 'max_features': 3, 'n_estimators': 10}
57275.01901081235 {'bootstrap': False, 'max_features': 3, 'n_estimators': 30}
57490.61295685226 {'bootstrap': False, 'max_features': 4, 'n_estimators': 30}
51089.15415482374 {'bootstrap': False, 'max_features': 4, 'n_estimators': 10}
```

在这个示例中，我们通过将 `max_features` 超参数调整为 8，`n_estimators` 超参数调整为 30，得到了最佳解决方案。该组合的 RMSE 分数为 49,682，这比你之前使用默认超参数值得到的得分（50,182）稍微好一点。恭喜你，你成功地微调了你的最佳模型！

![](img/0684d2da98e09085c0a622d4fd69aaad_106_0.png)

不要忘记，你可以将某些数据准备步骤视为超参数。网格搜索会自动发现是否添加某个你不确定的特征（例如，使用你的 `CombinedAttributes` 转换器的 `add_bedrooms_room` 超参数）。它同样可以用于自动找到处理异常值、缺失特征、特征选择等的最佳方法。

# 随机搜索 (Randomized Search)

网格搜索方法适用于你探索较少组合的情况（如上一个示例），但当超参数搜索空间很大时，通常更是使用 `RandomizedSearchCV`。它的用法与 `GridSearch` 类相同，但它不是尝试所有可能的组合，而是通过在每次迭代中为每个超参数选择随机值，来评估给定数量的随机组合。这有两个主要优点：

- 如果你让随机搜索运行例如 1,000 次迭代，这种方法将为每个超参数探索 1,000 个不同的值（而不是像网格搜索方法那样每个超参数只尝试几个值）。
- 你只需通过设置迭代次数，就可以控制分配给超参数搜索的计算预算。

# 集成方法 (Ensemble Methods)

另一种微调系统的方法是组合表现最好的模型。群体（或称“集成”）的性能通常会比它们所依赖的单个决策树更好，特别是当单个模型产生非常不同类型的错误时。我们将在第 7 章详细介绍这个主题。

# 分析最佳模型及其误差

通过检查最佳模型，你将对问题获得良好的见解。例如，`RandomForestRegressor` 可以指示每个属性对做出准确预测的相对重要性：

```python
>>> feature_importances = grid_search.best_estimator_.feature_importances_
>>> feature_importances
>>> attrs = ["rooms_per_hhold", "pop_per_hhold", "bedrooms_per_room"]
>>> cat_encoder = full_pipeline.named_transformers_["cat"]
>>> cat_home_attribs = list(cat_encoder.categories_])
>>> attributes = new_attribs + feature_attributes + cat_home_attribs
>>> sorted(zip(feature_importances, attributes), reverse=True)
[(3.3641508163432, 6.29908075e-02, 4.11437985e-02, 1.42768524e-02, 1.406484235e-02, 1.48742809e-02, 1.42575993e-02, ...)]
```
