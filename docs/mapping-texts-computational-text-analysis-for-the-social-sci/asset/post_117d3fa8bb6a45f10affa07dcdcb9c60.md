

```r
# we can also create a TCM with the cross product
# column by column (i.e., term by term) matrix
tcm <- crossprod(dtm)

# this creates a document-similarity matrix
# row by row (i.e., document by document) matrix
dsm <- tcrossprod(dtm)
```

We'll either get a matrix of document-by-document similarities (DSM), or a term-by-term co-occurrence matrix (TCM). The output is a square N x N matrix, where N is either the size of the vocabulary or N is the number of documents in the corpus. In a TCM, the features are now the context terms with which a target term tends to co-occur within a sequence (here, an entire song). Now, cosine similarities will measure paradigmatic associations between words.

```r
vec1 <- as.vector(tcm["shake", ])
vec2 <- as.vector(tcm["love", ])
vec3 <- as.vector(tcm["alone", ])

cos_sim(vec1, vec2)
cos_sim(vec2, vec3)
cos_sim(vec3, vec1)
```

[1] 0.4689983  
[1] 0.862345  
[1] 0.5598621  

The magnitudes have changed considerably, but the rank of similarities has not changed. “Alone” and “love” remain the most similar.

Often the document is too large to provide an informative context for each term, or there is too much variation in document lengths. We can refine the TCM by changing the size of the “context.” Rather than an entire document, the context might be paragraphs, sentences, or a moving window (i.e., a skipgram or shingle) of a certain number of words.

We'll create a TCM with a context window of five tokens for Swift's songs using `fcm()` (i.e., feature co-occurrence matrix). Let's also include a corpus of Beyonce's songs to compare.

```r
data("corpus_beyonce", package = "text2map.corpora")
df_beyonce <- corpus_beyonce |>
  mutate(text = tolower(song_text),
         text = gsub("[[:punct:]]", " ", text),
         text = trimws(text))
```

As a loose rule, smaller windows (e.g., one to three words) are more “syntactic,” while larger windows (e.g., four- to ten-word windows) are more “semantic.”36 Since we’re using songs, let’s set the window to four.

36 Linguists debate this distinction (Bybee et al. 1994). Another way of thinking about the difference is a spectrum from more specific meaning (semantic) to more generic meanings (syntactic) (Sweetser 1988).

```r
tkns_ts <- tokens(df_swift$text)
tkns_be <- tokens(df_beyonce$text)

tcm_ts <- fcm(tkns_ts, context = "window", window = 4L, tri = FALSE)
tcm_be <- fcm(tkns_be, context = "window", window = 4L, tri = FALSE)
```

In corpus linguistics, the TCM formalizes Firth’s (1957:11) famous quip “you shall know a word by the company it keeps.” If the context window is relatively small, the TCM captures a special kind of co-occurrence called **collocation**. This refers to words that are often right next to each other, for example, “fast food,” or “european union.” One use for collocations is determining which *n*-grams we may want to retain during tokenization.

How do we measure whether two (or more) terms co-occur an *unusual amount* in a corpus? We find the probability a target term occurs with a context term *controlling for* the probability of those terms appearing on their own. If we take the natural log of this, then we have the **pointwise mutual information** (PMI).37 Although there are packages for this, let’s build a function step-by-step (adapted from textvec’s `coherence()` ).

```r
get_ppmi <- function(tcm, tkns) {
  # how big of context windows did we use
  n_windows <- round(sum(lengths(tkns)) / 4L)
  # small constant to avoid a logarithm of zero
  constant <- 1e-10
  # get overall probabilities
  tcm_pmi <- (tcm / n_windows) + constant
  # get the diagonal: how many times a word occurs at all
  tcm_diag <- diag(tcm_pmi)
  # divide the cells by the diagonal
  tcm_pmi <- tcm_pmi / tcm_diag
  # fix the diagonal and log
  tcm_pmi <- tcm_pmi %*% diag(1 / tcm_diag)
  tcm_pmi <- log(tcm_pmi)

  # convert it to a base R matrix
  tcm_pmi <- as.matrix(tcm_pmi)
  colnames(tcm_pmi) <- rownames(tcm_pmi)
  return(tcm_pmi)
}
```

After running our function, we can use it to weight our TCMs.

```r
tcm_pmi_ts <- get_ppmi(tcm_ts, tkns_ts)
tcm_pmi_be <- get_ppmi(tcm_be, tkns_be)

# have a look
tcm_pmi_ts[1:3, 1:3]
tcm_pmi_be[1:3, 1:3]
```

| | V1 | V2 | V3 |
|---|---|---|---|
| i | 1.723724 | 16.46247 | 3.281868 |
| blew | 16.462466 | 23.02585 | 20.946410 |
| things | 3.281868 | 20.94641 | 7.306280 |

37 A TCM weighted by PMI is foundational to “word embeddings” (Levy and Goldberg 2014); see Extended Inductive.

| | certified | quality | a |
|---|---|---|---|
| certified | 23.02585 | 36.81142 | 16.894625 |
| quality | 36.81142 | 23.02585 | 16.894625 |
| a | 16.89463 | 16.89463 | 3.109061 |

If two terms have a high PMI, this means whenever we see one term, we'll probably see the other term nearby (again, syntactic associations). For example, in Beyoncé’s songs, if we see “certified,” we’ll likely see “quality.” Let’s look at only the row for the terms with the highest PMI to “winning” in our Swift TCM (output in margin).

| | pmi | terms |
|---|---|---|
| 1 | 36.889908 | smile |
| 2 | 36.889908 | ring |
| 3 | 36.889908 | suburban |

```r
df_winning <- data.frame(
  pmi = as.vector(tcm_pmi_ts["winning", ]),
  terms = names(tcm_pmi_ts["winning", ])) |>
  arrange(desc(pmi))
head(df_winning, n = 3)
```

38 This checks out when we look at lyrics from "Coney Island.": "...the gift-wrapped suburban dreams.... Sorry for not winning you an arcade ring."

We can conclude that whenever we see “winning” in Swift’s songs, we’ll likely see “smile,” “ring,” or “suburban” nearby!38

After weighting the TCM by pointwise mutual information, let’s again use cosine to compare terms (i.e., get paradigmatic associations). Below, we’ll compare all the shared words in Beyoncé and Swift’s songs using an anchor term, “sorry.” Below, we’ll subset both TCMs so they have the same vocabulary.

```r
vocab <- intersect(colnames(tcm_pmi_be), colnames(tcm_pmi_ts))
tcm_pmi_be <- tcm_pmi_be[vocab, vocab]
tcm_pmi_ts <- tcm_pmi_ts[vocab, vocab]
```

39 In addition to sim2() and dist2() in text2vec, we could use dist() in base R to compare row vectors. quanteda has similar functions.

We’ll use a faster function from text2vec .39

```r
sim_be <- sim2(tcm_pmi_be["sorry", , drop = FALSE],
                 tcm_pmi_be, method = "cosine")
sim_ts <- sim2(tcm_pmi_ts["sorry", , drop = FALSE],
               tcm_pmi_ts, method = "cosine")
df_compare <- data.frame(
  term = rownames(tcm_pmi_be),
  swift = as.vector(sim_be),
  beyonce = as.vector(sim_ts)
)
```

Finally, let’s plot all the shared words by their cosine similarity to “sorry” in Beyoncé’s songs and “sorry” in Swift’s songs (Figure 6.4).

```r
df_compare |>
  ggplot(aes(x = swift, y = beyonce)) +
  geom_abline(intercept = 0, slope = 1, linetype=2) +
  geom_label(aes(label = term)) +
  labs(x = "Cosine to 'Sorry' in Taylor Swift's Songs",
       y = "Cosine to 'Sorry' in Beyonce's Songs")
```

![](img/ccc0ce559da97114ef913045f55e3801_100_0.png)

Figure 6.4: Term Similarities with PMI-Weighted TCMs.

We added a diagonal line where terms above it are more similar to “sorry” in Beyonce’s songs and terms below are more similar to “sorry” in Swift’s songs. “Single” is more similar in Swift’s corpus, while “fake” is more similar in Beyonce’s.

What jumps out when we see this scatter plot, though, is that the words are kind of a mess. Language is high-dimensional or feature-rich. Songs, like any other text, have multiple levels of meanings (Barthes and Duisit 1975). To map these meanings, we often *reduce these dimensions* to facilitate interpretation.

## DIMENSION REDUCTION

The matrices we use to represent document- and term- features are often “high dimensional.” In plain terms, this means our matrices have lots of columns. Consider, for example, the co-occurrences of words in a short piece of text: the excerpt from Kennedy’s Rice speech we previously auto-transcribed. It contains 35 unique types.

```r
jfk_text <- c(
"We choose to go to the moon
We choose to go to the moon
We choose to go to the moon in this decade
and do the other things not because they are easy but
because they are hard because they measure the best of
our energies and skills because that challenges one
that we're willing to accept one we are willing to
postpone and one we intend to win"
)
```

To create a visualization, let’s chunk the text by 5-gram shingles, then tokenize by word boundary before making a DTM. Finally, we’ll use matrix multiplication to create a TCM like before. We’ll also force the functions to *not* lowercase the text.

```r
jfk_shingles <- tokenize_ngrams(jfk_text,
                                  n = 6L, n_min = 6L,
                                  lowercase = FALSE
                              )
```

```r
dtm <- tokens(unlist(jfk_shingles)) |>
  dfm(tolower = FALSE)
```

```r
tcm <- t(dtm) %*% dtm
```

Now, let’s treat our term-co-occurrence matrix as if an “adjacency matrix”—a common data structure in network analysis.40 We can plot this as a network graph, where words are nodes and connections are the co-occurrences between words.41 The graph is shown in Figure 6.5.

40 See Math Basics and Extended Inductive.

41 For this, we need specialty packages: tidygraph and ggraph.

```r
gr <- tcm |>
  as.matrix() |>
  as_tbl_graph(directed = FALSE) |>
  mutate(name = ifelse(name %in% c("We", "we"), 4, 1))

ggraph(gr, layout = "grid") +
  geom_edge_arc(aes(alpha = weight, strength = .04)) +
  geom_node_label(aes(label = name, fontface = "bold")) +
  theme_void() +
  theme(legend.position = "none")
```

Even with this short text, our graph is on the verge of being unruly. We’ll discuss strategies to *reduce these dimensions* or *limit the feature space* later. Many of these strategies, however, are not typical dimension reduction techniques, but are better understood as such. For example, when we didn’t lowercase our texts, this is telling our scripts to treat “We” and “we” as distinct types instead of the same type. If we rerun the above script but allow the functions to lowercase our text, this would reduce the dimensions of our matrices. In our example, the DTM had 36 columns. Had we lowercased first, it would be 35 columns. This doesn’t seem like much, but in larger corpora, lowercasing can significantly reduce columns. Information is also lost when we remove the distinction

