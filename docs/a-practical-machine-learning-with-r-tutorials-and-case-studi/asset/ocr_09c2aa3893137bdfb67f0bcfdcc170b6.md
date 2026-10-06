# 3 Introduction to R and RStudio

```
VecBirthYears=CurrentYear-VecCages
cat("Birth years for", VecFirstNames, "are":, VecBirthYears)
```

# ## Birth years for Carsten Jose Jane: 1979 2001

Run the code to estimate the birth years for Carsten, Jose, and Jane. The estimated birth years are calculated as the difference between the current year (the numeric value stored in the R object CurrentYear) and all three values stored in the vector object VecCages. Consequently, the result (VecBirthYears) contains three values and is also a vector object.

**Your turn:**

+   * Adjust the CurrentYear object to include the current year, needed.
* Adjust the vector object VecFirstNames to include the names of your friends.
* Adjust the vector object VecCages to include the ages of your three friends.
* Execute the modified code to estimate the birth years of your three friends.

# **Data Frame Objects**

In the previous exercise section, you analyzed the content of different vectors under the assumption that their elements were in the same order. Required remembering the order of elements in a vector when performing analysis, which is cumbersome and can be avoided with data frames.

You can think of a data frame as a table with variables in the columns, variables in the first row, and related observations in all rows — just like an *Exel* table.

The variables in the columns of a data frame are very similar to vector objects — that they are part of the data frame. In fact, we will show in the exercises that the columns of a data frame can be populated with vector objects and columns of a data frame can be extracted as vector objects.

After a data frame object is defined, you can use commands from the tidyverse package to process the data. Throughout this book, we will almost exclusively work with data frames and use the tidyverse for data engineering.

# **Exercise 12:**

Regardless of whether the file is on your computer or the Internet, tabular data in a file can be imported into a data frame with the `import()` command from the `rio` package.