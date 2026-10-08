no accident), then it makes more sense to just get the information from the cases in a population of interest, instead of also getting the information from the non-cases as typical cohort and case-control studies. For example, in the publicly available COVID-19 data, only the number of deaths were reported along with some basic sociodemographic and clinical information for the cases. Whenever the information for the non-cases are available, it is quite easy to use logistic regression for the analysis.

Basically, Poisson regression models the linear relationship between:

+   **outcome**: count variable (e.g. the number of hospital admissions, parity, cancerous lesions and astumatic attacks). This is transformed into the natural log scale.
**predictors/independent variables**: numerical variables (e.g. age, blood pressure and income) and categorical variables (e.g. gender, race and education level).

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

for the coefficient b_p of the p's predictor. This is interpreted in similar way to the odds ratio for logistic regression, which is approximately the relative risk given a predictor.