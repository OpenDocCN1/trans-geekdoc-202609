```
```r
confusion.glmnet(fit,
  newx = dtm_tst,
  newy = df_tst$positive,
  s = "lambda.min"
)
```
```

| | Predicted FALSE | TRUE | Total |
|---|---|---|---|
| True FALSE | 595 | 242 | 837 |
| TRUE | 36 | 139 | 175 |
| Total | 631 | 381 | 1012 |

Percent Correct: 0.7253

Using a “confusion matrix,” a table that tallies which guesses we got right and which we got wrong, we can see it did okay.29 The articles not labeled with positive sentiment (the FALSE column) were only misclassified a little. We didn’t as well guessing which articles were labeled with positive sentiment (the TRUE column). We may need to incorporate valence shifters or other fine-tuning—dictionary building is, after all, an iterative process.

Setting s to "lambda.min" means we use the lambda weights giving the smallest average mean-squared error when predicting the heldout subsets.

Another way we can see how well our dictionary “learned” sentiment is by comparing it to one of the pre-constructed sentiment dictionaries. We’ll use inner_join to only keep the words present in both, and then use cor() to calculate correlations between them.

```
```r
data("hash_sentiment_jockers_rinker", package = "lexicon")
dict <- data.frame(term = rownames(coef(fit)),
                   weight = coef(fit)[, 1])
dict <- inner_join(dict, hash_sentiment_jockers_rinker,
                   by = c("term" = "x"))
cor(dict$weight, dict$y)
```
```

[1] 0.4218874

Our learned dictionary is positively correlated with one of the best pre-built sentiment dictionaries available—albeit moderately. As a first run, though, that’s not bad!

When classifying documents, precompiled dictionaries are a great place to start. Like all methods in this book, results from such dictionaries should be checked against our intuitions, prior research, and our research questions.30 If we do end with a custom dictionary, however constructed, we must share this dictionary with our community. Otherwise, researchers will struggle to reproduce or build upon our findings—or correct our errors.

We direct readers to the very useful literature on construct validity and its various cousins. However, if we continue to fail to find what we are looking for, our corpus may simply be talking about something else!