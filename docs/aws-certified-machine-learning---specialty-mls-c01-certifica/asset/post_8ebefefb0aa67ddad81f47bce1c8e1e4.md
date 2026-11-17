

Discretization is the process of transforming a continuous variable into discrete or nominal attributes. These continuous values can be discretized by multiple strategies, such as **equal-width** and **equal-frequency**.

An equal-width strategy will split your data across multiple bins of the same width. Equal-frequency will split your data across multiple bins with the same number of frequencies.

Look at the following example. Suppose you have the following list containing 16 numbers: 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 90. As you can see, this list ranges between 10 and 90. Assuming you want to create four bins using an equal-width strategy, you could come up with the following bins:

- Bin >= 10 <= 30: 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24
- Bin > 30 <= 50:
- Bin > 50 <= 70:
- Bin > 71 <= 90: 90

In this case, the width of each bin is the same (20 units), but the observations are not equally distributed. Now, the next example simulates an equal-frequency strategy:

- Bin >= 10 <= 13: 10, 11, 12, 13
- Bin > 13 <= 17: 14, 15, 16, 17
- Bin > 17 <= 21: 18, 19, 20, 21
- Bin > 21 <= 90: 22, 23, 24, 90

In this case, all the bins have the same frequency of observations, although they have been built with different bin widths to make that possible.

Once you have computed your bins, you should be wondering what's next, right? Here, you have some options:

- You can name your bins and use them as a nominal feature on your model! Of course, as a nominal variable, you should think about applying one-hot encoding before feeding an ML model with this data.
- You might want to order your bins and use them as an ordinal feature.
- Maybe you want to remove some noise from your feature by averaging the minimum and maximum values of each bin and using that value as your transformed feature.

Take a look at Table 4.8 to understand these approaches using our equal-frequency example:

| Ordinal value | Bin | Transforming to a nominal feature | Transforming to an ordinal feature | Removing noise |
|---|---|---|---|---|
| 10 | Bin >= 10 <= 13 | Bin A | 1 | 11.5 |
| 11 | Bin >= 10 <= 13 | Bin A | 1 | 11.5 |
| 12 | Bin >= 10 <= 13 | Bin A | 1 | 11.5 |
| 13 | Bin >= 10 <= 13 | Bin A | 1 | 11.5 |
| 14 | Bin > 13 <= 17 | Bin B | 2 | 15.5 |
| 15 | Bin > 13 <= 17 | Bin B | 2 | 15.5 |
| 16 | Bin > 13 <= 17 | Bin B | 2 | 15.5 |
| 17 | Bin > 13 <= 17 | Bin B | 2 | 15.5 |
| 18 | Bin > 17 <= 21 | Bin C | 3 | 19.5 |
| 19 | Bin > 17 <= 21 | Bin C | 3 | 19.5 |
| 20 | Bin > 17 <= 21 | Bin C | 3 | 19.5 |
| 21 | Bin > 17 <= 21 | Bin C | 3 | 19.5 |
| 22 | Bin > 21 <= 90 | Bin D | 4 | 55.5 |
| 23 | Bin > 21 <= 90 | Bin D | 4 | 55.5 |
| 24 | Bin > 21 <= 90 | Bin D | 4 | 55.5 |
| 90 | Bin > 21 <= 90 | Bin D | 4 | 55.5 |

Table 4.8 – Different approaches to working with bins and discretization

Again, playing with different binning strategies will give you different results and you should analyze/test the best approach for your dataset. There is no standard answer here – it is all about data exploration!

## Applying other types of numerical transformations

Normalization and standardization rely on your training data to fit their parameters: minimum and maximum values, in the case of normalization, and mean and standard deviation in the case of standard scaling. This also means you must fit those parameters using *only* your training data and never the testing data.

However, there are other types of numerical transformations that do not require parameters from training data to be applied. These types of transformations rely purely on mathematical computations. For example, one of these transformations is known as logarithmic transformation. This is a very common type of transformation in ML models and is especially beneficial for skewed features. If you don’t know what a skewed distribution is, take a look at *Figure 4.5*.

![](img/87c29232224b00f5a8bba6a66a391700_106_0.png)

### Figure 4.5 – Skewed distributions

In the middle, you have a normal distribution (or Gaussian distribution). On the left- and right-hand sides, you have skewed distributions. In terms of skewed features, there will be some values far away from the mean in one single direction (either left or right). Such behavior will push both the median and mean values of this distribution in the same direction, that of the long tail you can see in Figure 4.5.

One very clear example of data that used to be skewed is the annual salaries of a particular group of professionals in a given region, such as senior data scientists working in Florida, US. This type of variable usually has most of its values close to the others (because people used to earn an average salary) and just has a few very high values (because a small group of people makes much more money than others).

Hopefully, you can now easily understand why the mean and median values will move to the tail direction, right? The big salaries will push them in that direction.

Alright, but why will a logarithmic transformation be beneficial for this type of feature? The answer to this question can be explained by the math behind it:

```
log(x^n) = nlog(x)
```

### Figure 4.6 – Logarithmic properties

Computing the log of a number is the inverse of the exponential function. Log transformation will then reduce the scale of your number according to a given base (such as base 2, base 10, or base e, in the case of a natural logarithm). Looking at the salary distribution from the previous example, you would bring all those numbers down so that the higher the number, the higher the reduction; however, you would do this in a log scale and not in a linear fashion. Such behavior will remove the outliers of this distribution (making it closer to a normal distribution), which is beneficial for many ML algorithms, such as linear regression. Table 4.9 shows you some of the differences when transforming a number in a linear scale versus a log scale:

| Ordinal value | Linear scale (normalization) | Log scale (base 10) |
|---|---|---|
| 10 | 0.0001 | 1 |
| 1,000 | 0.01 | 3 |
| 10,000 | 0.1 | 4 |
| 100,000 | 1 | 5 |

Table 4.9 – Differences between linear transformation and log transformation

As you can see, the linear transformation kept the original magnitude of the data (you can still see outliers, but in another scale), while the log transformation removed those differences of magnitude and still kept the order of the values.

Would you be able to think about another type of mathematical transformation that follows the same behavior of log (making the distribution closer to Gaussian)? OK, here you have another: square root. Take the square root of those numbers shown in Table 4.9 and see yourself!

Now, pay attention to this: both log and square root belong to a set of transformations known as power transformations, and there is a very popular method, which is likely to be mentioned on your AWS exam, that can perform a range of power transformations like those you have seen. This method was proposed by George Box and David Cox and its name is Box-Cox.

## IMPORTANT NOTE

During your exam, if you see questions about the Box-Cox transformation, remember that it is a method that can perform many power transformations (according to a lambda parameter), and its end goal is to make the original distribution closer to a normal distribution.

Just to conclude this discussion regarding why mathematical transformations can really make a difference to ML models, here is an example of exponential transformations.

Suppose you have a set of data points, such as those on the left-hand side of Figure 4.7. Your goal is to draw a line that will perfectly split blue and red points. Just by looking at the original data (again, on the left-hand side), you know that your best guess for performing this linear task would be the one you can see in the same figure. However, the science (not magic) happens on the right-hand side of

