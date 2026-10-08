
This study was conducted from the latest release data from the 2017 submission of the SEER database (1973 to 2015 data) of the National Cancer Institute. Patients with a diagnosis of AO were selected from the SEER database using the International Classification of Diseases for Oncology, Third Edition (ICD-O-3) histology code 9451. There are 1824 patients diagnosed with AO in this dataset.

## 12.4 Analysis

The dataset contains all variables of our interest. For the purpose of this assignment, we want to explore prognostic factor association of age, surgery status and marital status with the survival of AO patients. The variables in the dataset as follow:

- age: biological age at the beginning of the study. This data is in numerical values.
- surgery: is the patient who has undergone surgery. Coded as "Yes" and "No".
- marital: Marital status at assignment. Coded as "single", "married", or "separated/divorced/widowed".
- survival: survival time in month. This data is in numerical values.
- status: survival status coded as "1 = died" and "0 = censored".

We use these packages:

- here to specify the location of the working directory
- tidyverse: for exploratory data analysis, data wrangling and plotting.
- gsummary to provide nice statistical tables
- broom to provide clean and polish table for the estimates
- flexsurv to perform flexible parametric survival analysis models for time-to-event data, including the generalized gamma, the generalized F and the Royston-Parmar spline model, and extensible to user-defined distributions.
- SurvRefCensCov to transform output-based Weibull distribution to a more natural parameterization.

```
library(here)

# here starts at C:/Users/drkim/Downloads/multivariate_data_analysis/multivariate_data_analysis

library(tidyverse)

# -- Attaching tidyverse ---------------------------------------------------------------- tidyverse 2.0.0 -

# v dplyr      1.1.1 v readr      2.1.4
# v forcats    1.0.0 v string    1.5.0
# v ggplot2    3.4.2 v tibble     3.2.1
# v lubridate  1.9.2 v tidyr      1.3.0
# v purrr       1.0.1

# -- Conflicts --
tidyverse_conflicts() --
# x dplyr::filter()  masks stats::filter()
# x dplyr::lag()      masks stats::lag()
```

## Use the conflicted package (<http://conflicted.r-lib.org/> to force all conflicts to become errors)

```
library(gtsummary)
library(broom)
library(flexsurv)
```

## Loading required package: survival

```
library(SurvRegCensCov)
```

## Registered S3 method overwritten by 'SurvRegCensCov'
## method from
## print.src

## 12.4.3 Read dataset

```
d1 <- read_csv('data','survivaloa.csv')
```

```
## Rows: 1824 Columns: 8
## Column specification
---
## Delimiter: ","
## chr (5): marital, sex, surgery, race, first
## dbl (3): age, status, survivaltime
##
## i Use `spec()` to retrieve the full column specification for this data.
## i Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

## 12.4.4 Data wrangling

We will select only these variables to simplify our model-building process:

- age
- surgery
- marital
- survivaltime
- status

## 12.4 Analysis

And we will convert all character variables to factor variables.

```
d1 <- d1 %>%
  dplyr::select(age, surgery, marital, survivaltime, status) %>%
  mutate_if(is.character, as.factor)
glimpse(d1)

# Rows: 1,824
# Columns: 5
# $ age           <dbl> 4, 4, 4, 5, 5, 5, 6, 6, 8, 9, 11, 11, 11
# $ surgery       <fct> Yes, Yes, Yes, No, Yes, Yes
# $ marital       <fct> Single, Single, Single, Single, Single
# $ survivaltime   <dbl> 9, 10, 141, 12, 54, 161, 60, 8, 15, 298, 83
# $ status          <dbl> 0, 1, 0, 1, 1, 0, 1, 0, 1
```

## 12.4.5 Exploratory data analysis (EDA)

We will do some simple:

```
d1 %>%
  mutate(status = recode(status, "0" = "Censored", "1" = "Death")) %>%
  tbl_summary(by = status,
              statistic = list(all_continuous() ~ "{mean} ({sd})",
                              all_categorical() ~ "{n} ({p})"),
              type = list(where.logical ~ "categorical"),
              label = list(age ~ "Age (in years)",
                          surgery ~ "Surgery Status",
                          marital ~ "Marital Status",
                          survivaltime ~ "Time (month)"),
              missing_text = "**Missing**") %>%
  modify_header(label = "**Table 1. Patient Characteristic**") %>%
  modify_spanning_header(c("stat_1", "stat_2") ~ "**Survival Status**") %>%
  modify_footnote(all_stat_cols ~ "Mean (SD) or Frequency (%)") %>%
  bold_labels(everything()) %>%
  as_gt()
```

## Survival Status

| Variable | Censored, N = 835 | Death, N = 989 |
| :--- | :--- | :--- |
| Age (in years) | 45 (13) | 52 (16) |
| Surgery Status | 774 (93%) | 835 (84%) |
| Marital Status | 531 (64%) | 606 (61%) |
| Separated/divorced/widowed | 96 (11%) | 174 (18%) |
| Single | 208 (25%) | 209 (21%) |
| Time (month) | 83 (65) | 38 (42) |

*Mean (SD) or Frequency (%)

We can use the survreg() from **survival package**. However survreg() only perform estimation for AFT metric.

```
exp.mod.aft <- survreg(survivaltime, status) ~ age + marital + surgery,
              data = d1, dist = 'exponential')
```

```
## Call:
## survreg(formula = Surv(survivaltime, status) ~ age + marital +
##   surgery, data = d1, dist = "exponential"
##
## (Intercept)
##                 Value Std. Error Z p
##                 -0.0487 0.1601 41.45 < 2e-16
## age               -0.0609 0.0025 -19.50 < 2e-16
## maritalated/divorced/widowed -0.0681 0.0871 -0.70 0.4848
## maritalSingle     -0.3068 0.0823 -3.70 0.00019
## surgeryYes        0.5250 0.0879 5.97 2.4e-09
##
## Scale fixed at 1
##
## Exponential distribution
## Loglik(model)=-5401.2 Loglik(intercept only)=-5614.4
## Chisq=426.47 on 4 degrees of freedom, p=5.3e-91
## Number of Newton-Raphson Iterations: 5
## n=1824
```

## 12.4 Analysis

## 12.4.7 Weibull (accelerated failure time)

We first start with estimating a Weibull parametric survival model which will return an accelerated failure metric:

To do this, we will be using the survreg() function

```
wei.mod.aft <- survreg(Surv(survivaltime, status) ~ age + surgery + marital,
               data = d1, dist = 'weibull')
summary(wei.mod.aft)
```

```
## Call:
## survreg(formula = Surv(survivaltime, status) ~ age + surgery +
##             marital, data = d1, dist = "weibull"
##             Value Std. Error z p
## (Intercept) 0.19724 34.58 2e-16
## age
## surgeryYes
## maritalSeparated/divorced/widowed
## maritalSingle
## Log(scale)
## Scale= 1.23
```

```
## Weibull distribution
## Loglik(model)= -5365.4 Loglik(intercept only)= -5533.6
## Chisq=336.9 on 4 degrees of freedom, p=1.2e-7
## Number of Newton-Raphson Iterations: 5
## n=1824
```

However, the parameters estimated from survreg() do not make sense. To do this, we will use Weibull() to convert to hazard, AFT model.

```
Convertibull(wei.mod.aft, conf.level = 0.95)
```

## 12.4 Parametric Survival

Or we can simply use flexsurv() to obtain the log time and

```
wei.mod.aft <- flexsurv(Surv(survivaltime, status) ~ age + surgery + marital,
              data = d1, dist = 'weibull')
```

```
## Call:
## flexsurv(formula = Surv(survivaltime, status) ~ age + surgery +
##             marital, data = d1, dist = "weibull")
```

```
## Estimates:

data mean           est      L95     U95
## shape             NA       8.13e-01 7.73e-01 8.55e-01
## scale              NA       -5.27e-02 -5.87e-02 -4.67e-02
## age                4.89e-01 -5.87e-02 -4.67e-01
## surgeryYes         8.82e-01 6.25e-01 4.12e-01 8.39e-01
## maritalSeparated/divorced/widowed 1.48e-01 -1.00e-01 -3.10e-01 1.10e-01
## maritalSingle      2.29e-01 -3.54e-01 -5.54e-01 -1.55e-01

```
## N = 1824, Events: 989, Censored: 835
```

```
## Total time at risk: 106252
```

```
## Log-likelihood = -5365.418, df = 6
```

```
## AIC = 10742.84
```
