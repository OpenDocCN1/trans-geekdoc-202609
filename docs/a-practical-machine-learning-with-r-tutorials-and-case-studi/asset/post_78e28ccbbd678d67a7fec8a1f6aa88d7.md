
# 3.5 How R Stores Data

```r
ForeDays=length(VecTemp)
cat("The forecast is for", ForeDays, "days.")
```

## The forecast is for 3 days.

### Data Frame Object:

R can store a complete data table with rows and columns in an object- an object. We refer to such a table as a data frame object.

A data frame is very similar to an Excel table. The first row of a data frame defines the names of the variables that are stored in the columns — similar to a title in Excel. The following rows of a data frame (starting with row two) contain the values for the observations stored in the data frame. Each row is one observation.

Each data frame contains a named variable related to the observations. The variable's name and values are stored in the following entries. These values can be of various Data Types such as char, numeric, or factor — you can have different Data Types for different columns. However, each column can have only one type.

You can think of a data frame as a combination of R vectors arranged in the data frame's columns. In fact, you can extract the data frame column as a vector and the column (name) separated with a $\$-sign.

| Survived | Pclass | Name | Sex | Age | SiblingsSpousesAbroad | ParentsChildrenAbroad | FarePounds |
|---|---|---|---|---|---|---|---|
| 0 | 3 | Mr. Owen Harris Braun | male | 22 | 1 | 0 | 7.250 |
| 1 | 3 | Miss. Lina Heikkinen | female | 26 | 0 | 0 | 7.920 |
| 0 | 3 | Mr. William Henry Allen | male | 35 | 0 | 0 | 8.050 |
| 0 | 3 | Mr. James Morale | male | 27 | 0 | 0 | 8.458 |
| 1 | 1 | Miss. Elizabeth B | female | 58 | 0 | 0 | 26.550 |

#### FIGURE 3.2 Screenshot of the View()

Let us use the Titanic dataset as an example of how to work with data frames: Figure 3.2 displays five observations from the data frame Titanic. We used the import() command from the rio package to load the Titanic dataset from the Internet and assigned it to data frame Titanic.

```r
library(rio)
Titanic=import("https://ai.lang-analytics.com/data/Titanic.csv")
```

> ⁵The dataset provided here was obtained using the R package see (see Hendricks (2015)).

26 Introduction to R and RStudio

The content of Figure 3.2 was created with view(dataTitanic). The view() command can only be used in the Console of RStudio. It is a very useful command as it displays a complete scrollable view of a data frame.

Figure 3.2 reflects what you learned about data frames:

- The first row contains the names of variables that are related to the observations (passengers).

The variable Name is a character variable, Sex is a categorical variable (with categories male and female). All other variables are numerical variables.

- The observations (here: the first passengers) are in the rows (starting with Row 2).

We can extract the Age variable as an R vector object and then use the mean to calculate the average age of the Titanic passengers:

```r
VecAge=DataTitanic$Age
mean(VecAge)
```

## [1] 29.47

In the last line of the code block, we did not assign the output of the mean() command to an R object. Output not assigned to any object will be outputted to the Console. As you can see, the average age of Titanic passengers is 29.47.

You can also find how many passengers are considered in the data frame Titanic, as this coincides with the number of rows (observations) of Titanic. You can apply the length() command to any vector from the data frame to find the number of rows, as follows:

```r
cat("Number of observations-", length(DataTitanic$Name))
```

## Number of observations: 887

You cannot apply the length() command directly to a data frame, but you can find the number of rows (the number of observations) directly from a data frame with:

> Note that R assigned the data type char and not factor to the variable Sex. This is because R considers Sex a categorical variable. However, a user can use the command as factor() from the tidyverse package to convert Sex to a factor.

> As the original Titanic data is stored as a numerical variable with 1 for a surviving passenger and 0 otherwise. It would have been better coding practice to store Survived as a logical variable with values TRUE and FALSE (Section 3.5.1).

# 3.5 How R Stores Data

```r
cat("Number of observations:", nrow(DataTitanic))
## Number of observations: 887
```

In the two code blocks above, we nested the length() and the nrow() commands within the cat() command to generate a more informative output. In general, you are free to nest R objects inside each other to any level you choose, but the readability of your code might suffer.

R frames come in two varieties: i) original data frames from base R, which are called data frame and ii) a slightly more advanced version from the tidyverse package calling a tibble. In older versions of R (before Version 4.0), there were few differences between the two versions, and both currently, the base are almost identical.

In this chapter, we will work with the Titanic dataset. For now, it is essential to remember that data frame consists of columns representing variables and rows representing the observations. When working in RStudio, the content of data frame can be displayed by the icon.

# Advanced Objects:

Advanced objects include such as Data in DataStocks, Vec in Vecong (for a vector), Plot in PlotVar (for a plot), or Model in Model (for a model). If applicable, we will also start with R objects to indicate that we are working with a condition (e.g., IsWeatherGood=TRUE). These rules are not required, but may make the code easier.

# Summary:

Figure 3.3 shows how Data Types can be categorized.

> The dataset provided here was obtained using the R package see (see Hendricks (2015)).

