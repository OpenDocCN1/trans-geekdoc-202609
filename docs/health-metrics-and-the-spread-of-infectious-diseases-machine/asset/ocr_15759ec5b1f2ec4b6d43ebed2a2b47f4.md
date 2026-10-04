# Case Study: Germany Lung Cancer Study

# Table 4.13 <- Lung Cancer Cases in Germany 2019

```
gelung_YLD <- prev_germany_lungc %%
mutate(dw = 0.451, YLD = prevalence * dw)

gelung_YLD %%
head()
# # A tibble: 6 x 4
# age prevalence dw YLD
# <chr> <dbl dbl <dbl>
# 1 10-14 0.13 0.451 0.0586
# 2 15-19 0.68 0.451 0.307
# 3 20-24 0.98 0.451 0.442
# 4 25-29 1.66 0.451 0.749
# 5 30-34 3.85 0.451 1.754
# 6 35-39 9.24 0.451 4.17

 6 35-39 4502 4.17 4506.
# 7 40-44 10814 10.0 10824.
# 8 45-49 28982 28.3 29010.
# 9 50-54 73451 58.7 73510.
# 10 55-59 121449 101. 121550.
# 11 60-64 137749 139. 137888.
# 12 65-69 135861 164. 136025.
# 13 70-74 108507 169. 108226.
# 14 75-79 95872 136. 96000.
# 15 80-84 66681 112. 66793.
# 16 85+ 35158 77.1 35235.
```

```
(YLLs <- sum(gelung_YLD$YLL))
# [1] 821896.1
(YLDs <- sum(gelung_YLD$YLD))
# [1] 1000.589
(DALYs <- YLLs + Ylds)
# [1] 822896.6
```

Per 1000 population, the YLLs, YLDs, and DALYs for lung cancer deaths in Germany in 2019 are 821, and 822, respectively. These metrics provide a comprehensive view of the impact of lung cancer on the health status of the population, combining the years of life lost to premature death with the years lived with disability.

DALYs / 1000 # DALYs per 1000 population

The value of the metrics changes 169 when different weights are adopted. It is noteworthy that the value for the Years Lived with Disabilities (YLDs) is often quite small compared to the contribution made by the Years of Life Lost (YLLs) in the calculation of Disability-Adjusted Life Years (DALYs). This disparity highlights how mortality frequently dominates the overall disease burden in many health evaluations, underscoring the critical impact of premature death on public metrics.