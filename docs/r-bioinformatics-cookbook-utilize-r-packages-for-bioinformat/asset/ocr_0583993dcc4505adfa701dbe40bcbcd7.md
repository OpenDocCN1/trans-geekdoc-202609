Loading, Tidying, and Cleaning Data in the tidyverse

Note that the output lines are prefixed with ##.

# Loading data from files with readr

The readr package is a package that provides functions for reading and writing tabular data in a variety of formats, including comma-separated values, tab-separated values (TSV), and delimiter-separated files. It is designed to be flexible and stop help when data changes or unexpected items appear in the input. The two main advantages over base R functions include consistency in interface and the ability to be explicit about types and inspect those types.

This latter advantage can help avoid errors when reading data, as well as make data cleaning and manipulation easier. readr can automatically infer the data types of each column, which can be useful for a preliminary inspection of large datasets or when the data types are not known.

Consistency in interface and output is one of the main advantages of readr functions. readr functions provide a consistent interface for reading different types of data, which can make it easier to work with multiple types of files. For example, the read_csv() function can be used to read CSV files, while the read_tsv() function can be used to read TSV files. Additionally, readr returns a tibble, a modern version of a data frame that is more consistent in its output and easier to read than the base R data frame.

# Getting ready

For this recipe, we'll need the readr and rbioinfo own packages. The latter contains a census_2021.csv file that carries UK census data from 2021, from the UK Office for National Statistics (https://www.ons.gov.uk/). You will need to inspect it, especially its header, to understand the process in this recipe. The first step shows you how to find where the file is on your.

Note the delimiters in the file are commas,), and that the first seven lines contain metadata that isn't part of the main data. Also, look at the messy column headings and note that the numbers themselves are internally delimited by commas.

# How to do it...

We begin by getting a filename for the sample in the package:

+   1. Load the package and get a filename:

```
library(readr)
filename <- fs::path("extdata",
  "census_2021.csv",
  package="rbioinfocbook"
)
```