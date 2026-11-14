To show this, first, we'll *binarize* our DTM, which means creating a matrix with only ones and zeros (or `TRUE` and `FALSE`), where a one indicates that the word occurs at least once in a document.

```
```r
# 4 ways to create a binary matrix
bin_dtm <- dfm_weight(adtm_quanteda, scheme = "boolean")
bin_dtm <- as(dtm, "lMatrix")
bin_dtm <- ifelse(dtm > 0, 1, 0)
bin_dtm <- dtm[] > 0
```
```

When we sum the rows of our binarized DTM, we’ll get the number of types in each document. We then divide that by the total number of tokens in each document (the document length)—this is the *type-token ratio*.

```
```r
doc_types <- rowSums(bin_dtm) # get number of types
doc_lengths <- rowSums(dtm) # get number of tokens in each document
```
```

```
```r
type_token <- data.frame(
  types = doc_types,
  tokens = doc_lengths,
  lang = c(rep("French", 5000),
           rep("English", 5000))
)
```
```

```
```r
type_token |>
  ggplot(aes(x = tokens, y = types)) +
  geom_point(alpha = .2) +
  labs(x = "Tokens", y = "Types",
       subtitle = "Total Tokens by Total Type") +
  facet_wrap(~lang)
```
```

The plots are in the bottom two rows of Figure 6.1. There are, once again, striking similarities across the languages—as we would expect.

These two intertwined laws—Zipf’s and Herdan-Heaps’—hold for virtually any n-grams. They are a feature of corpora in most—possibly all—languages (Yu et al. 2018). This is the case even in “artificial” languages like Esperanto and Klingon (Smaha and Fellbaum 2015)! Regardless of the language we’re working with, then, *most documents will share most of their words*.

# # WEIGHTING AND NORMING

+   THIS SECTION NEEDS:
+   * tidyverse
+   * tidytext
+   * quanteda
+   * text2map
+   * gggpubr

Up to this point, we have primarily been working with DTMs where the cells are the raw frequency counts of unique terms, typically called *term frequencies* or *tf* (1975:4). Information retrieval researchers argued that “the frequency of word occurrence in an article furnishes a useful measure of word significance” (Luhn 1958:160).