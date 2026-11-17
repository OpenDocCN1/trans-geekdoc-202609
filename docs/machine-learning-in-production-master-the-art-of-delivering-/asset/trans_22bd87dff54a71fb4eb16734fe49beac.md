

它将返回工件根目录的路径，工件存储于此。

```
1. import mlflow
2. mlflow.get_artifact_uri()
3. './mlruns/0/be1cd88ebd704e9ab7629fd364747e1e/artifacts'
```

让我们考虑贷款预测的场景，其目标是预测客户是否符合贷款资格。首先，导入所需的库。

```
1. # Importing required packages
2. import pandas as pd
3. import numpy as np
4.
5. from sklearn.linear_model import LogisticRegression
6. from sklearn.ensemble import RandomForestClassifier
7. from sklearn.tree import DecisionTreeClassifier
8.
9. from matplotlib import pyplot as plt
10.
11. from sklearn import preprocessing
12. from sklearn.model_selection import train_test_split, GridSearchCV
13. from sklearn import metrics
14.
15. import mlflow
```

下一步是加载数据集，并将数值列和类别列的名称分别捕获到独立变量中：

```
1. # Reading the data
2. data = pd.read_csv("loan_dataset.csv")
3. num_col = data.select_dtypes(include=['int64','float64']).columns.tolist()
4. cat_col = data.select_dtypes(include=['object']).columns.tolist()
5. cat_col.remove('Loan_Status')
6. cat_col.remove('Loan_ID')
```

处理类别列和数值列中的缺失值：

```
1. # Creating a list of categorical and numerical variables
2. for col in cat_col:
3.     data[col].fillna(data[col].mode()[0], inplace=True)
4.
5. for col in num_col:
6.     data[col].fillna(data[col].median(), inplace=True)
```

对数值数据将极端值限制在第 5 和第 95 百分位数。

```
1. # Clipping extreme values
2. data[num_col] = data[num_col].apply(lambda x: x.clip(*x.quantile([0.05, 0.95])))
```

创建一个名为 **总收入** 的新特征，它是申请人收入和共同申请人收入之和。

```
1. # creating a new feature as Total Income
2. data['LoanAmount'] = np.log(data['LoanAmount']).copy()
3. data['TotalIncome'] = data['ApplicantIncome'] + data['CoapplicantIncome']
4. data['TotalIncome'] = np.log(data['TotalIncome']).copy()
```

删除申请人收入和共同申请人收入列。

```
1. # Dropping ApplicantIncome and CoapplicantIncome
2. data = data.drop(['ApplicantIncome', 'CoapplicantIncome'], axis=1)
```

使用标签编码技术将类别列转换为数值列。

```
1. # Label encoding categorical variables
2. for col in cat_col:
3.     le = preprocessing.LabelEncoder()
4.     data[col] = le.fit_transform(data[col])
5.
6. data['Loan_Status'] = le.fit_transform(data['Loan_Status'])
```

将数据拆分为训练集和测试集（70:30）。

```
1. # Train test split
2. X = data.drop(['Loan_Status', 'Loan_ID'], 1)
3. y = data.Loan_Status
4.
5. SEED = 1
6.
7. X_train, X_test, y_train, y_test = train_test_split(X,y, test_size = 0.3, random_state = SEED)
```

使用网格搜索交叉验证方法构建逻辑回归模型。

```
1. # Logistic Regression #
2.
3. lr = LogisticRegression(random_state=SEED)
4. lr_param_grid = {
5.     'C': [100, 10, 1.0, 0.1, 0.01],
6.     'penalty': ['l1','l2'],
7.     'solver':['liblinear']
8. }
9.
10. lr_gs = GridSearchCV(
11.     estimator=lr,
12.     param_grid=lr_param_grid,
13.     cv=5,
14.     n_jobs=-1,
15.     scoring='accuracy',
16.     verbose=0
17. )
18. lr_model = lr_gs.fit(X_train, y_train)
```

使用网格搜索交叉验证方法构建决策树模型。

```
1. # Decision Tree #
2.
3. dt = DecisionTreeClassifier(
4.     random_state=SEED
5. )
6.
7. dt_param_grid = {
8.     "max_depth": [3, 5, 7, 9, 11, 13],
9.     'criterion' : ["gini", "entropy"],
10. }
11.
12. dt_gs = GridSearchCV(
13.     estimator=dt,
14.     param_grid=dt_param_grid,
15.     cv=5,
16.     n_jobs=-1,
17.     scoring='accuracy',
18.     verbose=0
19. )
20. dt_model = dt_gs.fit(X_train, y_train)
```

使用网格搜索交叉验证方法构建随机森林模型。

```
1. #___________ Random Forest ___________#
2.
3. rf = RandomForestClassifier(random_state=SEED)
4. rf_param_grid = {
5.     'n_estimators': [400, 700],
6.     'max_depth': [15,20,25],
7.     'criterion' : ["gini", "entropy"],
8.     'max_leaf_nodes': [50, 100]
9. }
10.
11. rf_gs = GridSearchCV(
12.     estimator=rf,
13.     param_grid=rf_param_grid,
14.     cv=5,
15.     n_jobs=-1,
16.     scoring='accuracy',
17.     verbose=0
18. )
19. rf_model = rf_gs.fit(X_train, y_train)
```

创建一个用于评估模型指标的函数。

```
1. # Model evaluation metrics
2. def model_metrics(actual, pred):
3.     accuracy = metrics.accuracy_score(y_test, pred)
4.     f1 = metrics.f1_score(actual, pred, pos_label=1)
5.     fpr, tpr, thresholds1 = metrics.roc_curve(y_test, pred)
6.     auc = metrics.auc(fpr, tpr)
7.     plt.figure(figsize=(8,8))
8.     # plot auc
9.     plt.plot(fpr, tpr, color='blue', label='ROC curve area = %0.2f'%auc)
10.    plt.plot([0,1],[0,1], 'r--')
11.    plt.xlim([-0.1, 1.1])
12.    plt.ylim([-0.1, 1.1])
13.    plt.xlabel('False Positive Rate', size=14)
14.    plt.ylabel('True Positive Rate', size=14)
15.    plt.legend(loc='lower right')
16.
17.    # Save plot
18.    plt.savefig("plots/ROC_curve.png")
19.
20.    # Close plot
21.    plt.close()
22.
23.    return(accuracy, f1, auc)
```

创建一个使用 MLflow 捕获模型参数和模型指标等信息的函数。

```
1. # MLflow's logging functions
2. def mlflow_logs(model, X, y, name):
3.
4. with mlflow.start_run(run_name = name) as run:
5.
6. # Run id
7. run_id = run.info.run_id
8. mlflow.set_tag("run_id", run_id)
9.
10. # Make predictions
11. pred = model.predict(X)
12.
13. # Generate performance metrics
14. (accuracy, f1, auc) = model_metrics(y, pred)
15.
16. # Logging best parameters
17. mlflow.log_params(model.best_params_)
18.
19. # Logging model metric
20. mlflow.log_metric("Mean cv score", model.best_score_)
21. mlflow.log_metric("Accuracy", accuracy)
22. mlflow.log_metric("f1-score", f1)
23. mlflow.log_metric("AUC", auc)
24.
25. # Logging artifacts and model
26. mlflow.log_artifact("plots/ROC_curve.png")
27. mlflow.sklearn.log_model(model, name)
28.
29. mlflow.end_run()
```

对测试数据进行预测，并使用前述函数捕获模型指标和参数。

```
1. # Make predictions using ML models
2.
3. mlflow_logs(dt_model, X_test, y_test, "DecisionTreeClassifier")
4. mlflow_logs(lr_model, X_test, y_test, "LogisticRegression")
5. mlflow_logs(rf_model, X_test, y_test, "RandomForestClassifier")
```

激活虚拟环境：

```
conda activate venv
```

下图显示了在成功创建 conda 环境后的激活和停用命令。

![](img/cc4299656808e62a294f1843a1e18e72_116_0.png)

运行 train.py 文件，它将捕获参数和指标并将工件存储在指定位置。

启动 MLflow UI，然后运行 train.py 文件，如下图所示。

![](img/cc4299656808e62a294f1843a1e18e72_116_1.png)

```
python train.py
```

这不会打印任何内容，因此可以在 MLflow UI 上检查输出。

为演示目的，实现了三种不同的分类器，即逻辑回归、决策树和随机森林，以比较其性能。

下图显示已捕获模型指标、参数、模型名称和运行 ID。总体而言，逻辑回归的准确率为 78.9%，略好于其他模型。

![](img/cc4299656808e62a294f1843a1e18e72_117_0.png)

## 图 5.8：train.py 输出的 MLflow UI

在 **贷款预测** 实验下捕获 MLflow 日志，而不是在 **默认** 实验下。

```
1. # Make predictions using ML models
2. mlflow.set_experiment("Loan_prediction")
3. mlflow_logs(dt_model, X_test, y_test, "DecisionTreeClassifier")
4. mlflow_logs(lr_model, X_test, y_test, "LogisticRegression")
5. mlflow_logs(rf_model, X_test, y_test, "RandomForestClassifier")
```

默认情况下，MLflow 会在名为 **默认** 的实验下捕获信息。但是，你可以直接在命令中指定实验名称，如下所示：

```
python train.py --experiment-name Loan_prediction
```

由于 `train.py` 文件中没有打印语句，此命令不会在终端打印任何输出。

