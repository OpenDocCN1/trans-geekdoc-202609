# Term Frequency/Inverse Document Frequency

Words occurring infrequently within a corpus may still be distinctive for a particular document if it only occurs in that document (or in very few documents). Similarly, Sparck Jones (1972) argued that a word's frequency in a corpus (or **document frequency**) was inversely proportional to its significance. This was because less frequent words referred to more specific ideas. Her work introduced the idea of **inverse document frequency**, or **_idf_**. Roughly, this is the number of documents in a corpus, divided by the total documents in which a term appears. This allows us to identify words that are surprising to find in a document and thus potentially insightful.

We can use this to weight DTM cells by multiplying the term frequency within a document with the inverse of the term's document frequency in the corpus (i.e., **_tf-idf_**). This increases the weight of a word according to the times it occurs in a document _relative to_ its frequency in the corpus. Below is a method to weight our DTM by **_tf-idf_** in base R . <sup>29</sup>

<sup>29</sup> We'll use the base 10 logarithm in our calculation of the **_idf_** scores. This is also of the default in **quanteda** 's **dfm_tfidf()** . Different papers and packages use different bases, though. For example, Salton (Salton 1975:29) uses base 2 in his classic essay on indexing, and so does **tm** .

```
# we already have term frequencies
# assign it to a new object for clarity
tf <- dtm
# this calculates inverse-document frequencies
idf <- log10(nrow(dtm) / colSums(dtm != 0))
dtmtfidf <- tf * idf
```

Several packages have functions to weight DTMs by **_tf-idf_**—and can be faster. For example, this is how we'd re-weight a matrix using **quanteda** .

```
dtm_quanteda <- tokens(df_europarl$text) |> dfm()
dtmtfidf <- dfm_tfidf(dtm_quanteda)
```

Let's compare terms with high counts and relative frequencies with those terms that have high **_tf-idf_** scores. For this, let's use the US State of the Union addresses (SOTUs). See Figure 6.2.

We'll subset the DTMs by Richard Nixon's and John F. Kennedy's addresses. We need to divide our DTMs by which documents correspond to which president.

```
idx_nixon <- text_sotu$President == "Nixon"
idx_kennedy <- text_sotu$President == "Kennedy"

df_nixon <- data.frame(
  tf = colSums(dtm[idx_nixon, ]),
  rf = colSums(dtm rf[idx_nixon, ]),
  tfidf = colSums(dtm[tfidf[idx_nixon, ]]),
  President = "Nixon"),
  Term = colnames(dtm)
)
```