
# HALE Calculation

# 33

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_51_0.png)

Figure 3.5 HALE - GLOBAL HEALTH METRICS VOLUME 392, ISSUE 10159, P1859-1992, NOVEMBER 10, 2018

### 3.5.0.1 Simulating Life Table Data

To understand the process of calculating HALE, we can simulate life table data. We'll define age intervals (e.g., every 5 years) and simulate survival probabilities for each age interval (between 0 and 1).

```r
set.seed(040424)
age_intervals <- seq(0, 100, by = 5)
survival_probabilities <- runif(length(age_intervals),
               min = 0.5, max = 1)
```

```r
life_table <- data.frame(
  Age = age_intervals,
  Survival_Probability = survival_probabilities,
  LX = 100000 - (age_intervals * survival_probabilities))
)
```

```r
life_table %>% head()
# Age Survival_Probability               nLX
# 1 0                       0.5579497 100000.00
# 2 5                       0.9241893 99995.38
# 3 10                      0.8810716 99991.19
# 4 15                      0.9562922 99985.66
# 5 20                      0.6927314 99986.15
# 6 25                      0.5607453 99985.98
```

We calculate adjusted $T_x$ for each age group as the sum of health-adjusted person-years for all age intervals above the current age interval.

```r
# Simulate prevalences
prevalences <- runif(length(age_intervals),
               min = 0, max = 0.5)
```

# Simulate disability weights

```r
# Simulate disability weights
disability_weights <- runif(length(age_intervals),
min = 0, max = 1)
```

```r
# Calculate average health for each age group
average_health <- 1 - (prevalences * disability_weights)
```

```r
# Adjust Tx for each age group
life_table$adjusted_px <- life_table$Survival_Probability * average_health
```

```r
life_table %>% head()
# Age Survival_Probability nLx adjusted_px
# 1 0 0.5579497 100000.0 0.5345848
# 2 5 0.9241893 99995.38 0.7786488
# 3 10 0.8810716 99991.19 0.5781898
# 4 15 0.9562922 99985.65 0.7392462
# 5 20 0.6927314 99986.15 0.5813254
# 6 25 0.5607495 99985.98 0.3603310
```

Let's make a function to calculate the HALE:

```r
calculate_HALE <- function(age, px) {
  # Initialise a vector to store adjusted Tx for each age group
  adjusted_Tx <- numeric(length(age))
  # Iterate over each age interval to calculate adjusted Tx
  for (i in 1:length(age)) {
    # Calculate adjusted Tx for the current age group
    adjusted_Tx[i] <- sum(px[i:length(age)])
  }
  HALE <- numeric(length(age))
  # Calculate HALE for each age group
  for (i in 1:length(age)) {
    # Calculate HALE for the current age group
    HALE[i] <- adjusted_Tx[i] / px[i]
  }
  return(HALE)
}
```

Now, we calculate HALE for the simulated life table data.

```r
# Calculate HALE for the simulated life table data
HALE1 <- calculate_HALE(age_intervals, life_table$Survival_Probability)
HALE2 <- calculate_HALE(age_intervals, life_table$adjusted_px)
```

To visualise HALE for the standard and adjusted life table data we can plot the results with a line graph.

The difference between the two lines represents the impact of adjusting life table. The adjusted life table considers the prevalence of health conditions and their associated disability weights, providing a more accurate estimate of the number of years a person can expect to live in good health.

In general, HALE is a valuable metric for assessing the overall health of a population, by incorporating information on the prevalence of health conditions and their associated disability weights, HALE offers a more specific understanding of population health.

# Summary

## Health Adjusted Life Expectancy (HALE) by Age

![](img/6b61f0d3dcab44c60cdfe4e888d549c_53.png)

**Figure 3.6** Health Adjusted Life Expectancy (HALE) by Age. The blue line represents HALE for the simulated life table, the dotted line represents HALE for the adjusted life table.

### 3.6 Summary

In this chapter, we have detailed the methods and calculations for evaluating the burden of disease using key health metrics: YLLs, YLDs, and DALYs. By understanding how to compute these metrics, we gain insights into the impact of diseases on populations, guiding health decisions. We also introduced HALE, a metric that combines mortality and morbidity data to provide a comprehensive measure of population health. These metrics are invaluable tools for public health practitioners, policymakers, and researchers in their quest to improve global outcomes.

As we confront new health challenges like pandemics, aging populations, and climate-related risks, traditional metrics like DALYs and QALYs are evolving to meet new approaches to capture the complexity of health, becoming essential to understanding the full impact on individuals. In the next chapter (Chapter 4), we will delve deeper into the components and variations of these metrics, further enhancing our understanding of how to utilize them effectively in public health assessments.

# 4 Metrics Components

### Learning Objectives

- Understand the interpretation of life tables and rates for life expectancy
- Analyse mortality levels and rates to assess population health
- Distinguish between incidence and prevalence and their relevance in disease monitoring
- Interpret disability weights and severity levels in the context of burden of disease

In Chapter 3, we discussed the importance of health metrics in assessing the overall health status of a population and guiding the allocation of resources. We have seen how to calculate metrics but haven't discussed the components that make up these metrics. In this chapter, we will investigate life expectancy, mortality rates, incidence and prevalence and disability weights. These components are crucial for understanding the burden of diseases and injury at both global and population levels.

## 4.1 Cause-Specific or Population-Wide

Health metrics are essential tools for evaluating the health status of a population and guiding public health interventions. They provide valuable insights into the burden of disease and injury, helping policymakers and public health officials make informed decisions about resource allocation and health policy. By combining these metrics, policymakers and public health officials can make informed decisions about how to improve the health outcomes of a population and reduce the burden of disease.

> **What are the components of these health metrics, and how are they calculated?**

The evaluation of health metrics begins with the assessment of its components, which is crucial because results strongly depend on the life tables, mortality rates, and disability weights used in the analysis. Furthermore, it is important to consider whether the objective of the analysis is cause-specific or population-wide. This can significantly increase the granularity of health metrics, as alignment with general principles in epidemiological research and health metrics analysis discussed in the Global Burden of Disease (GBD) study.

¹Theo Vos et al., “Global Burden of Diseases and Injuries in 204 Countries and Territories, 1990-2019: A Systematic Analysis for the Global Burden of Disease Study 2019,” *The Lancet* 396, no. 10258 (October 2020): 1204–1222, doi:10.1016/S0140-6736(20)30925-9.

DOI: 10.1201/9781032265935-4

# Life Tables and Life Expectancy

Cause-specific metrics focus on disease intervention planning, such as the burden of HIV or tuberculosis on specific populations. Population-wide metrics, on the other hand, are ideal for broader health policy decisions, overall mortality rates or life expectancy, and provide a comprehensive view of the health landscape.

The results of health metrics calculations can vary significantly based on various factors, including geographic location, the type and severity of diseases or injuries, the specific cases of death or disability, and the age groups analysed (whether age-standardised or covering all ages). Additional variation arises from the points of analysis and whether the metrics are calculated across both sexes or specifically for males and females. The disability weights applied can differ depending on the condition's severity, its impact on quality of life, and other contextual parameters, resulting in tailored calculations that reflect local health challenges more accurately.

In this chapter, particular examples and case studies are provided to illustrate the process of applying the components to the metrics. By understanding the structure of the components, you will be better equipped to analyse and interpret health data and make informed decisions about health policy and resource allocation.

## 4.2 Life Tables and Life Expectancy

The first component is the life expectancy, used for calculating the YLLs in Equation 3.1. More specification about life tables used to calculate the life expectancy is in the Appendix A. As a key parameter in the calculation of health metrics, life expectancy is essential for estimating the number of years lost to premature death.

The standard life expectancy is defined as the average number of years a person is expected to live based on current mortality rates, an important indicator of the overall health status of a population used to compare the outcomes of different populations over time. It is calculated based on the probability of survival at each age, taking into account the mortality rates for that age group.

In life tables, the probability of survival and the mortality rates across different age groups are used for estimating the number of remaining expected years. These tables provide crucial insights into the longevity patterns within a population, enabling researchers and policymakers to predict life expectancy trends and to assess health strategies effectively.

**Table 4.1 Extraction of Global Health Observatory (GHO) Life Tables Components

| age | ndx | nLx | Tx | ex |
| :--- | :--- | :--- | :--- | :--- |
| 40-44 | 92380 | 1320 | 48599 | 353024 | 38 |
| 45-49 | 91060 | 1737 | 450958 | 3071605 | 34 |
| 50-54 | 89323 | 2547 | 440248 | 262467 | 29 |

Where $x$ is the number of people at the beginning of the age, $ndx$ is the number of person-years lived between age $x$ and $x+1$, $nLx$ is the number of person-years lived between age $x$ and $x+1$, $Tx$ is the total number of person-years lived by the cohort of persons alive at age $x$, and $ex$ is the expected remaining lifetime at age $x$.
