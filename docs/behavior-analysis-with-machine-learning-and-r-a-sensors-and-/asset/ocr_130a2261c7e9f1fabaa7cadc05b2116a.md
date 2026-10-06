# Bagging Train/Test accuracy

![](bbox=[0.133, 0.131, 0.866, 0.363])

Figure 3.2: Bagging results for different number of trees.

# ## 3.2 Random Forest

```
rf_activities.R iterated_rf_activities.R iterated_bagging_rf.R
```

Random Forest can be thought of as an extension of Bagging. Random Forests were proposed all by Breiman (2001) and as the name implies, they introduce more randomness to the individual trees since one of the aims is to have decorrelated trees. With Bagging, most of the trees are very similar at the root because the most important variables are selected first (see chapter 2). To avoid this happening, a simple modification can be introduced. When building a tree, instead of evaluating all features at each split to find the most important one (based on some purity measure like information gain), a random subset of the features (usually √features) is sampled. This simple modification produces more decorrelated trees and in general, it results in better performance compared to Bagging.

In R, the most famous library that implements Random Forest is..., yes you guessed it: randomForest (Liaw and Wiener, 2002). The following code snippet shows how to fit a Random Forest with 10 trees.

```
library(randomForest)
rf <- randomForest(class = ., trainSet, ntree = 10)
```