For the second analysis, we might be interested in determining if there is any seasonality in the Canadian labour force:

```
lfs_canada_employment |>
  group_by(month(REF_DATE)) |>
  summarize(mean(VALUE))
```

```
## # A tibble: 12 x 2
##  `month(REF_DATE)` `mean(VALUE)`
##                 <dbl>         <dbl>
## 1                1        17841.
## 2                2        17960.
## 3                3        17907.
## 4                4        17848.
## 5                5        18255.
## 6                6        18539.
## 7                7        18514.
## 8                8        18514.
## 9                9        18423.
## 10              10        18458.
## 11              11        18421.
## 12              12        18369.
```

# 12.3  Cleaning strings

> “Strings are not glamorous, high-profile components of R, but they do play a big role in many data cleaning and preparation tasks.” —{stringr} reference page

R provides some robust tools for working with character strings. In particular, the {stringr}(Wickham, 2019b) package is very flexible. But before we get there, we need to take a look at regular expressions.

# 12.3.1  Regular expressions

> “Some people, when confronted with a problem, think: ‘I know, I’ll use regular expressions.’ Now they have two problems.” — Jamie Zawinski

Regular expressions are a way to specify a pattern of characters. This pattern