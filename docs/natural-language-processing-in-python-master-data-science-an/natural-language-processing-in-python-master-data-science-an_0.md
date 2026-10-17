
# Python 自然语言处理实战：掌握垃圾检测、情感分析、潜在语义分析与文章重写的数据科学与机器学习

掌握数据科学与机器学习，用于垃圾邮件检测、情感分析、潜在语义分析与文章重写

作者：The LazyProgrammer ([`lazyprogrammer.me`](http://lazyprogrammer.me))

最近，微软的 Twitter 机器人“Tay”被发布到网络上，在向其他 Twitter 用户学习后，迅速开始发表种族主义和仇恨言论。这背后的技术是什么？自然语言处理。

自然语言处理是将机器学习算法应用于涉及文本的问题。

这是当今最重要的问题之一，因为互联网的很大一部分由文本组成。借助 NLP，我们可以分析它、理解它、对其分类并对其进行摘要——且这一切都能自动完成。

你是否想过，为什么现在收件箱里的垃圾邮件比 10 年前少得多？人们在用什么样的算法进行垃圾邮件检测？它们如何获取邮件中的词汇，并计算出它是否为垃圾邮件？在本书中，你将亲手构建一个垃圾邮件检测器。

你是否知道，人们已经利用 Twitter 判断公众对某家公司的当前情绪，以决定是买入还是卖出股票？拥有一台能判断人们对某事物感受的机器，用处极大，且能直接应用于收入优化。在本课程中，你将构建自己的情感分析器。

你是互联网营销人员，还是对 SEO 感兴趣？你是否曾想过如何自动生成内容？在本课程中，我们将初步尝试构建你自己的文章重写器。你将学习编写程序，接收一篇文章作为输入，输出一篇用词不同但含义相似的文章。如果你雇人写作，这能为你节省大量时间和数千美元。

自然语言处理，常缩写为 NLP——即利用编程和数学来完成基于语言的任务。

如果你使用 Windows 或 iOS，那你面前就有 NLP！Cortana 和 Siri 就是将你所说的话转化为可通过编程处理的有意义内容的应用程序。

关键点：**NLP 极其实用。NLP 无处不在。**

在进行真正的编程练习前，我们将先了解常见的 NLP 任务（其中一些我们将亲自编码实现，另一些仅作介绍，让你至少知道它们的存在）。随后我们将探讨文本常用的数据预处理技术。你将看到，这种预处理实际上会占据你做 NLP 时的大部分时间。

第一个编程练习是构建垃圾邮件检测器。你的电子邮箱就在用它，所以它显然非常实用，且已被研究了很长时间。

接下来我们将探讨“情感分析”，并构建你自己的“情感分析器”。这是计算机根据使用的词汇和短语，判断文本积极或消极程度的方法。这也极其实用——有人分析 Twitter 数据流来预测股票涨跌。

随后我们将了解 `NLTK` 库。这是一个非常流行的库，能解决 NLP 中许多基础问题——你可以在数据分析管道中将其与其他库结合使用。

接下来我们将探讨“潜在语义分析”。这本质上是对文本进行降维——它帮我们解决两个词含义相同的问题。它还能帮助我们解读数据并节省计算时间。

最后，我们将讨论 NLP 最流行的应用之一——文章重写。这对互联网营销人员和企业家非常实用。众所周知，重复内容会对你在 Google 等搜索引擎中的排名产生负面影响——所以如果能对写好的文章进行适度修改，就能将其发布在网络上的两个不同位置，而不受 Google 惩罚。

本书理解所需的数学知识极少。如果有数学内容，仅供兴趣参考，并非完成编程部分的关键。当然，你仍需懂得编程，因为 NLP 主要属于编程领域，但我设计本书所需的数学知识比我的深度学习和神经网络类书籍少得多。

跟随本书所需的所有材料均可**免费**下载。我们使用 `Python`、`NLTK`、`Sci-kit learn` 和 `Numpy`，均可通过简单命令安装。

## 第 1 章：NLP 究竟是做什么的？

既然 NLP 实质上是将机器学习和软件工程应用于文本和语言问题，我认为非常有必要讨论——这些应用是什么？它们在现实生活中有何用处？

在本章中，我将介绍 NLP 的一些实际应用，并探讨我们用现有技术解决这些问题的程度如何。本书大部分内容将略过理论，转而讨论“如何利用现有库编写代码解决这些 NLP 问题？”我们将先看几个当前技术非常成熟的问题，再看几个技术尚可但不够完美的问题，最后看几个技术“勉强能用”但仍有很大改进空间的问题。

以下是我们目前解决得非常好的问题：

我的邮箱里几乎不再收到垃圾邮件。Gmail 甚至有算法能将邮件分到不同标签页，如社交媒体相关帖子的“社交”标签、营销邮件的“推广”标签。

我们想知道句子中哪些词是副词、形容词、名词、代词、动词等。我们对这些分类的效果非常好。

**输入：**

> “The quick brown fox jumps over the lazy dog.”

**输出：**

> (冠词, 形容词, 形容词, 名词, 复数名词, …)

网上有许多在线工具可演示此功能，例如：[`parts-of-speech.info/`](http://parts-of-speech.info/)

**输入：** “Jim bought 300 shares of Apple in 2006.”

我们希望识别出“Jim”是人名，“Apple”是组织名，“2006”是日期。

有些问题我们解决得不错，但尚未达到完美：

这是本课程将涵盖的内容。假设你在网上查看酒店评论，想知道总体上人们认为这家酒店好还是坏。你可以自己阅读评论——但如果想让机器打出正向或负向分数，就没那么简单了。其中一个问题（还有许多其他问题）是机器难以轻易识别讽刺。所以如果你说的话词面意思与真实含义相反，就会让机器困惑。

这是一个类似 Google Translate 的工具。输入一个短语，将其通过几种不同的语言进行转换。你会发现，当我们转回英语时，结果讲不通。**练习：亲自试一试**

```python
from bs4 import BeautifulSoup

positive_reviews = BeautifulSoup(
    open(
        'electronics/positive.review'
    ).read())
positive_reviews = positive_reviews.findAll('review_text')
```

这一次，我们只看正面评论。

接下来，我们提取三元组。键将是首尾单词。值将是可能的中间单词数组。

```python
trigrams = {}

for review in positive_reviews:
    s = review.text.lower()
    tokens = nltk.tokenize.word_tokenize(s)
    for i in xrange(len(tokens) - 2):
        k = (tokens[i], tokens[i+2])
        if k not in trigrams:
            trigrams[k] = []
        trigrams[k].append(tokens[i+1])
```

接下来，我们要将每个中间单词数组转换为概率向量。

```python
trigram_probabilities = {}

for k, words in trigrams.iteritems():
    # 创建一个单词 -> 计数的字典
    if len(set(words)) > 1:
        # 只有当中间单词有不同可能性时才执行此操作
        d = {}
        n = 0
        for w in words:
            if w not in d:
                d[w] = 0
            d[w] += 1
            n += 1
        for w, c in d.iteritems():
            d[w] = float(c) / n
        trigram_probabilities[k] = d
```

这意味着如果可能的中间单词是 `["cat", "cat", "dog"]`，那么我们现在将得到一个字典 `{"cat": 0.67, "dog": 0.33}`。

因此，如果我们遇到上下文提供了这些可能性的情况，那么我们将以 2/3 的概率插入“cat”作为中间单词，以 1/3 的概率插入“dog”。

接下来，我们将创建一种从字典中随机采样的方法。

```python
def random_sample(d):
    # 从字典中选择一个随机样本，其中值为概率
    r = random.random()
    cumulative = 0
    for w, p in d.iteritems():
        cumulative += p
        if r < cumulative:
            return w
```

最后，让我们编写一个函数来测试重写器。

```python
def test_spinner():
    review = random.choice(positive_reviews)
    s = review.text.lower()
    print "Original:", s
    tokens = nltk.tokenize.word_tokenize(s)
    for i in xrange(len(tokens) - 2):
        if random.random() < 0.2: # 20% 替换几率
            k = (tokens[i], tokens[i+2])
            if k in trigram_probabilities:
                w = random_sample(trigram_probabilities[k])
                tokens[i+1] = w
    print "Spun:"
    print " ".join(tokens).replace(" .", ".").replace(" '", "'").replace(" ,", ",").replace("$ ", "$").replace(" !", "!")
```



最后一行替换了我注意到总是出现在奇怪位置的一些标点符号。或者，你也可以像前几章那样使用自定义分词器来替换标点符号。

以下是一些示例输出：

**原文：**

> i downloaded the driver from trendnet's website before installing the adapter. i did not encounter any problems at all, including the issue that some users had with it disconnecting when they plugged in another usb device

**重写后：**

> i downloaded the driver from trendnet's limits before installing the adapter. i did not encounter any problems at all, including the issue that new users had with it disconnecting when they plugged in another usb device

**另一个。**

**原文：**

> the reason it is not rated 5 stars is that the ink supply is utilized too rapidly and the expensive cartriges have to replaced too frequently

**重写后：**

> the reason it does not afford 5 stars is that the ink supply is utilized too rapidly and the expensive cartriges have to use too frequently

自己试试看还能得到什么结果。

你可以看到很多结果相当滑稽。这绝对表明应该有比仅检查两个相邻单词更多的上下文检查。

这告诉我们关于类“马尔可夫”假设的什么？它不成立！

这可能只是构建一个真正优秀的文章重写器所需工作的 5%。

请注意，这绝非易事。快速谷歌搜索显示，即使是顶级结果也远称不上是好的产品。

# 结语

我真心希望阅读这本书给你带来的乐趣，不亚于我制作它时的乐趣。

你有没有发现什么困惑的地方？有什么问题吗？

我随时可以提供帮助。只需发邮件至：info@lazyprogrammer.me

想了解更多关于数据科学和机器学习的知识吗？也许在线课程更适合你。我恰好在 Udemy 上有几门课程。

深度学习和神经网络的背景及先修知识可以在我的课程“Data Science: Deep Learning in Python”（正式称为系列的“第 1 部分”）中找到。在该课程中，我教你神经网络的前向传播机制（本书假设你已知晓），以及如何推导称为反向传播的训练算法（本书也假设你已知晓）：

[Data Science: Deep Learning in Python](https://udemy.com/data-science-deep-learning-in-python)

[`udemy.com/data-science-deep-learning-in-python`](https://udemy.com/data-science-deep-learning-in-python)

Kindle 版对应书籍：

[`kdp.amazon.com/amazon-dp-action/us/bookshelf.marketplacelink/B01CVJ19E8`](https://kdp.amazon.com/amazon-dp-action/us/bookshelf.marketplacelink/B01CVJ19E8)

你对这些材料驾轻就熟，并想将深度学习技能提升到一个新水平吗？那么我的深度学习后续 Udemy 课程适合你。类似于前一本书，我将带你了解 Theano 和 TensorFlow 的基础知识——创建函数、变量和表达式，并从头构建神经网络。我教你加速学习过程的方法，包括批量梯度下降、动量和自适应学习率。我还会现场演示如何在 Amazon AWS EC2 上创建 GPU 实例，并向你证明使用 GPU 优化训练神经网络比在 CPU 上快几个数量级。

[Data Science: Practical Deep Learning in Theano and TensorFlow](https://www.udemy.com/data-science-deep-learning-in-theano-tensorflow/)

[`www.udemy.com/data-science-deep-learning-in-theano-tensorflow`](https://www.udemy.com/data-science-deep-learning-in-theano-tensorflow)

在深度学习第 3 部分——卷积神经网络中，我教你一种特殊的神经网络，专为图像分类和特征学习而设计。

[Deep Learning: Convolutional Neural Networks in Python](https://www.udemy.com/deep-learning-convolutional-neural-networks-theano-tensorflow)

## 推荐课程与资源

### 深度学习系列第 4 部分：无监督深度学习

[`www.udemy.com/deep-learning-convolutional-neural-networks-theano-tensorflow`](https://www.udemy.com/deep-learning-convolutional-neural-networks-theano-tensorflow)

在深度学习系列的第 4 部分中，我将带你了解无监督深度学习方法。我们将学习主成分分析（PCA）、t-SNE（由深度学习教父 Geoffrey Hinton 共同开发）、深度自编码器和受限玻尔兹曼机（RBMs）。我将演示如何使用自编码器和 RBMs 对深度网络进行无监督预训练，从而提升有监督学习的性能。

### Python 无监督深度学习

[Python 无监督深度学习](https://www.udemy.com/unsupervised-deep-learning-in-python)

[`www.udemy.com/unsupervised-deep-learning-in-python`](https://www.udemy.com/unsupervised-deep-learning-in-python)

### 逻辑回归入门

想要了解神经网络的基本构建模块——逻辑回归吗？在本课程中，我讲解逻辑回归理论（我们的神经元计算模型），并深入探讨二分类、手动创建特征和梯度下降。如果你觉得本书内容太有挑战性，不妨看看这门课程。

[数据科学：Python 逻辑回归](https://udemy.com/data-science-logistic-regression-in-python)

[`udemy.com/data-science-logistic-regression-in-python`](https://udemy.com/data-science-logistic-regression-in-python)

### 深度学习先修知识对应书籍

[`kdp.amazon.com/amazon-dp-action/us/bookshelf.marketplacelink/B01D7GDRQ2`](https://kdp.amazon.com/amazon-dp-action/us/bookshelf.marketplacelink/B01D7GDRQ2)

### 线性回归：机器学习的简化视角

为了获得对机器学习更简单的整体认识——我们甚至不需要梯度下降，只需以“闭式”直接求解最优模型参数——你可以看看我关于经典统计方法线性回归的第一门 Udemy 课程：

[数据科学：Python 线性回归](https://www.udemy.com/data-science-linear-regression-in-python)

[`www.udemy.com/data-science-linear-regression-in-python`](https://www.udemy.com/data-science-linear-regression-in-python)

### 自然语言处理（NLP）

如果你对机器学习如何应用于语言、文本和语音感兴趣，你会想看看我的自然语言处理（NLP）课程：

[数据科学：Python 自然语言处理](https://www.udemy.com/data-science-natural-language-processing-in-python)

[`www.udemy.com/data-science-natural-language-processing-in-python`](https://www.udemy.com/data-science-natural-language-processing-in-python)

### 面向营销人员的 SQL

如果你有兴趣学习 SQL（结构化查询语言）——一种可应用于小至你 iPhone 中的数据库、大至跨越多个大陆的数据库的语言——不仅学习语言机制，还能知道如何将其应用于真实世界的数据分析和营销问题？请看这里：

[面向营销人员的 SQL：掌握数据分析、数据科学与大数据](https://www.udemy.com/sql-for-marketers-data-analytics-data-science-big-data)

[`www.udemy.com/sql-for-marketers-data-analytics-data-science-big-data`](https://www.udemy.com/sql-for-marketers-data-analytics-data-science-big-data)

### 免费优惠券与赠品通知渠道

最后，我经常发放优惠券并告知何时可以免费获取我的课程。但前提是你必须是我的现有学生！以下是我通知学生优惠券和免费赠品的一些方式：

- **我的通讯**，你可以在 [`lazyprogrammer.me`](http://lazyprogrammer.me) 注册（附赠免费的 6 周机器学习入门课程）
- **我的 Twitter**：[`twitter.com/lazy_scientist`](https://twitter.com/lazy_scientist)
- **我的 Facebook 主页**：[`facebook.com/lazyprogrammer.me`](https://facebook.com/lazyprogrammer.me)（别忘了点“赞”！）
