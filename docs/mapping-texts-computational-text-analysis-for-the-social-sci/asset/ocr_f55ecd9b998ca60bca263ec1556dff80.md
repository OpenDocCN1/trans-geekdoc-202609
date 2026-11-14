Let's walk through a toy example first. Let’s use lines from Mary Shelley’s *Frankenstein* and Octavia Butler’s *Parable of the Sower*. We’ll weight words by how they “predict” the author of the line.

```
shelley <- data.frame(
 text = c(
 "destroy your own creature oh praise the eternal justice",
 "of man yet i ask you not to spare me listen to me and",
 "then if you can and if you will destroy"
 )
)
```

```
butler <- data.frame(
 text = c(
 "we are earthlife maturing",
 "earthlife preparing to fall away from the parent world",
 "we are earthlife"
 )
)
```

```
shelley$butler <- 0
butler$butler <- 1
corpus <- rbind(butler, shelley)
```

Now we turn our mini-corpus into a DTM. We treat the terms as predictors in our regression and the author as the outcome. For this illustration, we also convert our DTM to a data.frame so we can append our outcome variable.

```
dtm <- corpus |
 rowid_to_column(var = "doc_id") |
 dtm_builder(text, doc_id = doc_id)
dtm <- as.data.frame(as.matrix(dtm))
dtm$butler <- corpus$butler
```

We’re ready to predict the author using terms in each line. Note that using the period means to use all columns in the dataframe except our outcome variable (here, “butler”).

```
mod <- glm(butler ~ ., family = binomial, data = dtm)
```

Instead of inspecting the model (as we did previously), let’s just extract an estimate (coefficient). Ignoring the numbers, the estimate for “earthlife” is positive (like we expect). This means, if we were to apply this small dictionary to new texts, the presence of “earthlife” would make it more likely we would label a text as authored by “Butler.”26

```
round(coef(mod)["earthlife"], 6)
```

```
earthlife
49.13214
```

Let’s scale this up. To begin, we’ll use a corpus of four thousand posts across five social media sites. Each comment has been hand-labeled as containing a positive or negative sentiment by three human labelers.

```
data("corpus_senti_bench4k", package = "text2map.corpora")
```

26 We’re being a little loose for illustration. In practice, we need many more examples and many more terms to build this dictionary because, as we learned in Text to Numbers, language is sparse.