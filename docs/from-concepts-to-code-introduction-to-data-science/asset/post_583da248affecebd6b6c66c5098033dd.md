
A higher FICO score reflects a lower risk of default. Loan-to-value ratio is the amount of the loan divided by the value of the asset. A higher ratio is considered riskier, as this implies a smaller downpayment.

Let's begin by importing modules and looking at some of the data:

```python
import numpy as np
import pandas as pd
import statsmodels.api as sm
syn = pd.read_csv('../datasets/mortgage_lending.csv')
syn.head()
```

OUTPUT:

| id | fico | ltv | gender | occupation | denied | loan.term | rate_type |
|---|---|---|---|---|---|---|---|
| 0 | 696 | 62 | m | salesperson | 0 | 30 | fixed |
| 1 | 752 | 61 | m | salesperson | 0 | 30 | fixed |

Note that loan_to_value is abbreviated as ltv due to margin constraints.

We conduct some exploratory data to better understand the data and uncover potential predictors. It would be helpful to understand the composition of the records by occupation and gender, for example. We can build a two-way table to explore this. For example, of the 12 accountants in the dataset, 5 are female and 7 are male.

```python
pd.crosstab(syn.occupation, syn.gender)
```

OUTPUT:

| occupation | f | m |
|---|---|---|
| accountant | 5 | 7 |
| contractor | 1 | 4 |
| ... | ... | ... |
| lawyer | 7 | 5 |
| librarian | 0 | 1 |
| mason | 0 | 1 |
| mechanic | 0 | 2 |
| nurse | 10 | 0 |
| ... | ... | ... |

An important observation is that some occupations are comprised of a single gender. For example, there are 10 nurses, and all of them are female. Suppose nurses historically defaulted on loans at a high rate in the bank's dataset. If occupation is used as a predictor in a lending model, the model will learn

# Case Study: Fair Lending Risk

that nurses have a high risk of default. This will lead to the model denying loan requests to nurses in the future, which effectively denies lending to more females. The occupation variable is acting as a discriminatory variable in this case, and it should not be included in the model.

Let's examine distributions of fico and loan_to_value for denied and approved applicants. These are summarized as boxplots in Figures 17.2 and 17.3. Denied applicants tended to have lower FICO scores and higher loan-to-value ratios, which makes sense.

```python
boxplot(x='denied', y='fico', data=syn)
boxplot(x='denied', y='loan_to_value', data=syn)
```

![](img/7f40a2246fd3d2d5353d109f489c4e33_355_0.png)

FIGURE 17.2: Denied by FICO Score

![](img/7f40a2246fd3d2d5353d109f489c4e33_355_1.png)

FIGURE 17.3: Denied by Loan to Value

Model Risk

Suppose the predictors we used in the underwriting model $M_U$

$L_U = ['fico', 'loan\_to\_value', 'loan\_term', 'nurse']$

We will use these predictors to build the model next, but first: which of these predictors should have been used? The variables $fico$ and $loan\_to\_value$ measure creditworthiness and the ability to repay the loan, so these should be used. The variable $loan\_term$ is a loan attribute, and it should be used. As discussed earlier, $nurse$ will introduce the risk of discriminating against females, and it should NOT be used.

Now lets train the underwriting model on the synthetic data.

```python
# build nurse indicator variable
syn['nurse'] = syn.occupation.apply(lambda x: 1 if x == 'nurse' else 0)
```

```python
X = syn[['fico', 'loan_to_value', 'loan_term', 'nurse']]
```

```python
# include intercept term
X = sm.add_constant(X)
```

```python
# target variable
y = syn['denied']
```

```python
# train logistic regression model
result_uw = sm.Logit(y, X).fit()
```

```python
print(result_uw.summary())
```

TABLE 17.5: Underwriting Model Parameter Estimates

| coef | std err | z | P >|z| | 0.05 | 0.075 |
|---|---|---|---|---|---|---|
| const | 11.088 | 0.057 | 0.002 | 0.999 | -9.52e+04 | 9.1e+04 |
| fico | -0.1400 | 0.057 | -2.455 | 0.014 | 0.252 | -0.028 |
| loan_to_value | 0.075 | 0.113 | 0.706 | 0.480 | -0.141 | 0.300 |
| loan_term | 0.4942 | 1552.666 | 0.000 | 1.000 | -3042.675 | 3043.664 |
| nurse | 2.7672 | 1.892 | 1.462 | 0.144 | -0.942 | 6.476 |

The parameter estimates are shown in Table 17.5. The only significant predictor in the model is fico as indicated by its p-value less than 0.05. The negative coefficient estimate of -0.14 indicates that a higher FICO score is associated with lower odds of denial, which makes sense.

# Chapter Summary

Next, we train the fair lending model $M_{FL}$ to understand if gender is a significant predictor. The model will include an intercept term, the credit factors, the attributes of the loan, and gender. If gender is a significant predictor in $M_{FL}$, this would indicate that it is being used to make lending decisions, which is discriminatory practice.

```python
# convert categorical gender to indicator
syn['gender_female'] = syn.gender.apply(lambda x: 1 if x == 'f' else 0)
```

```python
X = syn[['fico','loan_to_value','loan_term','gender_female']]
X = sm.add_constant(X)
```

```python
y = syn['denied']

result_fl = sm.Logit(y, X).fit()
```

```python
print(result_fl.summary())
```

TABLE 17.6: Fair Lending Model Estimates

| coef | std err | z | P > z | 0.025 | 0.975 |
|---|---|---|---|---|---|---|
| const | 96.2464 | 4.2e+04 | 0.002 | -2.516 | 0.998 | 8.25e+04 | 8.27e+04 |
| fico | -0.1670 | 0.067 | -2.516 | 0.012 | 0.012 | 0.297 |
| ltv | 0.075 | 0.113 | 0.706 | 0.480 | -0.141 | 0.300 |
| loan_term | 0.4942 | 1552.666 | 0.000 | 1.000 | -3042.675 | 3043.664 |
| gender_f | 2.7672 | 1.892 | 1.462 | 0.144 | -0.942 | 6.476 |

The parameter estimates are shown in Table 17.5. The only significant predictor in the model is fico as indicated by its p-value less than 0.05. The negative coefficient estimate of -0.14 indicates that a higher FICO score is associated with lower odds of denial, which makes sense. Note that loan_to_value is abbreviated as ltv due to margin constraints. The parameter estimates are shown in Table 17.5. The only significant predictor in the model is fico as indicated by its p-value less than 0.05. The negative coefficient estimate of -0.14 indicates that a higher FICO score is associated with lower odds of denial, which makes sense. Note that loan_to_value is abbreviated as ltv due to margin constraints. (Note: The OCR text contained some repetitions and inconsistencies in the final pages which have been cleaned for logical flow).
