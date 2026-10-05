# 3.3 summarize variables

```
summary_windspeed <- weather |
summarize(mean = mean(wind_speed, na.rm = TRUE),
std_dev = sd(wind_speed, na.rm = TRUE))
summarize_windspeed
```

```
# A tibble: 1 x 2
mean std_dev
<dbl>
1 9.44 5.26
```

Notice how the na.rm = TRUE are used as arguments to the mean() and sd() summary functions individually, and not to the summarize() function.

However, one needs to be cautious about missing values as we've just done. In the upcoming Learning checks, we'll consider the possible ramifications of blinding sweeping rows with missing values "under the rug". This is in fact the na_rm argument to any statistic function in R is set to FALSE by default. In other words, R does not ignore rows with missing values by default. It is alerting you to the presence of missing data and you should be mindful of this missingness and any potential causes of this missingness throughout your analysis.

What are other summary functions we can use inside the summarize() verb to compute summary statistics? As seen in the Figure 3.2, you can use any function in R that takes values and returns one. Here are just a few:

+   * mean(): the average
* sd(): the standard deviation, which is a measure of spread
* min() and max(): the minimum and maximum values, respectively
* IQR(): interquartile range
* sum(): the total amount when adding multiple numbers
* n(): a count of the rows in each group. This particular summary function will make more sense when group_by() is covered in Section 3.4.

> Learning check

(LC3.2) Say a doctor is studying the effect of smoking on lung cancer for a large number of patients who have records measured at five-year intervals. She notices that a large number of patients have missing data because the patient died, so she chooses to ignore these patients in her analysis. What is wrong with this doctor's approach?

(LC3.3) Modify the earlier summarize() function code that creates the summary_windspeed data frame to also use the n() summary function: summarize(..., count = n()). What does the returned value correspond to?