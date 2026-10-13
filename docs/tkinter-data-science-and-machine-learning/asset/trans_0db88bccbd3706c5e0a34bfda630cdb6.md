

# 随机森林实现

```python
'min_samples_split': [2, 5, 10],
'min_samples_leaf': [1, 2, 4]
}

# 初始化 RandomForestClassifier 模型
rf = RandomForestClassifier(random_state=2021)

# 使用 RandomForestClassifier 模型和参数网格创建 GridSearchCV
grid_search = GridSearchCV(rf, param_grid, cv=3, scoring='accuracy', n_jobs=-1)

# 训练并执行网格搜索
grid_search.fit(X_train, y_train)

# 从网格搜索中获取最佳 RandomForestClassifier 模型
best_model = grid_search.best_estimator_

# 保存模型
joblib.dump(best_model, 'RF_Model.pkl')

# 打印找到的最佳超参数
print(f"Best Hyperparameters for RF:")
print(grid_search.best_params_)

return best_model
```

## `implement_RF` 方法

```python
def implement_RF(self, chosen, X_train, X_test, y_train, y_test):
    file_path = os.getcwd() + "/RF_Model.pkl"
    if os.path.exists(file_path):
        model = joblib.load('RF_Model.pkl')
        y_pred = self.run_model(chosen, model, X_train, X_test, y_train, y_test, proba=True)
    else:
        model = self.random_forest(chosen, X_train, X_test, y_train, y_test)
        y_pred = self.run_model(chosen, model, X_train, X_test, y_train, y_test, proba=True)

    # 将结果保存到 excel 文件
    self.obj_data.save_result(y_test, y_pred, "results_RF.csv")
    print("Training Random Forest done...")
    return model, y_pred
```

# K 近邻实现

## `knearest_neigbors` 方法

```python
# KNN 分类器
# 定义网格搜索的参数网格
param_grid = {
    'n_neighbors': list(range(2, 10))
}

# 初始化 KNN 分类器
knn = KNeighborsClassifier()

# 使用 KNN 模型和参数网格创建 GridSearchCV
grid_search = GridSearchCV(knn, param_grid, cv=3, scoring='accuracy', n_jobs=-1)

# 训练并执行网格搜索
grid_search.fit(X_train, y_train)

# 从网格搜索中获取最佳 KNN 模型
best_model = grid_search.best_estimator_

# 保存模型
joblib.dump(best_model, 'KNN_Model.pkl')

# 打印找到的最佳超参数
print(f"Best Hyperparameters for KNN:")
print(grid_search.best_params_)

return best_model
```

## `implement_KNN` 方法

```python
def implement_KNN(self, chosen, X_train, X_test, y_train, y_test):
    file_path = os.getcwd() + "/KNN_Model.pkl"
    if os.path.exists(file_path):
        model = joblib.load('KNN_Model.pkl')
        y_pred = self.run_model(chosen, model, X_train, X_test, y_train, y_test, proba=True)
    else:
        model = self.knearest_neigbors(chosen, X_train, X_test, y_train, y_test)
        y_pred = self.run_model(chosen, model, X_train, X_test, y_train, y_test, proba=True)

    # 将结果保存到 excel 文件
    self.obj_data.save_result(y_test, y_pred, "results_KNN.csv")
    print("Training KNN done...")
    return model, y_pred
```

# 决策树实现

## `decision_trees` 方法

```python
# 初始化 DecisionTreeClassifier 模型
dt_clf = DecisionTreeClassifier(random_state=2021)

# 定义网格搜索的参数网格
param_grid = {
    'max_depth': np.arange(1, 51, 1),
    'criterion': ['gini', 'entropy'],
    'min_samples_split': [2, 5, 10],
    'min_samples_leaf': [1, 2, 4],
}

# 使用 DecisionTreeClassifier 模型和参数网格创建 GridSearchCV
grid_search = GridSearchCV(dt_clf, param_grid, cv=3, scoring='accuracy', n_jobs=-1)

# 训练并执行网格搜索
grid_search.fit(X_train, y_train)

# 从网格搜索中获取最佳 DecisionTreeClassifier 模型
best_model = grid_search.best_estimator_

# 保存模型
joblib.dump(best_model, 'DT_Model.pkl')

# 打印找到的最佳超参数
print(f"Best Hyperparameters for DT:")
print(grid_search.best_params_)

return best_model
```

## `implement_DT` 方法

```python
def implement_DT(self, chosen, X_train, X_test, y_train, y_test):
    file_path = os.getcwd() + "/DT_Model.pkl"
    if os.path.exists(file_path):
        model = joblib.load('DT_Model.pkl')
        y_pred = self.run_model(chosen, model, X_train, X_test, y_train, y_test, proba=True)
    else:
        model = self.decision_trees(chosen, X_train, X_test, y_train, y_test)
        y_pred = self.run_model(chosen, model, X_train, X_test, y_train, y_test, proba=True)

    # 将结果保存到 excel 文件
    self.obj_data.save_result(y_test, y_pred, "results_DT.csv")
    print("Training Decision Trees done...")
    return model, y_pred
```

# 梯度提升实现

## `gradient_boosting` 方法

```python
# 梯度提升分类器
# 初始化 GradientBoostingClassifier 模型
gbt = GradientBoostingClassifier(random_state=2021)

# 定义网格搜索的参数网格
param_grid = {
    'n_estimators': [100, 200, 300],
    'max_depth': [10, 20, 30],
    'subsample': [0.6, 0.8, 1.0],
    'max_features': [0.2, 0.4, 0.6, 0.8, 1.0],
}

# 使用 GradientBoostingClassifier 模型和参数网格创建 GridSearchCV
grid_search = GridSearchCV(gbt, param_grid, cv=3, scoring='accuracy', n_jobs=-1)

# 训练并执行网格搜索
grid_search.fit(X_train, y_train)

# 从网格搜索中获取最佳 GradientBoostingClassifier 模型
best_model = grid_search.best_estimator_

# 保存模型
joblib.dump(best_model, 'GB_Model.pkl')

# 打印找到的最佳超参数
print(f"Best Hyperparameters for GB:")
print(grid_search.best_params_)

return best_model
```

## `implement_GB` 方法

```python
def implement_GB(self, chosen, X_train, X_test, y_train, y_test):
    file_path = os.getcwd() + "/GB_Model.pkl"
    if os.path.exists(file_path):
        model = joblib.load('GB_Model.pkl')
        y_pred = self.run_model(chosen, model, X_train, X_test, y_train, y_test, proba=True)
    else:
        model = self.gradient_boosting(chosen, X_train, X_test, y_train, y_test)
        y_pred = self.run_model(chosen, model, X_train, X_test, y_train, y_test, proba=True)

    # 将结果保存到 excel 文件
    self.obj_data.save_result(y_test, y_pred, "results_GB.csv")
    print("Training Gradient Boosting done...")
    return model, y_pred
```

# Light Gradient Boosting（已注释掉）

```python
# def light_gradient_boosting(self, name, X_train, X_test, y_train, y_test):
#     # LGBM 分类器
#     # 定义网格搜索的参数网格
#     param_grid = {
#         'max_depth': [10, 20, 30],
#         'n_estimators': [100, 200, 300],
#         'subsample': [0.6, 0.8, 1.0],
#         'random_state': [2021]
#     }
#     # 初始化 LightGBM 分类器
#     lgbm = LGBMClassifier()
#     # 使用 LightGBM 分类器和参数网格创建 GridSearchCV
#     grid_search = GridSearchCV(lgbm, param_grid, cv=3, scoring='accuracy', n_jobs=-1)
#     # 训练并执行网格搜索
#     grid_search.fit(X_train, y_train)
#     # 从网格搜索中获取最佳 LightGBM 分类器模型
#     best_model = grid_search.best_estimator_
#     # 保存模型
#     joblib.dump(best_model, 'LGB_Model.pkl')
#     # 打印找到的最佳超参数
#     print(f"Best Hyperparameters for LGB:")
#     print(grid_search.best_params_)
#     return best_model

# def implement_LGB(self, chosen, X_train, X_test, y_train, y_test):
#     file_path = os.getcwd() + "/LGB_Model.pkl"
#     if os.path.exists(file_path):
#         model = joblib.load('LGB_Model.pkl')
#         y_pred = self.run_model(chosen, model, X_train, X_test, y_train, y_test, proba=True)
#     else:
#         model = self.light_gradient_boosting(chosen, X_train, X_test, y_train, y_test)
#         y_pred = self.run_model(chosen, model, X_train, X_test, y_train, y_test, proba=True)
#     # 将结果保存到 excel 文件
#     self.save_result(y_test, y_pred, "results_LGB.csv")
#     print("Training Light Gradient Boosting done...")
#     return model, y_pred
```

# Extreme Gradient Boosting 实现

## `extreme_gradient_boosting` 方法

```python
# 定义网格搜索的参数网格
param_grid = {
    'n_estimators': [100, 200, 300],
    'max_depth': [10, 20, 30],
```

