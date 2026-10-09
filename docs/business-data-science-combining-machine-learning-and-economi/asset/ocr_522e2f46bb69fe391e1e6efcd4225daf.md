PLS(1); see Chapter 7. They are regressing repshare on speech content to build a model that connects language to partisanship. This is then used to quantify political slant in newspapers and investigate issues around partisanship and press ownership.

We can replicate their analysis using the pls function:

```
```
> x <- congress109Counts
> slant <- pls(x, congress109Ideology$repshare, K=3)
```
```

Figure 8.3 shows results for the first three PLS directions. The insample $R_2$ for each direction is 0.17, 0.32, and 0.43—there is a big increase with each extra dimension. Qualitatively, the second direction appears to be necessary for picking up the language associated with high-repshare Republicans (those likely on the right of the party).

![](bbox=[0.17, 0.4, 0.87, 0.61])

The PLS fits for repshare on relative term usage in the 1000 bigram congress109 vocabulary. Points are colored by political party—grey for Republicans and black for Democrats.

As an alternative to PLS, we can also run a lasso regression for repshare on text:

```
```
> Lassoslant <- cv.gam1r(x, congress109Ideology)
```
```

Figure 8.4 shows the results of a CV experiment used to select $\lambda$ next to an OOS experiment to evaluate the number of PLS directions. We see that the lasso generally outperforms PLS here—the best PLS results are for $K$ of one