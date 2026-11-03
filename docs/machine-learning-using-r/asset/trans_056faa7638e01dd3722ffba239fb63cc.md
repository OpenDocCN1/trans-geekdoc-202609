
默认情况下，`unnest_tokens()` 会将词元转换为小写并去掉标点符号。我们可以使用 `to_lower` 和 `strip_punct` 参数来更改默认行为。

## 清理推文

在使用 `unnest_tokens()` 拆分数据之前，让我们了解一些需要处理的问题。我们将使用下面的文本来突出本节讨论的所有问题并依次修复它们。

![](images/page361-01.png)

**1.** 推特数据的其中一个问题是大多数推文会包含推特账号。我们使用 #IndiaFightsCorona、@COVIDNewsByMIB、@covid19indiaorg、@ COVID19_INDIA 来抓取推文。因此，推文会大量包含这些词，但不会携带太多信息。下面的正则表达式处理以‘#’或‘@’开头的词。我们将从推文中删除此类词。

正则表达式完美地完成了工作。

![](images/page362-01.png)

**2.** 推文中的 URL 在分析中可能不需要，这样的 URL 和不需要的词也需要删除。下面的正则表达式处理 URL 并将其删除。

![](images/page362-02.png)

**3.** 有些词可能不是 hashtags 和 URL，但仍在分析中可能没有太多意义。我们在文本数据中也不需要数字和标点符号。让我们创建一个表达式来删除此类词。我们可能无法提前识别所有信息量较小的词。可能需要多次迭代才能识别并删除信息量较小的词。

![](images/page362-03.png)

大部分表达式之前已讨论过，但让我们来看一下正则表达式“COVID(-?19)?”：

![](images/page362-04.png)

我们将同时对文本应用这三个正则表达式并查看结果。

![](images/page363-01.png)

上述输出显示，在应用所有正则表达式后，我们已修复了文本数据中的一些问题。然而，我们仍然在上述输出中发现一些 unicode 文本。该 unicode 对应于 emoji ![](images/pageIn_ch9-02.png)和 ![](images/pageIn_ch9-03.png)。我们还看到一些其他语言的文本。我们也将处理这两个问题。

**4.** 推特数据或一般社交媒体数据的一个主要问题是使用字形/表情符号，例如，![](images/pageIn_ch9-04.png)，等。这些被称为 Unicode 字符。Unicode 是一个字符集，旨在定义所有语言中的所有字符和字形（图形表示）。根据分析目的，我们可能希望保留数据中的字形，也可能不希望保留。要删除字形，我们可以在正则表达式中使用 Unicode，如下所示：

![](images/page363-02.png)

\\p 用于匹配表情符号。其后的字符表示表情符号所属的类别。Emoji 属于类 ‘Other_Symbol’ (So) 和 ‘Unassigned’ (Cn) 类。‘Math_Symbol’ (Sm) 和 ‘Currency_Symbol’ (Sc) 有时也可能需要。上述正则表达式中的最后一个表达式是为了处理未被 \\p{xx} 字符类处理的 emoji。例如，![](images/pageIn_ch9-05.png)(方括号内的问号) 的编码为 ‘\\U0001f3fd’，但未被 \\p{xx} 删除。为了删除此类特殊字符，我们可以使用由 \[\\U{1F000}-\\U{1FFFF}\] 给出的 Unicode 字符范围。- ..

**5.** 就用户书写文本的方式而言，Twitter 数据很混乱。我们总会在推文中看到语言混杂。在处理英语时，我们可能需要删除非英语的词。我们可以通过使用如下正则表达式来实现：

![](images/page363-03.png)

在 ‘`remove_non_english_regex`’ 中，表达式 “\[∧\\x01-\\x7F\] +”，匹配 ASCII 字符集（0-127，即 0x0 到 0x7F）。在 Unicode 中，相同的表达式将写为 “\[∧\\u0000-\\u007F\]+”。该表达式不仅可以删除非英语词，还有助于删除特殊/不可见字符和表情符号。因此，第 4 步也可能是多余的。

**6.** 词 ‘RT’ 也会出现在大多数推文中，表示它是转推。我们将使用 `dplyr` 和 `stringr` 中的 `filter()` 和 `str_detect()` 函数过滤掉转推。

**7.** 我们将使用 `tidytext` 包中内置的英语语法 BoW/词表，通过使用 `anti_join()` 来删除这些词。`anti_join()` 返回推文中在 `stop_words` 中没有匹配项的所有行。

上述七个步骤中使用的正则表达式可能需要根据分析的文本数据进行修改。让我们考虑上述七个步骤并使用 `unnest_token()` 对 `covid_twitter_df` 中的文本列进行拆分。**[表 9.13](#17_Chapter09.xhtml#tab9.13)** 显示了结果表中十个观察值。

![](images/page364-01.png)![](images/page364-02.png)![](images/page365-01.png)

词汇表包含 4,444 个词。请注意，如果在创建词元之前不应用正则表达式，词汇表将有 7,825 个唯一词。因此，它将创建一个长度为 7,825 的向量并消耗更多内存。

## 9.7.3 可视化 – 单词/词

让我们尝试了解语料库中使用的高频词是什么？**[表 9.14](#17_Chapter09.xhtml#tab9.14)** 显示了出现次数最多的前六个词。**[图 9.8](#17_Chapter09.xhtml#fig9.8)** 显示了数据的图表。

![](images/page365-02.png)

**表 9.14** | 高频词

| Word || *n* |
| --- | --- |
| Follow || 316 |
| --- | --- |
| Active || 300 |
| Mask || 261 |
| deaths || 243 |
| Hands || 230 |
| swachhbharat || 228 |

我们将绘制 `word_tokens` 中词元计数超过 40 的前 50 个词。此数据切片是通过从 `dplyr` 包中应用 `filter()` 然后 `slice_max()` 从 ‘word_tokens’ 中提取的。此外，在绘制数据时，我们将以正向显示频率计数 100+，以反向显示频率计数小于 100。这是通过将 `geom_segment` 的 `y` 参数设置为 100 来实现的。**[图 9.8](#17_Chapter09.xhtml#fig9.8)** 显示了数据的图表。

![](images/page365-03.png)![](images/page366-01.png)

在上面的代码片段中，`filter()` 函数是多余的，因为使用 `slice_max()` 提取的前 50 个词的计数都超过了 40。然而，这对于任何其他数据集可能不成立。从 **[图 9.8](#17_Chapter09.xhtml#fig9.8)** 中，我们可以得出结论

**1.** 使用 words like mask, wear, hands, wash, social, distancing, clean, don’t, etc. 表明人们对卫生的普遍认知。

**2.** 人们似乎在大量谈论 swachh bharat、PM (prime minister)。

**3.** 人们在谈论 deaths 和 recovery。推文中这些词的使用可能反映了人们在应对 COVID-19 时普遍的担忧情绪和谨慎态度。

**[图 9.9](#17_Chapter09.xhtml#fig9.9)** 显示了词元中计数为 40 及以上的最后 50 个词的图表。

![](images/page367-01.png)![](images/page367-02.png)

迄今为止我们看到的图表基于 BoW (`twitter_words`) 中词的简单计数。然而，我们也可以按每个用户 (`screenName`) 统计词的计数。在这里，`screenName` 可以被视为一个文档（在 [第 9.6.1 节](#17_Chapter09.xhtml#sec9.6.1) 中讨论），我们希望通过它来获取计数。让我们获取拥有多个推文（推文总词数超过 100）的用户 (`screenName`) 并了解他们使用的词。数据可以通过以下步骤准备：

**1.** 使用 `twitter_words` 数据框：
– 选择 `screenName` 和 `word` 列并使用 `count()` 获取所有词的计数。
– 使用 `group_by()` 按 `screenName` 分组数据。
– 创建一个存储用户所写总词数的列。这可以通过 `mutate()` 实现。
– 过滤总词数超过 100 的推文。使用 `filter()` 函数实现此操作。
– 使用 `slice_max()` 从每个用户中选择前七条记录。
– 使用 `ungroup()` 对数据取消分组。
– 使用 `arrange()` 按 `screenName` 和词计数排列数据。

