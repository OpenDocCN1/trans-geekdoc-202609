# 6

# Multiple Regression

In Chapter 5, we studied simple linear regression as a model that represents the relationship between two variables: an outcome variable or response y and an explanatory variable or regressor x. Furthermore, to keep things simple, we only considered models with one explanatory x that was either numerical in Section 5.1 or categorical in Section 5.2.

In this chapter, we introduce multiple regression, the direct extension to simple linear regression when more than one explanatory variable is taken into account to explain the changes in the outcome variable. As we show in the next sections, much of the material developed for simple linear regression translates directly into multiple linear regression, but the interpretation of the associated effect of any one explanatory variable must be made making taking into account the other explanatory variables included in the model.

# Needed packages

If needed, read Section 1.3 for information on how to install and load R packages.

```
library(tidyverse)
library(moderndrive)
library(ISLR2)
```

# 6.1 One numerical and one categorical explanatory variable

We continue using the UN member states dataset introduced in Section 5.1. Recall that we studied the relationship between the outcome variable fertility rate, y, and the regressor life expectancy, x.

In this section, we introduce one additional regressor to this model: the categorical variable income group with four categories: Low income, Lower middle income, Upper middle

DOI: 10.1201/9781033272454-6