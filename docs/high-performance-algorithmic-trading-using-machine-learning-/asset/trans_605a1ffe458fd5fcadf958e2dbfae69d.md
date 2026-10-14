

## 2. 填补缺失值

在下一步中，对于每一列，我们使用 `fillna` 函数将缺失值替换为该板块（`groupby`）的中位数（`transform('median')`）。

这是会计师和财务分析师推荐并遵循的方法：

```python
df.fillna(df.groupby('Sector').transform('median'), inplace=True)
```

## 3. 删除列

标记为 `2015 PRICE VAR [%]` 的列在事前是未知的。

必须小心避免引入数据泄露。换句话说，即模型运行时不可用的信息。因此，该列绝不能展示给算法，也不能成为模型输入的一部分。我们将该列从模型输入列表中移除，并将其存储以备将来使用：

```python
y_price_var = df.pop('2015 PRICE VAR [%]')
```

下一步是标签编码。

## 4. 标签编码

标签编码是指将每个字母数字（文本）类别数据值替换为数字代码。换句话说，就是一个数字。原因在于大多数机器学习算法仅接受数字作为输入数据，对于字母数字（文本）数据会产生错误信息。要执行的编码针对 'Sector' 列。

以下是该列中发现的值的列表：

```python
lst_sector = list(np.unique(df['Sector']))
lst_sector
```

```
['Basic Materials',
 'Communication Services',
 'Consumer Cyclical',
 'Consumer Defensive',
 'Energy',
 'Financial Services',
 'Healthcare',
 'Industrials',
 'Real Estate',
 'Technology',
 'Utilities']
```

该列表使用 Scikit-Learn 机器学习 API 中的 `LabelEncoder` 对象进行编码，我们在上一章中已使用过它：

```python
from sklearn.preprocessing import LabelEncoder

lbl = LabelEncoder()

# 学习编码
lbl.fit(lst_sector)

# 应用该编码（转换）
df['Sector'] = lbl.transform(df['Sector'])
```

编码结果可在以下代码中看到：

```python
dict(zip(lst_sector, lbl.transform(lst_sector)))
```

```
{'Basic Materials': 0,
 'Communication Services': 1,
 'Consumer Cyclical': 2,
 'Consumer Defensive': 3,
 'Energy': 4,
 'Financial Services': 5,
 'Healthcare': 6,
 'Industrials': 7,
 'Real Estate': 8,
 'Technology': 9,
 'Utilities': 10}
```

## 5. 准备目标列

倒数第二步是准备目标列（`y`），算法将学习从输入映射到该目标。该目标列是收益率的符号（其所属的类别：正或负）：

```python
y = df.pop('Class')
```

## 6. 划分数据

剩下的就是将数据分为两组：学习集和测试集。正如我们在上一章[13](#chap02.xhtml#footnote-147)中提到的，学习阶段仅使用训练数据（子集 `X_train`）：

```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(df, y, shuffle=False)
```

### 训练阶段

我们选择了随机森林[14](#chap02.xhtml#footnote-146)，这是一种高性能算法，无需特别的校准工作即可产生准确的预测。该算法的原理是自动构建一组决策树。可以将决策树想象为一系列指导选择的是非问题（最优问卷）。每棵树从数据中学习以对项目进行分类，例如基于会计数据决定是否投资该股票。

以下是从训练集构建的决策树示例：

![](images/fig-2-3.png)

可以看到学习算法构建的最优问题和答案序列。这是第一个问答：“`CapitalExpenditureRatio` < -2.318 吗？”。如果为 False，则下一个问题是：`Debt to Asset ratio` < 0.245...

这种自动化专业知识生成了一个经过优化的问卷，能引导得出最准确的答案。

现在，将随机森林设想为这些树的一个群体，一个多样化的决策者群体。它们都以各自独特的方式从数据中学习。当我们需要做决策时，每棵树对答案进行投票。得票最多的结果获胜，确保了平衡且准确的结果。它是一个专家委员会。

机器学习的新颖之处在于，每棵决策树都是在没有任何专家人工干预的情况下被学习、构建和优化的。使用包含每家公司会计和财务信息的训练数据（`X_train`），随机森林算法学会推断其所属的类别（`y_train`）：

```python
from sklearn.ensemble import RandomForestClassifier

# 定义分类器
clf = RandomForestClassifier()

# 在训练数据上拟合分类器
clf.fit(X_train, y_train)
```

学习过程完成后，会计算一个准确率得分[15](#chap02.xhtml#footnote-145)，即正确预测数量与总预测数量的比率。该得分始终在测试集（`X_test`）上计算。换句话说，即模型训练期间未见过的数据：

```python
clf.score(X_test, y_test)
```

```
0.63
```

为了根据两个类别（正和负）更精确地了解预测分布，我们计算以下两个指标：`classification_report` 和 `confusion_matrix`。

Scikit-Learn 中的 `classification_report` 函数用于评估分类模型的性能。

它提供了各类别各项指标的综合摘要，包括：

- **precision**（精确率）：正向预测的准确性
- **recall**（召回率，或灵敏度）：召回率检查模型是否捕捉到了大多数真正例，避免漏报
- **F1-score**（F1 分数）：精确率和召回率之间的平衡
- **Support**（支持度）：每个类别中的样本数量

```python
from sklearn.metrics import classification_report, confusion_matrix
```

导入两个指标计算函数后，我们使用训练好的模型（`clf`，作为分类器）为前述整个测试集计算（`clf.predict`）一组预测值（`pred`）：

```python
pred = clf.predict(X_test)
```

分类报告将把这些预测与收益率的实际值（`y_test`）（正或负类别）进行比较：

```python
print(classification_report(y_test, pred))
```

```
              precision    recall  f1-score   support

           0       0.58      0.84      0.68       449
           1       0.76      0.46      0.56       503

    accuracy                           0.63       952
```

就解释而言，得分应读作“越高越好”。获得的数值令人鼓舞。指标远高于随机预测（0.5：抛硬币）。

负类别（负收益）的检测精确度低于正类别。事实上，其精确率得分较低（0.58，而正类别为 0.76）。另一方面，有少数负收益被错误检测为正收益。事实上，负类别的召回率得分很高。

正收益被非常精确地检测出来。极少出现假阳性。具体而言，这意味着极少出现亏损的多头交易（预期为正但实际为负）。76% 的正收益被正确预测。

我们通过混淆矩阵（`confusion_matrix`）来佐证这一点。该指标采用上述概念并将其组织在一个称为混淆矩阵的表格中：

```python
# tp : true positive , fp : false positive ,tn : true negative ,fn : false negative
tn, fp, fn, tp = confusion_matrix(y_test, pred).ravel()

print(f"FALSE PREDICTIONS : {fp} negative returns wrongly detected as positive return and {fn} positive returns not detected")
```

