partitioned computing ideas that we introduced at the end of Chapter 4. To close this section on RFs, we'll outline the techniques necessary for deploying them at Internet scale.

First, if you ran the 200-tree RF for the California housing regression, you would have noticed that it took much longer than running CART—perhaps even 200 times longer. However, each of these trees could have been fit at the same time if you had enough available processors. Indeed, the ranger library automatically uses all of your cores for parallel processing—that is, you were probably parallel computing even if you didn't know it. The num.threads argument specifies the number parallel tree-fitting processes (threads), and the default of num.threads=NULL chooses as many threads as you have cores. Moving from one to four threads decreases my compute time by half to one-third.

```
system.time(carf <- ranger(logMedVal ~ ., data=CAhousing, num.threads=1, ...)
user system elapsed
8.75 0.03 8.92
system.time(carf <- ranger(logMedVal ~ ., data=CAhousing, num.threads=4, ...)
user system elapsed
13.00 0.04 3.50
```

In these printouts the elapsed number corresponds to the actual wall-clock time spent waiting. The speed-up is less than a factor of 4 because of the considerable overhead involved in copying data across the four compute cores.

The overhead created by data copy points to the problem with this type of basic parallelization: no matter how many cores you can get, you will be limited by the communication cost of data transfer. Even worse, if the data are very big, then it can be impossible to fit them into the working memory of a single processing unit. In that case, full parallelization becomes infeasible and RFs are hopelessly slow. In industry, engineers have developed a number of work-arounds to deal with this issue of memory limits. One common strategy is to replace the with-replacement sampling of RFs with subsampling: each tree is fit to a without-replacement sample of size smaller than n (small enough to fit on a single core). This leads to what I call a subsampling forest, in which each tree has been fit to a small random data subset.

This is a really bad idea. Subsampling forests tend to have sharply worse predictive performance than RFs. Understanding why this happens gets to the