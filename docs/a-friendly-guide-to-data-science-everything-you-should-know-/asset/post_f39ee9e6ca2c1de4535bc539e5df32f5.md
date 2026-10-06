
# CHAPTER 4 COMING TO COMPLEX CONCLUSIONS: INFERENTIAL STATISTICS AND STATISTICAL TESTING

Note that there are tests that you may need to do to see if your data meets the assumptions required.

Deciding the tests to use in statistics is something that is sometimes difficult at first, but comes with practice. You will probably need to spend some time researching a test to learn more about it any time you are considering one. But one day, your instincts will make it easier.

## Testing Limits and Significance

One important final consideration around statistical testing that we need to remember is that every time we run a test looking for a significant find, we are at risk of encountering a Type I error. It's tempting to test for a bunch of things at once, especially when we don't really know what could be important. For instance, remember what a p-value 0.05 means—basically that 1 time out of 20 (5 out of 100) we could see an apparently significant result that isn't actually significant and just occurred by chance.

If we have ten predictor variables that have no genuine impact and run tests on all of them, it's possible that at least one will come up as significant even though it isn't. We can compute the probability of one variable testing positive out of ten that aren't impactful. Basically, with a significance level of 0.05, that means an insignificant variable has a 0.95 chance to correctly test insignificant, but a 0.05 chance of incorrectly labeled significant. The probability that all tests run for these insignificant variables will accurately test insignificant is 0.95¹⁰, 0.60. With only ten variables tested—a number that doesn't seem too crazy—there's a 40% (1–0.60) chance that at least one will incorrectly test significant. If we increase the number of variables to 20, it's actually likely that at least one will show up as wrongly significant than not (0.95²⁰=0.36, so there's a 64% chance).

This is why some people advocate p-values like 0.01 or looking at other numbers besides the p-value. But even at a 0.01 level, the likelihood of at least one of insignificant variables tested will show up as significant as 10% and 18% if we test two. So it doesn't solve the problem, but it does make it less likely to crop up. There's also a technique called the Bonferroni correction that reduces the chance of a Type I error (a false positive) by adjusting the p-value threshold based on the number of tests.

This is another reason repeating studies is so important for understanding of things. If we test only one in a study at a 0.05 level of significance, there is still a 5% chance that test will yield a significant result even if the variable isn't actually impactful. But if someone else tests the same thing in a different study, the chances of them also finding the variable significant are also 5%, but the likelihood of those things happening is only 0.25% (0.05 * 0.05), clearly much lower.

## Correlation and Covariance

Most people have heard the warning, "Correlation is not causation," even if they don't know exactly what that means. As a concept, correlation is simply a measure of the strength and direction of the relationship between two variables. In positive correlation, when one variable increases, so does the other one. In negative correlation, the variables are inversely related—when one increases, the other decreases. Height and weight of children are positively correlated with each other, and both are correlated with age, whereas the amount of sleep a child needs is negatively correlated with age.

Covariance is a similar concept to correlation, also specifying a relationship between two variables, the difference between them is basically in the range of values they can possibly have and how they are calculated, which we'll see below.

Data analysts and scientists are in the business of explaining why things happen based on data, so it's probably not surprising that understanding relationships between variables is really important. They calculate correlations and covariance frequently for different reasons, which we will go into in later chapters.

## Correlation

Scatterplots are also often created to visually see a correlation, as it's easy to look at a plot and also see that the values are positively correlated when the data points hover around a diagonal line going up from the origin to the top right. Similarly, a negative correlation would have a diagonal line going from the top left to the bottom right. But seeing a correlation in a chart is only valuable to a point—if we want to know if the correlation is statistically significant, we need to quantify it. See Figure 4-4 for different types of correlation.

![](img/df37a23523ff92247f9125691b1edea2_194_0.png)

Figure 4-4. Four views of correlation

The top left is entirely random data with no correlation. The upper right has some correlation, but it's weak because of a lot of random values. The bottom left is strong positive correlation (as one variable increases, so does the other), and the bottom right is strong negative correlation (as one variable increases, the other decreases at a similar rate).

Quantifying correlation first means calculating the correlation coefficient, which is a single value representing the relationship between two specific variables. It's what's called a standardized calculation because it's a product of the measure of the two variables being compared divided by the product of their standard deviations, which makes it unitless and always between -1 and 1. Positive values indicate positive correlation (same direction), and negative indicate negative correlation (opposite direction). Because the value is standardized, it makes easy to compare correlation of completely different datasets. It's common to display several correlation coefficients from a single dataset in a correlation matrix, which displays them in an easy-to-read grid format.

There are several different options for calculating the correlation coefficient, each of which has pros and cons in particular situations. The Pearson correlation coefficient is the most common, and it requires the data to be normally distributed. A couple other correlation measures we won't discuss here but don't require normality is Spearman rank and Kendall rank. Calculating Pearson requires multiplying each X and Y point's difference from the mean and dividing by the product of the X and Y standards.

However you decide to calculate correlation, it's common to display multiple correlations in a correlation matrix. We ran Pearson on the data on sick kids with their height, weight, and age that we looked at in Chapter 2, and Table 4-6 shows the results in a typical view.

**Table 4-6. Correlation matrix of sick child age, height, and weight**

| Age (years) | Height (in) | Weight (Kg) |
|---|---|---|
| Age (years) | 1.000000 | 0.910758 | 0.704657 |
| Height (in) | 0.910758 | 1.000000 | 0.751830 |
| Weight (Kg) | 0.704657 | 0.751830 | 1.000000 |

Each cell shows the correlation of the column and row variables, as they are mirrored across the diagonal. You can also see that the diagonal shows correlations of 1, because a variable is always perfectly correlated itself.

Correlation is one way only, so height is correlated with age exactly as age is correlated with height. Another common way to look at the correlation matrix is a heatmap, which makes the values a little clearer. Figure 4-5 shows a heatmap on this same data.

![](img/df37a23523ff92247f9125691b1edea2_196_0.png)

**Figure 4-5. Correlation heatmap of sick child age, height, and weight data**

These variables are all correlated pretty significantly, the range of colors from low to high show for positive values from 0.7 to 1.0. It's also common for a heatmap to show negatives in one color and positives in another. These are great for a few variables, up to ten or so, but can get unwieldy like a lot of other visualizations.
