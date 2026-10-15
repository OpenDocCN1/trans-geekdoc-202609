
In this first solution, we name the largest provinces separately:

```
canpop |>
  mutate(pt_grp = case_when(
    # evaluation ~ new value
    province_territory == "Ontario" ~ "Ontario",
    province_territory == "Quebec" ~ "Quebec",
    province_territory == "British Columbia" ~ "British Columbia",
    province_territory == "Alberta" ~ "Alberta",
    # all others get recoded as "other"
    TRUE ~ "other"
  ))
```

```
## # A tibble: 13 × 3
##   province_territory      population pt_grp
##   <chr>                       <dbl> <chr>
## 1 Ontario                  13448494 Ontario
## 2 Quebec                    8164361 Quebec
## 3 British Columbia          4648055 British Columbia
## 4 Alberta                   4067175 Alberta
## 5 Manitoba                  1278365 other
## 6 Saskatchewan              1098352 other
## 7 Nova Scotia                923598 other
## 8 New Brunswick              747101 other
## 9 Newfoundland and Labrador  519716 other
## 10 Prince Edward Island      142907 other
## 11 Northwest Territories      41786 other
## 12 Nunavut                    35944 other
## 13 Yukon                      35874 other
```

But that's a lot of typing. A more streamlined approach is to put the name of our provinces in a list, and then recode our new variable with the value from the original variable province_territory:

```
canpop |>
  mutate(pt_grp = case_when(
    province_territory %in%
      c("Ontario", "Quebec", "British Columbia", "Alberta") ~
      province_territory,
    TRUE ~
      "other"
  ))
```

```
## # A tibble: 13 × 3
##   province_territory      population pt_grp
##   <chr>                       <dbl> <chr>
## 1 Ontario                  13448494 Ontario
## 2 Quebec                    8164361 Quebec
## 3 British Columbia          4648055 British Columbia
## 4 Alberta                   4067175 Alberta
## 5 Manitoba                  1278365 other
## 6 Saskatchewan              1098352 other
## 7 Nova Scotia                923598 other
## 8 New Brunswick              747101 other
## 9 Newfoundland and Labrador  519716 other
## 10 Prince Edward Island      142907 other
## 11 Northwest Territories      41786 other
## 12 Nunavut                    35944 other
## 13 Yukon                      35874 other
```

We could also use a comparison to create a population threshold, in this case four million:

```
canpop <- canpop |>
  mutate(pt_grp = case_when(
    population > 4000000 ~ province_territory,
    TRUE ~ "other"
  ))

canpop
```

```
## # A tibble: 13 × 3
##   province_territory      population pt_grp
##   <chr>                       <dbl> <chr>
## 1 Ontario                  13448494 Ontario
## 2 Quebec                    8164361 Quebec
## 3 British Columbia          4648055 British Columbia
## 4 Alberta                   4067175 Alberta
## 5 Manitoba                  1278365 other
## 6 Saskatchewan              1098352 other
## 7 Nova Scotia                923598 other
## 8 New Brunswick              747101 other
## 9 Newfoundland and Labrador  519716 other
## 10 Prince Edward Island      142907 other
## 11 Northwest Territories      41786 other
## 12 Nunavut                    35944 other
## 13 Yukon                      35874 other
```

Whatever the approach we choose, that new variable can be used to group a table:

```
canpop |>
  group_by(pt_grp) |>
  summarize(pt_pop = sum(population)) |>
  arrange(desc(pt_pop))
```

```
## # A tibble: 5 × 2
##   pt_grp          pt_pop
##   <chr>            <dbl>
## 1 Ontario        13448494
## 2 Quebec          8164361
## 3 other           4823643
## 4 British Columbia 4648055
## 5 Alberta         4067175
```

### 12.4.1 Classification systems

As we start to create new variables in our data, it is useful to be aware of various classification systems that already exist. That way, you can:

- save yourself the challenge of coming up with your own classifications for your variables, and
- ensure that your analysis can be compared to other results.

Of course, these classification systems are subject-matter specific.

As one example, in much social and business data, people's ages are often grouped into 5-year “bins”, starting with ages 0–4, 5–9, 10–14, and so on. But not all age classification systems follow this; it will be driven by the specific context. The demographics of a workforce will not require a “0–4” category, while an analysis of school-age children might group them by the ages they attend junior, middle, and secondary school. As a consequence, many demographic tables will provide different data sets with the ages grouped in a variety of ways. (For an example, see (Statistics Canada, 2007).)

And be aware that the elements with a classification system can change over time. One familiar example is that the geographical boundaries of cities and countries of the world have changed. City boundaries change, often with the more populous city expanding to absorb smaller communities within the larger legal entity. (The current City of Toronto is an amalgamation of what were six smaller municipalities.) Some regions have a rather turbulent history of changes in their boundaries, and some countries have been created only to disappear a few years later.

If you’re working in the area of social and economic research, the national and international statistics agencies provide robust and in-depth classification systems, many of which are explicitly designed to allow for international comparisons. These systems cover a wide range of economic and social statistics. Earlier in this chapter there was an example using the North American Industry Classification System (NAICS), used in Canada, the United States, and Mexico. (Executive Office of the President, Office of Management and Budget, 2022, Statistics Canada (2022); see also Statistics Canada, 2020). A similar classification system exists for Australia and New Zealand (Australian Bureau of Statistics, 2006), and the European Union’s Eurostat office publishes a standard classification system for the products that are created through mining, manufacturing, and material recovery (EUROSTAT PRODCOM team, 2022). For international statistics, you can start with the classification system maintained by the United Nations Statistics Division (United Nations Statistics Division, 2020). In Chapter 6, we saw population statistics reported by the administrative geography of England and Wales.

Following these standardized categories in our own work is advantageous. It provides us with a validated structure, and should it be appropriate, gives us access to other data that can be incorporated into our own research.

Your subject area has established classifications; seek them out and use them. Ensuring that your data can be combined with and compared to other datasets will add value to your analysis, and make it easier for future researchers (including future you!) to work with your data. (White et al., 2013)

### 12.5 Indicator variables

> To include a categorical variable in a regression, a natural approach is to construct an ‘indicator variable’ for each category. This allows a separate effect for each level of the category, without assuming any ordering or other structure on the categories. (Gelman et al., 2014, p.366)

Indicator variables are also known as dummy variables (Suits, 1957) and “one hot” encoding.

Examples of this approach abound. It can be a useful approach in forecasting methods; Hyndman and Athanasopoulos provide examples where public holidays and days of the week are set as dummy variables (Hyndman and Athanasopoulos, 2021, section 7.4 “Some useful predictors”).

It is also a common approach in social data analysis, where categorical variables are used to code information. In the section on “Discrimination and collider bias” in (Cunningham, 2021, pp.106–110), the data are represented in the following way⁴:

```
## # A tibble: 6 × 5
##    female ability discrimination occupation   wage
##    <dbl>  <dbl>              <dbl>      <dbl>  <dbl>
## 1      0  -0.786                 0     -0.555  0.162
## 2      1   2.81                  1      4.93  11.6
## 3      1  -0.977                 1     -4.23  -5.86
## 4      0   1.75                  0      3.95  10.4
## 5      0   0.152                 0      2.11   4.77
## 6      1  -0.561                 1     -1.48  -3.41
```

In this data, the variable female is coded as numeric, so it can be used as part of the regression modelling.

More commonly, though, this variable will have been captured and saved in one called gender or sex, and often as a character string. The source data for the above table might have originally looked like this:

```
tb2 <- tb |> 
  dplyr::rename(gender = female) |>
  mutate(gender = case_when(
    gender == 1 ~ "female",
    TRUE ~ "male"
  ))
```

```
tb2
```

```
## # A tibble: 10 × 5
##    gender ability discrimination occupation   wage
```

⁴ Note: the data in this table is different from what appears in *Causal Inference: The Mixtape*, since the values in the data in that source are randomly generated.
