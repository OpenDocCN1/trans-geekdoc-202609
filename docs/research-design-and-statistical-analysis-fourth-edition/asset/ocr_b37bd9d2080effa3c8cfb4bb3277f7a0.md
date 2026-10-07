# 46 Research Design and Statistical Analysis

More extensive discussions of views of plotting data and resistant statistics may be found in many sources. In particular, we recommend the three volumes edited by Hoaglin et al. (1983; Hoaglin, Mosteller & Tukey, 1991). They provide a clear presentation of many topics beyond the scope of this book, as well as further discussion and examples of topics we have introduced. Other suggestions of possible ways of plotting data, and references to useful sources, may be found in the report of the American Psychological Association's Task Force on Statistical Inference (Wilkinson & Task Force, 1999). There are also powerful tools for data manipulation and plotting available in many packages within R. Of particular note are [dplyr] for data transformation and [ggplot2] for data visualization.

# Exercises

+   2.1 [Calculating summary statistics] We have scores for 16 individuals on a mean of problem-solving ability: Y = 21, 40, 34, 34, 16, 37, 21, 38, 11, 34, 26, 27, 33, 47. Without using statistical software, find (a) the mean, (b) the median, (c) $\Sigma Y$, (d) $\Sigma$, $\Sigma Y^2$, (e) the standard deviation, and (f) the upper and lower hinges for these data. (g) Check your answers using R or another software package, then compute and kurtosis.

+   2.2 [Effect of data transformation on summary statistics]

+   a) Transform the scores in Exercise 2.1 to a new scale so that they have a mean of 100 and a standard deviation of 15.
b) What will be the new values of the median and hinges be?

+   2.3 [Understanding means and variances] Given the five scores 37, 53, 77, 30, and 28,
a) What sixth score must be added so that all six scores together have a mean of 47?
b) What sixth score should be added so that the set of six scores has the smallest possible variance?

+   2.4 [Assessing normality] Following are sets of scores in ranked order. For each data set, is there any indication that it does not come from a normal distribution? Explain, using graphical evidence to support your conclusion.
a) X = 10, 16, 50, 50, 50, 50, 55, 55, 57, 61, 62, 63, 73, 75, 83, 85, 107, 114.
b) Y = 15, 25, 26, 37, 39, 45, 45, 48, 49, 52, 53, 61, 63, 68, 70, 72, 76.
c) Z = 99, 10, 12, 14, 14, 15, 16, 16, 17, 18, 24, 31, 32, 35, 47, 59.
d) Find the mean and median of data sets (b) and (c). How do the results relate to your conclusion based on the graphical evidence?

+   2.5 [Interpreting equations with data] We have the following data set:
X = 6, 5, 7, 1, 11
Y = 7, 11, 14, 21, 9

Calculate (a) $\sum_{i=1}^5(X_i+Y_i)$ (b) $\sum_{i=1}^5 X_i^2$; (c) $\left[\sum_{i=1}^5 X_iight]^2$; (d) $\sum_{i=1}^5 X_i Y_i$;
(e) $\sum_{i=1}^5(X_i+Y_i^2+27)$; (f) the variance of X, and that of Y, and of X+Y.