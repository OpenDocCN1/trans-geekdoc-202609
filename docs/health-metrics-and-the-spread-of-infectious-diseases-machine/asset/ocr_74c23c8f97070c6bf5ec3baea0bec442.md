COVID-19 and DALYs

# YLDs by Country and Month Cycle

![](bbox=[0.118, 0.107, 0.871, 0.432])

**Figure 15.14** YLDs by Country and Month Cycle

Finally, let's plot the DALYs by country and month cycle, with the y axis representing the DALYs formatted in millions.

```
COVID19_dalys %>%
filter(year %in% c(2020, 2021)) %>%
gplot() +
  geom_col(aes(x = month_cycle, y = dalys,
    fill = country_region)) +
  scale_y_continuous(
    labels = scales::unit_format(unit = "M",
    scale = 1e-6)) +
  scale_fill_grey(start = 0.2, end = 0.8) +
  labs(title = "DALYs by Country and Month Cycle",
    fill = "Country",
    x = "4-Month Cycle", y = "DALYs") +
  facet_wrap(~year) +
  theme(axis.text.x = element_text(angle = 45, hjust = 1))
```