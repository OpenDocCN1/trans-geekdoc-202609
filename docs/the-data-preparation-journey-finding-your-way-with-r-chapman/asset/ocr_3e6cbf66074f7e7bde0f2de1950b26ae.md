![](bbox=[0.11, 0.14, 0.9, 0.29])

# FIGURE 8.8 BC Ferries: table 2.

+   - there's the route type sub-total rows
+   - a blank row
+   - the difference columns

```
bcf_table_3 <- bcf_table_2 |>
# succinct way to remove a row which has a single "NA"
na.omit() |>
select(route,
    starts_with("passengers_"),
    starts_with("passenger_tariff_rev")) |>
# change variables to numeric
mutate(passengers_fy2021 = as.numeric(passengers_fy2021),
    passengers_fy2020 = as.numeric(passengers_fy2020),
    passenger_tariff_revenue_fy2021 =
    as.numeric(passenger_tariff_revenue_fy2021),
    passenger_tariff_revenue_fy2020 =
    as.numeric(passenger_tariff_revenue_fy2020))
```

```
bcf_table_3
```

If we need to create sub-totals by route type, it would be better to have a separate variable for that. Here’s where we can use the case_when() function from {dplyr}.

```
bcf_table_3 <- bcf_table_3 |>
    mutate(route_type = case_when(
    route %in% c("1", "2", "3", "30") ~ "major",
```