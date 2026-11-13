
## 从本地驱动器导入数据集

```python
from sklearn.feature_selection import mutual_info_classif
from sklearn.model_selection import GridSearchCV
from sklearn.metrics import confusion_matrix, classification_report
from sklearn.metrics import accuracy_score
from sklearn.metrics import balanced_accuracy_score, roc_auc_score, make_scorer
from sklearn.metrics import plot_confusion_matrix
from sklearn.model_selection import StratifiedKFold
from sklearn.model_selection import cross_val_score
```

```python
fire = pd.read_csv('database.csv')
# fire = fire[fire['Steel fiber quantity (kg/m3)'] > 0]
# A = fire.agg(
#     {
#     "Water/binder ratio (%)": ["min", "max", "median", "skew", "std", "mean"],
#     "Aggregate/binder ratio (%)": ["min", "max", "median", "skew", "std", "mean"],
#     "Sand/binder ratio (%)": ["min", "max", "median", "skew", "std", "mean"],
#     "Heating rate (°C/min)": ["min", "max", "median", "skew", "std", "mean"],
#     "Moisture content (%)": ["min", "max", "median", "skew", "std", "mean"],
#     "Maximum exposure temperature (°C)": ["min", "max", "median", "skew", "std", "mean"],
#     "Silica fume/binder ratio (%)": ["min", "max", "median", "skew", "std", "mean"],
#     "Aggregate size (mm)": ["min", "max", "median", "skew", "std", "mean"],
#     "GGBS/binder ratio (%)": ["min", "max", "median", "skew", "std", "mean"],
#     "FA/binder ratio (%)": ["min", "max", "median", "skew", "std", "mean"],
#     "PP fiber quantity (kg/m3)": ["min", "max", "median", "skew", "std", "mean"],
#     "PP fiber diameter (um)": ["min", "max", "median", "skew", "std", "mean"],
#     "PP fiber length (mm)": ["min", "max", "median", "skew", "std", "mean"],
#     "Steel fiber quantity (kg/m3)": ["min", "max", "median", "skew", "std", "mean"],
#     "Steel fiber diameter (mm)": ["min", "max", "median", "skew", "std", "mean"],
#     "Steel fiber length (mm)": ["min", "max", "median", "skew", "std", "mean"],
#     }
# )
fire
```

| Water/binder ratio (%) | Aggregate/binder ratio (%) | Sand/binder ratio (%) | Heating rate (C/min) | Moisture content (%) | Maximum exposure temperature (C) | Silica fume/binder ratio (%) | Aggregate size (mm) | GGBS/binder ratio (%) | FA/binder ratio (%) | PP fiber quantity (kg/m3) | PP fiber diameter (um) | PP fiber length (mm) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0 | 0.273 | 2.000 | 1.049 | 101.0 | 0.049 | 1034 | 0.0 | 7.0 | 0.25 | 0.0 | 0.0 | 0.0 |
| 1 | 0.273 | 2.000 | 1.049 | 101.0 | 0.049 | 1034 | 0.0 | 14.0 | 0.25 | 0.0 | 0.0 | 0.0 |
| 2 | 0.300 | 2.000 | 1.033 | 101.0 | 0.049 | 1034 | 0.0 | 20.0 | 0.25 | 0.0 | 0.0 | 0.0 |
| 3 | 0.218 | 1.374 | 1.199 | 101.0 | 0.047 | 1034 | 0.0 | 7.0 | 0.25 | 0.0 | 0.0 | 0.0 |
| 4 | 0.218 | 1.374 | 1.199 | 101.0 | 0.043 | 1034 | 0.0 | 7.0 | 0.25 | 0.0 | 0.0 | 0.0 |
| -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- |
| 641 | 0.200 | 0.000 | 1.040 | 15.0 | 0.063 | 800 | 0.2 | 0.6 | 0.00 | 0.0 | 1.0 | 36.0 |
| 642 | 0.200 | 0.000 | 1.040 | 15.0 | 0.065 | 800 | 0.2 | 0.6 | 0.00 | 0.0 | 1.5 | 36.0 |
| 643 | 0.200 | 0.000 | 1.040 | 15.0 | 0.066 | 800 | 0.2 | 0.6 | 0.00 | 0.0 | 2.0 | 36.0 |
| 644 | 0.200 | 0.000 | 1.040 | 15.0 | 0.064 | 800 | 0.2 | 0.6 | 0.00 | 0.0 | 2.5 | 36.0 |
| 645 | 0.200 | 0.000 | 1.040 | 15.0 | 0.066 | 800 | 0.2 | 0.6 | 0.00 | 0.0 | 3.0 | 36.0 |

```python
x = fire.drop(['Output'], axis=1)
y = fire['Output']
x_train, x_test, y_train, y_test = train_test_split(x, y, test_size=0.30, random_state=111)
# fire['pp fiber length (mm)'] = fire['pp fiber length (mm)'].astype(float)
# fire['maximum exposure temperature'] = fire['maximum exposure temperature'].astype(float)
# fire['s fiber length (mm)'] = fire['s fiber length (mm)'].astype(float)
# fire['output'] = fire['output'].astype(int)
fire.dtypes
# fire['output'].hist()
```

| 特征 | 数据类型 |
|---|---|
| Water/binder ratio (%) | float64 |
| Aggregate/binder ratio (%) | float64 |
| Sand/binder ratio (%) | float64 |
| Heating rate (C/min) | float64 |
| Moisture content (%) | float64 |
| Maximum exposure temperature (C) | int64 |
| Silica fume/binder ratio (%) | float64 |
| Aggregate size (mm) | float64 |
| GGBS/binder ratio (%) | float64 |
| FA/binder ratio (%) | float64 |
| PP fiber quantity (kg/m3) | float64 |
| PP fiber diameter (um) | float64 |
| PP fiber length (mm) | int64 |
| Steel fiber quantity (kg/m3) | float64 |
| Steel fiber diameter (mm) | float64 |
| Steel fiber length (mm) | int64 |
| Output | int64 |

### 绘制输出的直方图

```python
wb = fire['Output']
pyplot.hist(wb, edgecolor='black')
pyplot.title('Water/binder ratio')
pyplot.xlabel('Ratio')
pyplot.ylabel('No. of samples')
pyplot.show()
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_386_0.png)

### 绘制多个特征直方图的另一种方法

```python
for i, col in enumerate(fire.columns):
    pyplot.figure(i)
    sns.histplot(fire[col])
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_387_0.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_387_1.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_387_2.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_388_0.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_388_1.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_388_2.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_389_0.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_389_1.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_389_2.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_390_0.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_390_1.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_390_2.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_391_0.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_391_1.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_391_2.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_392_0.png)

### 执行并拟合算法

```python
# Executing and fitting the algorithm.
xgbc = xgb.XGBClassifier(objective='binary:logistic', missing=1, seed=42, learning_rate=0.05, max_depth=3)
xgbc.fit(x_train, y_train, verbose=True, early_stopping_rounds=50, eval_metric='aucpr', eval_set=[(x_test, y_test)])
predictions = xgbc.predict(x_test)
kfold = StratifiedKFold(n_splits=10, random_state=7, shuffle=True)
results = cross_val_score(xgbc, x, y, cv=kfold)
print("Accuracy: %.2f%% (%.2f%%) " % (results.mean() * 100, results.std() * 100))
```

```python
class_names = ['no spalling', 'spalling']
disp = plot_confusion_matrix(xgbc, x_test, y_test, display_labels=class_names, cmap=pyplot.cm.Blues, xticks_rotation='vertical')
pyplot.grid(b=None)
pyplot.title('Testing set')
print(classification_report(y_test, predictions))
```

| | 精确率 | 召回率 | F1-score | 支持度 |
|---|---|---|---|---|
| 0 | 0.90 | 0.97 | 0.94 | 135 |
| 1 | 0.92 | 0.76 | 0.83 | 59 |
| 准确率 | | | 0.91 | 194 |
| 宏观平均 | 0.91 | 0.87 | 0.88 | 194 |
| 加权平均 | 0.91 | 0.91 | 0.90 | 194 |

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_392_1.png)

```python
class_names = ['no spalling', 'spalling']
disp = plot_confusion_matrix(xgbc, x_train, y_train, display_labels=class_names, colorbar=True, cmap=pyplot.cm.Blues, xticks_rotation='vertical')
pyplot.grid(b=None)
pyplot.title('Training set')
```

Text(0.5, 1.0, 'Training set')

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_393_0.png)

```python
r_auc = roc_auc_score(y_train, predictions)
r_auc
```

```python
yhat = xgbc.predict_proba(x_test)
# retrieve just the probabilities for the positive class
pos_probs = yhat[:, 1]
# plot no skill roc curve
pyplot.plot([0, 1], [0, 1], linestyle='--')
# calculate roc curve for model
fpr, tpr, _ = roc_curve(y_test, pos_probs)
# plot model roc curve
pyplot.plot(fpr, tpr, marker='.', label='AUC=0.866')
# axis labels
pyplot.xlabel('False Positive Rate')
pyplot.ylabel('True Positive Rate')
# show the legend
pyplot.legend()
pyplot.title('Testing set')
# show the plot
pyplot.show()
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_394_0.png)

```python
yhat = xgbc.predict_proba(x_train)

# retrieve just the probabilities for the positive class
pos_probs = yhat[:, 1]
# plot no skill roc curve
pyplot.plot([0, 1], [0, 1], linestyle='--')
# calculate roc curve for model
fpr, tpr, _ = roc_curve(y_train, pos_probs)
# plot model roc curve
pyplot.plot(fpr, tpr, marker='.', label='AUC=0.907')
# axis labels
pyplot.xlabel('False Positive Rate')
pyplot.ylabel('True Positive Rate')
# show the legend
pyplot.legend()
pyplot.title('Training set')
# show the plot
pyplot.show()
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_394_1.png)
