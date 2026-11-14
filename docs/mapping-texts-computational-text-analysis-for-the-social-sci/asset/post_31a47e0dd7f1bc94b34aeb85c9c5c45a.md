
```r
df_plot <- rbind(df_nixon, df_kennedy) |>
  pivot_longer(cols = c("tf", "rf", "tfidf"),
               names_to = "Weight",
               values_to = "Value") |>
  group_by(President, Weight) |>
  slice_max(Value, n = 10)
```

30 ggarrange() prints plots side by side.

31 There are more advanced methods for finding keywords, such as the TextRank model (Mihalcea and Tarau 2004).

Finally, we'll plot each president separately and select the top ten terms within each weighting variable.30 tf-idf provides more informative words by selecting those most unique to each president. We can think of tf-idf scores as giving us the **keywords** for a document – the set of words best summarizing the purpose or content of that text.31 The tf-idf of Kennedy’s speeches includes “communist,” and “nuclear,” all of which give insight into prescient concerns during his presidency.

```r
plot_nixon <- df_plot |>
  filter(President == "Nixon") |>
  mutate(Term = fct_reorder(Term, Value)) |>
  ggplot(aes(x = Term, y = Value, fill = Weight)) +
  geom_col() +
  facet_wrap(~ Weight, scales = "free", ncol = 1) +
  coord_flip() +
  labs(subtitle = "Top Terms in Nixon’s Addresses")
```

```r
plot_kennedy <- df_plot |>
  filter(President == "Kennedy") |>
  mutate(Term = fct_reorder(Term, Value)) |>
  ggplot(aes(x = Term, y = Value, fill = Weight)) +
  geom_col() +
  facet_wrap(~ Weight, scales = "free", ncol = 1) +
  coord_flip() +
  labs(subtitle = "Top Terms in Kennedy’s Addresses")
```

```r
ggarrange(plot_kennedy, plot_nixon, common.legend = TRUE)
```

## Summary of Weightings

We covered several types of DTMs: term frequency, relative term frequency, binary, and term frequency/inverse document frequency. There are several more weighting schemes, however. Nearly all try to overcome the problem of the non-normal distribution of words. While we won’t go over all of these here, Table 6.2 contains additional weighting schemes that we can explore on our own.

Table 6.2: Selection of DTM Weighting Schemes

| Weighting | Description |
|---|---|
| Term Frequency (TF) | Term's count in a document |
| Relative TF (RF) | Divide TF by total terms in a document |
| Binary or Boolean | Zero cells are 0 (FALSE); otherwise, 1 (TRUE) |
| Document Frequency (DF) | Total documents in which a term occurs |
| Inverse DF (IDF) | Log of the total documents divided by the DF |
| Relative DF | Term's corpus count divided by term's DF |
| TF-IDF | Multiply RF with the IDF |
| Pointwise Mutual Information (PMI) | log2 of TF divided by expected count |
| Positive PMI (PPMI) | Same as PMI, but negative values set to 0 |

## TERM FEATURES

In addition to mapping the meaningful patterns in documents, we often want to summarize ways tokens are used. Broadly, we do this by looking at a token’s **context**. At the simplest, we can consider the “dispersion” or locations of tokens within a text (Carpeña et al. 2009; Ortuño et al. 2002). Not only are some words much more frequent in a corpus, but some words are also much more evenly distributed within documents than others. To see this, let’s create a “lexical dispersion” plot.

The first step is associating a given token with a given location in a document or corpus. Let’s use Star Trek scripts and see how words are dispersed over each episode.

```r
data("corpus_tng_season5", package = "text2map.corpora")
```

Let's pick keywords that occur with roughly the same frequency but have different dispersions. Here, “vulcan” occurs 72 times; “every” occurs 72; “romulan” occurs 78; and “klingon” occurs 84 times in the season.

```r
key_words <- c("vulcan", "romulan", "klingon", "every")
df_token_position <- corpus_tng_season5 |>
  unnest_tokens(word, line) |>
  mutate(position = 1:n()) |>
  filter(word %in% key_words)
```

```r
df_token_position |>
ggplot(aes(x = position, y = 1)) +
  geom_segment(aes(xend = position, yend = 0)) +
  facet_grid(word ~ .) +
  labs(y = NULL, x = "Position") +
  theme(panel.grid.major.y = element_blank(),
        axis.ticks.y = element_blank(),
        axis.text.y = element_blank())
```

In Figure 6.3, we interpret concentrated terms, like “klingon,” as significant to the show’s plot. We can glean that earlier in the season, “vulcan” was important.

- THIS SECTION NEEDS:
  - tidyverse
  - text2map
  - quanteda
  - text2vec
  - tidytext
  - tokenizers
  - Matrix
  - ggraph
  - tidygraph

![](img/ccc0ce559da97114ef913045f55e3801_95_0.png)

Figure 6.3: Lexical Dispersion Plot.

of documents in a corpus, the **TCM** shows how terms are used in a corpus. Here, the rows of the TCM are target words, and columns are **contexts** to which the target term is associated. In the example above, the context is simply a word's position in a string of words. We could also rotate a DTM to get a *term-document matrix*, where the document is the term's context. Finally, in a term co-occurrence matrix, each row is a term, _i_, and each column is also a term, _j_, that _i_ appears alongside. These are all TCMs; their “contexts” vary by scale—as if zooming in and out of a map.32

32 We'll add considerable complexity to TCMs in Extended Inductive.

Term co-occurrence matrices capture two kinds of word _associations_. First, we get **syntagmatic** similarities: two words are literally used together. Second, we get **paradigmatic** associations: two words can be used in similar places but might never co-occur.

Let's explore this with Taylor Swift's songs from her first ten albums. We'll again do minimal preprocessing (lowercase, remove punctuation).

```r
data("corpus_taylor_swift", package = "text2map.corpora")
df_swift <- corpus_taylor_swift |>
  mutate(text = tolower(song$text),
         text = gsub("[:punct:]", " ", text),
         text = trims(text))
```

Then, we'll create a DTM where each row is a song.

```r
dtm <- dtm_builder(df_swift, text, song_id)
dim(dtm) # 120 songs and a vocab of 3240
```

Next, we'll transpose the DTM, which tips and twists it, so the dimensions are flipped.

```r
tdm <- t(dtm) # transpose the dtm to get a tdm
dim(tdm) # A vocab of 3240 and 120 songs
```

In this TCM, the features summarizing each token are the songs in which they occur and do not occur. With a feature matrix like this, we can compare how associated any two terms are by comparing their vectors (i.e., their respective rows in the TCM). There are many methods to measuring similarity between rows in a matrix—for example, the Jaccard index, Euclidean distance, cosine similarity, and Pearson's correlation. Here, we'll cover the most common in text analysis, cosine similarity.

Cosine similarity treats the rows of our TCM as vectors representing the uses of terms and the locations of these terms in an abstract metric “space.” This space is more than three dimensions, so it is difficult to imagine, but we’ll compare the “angle” between these two vectors using cosine. If two vectors are similar—that is, they have similar counts in the same positions—they’ll have a smaller angle. Let’s create our own cosine similarity function.

```r
cos_sim <- function(A, B) {
  sum(A * B) / sqrt(sum(A^2) * sum(B^2))
}
```

```r
# get select the rows by word
vec1 <- as.vector(tdm["shake", ])
vec2 <- as.vector(tdm["love", ])
vec3 <- as.vector(tdm["alone", ])
cos_sim(vec1, vec2) # "shake" and "love"
cos_sim(vec2, vec3) # "love" and "alone"
cos_sim(vec3, vec1) # "alone" and "shake"
[1] 0.0006406371
[1] 0.05576185
[1] 0.001531841
```

With cosine similarity, a “1” means the vectors are the same. So, “love” and “alone” are more similar to each other than either is to “shake.” Remember, perfect similarity here means two words are present in the same songs and absent from the same songs. This gets at syntagmatic associations between words.

Using matrix multiplication, we can project the DTM to a term-co-occurrence matrix (TCM), showing which words “co-occur” with other words in a document (here, a song). First, we transpose the DTM to get a term-document matrix (TDM). Second, we “project” our rectangular matrix into one of two square matrices using matrix multiplication.
