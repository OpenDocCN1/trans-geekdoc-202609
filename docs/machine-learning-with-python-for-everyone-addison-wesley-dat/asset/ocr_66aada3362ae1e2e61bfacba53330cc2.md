![](bbox=[0.22, 0.2, 0.78, 0.48])

We see that we have a lot of similar outcomes. 5-NN appears to win on three folds, while GNB wins on one. The others are visual ties. We would be unable to do this sort of “who won” comparison on stripplots or from calculated means. The stripplot loses the connection to the fold and the mean compresses all the comparative information in the individual folds.

# 5.9 EOC

# 5.9.1 Summary

We have become more sophisticated in the machinery we use to compare different learners: instead of single train-test splits, we make multiple splits. That’s good. We also dove into one of the fundamental theoretical issues in learning: the bias-variance tradeoff. Lastly, we’ve looked at two graphical methods learning curves, complexity curves, and comparing learners across several folds of cross-validation. However, we’re still using only a small toolbox of methods and we’re not really selecting hyperparameters for those methods in a structured way. More to come!

# 5.9.2 Notes

# External Issues in Evaluation

When we build a bridge, we want to make certain that it is safe. We want to ensure that it can handle the weight and wind—hi Tacoma Narrows!—that it will experience. Yet, before we even start construction, someone needs