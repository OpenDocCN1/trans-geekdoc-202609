# HALE Calculation

# 33

![](bbox=[0.106, 0.093, 0.892, 0.345])

Figure 3.5 HALE - GLOBAL HEALTH METRICS VOLUME 392, ISSUE 10159, P1859-1992, NOVEMBER 10, 2018

# ### 3.5.0.1 Simulating Life Table Data

To understand the process of calculating HALE, we can simulate life table data. We'll define age intervals (e.g., every 5 years) and simulate survival probabilities for each age interval (between 0 and 1).

```
set.seed(040424)
age_intervals <- seq(0, 100, length(age_intervals),
survival_probabilities <- runif(length(age_intervals),
               min = 0.5, max = 1)
```

```
life_table <- data.frame(
Age = age_intervals,
Survival_Probability = survival_probabilities,
LX = 100000 - (age_intervals * survival_probabilities))
```

```
life_table%% head(
# Age Survival_Probability               nLX
# 1 0                       0.5579497 100000.00
# 2 5                       0.9241893 99995.38
# 3 10                      0.8810716 99991.19
# 4 15                      0.9562922 99985.66
# 5 20                      0.6927314 99986.15
# 6 25                      0.5607453 99985.98
```

We calculate adjusted $T_x$ for each age group as the sum of health-adjusted person-years for all age intervals above the current age interval.

```
# Simulate prevalences
prevalences <- runif(length(age_intervals),
               min = 0, max = 0.5)
```