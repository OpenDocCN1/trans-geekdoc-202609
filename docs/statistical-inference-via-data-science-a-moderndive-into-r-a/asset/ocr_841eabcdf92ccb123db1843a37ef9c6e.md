# 6.1 One numerical and one categorical explanatory variable

Figure 5.2. But this time, we incorporate the categorical income by mapping this variable to the color aesthetic, creating a colored scatterplot.

```
ggplot(UN_data_ch6, aes(x = life_exp, y = fert_rate, color = income) +
  geom_point() +
  labs(x = "Life Expectancy", y = "Fertility Rate", color = "Income group") +
  geom_smooth(method = "lm", se = FALSE)
```

![](bbox=[0.118, 0.239, 0.882, 0.503])

FIGURE 6.1: Colored scatterplot of life expectancy and fertility rate.

In the resulting Figure 6.1, observe that ggplot() assigns a default color scheme to the points and to the lines associated with the four levels of income: Low income, Lower middle income, Upper middle income, and High income. Furthermore, the geom_smooth(method = "lm", se = FALSE) layer automatically fits a regression line for each group.

We can see some interesting trends. First, observe that we get a different line for each income group. Second, the slopes for all the income groups are negative. Third, the slope for the High income group is clearly less steep than the slopes for all other three groups. So, the changes in fertility rate due to life expectancy are dependent on the level of income of a given country. Fourth, observe that high-income countries have, in general, high life expectancy and low fertility rates.

# 6.1.2 Model with interactions

We can represent the four regression lines in Figure 6.1 as a multiple regression model with interactions.