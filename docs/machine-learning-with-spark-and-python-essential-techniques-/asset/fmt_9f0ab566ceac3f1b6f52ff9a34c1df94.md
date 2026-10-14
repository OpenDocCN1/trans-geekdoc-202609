
## Figures 6.25–6.27: MSE vs. Number of Trees with Random Attribute Selection

[Figures 6.25](#c06.xhtml#c06-fig-0025) through [6.27](#c06.xhtml#c06-fig-0027) show how the addition of random attribute selection affects the curves of MSE versus the number of trees included in the ensemble.

[Figure 6.25](#c06.xhtml#c06-fig-0025) shows the result when the individual trees are depth 1 trees. The picture is very similar to bagging in that the ensemble doesn't improve performance very much. Depth 1 trees mostly cause bias error, not variance error. Bias can't be averaged away.

![Figure 6.25: MSE versus number of trees for bagging + random attribute selection—Depth 1 trees](images/c06f025.png)

[**Figure 6.25**](#c06.xhtml#R_c06-fig-0025): MSE versus number of trees for bagging + random attribute selection—Depth 1 trees

![Figure 6.26: MSE versus number of trees for bagging + random attribute selection—Depth 5 trees](images/c06f026.png)

[**Figure 6.26**](#c06.xhtml#R_c06-fig-0026): MSE versus number of trees for bagging + random attribute selection—Depth 5 trees

![Figure 6.27: MSE versus number of trees for bagging + random attribute selection—Depth 12 trees](images/c06f027.png)

[**Figure 6.27**](#c06.xhtml#R_c06-fig-0027): MSE versus number of trees for bagging + random attribute selection—Depth 12 trees

[Figure 6.26](#c06.xhtml#c06-fig-0026) shows the MSE curve using depth 5 trees. Now the variance reduction with bagging plus random attribute selection begins to show some performance. The improvement with this combination gets similar performance to other methods demonstrated.

[Figure 6.27](#c06.xhtml#c06-fig-0027) shows that a little more performance is available by using depth—12 trees.

### Random Forests Summary

Random forests is a combination of bagging and a random attribute selection modification to the binary tree base learners. These differences may not seem substantial, but they give random forests different performance characteristics from bagging and gradient boosting. Some results suggest that random forest has an advantage with wide sparse attribute spaces such as occur in text mining problems. Random forest is a little easier to parallelize than gradient boosting because the individual base learners can be trained independently of one another, whereas with gradient boosting each base learner needs the results from the ones before it.

Differences like these mean that you may want to try both random forests in addition to gradient boosting, if you need to wring as much performance as possible from your data.

## Summary

This chapter gave you some background on basic ensemble algorithms. It explained that ensemble methods consisted of a hierarchy of two algorithms. Ensemble methods train hundreds or thousands of the low-level algorithms called *base learners*. The higher-level algorithm controls the training of the base learners in order that their models turn out somewhat independent from one another so that combining them will reduce the variance of the combination. For bagging, the higher-level algorithm is to take bootstrap samples of the training set and train base learners on these samples. For gradient boosting, the higher-level algorithm at each stage takes a sample of the input data and trains a base learner on it. With gradient boosting, the target used to train each base learner is the error from the accumulation of all the earlier base learners. Random forest is a combination of bagging as a higher-level algorithm and base learners that are modified versions of binary decision trees. The base learners with random forests are binary trees where, at each node, the split point decisions are restricted to a random sample of the available attributes instead of considering all the attributes in each split. The packages available for doing gradient boosting in Python permit you to use random forest base learners with gradient boosting. You will see that use in the next chapter, "Building Ensemble Methods with Python."

The chapter coded each of the high-level algorithms and showed a facsimile of the random forest's base learners. The purpose for coding these is for you to gain an understanding of the mechanisms at work in each of the algorithms. The idea behind that is that you will better understand the options, input variables, nominal starting values, and so on for the Python packages for these algorithms. The next chapter uses available Python packages to generate solutions to some of the problems you've seen solved by penalized linear regression.

## References

1.  Panda Biswanath, Joshua S. Herbach, Sugato Basu, and Roberto J. Bayardo. (2009). "PLANET: Massively Parallel Learning of Tree Ensembles with MapReduce." *Proceedings of the 35th International Conference on Very Large Data Bases*. Retrieved from `http://research.google.com/pubs/pub36296.html`.

2.  Leo Breiman. (September, 1994). "Bagging Predictors." *Technical Report No. 421*. Department of Statistics, UC Berkeley. Retrieved from `http://statistics.berkeley.edu/sites/default/files/tech-reports/421.pdf`.

3.  Leo Breiman. (2001). "Random Forests. *Machine Learning*," *45*:5–32. Retrieved from `https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf`.

4.  J.H. Friedman. (2001). "Greedy Function Approximation: A Gradient Boosting Machine." *Annals of Statistics*, *29*(5):1189–1232. Retrieved from `http://statweb.stanford.edu/~jhf/ftp/trebst.pdf`.

5.  J.H. Friedman. (2002). "Stochastic Gradient Boosting." *Computational Statistics and Data Analysis*, *38*(4):367–378. Retrieved from `http://statweb.stanford.edu/~jhf/ftp/stobst.pdf`.

# Chapter 7: Building Ensemble Models with Python

This chapter uses several available Python packages to build predictive models using the ensemble algorithms that you saw in [Chapter 6](#c06.xhtml), "Ensemble Methods." The problems used to illustrate them were introduced in [Chapter 2](#c02.xhtml), "Understand the Problem by Understanding the Data." You saw in [Chapter 5](#c05.xhtml), "Building Predictive Models Using Penalized Linear Methods," how to build predictive models for them using penalized linear regression. This chapter uses ensemble methods to solve the same problems. That will enable you to compare the algorithms and the available Python packages in terms of how easy the packages are to use, what kinds of accuracy is achievable with ensemble methods versus penalized linear regression, how the training times compare, and so on. The end of the chapter shows some summary comparisons of the various algorithms with which you've become familiar.

## Solving Regression Problems with Python Ensemble Packages

The next several sections demonstrate the application of available Python packages for building ensemble models. You will see the things you learned in [Chapter 6](#c06.xhtml) in action. The methods explained in [Chapter 6](#c06.xhtml) will be used on the series of problems explored in [Chapter 2](#c02.xhtml), and then used to demonstrate the application of penalized linear regression in [Chapter 5](#c05.xhtml). Using the same problems makes it possible to compare the algorithms covered here along several dimensions, including raw performance, training time, and ease of use. The chapter also covers the available Python packages. The background given in [Chapter 6](#c06.xhtml) helps you understand why the Python packages are structured the way they are and helps you see how to get the most from these methods. This section goes through a variety of different problem types, beginning with regression problems.

### Using Gradient Boosting to Predict Wine Taste
