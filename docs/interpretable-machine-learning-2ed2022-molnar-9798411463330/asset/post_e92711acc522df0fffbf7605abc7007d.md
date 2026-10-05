
truths can be addressed either by reporting all counterfactual explanations or by having a criterion to evaluate counterfactuals and select the best one.

Speaking of criteria, how do we define a good counterfactual explanation? First, the user of a counterfactual explanation defines a relevant change in the prediction of an instance (= the alternative reality). An obvious first requirement is that a counterfactual instance produces the predefined prediction as closely as possible. It is not always possible to find a counterfactual. For example, in a classification setting with two classes, a rare class and a frequent class, the model might always classify an instance as the frequent class. Changing the feature values so that the predicted label would flip from the frequent class to the rare class might be impossible. We want to relax the requirement that the prediction of the counterfactual must match the predicted outcome exactly. In the classification example, we could look for a counterfactual where the probability of the rare class is increased to 10% instead of the current 2%. The question then is, what are the minimal changes in the features so that the predicted probability changes from 2% to 10% (or close to 10%)?

Another quality is that a counterfactual should be as similar as possible to the instance regarded. The distance between two instances can be measured, for example, with the Manhattan distance or the Gower distance if we have discrete and continuous features. The counterfactual should not only be close to the original instance, but also change as few features as possible. To measure how much a counterfactual explanation is in this metric, we can simply count the number of changed features or, in mathematical terms, measure the $l_0$ norm between counterfactual and actual instance.

Third, it is often desirable to generate multiple diverse counterfactual explanations so the decision-subject gets access to multiple ways of generating a different outcome. For instance, continuing a loan, one counterfactual explanation might suggest only double the income to get a loan, while another counterfactual might suggest shifting to a nearby city and increasing the income by a small amount to get a loan. It could be noted that the first counterfactual might be possible for some, the latter might be more actionable for others. Thus, besides providing a decision-subject with different ways to get the desired outcome, diversity also enables “diverse” individuals to alter the features that are convenient for them.

The last requirement is that a counterfactual instance should have feature values that are likely. It would not make sense to generate a counterfactual explanation for the rent example where the size of an apartment is negative or the number of rooms is set to 200. It is even better when the counterfactual is likely according to the joint distribution of the data, for example, an apartment with 10 rooms and 20 $m^2$ should not be regarded as a counterfactual explanation. Ideally, if the size of square meters is increased, an increase in the number of rooms should also be proposed.

## 8.3 COUNTERFACTUAL EXPLANATIONS

### 8.3.1 Generating Counterfactual Explanations

A simple and naive approach to generating counterfactual explanations is searching by trial and error. This approach involves randomly changing feature values of the instance of interest and stopping when the desired output is predicted. Like the example where Anna tried to find a version of her apartment where she could charge more. But there are better approaches than trial and error. First, we define a loss function based on the criteria mentioned above. This loss takes as input the instance of interest, a counterfactual and the desired (counterfactual) outcome. Then, we can find the counterfactual explanation that minimizes this loss using an optimization algorithm. Many methods proceed in this way, but differ in their definition of the loss function and optimization method.

In the following, we focus on two of them: first, the one by Wachter et al. (2017)¹² introduced counterfactual explanation as an interpretation method and, the second one by Dandl et al. (2020)¹³ that takes into account all four criteria mentioned above.

### 8.3.1 Method by Wachter et al.

Wachter suggests minimizing the following loss:

```
$L(x, x', \lambda) = \lambda \cdot (\hat{f}(x') - y)^2 + d(x, x')$
```

The first term is the quadratic distance which uses the model prediction for the counterfactual x' and the desired outcome y, which the user must define in advance. The second term is the distance between the instance x to be explained and the counterfactual x'. The loss measures how far the predicted outcome of the counterfactual is from the predefined outcome and how far the counterfactual is from the instance of interest. The distance d is defined as the Manhattan distance with the inverse mean absolute deviation (MAD) of each feature.

```
$d(x, x') = \sum_{j=1}^{p} \frac{|x_j - x'_j|}{MAD_j}$
```

The total distance is the sum of all p feature-wise distances, which are the absolute differences of feature values between instance x and counterfactual x'. The feature-wise distances are scaled by the inverse of the mean absolute deviation of feature j over the dataset defined as:

```
$MAD_j = median_{i\in\{1,...,n\}}(|x_{ij}| - median_{i\in\{1,...,n\}}(|x_{ij}|))$
```

¹² Wachter, Sandra, Brent Mitteausch, Martin Binder, and Chris Russell. "Counterfactual explanations without opening the black box: Automated decisions and the GDPR." (2017)  
¹³ Dandl, Susanne, Christoph Molnar, Martin Binder, Bernd Bischl. "Multi-objective counterfactual explanations." In: Back T. et al. (eds) Parallel Problem Solving from Nature – PPSN XVI PPSN 2020. Lecture Notes in Computer Science, Springer. Cham (2020).

## CHAPTER 8 LOCAL MODEL-AGNOSTIC METHODS

The median of a vector is the value at which half of the vector values are greater and the other half smaller. MAD is the equivalent of a feature, but instead of using the mean as the center and summing over the square distances, we use the median as the center and sum over the absolute distances. The proposed distance function has the advantage over the Euclidean distance that it is more robust to outliers. Scaling with the MAD is necessary to bring all features to the same scale - it should not matter whether you measure the size of an apartment in square meters or square feet.

The parameter $\lambda$ balances the distance in prediction (first term) against the distance in feature values (second term). A higher value of $\lambda$ means that we prefer counterfactuals close to the desired outcome y'; a lower value means that we prefer counterfactuals that are very similar to x in the feature values. The authors of the method suggest instead selecting a value for $\lambda$ to select a tolerance $\epsilon$ for how far from y' the prediction of the counterfactual is allowed to be. This can be written as:

> $|f(x') - y| \le \epsilon$

To minimize this loss, any suitable optimization algorithm can be used, such as Nelder-Mead. If you have access to the gradients of the machine learning model, you can use gradient-based methods like ADAM. The instance x to be explained, the desired outcome y' and the tolerance parameter $\epsilon$ must be set in advance. The loss is minimized for x' and the (locally) optimal counterfactual x' returned while increasing $\lambda$ until a sufficiently close solution is found (= within the tolerance):

```
arg min max_{\lambda} L(x, x', \lambda).
```

Overall, the recipe for producing the counterfactuals is:

1. Select an instance x to be explained, the desired outcome y', a tolerance $\epsilon$ and a (low) initial value for $\lambda$.
2. Sample a random instance as initial counterfactual.
3. Optimize the loss with the initially sampled counterfactual as starting point.
4. While $|f(x') - y| > \epsilon$:
    * Increase $\lambda$
    * Optimize the loss with the current counterfactual as starting point.
    * Return the counterfactual that minimizes the loss.
5. Repeat steps 2-4 and return the list of counterfactuals or the one that minimizes the loss.
