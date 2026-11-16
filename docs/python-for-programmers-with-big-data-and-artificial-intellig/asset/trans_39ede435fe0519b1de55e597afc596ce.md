

TextBlob 是 textblob 模块中用于 NLP 的基础类。让我们创建一个包含两个句子的 TextBlob：

http://textblob.readthedocs.io/en/latest/api_reference.html#textblob.blob.TextBlob

点击此处查看代码图像

```
In [1]: from textblob import TextBlob

In [2]: text = 'Today is a beautiful day.  Tomorrow looks like bad weather.'

In [3]: blob = TextBlob(text)

In [4]: blob
Out[4]: TextBlob("Today is a beautiful day.  Tomorrow  looks like bad weather.")
```

TextBlobs——以及，正如您很快将看到的，Sentences 和 Words——支持字符串方法，并且可以与字符串进行比较。它们还为各种 NLP 任务提供了方法。Sentences、Words 和 TextBlobs 继承自 BaseBlob，因此具有许多共同的方法和属性。

## 11.2.2 将文本分割为句子和单词

自然语言处理在执行其他 NLP 任务之前通常需要对文本进行分词。TextBlob 提供了方便的属性来访问 TextBlob 中的句子和单词。让我们使用 sentence 属性来获取 Sentence 对象列表：

点击此处查看代码图像

```
In [5]: blob.sentences
Out[5]:
[Sentence("Today is a beautiful day."),
Sentence("Tomorrow looks like bad weather.")]
```

words 属性返回一个 WordList 对象，其中包含 Word 对象列表，表示 TextBlob 中每个单词，并已移除标点符号：

点击此处查看代码图像

```
In [6]: blob.words
Out[6]: WordList(['Today', 'is', 'a', 'beautiful', 'day', 'Tomorrow', 'looks', 'like', 'bad', 'weather'])
```

## 11.2.3 词性标注

有些词有多种含义。例如，“set”和“run”这两个词各有数百种含义！如果你查看 dictionary.com 上单词“run”的定义，你会发现它可以是动词、名词、形容词或动词短语的一部分。POS 标记的一个重要用途是确定词在其可能的众多含义中的含义。这对于帮助计算机“理解”自然语言非常重要。

tags 属性返回一个元组列表，每个元组包含一个词和一个表示其词性标签的字符串：

点击此处查看代码图像

```
In [7]: blob
Out[7]: TextBlob("Today is a beautiful day. Tomorrow looks like bad weather.")

In [8]: blob.tags
Out[8]:
[('Today', 'NN'),
 ('is', 'VBZ'),
 ('a', 'DT'),
 ('beautiful', 'JJ'),
 ('day', 'NN'),
 ('Tomorrow', 'NNP'),
 ('looks', 'VBZ'),
 ('like', 'IN'),
 ('bad', 'JJ'),
 ('weather', 'NN')]
```

默认情况下，TextBlob 使用 PatternTagger 来确定词性。该类使用 pattern 库的词性标注功能：

https://www.clips.uantwerpen.be/pattern

您可以在以下网址查看该库的 63 个词性标签：

https://www.clips.uantwerpen.be/pages/MBSP-tags

在前面的代码片段输出中：

- Today、day 和 weather 被标记为 NN——单数名词或不可数名词。
- is 和 looks 被标记为 VBZ——第三人称单数现在时动词。
- a 被标记为 DT——限定词。
- beautiful 和 bad 被标记为 JJ——形容词。
- Tomorrow 被标记为 NNP——专有单数名词。
- like 被标记为 IN——从属连词或介词。

7 https://en.wikipedia.org/wiki/Determiner.

## 11.2.4 提取名词短语

假设您正在准备购买水上滑雪板，因此正在网上研究它们。您可能会搜索“best water ski”。在这种情况下，“water ski”是一个名词短语。如果搜索引擎未能正确解析名词短语，您可能无法获得最佳搜索结果。请上网尝试搜索“best water”、“best ski”和“best water ski”，看看会得到什么结果。

TextBlob 的 `noun_phrases` 属性返回一个 `WordList` 对象，其中包含 `Word` 对象列表——文本中每个名词短语对应一个：

点击此处查看代码图像

```
In [9]: blob
Out[9]: TextBlob("Today is a beautiful day. Tomorrow looks like bad weather.")

In [10]: blob.noun_phrases
Out[10]: WordList(['beautiful day', 'tomorrow', 'bad weather'])
```

请注意，表示名词短语的 `Word` 可以包含多个单词。`WordList` 是 Python 内置列表类型的扩展。WordList 提供了用于词干提取、词形还原、单数化和复数化的其他方法。

## 11.2.5 使用 TextBlob 默认情感分析器进行情感分析

最常见且最有价值的 NLP 任务之一是 **情感分析**，用于确定文本是积极、中性还是消极。例如，公司可能会使用此功能来确定人们在网上对其产品是正面评价还是负面评价。请考虑积极词“good”和消极词“bad”。仅仅因为句子包含“good”或“bad”并不意味着句子的情感必然是积极或消极。例如，句子

The food is not good.

明显带有消极情感。同样，句子

The movie was not bad.

明显带有积极情感，尽管可能不如类似句子那么积极

The movie was excellent!

情感分析是一个复杂的机器学习问题。然而，像 TextBlob 这样的库带有用于执行情感分析的预训练机器学习模型。

### 获取 TextBlob 的情感

TextBlob 的 `sentiment` 属性返回一个 `Sentiment` 对象，指示文本是积极还是消极，以及是客观还是主观：

点击此处查看代码图像

```
In [11]: blob
Out[11]: TextBlob("Today is a beautiful day. Tomorrow looks like bad weather.")
```

```
In [12]: blob.sentiment
Out[12]: Sentiment(polarity=0.075000000000000007,
 subjectivity=0.8333333333333333)
```

在前面的输出中，极性（polarity）的值范围从 -1.0（消极）到 1.0（积极），0.0 表示中性。主观性（subjectivity）的值范围从 0.0（客观）到 1.0（主观）。根据我们 TextBlob 的值，总体情感接近中性，文本大多是主观的。

### 从 Sentiment 对象获取极性和主观性

上面显示的值可能在大多数情况下提供了超出您所需精度的精度。这会影响数字输出的可读性。IPython 魔术命令 %precision 允许您为独立浮点对象以及列表、字典和元组等内置类型中的浮点对象指定默认精度。让我们使用该魔术命令将极性和主观性值舍入到小数点后三位：

点击此处查看代码图像

```
In [13]: %precision 3
Out[13]: '%.3f'

In [14]: blob.sentiment.polarity
Out[14]: 0.075

In [15]: blob.sentiment.subjectivity
Out[15]: 0.833
```

### 获取句子的情感

您也可以在单个句子级别获取情感。让我们使用 sentence 属性获取 Sentence 对象列表，然后遍历它们并显示每个 Sentence 的 sentiment 属性：

http://textblob.readthedocs.io/en/latest/api_reference.html#textblob.blob.Sentence

点击此处查看代码图像

```
In [16]: for sentence in blob.sentences:
    ...:     print(sentence.sentiment)
    ...:
Sentiment(polarity=0.85, subjectivity=1.0)
Sentiment(polarity=-0.69999999999999998, subjectivity=0.6666666666666666)
```

这可能解释了为什么整个 TextBlob 的情感接近 0.0（中性）——一个句子是积极的（0.85），另一个是消极的（-0.69999999999999998）。

## 11.2.6 使用 NaiveBayesAnalyzer 进行情感分析

默认情况下，TextBlob 及其派生的 Sentences 和 Words 使用 `PatternAnalyzer` 来确定情感，该分析器使用与 Pattern 库相同的情感分析技术。TextBlob 库还附带了一个 `NaiveBayesAnalyzer`[^9]（模块 `textblob.sentiments`），它在电影评论数据库上进行了训练。Naive Bayes[^0] 是一种常用的机器学习文本分类算法。以下内容使用 `analyzer` 关键字参数来指定 TextBlob 的情感分析器。请回顾，在此正在进行的 IPython 会话中，`text` 包含 'Today is a beautiful day. Tomorrow looks like bad weather.'：

[^9]: https://textblob.readthedocs.io/en/latest/api_reference.html#module-textblob.en.sentiments.
[^0]: https://en.wikipedia.org/wiki/Naive_Bayes_classifier.

点击此处查看代码图像

```
In [17]: from textblob.sentiments import NaiveBayesAnalyzer

In [18]: blob = TextBlob(text, analyzer=NaiveBayesAnalyzer())

In [19]: blob
Out[19]: TextBlob("Today is a beautiful day. Tomorrow looks like bad weather.")
```

让我们使用 TextBlob 的 sentiment 属性来使用 NaiveBayesAnalyzer 显示文本的情感：

点击此处查看代码图像

```
In [20]: blob.sentiment
Out[20]: Sentiment(classification='neg', p_pos=0.47662917962091056, p_neg=0.5233708203790894)
```

在此情况下，总体情感被分类为消极（`classification='neg'`）。`Sentiment` 对象的 `p_pos` 表示该 TextBlob 有 47.66% 是积极的，而其 `p_neg` 表示该 TextBlob 有 52.34% 是消极的。由于总体情感仅略微偏消极，我们可能会认为此 TextBlob 的总体情感是中性的。

现在，让我们获取每个 Sentence 的情感：

点击此处查看代码图像

```
In [21]: for sentence in blob.sentences:
   ...:     print(sentence.sentiment)
   ...:
Sentiment(classification='pos', p_pos=0.8117563121751951, p_neg=0.1882436878248049)
Sentiment(classification='neg', p_pos=0.174363226578349, p_neg=0.825636773421651)
```

请注意，与 `polarity` 和 `subjectivity` 不同，我们从 `NaiveBayesAnalyzer` 获得的 `Sentiment` 对象包含一个 `classification`——'pos'（积极）或 'neg'（消极）——以及 `p_pos`（积极百分比）和 `p_neg`（消极百分比）值，范围从 `0.0` 到 `1.0`。

