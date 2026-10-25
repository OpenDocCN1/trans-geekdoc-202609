puted from the test data. The model seems reasonably calibrated (as we would hope from a probability forest). The cumulative gains chart tells us, for example, that we could expect roughly 1,500 subscriptions by contacting the top 20% of clients with the highest predicted probability of subscribing.

![](bbox=[0.15, 0.18, 0.88, 0.46])

FIGURE 7.27: Graphical assessment of the performance on the test set. Left: isotonic regression-based calibration curve. Right: Cumulative gains chart.

Next, I'll look at the RF-based variable importance scores. Unfortunately, SparkR does not return the variable importance scores from tree-based models in a friendly format; it just gives one long nasty string, as can be seen below:

```
rfo.summary <- summary(rfo) # extract summary information
(vi <- rfo.summary$featureImportances) # gross...
#> [1] "(52,[0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,...
```

Nonetheless, I can use some regular expression (regex) magic to parse the output into a more friendly data frame. (By no means do I claim this to be the best solution; I'm certainly no regexpert—ba dum tsh.)

```
vi <- substr(vi, start = regexpr('"', text = vi)[1] + 1,
             stop = nchar(vi) - 1)
vi <- gsub("\\\\", replacement = "c(", x = vi)
```

YIt is not clearly documented which variable importance metric MLlib uses in its implementation of RFs, but I suspect it's the impurity-based metric (Section 7.5) since, as far as I'm aware, MLlib's RF implementation does not support the notion of OOB observations (Section 7.3).