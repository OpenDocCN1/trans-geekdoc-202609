# 5.8 More Complicated dplyr Verbs

+   - sex
- outcome

```
pep2 %>%
group_by(sex) %>%ncount(outcome, sort = TRUE)
```

```
## # A tibble: 4 x 3
## # Groups: sex [2]
## # <chr> <chr> <int>
## # 1 male alive 70
## # 2 male dead 26
## # 3 female alive 13
## # 4 female dead 12
```

```
pep2 %>%
count(sex, outcome, sort = TRUE)
```

```
## sex outcome n
## 1 male alive 70
## 2 male dead 26
## 3 female alive 13
## 4 female dead 12
```

# 5.8 More Complicated dplyr Verbs

To be more efficient, use multiple dplyr (a package inside tidyverse meta-package) functions in one line of R code. For example,

```
pep2 %>%
filter(sex == "male", diastolic >= 60, systolic >= 80) %>%
dplyr::select(age, systolic, diastolic, perforation, outcome) %>%%
group_by(outcome) %>%%
summarize(mean_sbp = mean(systolic, na.rm = TRUE),
mean_dbp = mean(diastolic, na.rm = TRUE),
mean_perf = mean(perforation, na.rm = TRUE),
freq = n())
```