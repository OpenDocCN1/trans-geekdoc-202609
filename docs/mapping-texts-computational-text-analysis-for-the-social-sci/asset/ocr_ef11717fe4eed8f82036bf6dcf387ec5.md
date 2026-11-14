| | x | y |
|---|---|---|
| 1: | care | 1.00 |
| 2: | love | 0.75 |

```
```
text <- "taking care is one way to show your love"
tkens <- strsplit(text, " ") |> unlist()
df_jr |> filter(x %in% tkens)
```
```

Most of the words are not in the dictionary—even with eleven thousand words. This is the out-of-vocabulary (OOV) problem. The typical strategy is to average the weights of the matched words, in this case giving us a sentiment score of 0.875. However, what about the text “I don’t care and I do not love you”? Our match-and-average system would score this as positive when it is the opposite. Therefore, we need to use another dictionary of valence or polarity “shifters” (output in the margin).

```
```
data("hash_valence_shifters", package = "lexicon")
```
```

| | x | y |
|---|---|---|
| 1 | ain't | 1 |
| 2 | absolutely | 2 |
| 3 | almost | 3 |
| 4 | although | 4 |

```
```
hash_valence_shifters |>
  group_by(y) |>
  slice_head(n = 1)
```
```

Instead of weights, though, each word is assigned to one of four categories: (1) negator, (2) amplifier, (3) de-amplifier, or (4) neutral context word. `sentimentr` combines polarity scores and valence shifters to calculate an aggregate sentiment score.

Using the Jinkers-Rocker polarity dictionary with the valence shifters dictionary, we’ll test the emotional polarity of “real” and “fake” news. The original dataset contained roughly 20,000 articles from Reuters, a real news service, and roughly 20,000 articles from a variety of sources deemed fake or unreliable (Ahmed et al. 2017, 2018). We provide a random sample of 1,000 “real” and 1,000 “fake” articles (to speed things up).

```
```
data("corpus_isot_fake_news2k", package = "text2map.corpora")
```
```

Our “rating” variable is a character vector, so let’s also convert it to a numeric 1 (for real) or 0 (for fake).

```
```
df_isot <- corpus_isot_fake_news2k |>
  mutate(rating = ifelse(rating == "real", 1, 0)) |>
  rowid_to_column(var = "element_id")
```
```

Use `get_sentences()` to break each document into sentences (this primarily uses punctuation marks). Next, using `sentimentr`, we’ll calculate the sentence-level sentiment score with our two dictionaries. Finally, we’ll join the output with the original dataframe containing the categorical veracity of the article.

```
```
df_polar <- df_isot$text |> get_sentences() |> sentiment()
df_mod <- left_join(df_polar, df_isot, by = "element_id")
```
```

Since we are predicting a binary outcome (fake or real), we’ll use logistic regression (by setting `family` to “binomial” within `glm()`).20 We’ll use the sentiment scores for each sentence to predict whether it is in an article from a “real” or “fake” news source.

20 See Math Basics.