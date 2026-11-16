FIGURE 4.7: The logistic regression model finds the correct decision boundary between malignant and benign depending on tumor size. The line is the logistic function shifted and squeezed to fit the data.

Classification works better with logistic regression and we can use 0.5 as a threshold in both cases. The inclusion of additional points does not really affect the estimated curve.

# 4.2.3 Interpretation

The interpretation of the weights in logistic regression differs from the interpretation of the weights in linear regression, since the outcome in logistic regression is a probability between 0 and 1. The weights do not influence the probability linearly any longer. The weighted sum is transformed by the logistic function to a probability. Therefore we need to reformulate the equation for the interpretation so that only the linear term is on the right side of the formula.

```
\( \log(\frac{P(y=1)}{1-P(y=1)})=\log(\frac{P(y=1)}{P(y=0)})=\beta_0+\beta_1x_1+\dots+\beta_px_p \)
```

We call the term in the log() function "odds" (probability of event divided by probability of no event) and wrapped in the logarithm it is called log odds.

This formula shows that the logistic regression model is a linear model for the log odds. Great! That does not sound helpful! With a little shuffling of the terms, you can figure out how the prediction changes when one of the features (x_j) is changed by 1 unit. To do this, we can first apply the exp() function to both sides of the equation:

```
\( \frac{P(y=1)}{1-P(y=1)}=\text{odds}=\exp(\beta_0+\beta_1x_1+\dots+\beta_px_p) \)
```

Then we compare what happens when we increase one of the feature values by 1. But instead of looking at the difference, we look at the ratio of the two predictions:

```
\( \frac{\text{odds}_{x_{j+1}}}{\text{odds}}=\frac{\exp(\beta_0+\beta_1x_1+\dots+\beta_j(x_j+1)+\dots+\beta_px_p)}{\exp(\beta_0+\beta_1x_1+\dots+\beta_jx_j+\dots+\beta_px_p)} \)
```

We apply the following rule:

```
\( \frac{\exp(a)}{\exp(b)}=\exp(a-b) \)
```

And we remove many terms:

```
\( \frac{\text{odds}_{x_{j+1}}}{\text{odds}}=\exp(\beta_j(x_j+1)-\beta_jx_j)=\exp(\beta_j) \)
```

In the end, we have something as simple as exp() of a feature weight. A change in a feature by one unit changes the odds ratio (multiplicative) by a factor of \( \exp(\beta_j) \). We could also interpret it this way: A change in (x_j) by one unit increases the log odds ratio by the value of the corresponding weight. Most people interpret the odds ratio because thinking about the log() of something is known to be hard on the brain. Interpreting the odds ratio already requires some getting used to. For example, if you have odds of 2, it means that the probability for y=1 is twice as high as y=0. If you have a weight (= log odds ratio) of 0.7, then increasing the respective feature by one unit multiplies the odds by exp(0.7) (approximately 2) and the odds change to 4. But usually you do not deal with the odds and interpret the weights only as the odds ratios. Because for actually calculating the odds you would need to set a value for each feature, which only makes sense if you want to look at one specific instance of your dataset.

These are the interpretations for the logistic regression model with different feature types:

+   - Numerical feature: If you increase the value of feature (x_j) by one unit, the estimated odds change by a factor of \( \exp(\beta_j) \)
+   - Binary categorical feature: One of the two values of the feature is the reference category (in some languages, the one encoded in 0). Changing the feature (x_j) from the reference category to the other category