# 5.1 One numerical explanatory variable 123

![](bbox=[0.11815, 0.072, 0.88185, 0.445])

**FIGURE 5.2:** Scatterplot of relationship of life expectancy and fertility rate.

We do not miss due to little to no overlap in the points. Most life expectancy expectancy entries appear to fall between 70 and 80 years, while most fertility rate entries fall between 1.5 and 3.5 births. Furthermore, while opinions may vary, it is our opinion that the relationship between fertility rate and life expectancy is "moderately negative." This is consistent with our earlier computed correlation coefficient of -0.812.

We build on the scatterplot in Figure 5.2 by adding a "best-fitting" line: of all lines we can draw on this scatterplot, it is the line that "best" fits the cloud of points. We do this by adding a new `geom_smooth(method = "lm", se = FALSE)` layer to the ggplot() code that created the scatterplot in Figure 5.2. The method = "lm" argument sets the line to be a "linear model." The se = FALSE argument suppresses standard error uncertainty bars. We will define the concept of standard error later in Section 7.3.4.

```
ggplot(UN_data_ch5, aes(x = life_exp, y = fert_rate) + 
geom_point(alpha = 0.1) + 
labs(x = "Life Expectancy",
y = "Fertility Rate",
title = "Relationship of life expectancy and fertility rate") + 
geom_smooth(method = "lm", se = FALSE)
```