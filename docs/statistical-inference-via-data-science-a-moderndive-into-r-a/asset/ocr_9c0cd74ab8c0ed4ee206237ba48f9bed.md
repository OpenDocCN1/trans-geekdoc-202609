# 5.1 One explanatory variable representing the country's obesity rate

4. obes_rate: A numerical variable representing the country's obesity rate in 2016. This will be another explanatory variable x that we use in the Learning check at the end of this subsection.

An alternative way to look at the raw data values is by choosing a random sample of the rows in UN_data_ch5 by piping it into the slice_sample() function from the dplyr package. Here we set the n argument to 5, indicating that we want a random sample of 5 rows. We display the results in Table 5.1. Note that due to the random nature of the sampling, you will likely end up with a different subset of 5 rows.

```
UN_data_ch5 |>
slice_sample(n = 5)
```

# TABLE 5.1: A random sample of 5 out of the 193 total countries (181 without missing data)

| | life_exp | fert_rate | obese_rate |
|---|---|---|-|
| PRT | 81.5 | 1.4 | 20.8 |
| MNE | 77.8 | 1.7 | 23.3 |
| CPV | 73.8 | 1.9 | 11.8 |
| VNM | 75.5 | 1.9 | 2.1 |
| IDN | 73.1 | 2.1 | 6.9 |

We have looked at the raw values in our UN_data_ch5 data frame and got a preliminary sense of the data. We can now compute summary statistics. We start by computing the mean and median of our numerical output variable fert_rate and our explanatory variable life_exp. We do this by using the summarize() function from dplyr along with the mean() and median() summary functions we see in Section 3.3.

```
UN_data_ch5 |>
sumize(mean_life_exp = mean(life_exp),
       mean_fert_rate = mean(fert_rate),
       median_life_exp = median(life_exp),
       median_fert_rate = median(fert_rate))
```

| life_exp | mean_fert_rate | median_life_exp | median_fert_rate |
|---|---|---|-|
| 73.6 | 2.5 | 75.1 | 2 |

However, if we want other summary statistics as well, such as the standard deviation (a measure of spread), the minimum and maximum values, and various percentiles?