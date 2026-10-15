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