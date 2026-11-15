

## 操作方法...

下面是预处理的步骤：

- 1. 加载所需的包：

```r
load_packages=c("janeaustenr","tidytext","dplyr","stringr","ggplot2","wordcloud","reshape2","igraph","ggraph","widyr","tidyr")
lapply(load_packages, require, character.only = TRUE)
```

- 2. 加载《傲慢与偏见》数据集。line_num 属性类似于书中印刷的行号：

```r
Pride_Prejudice <- data.frame("text" = prideprejudice,
"book" = "Pride and Prejudice",
"line_num" =
1:length(prideprejudice),
stringsAsFactors=F)
```

- 3. 现在，执行分词，将每行一个字符串的格式重构为每行一个词元的格式。在这里，词元可以指单个单词、一组字符、共现词（n-grams）、句子、段落等等。目前，我们将句子分词为单个单词：

```r
Pride_Prejudice <- Pride_Prejudice %>% unnest_tokens(word, text)
```

- 4. 然后，使用停用词移除语料库移除常见词，例如 the、and、for 等等：

```r
data(stop_words)
Pride_Prejudice <- Pride_Prejudice %>% anti_join(stop_words,
by="word")
```

- 5. 提取使用最频繁的文本单词：

```r
most.common <- Pride_Prejudice %>% dplyr::count(word, sort = TRUE)
```

- 6. 可视化出现频率最高的前 10 个单词，如下图所示：

![](img/88a9c35e3059565190fbb6413f1ca217_236_0.png)

前 10 个常用单词

```r
most.common$word <- factor(most.common$word , levels = most.common$word)
ggplot(data=most.common[1:10,], aes(x=word, y=n, fill=word)) +
geom_bar(colour="black", stat="identity")+
xlab("Common Words") + ylab("N Count")+
ggtitle("Top 10 common words")+
guides(fill=FALSE)+
theme(plot.title = element_text(hjust = 0.5))+
theme(text = element_text(size = 10))+
theme(panel.background = element_blank(), panel.grid.major =
element_blank(), panel.grid.minor = element_blank())
```

- 7. 然后，使用 bing 词典提取更高层级的情感（即正面或负面）。

```r
Pride_Prejudice_POS_NEG_sentiment <- Pride_Prejudice %>%
inner_join(get_sentiments("bing"), by="word") %>%
dplyr::count(book, index = line_num %/% 150, sentiment) %>%
spread(sentiment, n, fill = 0) %>% mutate(net_sentiment = positive - negative)
```

- 8. 可视化文本中小段落（每段 150 个单词）的情感，如下图所示：

![](img/88a9c35e3059565190fbb6413f1ca217_237_0.png)

每段 150 个单词的句子中正面和负面单词数量的分布

```r
ggplot(Pride_Prejudice_POS_NEG_sentiment, aes(index,
net_sentiment)) +
geom_col(show.legend = FALSE) +
geom_line(aes(y=mean(net_sentiment)), color="blue") +
xlab("Section (150 words each)") + ylab("Values") +
ggtitle("Net Sentiment (POS - NEG) of Pride and Prejudice") +
theme(plot.title = element_text(hjust = 0.5)) +
theme(text = element_text(size = 10)) +
theme(panel.background = element_blank(), panel.grid.major =
element_blank(), panel.grid.minor = element_blank())
```

- 9. 现在，使用 nrc 词典提取细粒度情感（即正面、负面、愤怒、厌恶、惊讶、信任等等）：

```r
Pride_Prejudice_GRAN_sentiment <- Pride_Prejudice %>%
inner_join(get_sentiments("nrc"), by="word") %>%
dplyr::count(book,
index = line_num %/% 150, sentiment) %>%
spread(sentiment, n, fill = 0)
```

- 10. 可视化不同定义情感之间的变化，如下图所示：

![](img/88a9c35e3059565190fbb6413f1ca217_238_0.png)

不同情感类型之间的变化

```r
ggplot(stack(Pride_Prejudice_GRAN_sentiment[,3:12]), aes(x = ind, y
= values)) +
geom_boxplot()+
xlab("Sentiment types") + ylab("Sections (150 words) of text")+
ggtitle("Variation across different sentiments")+
theme(plot.title = element_text(hjust = 0.5))+
theme(text = element_text(size = 15))+
theme(panel.background = element_blank(), panel.grid.major =
element_blank(),panel.grid.minor = element_blank())
```

- 11. 根据 bing 词典提取出现最频繁的正面和负面单词，并按下图所示进行可视化：

![](img/88a9c35e3059565190fbb6413f1ca217_239_0.png)

小说《傲慢与偏见》中前 10 个正面和负面单词

```r
POS_NEG_word_counts <- Pride_Prejudice %>%
inner_join(get_sentiments("bing"), by="word") %>%
dplyr::count(word, sentiment, sort = TRUE) %>% ungroup()
POS_NEG_word_counts %>% group_by(sentiment) %>% top_n(10) %>%
ungroup() %>% mutate(word = reorder(word, n)) %>% ggplot(aes(word,
n, fill = sentiment)) + geom_col(show.legend = FALSE) +
facet_wrap(~sentiment, scales = "free_y") + ggtitle("Top 10
positive and negative words") + coord_flip() + theme(plot.title =
element_text(hjust = 0.5)) + theme(text = element_text(size = 15)) +
labs(y = NULL, x = NULL) + theme(plot.background =
element_blank(),panel.border = element_rect(linetype = "dashed",
fill = NA))
```

- 12. 生成情感词云，如下图所示：

![](img/88a9c35e3059565190fbb6413f1ca217_240_0.png)

正面和负面单词的词云

```r
Pride_Prejudice %>%
inner_join(get_sentiments("bing"), by = "word") %>%
dplyr::count(word, sentiment, sort = TRUE) %>% acast(word ~
sentiment, value.var = "n", fill = 0) %>% comparison.cloud(colors =
c("red", "green"), max.words = 100,title.size=2, use.r.layout=TRUE,
random.order=TRUE, scale=c(6,0.5))
```

- 13. 现在分析图书各章节的情感：

  - 1. 提取章节，并执行分词：

```r
austen_books_df <-
as.data.frame(austen_books(), stringsAsFactors=F)
austen_books_df$book <- as.character(austen_books_df$book)
Pride_Prejudice_chapters <- austen_books_df %>%
group_by(book) %>% filter(book == "Pride & Prejudice") %>%
mutate(chapter = cumsum(str_detect(text, regex("^chapter
[\\divxl]", ignore_case = TRUE)))) %>% ungroup() %>%
unnest_tokens(word, text)
```

  - 2. 从 bing 词典提取正面和负面单词集：

```r
bingNEG <- get_sentiments("bing") %>%
filter(sentiment == "negative")
bingPOS <- get_sentiments("bing") %>%
filter(sentiment == "positive")
```

  - 3. 获取每个章节的单词计数：

```r
wordcounts <- Pride_Prejudice_chapters %>%
group_by(book, chapter) %>%
dplyr::summarize(words = n())
```

  - 4. 提取正面和负面单词的比例：

```r
POS_NEG_chapter_distribution <- merge (
Pride_Prejudice_chapters %>%
semi_join(bingNEG, by="word") %>%
group_by(book, chapter) %>%
dplyr::summarize(neg_words = n()) %>%
left_join (wordcounts, by = c("book", "chapter")) %>%
mutate(neg_ratio = round(neg_words*100/words,2)) %>%
filter(chapter != 0) %>%
ungroup(),
Pride_Prejudice_chapters %>%
semi_join (bingPOS, by="word") %>%
group_by(book, chapter) %>%
dplyr::summarize(pos_words = n()) %>%
left_join (wordcounts, by = c("book", "chapter")) %>%
mutate(pos_ratio = round(pos_words*100/words,2)) %>%
filter(chapter != 0) %>%
ungroup() )
```

  - 5. 根据正面和负面单词的比例为每个章节生成情感标志：

```r
POS_NEG_chapter_distribution$sentiment_flag <-
ifelse(POS_NEG_chapter_distribution$neg_ratio >
POS_NEG_chapter_distribution$pos_ratio,"NEG","POS")
table (POS_NEG_chapter_distribution$sentiment_flag)
```

### 工作原理...

如前所述，本节使用了简·奥斯汀的著名小说《傲慢与偏见》，详细介绍了数据整理的步骤，以及使用（公开可用）词典提取情感的过程。

步骤 1 和 2 展示了所需 CRAN 包和所需文本的加载。步骤 3 和 4 执行一元分词和停用词移除。步骤 5 和 6 提取并可视化所有 62 个章节中出现频率最高的前 10 个单词。步骤 7 到 12 使用两种广泛使用的词典 bing 和 nrc 演示高层级和细粒度情感。

两个词典都包含一系列被标记为情感的广泛使用的英文单词。在 bing 中，每个单词被标记为一个高层级二元情感（正面或负面），而在 nrc 中，每个单词被标记为一个细粒度多元情感（正面、负面、愤怒、期待、喜悦、恐惧、厌恶、信任、悲伤和惊讶）。

每个 150 个单词长度的句子被标记为一种情感，这在“每段 150 个单词的句子中正面和负面单词数量的分布”图中已展示。在步骤 13 中，使用 bing 词典中正面或负面单词出现次数最多的方式进行逐章情感标记。在 62 个章节中，52 个章节正面词典出现次数更多，10 个章节负面词典出现次数更多。

# 使用 tf-idf 分析文档

在本节中，我们将学习如何定量分析文档。一种简单的方法是查看文档中一元单词的分布及其出现频率，也称为术语频率（tf）。出现频率较高的单词通常倾向于主导文档。

然而，对于 the、is、of 等普遍出现的单词，人们可能会持不同意见。因此，这些单词会被停用词字典移除。除了这些停用词之外，可能还有一些特定单词出现频率高但相关性低。这类单词会使用其逆文档频率（idf）值进行惩罚。在这里，出现频率较高的单词会受到惩罚。

tf-idf 统计量将这两个量相乘结合，并提供衡量每个单词在给定文档（跨多个文档或语料库）中的重要性或相关性的指标。

在本节中，我们将生成图书《傲慢与偏见》各章节的 tf-idf 矩阵。

