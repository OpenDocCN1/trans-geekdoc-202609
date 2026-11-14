```
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
```

To create a visualization, let’s chunk the text by 5-gram shingles, then tokenize by word boundary before making a DTM. Finally, we’ll use matrix multiplication to create a TCM like before. We’ll also force the functions to *not* lowercase the text.

```
```r
jfk_shingles <- tokenize_ngrams(jfk_text,
                                  n = 6L, n_min = 6L,
                                  lowercase = FALSE
                              )
```
```

```
```r
dtm <- tokens(unlist(jfk_shingles)) |>\n  dfm(tolower = FALSE)
```
```

```
```r
tcm <- t(dtm) %*% dtm
```
```

Now, let’s treat our term-co-occurrence matrix as if an “adjacency matrix”—a common data structure in network analysis.40 We can plot this as a network graph, where words are nodes and connections are the co-occurrences between words.41 The graph is shown in Figure 6.5.

40 See Math Basics and Extended Inductive.

41 For this, we need specialty packages: tidygraph and ggraph .

```
```r
gr <- tcm |>
  as.matrix() |>
  as_tbl_graph(directed = FALSE) |>
  mutate(name = ifelse(name %in% c("We", "we"), 4, 1))

ggraph(gr, layout = "grid") +
  geom_edge_arc(aes(alpha = weight, strength = .04) +
  geom_node_label(aes(label = name, fontface = f on)) +
  theme_void() +
  theme(legend.position = "none")
```
```

Even with this short text, our graph is on the verge of being unruly. We’ll discuss strategies to *reduce these dimensions* or *limit the feature space* later. Many of these strategies, however, are not typical dimension reduction techniques, but are better understood as such. For example, when we didn’t lowercase our texts, this is telling our scripts to treat “We” and “we” as distinct types instead of the same type. If we rerun the above script but allow the functions to lowercase our text, this would reduce the dimensions of our matrices. In our example, the DTM had 36 columns. Had we lowercased first, it would be 35 columns. This doesn’t seem like much, but in larger corpora, lowercasing can significantly reduce columns. Information is also lost when we remove the distinction