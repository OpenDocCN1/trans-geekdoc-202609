# Table 4.12 lung cancer - Disability Weights

```
lung_dw <- hmsidR::disweights %%
filter(year == 2019,
  str_detect(seuela, "lung")) %%
select(seuela, dv)
```

Now to calculate the YLDs for lung-cancer we consider not fatal disability status. This can appear in conjunction with other acting together with the lung-cancer.10 The Disability weights are available from GBD study11 are the same as those found in the disweights dataset.

0.451 is the disability weight for the metastatic phase of lung, or cancer we. We can use this value with prevalence of the disease to show how to calculate the YLDs for the lung cancer deaths in Germany in 2019. The number of lung cases in Germany in 2019 is 34,000, and the prevalence of the disease is 0.0004 for all ages and we. While considering 5-yrs age groups with a common disability weight of 0.451. Total YLDs can be calculated as the sum of the product of the prevalence and the disability weight for each group.

```
prev_germany_lungc <- germany_lungc %%
filter(sex == "both") %%
select(age, prevalence)
```

```
prev_germany_lungc %> head()
# # A tibble: 6 x 2
#   age prevalence
# <chr> <dbl>
# 1 10-14 0.13
# 2 15-19 0.68
# 3 20-24 0.98
# 4 25-29 1.66
# 5 30-34 3.85
# 6 35-39 9.24
```

```
gelung_YLL %>%%
select(age, YLL) %>%%
left_join(gelung_YLL %>%% select(age, YLD)) %>%%
mutate(DALY = YLL + YLD)
# # A tibble: 16 x 4
#   age YLL YLD DALY
# <chr> <dbl> <dbl> <dbl>
# 1 10-14 51.7 0.0586 51.7
# 2 15-19 174. 0.307 175.
# 3 20-24 349. 0.442 350.
# 4 25-29 704. 0.749 705.
# 5 30-34 2041. 1.74 2043.
```

> 10Michael Post et al., “The Burden of Disease in Germany at the National and Regional Level,” Deutsches Ärzteblatt International 119, no. 46 (November 2022): 785-92, doi:10.3238/artebl.m.2022.0314.
11 Ihmeuw/Ihmeuw-Modeling (Institute for Health Metrics: Evaluation, 2024), https://github.com/ihmeuw/ihme-modeling.