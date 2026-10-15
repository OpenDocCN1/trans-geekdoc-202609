```
# mutate new values
# --note that creating three separate variables allows for comparisons
#   as the values change from one step to the next
pc_kimberley_tbl |>
  # extract the postal codes
  mutate(pc_extract = str_extract(value, postalcode)) |>
  # remove space or hyphen
  mutate(pc_remove = str_remove(pc_extract, "[ -]")) |>
  # change to upper case
  mutate(pc_upper = str_to_upper(pc_remove))
```

```
## # A tibble: 4 x 4
##   value      pc_extract pc_remove pc_upper
##   <chr>      <chr>      <chr>     <chr>
## 1 V1A2B3     V1A2B3     V1A2B3    V1A2B3
## 2 V1A 2B3    V1A 2B3    V1A2B3    V1A2B3
## 3 v1a 2B3xyz v1a 2B3    v1a2B3    V1A2B3
## 4 v1a-2b3    v1a-2b3    v1a2b3    V1A2B3
```

# 12.3.2.3  Split and combine strings

Below, we split an address based on comma and space location, using the str_split() function.

```
UVic_address <- 
  "Continuing Studies,
  3800 Finnerty Rd,
  Victoria, BC,
  V8P 5C2"

str_split(UVic_address, ", ")
```

```
## [[1]]
## [1] "Continuing Studies,\n  3800 Finnerty Rd"
## [2] "\n  Victoria"
## [3] "BC"
## [4] "\n  V8P 5C2"
```

{stringr} contains three useful functions for combining strings. str_c() collapses multiple strings into a single string, separated by whatever we specify (the default is nothing, that is to say, "").