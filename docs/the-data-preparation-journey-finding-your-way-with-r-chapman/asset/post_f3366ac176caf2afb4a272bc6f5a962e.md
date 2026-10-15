
```
    col_names = c("first", "last", "state", "unique_id")
    )
```

```text
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

```r
authors2_path <- dpjr::dpjr_data("authors2_fwf.txt")

fwf_empty(authors2_path,
    col_names = c("first", "last", "state", "unique_id"))
```

```text
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

When we use the read function, it finds three columns:

```r
read_fwf(dpjr::dpjr_data("authors2_fwf.txt"))
```

```text
## # A tibble: 10 x 3
##    X1                  X2    X3
##    <chr>               <chr> <chr>
##  1 Toni Morrison       IL    DJ-1944-QF96
##  2 Kurt Vonnegut       IN    XN-5632-TP58
##  3 Walt Whitman        NY    LW-1752-TD08
##  4 Ursula K. Le Guin   CA    EZ-9789-EA77
##  5 Ta-Nehisi Coates    NY    YN-5151-NV82
##  6 W. E. B. Du Bois    MA    HN-6134-NF80
##  7 F. Scott Fitzgerald MN    YH-4405-TR02
##  8 N.K. Jemisin        IA    EF-7340-DW20
##  9 Flannery O'Connor   GA    HB-8269-XC88
## 10 Henry David Thoreau MA   RL-8200-SU83

Rows: 10 Columns: 3— Column specification

chr (3): X1, X2, X3
i Use `spec()` to retrieve the full column specification for this data.
i Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

**FIGURE 5.3** *read_fwf message.*

Adding the `col_names =` argument now mis-identifies the variables.

```r
read_fwf(authors2_path,
         fwf_empty(
           authors2_path,
           col_names = c("first", "last", "state", "unique_id")
         ))
```

```text
## # A tibble: 10 x 3
##    first                 last  state
##    <chr>                 <chr> <chr>
##  1 Toni Morrison         IL    DJ-1944-QF96
##  2 Kurt Vonnegut         IN    XN-5632-TP58
##  3 Walt Whitman          NY    LW-1752-TD08
##  4 Ursula K. Le Guin     CA    EZ-9789-EA77
##  5 Ta-Nehisi Coates      NY    YN-5151-NV82
##  6 W. E. B. Du Bois      MA    HN-6134-NF80
##  7 F. Scott Fitzgerald   MN    YH-4405-TR02
##  8 N.K. Jemisin          IA    EF-7340-DW20
##  9 Flannery O'Connor     GA    HB-8269-XC88
## 10 Henry David Thoreau   MA    RL-8200-SU83

Rows: 10 Columns: 3— Column specification

chr (3): first, last, state
i Use `spec()` to retrieve the full column specification for this data.
i Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

**FIGURE 5.4** *read_fwf message.*

A more reliable approach is to specify exactly the width of each column. Note that in the example below, we specify only “name” without splitting it into first and last.

The variables and their widths are as follows:

| variable | width | start position | end position |
|----------|-------|----------------|--------------|
| name     | 20    | 1              | 20           |
| state    | 10    | 21             | 30           |
| uniqueID | 12    | 31             | 42           |

The widths of each column can be added using the fwf_widths argument:

```r
read_fwf(authors2_path,
    fwf_widths(widths = c(20, 10, 12),
        col_names = c("name", "state", "unique_id")))
```

```text
## # A tibble: 10 x 3
##   name                state unique_id
##   <chr>               <chr> <chr>
## 1 Toni Morrison       IL    DJ-1944-QF96
## 2 Kurt Vonnegut       IN    XN-5632-TP58
## 3 Walt Whitman        NY    LW-1752-TD08
## 4 Ursula K. Le Guin   CA    EZ-9789-EA77
## 5 Ta-Nehisi Coates    NY    YN-5151-NV82
## 6 W. E. B. Du Bois    MA    HN-6134-NF80
## 7 F. Scott Fitzgerald MN    YH-4405-TR02
## 8 N.K. Jemisin        IA    EF-7340-DW20
## 9 Flannery O'Connor   GA    HB-8269-XC88
## 10 Henry David Thoreau MA   RL-8200-SU83

Rows: 10 Columns: 3— Column specification

chr (3): X1, X2, X3
i Use `spec()` to retrieve the full column specification for this data.
i Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

**FIGURE 5.5** *read_fwf message.*

A third option is to provide two lists of locations using fwf_positions(), the first with the start positions, and the second with the end positions. The first variable name starts at position 1 and ends at position 20, and the second variable unique_id starts at 31 and ends at 42. Note that we won’t read the state variable which occupies the ten columns from 21 through 30.

```r
read_fwf(authors2_path,
    fwf_positions(start = c(1, 31), end = c(20, 42),
        col_names = c("name", "unique_id")))
```

```text
## # A tibble: 10 x 2
##   name               unique_id
##   <chr>              <chr>
## 1 Toni Morrison      DJ-1944-QF96
## 2 Kurt Vonnegut      XN-5632-TP58
## 3 Walt Whitman       LW-1752-TD08
## 4 Ursula K. Le Guin  EZ-9789-EA77
## 5 Ta-Nehisi Coates   YN-5151-NV82
## 6 W. E. B. Du Bois   HN-6134-NF80
## 7 F. Scott Fitzgerald YH-4405-TR02
## 8 N.K. Jemisin       EF-7340-DW20
## 9 Flannery O'Connor  HB-8269-XC88
## 10 Henry David Thoreau RL-8200-SU83

Rows: 10 Columns: 2— Column specification

chr (2): name, unique_id
i Use `spec()` to retrieve the full column specification for this data.
i Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

**FIGURE 5.6** *read_fwf message.*

The fourth option is a syntactic variation on the third, with the same values but in a different order. This time, all of the relevant information about each variable is aggregated, with the variable name followed by the start and end locations.

```r
read_fwf(authors2_path,
         fwf_cols(name = c(1, 20), unique_id = c(31, 42)))
```

```text
## # A tibble: 10 x 2
##    name                 unique_id
##    <chr>                <chr>
##  1 Toni Morrison        DJ-1944-QF96
##  2 Kurt Vonnegut        XN-5632-TP58
##  3 Walt Whitman         LW-1752-TD08
##  4 Ursula K. Le Guin    EZ-9789-EA77
##  5 Ta-Nehisi Coates     YN-5151-NV82
##  6 W. E. B. Du Bois     HN-6134-NF80
##  7 F. Scott Fitzgerald  YH-4405-TR02
##  8 N.K. Jemisin         EF-7340-DW20
##  9 Flannery O'Connor    HB-8269-XC88
## 10 Henry David Thoreau  RL-8200-SU83

Rows: 10 Columns: 2— Column specification

chr (2): name, unique_id
i Use `spec()` to retrieve the full column specification for this data.
i Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

**FIGURE 5.7** *read_fwf message.*

And finally, {readr} provides a fifth way to read in a fixed-width file that is a variation on the second approach we saw, with the name and the width values aggregated.

```r
read_fwf(authors2_path,
         fwf_cols(name = 20, state = 10, unique_id = 12))
```

```text
## # A tibble: 10 x 3
##    name                 state unique_id
##    <chr>                <chr> <chr>
##  1 Toni Morrison        IL    DJ-1944-QF96
##  2 Kurt Vonnegut        IN    XN-5632-TP58
##  3 Walt Whitman         NY    LW-1752-TD08
##  4 Ursula K. Le Guin    CA    EZ-9789-EA77
##  5 Ta-Nehisi Coates     NY    YN-5151-NV82
##  6 W. E. B. Du Bois     MA    HN-6134-NF80
##  7 F. Scott Fitzgerald  MN    YH-4405-TR02
##  8 N.K. Jemisin         IA    EF-7340-DW20
##  9 Flannery O'Connor    GA    HB-8269-XC88
## 10 Henry David Thoreau  MA    RL-8200-SU83

Rows: 10 Columns: 3— Column specification

chr (3): name, state, unique_id
i Use `spec()` to retrieve the full column specification for this data.
i Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

**FIGURE 5.8** *read_fwf message.*

## 5.3.1 An extreme example of a fixed-width file

A particularly interesting research question is the relationship between education level and different health outcomes. In this example, we will start the process of importing a large file that contains data that will allow us to explore whether there is a correlation.

Statistics Canada has made available a Public-Use Microdata File (PUMF) of the Joint Canada/United States Survey of Health (JCUSH), a telephone survey conducted in late 2002 and early 2003. There were 8,688 respondents to the survey, 3,505 Canadians and 5,183 Americans. The data file that is available is anonymized, so we have access to the individual responses, which will facilitate additional analysis.

The webpage for the survey, including the PUMF file, data dictionary, and methodological notes, is here: https://www150.statcan.gc.ca/n1/pub/82m0022x/2003001/4069119-eng.htm

The PUMF is a fixed-width file named “JCUSH.txt”. This file is quite a lot larger than the author names example above. There are 8,688 records, one for each survey respondent. The data also consists of 366 variables, a combination of assigned variables (such as the unique respondent identification number and the country), survey question responses, and derived variables that are calculated as part of the post-survey data processing.
