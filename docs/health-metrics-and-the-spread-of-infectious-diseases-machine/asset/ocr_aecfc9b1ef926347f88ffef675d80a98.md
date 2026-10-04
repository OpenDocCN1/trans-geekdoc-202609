# Methods and Calculations

# 3.2.1 Example: YLDs Due to Stroke

Since the release of GBD 2010, the WHO has decided to switch to a prevalence-based approach for the calculation of YLDs. The major impact of this shift is to distribute the weights of the YLDs more evenly across all age groups, rather than concentrating them at the age of incidence.

In the following example we use the disability weights and the severity levels extracted from a dataset in the GBD study. The disweights dataset is stored in the {hmsidwR} package and is made of 463 observations and 9 variables. It contains the estimated values for disability weights, which are measured on a scale from 0 to 1, where 0 equals a state of full health and 1 equals death.

```
hmsidwR::disweights %
filter(year == 2019)%
group_by(cause1, severity)%
reframe(dw = mean(dw))%
filter(cause1 == "Stroke")
# # A tibble: 3 x 3
#   cause1 severity dw
#   <chr> <chr> <dbl>
#   1 Stroke mild 0.019
#   2 Stroke moderate 0.193
#   3 Stroke severe 0.57
```

The level of severity is assigned based on the degree of disability assessed by the National Institutes of Health Stroke Scale (NIHSS). The classification is used by healthcare providers to objectively quantify the impairment caused by a stroke. Here is assumed a sample population affected by a stroke, categorised as mild, moderate, or severe with appropriate proportions.

# Table 3.4 Level of disability by the National Institutes of Health NIH or more specifically by the National Institutes of Health Stroke Scale (NIHSS).

| Score Stroke severity Severity Level Severity % |
| 0-4 Minor stroke Mild 50.3% |
| 5-20 Moderate stroke Moderate 25.3% |
| 21-42 Severe stroke Severe 24.4% |

These values are general for all ages; the values may vary for other specifications of the level of disability.⁹

```
dwsev2019 <- hmsidwR::%
select(cause1, severity, dw)%
drop_na()%
mutate(severity_n = case_when(
severity == "mild" ~ 0.503,
severity == "moderate" ~ 0.253,
severity == "severe" ~ 0.244))
```

> Grant M. A. Wyper et al., “Prioritising of Severity Distributions in Burden of Disease Studies for Countries in the European Region,” Archives of Public Health 78, no. 1 (January 2020): 3, doi:10.1186/s13690-019-0385-6.