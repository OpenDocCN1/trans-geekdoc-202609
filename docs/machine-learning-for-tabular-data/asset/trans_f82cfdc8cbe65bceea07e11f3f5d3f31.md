

# 第 6 章 高级特征处理方法

# 列表 6 使用 Optuna 的贝叶斯搜索

```python
import optuna
from XGBoost import XGBClassifier
from sklearn.model_selection import cross_validate
```

def objective(trial):

```python
params = {
    'n_estimators': trial.suggest_int('n_estimators', 100, 2000),
    'learning_rate': trial.suggest_float(
        'learning_rate', 0.01, 1.0, log=True
    ),
    'subsample': trial.suggest_float('subsample', 0.1, 1.0),
    'colsample_bytree': trial.suggest_float(
        'colsample_bytree', 0.1, 1.0
    ),
    'max_depth': trial.suggest_int('max_depth', 1, 7),
    'min_child_weight': trial.suggest_int('min_child_weight', 1, 8),
    'reg_lambda': trial.suggest_float(
        'reg_lambda', 1e-9, 10.0, log=True
    ),
    'reg_alpha': trial.suggest_float(
        'reg_alpha', 1e-9, 100.0, log=True
    )
}
```

```python
xgb = XGBClassifier(
    objective='reg:logistic',
    random_state=42, **params
)
```

```python
model_pipeline = Pipeline(
    [('processing', column_transform), ('xgb', xgb)]
)
accuracy = make_scorer(accuracy_score)
cv = KFold(n=5, shuffle=True, random_state=0)
```

```python
cv_scores = cross_validate(model_pipeline, X=data, y=y_target, scoring=accuracy, cv=cv)
cv_accuracy = np.mean(cv_scores['test_score'])
```

```python
study = optuna.create_study(direction="maximize")
study.optimize(objective, n_trials=50)
print(study.best_value)
print(study.best_params)
```

- 一个定义了 Optuna 超参数搜索空间的字典
- 创建一个带有 Optuna 建议的超参数的 XGBClassifier
- 执行交叉验证以使用超参数评估模型性能
- 一个作为优化目标值的函数，通过返回交叉验证的平均准确率得分
- 创建一个以最大化目标函数为目标的 Optuna 研究（study）
- 使用定义的目标函数和最多 60 次尝试启动优化过程
- 打印 Optuna 找到的最优超参数
- 打印目标函数的最优值

![](img/def89cc476fa39f4c54bd34e78d91674_248_0.png)

![](img/def89cc476fa39f4c54bd34e78d91674_248_1.png)

![](img/def89cc476fa39f4c54bd34e78d91674_248_2.png)

![](img/def89cc476fa39f4c54bd34e78d91674_248_3.png)

![](img/def89cc476fa39f4c54bd34e78d91674_248_4.png)

![](img/def89cc476fa39f4c54bd34e78d91674_248_5.png)

# 优化超参数

在 Google Colab 实例上，该过程可能花费两个小时，但结果是是通过超参数优化可以获得的最结果：

```python
'n_estimators': 1434,
'learning_rate': 0.03126858873978429,
'subsample': 0.782534239551612,
'colsample_bytree': 0.9427647573058971,
'max_depth': 7,
'min_child_weight': 2,
'reg_lambda': 2.3123637571345327e-06,
'reg_alpha': 1.8176941947139153e-05
0.848197332365161
```

作为 Optuna 提供的额外功能，通过对前面的代码进行一些简单的添加，你就可以将研究存储在项目数据库中并随时重启优化。如果你在创建研究时声明了研究名称和目标数据库，Optuna 可以将其优化过程与 SQLite 集成：

```python
sqlite_db = "sqlite:///sqlite.db"
study_name = "optimize_GBoost"
study = optuna.create_study(storage=sqlite_db, study_name=study_name,
direction="maximize", load_if_exists=True)
study.optimize(objective, n_trials=60)
print(study.best_params)
print(study.best_value)
```

| 描述 |
| :--- |
| 一个定义了 Optuna 超参数搜索空间的字典 |
| 创建一个带有 Optuna 建议的超参数的 XGBClassifier |
| 执行交叉验证以使用超参数评估模型性能 |
| 一个作为优化目标值的函数，通过返回交叉验证的平均准确率得分 |
| 创建一个以最大化目标函数为目标的 Optuna 研究（study） |
| 使用定义的目标函数和最多 60 次尝试启动优化过程 |
| 打印 Optuna 找到的最优超参数 |
| 打印目标函数的最优值 |

| 代码 | 描述 |
| :--- | :--- |
| `sqlite_db = "sqlite:///sqlite.db"` | 定义 SQLite 的路径 |
| `study_name = "optimize_GBoost"` | 设置研究名称 |
| `study = optuna.create_study(...)` | 创建一个带有存储、名称和方向的 Optuna 研究 |
| `study.optimize(objective, n_trials=60)` | 启动优化过程 |
| `print(study.best_params)` | 打印最优超参数 |
| `print(study.best_value)` | 打印最优值 |

![](img/def89cc476fa39f4c54bd34e78d91674_248_0.png)

![](img/def89cc476fa39f4c54bd34e78d91674_248_1.png)

![](img/def89cc476fa39f4c54bd34e78d91674_248_2.png)

![](img/def89cc476fa39f4c54bd34e78d91674_248_3.png)

![](img/def89cc476fa39f4c54bd34e78d91674_248_4.png)

![](img/def89cc476fa39f4c54bd34e78d91674_248_5.png)

