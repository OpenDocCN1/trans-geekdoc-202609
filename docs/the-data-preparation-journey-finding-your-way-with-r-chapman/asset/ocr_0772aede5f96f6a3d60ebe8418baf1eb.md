In the version below, only the final line changes. All of the other indentation values have been evaluated, so it doesn’t require the “–if” and the associated evaluation, nor does it require the “–up” of the direction.

```
```r
uk_census_behead <- uk_census |>
  dplyr::filter((row >= 7)) |>
  filter(col != 1) |>
  behead_if(indent[local_format_id] == 0,
            direction = "left-up", name = "field0") |>
  behead_if(indent[local_format_id] == 1,
            direction = "left-up", name = "field1") |>
  behead_if(indent[local_format_id] == 2,
            direction = "left-up", name = "field2") |>
  behead_if(indent[local_format_id] == 3,
            direction = "left-up", name = "field3") |>
  behead(direction = "left", name = "field4")
```
```

In the code below, the addition is the assignment of column headers. In the UK Census data, the structure is not particularly complex, but {tidyr} can also deal with nested hierarchy in the headers as well.

```
```r
# from the previous chunk:

uk_census_behead <- uk_census |>
  dplyr::filter((row >= 7)) |>
  filter(col != 1) |>
  behead_if(indent[local_format_id] == 0,
            direction = "left-up", name = "field0") |>
  behead_if(indent[local_format_id] == 1,
            direction = "left-up", name = "field1") |>
  behead_if(indent[local_format_id] == 2,
            direction = "left-up", name = "field2") |>
  behead_if(indent[local_format_id] == 3,
            direction = "left-up", name = "field3") |>
  behead(direction = "left", name = "field4") |>
# now strip (behead) the column names
  behead(direction = "up", name = "gender") |>
# add row strips to preserve visual compatibility
  arrange(row)
```
```

Did we get the results we expected? Let’s do some quick checks of the data,