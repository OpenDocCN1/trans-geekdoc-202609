```
text = gsub("\\W+[ '_-:]+\\w+", "", text),
text = gsub("[[:punct:]]+", "", text),
text = gsub("[[:digit:]]+", "", text),
text = str_squish(text)
)
```

```
dtm_sotu <- sotu |>
dtm_builder(text, doc_id) |>
dtm_stopper(stop_list = get_stoplist("snowball2014"), dense = TRUE)
```

Now we need to get our document-by-document distance matrix. Let's go with cosine. We'll use dist2(). 11

11 Similarities are the inverse of distances, so we could use sim2() again and then subtract the resulting similarities by 1 to get the cosine distances.

```
cos_sotu <- dist2(dtm_sotu, method = "cosine")
```

Next, we'll create our cluster tree.12 We'll let hcut() know this is a distance matrix with as.dist(). For our merging criterion, we'll use Ward's method, which we specify with hc_method = "ward.D2".

12 We'll use factoextra , although there are many packages for hierarchical clustering.

```
hier_sotu <- hcut(as.dist(cos_sotu), hc_method = "ward.D2")
```

Let's inspect the tree structure of the hierarchical clustering— visualized in the form of a dendrogram. We'll use fviz_dend() for this, starting with k = 2.13

13 The cex parameter controls the size of the document labels, and horiz turns the plot left to right.

```
fviz_dend(hier_sotu, cex = .5, k = 2, horiz = TRUE,
          k_colors = c("#440154FF", "#3ASE8CFF"))
)
```

Figure 10.1: Dendrogram for Hierarchical Clustering.

# Cluster Dendrogram

![](bbox=[0.35, 0.58, 0.9, 0.9])