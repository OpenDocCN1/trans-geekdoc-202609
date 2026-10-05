

# 信息处理

并且基于我们目前拥有的分析数据。

```
davinciSentenceAnalyticsMeasure::quantQ.infth.wordAddAnalytics[
  davinciSentenceAnalyticsAnalytics];
```

输出结果与输入的形式相同，它额外增加了两个单词。通过观察第一句话来确认这一点：

davinciSentenceAnalyticsMeasure

```
"there";"no";"human";"experience";"that";"can";"be";"termed";"true"
science";"unless";"it";"mathematically";"demonstrated";"AVERAGE"
MAX"
1.0212766 0.003278689 0.01923077 0.1428571 0.0625 0.006711409 0.05405405
  0.01904762 0.2 0.08333333 0.0666667 0.166667 0.00468295 1 1
  0.1900154
```

特别是，如果我们提取出刚刚添加的两个额外单词：

(第一个 davinciSentenceAnalyticsMeasure) each ("AVERAGE"; "MAX")

0.1900154 1

我们正在向句子中添加单词。由于我们对包含的指标使用了大写，我们避免了与原文产生混淆。
句子中达到的最大指标值为 1。事实上，我们的参考文本其实很小；它是由一位科学家写的书的一个章节，因此文本中可能使用了许多单词。确实：

```
sum {1=x["MAX"] each davinciSentenceAnalyticsMeasure
```

227

看到 227 句具有唯一单词的句子，而总共有

count davinciSentenceAnalyticsMeasure

260

总共 260 句。单词在句子中的唯一性对我们的文本没有意义。
每句子的平均指标值是我们手头的另一种替代方案。让我们取平均指标高于 0.5 阈值的句子（我们选择了一个处于句子范围中间且数字整齐的值）。以下显示了我们获得了多少句句子：

```
sum {0.5<x["AVERAGE"] each davinciSentenceAnalyticsMeasure
```

3

# 528

# 机器学习

我们选择了三句希望为我们提供有用指标的句子：

daVinciSentenceAnalyticsMeasure where {0.5x["AVERAGE"]} each

daVinciSentenceAnalyticsMeasure

```
(("syllogism";"to";"speak";"doubtfully";"AVERAGE";"MAX")! 0.004 0.1666667
- 0.5426667 1
("sophism";"to";"speak";"confused";"falsehood";"for";"truth";"AVERAGE";
"MAX")! 0.01666667 1 0.03225806 0.333333 0.5051971 1;
("AVERAGE";"MAX")! 1 1f
```

这三个句子具有独特的内容。最后一句实际上是我们的过滤方法的结果。选定的句子有两个。上面的字典没有提供完整的句子，而是将其拆解为单个单词。我们恢复了句子：

daVinci where {0.5x["AVERAGE"]} each daVinciSentenceAnalyticsMeasure

"syllogism to speak doubtfully";"sophism to speak confused forshadow"
- "truth";

这两个句子相当独特。它们听起来像是值得记住的引言。我们读者对所选作者的引言进行自己的分析，并对以下假设建立了统计有效性：即引言可能会增加平均文本样本的平均指标 Ω。

# 27.1.3 tf-idf

在本节中，我们将详细阐述词频测量指标，并引入信息检索中使用的定义妥的指标。该指标被称为词频-逆文档频率，或 tf-idf。它与之前的指标具有相似的基础；它将文档视为“词袋”，其中单词的顺序不起任何作用。它为单词分配重要性，并根据个体单词来评估文档。这意味着“John killed Mary”和“Mary killed John”被认为是相同的，尽管它们带有不同的含义。在最终，确实有一个人被杀死了。这立即给该方法带来了局限性。如果我们想包含句子的含义，我们需要使用更复杂的模型，如深度神经网络。

单词在文档中的重要性由两个部分组成。首先，它与单词在文档中的频率成正比。如果我们写一篇关于某个词的文章，它应该在文中频繁出现。这将使文本变得相关。另一方面，频率本身必须结合语境：该词在整个文档语料库中使用的频率是多少？如果这个词是常见的且存在于许多文档中，我们只需要它在文档中出现几次即可认为它是相关的。另一方面，对于一个在语料库中稀有的术语，出现一次就会使文档变得相关。相对定义通过文档的总数对单词计数进行归一化。最后，对数定义使用对数函数转换发生率。对数的使用在信息分析师非常流行，它可以消除指数律的影响。

在实现方面，我们可以之前实现频率并保持对单词的简单计数。
tf-idf 词的第二部分对应逆文档频率。文档中的单词计数必须通过该词在整个语料库中的频率进行归一化。在上节中，我们使用了跨整个语料库的词频。然而，这可能是误导的。语料库可能包含某些单词过度膨胀的。这种现象可能会发生，例如由于技术错误导致单词频率增加，或者语料库中的文档源于自动生成的扫描。更稳定的归一化指标是语料库中包含给定单词的文档数量。这将代表本章中整体词频更稳定的衡量标准。

我们在所有（我们交替使用文档术语和句子）语料库中定义频率（是的，我们再次使用了这个词并增加了文档的值）：

```
$idf_{corpus}(w) = \log \frac{\sum_{document\in corpus}}{\sum_{document\in corpus}1(w\in document')}$ (27.8)
```

分子对应语料库的大小，而分母是语料库中包含给定单词的文档数。

我们将 IDF 实现如下函数，它接受整个语料库作为字典，并返回一个每个单词 IDF 的字典。这个定义足够详细，应该只执行一次。后续查询应从内存中获取结果。

```
.quantq0 infth.idf:[{corpus}
// 清后的语料库
uniqueWords: distinct "vs" "sv corpus;
// 包含给定单词的文档计数
vals: {{corpus]; sum in "vs y"}[word];each corpus];corpus];
     each uniqueWords;
n// IDF
 :log uniqueWords!(count corpus)%vals;
}
```

示例单词 "there" 的 IDF：

```
.quantq1 infth.idf[daVinci]["there"]
```

2.159484

此外，我们将 tf 和 IDF 两个指标合并为单个函数。tfidfSentence 计算 tf-idf 指标。它接受两个参数。第一个是

