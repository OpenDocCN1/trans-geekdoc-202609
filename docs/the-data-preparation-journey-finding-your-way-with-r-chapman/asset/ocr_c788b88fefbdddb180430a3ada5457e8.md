```
# read the contents of the CSV file
penguins_data <- read_csv(penguins_path)
```

```
Rows: 344 Columns: 8— Column specification
Delimiter: ","
chr (3): species, island, sex
dbl (5): bill_length_mm, bill_depth_mm, flipper_length_mm, body_mass_g, year
i Use `spec()` to retrieve the full column specification for this data.
i Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

# FIGURE 5.1 read_csv message.

The function returns a message letting us know the type that each variable is assigned.

The arguments of the {readr} package allow a lot of control over how the file is read. Of particular utility are the following:

| argument | purpose |
|---|---|
| col_types = cols() | define variable types |
| na = "" | specify which values you want to be turned into NA |
| skip = 0 | specify how many rows to skip; the default is 0 |
| n_max = Inf | the maximum number of records to read; the default is Inf for infinity, interpreted as the last row of the file |

Adding the col_types = cols() parameter has two benefits. First, defining the variable type avoids errors (such as numeric fields will be read as such, and not as characters) and speeds up the read process since R doesn't have to check and infer the variable type.

Second, it allows us to alter what {readr} has decided for us. For example, we could set the species variable to be a factor type variable.

When we show the entire table, we can see that the variable species is now a factor type.

```
penguins_data <- read_csv(penguins_path,
    col_types =
      cols(species = col_factor()))
penguins_data
```