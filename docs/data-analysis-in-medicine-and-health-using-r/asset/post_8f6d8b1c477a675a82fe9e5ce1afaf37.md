
# 9.11 Presentation of Multinomial Regression Model

We can make a better table using knitr and kableExtra packages. Or we can save the results as a .csv file so we edit it using spreadsheets.

```r
tab_mlog %%%
write_csv("results_multinomial.csv")
```

# 9.12 Summary

In this chapter, we extend binary logistic regression to data with a categorical outcome that has three or more levels. We describe the multinomial logistic regression model, the log odds and the conditional probabilities. When then show estimation for the single and multiple multinomial logistic regression inclusion models with an interaction. Following that, we describe how to make inferences and perform predictions. Lastly, make use of kableExtra package to produce a nice table for our model. We are big fans of two excellent books on logistic regression. The first one is Applied Logistic Regression (Hosmer et al., 2013) and the second one is Logistic Regression: Self Learning Text (Kleinbaum, 2010). You will acquire strong understanding of the concepts and model-building process from the two books. To see what packages and functions relevant to logistic regression, you can refer to A Handbook of Statistical Analyses Using R (Everitt and Hothorn, 2017).

![](img/2bc6b006fe018e0018b86f206ab98644_192_0.png)

# 10
# Poisson Regression

After completing this chapter, the readers are expected to:

- understand the basic concepts behind Poisson regression for count and rate data
- perform Poisson regression for count and rate
- perform model fit assessment
- present and interpret the results of Poisson regression analyses

Poisson regression is a regression analysis for count and rate data. As mentioned before in Chapter 7, it is a type of generalized linear models (GLMs) whenever the outcome is. It also accommodates rate data, as we will see shortly. Although count and rate data are very common in medical and health sciences, in our experience, Poisson regression is underutilized in medical research. Most often, researchers end up using linear regression because they are more familiar with it and lack of exposure to the advantage of using Poisson regression to handle count and rate data.

Count is discrete numerical data. Although it is convenient to use linear regression to handle the count outcome by assuming the count or discrete numerical data (e.g. the number of hospital admissions) as continuous numerical data (e.g. systolic blood pressure in mmHg), it may result in illogical predicted values. For example, by using linear regression to predict the number of asthmatic attacks in the past year, we may end up with a negative number of attacks, which does not make any clinical sense! So it is recommended that medical researchers get familiar with Poisson regression and make use of it whenever the outcome variable is a count variable.

Another reason for using Poisson regression is whenever the number of cases (e.g. deaths and accidents) is small relative to the number of events (e.g. alive and no accident), then it makes more sense to just get the information from the cases in a population of interest, instead of also getting the information from the non-cases as typical cohort and case-control studies. For example, in the publicly available COVID-19 data, only the number of deaths were reported along with some basic sociodemographic and clinical information for the cases. Whenever the information for the non-cases are available, it is quite easy to use logistic regression for the analysis.

Basically, Poisson regression models the linear relationship between:

- **outcome**: count variable (e.g. the number of hospital admissions, parity, cancerous lesions and astumatic attacks). This is transformed into the natural log scale.
- **predictors/independent variables**: numerical variables (e.g. age, blood pressure and income) and categorical variables (e.g. gender, race and education level).

We might be interested in knowing the relationship between the number of astumatic attacks in the past year with sociodemographic factors. This relationship can be explored by a Poisson regression analysis.

Basically, for Poisson regression, the relationship between the outcome and predictors is:

```
natural log of count outcome = numerical predictors
+ categorical predictors
```

At times, the count is proportional to a denominator. For example, given the same number of deaths, the death rate in a small population will be higher than the rate in a large population. If we were to compare the number of deaths between the populations, it would not make a fair comparison. Thus, we may consider adding denominators in the Poisson regression modeling in the form of offsets. This denominator could also be the unit of exposure, for example person-years of cigarette smoking. This will be explained later under Poisson regression for rate section.

In the previous chapter, we learned that logistic regression allows us to obtain the odds ratio, which is approximately the relative risk given a predictor. For Poisson regression, by taking the exponent of the coefficient, we obtain the rate ratio RR (also known as incidence rate ratio IRR),

```
RR = exp(b_p)
```

the coefficient b_p of predictor. This is interpreted in similar way to the odds ratio for logistic regression.

# 10.3 Prepare R Environment

## 10.3.1 Libraries

For this chapter, we will use the following packages:

- tidyverse: a general and powerful package
- psych: descriptive statistics
- summary: coming up with nice tables
- broom: tidying the results
- epiDisplay: epidemiological data

These are loaded as follows:

```r
library(tidyverse)
library(psych)
library(gtsmary)
library(broom)
```

For epiDisplay, we will use the function directly because it has some conflicts with the packages loaded above.

# 10.4 Poisson Regression for Count

## 10.4.1 About Poisson regression

Poisson regression models the linear relationship between:

- **outcome**: count variable (e.g. the number of hospital admissions, parity, cancerous lesions and astumatic attacks). This is transformed into the natural log scale.
- **predictors**: numerical variables (e.g. age, blood pressure and income) and categorical variables (e.g. gender, race and education level).

We might be interested in knowing the relationship between the number of astumatic attacks in the past year with sociodemographic factors. This relationship can be explored by a Poisson regression analysis.

Multiple Poisson regression for count is given:

```
ln(count outcome) = intercept + numerical predictors
+ categorical predictors
```

or in a shorter form,

$$Ln(\tilde{y}) = b_0 + b_1x_1 + ... + b_px_p$$

where we have p predictors.

## 10.4.2 Dataset

The data on the number of asthmatic attacks per year among a sample of 120 patients and the associated factors are given in asthma.csv.

The dataset contains four variables:

- **gender**: Gender of the subjects (categorical) [male, female].
- **res_inf**: Recurrent respiratory infection (categorical) [no, yes].
- **ghq12**: General Health Questionnaire 12 (GHQ-12) score of psychological well being (numerical) [0 to 36].
- **attack**: Number of asthmatic attack per year (count).

The dataset is loaded as:

```r
asthma = read.csv("data/asthma.csv")
```

We now look at the basic structure of the dataset:

```
## 'data.frame': 120 obs. of 4 variables:
## $ gender : chr "female" "male" "female"
## $ res_inf: chr "yes" "no" "yes"
## $ ghq12 : int 21 17 30 22 27 33 24 23 25 28 ...
## $ attack : int 6 4 8 5 2 3 1 2 ...
```

## 10.4.3 Data exploration

For descriptive statistics, we introduce the epiddisplay package. It is a nice package that allows us to easily obtain statistics for both numerical and categorical variables. We use codebook() function from the package.

```r
epidDisplay::codebook(asthma)
```
