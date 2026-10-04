![](bbox=[0.1, 0.05, 0.9, 0.22])

**Figure 8.1** Health Metrics due to Dengue

The trend of the metrics in some locations is quite flat ranging around zero, while in others it is more evident. YLLs are the leading cause of DALYs, but YLDs are also contributing to the burden of disease.

We focus on DALYs due to **Dengue** in three locations, Malawi, Zambia, and Central African Republic. The data from 2017 to 2021 (26 years) is not included in the analysis and held out to be new data for testing the model's performance, as shown in Chapter 9.

Data are preprocessed to remove missing values, the values of DALYs only appeared in 1990, and then grouped by location id; the location name is removed.

```
dalys_dengue <- hmidw::infectious_diseases %>%
arrange(year) == "Dengue",
yyear=2016,
location_name%in%c("Eswatini", "Lesotho") %>%
drop_na() %>%
group_by(location_id) %>%
select(-location_name, -causal_name)
```

```
dalys_dengue %>%
head(
# # A tibble: 6 x 8
# # Groups: location_id [3]
# # year location_id Deaths DALYs YLDs YLLs Prevalence Incidence
# # <td> <td> <td> <td> <td> <td> <td> <td>
# 1 1990 182.0330 7.59 5.35 2.24 33.7 560.
# 2 1991 191.00135 6.88 6.64 0.0230 42.4 713.
# 3 1990 169.00760 2.25 - 13.1 222.
# 4 1991 191.00135 8.57 8.54 0.0230 52.5 884.
# 5 1991 182.0327 8.68 6.47 2.21 40.9 681.
# 6 1991 169.00760 2.23 2.22 0.0185 13.0 218.)
```

The {mlr3} is a meta-package particularly useful for its syntax, it guides the user through the machine learning steps by providing a consistent naming convention. It is also useful for benchmarking different models. In addition to the {mlr3} package, {mlr3learners}, {mlr3viz}, and {mlr3verse}, and {data.table} packages are also loaded. Each of these