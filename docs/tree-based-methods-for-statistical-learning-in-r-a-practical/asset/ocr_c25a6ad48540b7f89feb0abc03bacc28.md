# 7.6.3.1 Example: Swiss banknotes

Continuing with the Swiss banknote example, I generated a synthetic version of the data set using the bootstrap approach outlined in the previous section, and then stacked the data together into a two-class problem:

```
bn <- treemisc::banknote
X.original <- subset(bn, select = -y) # features only
X.synthetic <- X.original
set.seed(1034)
for (i in seq_len(ncol(X.original))) {
  X.synthetic[[i]] <- sample(X.synthetic[[i]], replace = TRUE)
}
X <- rbind(X.original, X.synthetic)

# Add binary indicator (doesn't)
X$y <- rep(c("original", "synthetic"), each = nrow(bn))
```

I then fit an RF of 1000 trees using the newly created binary indicator y and generated proximities for the original (i.e., first 200) observations. So how well did the unsupervised RF cluster the data? Well, we could convert the proximity matrix into a dissimilarity matrix and feed it into any distance-based clustering algorithm. Another approach, which I'll take here, is to visualize the dissimilarities using multidimensional scaling (MDS). MDS is one of many methods for displaying (transformed) multidimensional data in a lower-dimensional space; for details, see Johnson and Wichern [2007, Sec. 12.6]. Essentially, MDS takes a set of dissimilarities—one minus the proximities, in this case—and returns a set of points such that the distances between the points are approximately equal to the dissimilarities. Figure 7.10 shows the best-fitting two-dimensional representation. Here you can see a clear separation between the genuine bills (black) and counterfeit bills (yellow).

# 7.6.4 Case-specific random forests

The case-specific RF [Xu et al., 2016] is another interesting application of RF proximities (Section 7.6. The idea is to build a new RF to more accurately predict each individual observation in the test set. The individual RFs give more weight to the training observations that have higher proximity to the observations in the test set.

Let d_trn and d_tst be the train and test data sets with N and N_tst observations, respectively. The general steps for growing a case-specific RF are outlined in Algorithm 7.3 below: