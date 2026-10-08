# 6 Exploratory Data Analysis

```
# $ ASA
<dbl> 1, 1, 1, 1, 2, 1, 2, 1, 1, 2, 1, 2, -
```

```
# $ systolic
<dbl> 141, 197, 126, 90, 147, 115, 103, 159, 145, 185,
```

```
# $ diastolic
<dbl> 98, 88, 73, 40, 82, 56, 58, 65, 74, 50, 86-
```

```
# $ intropes
<chr> "no", "no", "no", "no", "no", "no", "n-
```

```
# $ pulse
<dbl> 109, 126, 64, 112, 89, 96, 100, 57, 100, 109, -
```

```
# $ tenderness
<chr> "generalized", "generalized", "generalized", "Loca-
```

```
# $ guarding
<chr> "yes", "yes", "yes", "yes", "yes", "n", -
```

```
# $ hemoglobin
<dbl> 18.0, 12.0, 12.0, 11.0, 8.1, 13.3, 11-
```

```
# $ twc
<dbl> 6.0, 6.3, 13.0, 21.0, 4.0, 5.0, 12.0, 6.0-
```

```
# $ platelet
<dbl> 2, 3, 2, 7, 1, 2, 5, 4, 3, 6, 5, 1,
```

```
# $ creatinine
<dbl> 135, 66, 84, 137, 102, 69, 92, 94, 104, 58, 24-
```

```
# $ albumin
<chr> "27", "32", "42", "38", "30", "41"
```

```
# $ PULP
<dbl> 2, 3, 2, 7, 1, 2, 5, 4, 3, 6, 5, 1, -
```

```
# $ perforation
<dbl> 0.5, 1.0, 0.5, 1.0, 3.0, 1.5, 0.5, 1.5, -
```

There are quite several variables. For the sake of simplicity, we will select various by
which we might be important for data exploration using the select()

```
pep <- pep%
select(age, systolic, diastolic, hemoglobin, twc,
ASA, PULP, perforation, epigastric_pain,
malena, tenderness, decomposition, outcome)
```

# 6.5 EDA in Tables

We can get the overall descriptive statistics of the peptic ulcer data using the
tbl_summary.function.

```
pep <- pep%
tbl_summary(
```