
```
haven::write_dta(nts_person_2020_hav,
    here("data_output", "nts_person_2020.13.dta"),
    version = 13)

# export RDS
readr::write_rds(nts_person_2020_hav,
    here("data_output", "nts_person_2020.rds"))
```

## 8

## Importing data: PDF files

In this chapter:

- Reading data and text from PDF files
- Manipulating the resulting objects into a tidy structure

### 8.1 PDF files

> Portable Document Format (PDF) is a file format developed by Adobe in 1992 to present documents, including text formatting and images, in a manner independent of application software, hardware, and operating systems<sup>1</sup>.

The PDF file format provides a great deal of functionality and flexibility to create high quality output. PDF files are often used for things like branded marketing materials and annual reports, where there is a use-case for a document that looks on screen as it would if printed on paper, with a combination of text and images, all designed and formatted in a way to make it visually appealing.

Included in those documents may be data we want for our analysis. Or we may want to analyze the text in the document. The way a PDF file is structured can make extracting the contents, whether data tables or text, a challenge. The “export to Excel” function in Adobe Acrobat and other PDF tools might work successfully; always give this a try first. The operative phrase in that sentence is might work. Similar to the challenges that we confront when importing a formatted Excel file, your PDF exporter will confront structures that look like tables visually, but which are not in a consistent tidy format. Sometimes text wrapping in variable names leads to splitting into multiple rows, and in other instances what looks like multiple cells in the table are read as one.

<sup>1</sup>Wikipedia entry, “PDF” (Wikipedia contributors, 2022b)

Fortunately for us, other data scientists have already confronted the challenge of reading data tables in PDF files, and have made tools available for the rest of us. One such package is {pdftools}(Ooms, 2022)

In addition to {pdftools}, for this chapter we will also be using the data manipulation packages {dplyr} and {tidyr}, and the text manipulation package {stringr}(Wickham, 2019b)

```
# reading the contents of a PDF file
library(pdftools)

# data wrangling packages
library(dplyr)
library(tidyr)

# string manipulation
library(stringr)
```

### 8.1.1 Getting started

To get started in reading data from a PDF file, we will read data from a summary of the {palmerpenguins} (Horst et al., 2022; Horst, 2020) data.

While this is for a single table on a single page, the same approach will work for multiple tables across multiple pages, if the structure of each table on each page is the same. The process is always the same: start with the smallest unit and expand out.

- The way that PDF files are read, the smallest unit is a single row.
- Expand that to the entire table. Apply column splitting and assigning headers at the end of this stage.
- If there are multiple tables with the same structure, tackle that next by looping through each of the tables.
- And once you have a single page working, you can loop through multiple pages.

We read the entire contents of the file using the pdf_text() function from the {pdftools} package, and assign the contents to an R object in our environment.

Next we use the str() function to display a summary of the structure of our new object.

```
penguin_summary <- pdf_text(dpjr::dpjr_data("penguin_summary.pdf"))
```

```
str(penguin_summary)
```

```
chr " species island mean_flipper_length_mm mean_body_mass_g\n\n1 Adelie Biscoe 188.795"| __truncated__
```

## FIGURE 8.1 penguin data from PDF file.

What we have as a result of this is a single character string, with the contents of the file. In this example, there is only one page and thus one string. If you are dealing with a multi-page document, each page gets its own string.

In a visual scan of this output, we see the variable names starting with species. After the last of the variables mean_body_mass_g there are two end of line characters, represented by “\n” (pronounced “backslash n”). We will be using these end of line characters as part of the parsing process.

Another way to look at the contents of a page is to use the cat() function (from {base R}), which displays the contents as it would be printed:

```
cat(penguin_summary)
```

```
## species island mean_flipper_length_mm mean_body_mass_g
##
## 1 Adelie Biscoe 188.7955 3709.659
##
## 2 Adelie Dream 189.7321 3688.393
##
## 3 Adelie Torgersen 191.1961 3706.373
##
## 4 Chinstrap Dream 195.8235 3733.088
##
## 5 Gentoo Biscoe 217.1870 5076.016
```

Next we use the strsplit() function (from {base R}) to separate the long string into separate rows. As we noted there are two “\n” character pairs marking the end of each line; if we use only one in the strsplit() function, an extra row appears between the data rows.

```
penguin_summary_2 <- penguin_summary |>
  strsplit(split = "\n\n")

penguin_summary_2
```

```
## [[1]]
## [1] " species  island  mean_flipper_length_mm mean_body_mass_g"
## [2] "1 Adelie  Biscoe          188.7955          3709.659"
## [3] "2 Adelie  Dream           189.7321          3688.393"
## [4] "3 Adelie  Torgersen       191.1961          3706.373"
## [5] "4 Chinstrap Dream          195.8235          3733.088"
## [6] "5 Gentoo   Biscoe          217.1870          5076.016\n"
```

At this stage, we need to apply some cleaning. If we don’t do it now, it’s going to cause some challenges later. There is an extra line return at the end of the last data cell, so let’s use a regular expression to remove it. There’s also space at the beginning of the first line and the number-space combination at the beginning of the data rows.

And by using the double square bracket accessor in the first row, the object returned is no longer nested, but instead has a single character string for each row.

```
penguin_summary_3 <- penguin_summary_2[[1]] |>
  str_remove("\\n$") |>
  str_remove("^\\s+") |>
  str_remove("^\\d ")
```

Next, we create a list object with the variable names, in order to keep the names separate from the data in our resulting table. This is accomplished by assigning the row that contains the names (row 1, identified using the square bracket [1]) to a vector with one element.

```
penguin_variable_vector <- as.vector(penguin_summary_3[1])

penguin_variable_vector
```

```
## [1] "species    island    mean_flipper_length_mm mean_body_mass_g"
```

The next step is to split this vector into 4 separate elements at the points where there are one or more white spaces, identified in the regular expression “\s+". The “\s" finds a single space, and adding the “+" extends that to “one or more" of the character the precedes it.

This returns another nested list.

```
penguin_variable_list <- str_split(penguin_variable_vector, "\\s+")
penguin_variable_list
```

```
## [[1]]
## [1] "species"            "island"
## [3] "mean_flipper_length_mm" "mean_body_mass_g"
```

In order to have the structure we need, we apply the unlist() function to the result.

```
penguin_variable_names <- unlist(penguin_variable_list)
penguin_variable_names
```

```
## [1] "species"            "island"
## [3] "mean_flipper_length_mm" "mean_body_mass_g"
```

It is possible to turn those two steps into one by wrapping the string split inside the unlist():

```
penguin_variable_names <-
  unlist(str_split(penguin_variable_vector, "\\s+"))
penguin_variable_names
```

```
## [1] "species"            "island"
## [3] "mean_flipper_length_mm" "mean_body_mass_g"
```

The next step is to build a table, using a for-loop. (See (Wickham et al., 2023b, Chapter 27 Iteration) for a review of this process.)

```
# 1. define output
penguin_table <- tibble(value = NULL)

# 2. loop through the rows
# Because the first element is the titles,
# we want the length to be one shorter
loop_length <- length(penguin_summary_3) - 1

for (i in 1:5) {
  j <- i + 1
  dat <- as_tibble(penguin_summary_3[j])
  penguin_table <- bind_rows(penguin_table, dat)
}

penguin_table
```

```
## # A tibble: 5 x 1
##   value
##   <chr>
## 1 Adelie   Biscoe          188.7955    3709.659
## 2 Adelie   Dream           189.7321    3688.393
## 3 Adelie   Torgersen       191.1961    3706.373
## 4 Chinstrap Dream           195.8235    3733.088
## 5 Gentoo   Biscoe          217.1870    5076.016
```

The loop has created a tibble with one column, value. We will apply the separate() function to split the value into each of the variable names we assigned to the object penguin_variable_names earlier. The split is based on the location of one or more spaces in the original string, using the “\s+” regular expression.

```
penguin_table <- tidyr::separate(
  penguin_table,
  value,
  into = penguin_variable_names,
  "\\s+"
)

penguin_table
```

```
## # A tibble: 5 x 4
##   species   island   mean_flipper_length_mm mean_body_mass_g
```
