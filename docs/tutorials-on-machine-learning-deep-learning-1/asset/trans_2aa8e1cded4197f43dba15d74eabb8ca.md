
NLP 中的 TSV 或 CSV：现在的问题是，我们需要一个列与列由逗号（Comma）或制表符（Tab）分隔的数据集。我们在之前的模型中使用了 csv，但在 NLP 中我们将使用 TSV。原因为：

- 因为它不会与逗号、引号产生问题，因此我们不需要任何转义字符。

| Review (评论) | Liked (喜欢) | |
| :--- | :--- | :--- |
| Wow... | Loved this place. | 1 |
| Crust is not good. | 0 | |
| Not tasty and the texture was just nasty. | 0 | |

例如：我们的数据集是像上面的 tsv 格式。0 或 1 表示负面或正面。像 CSV 这样的评论会引起问题：

Wow, this place is amazing!!!, 1

- 它是一句话，但由于存在两个逗号（,,），导致 Wow and this place is amazing 它们被分到了不同的字段中。然后 1 到了了下一个字段。这里行不通。

- 此外，我们也可以使用双引号，评论也可能包含双引号，例如："Good lord !!" The place is Horrible,, 1

在编写评论时，使用制表符（tabs）更好，它们会带来奖励。这非常罕见。

- 因为当你在写评论时按下 Tab 键，你将无法继续输入。所以我们永远不会在评论中找到制表符，也不会遇到在某个特定评论中出现这些异常的问题。

为了避免问题，我们使用 csv。这使得导入数据变得更容易。因此，在 NLP 中，建议使用制表符分隔（TSV）来准备你的文本数据集。

## 7.4 Python 中的 NLP

自然语言处理（NLP）是机器学习的一个分支，我们主要在其中对文本进行预测性分析。NLP 是分析文本。这些文本可以是书籍评论、HTML 网页，或者是你从网络爬虫中提取的各种文本。

- 问题描述：在这里我们将编写一些餐厅评论。因此，我们将建立机器学习模型来预测评论是正面的还是负面的（根据我们 tsv 文件中的 t 或 0 来判断）。

- 该算法将使这部分成为一个通用模型，它将非常适用于其他类型的文本，例如：
    - 预测书籍的类型是惊悚片、喜剧还是浪漫小说
    - 使用 HTML 页面对这些页面进行你想做的任何类型的分析
    - 你也可以将其应用于报纸，以预测它属于哪一篇文章

我们需要添加一些特征，因为我们导入的是 tsv 文件，而 Pandas 的这个 `read_csv` 函数期望的是 csv。

```python
dataset = pd.read_csv("Restaurant_Reviews.tsv", delimiter = "\t", quoting = 3)
```

delimiter: 这个 `delimiter = "\t"` 如果分隔符不是逗号而是制表符 `"\t"`。Pandas 就会知道我们的两列是用制表符分隔的。
quoting:但在查看数据集时，我们不会在此停止，因为我们可能会遇到与其他双引号相关的问题。这就是为什么我们使用 `quoting = 3` 来确保我们不会在这些双引号上出现问题。

我们需要确保有 1000 条评论。
同时确保在 `like` 列中没有评论，或者在 `review` 列中没有 1 或 0。

## NLP：自然语言处理

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```

```python
# 数据预处理
# 导入数据集
# 因为我们使用的是 "tsv" 而不是 "csv"，我们需要指定一些参数。
# 因为 "pandas" 期望某些 "csv" 文件
dataset = pd.read_csv('Restaurant_Reviews.csv', delimiter = '\t', quoting = 3)
```

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_209_0.png)

### 7.4.1 清洁数据

清理数据：在这里我们将编写一些餐厅评论。后续是 NLP 的处理步骤。

- 此时：我们需要使用制表符，以便后续的步骤。

正则表达式：Python 有一个内置的 `re` 包可以用于正则表达式。正则表达式（或 Regular Expression）是字符的序列，可用于检查字符串是否包含特定的模式，我们将其用于清理文本。

```python
# 清理文本
import re
print("{dataset['0']}")
rev_w = re.sub("[^a-zA-Z]", " ", dataset[0])
rev_w = rev_w.lower() # 转换为小写
```

- i. 在 `re.sub()` 中，第一个参数意味着排除所有 a-z 和 A-Z。
- ii. 第二个参数意味着我们使用空格作为分隔符。
- iii. `dataset["Review'][0]` 是应用 `re.sub()` 的句子。

| rev_w | str | 1 | now |
| :--- | :--- | :--- | :--- |
| loved this place | | | |

- iv. 现在将所有单词转换为小写。

| rev_w | str | 1 | now |
| :--- | :--- | :--- | :--- |
| loved this place | | | |

移除无词：我们将移除像 that、in 这样的词。例如在 "Loved this place" 中。Loved 是指示这是一个正面的重要词，但 "this" 这个词并不重要，因为它也出现在负面评论中，例如：this sucks!!

nltk 是一个非常著名的包，nltk (自然语言工具包) 是一个用于自然语言处理的开源库。有一本免费的书。如果你将其用于学术研究，请引用该书：Steven Bird, Edward Klein 和 Edward Loper (2009). *Natural Language Processing with O'Reilly Media*. http://nltk.org/

```python
import nltk
ntlk.download("stopwords")
```

我们的目标是减少稀疏矩阵中的稀疏性。

为了实现这一点，我们使用列表推导式和集合来构建更快的算法。`set` 运行得比 `list` 快：
`reView = [word for word in rev_W if word not in (stopwords.words("english"))]`

