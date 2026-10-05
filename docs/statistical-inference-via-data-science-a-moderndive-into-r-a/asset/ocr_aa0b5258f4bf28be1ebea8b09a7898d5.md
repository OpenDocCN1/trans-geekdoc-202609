# 5.3 Related topics

fertility rates. A proxy for looking at the level of economic development could be the Human Development Index (HDI). It measures a country's average achievements in three basic aspects of human development: health (life expectancy), education (mean and expected years of schooling), and standard of living (gross national income capita). This is stored in the hdi_2022 column of un_member_states_2024. We explore its relationship with life expectancy and fertility rates:

```
ggplot(data = un_member_states_2024,
aes(x = hdi_2022, y = life_expectancy_2022)) +
geom_point() +
labs(x = "Human Development Index (HDI)", y = "Life Expectancy")
```

![](bbox=[0.118, 0.303, 0.882, 0.683])

```
ggplot(data = un_member_states_2024,
aes(x = hdi_2022, y = fertility_rate_2022)) +
geom_point() +
labs(x = "Human Development Index (HDI)", y = "Fertility Rate")
```