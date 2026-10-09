
![](img/315929ad4bddd26368466d02e06e2385_373_0.png)

![](img/315929ad4bddd26368466d02e06e2385_373_1.png)

![](img/315929ad4bddd26368466d02e06e2385_373_2.png)

FIGURE 9.12: In-sample residuals for the California home values for lasso, CART, and RF fitted regressions. These images were created using the maps package, which is one of the many tools in R for plotting and analyzing spatial data.

![](img/315929ad4bddd26368466d02e06e2385_373_3.png)

FIGURE 9.13: Out-of-sample performance over ten random folds for the California housing regressions.

**RANDOM FORESTS ARE A BIG DATA TECHNIQUE.** It just might not seem that way when fitting them on your laptop. Without making use of parallelization, the sequential fitting of trees will take a long time. However, forests are all about big data! They work on massive distributed datasets and can be deployed on industrial scale. You just need to make use of the parallel and partitioned computing ideas that we introduced at the end of Chapter 4. To close this section on RFs, we'll outline the techniques necessary for deploying them at Internet scale.

First, if you ran the 200-tree RF for the California housing regression, you would have noticed that it took much longer than running CART—perhaps even 200 times longer. However, each of these trees could have been fit at the same time if you had enough available processors. Indeed, the ranger library automatically uses all of your cores for parallel processing—that is, you were probably parallel computing even if you didn't know it. The `num.threads` argument specifies the number parallel tree-fitting processes (threads), and the default of `num.threads=NULL` chooses as many threads as you have cores. Moving from one to four threads decreases my compute time by half to one-third.

```
system.time(carf <- ranger(logMedVal ~ ., data=CAhousing, num.threads=1, ...))
  user  system elapsed
  8.75    0.03    8.92
system.time(carf <- ranger(logMedVal ~ ., data=CAhousing, num.threads=4, ...))
  user  system elapsed
 13.00    0.04    3.50
```

In these printouts the elapsed number corresponds to the actual wall-clock time spent waiting. The speed-up is less than a factor of 4 because of the considerable overhead involved in copying data across the four compute cores.

The overhead created by data copy points to the problem with this type of basic parallelization: no matter how many cores you can get, you will be limited by the communication cost of data transfer. Even worse, if the data are very big, then it can be impossible to fit them into the working memory of a single processing unit. In that case, full parallelization becomes infeasible and RFs are hopelessly slow. In industry, engineers have developed a number of work-arounds to deal with this issue of memory limits. One common strategy is to replace the with-replacement sampling of RFs with subsampling: each tree is fit to a without-replacement sample of size smaller than $n$ (small enough to fit on a single core). This leads to what I call a subsampling forest, in which each tree has been fit to a small random data subset.

This is a really bad idea. Subsampling forests tend to have sharply worse predictive performance than RFs. Understanding why this happens gets to the heart of nonparametrics. Methods such as trees lead to increasingly complex surfaces as you give them more data. The idea of RFs is to take advantage of this nonparametric adaptivity while using bootstrap aggregation to avoid overfit. If you replace the bootstrapping with subsampling, then you are starving your nonparametric learners (the trees) of the data that they need to perform well.

While working with eBay, a group of us noticed a prediction performance decrease because of a switch from full RFs to subsampling forests. This motivated us to formalize a simple alternative called *empirical Bayesian forests* ${ }^{10}$ (EBF; the Bayesian name is due to theory derived from a Bayesian bootstrap, but it is not important in practice). The algorithm is based on a simple observation: when you have a large dataset, the *tops* (or trunks—the first few splits) of the trees in a forest are mostly similar. ${ }^{11}$

For example, fitting CART to the California housing data down to a minimum leaf size of 3500 observations results in the *trunk* shown in Figure 9.14. After fitting an RF to the same data, a comparison across trees in the forest shows that they all have a trunk structure similar to that of Figure 9.14. In particular, that *exact* trunk occurs $62 \%$ of the time. The second most common trunk, occurring $28 \%$ of the time, differs only in that it splits on median income again instead of on housing median age. Thus, $90 \%$ of the posterior weight is on trees that split on income twice and then latitude. Moreover, a striking $100 \%$ of trees have first two splits on median income. Figure 9.15 shows the locations of these first two splits: each split-location is concentrated around the trunk split in Figure 9.14.

![](img/315929ad4bddd26368466d02e06e2385_376_0.png)

![](img/315929ad4bddd26368466d02e06e2385_376_1.png)

![](img/315929ad4bddd26368466d02e06e2385_376_2.png)

![](img/315929ad4bddd26368466d02e06e2385_376_3.png)

![](img/315929ad4bddd26368466d02e06e2385_376_4.png)

![](img/315929ad4bddd26368466d02e06e2385_376_5.png)

![](img/315929ad4bddd26368466d02e06e2385_376_6.png)

![](img/315929ad4bddd26368466d02e06e2385_376_7.png)

![](img/315929ad4bddd26368466d02e06e2385_376_8.png)

FIGURE 9.14: The trunk of the California housing tree that results when fitting with a minimum leaf size of 3500 (out of 20,640 total census tracts).

![](img/315929ad4bddd26368466d02e06e2385_376_9.png)

FIGURE 9.15: The distribution of median income and of the first two split locations for trees in the housing forest.

This trunk stability occurs after only 20,000 observations. The stability increases dramatically for the millions-plus observation datasets encountered in industrial big data settings. This all suggests an obvious distributed computing strategy for forests: since the trunks in the forest are all the same, just fit the trunk once and then use it to partition the data and facilitate parallelization. This is the empirical Bayesian forest (EBF) algorithm.

## **ALGORITHM 25** Empirical Bayesian Forest (EBF)

Given $K$ distributed processing units:

- Fit a CART trunk down to $K$ nodes—the trunk *branches*. If the data is massive (i.e., too big to fit on a single machine), then you can fit this trunk on a subsample. Since you are only fitting the first few tree splits, which correspond to dominant sources of response variation, you do not need big data to do a good job of trunk estimation.
- This trunk defines a mapper function in the MapReduce algorithm: *map* each observation to its allocated trunk branch and then *reduce* on each branch by fitting a full random forest. This returns the fitted EBF: a fixed trunk with RF models at each branch.

The result is a sort of hybrid CART-RF object, with fixed initial splits and a bootstrap sample of trees for deeper structure. Since the hypothetical (potentially infeasible) full sample RF has the same trunk for most trees, this EBF will lead to similar predictions. In the California housing example, an EBF with the trunk of **Figure 9.14** has 2% worse predictive performance than the full sample RF, compared with 10% worse for a subsampling forest of comparable computational cost. For large datasets the results are more dramatic; Taddy et al. [2015] show EBFs 1% to 4% worse than a full RF on examples where the subsampling forests are 12% to 38% worse.

In massive data environments, simple but efficient strategies like Algorithm 25 allow you to crunch more data faster. And more data always wins: even though an EBF does a bit worse than a full RF on the same dataset, an EBF with more data will give better predictions than a small-sample RF. For prediction tasks, never reduce the amount of data you can work with to fit some fancy but computationally costly model—you’re better off with a simple but flexible model fit to as much data as you can get your hands on.
