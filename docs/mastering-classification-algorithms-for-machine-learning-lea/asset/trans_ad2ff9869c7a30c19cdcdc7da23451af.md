
注意，我们已经创建了名为 ConcatenatedString 的列。我们将使用该列中的数据来创建 TF-IDF 向量。

以下代码用于构建 TF-IDF 向量：

```python
from sklearn.feature_extraction.text import TfidfVectorizer
tfidfconverter = TfidfVectorizer(max_features = 90000, ngram_range = (1,1))
arrNonNumericTIDF = tfidfconverter.fit_transform(dfNonNumeric)
ConcatenatedString(df) = pd.DataFrame(arrNonNumericTIDF,
columns = tfidfconverter.get_feature_names())
print(dfNonNumericTIDF.shape)
(4706, 53)
```

注意，我们现在有 53 个特征。

以下代码将包含数值数据的特征与 TF-IDF 向量进行合并：

```python
import pandas as pd
dfFormModel = pd.concat([dfNonNumeric, dfNonNumericTIDF], axis = 1)
import pickle
print(dfFormModel)
pickle.dump(dfFormModel, open(".Columns", 'wb'))
(4706, 2327)
```

注意，我们现在有 4,706 个数据点，每个数据点包含 2,327 个特征。数据集存储在变量 dfFormModel 中。

DataFrame dfFormModel 仅包含数值数据。我们可以使用此数据框来平衡数据。以下代码创建了一个平衡数据集：

```python
import imblearn as ib
```

XTransform = dfForModel.drop([FILE_TYPE_COLUMN_NAME], axis = 1)
yTransform = dfForModel[FILE_TYPE_COLUMN_NAME]

```python
# Transform the dataset
oversample = ib.over_sampling.SMOTE(random_state = 42)
XTrain, yTrain = oversample.fit_resample(XTransform, yTransform)
print(XTrain.shape)
print(yTrain.value_counts())
(12228, 2326)
0 2038
1 2038
2 2038
3 2038
4 2038
5 2038
```

Name: FileType, dtype: int64
注意，现在现在每种文件类型都有 2,038 个数据点。

## 构建随机森林模型

准备好数据后，我们现在可以创建模型了。以下代码创建随机森林模型。

```python
from sklearn.ensemble import RandomForestClassifier
import datetime
import pickle

print('Start Time: %s' % datetime.datetime.now())

# Create the Random Forest Model
modelRF = RandomForestClassifier(n_estimators = 1000,
criterion = "entropy",
oob_score = True

modelRF.fit(XTrain, yTrain)

pickle.dump(modelRF, open("./RFModelELFMalwareDetection", 'wb'))
```

```python
print('End Time: %s' % datetime.datetime.now())
Start Time: 2023-03-08 23:28:26.552642
End Time: 2023-03-08 23:29:26.652041
```

注意，模型在创建后保存到了文件中。当我们需要创建一个应用程序来使用该模型进行预测时，这是一个至关重要的步骤。通常，我们会创建一个 Web 服务，从该文件中加载模型，并调用方法对提供给 Web 服务的输入数据进行预测。该 Web 服务可以由任何发送输入数据的客户端应用程序调用。在这种情况下，输入数据将是一个或多个待测试是否包含恶意软件的 ELF 文件。

现在模型已经构建完成，我们将检查模型在训练集上的指标。

```python
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn import metrics
```

```python
# (此处为预测执行逻辑部分)
y_pred = modelRF.predict(XTrain)
cm = metrics.confusion_matrix(yTrain, y_pred)
```

```python
ax = plt.subplot()
sns.heatmap(cm, annot=True, fmt='g', ax=ax)

# labels, title and ticks
ax.set_xlabel('Predicted labels')
ax.set_ylabel('True labels')
ax.set_title('Confusion Matrix')
ax.xaxis.ticklabels(['Benign', 'Backdoor', 'Botnet', 'DDOS', 'Trojan', 'Virus'])
ax.yaxis.ticklabels(['Benign', 'Backdoor', 'Botnet', 'DDOS', 'Trojan', 'Virus'])
```

```python
print("\nAccuracy of the Model:", metrics.accuracy_score(yTrain, y_pred))
print("\nClassification Report")
print(metrics.classification_report(yTrain, y_pred))
```

模型准确率: 0.9868334968272

| | precision | recall | f1-score | support |
|---|---|---|---|---|
| 0 | 1.00 | 1.00 | 1.00 | 2038 |
| 1 | 0.98 | 1.00 | 0.99 | 2038 |
| 2 | 1.00 | 0.98 | 0.99 | 2038 |
| 3 | 1.00 | 1.00 | 1.00 | 2038 |
| 4 | 0.96 | 0.99 | 0.97 | 2038 |
| 5 | 0.99 | 0.96 | 0.98 | 2038 |
| accuracy | | | 0.99 | 12228 |
| macro avg | 0.99 | 0.99 | 0.99 | 12228 |
| weighted avg | 0.99 | 0.99 | 0.99 | 12228 |

## 混淆矩阵

| | Benign | Backdoor | Botnet | DDoS | Trojan | Virus |
|---|---|---|---|---|---|---|
| **Benign** | 2036 | 0 | 0 | 1 | 0 | 0 |
| **Backdoor** | 0 | 2034 | 0 | 1 | 3 | 0 |
| **Botnet** | 0 | 33 | 2002 | 2 | 1 | 0 |
| **DDoS** | 0 | 0 | 0 | 2035 | 1 | 2 |
| **Trojan** | 0 | 16 | 0 | 3 | 2009 | 10 |
| **Virus** | 0 | 0 | 0 | 0 | 87 | 1951 |

**图 7.4:** 模型在训练集上的测试混淆矩阵。注意模型在训练集上的准确率为 98.68%。

## 测试模型

我们现在有了模型。我们可以在预留的测试集上测试模型。注意，测试集与真实数据一样，因为模型在创建时从未见过测试集中的任何 ELF 文件。与真实数据的唯一区别是测试集是有标签的，我们知道这些文件是否包含恶意软件，如果包含，其性质是什么。

在将测试集中的 ELF 文件交给模型之前，我们必须对这些文件的数据进行预处理。

以下步骤执行所有必要的预处理，然后应用模型进行预测。

### 步骤 1：从 ELF 文件读取所有特征。

我们已经讨论过 `extractInformationFromDirectory()` 函数可以从目录中的所有 ELF 文件提取所有信息。我们将调用该函数提取测试集中所有 ELF 文件的特征。

```python
benchmarkTestFileFeatures, nValidFiles, nInvalidFiles, nFilesWithNoFileHeader, nFilesWithNoProgramHeader, nFilesWithNoSections = \
extractInformationFromDirectory("Data/TestData/Benign*/")
print("BENIGN Files:\nValid - %d\nInvalid - %d\nNo File Header - %d\nNo Program Header - %d\nNo Sections - %d\n ", \
(nValidFiles, nInvalidFiles, nFilesWithNoFileHeader, nFilesWithNoProgramHeader, nFilesWithNoSections))
```

# BENIGN FILES:
Valid - 222
Invalid - 10
No File Header - 0
No Program Header - 0
No Sections - 5

```python
extractInformationFromDirectory("Data/TestData/Backdoor*/")
print("BACKDOOR FILES:\nValid - %d\nInvalid - %d\nNo File Header - %d\nNo Program Header - %d\nNo Sections - %d\n ", \
(nValidFiles, nInvalidFiles, nFilesWithNoFileHeader, nFilesWithNoProgramHeader, nFilesWithNoSections))
```

# BACKDOOR FILES:
Valid - 62
Invalid - 2
No File Header - 0
No Program Header - 0
No Sections - 4

```python
botnetTestFileFeatures, nValidFiles, nInvalidFiles, nFilesWithNoFileHeader, nFilesWithNoProgramHeader, nFilesWithNoSections = \
extractInformationFromDirectory("Data/TestData/Botnet/*")
print("BOTNET FILES:\nValid - %d\nInvalid - %d\nNo File Header - %d\nNo Program Header - %d\nNo Sections - %d", \
(nValidFiles, nInvalidFiles, nFilesWithNoFileHeader, nFilesWithNoProgramHeader, nFilesWithNoSections))
```

# BOTNET FILES:
Valid - 61
Invalid - 6
No File Header - 0
No Program Header - 0
No Sections - 2

```python
ddosTestFileFeatures, nValidFiles, nInvalidFiles, nFilesWithNoFileHeader, nFilesWithNoProgramHeader, nFilesWithNoSections = \
extractInformationFromDirectory("Data/TestData/Ddos/*")
print("DDOS FILES:\nValid - %d\nInvalid - %d\nNo File Header - %d\nNo Program Header - %d\nNo Sections - %d", \
(nValidFiles, nInvalidFiles, nFilesWithNoFileHeader, nFilesWithNoProgramHeader, nFilesWithNoSections))
```

# DDOS FILES:
Valid - 71
Invalid - 3
No File Header - 0
No Program Header - 0
No Sections - 0

## 234 精通机器学习中的分类算法

trojanTestFileFeatures, nValidFiles, nInvalidFiles, nFilesWithNoFileHeader, nFilesWithNoProgramHeader, nFilesWithNoSections = \
extractInformationFromDirectory("Data/TestData/Trojan/*")
print("TROJAN FILES:\nValid - %d\nInvalid - %d\nNo File Header - %d\nNo Program Header - %d\nNo Sections - %d", \
(nValidFiles, nInvalidFiles, nFilesWithNoFileHeader, nFilesWithNoProgramHeader, nFilesWithNoSections))
```

# TROJAN FILES:
Valid - 40
Invalid - 3
No File Header - 0
No Program Header - 0
No Sections - 4

```python
virusTestFileFeatures, nValidFiles, nInvalidFiles, nFilesWithNoFileHeader, nFilesWithNoProgramHeader, nFilesWithNoSections = \
extractInformationFromDirectory("Data/TestData/Virus/*")
print("VIRUS FILES:\nValid - %d\nInvalid - %d\nNo File Header - %d\nNo Program Header - %d\nNo Sections - %d", \
(nValidFiles, nInvalidFiles, nFilesWithNoFileHeader, nFilesWithNoProgramHeader, nFilesWithNoSections))
```

# VIRUS FILES:
Valid - 48
Invalid - 4
No File Header - 0
No Program Header - 0
No Sections - 4
