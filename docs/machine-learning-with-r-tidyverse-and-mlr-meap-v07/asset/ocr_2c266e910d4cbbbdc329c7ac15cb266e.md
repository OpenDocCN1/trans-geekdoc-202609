![](bbox=[0.145, 0.045, 0.855, 0.525])



In this section I'm going to show you how to use the DBSCAN algorithm to cluster a dataset. We'll then use some of the techniques we learned in the last chapter to validate its performance and select the best-performing hyperparameter combination.

> The mlr package does have a learner for the DBSCAN algorithm ( cluster.dbscan), but we're not going to use it. There's nothing wrong with it, but as you'll see later, the presence of the noise cluster causes problems for our internal cluster metrics, and so we're going to do our own performance validation outside of mlr.