
Listing 5.5 包含一个导入语句，随后初始化变量 `sentences` 为文本字符串数组。随后的代码片段遍历 `sentences` 数组中的字符串，并打印每个句子以及其扩展后的版本。

如输出所示，数组 `sentences` 中最后一个句子的缩写词 `sky's` 未被扩展，因此需要添加新的扩展规则：

`contractions.add("sky's", "sky is")`

再次处理该字符串后，缩写词 `sky's` 会被正确扩展。运行 Listing 5.5 中的代码，将看到以下输出：

```
sentence: what's new? expanded: what is new?   sentence: how's the weather expanded: how is the weather   sentence: it's humid today expanded: it is humid today   sentence: we've been there before expanded: we have been there before   sentence: you should've been there! expanded: you should have been there!   sentence: the sky's the limit expanded: the sky's the limit   => updating contraction rules... sentence: the sky's the limit expanded: the sky is the limit
```

作为替代方法，你也可以编写 Python 代码扩展缩写词，如下所示：

```
CONTRACT = {"how's":"how is", "what's":"what is", "it's":"it is", "we've":"we have", "should've" :"should have", "sky's": "sky is"}

sentences = ["what's new?", "how's the weather", "it's humid today", "we've been there before", "you should've been there!", "the sky's the limit"]

for sent in sentences:
    words = sent.split()
    expanded = [CONTRACT[w] if w in CONTRACT else w for w in words]
    new_sent = " ".join(expanded)
    print("sentence:",sent)
    print("expanded:",new_sent)
    print()
```

## Python 代码示例：BoW（词袋模型）

正如第 4 章节所学，BoW 是一种将单词集合编码为数值向量的技术。本节包含一些简单的 Python 代码示例，演示如何在一组单词上执行此技术。

BoW 算法统计单词在文档中出现的次数，这将一般化为一种一热编码的扩展。这些单词计数使我们能够比较文档并衡量其相似度。BoW 算法可用于搜索、文档分类和主题建模等应用。此外，BoW 还可用于为深度学习神经网络预处理文本输入。

图 5.6 显示了 `bow_to_vector1.py` 的内容，展示了如何基于给定的词汇创建一维数值向量。

### Listing 5.6: bow_to_vector1.py

```
VOCAB = ['dog', 'cheese', 'cat', 'mouse']
TEXT1 = 'the mouse ate the cheese'
TEXT2 = 'the horse ate the hay'
def to_bow(text):
    words = text.split(" ")
    return [1 if w in words else 0 for w in VOCAB]
print("VOCAB: ",VOCAB)
print("TEXT1:",TEXT1)
print("BOW1: ",to_bow(TEXT1)) # [0, 1, 0, 1]
print("")
print("TEXT2:",TEXT2)
print("BOW2: ",to_bow(TEXT2)) # [0, 0, 0, 0]
```

Listing 5.6 初始化了变量 `VOCAB`、`TEXT1` 和 `TEXT2`，随后定义了 Python 函数 `to_bow()` 用于构建文本字符串的 BoW（袋状词）表示。接着，该函数分别用 `TEXT1` 和 `TEXT2` 调用两次。运行 Listing 5.6 中的代码，将看到如下输出：

```
VOCAB: ['dog', 'cheese', 'cat', 'mouse']
TEXT1: the mouse ate the cheese
BOW1: [0, 1, 0, 1]
TEXT2: the horse ate the hay
BOW2: [0, 0, 0, 0]
```

Listing 5.7 显示了 `bow_to_vector2.py` 的内容，展示了如何基于给定的词汇创建一维数值向量。

### Listing 5.7: bow_to_vector2.py

```
VOCAB = ['dog', 'cheese', 'cat', 'mouse']
MYTEXT = 'the mouse ate the cheese'
def to_bow(text):
    words = text.split(" ")
    found = [w if w in words else "MISS" for w in VOCAB]
    missing = [w if w not in words else "FOUND" for w in VOCAB]
    print("Found:",found)
    print("Missing:",missing)
    return [1 if w in words else 0 for w in VOCAB]
print("MYTEXT:",MYTEXT)
print("VOCAB: ",VOCAB)
print("MYTEXT:",to_bow(MYTEXT)) # [0, 1, 0, 1]
```

Listing 5.7 在 Listing 5.6 的基础上，增加了跟踪句子中未包含在词汇表里的单词的功能。运行 Listing 5.7 后，将看到如下输出：

```
MYTEXT: the mouse ate the cheese
VOCAB: ['dog', 'cheese', 'cat', 'mouse']
Found: ['MISS', 'cheese', 'MISS', 'mouse']
Missing: ['dog', 'FOUND', 'cat', 'FOUND']
MYTEXT: [0, 1, 0, 1]
```

Listing 5.8 显示了 `count_vectorize.py` 的内容，展示了如何基于给定的词汇创建一维数值向量。

### Listing 5.8: count_vectorize.py

```
VOCAB = ['dog', 'cheese', 'cat', 'mouse']
TEXT1 = 'the mouse ate the cheese'
TEXT2 = 'the horse ate the hay'
from sklearn.feature_extraction.text import CountVectorizer
vectorizer = CountVectorizer(vocabulary=VOCAB)
result1 = vectorizer.transform([TEXT1]).todense() # matrix([[0,1,0,1]])
result2 = vectorizer.transform([TEXT2]).todense() # matrix([[0,1,0,1]])
print("VOCAB: ",VOCAB)
print("TEXT1:",TEXT1)
print("BOW1: ",result1) # [0, 1, 0, 1]
print("")
print("TEXT2:",TEXT2)
print("BOW2: ",result2) # [0, 1, 0, 1]
print()
print("=> contents of countvectorizer:")
print(vectorizer)
```

Listing 5.8 通过 Sklearn 中的 `CountVectorizer` 类实现的功能与 Listing 5.6 中的自定义代码相同。运行 Listing 5.8 后，将看到如下输出（与 `bow_to_vector1.py` 的输出相同）：

```
VOCAB: ['dog', 'cheese', 'cat', 'mouse']
TEXT1: the mouse ate the cheese
BOW1: [[0 1 0 1]]
TEXT2: the horse ate the hay
BOW2: [[0 0 0 0]]
=> contents of countvectorizer:
CountVectorizer(analyzer='word', binary=False, decode_error='strict', dtype=<class 'numpy.int64'>, encoding='utf-8', input='content', lowercase=True, max_df=1.0, max_features=None, min_df=1, ngram_range=(1, 1), preprocessor=None, stop_words=None, strip_accents=None, token_pattern='(?u)\\b\\w\\w+\\b', tokenizer=None, vocabulary=['dog', 'cheese', 'cat', 'mouse'])
```

如上所示，变量 `vectorizer` 的词汇表与变量 `VOCAB` 的内容相同。

Listing 5.9 包含了一个 BoW 示例，展示了如何在 Pandas 数据框中使用 BoW 处理句子数组。

### Listing 5.9: bow_pandas.py

```
import pandas as pd
from sklearn.feature_extraction.text import CountVectorizer
sent = ["this is a sentence with text and very simple", "a second sentence with text and listed second", "a third sentence with text and listed third", "a final sentence with text"]
print("=> list of sentences:")
for s in sent:
    print(s)
print()
bow = CountVectorizer()
bow_fit = bow.fit_transform(sent)
bag_words = pd.DataFrame(bow_fit.toarray())
bag_words.columns = bow.get_feature_names()
print("=> bag_words for the sentences:")
print(bag_words)
```

Listing 5.9 初始化变量 `sent` 为句子数组，随后通过 for 循环显示这些句子。接着，变量 `bow` 初始化为 Sklearn 库提供的 `CountVectorizer` 实例。`bow_fit` 变量保存将 `sent` 数据进行 `fit_transform` 后的结果。`bag_words` 变量初始化为包含 `bow_fit` 数据的 DataFrame。为 `bag_words` 指定列名后，通过 `print()` 语句显示其内容。运行 Listing 5.9 将看到如下输出（因宽度限制，输出被截断）：

```
=> list of sentences:
this is a sentence with text and very simple
a second sentence with text and listed second
a third sentence with text and listed third
a final sentence with text
=> bag_words for the sentences:
and final is listed second sentence simple text third this very with
0 1 0 1 0 0 1 1 1 0 1 1 1 1 0 0 1 2 1 0 1 0 0 0 1 2 0 0 1 3 0 1 0 0 0 1 0 1 0 0 0 1 0 1 0 0 0 1
```

在章节 7 中，你将看到使用 NLTK 库创建 BoW 模型的示例；在章节 9 中，你将看到使用 TF2/Keras 创建 BoW 模型的示例。

### One-Hot Encoding 示例

回顾章节 4，一热编码为一组单词提供一个数值向量，每个向量中只有一个值为 1，其余值均为 0。例如，句子 “I love thick pizza” 可被分词为 `["i", "love", "thick", "pizza"]`，并一热编码为：

```
[1,0,0,0]
[0,1,0,0]
[0,0,1,0]
[0,0,0,1]
```

基于上述一热编码，句子 “We also love thick pizza” 可编码为：

```
[0,1,1,1] = [0,1,0,0] + [0,0,1,0] + [0,0,0,1]
```

可以看到，左侧向量 `[0,1,1,1]` 是三个单词（love、thick、pizza）的对应一热编码向量的求和。该句子的第一个索引为 0，是因为句子中包含 “we” 而非 “i”。

Listing 5.10 显示了 `onehot_encode.py` 的内容，展示了如何对一组单词进行一热编码。

### Listing 5.10: onehot_encode.py

```
import numpy as np
CLASSES = list(np.array([3, 1, 2])) # The dataset labels
LABELS = np.array([1, 2, 3, 1, 2, 1, 1, 2, 3])
VALUES = [3, 3, 1, 1, 2, 2]
ONEHOT = np.zeros((len(LABELS), len(CLASSES)))
for idx, value in enumerate(LABELS):
    print("idx:",idx,"value:",value)
    ONEHOT[idx, CLASSES.index(value)] = 1
print("One-hot Encoding:")
print(ONEHOT)
```

# 5.10 变量初始化

initializes the variable `CLASSES` as a list created from a NumPy array that contains the numbers 3, 1, and 2. The next code block initializes the variables `LABELS`, `VALUES`, and `ONEHOT`, followed by a for loop that initializes each row of `ONEHOT` as a one-hot encoded vector. Launch the code in Listing 5.10 and you will see the following output:

```
idx: 0 value: 1
idx: 1 value: 2
idx: 2 value: 3
idx: 3 value: 1
idx: 4 value: 2
idx: 5 value: 1
idx: 6 value: 1
idx: 7 value: 2
idx: 8 value: 3
One-hot Encoding:
[[0. 1. 0.]
 [0. 0. 1.]
 [1. 0. 0.]
 [0. 1. 0.]
 [0. 0. 1.]
 [0. 1. 0.]
 [0. 1. 0.]
 [0. 0. 1.]
 [1. 0. 0.]]
```

## Sklearn and Word Embedding Examples

Word embeddings pertain to algorithms that represent words (as well as documents) using a dense vector representation, which is a distributed representation. By contrast, vector representations refer to discrete representations, such as the use of the tf-idf values of words to generate vector representations of words.

Earlier in this chapter you saw an example of word vectorization, and this section contains a consolidated list of word embedding techniques, along with code samples that illustrate how to use these techniques:

- Count Vectorizer
- TF-IDF Vectorizer
- Hashing Vectorizer
- Word2Vec (gensim)

Listing 5.11 displays the contents of `count_vectorize2.py` that illustrates how to vectorize an array of sentences using the `CountVectorizer` class in Sklearn.

### Listing 5.11: count_vectorize2.py

```
