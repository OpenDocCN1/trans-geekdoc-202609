```
data("vecs_fasttext300_commoncrawl", package="text2map.pretrained")
wv <- vecs_fasttext300_commoncrawl # rename so it's tidier
```

Now let's create a word vector representation of our DTM by taking the vocabulary intersection of the DTM and the embedding matrix. Remember, words are in the DTM's columns and embedding matrix's rows.

```
atn_vectors <- wv[rownames(wv) %in% colnames(dtm_atn), ]
```

We have vectors for only the words used in our ATN corpus—and we didn't have to train ourselves! Now, we'll analyze some semantic directions. We did this earlier by creating a gender direction anchored by "boy" and "girl". Let's turn our attention to a citizenship-immigration direction, 60 but now let's add *more* terms to each pole. This hones in on the area of the embedding space with this precise meaning. Let's go with a list of 12 terms for each pole, 61 though some terms repeat.

60 Immigrants can, of course, be citizens. This direction is instead "understood as measuring a persistent symbolic structure rather than a legal distinction" (Stoltz and Taylor 2021:10). See also Beaman (2016) and Jaworsky (2013).

61 These are the same terms we used in Stoltz and Taylor (2021).

Let's first construct our dataframe with each anchor list as a separate column.

```
anchors <- data.frame(
  add = c("immigrants", "immigration", "immigrant", "foreign",
        "foreigner", "outsider", "stranger", "alien", "foreigner",
        "alien", "immigrant", "foreign"),
  sub = c("citizens", "citizenship", "citizen", "domestic", "native",
        "insider", "local", "resident", "resident", "native",
        "local", "familiar")
)
```

We get semantic directions using *vector offset* methods. First, is the *paired method*: each pair of words across the two anchor lists (e.g., "conservative" to "liberal" and "traditional" to "progressive") is an antonym pair, we subtract one of the vectors in the pair from the other, and then the sum of those vector differences is divided by the total number of pairs. This method requires the same number of words in each anchor list—since they have to be pairs—though words can repeat.

Second, is the *pooled method*, which involves finding the average vector for each anchor list (i.e., the average vector for the pole #1 words and the average vector of the pole #2 words) and then taking the difference. 62

62 Note that with either the paired or pooled method, we get the offsets *before* calculating cosines. We did the opposite with the gender bias illustration.

Third, is the *PCA method*. We take the vector differences for each antonym pair (as with the paired method), passing that d-by-v matrix 63 to a *principal components analysis (PCA)*, and then retaining the first principal component (Bolukbasi et al. 2016a, b).

63 d is the number of dimensions and v the number of vector differences.

Using `get_direction()` and the paired method (the default), we'll find the semantic direction for "ideological bias."