2. Specify a vector of new names for columns:

```
col_names = c(
  c("area_code", "country", "region",
  "area_name", "all_persons", "under_4"),
  paste0(
  seq(5, 85, by = 5),
  "_to_",
  seq(9, 89, by = 5)),c("over_90")
)
```

3. Set the column types by new names and on contents:

```
col_types = cols(
  area_code = col_character(),
  country = col_factor(levels = c("England", "Wales")),
  region = col_factor(levels = c("North East",
  "Yorkshire Humber",
  "East Midlands",
  "West Midlands",
  "East of \n  "England",  "London",
  "South East",
  "South West",
  "Wales"), ordered = TRUE),
  area_name = col_character(),
  .default = col_number()
)
```

4. Put it together and read the file:

```
df <- read_csv(filename,
  skip = 8,
  col_names = col_names,
  col_types = col_types)
```

And with that, we've loaded in a file with careful checking of the data types.

# How it works...

Step 1 loads the library (readr) package. This package contains functions for reading and writing tabular data in a variety of formats, including CSV. The fs::path_package("extdata",
"census_2021.csv", package="rbioinfocookbook") function is used to create a file
path to the census_2021.csv file. It simply finds the place where the rbioinfocookbook