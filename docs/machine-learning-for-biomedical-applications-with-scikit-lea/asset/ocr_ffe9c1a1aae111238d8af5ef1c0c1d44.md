# 7.2.8 Boosting

```
@ train model
clf.fit(X,Y)
# report oob score
print("the oob score is ".format(clf.oob_score))
```

Boosting contrasts with bagging and forests in that it tags weak learners serially, one after another. After each model is fit, misclassified examples are identified and given higher importance for subsequent runs.

To see how this works, the toy example is in Fig. 7.8. In this case, the various classes of example are indicated by pluses or minuses. We can see from Fig. 7.8a, perfect supervision would require a nonlinear decision boundary.
7.8b-f simulate the process of boosting. 7.8b an initial axis-aligned decision step is fit by the red box. This correctly classifies two red crosses and all of the minus class. However, three red crosses are misclassified as belonging to the blue class. 7.8c shows how boosting upgrades the misclassified examples in the second round, ensuring that these are correctly classified by the second classifier (shown in Fig. 7.8d); now here three blue are misclassified and so boosted for the third round. The third and final classifier is the ensemble in Fig. 7.8e. This trains an axis-aligned classifier on the vertical axis, correctly classifying the weighted cross and minus class. We can see that, when all three classifiers in the ensemble are combined (with weightings as in Fig. 7.8f) the final result achieves correct classification for all examples.

In this way boosting can learn precise, nonlinear models that significantly improve the accuracy of the ensemble relative to individual base learners. Boosting can be shown to that, even when training performance has saturated, boosting continues to refine predictions by the margins further and further optimizing the losses of each base learner [42]. In other words, it seeks to make the margins between classes bigger and bigger, similarly to the behavior of support vector machines.

# 7.2.9 Adaboot

There are many variants of boosting that differ primarily in the way they combine and weight components during training. Here, we will focus on one of the earliest and best known, Adaboot [15], where we will assume each learner is an axis-aligned decision stump, similar to that in Fig. 7.8.

The Adaboot classifier (Algorithm 7.2) starts by giving all examples in the training set equal weights ($w_i = rac{1}{n}$). Then, for each tree or stump, the algorithm first estimates $p^i$ (which represents normalized weights, or probabilities, for each example).