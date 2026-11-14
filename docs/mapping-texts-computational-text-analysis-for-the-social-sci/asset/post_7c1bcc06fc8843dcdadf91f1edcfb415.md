
These three lists—from the projections, Euclidean distances/similarities, and cosine similarities—all look somewhat different. While many factors could cause discrepancies between metrics, that document length changes our Euclidean measures is why cosine similarity is far more popular. There are many other similarity metrics to explore that could cross-validate discrepancies. Each metric, though, should be compared with a close reading of a sample of documents.

## DOCUMENT CLUSTERING

Cluster analysis is a ubiquitous technique and one of the first forms of “unsupervised learning” discussed in data science texts. Document clustering is a suite of methods for inductively grouping texts based on similar distributions. These distributions could be word counts across a vocabulary, topics, emotion classification scores—anything.

- THIS SECTION NEEDS:
  - stringr
  - text2map
  - text2vec
  - factoextra
  - tidyverse
  - tidytext

Clustering methods find the partition of documents minimizing the differences between documents within a cluster and maximizing the differences between documents across clusters (Evans and Aceves 2016:32). This is done with an objective function (we’ll flesh this out shortly) used to successively determine whether any two documents should be clustered together.

Miller (1997), for example, used hierarchical clustering to identify “frames” in a corpus of Associated Press news articles on wetlands issues; around the same time, Kabanoff, Waldersee, and Cohen (1995) used a type of k-means clustering to identify the value structures across a sample of Australian organizations using their organizational literature. Document clustering is still in rotation in contemporary computational text analysis—clustering is integrated with topic modeling (more on that later) to, for example, cluster authors (Tierney et al. 2021). We focus on two popular forms: hierarchical clustering and k-means clustering (Grimmer et al. 2022:123–37). One of these requires a distance matrix and one does not.

6 Documents need not be the units to be clustered. For example, instead of clustering documents based on similar word count distributions, we could instead cluster the words in the vocabulary based on their similar distributions across documents.

7 This is any partition into k number of clusters.

This means the maximum number of clusters is the total documents in the corpus ($k = N$, where $N$ is the total document count), while the minimum number is one ($k = 1$).

### Hierarchical Clustering

There are two forms of hierarchical clustering: *agglomerative* and *divisive* (Jain et al. 1999:274). We'll focus on agglomerative clustering because it is more popular than divisive clustering (Roux 2018:345).

8 They differ in their starting point in the hierarchical clustering structure. With agglomerative clustering, each document starts as its own cluster. Then, the most similar documents—that is, those closest—are grouped. This process is repeated until, theoretically, all documents occupy a single cluster. Divisive clustering works in the other direction: all documents occupy the same cluster and then documents are successively separated until each document occupies its own cluster.

So, we start with each document in its own cluster and then successively merge clusters until all documents are in one. We merge clusters based on similarity. But how do we decide which two clusters are the most similar? This is where the **distance matrix** comes in. Two clusters are merged if they are the closest to one another relative to all other possible pairwise cluster comparisons, based on the distance between them.

Implicit here is our **objective function**: minimizing distances between all documents within a cluster. We'll need to select a **merging criterion**: a means of deciding whether the distance between two clusters is the smallest possible given all other possible cluster mergers, and then joining those two clusters based on that minimization. There are many merging criteria but the most popular are the complete-linkage, single-linkage, and Ward's method (Jain et al. 1999:275).

No one merging criterion is consistently favored. Justification for selecting one criterion is rarely provided, outside of picking the one passing the “eye-test”—that is, providing clusters matching expectations given researchers’ substantive knowledge or theory.

Regardless of criterion, clustering provides inductively derived groups of semantically similar documents. Let’s see. We’ll work with the State of the Union speeches—specifically Bill Clinton’s first SOTU in 1993 to Donald J. Trump’s speech in 2020.

9 Tree-based clustering can quickly become computationally demanding with even modestly sized corpora.

Load the data, take care of some wrangling, and create the DTM. We’ll remove all punctuation except for any underscores, commas, or dashes internal to a word, and also remove capitalization, numbers, and excess spaces. We eventually want to see the top words per cluster, so we’ll remove words in the 2014 Snowball stoplist as part of our DTM construction. The functions we’ll use for clustering only work with base R dense matrices.

10 Recall, this is less memory efficient. See Text to Numbers.

```r
data("data_corpus_sotu", package = "quanteda.corpora")

sotu <- tidy(data_corpus_sotu) |>
  filter(Date >= "1993-02-17") |>
  mutate(
    year = gsub("\\d+-.-*", "\\1", Date),
    doc_id = paste0(President, "_", year),
    text = tolower(text),
    text = gsub("\\W+[ '_-:]+\\w+", "", text),
    text = gsub("[[:punct:]]+", "", text),
    text = gsub("[[:digit:]]+", "", text),
    text = str_squish(text)
  )
```

```r
dtm_sotu <- sotu |>
dtm_builder(text, doc_id) |>
dtm_stopper(stop_list = get_stoplist("snowball2014"), dense = TRUE)
```

Now we need to get our document-by-document distance matrix. Let's go with cosine. We'll use dist2().

11 Similarities are the inverse of distances, so we could use sim2() again and then subtract the resulting similarities by 1 to get the cosine distances.

```r
cos_sotu <- dist2(dtm_sotu, method = "cosine")
```

Next, we'll create our cluster tree. We'll let hcut() know this is a distance matrix with as.dist(). For our merging criterion, we'll use Ward's method, which we specify with hc_method = "ward.D2".

12 We'll use factoextra, although there are many packages for hierarchical clustering.

```r
hier_sotu <- hcut(as.dist(cos_sotu), hc_method = "ward.D2")
```

Let's inspect the tree structure of the hierarchical clustering—visualized in the form of a dendrogram. We'll use fviz_dend() for this, starting with k = 2.

13 The cex parameter controls the size of the document labels, and horiz turns the plot left to right.

```r
fviz_dend(hier_sotu, cex = .5, k = 2, horiz = TRUE,
          k_colors = c("#440154FF", "#3A5E8CFF"))
```

Figure 10.1: Dendrogram for Hierarchical Clustering.

### Cluster Dendrogram

![](img/ccc0ce559da97114ef913045f55e3801_177_0.png)

Starting from the right of Figure 10.1, each speech starts in its own cluster—as expected with agglomerative clustering. The first cluster (i.e., the first time two documents are grouped) consisted of Clinton’s 1998 and 2000 speeches. We know this because, if we “read” right to left, those are the first two speeches merging under one line. This clustering process continues until all speeches are in one cluster.

As this illustrates, where we “cut” the dendrogram leads to different cluster solutions. For instance, cutting the dendrogram at 0.1 (following the x-axis) creates 28 clusters—one for each document. Cutting at 0.6, though, creates three clusters (since we would cross three horizontal lines if we sliced at x = 0.6). The inevitable question is: Where to cut?

There are two broad ways to decide on k: interpretive and statistical. First, we can compare the cluster solution against domain knowledge and theory. For instance, does it make sense for Bush’s ’01 speech to be in the same cluster as Clinton’s ’94 and ’95 speeches? What were they talking about? Did they take place during similar social, political, cultural, and/or economic contexts that would account for semantic similarity?

There are also many “fit statistics” to guide the decision for k: the silhouette width statistic, gap statistic, and gamma index, to name a few.

14 NbClust provides 30 different fit statistics (Charrad et al. 2014).

We’ll focus on one of our favorites: the **silhouette width** statistic.

For each document at a given solution, we calculate its silhouette width by finding the average cosine distance between that document and the other documents in its cluster. Call this c_i. We then calculate the average cosine distance between that document and all other documents cluster by cluster. The smallest average distance between the document and the other clusters is c'_i. The silhouette width for that document is then found by subtracting c_i from c'_i and then dividing that difference by the larger of those two values.

We can then find the average of all documents’ silhouette widths. Values range from -1 to 1, where values closer to 1 indicate excellent average cluster placement and values closer to -1 indicate very poor average cluster placement. If we made our decision for k purely on the silhouette width (which we probably wouldn’t want to do in practice), we would want the k with the largest average value.

How many clusters does the (average) silhouette statistic recommend? We can determine this using `fviz_nbclust()`. To make this work, we first want to define a function that specifies that we want to perform hierarchical clustering with Ward’s method iteratively at different ks.
