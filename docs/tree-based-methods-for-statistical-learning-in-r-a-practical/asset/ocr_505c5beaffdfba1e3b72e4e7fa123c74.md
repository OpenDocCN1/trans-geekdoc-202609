![](bbox=[0.16, 0.09, 0.48, 0.33])

![](bbox=[0.53, 0.09, 0.86, 0.33])

FIGURE 5.1: Simulated sine wave example ($N = 500$). Left: a single (overgrown) regression tree. Right: a bagged ensemble of $B = 1000$ overgrown regression trees whose predictions have been averaged together; here each tree was induced from a different bootstrap sample of the original data points. The individual tree is too complex (i.e., low bias and high variance) but averaging many such trees together results in a more stable prediction and smoother fit.

et al., 2004]. An improved bagging strategy specific to decision trees, called random forest, is the topic of Chapter 7.

The (optional) OOB data in step 2) (b) of Algorithm 5.1 will be discussed in Section 7.3, so just ignore it for now. The recommended default value for $n_{min}$ (the minimum size of any terminal node in a tree) depends on the type of response variable:

```
n_{min} = \begin{cases} 1, & \text{for classification} \\ 5, & \text{for regression} \end{cases}.
```

Step 4) of Algorithm 5.1 mentions classification via voting. By voting, I mean that each tree makes a classification (i.e., casts a vote), and the ensemble classification is obtained by a majority vote (or plurality in the multiclass setting), with ties\(^\text{b}\) typically handled at random. Class probability estimates for categorical outcomes can also be obtained from bagged tree ensembles and a discussion of different approaches is deferred to Section 7.2.1; often, the class proportions from each tree are just averaged across all the trees in the bagged ensemble (similar to regression).