
# 5 Simple Linear Regression

(LC5.10) Which of the following statements is true about the regression line in a simple linear regression model?

- A. The regression line represents the average of the outcome variable.
- B. The regression line minimizes the sum of squared differences between the observed and predicted values.
- C. The regression line always has a slope of zero.
- D. The regression line is only useful when there is no correlation between variables.

# 5.2 One categorical explanatory variable

It is an unfortunate truth that life expectancy is not the same across all countries in the world. International development agencies are interested in studying these differences in life expectancy in the hopes of identifying where governments should allocate resources to this problem. In this section, we explore differences in life expectancy in two ways:

- Differences between continents: Are there significant differences in average life expectancy between the six populated continents of the world: Africa, North America, South America, Asia, Europe, and Oceania?
- Differences within continents: How does life expectancy vary within the world's five continents? For example, is the spread of life expectancy among the countries of Africa larger than the spread of life expectancy among the countries of Asia?

To answer such questions, we use an updated version of the gapminder data frame we visualized in Figure 2.1 in Subsection 2.1.2 on the grammar of graphics. This updated data `un_member_states_2024` we worked with earlier in this chapter, and it is included in the modernverse package. This dataset has international development statistics such as life expectancy, GDP per capita, and population for 193 countries for years near 2024.

We use this data for basic regression again, but now using an explanatory variable $x$ that is categorical, as opposed to the numerical explanatory variable model we used in the previous Section 5.1.

- A numerical outcome variable $y$ (a country's life expectancy) and
- A single categorical explanatory variable $x$ (the continent that the country is a part of).

When the explanatory variable $x$ is categorical, the concept of a "best-fitting" regression is a little different than the one we saw previously in Section 5.1 where the explanatory variable $x$ was numerical. We study these differences shortly in Subsection 5.2.2, but we first conduct an exploratory data analysis.

### 5.2.1 Exploratory data analysis

Data on the 193 countries can be found in the `un_member_states_2024` data frame included in the moderndive package. However

```r
gapminder2022 <- un_member_states_2024 |
  select(country, life_exp = life_expectancy_2022, continent,
         gdp_per_capita) |>
  na.omit()
```

We perform the first common step in an exploratory data analysis: looking at the raw data values. You can do this by using RStudio's spreadsheet viewer or by using the `glimpse()` command as introduced in Subsection 1.4.3 on exploring data frames:

```r
glimpse(gapminder2022)
```

Rows: 188
Columns: 4
$ country <chr> "Afghanistan", "Albania", "Algeria", "Andorra", "..."
$ life_exp <dbl> 53.6, 79.5, 78.0, 83.4, 62.1, 77.8, 78.3, 76.1, 83...
$ continent <fct> Asia, Europe, Africa, Europe, North America...
$ gdp_per_capita <dbl> 356, 6810, 4343, 41993, 3000, 19260, 13651, 7018...

Observe that Rows: 188 indicates there are 188 rows/observations in gapminder2022, where each row corresponds to one country. In other words, the *observational unit* is an individual country. Furthermore, observe that the variable continent is of type `<fct>`, which stands for *factor*, that is R's way of encoding categorical variables.

A full description of all the variables in `un_member_states_2024` can be found by reading the associated help file (run `un_member_states_2024` in the console). However, we fully describe only the 4 variables we selected in gapminder2022:

- 1. country: An identification variable of type character/text used to distinguish the 142 countries in the dataset.
- 2. life_exp: A numerical variable of that country’s life expectancy at birth. This is the outcome variable $y$ of interest.
- 3. continent: A categorical variable with five levels. “levels” correspond to the possible categories: Africa, Asia, Americas, Europe, and Oceania. This is the explanatory variable $x$ of interest.
- 4. gdp_per_capita: A numerical variable of that country’s GDP per capita in US inflation-adjusted dollars that we’ll use as another outcome variable $y$ in the Learning check at the end of this subsection.

We next look at a random sample of three out of the 188 countries in Table 5.4.

```r
gapminder2022 |> sample_n(size = 3)
```

# TABLE 5.4: Random sample of 5 out of 193 countries

| country | life_exp | continent | gdp_per_capita |
|---|---|---|---|
| Panama | 77.6 | North America | 17358 |
| Micronesia, Federated States of | 74.4 | Oceania | 3714 |
| Burundi | 67.4 | Africa | 259 |
| United Arab Emirates | 79.6 | Asia | 53708 |
| India | 67.2 | Asia | 241 |

Random sampling will likely produce a different subset of 3 rows for what that’s showing now. Now that we have looked at the raw values in our gapminder2022 data frame and got a sense of the data, we compute summary statistics. We again apply tidy_summary() from the modernverse package. Recall that this function takes in a data frame, summarizes it, and returns common summary statistics. We take our gapminder2022 data frame, select the outcome and continent, and pipe them into tidy_summary():

```r
gapminder2022 |> select(life_exp, continent) |> tidy_summary()
```

# TABLE 5.5: Summary of life expectancy

| column | n | type | min | Q1 | median | Q3 | max | sd |
|---|---|---|---|---|---|---|---|
| life_exp | 188 | numeric | 53.6 | 69.4 | 75.2 | 78.4 | 89.6 | 11.9 |
| Africa | 44 | fct | | | | | | |
| Asia | 53 | fct | | | | | | |
| Americas | 39 | fct | | | | | | |
| Europe | 36 | fct | | | | | | |
| Oceania | 14 | fct | | | | | | |

We see that this data is left-skewed, also known as negatively skewed: there are a few countries with low life expectancy that are bringing down the mean. However, the median is less sensitive to the effects of such outliers; the median is greater than the mean.

Remember, that we want to compare life expectations both between and within continents. In other words, our visualizations need some notion of the continent. We can do this easily with a faceted histogram. Recall from Section 2.6 that facets us to split a visualization by the different values of another variable. We display the resulting visualization in Figure 5.7 by adding a facet_wrap(~ continent, nrow = 2).

```r
ggplot(gapminder2022, aes(x = life_exp)) +
  geom_histogram(binwidth = 5, color = "white") +
  labs(x = "Number of countries",
       title = "Histogram of distribution of worldwide expectancies") +
  facet_wrap(~ continent, nrow = 2)
```

![](img/44572518041017e8f011b0c31d9169_0.png)

**FIGURE 5.6:** Histogram of life expectancy in 2022.
