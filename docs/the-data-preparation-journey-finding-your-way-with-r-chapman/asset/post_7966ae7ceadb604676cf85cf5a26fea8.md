
```text
## 4 E06000047 County Durham              522100
## 5 E06000005 Darlington                  107800
## 6 E06000001 Hartlepool                   92300
## # i 19 more variables: aged_4_years_and_under <dbl>,
## #   aged_5_to_9_years <dbl>,
## #   aged_10_to_14_years <dbl>,
## #   aged_15_to_19_years <dbl>,
## #   aged_20_to_24_years <dbl>,
## #   aged_25_to_29_years <dbl>,
## #   aged_30_to_34_years <dbl>, ...
```

The filter() step below does the following:

- selects the area code and the population categories of interest,
- joins the detailed geographic descriptions,
- filters the level 3 values, but this leaves those UA regions that are further disaggregated into the city category.

```r
uk_census_pop_90 <- uk_census_pop_90 |>
  select(area_code, all_persons, aged_90_years_and_over) |>
  full_join(uk_census_geo_code, by = "area_code") |>
  # filter so that only UAs remain
  filter(geo_level == 3)
```

With this table, the proportion of persons aged 90 or older can be calculated and the table sorted in descending order:

```r
uk_census_pop_90 |>
  mutate(
    pct_90_plus =
      round((aged_90_years_and_over / all_persons * 100), 1)
  ) |>
  arrange(desc(pct_90_plus)) |>
  select(area_name, aged_90_years_and_over, pct_90_plus) |>
  slice_head(n = 10)
```

*# A tibble: 10 × 3*

Column types: area_name `<chr>`, aged_90_years_and_over `<dbl>`, pct_90_plus `<dbl>`

| # | area_name | aged_90_years_and_over | pct_90_plus |
|---|-----------|------------------------|------------|
| 1 | Dorset [note 10] | 6300 | 1.7 |
| 2 | East Sussex | 8100 | 1.5 |
| 3 | Conwy | 1700 | 1.5 |
| 4 | Isle of Wight | 2000 | 1.4 |
| 5 | Torbay | 2000 | 1.4 |
| 6 | Devon | 11200 | 1.4 |
| 7 | Herefordshire, C~ | 2400 | 1.3 |
| 8 | West Sussex | 11900 | 1.3 |
| 9 | Bournemouth, Chr~ | 5400 | 1.3 |
| 10 | North Somerset | 2800 | 1.3 |

## 7 Importing data: statistical software

In this chapter:

- Importing survey data from statistical software packages that include labelled data formats, with an emphasis on SPSS
- Importing survey data from an Excel file, including the data dictionary created by survey software, and creating labels from the data dictionary.
- Importing plain-text data and applying syntax from statistical software packages to apply labels and output as statistical software data formats, with an emphasis on SPSS.

### 7.1 Statistical software

If you are one or work with statisticians, economists, sociologists, survey practitioners, and many others, you will find yourself encountering data files created using the software packages SAS, SPSS, and Stata. These tools have been around a long time (SAS and SPSS trace their history back to the late 1960s, and Stata was created in 1985), and over the years they have evolved, demonstrated their robustness, and have become common in many academic, corporate, and government settings.

A feature of these programs is that the variables and the associated values can be labelled. If you’re familiar with R, value labelling is conceptually similar to the use of factor labels. These labels can carry a great deal of detail to which you might otherwise not have easy access.

The R package {haven} (Wickham and Miller, 2021) provides the functionality to read these three types of files¹. There are other packages related to {haven} that we will also use.

```r
library(haven)
```

¹The reference page for {haven} is here: https://haven.tidyverse.org/index.html

In the following examples, we will use versions of the data in the {palmer-penguins} data (Horst et al., 2022; Horst, 2020). We will work with SPSS formatted files; the approach is similar for SAS and Stata formats, and only differs in the details. For example, the haven::read_() functions vary only with the extension; a Stata data file has the extension “.dta”, so the read function is read_dta():

```r
haven::read_dta(dpjr::dpjr_data("penguins.dta"))
```

The equivalent for a SAS file is as follows:

```r
haven::read_sas(dpjr::dpjr_data("penguins.sas"))
```

Here’s the code to read that same data file in SPSS’s “.sav” format and assigns it to an R object penguins_sav:

```r
penguins_sav <- haven::read_sav(dpjr::dpjr_data("penguins.sav"))

penguins_sav
```

*# A tibble: 344 × 8*

Columns: species `<dbl+lbl>`, island `<dbl+lbl>`, bill_length_mm `<dbl>`, bill_depth_mm `<dbl>`, flipper_length_mm `<dbl>`, body_mass_g `<dbl>`, sex `<dbl+lbl>`, year `<dbl>`

| # | species | island | bill_length_mm | bill_depth_mm |
|---|---------|--------|----------------|---------------|
| 1 | 1 [Adelie] | 3 [Torgersen] | 39.1 | 18.7 |
| 2 | 1 [Adelie] | 3 [Torgersen] | 39.5 | 17.4 |
| 3 | 1 [Adelie] | 3 [Torgersen] | 40.3 | 18 |
| 4 | 1 [Adelie] | 3 [Torgersen] | NA | NA |
| 5 | 1 [Adelie] | 3 [Torgersen] | 36.7 | 19.3 |
| 6 | 1 [Adelie] | 3 [Torgersen] | 39.3 | 20.6 |
| 7 | 1 [Adelie] | 3 [Torgersen] | 38.9 | 17.8 |
| 8 | 1 [Adelie] | 3 [Torgersen] | 39.2 | 19.6 |
| 9 | 1 [Adelie] | 3 [Torgersen] | 34.1 | 18.1 |
| 10 | 1 [Adelie] | 3 [Torgersen] | 42 | 20.2 |

*… with 334 more rows, and 4 more variables: flipper_length_mm `<dbl>`, body_mass_g `<dbl>`, sex `<dbl+lbl>`, year `<dbl>`*

You will notice that the values of the variables in the .sav version of the penguins dataframe are different than what was read in from the .csv version. All of the variables, including those that were character strings, are numeric.

For example in the variable “species” the values are a column of “1”s, “2”s, and “3”s instead of being the names of the species.

Note also that in the variable descriptions, it includes <S3: haven_labelled> for those that bring the SPSS labels with them.

### 7.1.1 {labelled}

Once we have read our SAS, SPSS, or Stata data into R using one of the {haven} functions, the package {labelled}(Larmarange, 2022) gives us a range of powerful tools for working with the variable labels, value labels, and defined missing values.

```r
library(labelled)
```

The first function we will use is look_for(), which returns the labels, column types, and values of the variables in our data.

```r
look_for(penguins_sav)
```

| pos | variable | label | col_type | missing | values |
|-----|----------|-------|----------|---------|--------|
| 1 | species | – | dbl+lbl | 0 | [1] Adelie, [2] Chinstrap, [3] Gentoo |
| 2 | island | – | dbl+lbl | 0 | [1] Biscoe, [2] Dream, [3] Torgersen |
| 3 | bill_length_mm | – | dbl | 2 | |
| 4 | bill_depth_mm | – | dbl | 2 | |
| 5 | flipper_length_mm | – | dbl | 2 | |
| 6 | body_mass_g | – | dbl | 2 | |
| 7 | sex | – | dbl+lbl | 11 | [1] female, [2] male |
| 8 | year | – | dbl | 0 | |

In this view, we can spot the species names in the “values” column. Also notice that the “col_type” column shows “dbl+lbl”: double and label. In this dataframe, no labels have been defined.

The function var_label() allows us to add a descriptive label to a variable. In the next code chunk, we add a label to the species variable:

```r
var_label(penguins_sav$species) <- "Penguin species"
```

We can see that the label is now incorporated into the dataframe using the look_for() function:

```r
look_for(penguins_sav)
```

| pos | variable | label | col_type | missing | values |
|-----|----------|-------|----------|---------|--------|
| 1 | species | Penguin species | dbl+lbl | 0 | [1] Adelie, [2] Chinstrap, [3] Gentoo |
| 2 | island | – | dbl+lbl | 0 | [1] Biscoe, [2] Dream, [3] Torgersen |
| 3 | bill_length_mm | – | dbl | 2 | |
| 4 | bill_depth_mm | – | dbl | 2 | |
| 5 | flipper_length_mm | – | dbl | 2 | |
| 6 | body_mass_g | – | dbl | 2 | |
| 7 | sex | – | dbl+lbl | 11 | [1] female, [2] male |
| 8 | year | – | dbl | 0 | |

It’s also possible to add multiple labels. Note that in this example, a label is added to both “dbl+lbl” and “dbl” types.

```r
var_label(penguins_sav) <- list(island = "Island of record",
    body_mass_g = "Weight, in grams")
```

```r
look_for(penguins_sav)
```

| pos | variable | label | col_type | missing | values |
|-----|----------|-------|----------|---------|--------|
| 1 | species | Penguin species | dbl+lbl | 0 | [1] Adelie, [2] Chinstrap, [3] Gentoo |
| 2 | island | Island of record | dbl+lbl | 0 | [1] Biscoe, [2] Dream, [3] Torgersen |
| 3 | bill_length_mm | – | dbl | 2 | |
| 4 | bill_depth_mm | – | dbl | 2 | |
| 5 | flipper_length_mm | – | dbl | 2 | |
| 6 | body_mass_g | Weight, in grams | dbl | 2 | |
| 7 | sex | – | dbl+lbl | 11 | [1] female, [2] male |
| 8 | year | – | dbl | 0 | |

