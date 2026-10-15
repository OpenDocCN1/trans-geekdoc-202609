```
```r
penguin_subset_1 <- penguin_subset |>
  fastDummies::dummy_cols()

glimpse(penguin_subset_1, width = 65)
```
```

```
```
## Rows: 6
## Columns: 8
## $ species          <fct> Adelie, Adelie, Chinstrap, Gentoo, Ge~
## $ island           <fct> Biscoe, Torgersen, Dream, Biscoe, Bis~
## $ species_Adelie   <int> 1, 1, 0, 0, 0, 0
## $ species_Chinstrap <int> 0, 0, 1, 0, 0, 0
## $ species_Gentoo   <int> 0, 0, 0, 1, 1, 1
## $ island_Biscoe    <int> 1, 0, 0, 1, 1, 1
## $ island_Dream     <int> 0, 0, 1, 0, 0, 0
## $ island_Torgersen <int> 0, 1, 0, 0, 0, 0
```
```

First, you will notice that we started with two factor variables, species and island; we now have indicator variables for both.

And because there are three species of penguins and three islands, we have three indicator variables for both of the original variables.

In the instance where we have multiple character or factor variables in our source data, we can control which variables get the `dummy_cols()` treatment with the option, `select_columns`. In the example below, the result provides us with an indicator variable for species but not island.

In addition, rather than dropping the first created variable, we can specify that the most frequently occurring value be removed with the argument `remove_most_frequent_dummy = TRUE`. Because there are more Gentoo penguins in our sample of the data, the indicator variable `species_Gentoo` is not created.

```
```r
penguin_subset_2 <- penguin_subset |>
  fastDummies::dummy_cols(
    select_columns = "species",
    remove_most_frequent_dummy = TRUE)

glimpse(penguin_subset_2, width = 65)
```
```

```
```
## Rows: 6
## Columns: 4
## $ species <fct> Adelie, Adelie, Chinstrap, Gentoo, Ge~
## $ island  <fct> Biscoe, Torgersen, Dream, Biscoe, Bis~
```
```