
# YLLs Calculation

Building on these ideas, Mary Demsey formalized the concept in 1947 to assess the burden of tuberculosis, coining the term Years of Life Loss (YLLs). This metric was specifically designed to identify areas requiring improvement to reduce loss and prevent premature death.3 Her work established YLLs as a critical tool for understanding and addressing the disproportionate effects of early mortality on population health.

The impact of premature loss on society extends the grief of losing a loved one; it includes the economic and social cost of losing productive members of the workforce. whereas premature death leads to a significant burden on the community, affecting overall economic stability and societal well-being.

# Standard Formula

```
YLL = N * le (3.1)
```

In Equation 3.1, N is the number of premature deaths, and le is the standard life expectancy at the age of death. This calculation takes into account the number of deaths at each age and multiplies it by the standard life expectancy remaining at that age, using global life tables to determine life expectancy. More details about the concepts of YLLs are provided in the next chapter (Chapter 4), and a sample of the construction of a life table with relative estimations of the life expectancy can be found in Appendix A.

In general, the Global Burden of Disease studies (GBD) used standardised life tables, to consistently measure the impact of various diseases. This approach allows for reliable comparisons across different conditions and populations, providing a comprehensive assessment of disease burden on a global scale.4 Additionally, country-specific life expectancies are valuable for investigating premature deaths resulting from health-related causes, such as fatal diseases. For instance, certain types of country-specific life expectancies are frequently recommended to provide insight into longevity characteristics, which can inform policymakers and aid in prevention efforts, as exemplified by the Japanese life expectancy.5 A G7 cross-country study demonstrated that Japan has the longest life expectancy, primarily attributed to low mortality rates from ischemic disease and cancer, which are the leading causes of death in most countries, as indicated by the GBD study.

# 3.1.1 Example: YLLs Due to Stroke

Stroke can be a consequence of several infectious diseases, such as COVID-19, Tuberculosis (TB), and malaria. The impact of these diseases on the cardiovascular system can lead to stroke, as infections can cause inflammation, blood formation, or direct damage to brain vessels.

In the following, we calculate the YLLs due to stroke in the year 2019 for the Global region. We use the Global Burden of Disease (GBD) study, which

> 2Mary Demsey, "Decline in Tuberculosis," American Review of Tuberculosis, April 23, 2019, https://www.ajjournals.org/epdf/10.1164/art.1947.56.2.1576=tab.

> 3 Robert C Simon and Israel Lu, "The Overlapping Burden of the Leading Causes of Disease in Adults and Children," Nature Communications 13, no. 1 (December 6, 2022): 7457; doi:10.1038/s41467-022-3424-6

> 4brecht Devchsler et al., "Valuing the Years of Life Lost Due to COVID-19: The Differences and Pitfalls," International Journal of Public Health 65, no. 6 (2020): 719-20, doi:10.1007/s00038-020-01430-2.

> 5Shoichiro Tsugane, "Why Japan is the World's Long-Lived Country: Insights from a Food and Nutrition Perspective," European Journal of Clinical Nutrition 75, no. 6 (2021): 921-28, doi:10.1038/s41537-020-0877-5.

# Methods and Calculations

estimates of the number of deaths due to stroke in different regions. The data can be downloaded from the hmsidWR package, which contains the necessary datasets for this calculation. The deaths2019 dataset comprises 2754 observations and 7 variables, containing the estimated number of deaths to 9 cases, including stroke, across 6 regions: Global, France, Italy, Germany, the United Kingdom, and the United States. We use the Global Health Observatory Life Tables to estimate the life expectancy at different ages, which is used to calculate the YLLs due to.

```
install.packages("hmsidWR")
# install.packages("devtools")
```
```
library(tidyverse)
library(hmsidWR)
```
```
install_github("Fgazzelloni/hmsidWR")
```
```
unique(hmsidWR::deaths2019$cause)
# [1] "Lower respiratory infections"
# [2] "Stroke"
# [3] "Chronic obstructive pulmonary disease"
# [4] "Road injuries"
# [5] "Diabetes and kidney diseases"
# [6] "Colon and rectum cancer"
# [7] "Tracheal, bronchus, and lung cancer"
# [8] "Breast cancer"
# [9] "Alzheimer's disease and other dementias"
```

specific task is to calculate the Years of Life Lost (YLLs) attributable to stroke in the year 2019 for the Global region. We filter the location to be "Global" and the cause to be "Stroke". The use of str_detect() is to match the cause of death, it is very useful when the cause of death is not

```
deaths_stroke <- hmsidWR::deaths2019 %>%
arrange(age) %>%
filter(location == "Global",
       str_detect(cause, "Stroke")) %>%
select(-location, -cause, -upper, -lower)
```
```
deaths_stroke %>% head()
# A tibble: 6 x 3
# sex age dx
#  <chr> <ord> <dbl>
# 1 male <1
# 2 female <1
# 3 both <1
# 4 male 01-04
# 5 female 01-04
# 6 both 01-04
```

Then, we visualise the number of deaths due to stroke by age group with a geom_boxplot(). The boxplot shows the distribution of the number of deaths by age group, with the median, quartiles, and outliers. The plot is divided by age group and shows the

```
deaths_stroke %%
filter(!sex == "both") %%
ggplot(aes(x = age, y = dx)) +
geom_boxplot() +
labs(title = "Male and Female Deaths to Stroke",
  subtitle = "Year 2019",
  caption = "IHME GBD 2019 Data",
  x = "Age Group", y = "Deaths") +
theme(axis.text.x = element_text(angle = 45, hjust = 1))
```

# Male and Female Deaths to Stroke

Year 2019

![](img/6b1f0d3dcab44c60cdfe4e88d549c9_37_0.png)

Figure 3.1 Boxplots showing male and female deaths variation due to Stroke by Age Group (2019)

Among the indicators available in the hmsidvr::ghltables dataset, we specifically focus on the indicator denoted as ex. The expectation of life at age x (ex) refers to the average number of additional years a person is expected to live, given that they have already reached x. This measure is commonly referred to as life expectancy at age x. This dataset is part of the Global Health Observatory (GHO) data repository, which is maintained by the World Health Organization (WHO). The dataset also contains life table indicators, such as the number of person-years lived above age x (lx), the number of person-years lived between ages x and x+n (nLx), the age-specific death rate between ages x and x+n (n_x), the number of people dying between ages x and x+n (ndx), and the probability of dying between ages x and x+n (nq).

# Table 3.1 Life Table Indicators

| Indicator | Description |
|---|---|
| Tx | person-years lived above age x |
| ex | expectation of left alive at age x |
| lx | number of people left alive at age x |
| NLx | person-years lived between ages x and x+n |
| nmx | age-specific death rate between ages x and x+n |
| ndx | number of people dying between ages x and x+n |
| nqx | probability of dying between ages x and x+n |

We estimated the value of the expected life for 5-year age groups, as <1, ... , 05-09, 10-14, etc. for both females and males.

On the other hand, the standard life expectancy represents the maximum number of years a person is expected to live from birth. For example, according to estimates released in 2021 by the United Nations Population Division, the Japanese life expectancy at birth is approximately 84.6 years. This figure is significantly higher than the global average life expectancy of 72.6 years.

To calculate the YLLs due to stroke, we need to use the life expectancy at different ages. We filter the `gh__tables` dataset to 2019, which is the most updated year for the life expectancy data, and select the indicator `ex` to get the life expectancy at different ages, renaming it as `le`.

```
ex2019 <- hmsidwr::gh_datatables %>%
filter(year == 2019, indicator == "ex") %>%
select(-indicator, -year) %>%
rename(le = value) %>%
head()
# A tibble: 6 x 3
# age sex le
#  <chr> <ord> <dbl>
# 1 male <1 70.8
# 2 female <1 75.9
# 3 both <1 73.3
# 4 male 01-04 72.0
# 5 female 01-04 76.9
# 6 both 01-04 74.4
```

Then we merge the `deaths_stroke` with the ex2019 data to calculate the YLLs due to stroke in the Global region with the `full_join()` function, and group the data by age and sex to create one more vector named YLL, which is the product of the number of deaths and the life expectancy at that age. These YLLs are expressed in millions, and are not necessarily the real values, but estimated values. Their values are strongly dependent on the life expectancy and the number of deaths due to stroke, also other adjustments can be made to the life expectancy values to get more accurate results. In the past, the calculation of YLLs included the use of a discount rate, which is no longer used in the most recent calculations.
