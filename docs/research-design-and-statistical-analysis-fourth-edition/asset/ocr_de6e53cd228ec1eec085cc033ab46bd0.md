# Introduction to Multiple Regression

Table 20.1 Descriptive statistics for women aged 65 years or less
(a) for all cases with data on all three variables

# Descriptive Statistics

| N | Minimum | Maximum | Mean | Std. | Skewness | Kurtosis |
|---|---|---|---|---|---|---||
| Statistic | Statistic | Statistic | Statistic | Statistic | Std. Error | Statistic | Std. Error |
| Age | 190 | 20.00 | 65.00 | 46.74 | 10.59 | -.08 | .18 | -.74 | .35 |
| TC | 190 | 114.88 | 320.00 | 211.61 | 39.91 | .28 | .18 | -.01 | .35 |
| BMI | 190 | 17.69 | 57.11 | 26.60 | 6.30 | 1.68 | .18 | 3.91 | .35 |
| Valid | 190 | | | | | | | |
| (listwise) | | | | | | | | |

(b) for cases with BMI of 40 or less

# Descriptive Statistics

| N | Minimum | Maximum | Mean | Std. | Skewness | Kurtosis |
|---|---|---|---|---|---|---||
| Statistic | Statistic | Statistic | Statistic | Statistic | Std. Error | Statistic | Std. Error |
| Age | 181 | 20.00 | 65.00 | 46.93 | 10.63 | -.12 | .18 | -.72 | .36 |
| TC | 181 | 114.88 | 316.00 | 211.58 | 39.17 | .24 | .18 | -.17 | .36 |
| BMI | 181 | 17.69 | 39.12 | 25.67 | 4.67 | .83 | .18 | .26 | .36 |
| Valid | 181 | | | | | | | | |
| (listwise) | | | | | | | | |

Table 20.2 Pairwise Pearson correlations (cor) for TC, age, and BMI for women aged 65 years less with BMI less than or equal to 40

| Var1 | | | | p |
|---|---|---|---|---|n| 1 | Age | TC | | 0.49 | 2.05e-12 |
| 2 | BMI | TC | | 0.23 | 1.79e-03 |
| 3 | | Age | | 0.12 | 1.19e-01 |

smo (see Chapter 17), it appears that the BMI outliers tend to have relatively low TC scores. From the scatterplot we see that these introduce a somewhat curvilinear component to the relationship between TC and BMI. Because we are concerned with describing the relationships among the variables for participants who do not have extreme scores, we exclude the data points of the nine participants whose BMI scores were greater than 40. As can be seen in Panel b of Table 20.1, when we exclude the outlying BMI scores, the ratios of the skewness and kurtosis measures to their standard errors are much smaller.

Information about the correlations among TC, age, and BMI is shown in Table 20.2, which contains R output for the 181 women aged 20 to 65 years with BMIs of 40 or less who have scores on all three measures. The significant correlations of TC with both age,