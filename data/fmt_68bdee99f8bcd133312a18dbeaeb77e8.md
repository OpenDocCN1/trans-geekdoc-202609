
我们导入 `PorterStemmer`，创建一个对象 `it`。我们在列表推导式中将其应用于列表中的单词。

- 我们在列表推导式中将 `wrd` 更改为 `prt_stem.stem(wrd)`。

```python
from nltk.stem.porter import PorterStemmer
prt_stem = PorterStemmer()
review = [prt_stem.stem(wrd) for wrd in rev_w if wrd not in (stopwords.words('english'))]
```

然后我们将生成的单词列表生成一个字符串

```python
rew = " ".join(review)
```

| 之前 | | | 之后 | | |

|---|---|---|---|---|---|

| rev_w | str | loved this place | rew | str | wow love place |

```python
# 清洗文本
import re
import nltk
# nltk.download('stopwords')
from nltk.corpus import stopwords
from nltk.stem.porter import PorterStemmer
print(dataset['Review'][0])
rev_W = re.sub(r'[^a-zA-Z ]', '', dataset['Review'])
rev_w = [word.lower() for word in rev_W] # 转换为小写
review = [wrd for wrd in rev_w if wrd not in stopwords.words()] # 转换为“列表”
# 移除停用词。词干：找到同一个单词不同版本的根
prt_stem = PorterStemmer()
review = [prt_stem.stem(wrd) for wrd in rev_w if wrd not in (stopwords.words('english'))]
rew = " ".join(review)
```

循环遍历 1000 条评论：我们将创建一个新列表，然后在 `for` 循环内部我们将在迭代中将其添加进去。

| 索引 | 评论 | 喜欢 | 索引类型 | 值 | |

|---|---|---|---|---|---|

| 0 | ...We loved this place . | | 0 | str | wow love place |

| 1 | Crust not good. | | 1 | str | crust good |

| 2 | Not tasty and the texture was just | | 2 | str | tasty |

| 3 | Stopped by the late Steve recommended and loved it. The relation on menu was great and so were the prices. | | 3 | str | stop late |

| 4 | I got angry and I want my now. | | 4 | str | get want |

| 5 | | | 5 | str | get angry |

| 6 | Honesty it't taste fresh. | | 6 | str | honesty fast |

| 7 | The potatoes were like you could. | | 7 | str | potato like |

| 8 | The fries were great. | | 8 | str | fri great |

| 9 | A great. | | 9 | str | great touch |

```python
# 清洗文本
import re
import nltk
nltk.download("stopwords")
from nltk.corpus import stopwords
from nltk.stem.porter import PorterStemmer
print(f"{dataset['Review']}")
corpus_review = []

for i in range(1000):
    rew = re.sub(r'[^a-zA-Z ]', '', dataset["Review"])
    rew = [word.lower() for word in rew.split()] # 转换为小写
    review = [word for word in rew if word not in stopwords.words()]
 # 移除停用词。词干：找到同一个单词不同版本的根
    prt_stem = PorterStemmer()
    review = [prt_stem.stem(word) for word in review if word not in stopwords.words('english')]
    rew = " ".join(review)
    corpus_review.append(rew)
```

停用词（Stopwords）：停用词是常用的（例如 `"the"`, `"a"`, `"in"`），搜索引擎在对条目建立索引和作为查询结果检索它们时会被程序忽略这些词。

```python
import nltk
from nltk.corpus import stopwords
print(stopwords.words('english'))
```

词干（Stemming）：例如：只保留单词 `"it"` 的根。`"I love"` 因为我们在评论中可能有 `"loved"`, `"loved"` 或 `"loving"` 或 `"will love"`，这给了我们关于关于该词是正面还是负面的提示，所以我们不需要单词的过去式、将来式或现在式的变体。

由于我们保留了单词的所有不同版本，最终在我们的稀疏矩阵中，我们将有几十个单词，从而导致稀疏性，我们的算法运行起来会遇到困难，因为我们最终会有很多列，你知道稀疏矩阵会有它自己的列。这就是为什么我们在这里进行一些稀疏化处理。

我们导入 `PorterStemmer`，创建一个对象 `it`。我们在列表推导式中将其应用于列表中的单词。

- 我们在列表推导式中将 `wrd` 更改为 `prt_stem.stem(wrd)`。

```python
from nltk.stem.porter import PorterStemmer
prt_stem = PorterStemmer()
review = [prt_stem.stem(wrd) for wrd in rev_w if wrd not in (stopwords.words('english'))]
```

## 构建模型

我们现在使用任何分类算法来构建模型。

现在我们拥有的与第 3 章中的完全相同：分类。我们有一个独立变量矩阵 `$X$`，其中包含 1500 条独立的评论（已经计算过数量）。每一行对应一条特定的评论，且 `$Y$` 不在评论中，`$w$` 也不在评论中。

所以基本上我们使用一个分类模型，我们将训练一个机器学习模型来尝试理解单词出现与结果结果之间的相关性（如果是负面评论则为 `$y$`，如果是正面评论则为 `1`）。

我们将使用降维（Dimensionality Reduction）来减少这个稀疏矩阵的稀疏性，但我们将在第 9 章进行。

### 选择分类模型

我们需要复制一些在第 3 章中构建的机器学习分类模型。我们有：

- i. 逻辑回归 `Logistic Regression`，
- ii. `KNN` `k近邻算法`
- iii. `SVM` `支持向量机`，
- iv. 核向量机 `Kernel SVM`，
- v. 朴素贝叶斯 `Naive Bayes`，
- vi. 决策树分类 `Decision tree classification` 以及
- vii. 随机森林分类 `Random forest classification`。

那么哪种最适合自然语言处理呢？这里有两个选项：

- [1] 既然我们已经有了特征矩阵和因变量向量，而且由于我们的机器学习分类模型都已准备就绪，我们可以应用所有模型并比较混淆矩阵（Confusion Matrix）。通过观察假阳性和假阴性的准确率，并查看它们的性能标准，来决定哪个是最佳模型。
- [2] 其次，数据科学家通常在自然语言处理中使用朴素贝叶斯、决策树分类和随机森林分类。

对于这一节，我们选择了朴素贝叶斯。

## NLP：自然语言处理 `Natural Language Processing`

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```

```python
#
# 数据预处理
# 导入数据集
# 因为我们使用的是 "tsv" 而不是 "csv"，我们需要指定一些参数。
# 因为 "Pandas" 期望某些 "csv" 文件
dataset = pd.read_csv("Reviews.tsv", delimiter="\t", quoting=3)
```

```python
#
# 文本清洗
import re
import nltk
# nltk.download('stopwords')
from nltk.corpus import stopwords
from nltk.stem import PorterStemmer
print(f"{Review[0]}")
corpus_reviews = {}
```

```python
for i in range(len(dataset)):
    rev_w = dataset[i].sub("[^a-zA-Z]+", "", dataset["Review"][i])
    rev_w = rev_w.lower() # 转换为小写
    rev_w = rev_w.split() # 转换为“列表”
    review = [word for word in rev_w if word not in stopwords.words("english")]
    # 去停用词并词干：寻找同一个单词不同形式的根
    stemmer = PorterStemmer()
    review = [stemmer.stem(word) for word in rev_w if word not in set(stopwords.words("english"))]
    rev_w = " ".join(review)
corpus_reviews.append(rev_w)
```

```python
# 创建词袋 bag of words
from sklearn.feature_extraction.text import CountVectorizer
cntvectorizer = CountVectorizer()
cntvectorizer = CountVectorizer(max_features=1500)
X = cntvectorizer.fit_transform(corpus_reviews).toarray()
y = dataset.iloc[:, 1].values
```

```python
# 朴素贝叶斯
```

```python
# 数据划分
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.20, random_state=0)
```

```python
# 特征缩放
```

```python
from sklearn.preprocessing import StandardScaler
st = StandardScaler()
X_train = st.fit_transform(X_train)
X_test = st.transform(X_test)
```

```python
# 训练集到朴素贝叶斯分类器：不需要参数
from sklearn.naive_bayes import GaussianNB
classifier = GaussianNB()
classifier.fit(X_train, y_train) # 拟合数据集
```

```python
# 预测
y_pred = classifier.predict(X_test)
```

```python
# 使用函数 "confusion_matrix" 生成混淆矩阵
from sklearn.metrics import confusion_matrix
cm = confusion_matrix(y_true, y_pred)
# cm 的参数：[[0,0],[1,1]] 真值，预测值
```

```python
accuracy (cm[0][0] + cm[1][1]) / cm.shape[0]
```

```python
# 如何找到这个矩阵的行（或列）的长度？等价地，如何知道有多少行或列？
```

```python
# shape 是 ndarray 和 arrays 的共同属性。
# A.shape
将返回一个元组 (m, n)，其中 m 是行数，n 是列数。
```

```python
# import nltk
from nltk.corpus import stopwords
print(stopwords.words('english'))
print(set(stopwords.words('english')))
```

```python
# python prctc_nlp.py
```

- 我们取测试集大小为 20%。

我们不需要任何特征缩放，因为我们只处理 0 和 1。

从混淆矩阵来看，在 200 个测试样本中，148 个（真阴性 55，真阳性 93）是正确的，52 个（假阳性 42）是错误的，准确率为 73%。

- 从 97 条负面评论中预测了 55 条正确的

从 103 条正面评论中预测了 91 条正确的

| 0 | 1 |

|---|---|

| 0 | 55 | 42 |

| 1 | 12 | 91 |

```python
posve = [k for k in y_test if k==1]
total_posve = len(posve)
```

## 第 8 章：部分 1

## 深度学习

### ANN：人工神经网络

### 神经网络简介

#### 8.1.1 深度学习的历史

深度学习发明于 60 年代和70 年代，80 年代经常讨论它们。但这种趋势在随后的几十年里变得缓慢并消失了。原因是观点不够清晰，技术尚未准备好。

从 2000 年到 2020 年，存储容量变得足够大，计算机的计算能力提高了。这就是为什么深度学习在近年来变得流行。

为了深度学习正常工作，你需要两点：大量的数据和处理这些数据的能力（强大的计算机）。

| 读写速度 ms/bit | 数据保存时间 年 | 功耗 watts/GB | 数据密度 bits/cm² | 硬盘 | 闪存 | 存储世界数据的权重 |

|---|---|---|---|---|---|---|

| ~3000 | >10 | -0.04 | ~10² | | | |

| | >10 | ~0.01-0.04 | ~10⁴ | <10³ | <10⁰ | |

| | | | ~10⁹ | | | |

| 读写速度 ms/bit | 数据保存时间 年 | 功耗 watts/GB | 数据密度 bits/cm² | 硬盘 | 闪存 | 存储世界数据的权重 |

|---|---|---|---|---|---|---|

| ~3000 | >10 | -0.04 | ~10² | | | |

| | >10 | ~0.01-0.04 | ~10⁴ | <10³ | <10⁰ | |

| | | | ~10⁹ | | | |

- 加速的节奏...
- 存在指数级增长...
- 奇点

### 计算能力的提升

什么是深度学习？这位男士被称为“深度学习之父”。他在深度学习方面做了大量工作。

- **输入层**：用于输入值的神经元。这些是你了解某些情况的值。例如：你正在对某些东西，想要预测某些东西，你总是有一些输入开始，这被称为**输入层**。
- **输出层**：然后你有了输出。这是你想预测的值，例如：对于银行交易，这是一笔欺诈交易等等。这将是**输出层**。
- **隐藏层层**：在**输入层**和**输出层**之间，我们将有一个**隐藏层**。**输入层**的神经元连接到连接输出的**隐藏层**神经元。
- **浅层学习与深度学习**：少数隐藏层被称为浅层学习。当隐藏层增加时，它就是深度学习。

小脑的实际部分

上面的图像显示了有多少神经元，比如数十亿数十亿的神经元相互连接。这就是我们要尝试重建的。

我们如何在计算机中重建这个呢？我们将创建一个名为神经网络的人工结构，其中有节点或神经元。我们将有一些

- **输入层**：用于输入值的神经元。这些是你了解某些情况的值。例如：你正在对某些东西，想要预测某些东西，你总是有一些输入开始，这被称为**输入层**。
- **输出层**：然后你有了输出。这是你想预测的值，例如：对于银行交易，这是一笔欺诈交易等等。这将是**输出层**。
- **隐藏层层**：在**输入层**和**输出层**之间，我们将有一个**隐藏层**。**输入层**的神经元连接到连接输出的**隐藏层**神经元。

这就是**输入值**是如何像人类大脑一样，通过所有这些**隐藏层**进行处理的。然后我们得到了输出。所以这就是深度学习在非常抽象的上的本质。

# 我们在这一节中学习到什么

- i. **神经元**：我们将学习一点神经科学知识，了解人类大脑是如何运作的，以及我们为什么要尝试复制它。我们还将会看到神经网络的主要构建单元——神经元是什么样子的。
