
## How to do it...

Here is how we go about preprocessing:

- 1. Load the required packages:

```r
load_packages=c("janeaustenr","tidytext","dplyr","stringr","ggplot2","wordcloud","reshape2","igraph","ggraph","widyr","tidyr")
lapply(load_packages, require, character.only = TRUE)
```

- 2. Load the Pride and Prejudice dataset. The line_num attribute is analogous to the line number printed in the book:

```r
Pride_Prejudice <- data.frame("text" = prideprejudice,
"book" = "Pride and Prejudice",
"line_num" =
1:length(prideprejudice),
stringsAsFactors=F)
```

- 3. Now, perform tokenization to restructure the one-string-per-row format to a one-token-per-row format. Here, the token can refer to a single word, a group of characters, co-occurring words (n-grams), sentences, paragraphs, and so on. Currently, we will tokenize sentence into singular words:

```r
Pride_Prejudice <- Pride_Prejudice %>% unnest_tokens(word, text)
```

- 4. Then, remove the commonly occurring words such as the, and, for, and so on using the stop words removal corpus:

```r
data(stop_words)
Pride_Prejudice <- Pride_Prejudice %>% anti_join(stop_words,
by="word")
```

- 5. Extract the most common textual words used:

```r
most.common <- Pride_Prejudice %>% dplyr::count(word, sort = TRUE)
```

- 6. Visualize the top 10 common occurring words, as shown in the following figure:

![](img/88a9c35e3059565190fbb6413f1ca217_236_0.png)

Top 10 common words

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

- 7. Then, extract sentiments at a higher level (that is positive or negative) using the bing lexicon.

```r
Pride_Prejudice_POS_NEG_sentiment <- Pride_Prejudice %>%
inner_join(get_sentiments("bing"), by="word") %>%
dplyr::count(book, index = line_num %/% 150, sentiment) %>%
spread(sentiment, n, fill = 0) %>% mutate(net_sentiment = positive - negative)
```

- 8. Visualize the sentiments across small sections (150 words) of text, as shown in the following figure:

![](img/88a9c35e3059565190fbb6413f1ca217_237_0.png)

Distribution of the number of positive and negative words across sentences of 150 words each

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

- 9. Now extract sentiments at a granular level (namely positive, negative, anger, disgust, surprise, trust, and so on.) using the nrc lexicon:

```r
Pride_Prejudice_GRAN_sentiment <- Pride_Prejudice %>%
inner_join(get_sentiments("nrc"), by="word") %>%
dplyr::count(book,
index = line_num %/% 150, sentiment) %>%
spread(sentiment, n, fill = 0)
```

- 10. Visualize the variation across different sentiments defined, as shown in the following figure:

![](img/88a9c35e3059565190fbb6413f1ca217_238_0.png)

Variation across different types of sentiments

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

- 11. Extract the most occurring positive and negative words based on the bing lexicon, and visualize them as shown in the following figure:

![](img/88a9c35e3059565190fbb6413f1ca217_239_0.png)

Top 10 positive and negative words in the novel Pride And Prejudice

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

- 12. Generate a sentiment word cloud as shown in the following figure:

![](img/88a9c35e3059565190fbb6413f1ca217_240_0.png)

Word cloud of positive and negative words

```r
Pride_Prejudice %>%
inner_join(get_sentiments("bing"), by = "word") %>%
dplyr::count(word, sentiment, sort = TRUE) %>% acast(word ~
sentiment, value.var = "n", fill = 0) %>% comparison.cloud(colors =
c("red", "green"), max.words = 100,title.size=2, use.r.layout=TRUE,
random.order=TRUE, scale=c(6,0.5))
```

- 13. Now analyze sentiments across the chapters of the book:

  - 1. Extract the chapters, and perform tokenization:

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

  - 2. Extract the set positive and negative words from the bing lexicon:

```r
bingNEG <- get_sentiments("bing") %>%
filter(sentiment == "negative")
bingPOS <- get_sentiments("bing") %>%
filter(sentiment == "positive")
```

  - 3. Get the count of words for each chapter:

```r
wordcounts <- Pride_Prejudice_chapters %>%
group_by(book, chapter) %>%
dplyr::summarize(words = n())
```

  - 4. Extract the ratio of positive and negative words:

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

  - 5. Generate a sentiment flag for each chapter based on the proportion of positive and negative words:

```r
POS_NEG_chapter_distribution$sentiment_flag <-
ifelse(POS_NEG_chapter_distribution$neg_ratio >
POS_NEG_chapter_distribution$pos_ratio,"NEG","POS")
table (POS_NEG_chapter_distribution$sentiment_flag)
```

### How it works...

As mentioned earlier, we have used Jane Austen's famous novel Pride and Prejudice in this section, detailing the steps involved in tidying the data, and extracting sentiments using (publicly) available lexicons.

Steps 1 and 2 show the loading of the required CRAN packages and the required text. Steps 3 and 4 perform unigram tokenization and stop word removal. Steps 5 and 6 extract and visualize the top 10 most occurring words across all the 62 chapters. Steps 7 to 12 demonstrate high and granular-level sentiments using two widely used lexicons bing and nrc.

Both the lexicons contains a list of widely used English words that are tagged to sentiments. In bing, each word is tagged to one of the high level binary sentiments (positive or negative), and in nrc, each word is tagged to one of the granular-level multiple sentiments (positive, negative, anger, anticipation, joy, fear, disgust, trust, sadness, and surprise).

Each 150-word-long sentence is tagged to a sentiment, and the same has been shown in the figure showing the Distribution of number of positive and negative words across sentences of 150 words each. In step 13, chapter-wise sentiment tagging is performed using maximum occurrence of positive or negative words from the bing lexicon. Out of 62 chapters, 52 have more occurrences of positive lexicons, and 10 have more occurrences of negative lexicons.

# Analyzing documents using tf-idf

In this section, we will learn how to analyze documents quantitatively. A simple way is to look at the distribution of unigram words across the document and their frequency of occurrence, also termed as term frequency (tf). The words with higher frequency of occurrence generally tend to dominate the document.

However, one would disagree in case of generally occurring words such as the, is, of, and so on. Hence, these are removed by stop word dictionaries. Apart from these stop words, there might be some specific words that are more frequent with less relevance. Such kinds of words are penalized using their inverse document frequency (idf) values. Here, the words with higher frequency of occurrence are penalized.

The statistic tf-idf combines these two quantities (by multiplication) and provides a measure of importance or relevance of each word for a given document across multiple documents (or a corpus).

In this section, we will generate a tf-idf matrix across chapters of the book Pride and Prejudice.
