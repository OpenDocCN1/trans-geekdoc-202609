

我们的目标是，至少在视觉上，确定先前评论的情感。让我们先快速汇总一下词频：

```
library(ggplot2)
text_df %>%
  count(word, sort=T) %>%
  mutate(word = reorder(word, n)) %>%
  ggplot(aes(word, n)) +
  geom_col() +
  xlab(NULL) +
  coord_flip() +
  theme_bw()
```

我们得到一个漂亮的柱状图，如下所示：

![](img/da8fb67f2acf661518076e08b6ffd9b9_203_0.png)

我们玩具评论数据集中的基本词频统计

tidytext 包包含三个按情感标注的词汇表（词语集合）：

- 来自 Finn Årup Nielsen 的 AFINN (http://www2.imm.dtu.dk/pubdb/views/publication_details.php?id=6010)
- 来自 Bing Liu 和合作者的 bing (https://www.cs.uic.edu/~liub/FBS/sentiment-analysis.html)
- 来自 Saif Mohammad 和 Peter Turney 的 nrc (http://saifmohammad.com/WebPages/NRC-Emotion-Lexicon.htm)

AFINN 词汇表为英语中常见词汇赋予 -5 到 5 之间的数值，负值表示负面词汇。例如：

```
get_sentiments("afinn") %>%
  filter(score==-5) %>%
  head
```

结果如下（敏感读者请跳过下一段代码）：

```
# A tibble: 6 x 2
  word score
  <chr> <int>
1 bastard   -5
2 bastards  -5
```

而，下面的代码：

```
get_sentiments("afinn") %>%
  filter(score==0) %>%
  head
```

结果简单如下：

```
# A tibble: 1 x 2
  word score
  <chr> <int>
1 some kind   0
```

还有下面的代码：

```
get_sentiments("afinn") %>%
  filter(score == 5) %>%
  head
```

### 返回结果：

```
# A tibble: 5 x 2
  word score
  <chr> <int>
1 breathtaking 5
2 hurrah 5
3 outstanding 5
4 superb 5
5 thrilled 5
```

## bing 词汇表仅包含正面和负面词汇：

```
> get_sentiments("bing") %>% head
# A tibble: 6 x 2
  word sentiment
  <chr> <chr>
1 2-faced negative
2 2-faces negative
3 a+ positive
4 abnormal negative
5 abolish negative
6 abominable negative
```

## 而，nrc 具有不同的类别：

```
> get_sentiments("nrc") %>% head
# A tibble: 6 x 2
  word sentiment
  <chr> <chr>
1 abacus trust
2 abandon fear
3 abandon negative
4 abandon sadness
5 abandoned anger
6 abandoned fear
```

我们该如何使用这些单词列表呢？嗯，一旦数据整齐化，我们就可以将它们连接起来，并创建不同的汇总，以试图了解发生了什么。让我们先将 bing 词汇表存储在某个位置：

```
bing <- get_sentiments("bing")
```

并将其与我们的数据连接：

```
> text_df %>% inner_join(bing) %>% count(line, sentiment)
Joining, by = "word"
# A tibble: 5 x 3
line sentiment n
<int> <chr> <int>
1 1 negative 1
2 2 negative 1
3 3 negative 3
4 3 positive 1
5 4 positive 2
```

不错，但我们总可以通过绘图做得更好：

```
# Plot
text_df %>%
inner_join(bing) %>%
count(line, sentiment) %>%
ggplot(aes(line, n, fill=sentiment))+
geom_col () +
coord_flip ()+
theme_bw ()
```

结果如下所示。不错。我们看到，简单的连接和汇总聚合已经能让我们基本了解如何按情感对评论进行分类：

![](img/da8fb67f2acf661518076e08b6ffd9b9_206_0.png)

这已经很有价值了，但在某些情况下，我们希望知道一条评论有多正面或多负面；例如，为了将问题转交给合适的客服代表。在这种情况下，使用 `AFINN` 词汇表可能会更有用：

```
afinn <- get_sentiments("afinn")
```

现在，我们像之前一样连接评论数据：

```
text_df %>% inner_join(afinn)
```

并查看每条评论的总得分：

```
# Group
text_df %>%
inner_join(afinn) %>%
group_by (line) %>%
summarize (total_score = sum(score))
```

不错；不过，同样，绘图效果更好：

```
# Plot
text_df %>%
inner_join(afinn) %>%
group_by (line) %>%
summarize (total_score = sum(score)) %>%
mutate(sentiment=ifelse(total_score>0,"positive","negative")) %>%
ggplot(aes(line, total_score, fill=sentiment))+%
geom_col() +
coord_flip() +
theme_bw()
```

如下所示：

![](img/da8fb67f2acf661518076e08b6ffd9b9_208_0.png)

使用 AFINN 词汇表的汇总统计

哇，这里发生了什么？情况有点奇怪。首先，请注意一条评论不见了。这是因为第一条评论与 `AFINN` 词汇表没有共同单词（回顾一下，我们使用了内连接）。更令人担忧的是第三条评论的情况。得分为零，这是根据 `AFINN` 词汇表，将评论中每个单词的正负得分相加得来的。然而，请注意，评论 3 主要是正面的。那到底发生了什么？

## 越多越好——计算 n-gram 而非单个词语

前一节出现如此奇怪结果的原因可以追溯到上下文。请注意，评论 3 中有短语 "No nonsense, no gimmicks"，它大体上是正面的，但带有两个负面词汇。我们如何考虑上下文呢？答案是 n-grams。n-gram 是给定文本或语音序列中 n 个连续项（单词，或者在语音的情况下为音素）的序列。让我们通过一个示例来说明，并使用 2-gram（也称 bigram）：

```
text_df <- data_frame(line = 1:4, text = text)
text_df <- text_df %>%
unnest_tokens(bigram, text, token="ngrams", n=2)
text_df
```

这会给我们如下结果：

```
# A tibble: 70 x 2
  line bigram
  <int> <chr>
1 1 the food
2 1 food is
3 1 is typical
4 1 typical czech
5 1 czech and
6 1 and the
7 1 the beer
8 1 beer is
9 1 is good
10 1 good the
# ... with 60 more rows
```

所以，我们现在看到连续单词被组合在一起了。这已经足以帮助我们判断那些实际上是正面意义的负面词的否定情况，就像我们之前提到的评论 3。让我们找出哪些负面词被否定了。首先，我们将 bigram 的两个单词拆分为两列：

```
library(tidyr)
text_df <- text_df %>% separate(bigram, c("w1","w2"), sep=" ")
text_df
```

结果如下：

```
# A tibble: 70 x 3
  line w1  w2
* <int> <chr> <chr>
  1  1 the   food
  2  2 food  is
  3  3 is    typical
  4  1 typical czech
  5  1 czech and
  6  1 and   the
  7  1 the   beer
  8  1 beer  is
  9  1 is    good
 10  1 good  the
# ... with 60 more rows
```

借助 dplyr 的一点神奇操作，我们可以找出句子中有问题的部分：

```
text_df %>%
 filter(w1=="no") %>%
 inner_join(afinn, by=c(w2="word") )
```

结果如下：

```
# A tibble: 1 x 4
 line w1   w2   score
<int> <chr> <chr> <int>
 1     3 no   nonsense -2
```

我们现在可以使用这些信息来覆盖第三条评论的得分。然而，请注意这个过程可能相当复杂。当然，在许多情况下它效果不错，但我们应该寻找更系统的方法来处理上下文。

> n-gram 对于跟踪单词的上下文，并正确地用于分类至关重要。

## 词袋基准

在识别欺诈电子邮件的第 3 章《使用自编码器进行欺诈检测》中，我们接触过 one-hot 词嵌入。其思想是将每个单词表示为基向量；即，除了一个坐标外全为零的向量。因此，每个文档（在这里是一条评论）都表示为由零和一组成的向量。我们在此基础上更进一步，使用了不同的加权方式（tf-idf）。

让我们再次回顾这个模型，但这次使用 n-gram 而不是单个单词。这将是我们后续进行更复杂词嵌入时的基准。

### 准备数据

该数据是 Stanford Large Movie Review 数据集的一个子集，最初发表于：

Andrew L. Maas, Raymond E. Daly, Peter T. Pham, Dan Huang, Andrew Y. Ng, and Christopher Potts. (2011). Learning Word Vectors for Sentiment Analysis. The 49th Annual Meeting of the Association for Computational Linguistics (ACL 2011).

该数据可从 http://ai.stanford.edu/~amaas/data/sentiment/ 下载，前提是给原始论文适当署名。这是原始数据，但你可以在 Kaggle 上找到预处理版本，https://www.kaggle.com/c/word2vec-nlp-tutorial/ data。

让我们先加载数据：

```r
df <- read.csv("./data/labeledTrainData.tsv", encoding = "utf-8", quote = "", sep="\t", stringsAsFactors = F)
text <- df$review
```

我们再次使用 tm 库。请注意，代码略有不同，因为我们将文本加载为 VCorpus 而非之前的 Corpus：

```r
library(tm)
corpus <- VCorpus(VectorSource(text))
inspect(corpus[[1]])
```

