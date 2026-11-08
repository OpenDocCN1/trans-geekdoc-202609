
![Fig. 5.5 Effect of varying the probability threshold: (A) error curve; (B) cost curve.](images/F000066f05-05-9780443158889.jpg)

Fig. 5.5 Effect of varying the probability threshold: (A) error curve; (B) cost curve.

The line marked A represents the error rate of a particular classifier. If you calculate its performance on a certain test set, its FP rate `fp` is its expected error on a subsample of the test set that contains only negative examples (`P(+)` = 0), and its FN rate `fn` is the error on a subsample that contains only positive examples (`P(+)` = 1). These are the values of the intercepts at the left and right, respectively. You can see immediately from the plot that if `P(+)` is smaller than about 0.2, predictor A is outperformed by the extreme classifier that always predicts −, while if it is larger than about 0.65, the other extreme classifier is better.

So far we have not taken costs into account; rather, we have used the default cost matrix in which all errors cost the same. Cost curves, which do take cost into account, look very similar—very similar indeed—but the axes are different. [Fig. 5.5B](#Ch005_165-207_B9780443158889000066.xhtml#f0030) shows a cost curve for the same classifier A (note that the vertical scale has been enlarged, for convenience, and ignore the gray lines for now). It plots the expected cost of using A against the probability cost function, which is a distorted version of `P(+)` that retains the same extremes: zero when `P(+)` = 0 and one when `P(+)` = 1. Denote by `C[+|-]` the cost of predicting + when the instance is actually −, and the reverse by `C[-|+]`. Then the axes of [Fig. 5.5B](#Ch005_165-207_B9780443158889000066.xhtml#f0030) are

Normalized expected cost = `fn × P[C](+) + fp × (1−P[C](+))`

![Equation](images/F000066si84.png)

$\\mathit{Probability\\ cost\\ function}P\_{C}\\left( + \\right) = \\frac{P\\left( + \\right)C\\left\\lbrack - | + \\right\\rbrack}{P\\left( + \\right)C\\left\\lbrack - | + \\right\\rbrack + P\\left( - \\right)C\\left\\lbrack + | - \\right\\rbrack}.$

![Equation](images/F000066si85.png)

We are assuming here that correct predictions have no cost: `C[+|+]` = `C[-|-]` = 0. If that is not the case the formulas are a little more complex.

The maximum value that the normalized expected cost can have is 1 (i.e., why it is “normalized”). One nice thing about cost curves is that the extreme cost values at the left and right sides of the graph are `fp` and `fn`, just as they are for the error curve, so you can draw the cost curve for any classifier very easily.

[Fig. 5.5B](#Ch005_165-207_B9780443158889000066.xhtml#f0030) also shows classifier B, whose expected cost remains the same across the range—that is, its FP and FN rates are equal. As you can see, it outperforms classifier A if the probability cost function exceeds about 0.45, and knowing the costs we could easily work out what this corresponds to in terms of class distribution. In situations that involve different class distributions, cost curves make it easy to tell when one classifier will outperform another.

In what circumstances might this be useful? To return to our example of predicting when cows will be in estrus, their 30-day cycle, or 1/30 prior probability, is unlikely to vary greatly (barring a genetic cataclysm!). But a particular herd may have different proportions of cows that are likely to reach estrus in any given week, perhaps synchronized with—Who knows?—the phase of the moon. Then different classifiers would be appropriate at different times. In the oil spill example, different batches of data may have different spill probabilities. In these situations, cost curves can help to show which classifier to use when.

Each point on a lift chart, ROC curve, or recall-precision curve represents a classifier, typically obtained by using different threshold values for a method such as `Naïve Bayes`. Cost curves represent each classifier by a straight line, and a suite of classifiers will sweep out a curved envelope whose lower limit shows how well that type of classifier can do if the parameter is well chosen. [Fig. 5.5B](#Ch005_165-207_B9780443158889000066.xhtml#f0030) indicates this with a few gray lines. If the process were continued, it would sweep out the dotted parabolic curve.

The operating region of classifier B ranges from a probability cost value of about 0.25 to a value of about 0.75. Outside this region, classifier B is outperformed by the trivial classifiers represented by dashed lines. Suppose we decide to use classifier B within this range and the appropriate trivial classifier below and above it. All points on the parabola are certainly better than this scheme. But how much better? It is hard to answer such questions from an ROC curve, but the cost curve makes them easy. The performance difference is negligible if the probability cost value is around 0.5, and below a value of about 0.2 and above 0.8 it is barely perceptible. The greatest difference occurs at probability cost values of 0.25 and 0.75 and is about 0.04, or 4% of the maximum possible cost figure.

## 5.9 Evaluating Numeric Prediction

All the evaluation measures we have described pertain to classification rather than numeric prediction. The basic principles—using an independent test set rather than the training set for performance evaluation, the holdout method, cross-validation—apply equally well to numeric prediction. But the basic quality measure offered by the error rate is no longer appropriate; errors are not simply present or absent, they come in different sizes.

Several alternative measures, some of which are summarized in [Table 5.8](#Ch005_165-207_B9780443158889000066.xhtml#t0045), can be used to evaluate the success of numeric prediction. The predicted values on the test instances are `p[1]`, `p[2]`, …, `pn`; the actual values are `a[1]`, `a[2]`, …, `an`. Notice that `pi` means something very different here to what it did in the last section. There it was the probability that a particular prediction was in the `i`th class; here it refers to the numerical value of the prediction for the `i`th test instance.

Table 5.8

Performance Measures for Numeric Prediction
