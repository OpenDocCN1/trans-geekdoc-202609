```
glimpse(tb3_2, width = 65)
```

```
## Rows: 10
## Columns: 6
## $ gender      <fct> male, female, female, male, male, female~
## $ ability      <dbl> -0.78648, 2.81050, -0.97717, 1.74628, 0.~
## $ discrimination <dbl> 0, 1, 1, 0, 0, 1, 1, 0, 1, 1
## $ occupation    <dbl> -0.5551, 4.9340, -4.2303, 3.9487, 2.1148~
## $ wage          <dbl> 0.1616, 11.6113, -5.8595, 10.4124, 4.774~
## $ gender_female <int> 0, 1, 1, 0, 0, 1, 1, 0, 1, 1
```

There is also an option in fastDummies::dummy_cols() to remove_most_frequent_dummy = TRUE. In our discrimination data, there are more observations coded as “female”, so the variable gender_female is not included.

```
tb2_frequent <- tb2 |>
  fastDummies::dummy_cols(remove_most_frequent_dummy = TRUE)

glimpse(tb2_frequent, width = 65)
```

```
## Rows: 10
## Columns: 6
## $ gender      <chr> "male", "female", "female", "male", "mal~
## $ ability      <dbl> -0.78648, 2.81050, -0.97717, 1.74628, 0.~
## $ discrimination <dbl> 0, 1, 1, 0, 0, 1, 1, 0, 1, 1
## $ occupation    <dbl> -0.5551, 4.9340, -4.2303, 3.9487, 2.1148~
## $ wage          <dbl> 0.1616, 11.6113, -5.8595, 10.4124, 4.774~
## $ gender_male   <int> 1, 0, 0, 1, 1, 0, 0, 1, 0, 0
```

Another argument in the function is remove_selected_columns. The default value is FALSE, but if the argument is set to TRUE, the source column is excluded from the output.

```
tb2_select <- tb2 |>
  fastDummies::dummy_cols(remove_selected_columns = TRUE)

glimpse(tb2_select, width = 65)
```

```
## Rows: 10
```