
## 4.4 Data Importing and Tidy Data

```r
library(ggplot2)
library(dplyr)
library(readr)
library(tidyr)
```

Recall that ggplot2 is for data visualization, dplyr is for data wrangling, readr is for importing spreadsheet data into R, and tidyr is for converting data to "tidy" format. There is a much quicker way to load these packages than individually loading them by installing and loading the tidyverse package. The tidyverse package acts as an "umbrella" package whereby installing/loading it will install/load multiple packages at once for you.

After installing the tidyverse package as you would a normal package as seen in Section 1.3, running:

```r
library(tidyverse)
```

would be the same as running:

```r
library(ggplot2)
library(dplyr)
library(readr)
library(tidyr)
library(purr)
library(tibble)
library(stringr)
library(forcats)
```

The purrr, tibble, stringr, and forcats are left for a more advanced book; check out R for Data Science12 to learn about these packages.

For the remainder of this book, we'll start every chapter by running library(tidyverse), instead of loading the various component packages individually. The tidyverse "umbrella" package gets its name from the fact that all the functions in all its packages are designed to have common inputs and outputs: data frames in "tidy" format. This standardization of input and output data frames makes transitions between different functions in the different packages as seamless as possible. For more information, check out the tidyverse.org13 webpage for the package.

12 http://r4ds.had.co.nz/ 
13 https://www.tidyverse.org/

## 4.5 Conclusion

### 4.5.1 Additional resources

Solutions to all Learning checks can be found in the Appendices of the online version of the book. The Appendices start at https://moderndrive.com/v2/appendixa.

An R script file of all R code used in this chapter is available at https://www.modernrive.com/v2/scripts/04-tidy.R.

If you want to learn more about the readr and tidyr package, we suggest that you check out RStudio’s “Data Import Cheat Sheet.” In the current version of RStudio in 2024, you can access this cheatsheet by going to the RStudio Menu Bar -> Help -> Cheat Sheets... Scroll down the page to the “Data import with reader, readxl, and googlesheets4” for information on using the readr, readxl and googlesheets4 packages to import data, and Data tidying with tidyr cheatsheet for information on using the tidyr package “tidy” data.

### 4.5.2 What’s to come?

Congratulations! You’ve completed the “Data Science with tidyverse” portion of this book. We will now move to the “Statistical modeling with moderndrive” portion of this book in Chapters 5 and 6, where you’ll leverage your data visualization and wrangling skills to master relationships between different variables in data frames.

However, we are going to leave Chapter 10 on “Inference for Regression” until after we’ve covered statistical inference in Chapters 7, 8, and 9. Onwards and upwards into Statistical/Data Modeling as shown in Figure 4.6!

![](img/445742518041017e8f01f11b0c3190d9_145_0.png)

FIGURE 4.6: ModernDive flowchart — on Part II!

![](img/445742518041017e8f01f11b0c3190d9_146_0.png)

## Part II

## Statistical Modeling with moderndive

## Simple Linear Regression

We have introduced data visualization in Chapter 2, data wrangling in Chapter 3, and data importing and “tidy” data in Chapter 4. In this chapter, we work with regression, a method that helps us study the relationship between an outcome variable or response and one or more explanatory variables or regressors. The method starts by proposing a statistical model. Data is collected and used to estimate the coefficients and results are typically used for two purposes:

1. **For explanation** when we want to describe changes in one or more of the regressors are associated with changes in the response, quantify those changes, establish which of the regressors truly have an association with the response, or determine whether the model to describe the relationship between the response and the explanatory variables seems appropriate.
2. **For prediction** when we want to determine, based on the observed values of the regressors, what will the value of the response be? We are not concerned about how all the regressors relate and interact with one another or with the response, we simply want as good predictions as possible.

As an illustration, assume that we want to study the relationship between blood pressure and potential risk factors such as daily salt intake, age, and physical activity levels. The response is blood pressure, and the regressors are the risk factors. If we use linear regression for explanation, we want to determine whether reducing salt intake has a real effect on blood pressure, or by much blood pressure decreases if an individual reduces salt intake.

The most basic and commonly-used type of regression is linear regression. Linear regression involves a numerical response and one or more regressors that can be numerical or categorical. It is called linear because the statistical model that describes the response and the regressors is assumed to be linear. Linear regression is the foundation for almost any other type of regression.
