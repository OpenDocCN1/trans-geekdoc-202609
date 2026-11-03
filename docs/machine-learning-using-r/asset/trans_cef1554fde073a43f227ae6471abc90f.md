
表 9.33 中的短网址可以使用下面的代码片段进行展开。表 9.34 显示了展开后的网址。

![](images/page393-02.png)

表 9.34 | 展开 URL 的前六个观测值

| `url` || `status_code` |
| --- | --- |
| [https://twitter.com/MoHFW_INDIA/status/1316278631321100289/photo/1](https://twitter.com/MoHFW_INDIA/status/1316278631321100289/photo/1) || 400 |
| --- | --- |
| [https://twitter.com/mygovindia/status/1316602805818257410/photo/1](https://twitter.com/mygovindia/status/1316602805818257410/photo/1) || 400 |
| [https://twitter.com/mygovindia/status/1315610983793008640/photo/1](https://twitter.com/mygovindia/status/1315610983793008640/photo/1) || 400 |
| [https://twitter.com/mygovindia/status/1315616867776491520/photo/1](https://twitter.com/mygovindia/status/1315616867776491520/photo/1) || 400 |
| [https://twitter.com/mygovindia/status/1316596832928055297/photo/1](https://twitter.com/mygovindia/status/1316596832928055297/photo/1) || 400 |
| [https://twitter.com/MoHFW_INDIA/status/1317424639295909888/photo/1](https://twitter.com/MoHFW_INDIA/status/1317424639295909888/photo/1) || 400 |

让我们将 URL 链接与短网址绑定。表 9.35 显示了短网址和对应的 URL 链接。

![](images/page394-01.png)

我们将从 URL 链接中提取域名并统计域名。前面章节中解释的 `gsub()` 和 `regex` 的使用将被用来提取 URL 链接。表 9.36 显示了域名及其出现的次数。

![](images/page394-02.png)

### 9.7.10 可视化 URL

图 9.19 使用 `ggplot` 显示了推文中常见域名的图表。

![](images/page394-03.png)![](images/page394-04.png)

表 9.36 | 域名计数

| `domain` || `domain_count` |
| --- | --- |
| twitter.com || 448 |
| --- | --- |
| pledge.mygov.in || 24 |
| livemint.com || 16 |
| blog.mygov.in || 8 |

![](images/page395-01.png)

图 9.19 显示在大多数情况下，推文的信息链接到 Twitter 源本身。我们可能还想了解用户在转发时使用的 hashtags。我们留给读者自行尝试。

## 9.8 情感分析

在创建了 `BoW` 模型并理解了基本的词嵌入之后，让我们深入探讨文本分析中另一个感兴趣的话题。用户对特定主题的情感备受关注。在本例中，我们想了解用户对与 COVID-19 相关主题的情绪。通过人工阅读，可以阅读推文并了解用户反映的情绪。它可能是一条正面/负面推文或快乐/中性/悲伤推文等。但对于人类来说，阅读所有推文并标记推文以反映情感意图将是令人难以承受的。

`tidytext` 附带内置词典（可通过 `textdata` 包获得），可帮助将推文分类为预定义的情感标签之一。`tidytext` 中的四个通用词典如下：

1. `Afinn` – 该词典来自 Finn Årup Nielsen（Nielsen, 2011），将 2,477 个唯一的 unigram 按 −5（负面情感）到 5（正面情感）的分数进行分类。它采用开放数据库许可（ODbL）v1.0 许可。表 9.37 显示了 afinn 词典中的六个观测值。

![](images/page395-02.png)

表 9.37 | afinn 词典中的前六个观测值

| `Word` || `value` |
| --- | --- |
| Abandon || −2 |
| --- | --- |
| Abandoned || −2 |
| abandons || −2 |
| abducted || −2 |
| abducted || −2 |
| abducted || −2 |

表 9.38 | nrc 词典中的前六个词

| `Word` || `sentiment` |
| --- | --- |
| abacus || trust |
| --- | --- |
| abandon || fear |
| abandon || negative |
| abandon || sadness |
| abandoned || anger |
| abandoned || fear |

1. `Nrc` – 该词典来自 Saif Mohammad 和 Peter Turney（2013），将词语归类到 ‘trust’、‘fear’、‘negative’、‘sadness’、‘anger’、‘surprise’、‘positive’、‘disgust’、‘joy’ 和 ‘anticipation’ 等标签下。它是最全面的，已将 6,468 个 unigram 归类到这些标签下。一个词可以映射到多个标签。该数据集需要商业使用许可。表 9.38 显示了 nrc 词典中的六个观测值。

![](images/page396-01.png)

2. `Bing` – 该词典来自 Bing Liu（2015）及其合作者，以二元方式对词语进行分类，即 positive/negative，即两个唯一标签。它已将 6,783 个 unigram 归类到这些标签下。默认情况下，只有该词典作为 `tidytext` 的一部分可用。表 9.39 显示了 bing 词典的六个观测值（S Biguzzi, 2020）。

![](images/page396-02.png)

3. `lougharn` – 该词典来自 Loughran-McDonald（2019），将词语归类到 ‘negative’、‘positive’、‘uncertainty’、‘litigious’、‘constraining’ 和 ‘superfluous’ 等标签下。该词典已将 3,917 个英语单词归类到这些情感意图下。词语可能映射到多个标签下。该词典需要商业使用许可。表 9.40 显示了 lougharn 词典的六个观测值。

![](images/page396-03.png)

我们需要安装 `textdata` 包以访问 ‘afinn’、‘nrc’ 和 ‘lougharn’ 词典。`get_sentiments()` 函数内部使用 `textdata::lexicon_afinn()`、`textdata::lexicon_nrc()`、`textdata::lexicon_loughran()` 下载这些词典并使其可用。上述所有词典均由词典作者使用众包平台构建和验证。使用这些词典的优点是我们能快速从语料中得出情感。缺点是如果语料的写作风格非常不同（例如，一本 100 年前的书，我们使用上述词典来判断书中表达的情感），情感的准确性可能值得怀疑。

表 9.39 | bing 词典中的前六个词

| `Word` || `sentiment` |
| --- | --- |
| 2-faces || negative |
| --- | --- |
| abnormal || negative |
| abolish || negative |
| abominable || negative |
| abominably || negative |
| abominate || negative |

表 9.40 | lougharn 词典中的前六个词

| `Word` || `sentiment` |
| --- | --- |
| abandon || negative |
| --- | --- |
| abandoned || negative |
| abandoning || negative |
| abandonment || negative |
| abandonments || negative |
| abandons || negative |

这些词典基于 unigram，因此情感处于 unigram 层级。推文（表示为 `BoW`）的情感可以通过组合 unigram 的情感得出。我们将使用 ‘nrc’ 词典对 covid 数据进行情感分析。我们将了解用户（`screenName`）表达的情感，这些用户多次发布推文，每条推文 50 到 100 个词。来自 [第 9.7.3 节](#17_Chapter09.xhtml#sec9.7.3) 的 ‘`twitter_word_count`’ 对象包含使用 `unnest_token()` 创建的 unigram。表 9.41 显示了推文词数在 50 到 100 之间的用户的前 20 行。

![](images/page397-01.png)![](images/page397-02.png)

推文情感 df 中有 45 个唯一用户。

![](images/page398-01.png)

让我们获取用户的情绪。`nrc` 词典中的标签如下：‘trust’、‘fear’、‘negative’、‘sadness’、‘anger’、‘surprise’、‘positive’、‘disgust’、‘joy’ 和 ‘anticipation’。让我们查看反映 ‘sadness’ 的推文，我们将按照以下步骤进行：

1. 从 ‘nrc’ 词典中获取反映 sadness 的词语并将其存储在变量 ‘`nrc_sad`’ 中。
