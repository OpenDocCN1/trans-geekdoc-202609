get boosted. The second classifier therefore does a better job on these instances, and so on. The plot on the right represents the same sequence of predictors except that the learning rate is halved (i.e., the misclassified instance weights are boosted half as much at every iteration). As you can see, this sequential learning technique has many similarities with Gradient Descent, except of tweaking a single predictor’s parameters to minimize a cost function, AdaBoost adds predictors to the ensemble, gradually making it better.

![](bbox=[0.142, 0.23, 0.857, 0.413])

Figure 7-8. Decision boundaries of consecutive predictors

Once all predictors are trained, the ensemble makes predictions very much like bagging or pasting, except that predictors have different weights depending on their overall accuracy over the weighted training set.

> There is one important drawback to this sequential learning technique: it cannot be parallelized (or only partially), since each predictor can only be trained after the previous predictor has been trained and evaluated. As a result, it does not scale well as bagging or pasting.

Let’s take a closer look at the AdaBoost algorithm. Each instance weight $w^{(i)}$ is initially set to $\frac{1}{m}$. A first predictor is trained and its weighted error rate $r_1$ is computed on the training set; see Equation 7-1.

Equation 7-1. Weighted error rate of the $j^{th}$ predictor

```
$r_j = \frac{\sum_{i=1}^{m} w^{(i)} [y^{(i)} \neq \hat{y}^{(i)}]}{\sum_{i=1}^{m} w^{(i)} where $\hat{y}^{(i)}$ is the $j^{th}$ predictor’s prediction for the $i^{th}$ instance.$
```