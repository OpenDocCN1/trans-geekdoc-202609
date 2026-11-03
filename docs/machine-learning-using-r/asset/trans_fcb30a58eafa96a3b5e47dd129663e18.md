
技术如 feature hashing、word2vec、Glove 都是有助于创建 **词表示** 的算法，该表示减少了词所表示的维度。

我们可能需要一个一百万维的特征向量来表示 `BoW`，然后使用 `BoW` 对每本书进行评分。这可能需要更多的存储内存，同时在建模时变得计算成本高昂。因此，我们可能希望减小构建 `BoWs` 时的词汇表大小。确定我们希望在 `BoWs` 中保留为特征的正确词集变得很重要。以下是用于减小词汇表的一些方法：

1. 从文本数据中删除不需要的词。删除文档中的标点符号，如 ‘,’ ‘,’ 和 ‘://’。这些通常由 `tidytext` 包中的函数处理。一般来说，我们可以使用 `regex` 来删除标点符号和不需要的词（非上下文词）。
2. 词干提取和词形还原可以将词还原为其词根形式，这也有助于减少 `BoW`。该概念将在后面的章节中讨论。
3. 除了不需要的词之外，还删除英语语法中的冠词、介词和连词，如 ‘the’、‘of’、‘to’、‘an’、‘a’ 和 ‘in’。这些被称为停用词。可以通过创建 `stop_words` 词典并从 `BoWs` 中过滤掉这些词来删除停用词。

清理文本数据还有其他几个挑战。除了实施上述概念之外，让我们使用以下章节中的推特数据来了解其他潜在问题及其解决方案。

### 9.7 | Twitter 数据可视化

我们将使用 `covid_twitter_df` 并分析推文。我们希望了解

1. 哪些用户推文最多？
2. 用户总体上在谈论什么？具体用户在谈论什么？
3. 推文的信息来源是什么？我们可以通过提取文本中的 URL 并进行某些预处理来获取此信息。

让我们获取上述问题的答案。

#### 9.7.1 谁是推文最多的用户？

我们可以根据用户的 `screenName` 获取此信息。这相对直接。然而，对此查询可以得到两个不同的答案——一个包含转发，另一个排除转发。让我们绘制推文最多的用户（包含转发）。让我们绘制按推文数量排序的前 40 名用户。**[表 9.10](#17_Chapter09.xhtml#tab9.10)** 显示了六个用户的快照。数据可以使用 `ggplot` 包中的简单条形图（`geom_bar` 或 `geom_col`）表示。然而，我们使用的是 `ggplot` 包中的点图（`geom_point`）和线段图（`geom_segment`）的组合。这有助于构建一种称为棒棒糖图的精美图表。

**表 9.10** | 新冠疫情中推文数超过 40 的六大推文者

| `screenName` || `n` |
| --- | --- |
| ROBRAIPUR || 336 |
| --- | --- |
| PIBRaipur || 303 |
| NACOINDIA || 298 |
| BSDhruw2 || 293 |
| COVIDNewsByMIB || 255 |
| PIBKolkata || 253 |

![](images/page357-01.png)

从 **[图 9.5](#17_Chapter09.xhtml#fig9.5)** 可以看出，区域外联局（ROB）赖布尔、新闻信息局（PIB）赖布尔和实地外联局（FOB）比拉斯布尔（BSDhruw2）似乎非常活跃。

![](images/page357-02.png)![](images/page358-01.png)

国家艾滋病控制组织似乎也在积极就此话题发推。名为 kjayesh、vinyksr 和 VasGiri 的个人也很活跃。

让我们绘制至少有 100 条推文/转发的顶级用户。由于数据是根据推文数量排序的，**[图 9.6](#17_Chapter09.xhtml#fig9.6)** 将包含来自 **[图 9.5](#17_Chapter09.xhtml#fig9.5)** 的用户子集。

![](images/page358-02.png)

如果排除转发，活跃用户是谁？让我们绘制按推文数量排序的前 40 名用户。

![](images/page358-03.png)![](images/page359-01.png)

我们可以将 **[图 9.7](#17_Chapter09.xhtml#fig9.7)** 与 **[图 9.5](#17_Chapter09.xhtml#fig9.5)** 进行比较，可以看出 COVIDNewsByMIB 的转发并不多，但它正在积极发推。有趣的是，kjayeshb 似乎更积极转发而不是发推。让我们弄清楚这是否正确。**[表 9.11](#17_Chapter09.xhtml#tab9.11)** 显示了该用户的推文，它们大多似乎是转发，其中只提到了推特账号。在文本处理时，此类推文将被删除，因为它们不包含任何文本信息。

![](images/page359-02.png)

**表 9.11** | 用户 kjayeshb 的前六条推文

| `Text` || `screenName` |
| --- | --- |
| @COVIDNewsByMIB @FinMinIndia @MoHFW_INDIA @drharshvardhan @PrakashJavdekar @PIBHomeAffairs @ PIB_India @DDNewslive… [https://t.co/n1EHgJYGdL](https://t.co/n1EHgJYGdL) || kjayeshb |
| --- | --- |
| @COVIDNewsByMIB @FinMinIndia @MoHFW_INDIA @drharshvardhan @PrakashJavdekar @PIBHomeAffairs @ PIB_India @DDNewslive… [https://t.co/Tmhvas2TPN](https://t.co/Tmhvas2TPN) || kjayeshb |
| @COVIDNewsByMIB @FinMinIndia @MoHFW_INDIA @drharshvardhan @PrakashJavdekar @PIBHomeAffairs @ PIB_India @DDNewslive… [https://t.co/3I0UiT1c81](https://t.co/3I0UiT1c81) || kjayeshb |
| @COVIDNewsByMIB @ICMRDELHI @MoHFW_INDIA @AyushmanNHA @drharshvardhan @DDNewslive @ airnewsalerts @PIB_India… [https://t.co/5X0GTppdmG](https://t.co/5X0GTppdmG) || kjayeshb |
| @COVIDNewsByMIB @ICMRDELHI @MoHFW_INDIA @AyushmanNHA @drharshvardhan @DDNewslive @ airnewsalerts @PIB_India… [https://t.co/DJK9lodqUM](https://t.co/DJK9lodqUM) || kjayeshb |
| @MoHFW_INDIA @PMOIndia @drharshvardhan @AshwiniKChoubey @PIB_India @CovidIndiaSeva @COVID-NewsByMIB @mygovindia… [https://t.co/rA6dnhfEsc](https://t.co/rA6dnhfEsc) || kjayeshb |

![](images/page360-01.png)

在 **[表 9.12](#17_Chapter09.xhtml#tab9.12)** 中，我们看到另一方面 IndiaCovid19Bot 正在提供活跃病例和康复病例的每小时统计数据。这些文本数据还包含大量表情符号。在所进行的分析背景下，我们不需要数字、表情符号等，因此我们将使用 `regex` 删除此类词。

![](images/page360-02.png)![](images/page360-03.png)

#### 9.7.2 人们在谈论什么

回答此查询需要创建在 [第 9.6.1 节](#17_Chapter09.xhtml#sec9.6.1) 中讨论的 `BoW` 数据。我们将使用 `covid_twitter_df` 创建 `BoW`。我们将使用 `tidytext`/`tokenizer` 包中的 `unnest_tokens` 函数来拆分文档的词。这些拆分后的词可以称为 tokens。因此，token 是文本的单位，例如词，我们希望在分析中使用。分词是将文档/文本拆分为 tokens 的过程。`unnest_token()` 要求将以下函数作为参数传递：

1. `output` – 存储分词后输出的列名。
2. `input` – 要拆分的输入列名。在此示例中，它是 `covid_twitter_df` 中名为 ‘`text`’ 的列。
3. `format` – 要拆分的文档格式。默认是文本文档。这也支持 ‘HTML’、‘XML’ 和 ‘latex’ 格式的拆分。
4. `token` – 分词的单位。默认是 ‘`word`’，意味着用每个词拆分文档。

可以传递的其他值如下：

> “`characters`”、“`character shingles`”、“`ngrams`”、“`skip ngrams`”、“`sentences`”、“`lines`”、“`paragraphs`”、“`regex`”、“`tweets`”（按词分词但保留用户名、hashtags 和 URL），以及 “`ptb`”（宾夕法尼亚树库）。

我们将 `token` 用作 ‘`tweets`’ 来按词拆分，但仍保留用户名、hashtags 和 URL。我们还将使用 `strip_url` 参数进一步删除作为 tokens 创建的 URL。默认情况下，每个词单独作为一个 token。然而，tokens 也可以是词的组合，然后称为 n-gram token，其中 `n` 是组合中出现的词数。
