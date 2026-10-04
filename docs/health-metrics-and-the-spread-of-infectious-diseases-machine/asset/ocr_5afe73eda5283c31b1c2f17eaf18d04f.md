20

Methods and Calculations

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

On the other hand, the standard life expectancy represents the *maximum number of years a person is expected to live from birth*. For example, according to estimates released in 2021 by the United Nations Population Division, the *Japanese life expectancy at birth* is approximately 84.6 years. This figure is significantly higher than the global average life expectancy of 72.6 years.

To calculate the YLLs due to stroke, we need to use the life expectancy at different ages. We filter the `gh__tables` dataset to 2019, which is the most updated year for the life expectancy data, and select the indicator `ex` to get the life expectancy at different ages, renaming it as `le`.

```
ex2019 <- hmsidwr::gh_datatables %>%%
filter(year == 2019, indicator == "ex") %>%%
select(-indicator, -year) %>%%
rename(le = value) %>%%
head()
# A tibble: 6 x 3
# age sex
# ord <chr> <dbl>
# 1 <1 male 70.8
# 2 <1 female 75.9
# 3 <1 both 73.3
# 4 01-04 male 72.0
# 5 01-04 female 76.9
# 6 01-04 both 74.4
```

Then we merge the `deaths_stroke` with the ex2019 data to calculate the YLLs due to stroke in the Global region with the `full_join()` function, and group the data by age and sex to create one more vector named YLL, which is the product of the number of deaths and the life expectancy at that age. These YLLs are expressed in millions, and are not necessarily the real values, but estimated values. Their values are strongly dependent on the life expectancy and the number of deaths due to stroke, also other adjustments can be made to the life expectancy values to get more accurate results. In the past, the calculation of YLLs included the use of a discount rate, which is no longer used in the most recent calculations.