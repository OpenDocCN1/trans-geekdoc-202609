
由于正文内容较多，我们将其合理划分为多个章节和小节。

# 文本处理与情感分析实战

## 数据平衡与预处理

由于正面评论多于负面评论，我们只需对正面评论进行采样，使类别保持平衡。对某些分类器而言这不是问题，但为稳妥起见，我们仍执行此操作。

接下来，我们将定义一个函数，将每条评论转换为单词或标记的列表。这不仅仅是调用 `string.split()`。例如，如果我们有 "Dog" 和 "dog"，它们是同一个词。`NLTK` 包含自己的分词函数，我们可以直接使用。

```python
def my_tokenizer(s):
    s = s.lower() # downcase
    tokens = nltk.tokenize.word_tokenize(s) # split string into words (tokens)
    tokens = [t for t in tokens if len(t) > 2] # remove short words, they're probably not useful
    tokens = [wordnet_lemmatizer.lemmatize(t) for t in tokens] # put words into base form
    tokens = [t for t in tokens if t not in stopwords] # remove stopwords
    return tokens
```

注意，`NLTK` 的分词函数比 `string.split()` 慢得多，因此在自己的代码中可能需要探索其他选项。更高级的系统会处理拼写错误等情况。

## 构建数据矩阵

接下来，我们需要收集必要的数据，以便将所有文本转换为数据矩阵 `X`。这包括：确定词汇表总大小（单词总数），确定每个单词的索引（从 0 开始，依次递增 1），并保存每条评论的分词形式。

```python
word_index_map = {}
current_index = 0
positive_tokenized = []
negative_tokenized = []

for review in positive_reviews:
    tokens = my_tokenizer(review.text)
    positive_tokenized.append(tokens)
    for token in tokens:
        if token not in word_index_map:
            word_index_map[token] = current_index
            current_index += 1

for review in negative_reviews:
    tokens = my_tokenizer(review.text)
    negative_tokenized.append(tokens)
    for token in tokens:
        if token not in word_index_map:
            word_index_map[token] = current_index
            current_index += 1
```

注意，我们确定单词与索引映射关系的方法是 `word_index_map`，它是一个字典，以单词为键，返回索引作为值。

## 向量化表示

接下来，让我们创建一个函数，将每组标记（代表一条评论）转换为数据向量。

```python
def tokens_to_vector(tokens, label):
    x = np.zeros(len(word_index_map) + 1) # last element is for the label
    for t in tokens:
        i = word_index_map[t]
        x[i] += 1
    x = x / x.sum() # normalize it before setting label
    x[-1] = label
    return x
```

请注意，此函数假设我们此时仍将标签附加到向量上。

## 初始化数据矩阵

最后，我们初始化数据矩阵：

```python
N = len(positive_tokenized) + len(negative_tokenized)
# (N x D+1 matrix - keeping them together for now so we can shuffle more easily later
data = np.zeros((N, len(word_index_map) + 1))

i = 0
for tokens in positive_tokenized:
    xy = tokens_to_vector(tokens, 1)
    data[i,:] = xy
    i += 1

for tokens in negative_tokenized:
    xy = tokens_to_vector(tokens, 0)
    data[i,:] = xy
    i += 1
```

## 打乱数据与划分训练/测试集

接下来，我们打乱数据并创建训练/测试集划分：

```python
np.random.shuffle(data)

X = data[:,:-1]
Y = data[:,-1]

# last 100 rows will be test
Xtrain = X[:-100,]
Ytrain = Y[:-100,]
Xtest = X[-100:,]
Ytest = Y[-100:,]
```

此时，正如上一章所做的那样，训练分类器并查看测试分类率变得非常容易。

```python
model = LogisticRegression()
model.fit(Xtrain, Ytrain)
print "Classification rate:", model.score(Xtest, Ytest)
```

再次注意，90% 的工作只是数据处理！智能地完成这部分是 NLP 的重要组成部分。

请尝试运行并查看获得的分类率。

## 词级情感分析

最后，我们可以通过检查逻辑回归权重来查看每个单词的情感倾向。

```python
threshold = 0.5
for word, index in word_index_map.iteritems():
    weight = model.coef_[0][index]
    if weight > threshold or weight < -threshold:
        print word, weight
```

我们选择 0.5 作为阈值（即绝对值小于 0.5 的权重被视为中性）。以下是我发现的一些有趣结果：

| 单词 | 权重 |
| :--- | :--- |
| easy | 0.919927614044 |
| time | -0.600961986429 |
| love | 0.615388184001 |
| returned | -0.542160355628 |
| cable | 0.525780463192 |
| waste | -0.5615910491 |
| card | -0.623082827818 |
| price | 1.79091994573 |
| return | -0.622817513478 |
| you | 0.752460553703 |
| look | 0.509584059602 |
| quality | 0.976849032448 |
| speaker | 0.553046521681 |
| recommend | 0.540623118612 |
| item | -0.636201081354 |
| little | 0.532198613503 |
| sound | 0.577221784706 |
| n't | -1.42002037539 |
| buy | -0.513862313368 |
| excellent | 1.08015208784 |
| memory | 0.565900106762 |
| fast | 0.503794112607 |

令人鼓舞的是，这些结果大多非常合理！事实上，“讲得通”是对算法进行合理性检查的好方法。

# 第 5 章：NLTK 探索

在上一章中，我向您预览了 `NLTK`。您已经看到了 `tokenize` 函数和 `lemmatizer` —— 所以您已经知道 `NLTK` 如何发挥作用。

“NLTK” 是自然语言工具包。它是一个封装了大量 NLP 任务的库，这样您就不必自己编写它们。在本系列讲座中，我们将了解其中的一些功能，让您有个大概的了解，并可能为您自己的项目提供一些思路。

## 词性标注

我们要看的第一件事是“词性标注”或 POS tagging。当您看到它的实际效果时，它的作用将非常明显，而不是我试图抽象地解释它，所以让我们直接进入代码。

如果您尚未安装 `NLTK`，可以在命令行中执行 `sudo pip install nltk`。

请注意，对于其中一些示例，`NLTK` 可能会提示找不到某些资源。它会告诉您该资源是什么，以及如何下载它的说明 —— 只需在控制台运行 `nltk.download()`，选择它要求您下载的内容，然后您之前尝试做的事情现在应该可以工作了。

**POS 标注示例：**

```python
nltk.pos_tag("Machine learning is great".split())
```

输出：

```text
[('Machine', 'NN'), ('learning', 'NN'), ('is', 'VBZ'), ('great', 'JJ')]
```

在这里，您可以看到 POS 标注器告诉我们句子中每个单词的角色。它表明 "machine" 是名词，"learning" 是名词，"is" 是第三人称现在时动词，"great" 是形容词。

有关这些缩写含义的完整列表，请访问：[https://www.ling.upenn.edu/courses/Fall_2003/ling001/penn_treebank_pos.html](https://www.ling.upenn.edu/courses/Fall_2003/ling001/penn_treebank_pos.html)

## 词干提取与词形还原

接下来我们要看的是“词干提取”和“词形还原”。我们在情感分析器中已经使用过它们了。

两者的基本思想都是将单词还原为其基本形式。因此，如果是复数如 "dogs"，它会还原为 "dog"。"Jumping" 会还原为 "jump"，以此类推。

如果您试图创建词袋模型，但希望减少每个单词的变体（因为 "dogs" 和 "dog" 本质上具有相同的含义），这会很有用。

那么，词干提取和词形还原有什么区别呢？

可以将词干提取视为该任务的一个更“基本”或“粗糙”的版本 —— 有时它只是切掉单词的结尾以给出基本形式。让我们做个例子。

```python
from nltk.stem.porter import PorterStemmer

porter_stemmer = PorterStemmer()
porter_stemmer.stem('wolves')
```

输出：`'wolv'`

对比：

```python
from nltk.stem import WordNetLemmatizer

wordnet_lemmatizer = WordNetLemmatizer()
wordnet_lemmatizer.lemmatize("wolves")
```

输出：`'wolf'`

因此，您可以看到词干提取更粗糙，因为它可能返回甚至不是真实单词的内容。这在您的系统中可能是个问题，也可能不是，这取决于您的决定。请实验并查看哪个更快。

## 命名实体识别

我们在简介中简要讨论过命名实体识别（NER）。

以下是 `NLTK` 中的一些示例。

```python
nltk.ne_chunk(nltk.pos_tag("Albert Einstein was born on March 14, 1879.".split())).draw()
```
