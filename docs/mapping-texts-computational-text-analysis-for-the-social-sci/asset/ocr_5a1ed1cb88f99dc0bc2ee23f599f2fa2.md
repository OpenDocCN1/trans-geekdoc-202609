Next, we'll transpose the DTM, which tips and twists it, so the dimensions are flipped.

```
tdm <- t(dtm) # transpose the dtm to get a tdm
dim(tdm) # A vocab of 3240 and 120 songs
```

In this TCM, the features summarizing each token are the songs in which they occur and do not occur. With a feature matrix like this, we can compare how associated any two terms are by comparing their vectors (i.e., their respective rows in the TCM). There are many methods to measuring similarity between rows in a matrix—for example, the Jaccard index, Euclidean distance, cosine similarity, and Pearson's correlation. Here, we'll cover the most common in text analysis, cosine similarity.

Cosine similarity treats the rows of our TCM as vectors representing the uses of terms and the locations of these terms in an abstract metric “space.” This space is more than three dimensions, so it is difficult to imagine, but we’ll compare the “angle” between these two vectors using cosine. If two vectors are similar—that is, they have similar counts in the same positions—they’ll have a smaller angle. Let’s create our own cosine similarity function.

```
cos_sim <- function(A, B) {
  sum(A * B) / sqrt(sum(A^2) * sum(B^2))
}
```

```
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