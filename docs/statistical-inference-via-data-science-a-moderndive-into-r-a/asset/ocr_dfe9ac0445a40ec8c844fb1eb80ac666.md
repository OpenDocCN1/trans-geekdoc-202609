116 5 Simple Linear Regression

In Chapter 5, we introduce linear regression with only one regressor. In Section 5.1, the explanatory variable is numerical. This scenario is known as simple linear regression. In Section 5.2, the explanatory variable is categorical.

In Chapter 6 on multiple regression, we extend these ideas and work with models with two explanatory variables. In Section 6.1, we work with two numerical and one categorical explanatory variables. In Section 6.2, we work with one numerical and one categorical explanatory variable and study the model with and without interactions.

In Chapter 10 on inference for regression, we revisit the regression models and analyze the results using statistical inference, a method discussed in Chapters 7, 8, and 9 on sampling, bootstrapping and confidence intervals, and hypothesis testing and p-values, respectively. The focus there is also on linear regression for prediction instead of explanation.

We begin with regression with a single explanatory variable. We also introduce the correlation coefficient, discuss "correlation versus causation," and determine whether the model fits the data.

# Needed packages

We load all the packages needed for this chapter (this assumes you've already installed them). In this chapter, we introduce some new packages:

+   1. The tidyverse “umbrella” (Wickham, 2023) package. Recall from our discussion in Section 4.4 that loading the tidyverse package by running library(tidyverse) loads the following commonly used data science packages all at once:
* ggplot2 for data visualization
* dplyr for data wrangling
* tidyr for converting data to "tidy" format
* readr for importing data into R
* As as the more advanced purrr, tibble, stringr, and forcats packages
2. The moderive package of datasets and functions for tidyverse-friendly-intro linear regression as well as a data frame summary function.

If needed, read Section 1.3 for information on how to install and load R packages.

```
library(tidyverse)
library(moderive)
```