are built based on different sets of features. The user chooses how many features to retain and then the algorithm selects these features randomly at each try.

Hence, it becomes simple to grow many different trees and the ensemble is simply a **weighted combination** of all trees. Usually, equal weights are used, which is an agnostic and robust choice. We illustrate the idea of simple combinations (also referred to as bagging) in Figure 6.4 below. The terminal prediction is simply the mean of all intermediate predictions.

![](bbox=[0.136, 0.194, 0.88, 0.342])

FIGURE 6.4: Combining tree outputs via random forests.

Random forests, because they are built on the idea of bootstrapping, are more efficient than simple trees. They are used by Ballings et al. (2015), Patel et al. (2015a), Krauss et al. (2017), and Huck (2019) and they are shown to perform very well in these papers. The original theoretical properties of random forests are demonstrated in Breiman (2001) for classification trees. In classification exercises, the decision is taken by a vote: each tree votes for a particular class and the class with the most votes wins (with possible random picks in case of ties). Breiman (2001) defines the margin function as

```
$$mg = M^{-1} \sum_{m=1}^M 1_{\{h_m(\mathbf{x})=y\}} - \max_{j \neq y} \left( M^{-1} \sum_{m=1}^M 1_{\{h_m(\mathbf{x})=j\}} \right),$$
```

where the left part is the average number of votes based on the \(M\) trees \(h_m\) for the correct class (the models \(h_m\) based on **x** matches the data value \(y\)). The right part is the maximum average for any other class. The margin reflects the confidence that the aggregate forest will classify properly. The generalization error is the probability that \(mg\) is strictly negative. Breiman (2001) shows that the inaccuracy of the aggregation (as measured by generalization error) is bounded by \(\bar{\rho}(1-s^2)/s^2\), where

+   - \(s\) is the strength (average quality\(^2\)) of the individual classifiers and
+   - \(\bar{\rho}\) is the average correlation between the learners.

Notably, Breiman (2001) also shows that as the number of trees grows to infinity, the inaccuracy converges to some finite number which explains why random forests are not prone to overfitting.

While the original paper of Breiman (2001) is dedicated to classification models, many articles have since then tackled the problem of regression trees. We refer the interested reader to Biau (2012) and Scornet et al. (2015). Finally, further results on classifying ensembles can be obtained in Biau et al. (2008) and we mention the short survey paper by Denis et al. (2014) which sums up recent results in this field.

\(^2\)The strength is measured as the average margin, i.e. the average of \(mg\) when there is only one tree.