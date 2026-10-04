```
total_cases <- sum(covid_data$Cases)
total_recoveries <- sum(covid_data$Recovered)
```

# 4.4.1.3 Incidence and Prevalence Rates for the Year

```
incidence_rate <- total_cases / population_size
# [1] 0.00071
prevalence_rate <- (total_cases - total_recoveries) / population_size
# [1] 0.00052
```

# Incidence and Prevalence COVID-19 Cases

![](bbox=[0.127, 0.323, 0.891, 0.613])

Figure 4.2 Incidence and Prevalence COVID-19 Cases - simulate data

# 4.5 Disability Weights and Severity Levels

The disability weights measure the severity of the health loss associated with specific health outcomes or diseases, ranging from 0 (no disability) to 1 (equivalent to death). These weights are used to calculate the number of years lived with a disability (YLDs) in the calculation of DALYs, and play a pivotal role between mortality and morbidity when estimating the Health Adjusted Life Expectancy (HALE).

The disability weights are crucial for understanding the impact of diseases and injuries on the health status of a population, if the disability weight of a specific disease is overestimated,