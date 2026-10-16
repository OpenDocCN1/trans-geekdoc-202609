
from `sklearn.datasets.load_wine` and `sklearn.datasets.load_breast_cancer` will get you started. You can also download numerous datasets from online resources like:

- The UCI Machine Learning Repository, https://archive.ics.uci.edu/ml/datasets.html
- Kaggle, www.kaggle.com/datasets

## Predicting Numerical Values:
Getting Started with Regression

```
In [1]:
# setup
from mlwpy import *
%matplotlib inline
```

### 4.1 A Simple Regression Dataset

Regression is the process of predicting a finely graded numerical value from inputs. To illustrate, we need a simple dataset that has numerical results. sklearn comes with the diabetes dataset that will serve us nicely. The dataset consists of several biometric and demographic measurements. The version included with sklearn has been modified from raw numerical features by subtracting the mean and dividing by the standard deviation of each column. That process is called standardizing or z-scoring the features. We’ll return to the standard deviation later; briefly, it is a measure of how spread out a set of values are.

The net result of standardizing the columns is that each column has a mean of 0 and a standard deviation of 1. We standardize, or otherwise rescale, the data so that differences in feature ranges—heights within 50–100 inches or incomes from $20,000 to $200,000—don’t incur undue weight penalties or benefits just from their scale. We’ll discuss standardization and scaling more in Section 10.3. The categorical values in diabetes were recorded numerically as {0, 1} and then standardized. I mention it to explain why there are negative ages (the mean age is zero after standardizing) and why the sexes are coded, or recorded, as {0.0507, −0.0446} instead of {M, F}.

```
In [2]:
diabetes = datasets.load_diabetes()

tts = skms.train_test_split(diabetes.data,
                            diabetes.target,
                            test_size=.25)

(diabetes_train_ftrs, diabetes_test_ftrs,
 diabetes_train_tgt,  diabetes_test_tgt) = tts
```

We can dress the dataset up with a DataFrame and look at the first few rows:

```
In [3]:
diabetes_df = pd.DataFrame(diabetes.data,
                           columns=diabetes.feature_names)
diabetes_df['target'] = diabetes.target
diabetes_df.head()
```

Out[3]:

|   | age | sex | bmi | bp | s1 | s2 | s3 | s4 | s5 | s6 | target |
|---|-----|-----|-----|----|----|----|----|----|----|----|--------|
| 0 | 0.04 | 0.05 | 0.06 | 0.02 | -0.04 | -0.03 | -0.04 | 0.00 | 0.02 | -0.02 | 151.00 |
| 1 | 0.00 | -0.04 | -0.05 | -0.03 | -0.01 | -0.02 | 0.07 | -0.04 | -0.07 | -0.10 | 75.00 |
| 2 | 0.09 | 0.05 | 0.04 | -0.01 | -0.05 | -0.03 | -0.03 | 0.00 | 0.00 | -0.03 | 141.00 |
| 3 | -0.09 | -0.04 | -0.01 | -0.04 | 0.01 | 0.02 | -0.04 | 0.03 | 0.02 | -0.01 | 206.00 |
| 4 | 0.01 | -0.04 | -0.04 | 0.02 | 0.00 | 0.02 | 0.01 | 0.00 | -0.03 | -0.05 | 135.00 |

Aside from the odd values for seemingly categorical measures like age and sex, two of the other columns are quickly explainable; the rest are more specialized and somewhat underspecified:

- *bmi* is the *body mass index*, computed from height and weight, which is an approximation of body-fat percentage,
- *bp* is the *blood pressure*,
- *s1–s6* are six *blood serum measurements*, and
- *target* is a numerical score measuring the progression of a patient's illness.

As we did with the iris data, we can investigate the bivariate relationships with Seaborn's pairplot. We'll keep just a subset of the measurements for this graphic. The resulting mini-plots are still fairly small, but we can still glance through them and look for overall patterns. We can always redo the pairplot with all the features if we want to zoom out for a more global view.

```
sns.pairplot(diabetes_df[['age', 'sex', 'bmi', 'bp', 's1']],
    size=1.5, hue='sex', plot_kws={'alpha':.2});
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_115_0.png)

## 4.2 Nearest-Neighbors Regression and Summary Statistics

We discussed nearest-neighbor classification in the previous chapter and we came up with the following sequence of steps:

- 1. Describe similarity between pairs of examples.
- 2. Pick several of the most-similar examples.
- 3. Combine the picked examples into a single answer.

As we shift our focus from predicting a class or category to predicting a numerical value, steps 1 and 2 can stay the same. Everything that we said about them still applies. However, when we get to step 3, we have to make adjustments. Instead of simply voting for candidate answers, we now need to take into account the quantities represented by the outputs. To do this, we need to combine the numerical values into a single, representative answer. Fortunately, there are several handy techniques for calculating a single summary value from a set of values. Values computed from a set of data are called statistics. If we are trying to represent—to summarize, if you will—the overall dataset with one of these, we call it a summary statistic. Let's turn our attention to two of these: the median and the mean.

### 4.2.1 Measures of Center: Median and Mean

You may be familiar with the average, also called the arithmetic mean. But I’m going start with a—seemingly!—less math-heavy alternative: the median. The median of a group of numbers is the middle number when that group is written in order. For example, if I have three numbers, listed in order as [1, 8, 10], then 8 is the middle value: there is one number above it and one below. Within a group of numbers, the median has the same count of values below it and above it. To put it another way, if all the numbers have equal weight, regardless of their numerical value, then a scale placed at the median would be balanced (Figure 4.1). Regardless of the biggest value on the right—be it 15 or 40—the median stays the same.

You might be wondering what to do when we have an even number of values, say [1, 2, 3, 4]. The usual way to construct the median is to take the middle two values—the 2 and 3—and take their average, which gives us 2.5. Note that there are still the same number of values, two, above and below this median.

Using the median as a summary statistic has one wonderful property. If I fiddle with the values of the numbers at the start or end of the sorted data, the median stays the same. For example, if my data recorder is fuzzy towards the tails—i.e., values far from the median—and instead of [1, 8, 10], I record [2, 8, 11], my median is the same! This resilience in the face of differing measured values is called robustness. The median is a robust measure of center.

Now, there are scenarios where we care about the actual numbers, not just their in-order positions. The other familiar way of estimating the center is the mean. Whereas the median balances the count of values to the left and right, the mean balances the total distances to the left and right. So, the mean is the value for which `sum(distance(s,mean) for s in smaller)` is equal to `sum(distance(b,mean) for b in bigger)`. The only value that meets this constraint is `mean=sum(d)/len(d)` or, as the mathematicians say, mean = x̄ = Σ_i x_i / n. Referring back to Figure 4.1, if we trade the 15 for a 40, we get a different balance point: the mean has increased because the sum of the values has increased.

The benefit of the mean is that it accounts for the specific numeric values of the numbers: the value 3 is five units below the mean of 8. Compare to the median which

![](img/d94e4cd766940d79abed0bc6ba4e4344_116_0.png)

Figure 4.1 Comparing mean and median with balances.

abstracts distance away in favor of ordering: the value 3 is less than the median 8. The problem with the mean is that if we get an outlier—a rare event near the tails of our data—it can badly skew our computation precisely because the specific value matters.

As an example, here's what happens if we shift one value by “a lot” and recompute the mean and median:

```
In [5]:
values = np.array([1, 3, 5, 8, 11, 13, 15])
print("no outlier")
print(np.mean(values),
      np.median(values))

values_with_outlier = np.array([1, 3, 5, 8, 11, 13, 40])
print("with outlier")
print("%.2f" % np.mean(values_with_outlier),
      np.median(values_with_outlier))
```

no outlier
8.0 8.0
with outlier
11.57 8.0

Beyond the mean and median, there are many possible ways to combine the nearest-neighbor answers into an answer for a test example. One combiner that builds on the idea of the mean is a weighted mean which we discussed in Section 2.5.1. In the nearest-neighbor context, we have a perfect candidate to serve as the weighting factor: the distance from our new example to the neighbor. So, instead of neighbors contributing just their values [4.0, 6.0, 8.0], we can also incorporate the distance from each neighbor to our example. Let’s say those distances are [2.0, 4.0, 4.0], i.e. the second and third training examples are twice as far from our test example as the first one. A simple way to incorporate the distance is to compute a weighted average using

```
In [6]:
distances = np.array([2.0, 4.0, 4.0])
closeness = 1.0 / distances  # element-by-element division
weights = closeness / np.sum(closeness)  # normalize sum to one
weights
```

```
Out[6]:
```
array([0.4, 0.2, 0.2])
```

Or, in mathese:

$$\frac{\frac{1}{\text{distances}}}{\sum\left(\frac{1}{\text{distances}}\right)}$$
