```
    col_names = c("first", "last", "state", "unique_id")
    )
```

```
## # A tibble: 3 x 4
##   first last      state unique_id
##   <chr> <chr>     <chr> <chr>
## 1 Toni  Morrison  IL    DJ-1944-QF96
## 2 Kurt  Vonnegut  IN    XN-5632-TP58
## 3 Walt  Whitman   NY    LW-1752-TD08
```

Note that {readr} will impute the variable type, as it did with the CSV file. And although we won’t implement it in these examples, in the same way read_fwf() allows us to use the col_types specification, as well as na, skip, and others. See the read_fwf() reference at https://readr.tidyverse.org/reference/read_fwf.html for all the details.

Reading this fixed-width file with these three author names worked, but it could break quite easily. We just need one person with three or more components to their name (initials, spaces, or hyphens, as in Ursula K. Le Guin¹ or Ta-Nehisi Coates²), or some missing values, and the inconsistent structure throws off the read_fwf() parser.

In the following example, we read a longer list of author names:

```
authors2_path <- dpjr::dpjr_data("authors2_fwf.txt")

fwf_empty(authors2_path,
    col_names = c("first", "last", "state", "unique_id"))
```

```
## $begin
## [1]  0 20 30
##
## $end
## [1] 19 22 NA
##
## $col_names
## [1] "first"     "last"      "state"     "unique_id"
```

The fwf_empty() function found only three columns, as shown in the “begin” and “end” values that are returned.

¹ https://en.wikipedia.org/wiki/Ursula_K._Le_Guin
² https://en.wikipedia.org/wiki/Ta-Nehisi_Coates