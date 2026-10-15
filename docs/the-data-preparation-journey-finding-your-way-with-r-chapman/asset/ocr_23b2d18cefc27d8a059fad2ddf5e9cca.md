##  <chr>  <chr>  <chr>  <chr>
## 1 Adelie  Biscoe  188.7955  3709.659
## 2 Adelie  Dream  189.7321  3688.393
## 3 Adelie  Torgersen 191.1961  3706.373
## 4 Chinstrap Dream  195.8235  3733.088
## 5 Gentoo  Biscoe  217.1870  5076.016

There is one final step: to change the variable types of the values to numeric.

```
penguin_table <- penguin_table |>
  mutate(
    across(
      contains("mean_"),
      ~ as.numeric(.x)
    )
  )

penguin_table
```

## # A tibble: 5 x 4
## species island mean_flipper_length_mm mean_body_mass_g
## <chr> <chr> <dbl> <dbl>
## 1 Adelie Biscoe 189. 3710.
## 2 Adelie Dream 190. 3688.
## 3 Adelie Torgersen 191. 3706.
## 4 Chinstrap Dream 196. 3733.
## 5 Gentoo Biscoe 217. 5076.

# 8.1.2 Extended example: ferry traffic

For this exercise, we will extract a data table from Annual Report to the British Columbia Ferries Commissioner for the fiscal year ending March 31, 2021 (that is, the twelve month period from 2020-04-01 to 2021-03-31) (British Columbia Ferry Services Inc., 2021).

This report is published as a PDF file that is 101 pages long and contains a mixture of written text and data tables.

{pdftools} gives us the ability to download and read the file from a local copy or from the web. The chunk below shows the code to download the file from a URL.