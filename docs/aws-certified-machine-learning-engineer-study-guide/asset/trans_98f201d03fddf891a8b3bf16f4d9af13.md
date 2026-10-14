

```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn import datasets
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression
from sklearn.ensemble import RandomForestClassifier
from xgboost import XGBClassifier
from sklearn.metrics import roc_curve, roc_auc_score
import os

# 加载 Digits 数据集
digits = datasets.load_digits()
X = digits.data
y = (digits.target == 1).astype(int)  # 转换为二分类（类别 1 对其余类别）

# 将数据集划分为训练集和测试集
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)

# 初始化不同的模型和超参数
models = {
    'Logistic Regression': [
        LogisticRegression(C=1, solver='liblinear', random_state=42),
        LogisticRegression(C=0.1, solver='liblinear', random_state=42)
    ],
    'Random Forest': [
        RandomForestClassifier(n_estimators=50, max_depth=5, random_state=42),
        RandomForestClassifier(n_estimators=100, max_depth=7, random_state=42)
    ],
    'XGBoost': [
        XGBClassifier(n_estimators=50, max_depth=5, eval_metric='logloss', random_state=42),
        XGBClassifier(n_estimators=100, max_depth=7, eval_metric='logloss', random_state=42)
    ]
}

# 如果目录不存在则创建
output_dir = './ch05/images'
os.makedirs(output_dir, exist_ok=True)

# 绘制 ROC 曲线
plt.figure(figsize=(10, 7))

for model_name, model_list in models.items():
    for model in model_list:
        model.fit(X_train, y_train)
        y_pred_prob = model.predict_proba(X_test)[:, 1]
        fpr, tpr, _ = roc_curve(y_test, y_pred_prob)
        auc = roc_auc_score(y_test, y_pred_prob)
        label = f'{model_name} (n_estimators={getattr(model, "n_estimators", "N/A")}, C={getattr(model, "C", "N/A")}, max_depth={getattr(model, "max_depth", "N/A")}) (AUC = {auc:.2f})'
        plt.plot(fpr, tpr, label=label)

# 绘制随机猜测基准线
plt.plot([0, 1], [0, 1], linestyle='--', color='gray')

# 添加标签和图例
plt.xlabel('False Positive Rate')
plt.ylabel('True Positive Rate')
plt.title('ROC Curve for Different Models and Hyperparameters (Digits Dataset)')
plt.legend(loc='best')

# 保存图表而非显示
plt.savefig(os.path.join(output_dir, 'roc_curve_digits_dataset.png'))
plt.close()
```

[图 5.5](#c005.xhtml#c05-fig-5) 中的 AUC-ROC 图清晰地对比了逻辑回归、随机森林和 XGBoost 分类器在 Digits 数据集中区分数字“1”与其他数字方面的性能。通过在不同阈值下绘制 TPR（灵敏度）与 FPR（1 − 特异性）的关系，我们可以直观地评估每个模型在最小化假阳性的同时正确识别数字“1”的能力。ROC 曲线越接近左上角，模型在区分正负类别方面的效果越好。

![图 5.5 ROC 曲线对比。](images/c05f005.png)

[图 5.5](#c005.xhtml#rc05-fig-5) ROC 曲线对比。

AUC 值量化了这种性能，AUC 越高表示分类能力越强。通过对比逻辑回归、随机森林和 XGBoost 的 AUC 值，我们可以确定哪个模型在对数字“1”进行分类时表现最佳。AUC 值越高的模型，在将数字“1”与其他数字区分开方面越有效，使其成为该二分类任务的首选。

## 回归问题指标

与旨在将数据点归类为离散类别的分类问题不同，回归问题旨在预测连续值。换句话说，分类模型可能预测一封邮件是否为垃圾邮件（二元决策），而回归模型可能根据房屋特征预测房价（连续值）。输出类型的这一根本差异要求回归模型使用不同的评估指标。

在评估回归模型时，通常会使用几个关键指标来评估性能。其中包括 `MSE`、`RMSE`、`MAE`、`MAPE` 和 `R-squared`。这些指标有助于量化预测值与实际值之间的差异，从而深入了解模型的准确性和可靠性。分类指标（如准确率、精确率、召回率和 `AUC-ROC`）侧重于评估分类预测的正确性，而回归指标则关注连续预测中误差的大小。这些度量确保我们能有效衡量回归模型在预测真实值结果方面的质量和性能。

在以下章节中，我们将解释考试中评估机器学习回归模型性能所需理解的基本指标。

### 均方误差

`MSE` 是评估回归模型性能的常用指标。它衡量实际值与预测值之间平方差的平均值，反映了预测值与实际值的接近程度。`MSE` 的计算方法是：将实际值 $y_i$ 与预测值 $\hat{y}_i$ 之间的平方差求和，然后除以数据点数量 $n$。对差值进行平方运算可确保正负误差对指标的贡献相等，并对较大的误差施以更重的惩罚。`MSE` 的公式如下：

$$
\text{MSE} = \frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2
$$

`MSE` 是评估回归模型准确性的关键指标，`MSE` 越低表示预测性能越好。

### 均方根误差

`RMSE` 是另一个广泛用于评估回归模型性能的指标。它是 `MSE` 的平方根，提供了一个可解释的平均误差大小度量。`RMSE` 特别有用，因为它保留了原始数据的单位，使误差的规模更易于理解。通过对 `MSE` 开平方，`RMSE` 反映了预测误差平均偏离真实值的程度。`RMSE` 的公式如下：

