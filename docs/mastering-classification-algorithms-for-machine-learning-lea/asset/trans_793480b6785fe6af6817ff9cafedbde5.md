

## 朴叶贝斯算法 49

| | NaN | NaN |
|---|---|---|
| 5568 | NaN | NaN |
| 5569 | NaN | NaN |
| 5570 | NaN | NaN |
| 5571 | NaN | NaN |

[5572 行 x 5 列]

如果数据框上传正确，你会发现该数据框有 5 列和 5572 行。列名应该为 v1, v2, Unnamed: 2, Unnamed: 3 和 Unnamed: 4。列 v2 包含短信文本，而列 v1 包含标签，对应 v2 列中的短信文本是垃圾短信（Spam）还是正常短信（Good）。我们只需要 v1 和 v2 列。因此，我们首先保留 v1 和 v2 列。

```python
df = df[['v1', 'v2']]
df.head()
```

| v1 | v2 |
|---|---|
| 0 ham | Go jurong point, crazy.. Available only |
| 1 ham | Ok lar... Joking wif u oni... |
| 2 spam | Free entry in 2 a wkly to win FA Cup fina... |
| 3 ham | U say so early hour... U already then say... |
| 4 ham | Nah I don't think he goes to us, lives aro... |

列 v2 是我们的自变量，列 v1 是因变量。让我们查看列 v1 列中的唯一值：

```python
# Checking the unique values in the column v1 in the data frame
df.v1.unique()
array(['ham', 'spam'], dtype=object)
```

注意列 v1 有 ham 和 spam 值。在这里，ham 表示对应的短信是正常的，而 spam 表示对应的短信是垃圾短信。

让我们检查数据集中这两种类型的数据有多少个。

```python
df.v1.value_counts()
ham       4825
spam      747
Name: v1, dtype: int64
```

我们看到数据集需要进行平衡，因为正常短信的数量几乎是垃圾短信数量的七倍。

列 v1（我们的因变量）包含文本 'ham' 或 'spam'。然而，我们知道计算机无法理解 v1 列中提供的任何文本。因此，我们需要将 v1 列的内容转换为数字。我们将使用 Label Encoder（标签编码器）将 v1 列中的值编码为数字。Label Encoder 会提取列中的唯一值并分配从 0 开始到 (n-1) 的值，其中 n 是该列中唯一值的数量。要了解更多关于编码器的信息，请参考附录 7。

```python
from sklearn.preprocessing import LabelEncoder

le = LabelEncoder()
df['label'] = le.fit_transform(df['v1'])
print(df.head())
print("Unique values of the column 'label'", df.label.unique())
```

| v1 | v2 |
|---|---|
| 0 ham | Go jurong point, crazy.. Available only |
| 1 ham | Ok lar... Joking wif u oni... |
| 2 spam | Free entry in 2 a wkly to win FA Cup fina... |
| 3 ham | U say so early hour... U already then say... |
| 4 ham | Nah I don't think he goes to us, lives aro... |

列 "label" 的唯一值 [0 1]

我们将 v2 列的内容赋给变量。X 将是我们的自变量。我们将 label 列的内容赋给变量。Y 将是我们的因变量。

```python
X = df['v2']
y = df['label']
```

## 创建训练集和测试集

我们将随机划分数据以获得两个集合。我们将使用其中一个集合来训练模型，另一个来验证模型的效果。我们将划分数据，使得 90% 的数据用于训练，其余 10% 用于验证。我们将使用 Scikit-Learn 库中的 `train_test_split()` 函数将数据分为训练集和测试集：

```python
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.1, random_state=42)
print("Number of data points in the training set = %d" % (X_train.shape[0]))
print("Number of data points in the test set = %d" % (X_test.shape[0]))
```

训练集的数据点数量为 5014
测试集的数据点数量为 558

`train_test_split()` 返回数据集。我们将这些数据集捕获在变量 `X_train`, `X_test`, `y_train` 和 `y_test` 中。`X_train` 包含了原始数据集 90% 的自变量，`y_train` 是其对应的因变量。`X_test` 包含了剩余 10% 的自变量，`y_test` 是其对应的因变量。

我们将使用 `X_train` 和 `y_train` 训练模型。我们将使用 `X_test` 进行预测来测试模型的效果。

## 数据预处理

如前，我们必须找到一种将文本表示数字的方法。一种方法是对每个数据点准备词频-逆文档频率（TF-IDF）。我们将此类数据称为 TF-IDF 向量。要了解更多关于 TF-IDF 的信息，请参考附录 6。

然而，在创建 TF-IDF 向量之前，我们可以从数据中移除非必要的单词/元素。这些非必要的元素包括：

- 常用词，如 a, an, the 等。这些被称为停用词（Stop words）。
- 标点和特殊字符
- URL
- 数字
- 多余空格

在上述类别中，URL 是特殊类别。通常，垃圾短信包含一些 URL。由于我们无法让计算机从 URL 推断，我们将在 dataframe 中创建一个列，如果 X 中存在 URL 则值为 1，否则为 0。让我们先执行此操作。

## 检测文本中是否存在 URL

让我们写一个函数来检测提供的中是否存在一个或多个 URL。如果存在一个或多个 URL，函数返回 1 并从文本中移除 URL。如果文本不包含短信，函数应返回 0。

```python
import re

def identifyAndRemoveURLs(text):
    present = re.search(r'https?://[\w.-]+\.[\w.-][^\s]*', text)
    if present:
        return re.sub(r'https?://[\w.-]+\.[\w.-][^\s]*', '', text, 1), 1
    else:
        return text, 0
```

让我们测试这个函数。`identifyAndRemoveURLs("Click this link to register -")`

print('Example 1:', identifyAndRemoveURLs('https://www.fake.com OR this link for information - http://info.org or download this file:/test.txt'))
print('Example 2:', identifyAndRemoveURLs('This contains no URLs'))

Example 1: ('Click this link to register - OR this link for information - or download this file - ', 1)
Example 2: ('This contains no URLs', 0)

## 朴叶贝斯算法 53

我们将此函数应用于训练数据集并移除文本中所有的 URL。此外，让我们创建一个新的 Series URLPresent，它分别包含 1 或 0。一旦我们将 `X_train` 转换为 TF-IDF，我们将添加 `URLPresent` 以形成训练数据。

```python
URLPresent = pd.Series([identifyAndRemoveURLs(text)[1] for text in X_train])
X_train = pd.Series([identifyAndRemoveURLs(text)[0] for text in X_train])
```

```python
print('New Text:\n', X_train.head())
print('\n Present Indicator:\n', URLPresent.head())
```

新文本：

0 LookMe!: Thanks for your purchase of a video
1 Aight, I'll hit you when I get some cash
2 Donno whats you plan?
3 Going to take your babe out
4 No need de phone card.

```
dtype: object
```

URL 存在指示：

```
0 0
1 0
2 0
3 0
4 0
```

```
dtype: int64
```

## 从数据中移除非元素的函数

我们现在编写一个函数从数据中移除非必要的元素。然后我们将此函数应用于数据集中的文本。要了解更多关于文本预处理，请参考附录 4。

```python
import nltk
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize
```

```python
# Gather the list of Stop Words
stopWordList = nltk.corpus.stopwords.words('english')
```

```python
# Function to remove Stop Words
def removeStopWords(text):
    # 将字符串拆分为标记（单词列表）
    tokens = word_tokenize(text)
    tokens = [token.strip() for token in tokens]
    # 过滤掉停用词
    filtered_tokens = [token for token in tokens if token not in stopWordList]
    filtered_text = ' '.join(filtered_tokens)
```

```python
    return filtered_text
def removeSpecialCharacters(text):
    pattern = r'[^a-zA-Z0-9\s]'
    return re.sub(pattern, '', text)
def removeNumbers(text):
    return re.sub('[0-9]+', '', text)
def removeExtraWhiteSpaces(text):
    return " ".join(text.split())
def cleanData(text):
    text = removeSpecialCharacters(text)
    text = removeStopWords(text)
    text = removeNumbers(text)
    text = removeExtraWhiteSpaces(text)
```

```python
    text = removeSpecialCharacters(text)
    text = removeStopWords(text)
    text = removeNumbers(text)
    text = removeExtraWhiteSpaces(text)
    return text
```

