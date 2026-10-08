# 6.6 EDA with Plots

```
## 1 alive female 70.2 11.4
## 2 alive male 56.0 18.8
## 3 dead female 70.1 11.2
## 4 dead male 63.1 17.7
```

# 6.6.6 Line plot

Line graphs are typically used for visualizing how one continuous variable on the y-axis changes concerning another continuous variable on the x-axis. This is very useful for longitudinal data. Line graphs can also be used with a discrete variable on the x-axis. This is appropriate when the variable is ordered (e.g. "small", "medium", and "large").

Let Us gapminder package and view the variables and the observations of the gapminder dataset.

```
library(gapminder)
gimpse(gapminder)

## Rows: 1,704
## Columns: 6
## $ country <fct> "Afghanistan", "Afghanistan", "Afghanistan", "Afghanistan", -
## $ continent <fct> Asia, Asia, Asia, Asia, Asia, Asia, Asia, Asia, -
## $ year <int> 1952, 1957, 1962, 1967, 1972, 1977, 1982, 1987, 1992,
## $ lifeExp <dbl> 28.01, 30.332, 31.997, 34.020, 36.088, 38.438, 39.854, 40.8-
## $ pop <int> 842533, 9240934, 1026083, 11537966, 1307940, 1488032, 12-
## $ gdpPerCap <dbl> 779.443, 820.858, 853.1007, 836.1971, 739.981, 786.1134, ~
```

We can print the relationship between life expectancy lifeExp only for count- in the Asia continent. To do so, we

+   - select the data. In this case gapminder dataset
- choose only Asia continent using the filter()
- choose variable life expectancy for the y axis and year for the x axis. Then we will give different lines from different countries.
- use geom_line() to generate the line plot

```
gapminder %>%%
filter(continent == "Asia") %>%
gggplot(mapping = aes(x = year, y = lifeExp, linetype = country)) +
geom_line(show.legend = FALSE) +
xlab("Year") + ylab("Life Expectancy") + 
theme_bw()
```