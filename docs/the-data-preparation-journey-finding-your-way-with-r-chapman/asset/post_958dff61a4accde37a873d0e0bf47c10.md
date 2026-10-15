
## 5 Importing data: plain-text files

In this chapter:

- Importing data from delimited text files
- Importing data from fixed-width text files

### 5.1 Delimited plain-text files

Plain-text files (sometimes called “ASCII files”, after the character encoding standard they use) are often used to share data. They are limited in what they can contain, which has both downsides and upsides. On the downside, they can’t carry any additional information with them, such as variable types and labels. But on the upside, they don’t carry any additional information that requires additional interpretation by the software. This means they can be read consistently by a wide variety of software tools.

Plain-text files come in two varieties: delimited and fixed-width. “Delimited” is a reference to the fact that the files have a character that marks the boundary between two variables. A very common delimited format is the CSV file; the letters in the file name stand for “Comma Separated Values”, and use a comma as the variable delimiter. Another delimited type, somewhat less common, uses the tab character to separate the variables, and will have the extension “TSV” for, you guessed it, “Tab Separated Values”. Occasionally you will find files that use semi-colons, colons, or spaces as the delimiters.

There are base R functions to read this type of file. The functions within the `{readr}` package (Wickham and Hester, 2020) have some advantages over the base R functions when it comes to plain-text files. (The `{readr}` package is part of the tidyverse.) Compared to the equivalent base R functions, the `{readr}` functions are quite a bit faster, and the package’s functions provide some useful flexibility when it comes to defining variable types as part of the read operation (rather than reading in the data and then altering the variable types). As well, it returns a tibble instead of a dataframe. (For information about the difference, see (Wickham, 2019a, 3.6 Data frames and tibbles). For working with very large files, you may want to investigate the `fread()` function in the `{data.table}` package (Doyle et al., 2023.)

We activate `{readr}` by using the `library()` function:

```r
library(readr)
```

In this chapter, we will be using two of the `{readr}` functions. Each has a variety of arguments that allow us to control the behaviour of the function; those will be dealt with in the examples.

| function | purpose |
| --- | --- |
| `read_csv()` | reads the contents of a CSV file |
| `read_fwf()` | reads the contents of a fixed-width text file |

### 5.2 Using `{readr}` to read a CSV file

In the following examples, we will use versions of the data in the `{palmerpenguins}` data (Horst et al., 2022; Horst, 2020).

In the code chunks below, an R character string object `penguins_path` is created that contains the text string with the location of the file “penguins.csv”.

In the first example, the file has been loaded to our computer using the `{dpir}` package, and uses the `dpir_data()` function from that package to access the file (no matter its location on our computer).

In the second example, the file is located in a directory called “data” that is in our RStudio project folder. The `{here}` package will generate the full path, with slash or backslash separators (depending on your computer’s operating system), starting at the location of the RStudio project.

The `penguins_path` object is then used in the function `read_csv()` to create a dataframe object called `penguins_data`.

```r
# Example 2
# create object path using the {here} package
penguins_path <- here::here("data", "penguins.csv")

# read the contents of the CSV file
penguins_data <- read_csv(penguins_path)
```

```
Rows: 344 Columns: 8 — Column specification
Delimiter: ","
chr (3): species, island, sex
dbl (5): bill_length_mm, bill_depth_mm, flipper_length_mm, body_mass_g, year
i Use `spec()` to retrieve the full column specification for this data.
i Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

FIGURE 5.1 read_csv message.

The function returns a message letting us know the type that each variable is assigned.

The arguments of the `{readr}` package allow a lot of control over how the file is read. Of particular utility are the following:

| argument | purpose |
| --- | --- |
| `col_types = cols()` | define variable types |
| `na = ""` | specify which values you want to be turned into NA |
| `skip = 0` | specify how many rows to skip; the default is 0 |
| `n_max = Inf` | the maximum number of records to read; the default is Inf for infinity, interpreted as the last row of the file |

Adding the `col_types = cols()` parameter has two benefits. First, defining the variable type avoids errors (such as numeric fields will be read as such, and not as characters) and speeds up the read process since R doesn't have to check and infer the variable type.

Second, it allows us to alter what `{readr}` has decided for us. For example, we could set the species variable to be a factor type variable.

When we show the entire table, we can see that the variable species is now a factor type.

```r
penguins_data <- read_csv(penguins_path,
    col_types =
      cols(species = col_factor()))
penguins_data
```

Fixed-width files are a hold-over from the days when storage was expensive and/or on punch cards. This meant that specific columns in the table (or card) were assigned to a particular variable, and precious space was not consumed with a delimiter. Compression methods have since meant that a CSV file with unfixed variable lengths is more common, but in some big data applications, fixed-width files can be much more efficient.

If you ever have to deal with a fixed-width file, you will (or should!) receive a companion file letting you know the locations of each variable in every row.

In this example, we will use the one provided in the `{dpjr}` package, “authors_fwf.txt”. This code chunk assigns the path to the file location, which we can use in our code later.

```r
authors_path <- dpjr::dpjr_data("authors_fwf.txt")
```

This simple file has four (or as we will see, sometimes three, if we combine first and last name as one) variables, and three records (or rows).

- first name
- last name
- U.S. state of birth (two-letter abbreviation)
- randomly generated unique ID

If we open the file in a text editor, we see this:

```
Toni Morrison    IL    DJ-1944-QF96
Kurt Vonnegut    IN    XN-5632-TP58
Walt Whitman     NY    LW-1752-TD08
```

FIGURE 5.2 authors_fwf.txt.

We could also use the base R function `readLines()` to see the lines:

```r
readLines(authors_path)
```

```
## [1] "Toni Morrison    IL    DJ-1944-QF96"
## [2] "Kurt Vonnegut    IN    XN-5632-TP58"
## [3] "Walt Whitman     NY    LW-1752-TD08"
```

The arguments within the `readr::read_fwf()` function include those listed above for the `read_csv()` function, and some others that are specific to fixed-width files.

| argument | purpose |
| --- | --- |
| `col_names = c()` | defines a list of the names for the variables |
| `fwf_widths(widths = c(), col_names = c())` | a list of the character length of each variable, and their names |
| `fwf_positions(start = , end = , col_names = c())` | character position of the start and end of each variable, and their names |
| `fwf_cols(variable1_name = c(), variable2_name = c())` | name followed by start and end position of each variable |
| `fwf_cols(variable1_name = width, variable2_name = width)` | name followed by width of each variable |

The examples below will elaborate on these arguments.

The first approach would be to allow `{readr}` to guess where the column breaks are. The `fwf_empty()` function looks through the specified file and returns the beginning and ending locations it has guessed, as well as the skip value that the `read_fwf()` function uses.

Note that the column names are specified in a list.

```r
fwf_empty(
  authors_path,
  col_names = c("first", "last", "state", "unique_id")
)
```

```
## $begin
## [1] 0 5 20 30
##
## $end
## [1] 4 13 22 NA
##
## $col_names
## [1] "first"   "last"    "state"   "unique_id"
```

That information can then be used by the `read_fwf()` function:

```r
read_fwf(authors_path,
    fwf_empty(
      authors_path,
```

