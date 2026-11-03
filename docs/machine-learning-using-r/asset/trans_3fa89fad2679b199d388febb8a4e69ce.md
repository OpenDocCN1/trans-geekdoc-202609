
**2.** 对 `tweet_sentiment_df` 执行 `inner_join` 与 `nrc_sad` 并统计反映悲伤情绪的词。

下面代码将用于应用上述步骤。

![](images/page398-02.png)

`tweet_sad` 的维度表明只有 41 个词与 `nrc` 词表中的悲伤情绪相匹配。

![](images/page398-03.png)

**[表 9.42](#17_Chapter09.xhtml#tab9.42)** 显示前 10 个词。

![](images/page398-04.png)![](images/page398-05.png)

### 预建词典
`Pre-built dictionaries` 可以显著减少执行情感分析时对数据标注的人工干预。通过 `tidytext` 和 `textdata` 包提供的词典如 `Afinn`、`Bing`、`Nrc`，可用于理解文本信息中表达的情感。

**表 9.43** | 来自修改后停用词词表的首次 10 条观测

| 词 || 词表 |
| --- | --- |
| music || custom |
| --- | --- |
| feeling || custom |
| lowest || custom |
| a || SMART |
| a’s || SMART |
| able || SMART |
| about || SMART |
| above || SMART |
| according || SMART |
| accordingly || SMART |

使用 `nrc` 词表，我们可以分析文本中由词定义的任何情感商数。我们鼓励读者更改上述代码片段以尝试 ‘anger’、surprise’ 和 ‘positive’ 等情绪。从 **[表 9.42](#17_Chapter09.xhtml#tab9.42)** 中，我们可以看到在推文中反映悲伤情绪的用户（`screenName`）。

**1.** 诸如 negative、evil、lowest、accident、hospital 等词出现在推文中并反映悲伤情绪。

**2.** 我们还看到诸如 music、feeling、lowest 等词出现在推文中，在 covid 数据的上下文中这些词可能并非悲伤情绪。

处理情绪分类错误的词的一种方法如下：

**1.** 将此类词添加到 `stop_words` 词表中。

**2.** 执行 `anti_join()` 将其从 `unigram` 中移除。

**3.** 再次使用情感词表执行 `inner_join()`。

下面的代码显示了将某些词添加到 `stop_words` 词表中的步骤。**[表 9.43](#17_Chapter09.xhtml#tab9.43)** 显示了来自自定义 `stop_words` 词表的 top 10 条观测。

![](images/page399-01.png)

### 9.8.1 使用词表进行情感分析 – Bing
有时，我们可能有兴趣了解用户推文是否反映总体正面情感或负面情感，而非通过词来理解特定情绪。我们可以使用 `bing` 词表来获取正面或负面情感。需遵循的步骤如下：

**1.** 获取推文中每个词的情感得分（`tweet_sentiment_df`）。这可以通过使用 `bing` 词表进行 `inner_join` 来完成。**[表 9.44](#17_Chapter09.xhtml#tab9.44)** 显示了此步骤的输出。

![](images/page399-02.png)![](images/page400-01.png)![](images/page400-02.png)

**2.** 统计每个用户的正面和负面情感。下面的代码生成了 **[表 9.45](#17_Chapter09.xhtml#tab9.45)** 中显示的输出。

![](images/page400-03.png)

**3.** 从 **[表 9.45](#17_Chapter09.xhtml#tab9.45)** 中，将正面和负面情感计数分离到单独的列中。这可以使用 `spread()` 来完成。然后，计算每个用户的 `overall_sentiment`（正面-负面）。我们可以使用 `mutate()` 来实现。下面的代码将有助于应用此步骤。

![](images/page400-04.png)![](images/page401-01.png)

**[表 9.46](#17_Chapter09.xhtml#tab9.46)** 显示了上述代码片段得到的前十条观测。

![](images/page401-02.png)

尽管原始数据框 `tweet_sentiment_df` 有 45 个用户，`tweet_sentiment_bing` 仅显示 42 个唯一用户。可能剩余三位用户的推文中使用的词与 `bing` 词表中的任何词都不匹配。**[表 9.46](#17_Chapter09.xhtml#tab9.46)** 中的 `overall_sentiment` 列是用户在其推文中使用的正面词和负面词之间的差值。

**1.** `overall_sentiment` 的正值意味着推文表达了正面情感。

**2.** 计数为零意味着推文为中性。

**3.** 负值意味着推文表达了负面情感。

让我们绘制整体情感。

![](images/page401-03.png)![](images/page402-01.png)

从 **[图 9.20](#17_Chapter09.xhtml#fig9.20)** 可以看出，大多数政府的官方 twitter 账号反映出正面情感。这些账号使用的词可能更多是疫情期间需要遵循的预防措施、指南和补救措施，因此它们可能被标记为正面情感。有趣的是，`tb9gujarati`、`LogicalIndians` 的推文被标记为反映负面情感的推文。

让我们生成词云以了解推文中反映正面和负面情感的词。这可以通过以下步骤完成：

**1.** 对 `tweet_sentiment_df` 与 `bing` 词表执行 `inner join`。

**2.** 使用 `count()` 函数统计词和情感。

![](images/page403-01.png)

**[表 9.47](#17_Chapter09.xhtml#tab9.47)** 显示了上述步骤的结果。

![](images/page403-02.png)

我们可以使用 `wordcloud` 包中的 `comparison.cloud()` 来可视化来自 **[表 9.47](#17_Chapter09.xhtml#tab9.47)** 的正面和负面词。然而，该函数需要一个词频矩阵作为输入，其行代表词，其列代表文档（正面和负面词的计数）。为了将 `sentiment_word_cloud` 转换为 `term.matrix`，我们将使用 reshape 包中的 `acast`/`dcast` 方法。`acast()` 与 `tidyr` 中的 `spread()` 函数类似，但也可以处理矩阵/数组（而 `spread` 不能）。**[表 9.48](#17_Chapter09.xhtml#tab9.48)** 显示了使用 `acast()` 后的结果。

![](images/page403-03.png)![](images/page403-04.png)

在上面的代码片段中，`~` 左侧的参数，即 `word`，指的是 ID 变量，而 `~` 右侧的参数（`sentiment`）指的是要展开为列名的变量。要展开的值在变量 `n` 中（value.var=`"n"`）。现在我们可以使用 `comparison.cloud()` 来可视化正面和负面词。

![](images/page404-01.png)

**[图 9.21](#17_Chapter09.xhtml#fig9.21)** 显示了推文中使用的负面词以黑色字体显示（上半部分）以及正面词以灰色字体显示（下半部分 **[图 9.21](#17_Chapter09.xhtml#fig9.21)** 的下半部分）。推文中词的频率越高，文本大小越大。`Decline` 在 covid 数据的上下文中可能不是一个负面词，但由于英语中该词的一般用法，它被显示为负面词。

### 9.8.2 情感 – Bing vs. Nrc vs. Affin
在所有可用的词表中，我们如何决定使用哪一个进行情感分析？我们可以使用全部三种来比较结果。最终的选择可能在验证三个词表的情感得分不同后进行。下面的代码块使用了上一节中的 `bing` 词表。**[表 9.49](#17_Chapter09.xhtml#tab9.49)** 显示了使用 `bing` 的情感得分。

![](images/page404-02.png)

**表 9.49** | 使用 Bing 的前 10 位用户及其情感得分

| 用户名 || Bing情感得分 |
| --- | --- |
| arupwharton || 0 |
| --- | --- |
| CovidPlasmaIn || 1 |
| DistrictAdm_FBD || 0 |
| Drmubl || 2 |
| Esichq || −1 |
| FOBKeonjhar || 2 |
| FOBSrinagar || 6 |
| FOBUdhampur || 8 |
| HealthwireMedia || 4 |
| IndBloodDonors || 2 |

*注意：* 正值反映正面情感，负值反映负面情感，零值反映中性情感。

![](images/page405-01.png)
