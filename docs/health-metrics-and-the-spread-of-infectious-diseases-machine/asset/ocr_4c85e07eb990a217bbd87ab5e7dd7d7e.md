Example: Simulating Malaria Transmission Dynamics

```
head(nigeria_cases)
# # A tibble: 6 x 2
#   year positive
#   <int>  <dbl>
# 1 1985 873
# 2 1987 7
# 3 1988 1276
# 4 1989 134
# 5 1990 352
# 6 1992 92
```

Visualize the dynamics of malaria transmission in Nigeria using a line plot to show the number of infected cases over time.

```
nigeria_cases %>%
gggplot() + +
  geom_line(aes(x = year, y = positive),
            color = "navy",
            linetype = "solid") +
  labs(title = "Malaria Transmission Dynamics in Nigeria",
       subtitle = "23 years spanning from 1985 to 2018",
       x = "Time(Year)",
       y = "Number of Infected Cases") +
  theme_minimal()
```

# Malaria Transmission Dynamics in Nigeria
23 years spanning from 1985 to 2018

![](bbox=[0.109, 0.555, 0.89, 0.846])

Figure 16.3 The plot shows the dynamics of malaria transmission in Nigeria from 1985 to 2018. The blue line represents the number of infected cases over time, highlighting the fluctuations in malaria incidence during this period.