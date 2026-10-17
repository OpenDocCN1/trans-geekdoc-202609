# 4

# Intro to Exploratory Data Analysis

In the last chapter, we learned about loading data into R and practiced selecting and summarizing columns and rows of the data. In this chapter, we learn how to conduct more exploratory analysis, focusing on the univariate and bivariate sample distributions of the data. The first half focuses on using base R to create basic plots and summaries. In the second half, we show how to create summary plots using the **GGally** package (Schloerke et al. 2021) and tables using the **gt** (Iannone et al. 2023) and **gtsummary** (Sjoberg et al. 2023) packages.

```
library(HDSinRdata)
library(GGally)
library(gt)
library(gtsummary)
```

# 4.1 Univariate Distributions

In this chapter, we use a sample of the National Health and Nutrition Examination Survey (Centers for Disease Control and Prevention (CDC) 1999-2018) containing lead, blood pressure, BMI, smoking status, alcohol use, and demographic variables from NHANES 1999-2018. Variable selection and feature engineering followed the analysis in Huang (2022). There are 31,625 observations in this sample. Use the help operator `?NHANESsample` to read the column descriptions.

```
data(NHANESsample)
dim(NHANESsample)
#> [1] 31265   21
names(NHANESsample)
#>  [1] "ID"            "AGE"           "SEX"           "RACE"
#>  [5] "EDUCATION"     "INCOME"        "SMOKE"         "YEAR"
```