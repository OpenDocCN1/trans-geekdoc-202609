
### 限制树深度
限制树的最大深度可以防止其变得过于复杂并记忆训练数据。这鼓励模型专注于捕捉一般模式而不是过拟合到特定细节。

### 修剪树
后剪枝涉及移除预测能力提升不大的分支。通过评估分支对验证数据的影响，无帮助或冗余的分支会被剪掉以提高模型在新数据上的性能。

### 最小样本数
设置节点分裂所需的最少样本数可确保分裂是有意义的，而不是基于小且可能有噪声的数据子集。这降低了过拟合的可能性。

### 高级变体
决策树模型已发展为强大的集成技术，可解决其局限性，包括过拟合：

#### 随机森林
该集成方法构建多个决策树并聚合其预测结果（分类时采用多数投票，回归时采用平均）。通过在随机数据子集和特征上训练每棵树，`RandomForest` 降低了过拟合并提高了模型的准确性和鲁棒性。例如，由于其能够有效处理大型数据集和高维空间，它被广泛应用于欺诈检测和客户细分等应用。

#### 梯度提升
该方法依次构建树来纠正前一棵树所犯的错误，从而创建强大的预测模型。像 `XGBoost`、`LightGBM` 和 `CatBoost` 这样的模型基于梯度提升，并流行于结构化数据问题。例如，在 Kaggle 等预测建模竞赛中，由于其卓越的性能和灵活性，梯度提升方法通常更受青睐。

通过理解和应用这些方法，决策树模型可以有效地针对准确性和泛化能力进行优化，避免过拟合的陷阱，同时利用高级变体增强预测能力。

总之，决策树是机器学习任务中强大且灵活的工具。它们的可解释性和多功能性使其在各行业中得到广泛使用。然而，仔细的调优和验证对于避免过拟合并确保稳健性能至关重要。

# 18.3 评估分类模型（准确率、精确率、召回率、F1 分数）
评估分类模型的性能对于理解其有效性至关重要。常用的指标包括准确率、精确率、召回率和 F1 分数。这些指标各提供不同的见解，使你能够根据问题选择最相关的指标。

## 18.3.1 准确率
准确率是正确预测的实例数与总实例数的比率。

公式：

Accuracy = ![](image_rsrcF36.jpg)

其中：
• `TP`：真正例
• `TN`：真负例
• `FP`：假正例
• `FN`：假负例

特征：简单直观。当数据集平衡（各类别比例相等）时有效。

局限性：准确率对于不平衡数据集可能具有误导性。例如，如果 95% 的数据属于一个类别，始终预测该类别的模型将具有 95% 的准确率，但无法捕捉少数类别。

## 18.3.2 精确率
精确率衡量正确预测为正类的观测值占所有预测为正类的比例。

公式：

Precision = ![](image_rsrcF37.jpg)

特征：
• 专注于最小化假正例。
• 当假正例的成本很高时很有用（例如，在不存在疾病时诊断疾病）。

示例：
在垃圾邮件检测中，精确率表示被标记为垃圾邮件的邮件中实际为垃圾邮件的比例。

## 18.3.3 召回率（灵敏度或真正例率）
召回率衡量正确预测为正类的观测值占所有实际正类的比例。

公式：

Recall = ![](image_rsrcF38.jpg)

特征：
• 专注于最小化假负例。
• 当漏掉正类代价很高时很有用（例如，未检测到欺诈）。

示例：
在欺诈检测中，召回率表示成功识别的欺诈交易数量。

## 18.3.4 F1 分数
F1 分数是精确率和召回率的调和平均数，在两者之间提供平衡。

公式：

F1 Score = 2 × ![](image_rsrcF39.jpg)

特征：
• 用于评估精确率和召回率之间平衡的单一指标。
• 适用于不平衡数据集。

示例：
F1 分数为 0.8 表示模型在精确率和召回率之间取得了良好的平衡。

### 对比表
| 指标 || 聚焦 || 最佳使用场景 |
| --- | --- | --- |
| 准确率 || 总体正确性 || 平衡数据集 |
| 精确率 || 避免假正例 || 假正例成本高（例如，垃圾邮件过滤器） |
| 召回率 || 避免假负例 || 假负例成本高（例如，医学测试） |
| F1 分数 || 精确率/召回率平衡 || 不平衡数据集 |

### 使用 Python 的示例
下面是一个使用 scikit-learn 计算这些指标的示例：

```python
from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score

# True and predicted labels
y_true = [1, 0, 1, 1, 0, 1, 0, 0, 1, 0]
y_pred = [1, 0, 1, 0, 0, 1, 1, 0, 1, 0]

# Calculate metrics
accuracy = accuracy_score(y_true, y_pred)
precision = precision_score(y_true, y_pred)
recall = recall_score(y_true, y_pred)
f1 = f1_score(y_true, y_pred)

print(f"Accuracy: {accuracy}")
print(f"Precision: {precision}")
print(f"Recall: {recall}")
print(f"F1 Score: {f1}")
```

输出：
准确率：0.8
精确率：0.8333
召回率：0.7143
F1 分数：0.7692

总之，每一个评估指标都强调模型有效性的不同方面。

选择指标时，请考虑问题的需求。例如，在垃圾邮件检测中，精确率非常重要以最小化假正例，而召回率在医学诊断中至关重要以尽可能捕获所有阳性病例。F1 分数平衡了精确率和召回率，适用于不平衡数据集。综合查看这些指标可以更好地了解模型的优势和劣势。

# 18.4 实战：构建和评估分类模型
创建和评估分类模型是任何机器学习项目的一部分。本实战指南将演示使用 scikit-learn 创建分类模型并使用准确率、精确率、召回率和 F1 分数等指标评估其性能的过程。

### 导入必要的库
首先导入所需的 Python 库：

```python
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score, confusion_matrix, classification_report
```

### 准备数据集
使用示例数据集或加载真实世界数据集。对于本示例，我们将为二元分类创建合成数据集：

```python
# Sample dataset
data = {
    'age': [25, 30, 35, 40, 45],
    'income': [40000, 50000, 60000, 70000, 80000],
    'purchase': [0, 0, 1, 1, 1]  # Target variable
}
df = pd.DataFrame(data)

# Define features (X) and target (y)
X = df[['age', 'income']]
y = df['purchase']
```

### 分割数据
将数据集分为训练集和测试集，以在未见数据上评估模型的性能：

```python
# Split the data into training (80%) and testing (20%) sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
```

### 构建分类模型
在训练数据上训练 `RandomForestClassifier`：

```python
# Initialize and train the model
model = RandomForestClassifier(random_state=42)
model.fit(X_train, y_train)
```

### 进行预测
