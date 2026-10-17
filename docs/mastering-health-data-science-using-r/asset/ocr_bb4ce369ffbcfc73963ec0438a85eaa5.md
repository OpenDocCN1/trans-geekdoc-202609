# Table 22.2: Head of the NHANES Sample Dataset

| Age | Sex | Education Level | Poverty Income Ratio | Lead Level |
|---:|---|---|---:|---:|
| 77 | Male | MoreThanHS | 5.00 | 5.0 |
| 49 | Male | MoreThanHS | 5.00 | 1.6 |
| 37 | Male | MoreThanHS | 4.93 | 2.4 |
| 70 | Male | LessThanHS | 1.07 | 1.6 |
| 81 | Male | LessThanHS | 2.67 | 5.5 |
| 38 | Female | MoreThanHS | 4.52 | 1.5 |

In the previous code chunk, we saw that kable() produces a much nicer table in the knitted pdf that is more suitable for a data analysis report. In Chapter 4, we also introduced the gt package. This package is an alternative package to kableExtra that allows you to format each part of the table and includes options for formatting the columns, adding footers or subtitles, or grouping your table. See the package introduction⁵ for more details about this package. An example gt table is given in the following code and output. Note that for tables, we want to start our label with tbl- and can include a caption using the tbl-cap option. The resulting table from the code chunk below is shown in Figure 22.7.

```
```{r}
#| label: tbl-gt-ex
#| tbl-cap: ”Head of the NHANES Sample Data”

NHANESsample %>%
  select(AGE, SEX, EDUCATION, INCOME, LEAD) %>%
  head() %>%
  gt() %>%
  tab_header(title = ”Head of the NHANES Sample Data”) %>%
  cols_label(AGE ~ ”Age”,
    SEX ~ ”Sex”,
    EDUCATION ~ ”Education Level”,
    INCOME ~ ”Poverty Income Ratio”,
    LEAD ~ ”Lead Level”)
```
```

# 22.3.1  Using References

Quarto automatically adds figure and table numbers to the figures and tables in your report. By using the label options, we can also reference our figures

⁵ https://gt.rstudio.com/articles/intro-creating-gt-tables.html