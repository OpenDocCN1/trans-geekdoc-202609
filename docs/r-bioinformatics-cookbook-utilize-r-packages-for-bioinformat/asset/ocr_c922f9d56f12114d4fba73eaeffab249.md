3. Add a new list column, holding the results of tidying the linear model:

```
library (broom)
nested_mt_list_cols <- nested_mt_list_cols |>
mutate (tidy_model = map(model, tidy))
```

4. Unnest the dataframe:

```
simple_df <- unnest(nested_mt_list_cols, tidy_model)
```

This is how we work with nested dataframes.

# How it works...

First, we create a nested dataframe in step 1. We use the nest () function from tidyr to nest the mtcars dataframe. The - option tells the functions which columns to exclude from being collapsed into the nested part of the dataframe. This effectively makes the cyl column a factor on which subsets are created. It's conceptually similar to the dplyr::group_by () function, which you may be already familiar with. Inspecting the object classes what has happened:

```
## A tibble: 3 x 2
## cyl data
## <dbl> <list>
## 1 6 <tibble [7 x 10]>
## 2 4 <tibble [11 x 10]>
## 3 8 <tibble [14 x 10]>
```

The nested dataframe contains a new called column, into which the nested data has been collapsed. Each nested dataframe contains the rows from the original dataframe that had the value of each cyl displayed.

In step 2, we create a new column on our nested dataframe by mutate (). Within the mutate () call, we use the map () function from purrr to iterate over each of the sub-dataframes in the named column and apply the named function. The map data lm(...), so we iterate each mini-dataframe in the larger one and apply lm () to the mini-dataframe. Within the function, the new .x is very idiomatic, indicating the thing we're currently working on - the mini-dataframe. The nested dataframe looks like this:

```
## A tibble: 3 x 3
## cyl data
## <dbl> <list>
## 1 6 <tibble [7 x 10]> <lm>
## 2 4 <tibble [11 x 10]> <lm>
## 3 8 <tibble [14 x 10]> <lm>
```

A new column called model contains an lm () object at each value of cyl.