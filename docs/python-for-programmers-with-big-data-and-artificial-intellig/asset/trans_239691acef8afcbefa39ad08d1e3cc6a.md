

下载处理英文（en）文本所需的其他组件：

单击此处查看代码图像

```
python -m spacy download en
```

## 加载语言模型

使用 spaCy 的第一步是加载表示你正在分析的文本的自然语言的语言模型。为此，你将调用 `spacy` 模块的 `load` 函数。让我们加载上面下载的英文模型：

单击此处查看代码图像

```
In [1]: import spacy

In [2]: nlp = spacy.load('en')
```

spaCy 文档推荐使用变量名 `nlp`。

## 创建 spaCy Doc

接下来，你使用 `nlp` 对象创建一个 spaCy `Doc` 对象 ³，表示要处理的文档。这里我们使用了许多书籍中关于万维网（World Wide Web）介绍的一个句子：

³ https://spacy.io/api/doc.

单击此处查看代码图像

```
In [3]: document = nlp('In 1994, Tim Berners-Lee founded the ' +
... 'World Wide Web Consortium (W3C), devoted to ' +
... 'developing web technologies')
```

## 获取命名实体

`Doc` 对象的 `ents` 属性返回一个表示在 `Doc` 中找到的命名实体的 `Span` 对象元组。每个 `Span` 都有许多属性。⁴ 让我们遍历 `Span`s 并显示 `text` 和 `label_` 属性：

⁴ https://spacy.io/api/span.

单击此处查看代码图像

```
In [4]: for entity in document.ents:
... print(f'{entity.text}: {entity.label_}')
...
1994: DATE
Tim Berners-Lee: PERSON
the World Wide Web Consortium: ORG
```

每个 Span 的 text 属性将实体作为字符串返回，而 `label_` 属性返回一个表示实体类型的字符串。在这里，spaCy 找到了三个实体，分别表示 DATE（1994）、PERSON（Tim Berners-Lee）和 ORG（组织；万维网联盟）。要了解更多 spaCy 信息并查看其快速入门指南，请参阅

```
https://spacy.io/usage/models#section-quickstart
```

## 11.6 使用 spaCy 进行相似度检测

相似度检测是分析文档以确定它们有多相似的过程。一种可能的相似度检测技术是词频统计。例如，有些人认为威廉·莎士比亚的作品实际上可能是由弗朗西斯·培根爵士、克里斯托弗·马洛或其他人撰写的。5 将他们的作品词频与莎士比亚作品的词频进行比较，可以揭示写作风格的相似性。

5 https://en.wikipedia.org/wiki/Shakespeare_authorship_question.

后面章节将讨论的各种机器学习技术可用于研究文档相似性。然而，正如 Python 中经常发生的情况一样，有 spaCy 和 Gensim 等库可以为你完成这项工作。这里，我们将使用 spaCy 的相似度检测功能来比较代表《罗密欧与朱丽叶》的 Doc 对象与代表《爱德华二世》的 Christopher Marlowe 的 Doc 对象。你可以从 Project Gutenberg 下载《爱德华二世》，就像我们前面在本章对《罗密欧与朱丽叶》所做的那样。6

6 每个 Project Gutenberg 电子书都包含额外文本，例如其许可信息，这些不是电子书本身的一部分。为此示例，我们使用文本编辑器从我们的电子书副本中删除了该文本。

## 加载语言模型并创建 spaCy Doc

与前一部分一样，我们首先加载英文模型：

单击此处查看代码图像

```
In [1]: import spacy
In [2]: nlp = spacy.load('en')
```

## 创建 spaCy Docs

接下来，我们创建两个 Doc 对象——一个用于《罗密欧与朱丽叶》，另一个用于《爱德华二世》：

单击此处查看代码图像

```
In [3]: from pathlib import Path
In [4]: document1 = nlp(Path('RomeoAndJuliet.txt').read_text())
In [5]: document2 = nlp(Path('EdwardTheSecond.txt').read_text())
```

## 比较图书的相似度

最后，我们使用 `Doc` 类的 `similarity` 方法获取一个从 0.0（不相似）到 1.0（完全相同）的值，表示文档的相似程度：

单击此处查看代码图像

```
In [6]: document1.similarity(document2)
Out[6]: 0.9349950179100041
```

spaCy 认为这两个文档有显著相似性。为了进行比较，我们创建了一个代表当前新闻故事的 `Doc` 并将其与 *罗密欧与朱丽叶* 进行了比较。如预期，spaCy 返回了一个低值，表明它们之间几乎没有相似性。尝试将一篇当前新闻文章复制到文本文件中，然后自己执行相似度比较。

## 11.7 其他 NLP 库和工具

我们向你展示了各种 NLP 库，但调查你可用的各种选项始终是个好主意，以便你能为任务利用最佳工具。以下是一些额外的大多免费开源的 NLP 库和 API：

- Gensim—相似度检测和主题建模。
- Google Cloud Natural Language API—用于 NLP 任务的基于云的 API，例如命名实体识别、情感分析、词性分析和可视化、确定内容类别等。
- Microsoft Linguistic Analysis API。
- Bing 情感分析—Microsoft 的 Bing 搜索引擎现在在其搜索结果中使用情感。在撰写本文时，搜索结果中的情感分析仅在美国可用。
- PyTorch NLP—用于 NLP 的深度学习库。
- Stanford CoreNLP—一个 Java NLP 库，同时还提供 Python 封装器。包括共指消解，用于查找对同一事物的所有引用。
- Apache OpenNLP—另一个用于常见任务的基于 Java 的 NLP 库，包括共指消解。提供 Python 封装器。
- PyNLPl (pineapple)—Python NLP 库，包括基础和更高级的 NLP 功能。
- SnowNLP—简化中文文本处理的 Python 库。
- KoNLPy—韩语 NLP。
- stop-words—带有多种语言停用词的 Python 库。本章中我们使用了 NLTK 的停用词列表。
- TextRazor—一个付费的基于云的 NLP API，提供免费层。

## 11.8 机器学习和深度学习自然语言应用

有许多自然语言应用需要机器学习和深度学习技术。我们将在机器学习和深度学习章节中讨论以下一些应用：

- 回答自然语言问题—例如，我们的出版商 Pearson Education 与 IBM Watson 有合作伙伴关系，使用 Watson 作为虚拟导师。学生向 Watson 提出自然语言问题并获得答案。
- 文档摘要—分析文档并生成简短摘要（也称为 abstracts），例如可以包含在搜索结果中，帮助你决定阅读什么。
- 语音合成（语音转文本）和语音识别（文本转语音）—我们在“IBM Watson”章节中使用这些技术，并结合跨语言文本到文本翻译，开发近乎实时的跨语言语音到语音翻译器。
- 协同过滤—用于实现推荐系统（“如果你喜欢这部电影，你可能也会喜欢…”）。
- 文本分类—例如，按类别对新闻文章进行分类，如世界新闻、国家新闻、本地新闻、体育、商业、娱乐等。
- 主题建模—查找文档中讨论的主题。
- 讽刺检测—通常与情感分析一起使用。
- 文本简化—使文本更简洁、更易读。
- 语音转手语及反之—使与听力障碍人士的对话成为可能。
- 唇读技术—对于无法说话的人，将嘴唇动作转换为文本或语音以实现对话。
- 闭幕字幕—向视频添加文本字幕。

## 11.9 自然语言数据集

可用于自然语言处理的文本数据源数量庞大：

- 维基百科—维基百科的部分或全部内容（ `https://meta.wikimedia.org/wiki/Datasets`）。
- IMDB（互联网电影数据库）—提供各种电影和电视数据集。
- UCI 的文本数据集—许多数据集，包括 Spambase 数据集。

