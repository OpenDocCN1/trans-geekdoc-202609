# Examples

We will use RIPPER for the examples.

The RIPPER algorithm does not find any rule in the classification task for cervical cancer.

When we use RIPPER on the regression task to predict bike counts some rules are found. Since RIPPER only works
for classification, the bike counts must be turned into a categorical outcome. I achieved this by cutting the bike counts
into the quartiles. For example (4548, 5956) is the interval covering predicted bike counts between 4548 and 5956.
The following table shows the decision list of learned rules.

# rules

```
(days_since_2011 >= 438) and (temp >= 17) and (temp <= 27) and (hum <= 67) => cnt=(5956,8714]
(days_since_2011 >= 443) and (temp >= 12) and (weathersit = GOOD) and (hum >= 59) => cnt=(5956,8714]
(days_since_2011 >= 441) and (windspeed <= 10) and (temp >= 13) => cnt=(5956,8714]
(temp >= 12) and (hum <= 68) and (days_since_2011 >= 551) => cnt=(5956,8714]
(days_since_2011 >= 100) and (days_since_2011 <= 434) and (hum <= 72) and (workingday = WORKING DAY)
=> cnt=(3152,4548]
(days_since_2011 >= 106) and (days_since_2011 <= 323) => cnt=(3152,4548]
=> cnt=[22,3152]
```

The interpretation is simple: If the conditions apply, we predict the interval on the right hand side for the number of
bikes. The last rule is the default rule that applies when none of the other rules apply to an instance. To predict a new
instance, start at the top of the list and check whether a rule applies. When a condition matches, then the right hand
side of the rule is the prediction for this instance. The default rule ensures that there is always a prediction.

# 4.5.3 Bayesian Rule Lists

In this section, I will show you another approach to learning a decision list, which follows this rough recipe:

+   1. Pre-mine frequent patterns from the data that can be used as conditions for the decision rules.
+   2. Learn a decision list from a selection of the pre-mined rules.

A specific approach using this recipe is called Bayesian Rule Lists (Letham et. al, 2015)20 or BRL for short. BRL uses
Bayesian statistics to learn decision lists from frequent patterns which are pre-mined with the FP-tree algorithm
(Borgelt 2005)21

But let us start slowly with the first step of BRL.

# Pre-mining of frequent patterns

A frequent pattern is the frequent (co-)occurrence of feature values. As a pre-processing step for the BRL algorithm,
we use the features (we do not need the target outcome in this step) and extract frequently occurring patterns from
them. A pattern can be a single feature value such as size=medium or a combination of feature values such as
size=medium AND location=bad.

The frequency of a pattern is measured with its support in the dataset:

```
|{Support(x_j=A)=frac{1}n{sum_{i=1}^n I(x^{(i)}{j}=A)}}|
```

where A is the feature value, n the number of data points in the dataset and I the indicator function that returns 1 if the
feature (x_j) of the instance i has level A otherwise 0. In a dataset of house values, if 20% of houses have no balcony
and 80% have one or more, then the support for the pattern balcony=0 is 20%. Support can also be measured for
combinations of feature values, for example for balcony=0 AND pets=allowed.