```
```r
uk_census_behead_revised |>
  mutate(subtotal_row = case_when(
    field3 %in% field3_split$field3 & is.na(field4) ~ "subtotal",
    TRUE ~ NA_character_
  )) |>
  relocate(subtotal_row)
```
```

```
```text
## # A tibble: 1,125 x 8
##   subtotal_row field0      field1 field2 field3 field4
##   <chr>        <chr>       <chr>  <chr>  <chr>  <chr>
## 1 subtotal     England an~ <NA>   <NA>   <NA>   <NA>
## 2 subtotal     England an~ <NA>   <NA>   <NA>   <NA>
## 3 subtotal     England an~ <NA>   <NA>   <NA>   <NA>
## 4 subtotal     England an~ Engla~ <NA>   <NA>   <NA>
## 5 subtotal     England an~ Engla~ <NA>   <NA>   <NA>
## 6 subtotal     England an~ Engla~ <NA>   <NA>   <NA>
## 7 subtotal     England an~ Engla~ North~ <NA>   <NA>
## 8 subtotal     England an~ Engla~ North~ <NA>   <NA>
## 9 subtotal     England an~ Engla~ North~ <NA>   <NA>
## 10 <NA>        England an~ Engla~ North~ Count~ <NA>
## # ℹ 1,115 more rows
## # ℹ 2 more variables: gender <chr>, numeric <dbl>
```
```

# ## Approach 3 - build a concordance table

If we need a more flexible and re-usable approach, we can consider the option of creating a separate concordance table (also known as a crosswalk table). A table of this sort contains the distinct values of key variables and their corresponding values in another typology or schema. Once a table like this is built, it can be joined to our data, as well as to any other table we might need to use in the future.

For the UK Census data, we will create two separate concordance tables. We will save these tables as CSV files, so they are readily available for other instances when their use will make filtering and summarizing the data more efficient.

For the first table, we will build a table with each type of administrative region and its associated three-digit code. This is done programatically in R, using the {tibble} package (Müller and Wickham, 2021). We will use the tribble() function, which transposes the layout so it resembles the final tabular structure.

In addition to the area code prefix and the name of the administrative region type, the level in the hierarchy is also encoded in this table.