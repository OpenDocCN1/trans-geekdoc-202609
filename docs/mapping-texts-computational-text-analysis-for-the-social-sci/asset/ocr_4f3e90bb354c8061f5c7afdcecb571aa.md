this is a useful method for deductively mapping a particular concept in our texts without labeling them first.

# Retrofitting Pretrained Embeddings for Deductive Analysis

A criticism of the previous process might be that fastText embeddings are trained on the 2015 Wikipedia Data Dump, but Shakespeare was writing over 400 years ago. Recall many embedding methods (implicitly or explicitly) assign words vectors such that their cosine approximates their probability of co-occurring in the corpus. In other words, we can use pairwise cosine to re-create a TCM.

+   THIS SECTION NEEDS:
+   * tidyverse
+   * stringi
+   * gutenbergr
+   * text2map
+   * text2map.pretrained
+   * text2vec
+   * rsvd
+   * tidytext
+   * spacyr
+   * semgram

We can also go the other way: use a focal TCM to “retrofit” pretrained embeddings. We’ll start with all the plays in the First Folio, but won’t collapse lines. Then we’ll do the same preprocessing as before and remove any blank lines.

```
data("meta_shakespeare", package = "text2map")
my_mirror <- "mirrors.xmission.com/gutenberg/"
df_shake <- meta_shakespeare |>
  select(gutenberg_id) |>
  gutenberg_download(mirror = my_mirror) |>
  left_join(meta_shakespeare)
```

```
df_shake <- df_shake |>
  mutate(gutenberg_id = as.character(gutenberg_id)) |>
  rename(line = text) |>
  mutate(text = replace_non_ascii(line),
         text = replace_curly_quote(text),
         text = replace_contraction(text),
         text = gsub("[[ :punct: ]]+", " ", text),
         text = gsub("[[ :digit: ]]+", " ", text),
         text = tolower(text),
         text = str_squish(text)) |>
  filter(text != "")
```

Let’s create a TCM with a context window of 5 using text2vec . Remember, by default, create_tcm() weights each word by the inverse of its distance from the target word.

```
tkns <- unlist(df_shake$text) |> str_split(" ")
vectorizer <- itoken(tkns) |>
  create_vocabulary()
  vocab_vectorizer()
tcm_sh <- itoken(tkns) |>
  create_tcm(vectorizer, skip_grams_window = 5L)
```

Load in the fastText embeddings trained on the Common Crawl.

```
# load the model each session
data("vecs_fasttext300_commoncrawl", package = "text2map.pretrained")
ft_vw <- vecs_fasttext300_commoncrawl # rename so it's tidier
```