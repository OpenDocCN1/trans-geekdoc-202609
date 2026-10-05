# Case Study: Fair Lending Risk

+   - Individuals over the age of 65

+   - Black, Hispanic, and Native American individuals

Illegal, disparate treatment occurs when a lender bases its decision on one or more discriminatory factors covered by fair lending laws. For example, a bank using a lending process where females are offered an auto loan with a higher interest rate than males would be a violation of fair lending laws.

In finance, banks and other lenders typically use machine learning models to make lending decisions. The underwriting decision may use a logistic regression model. Given approval, the pricing decision may use a linear regression model.

The model predictors should capture the ability and willingness of borrowers to repay the loan. The predictors should not use protected class information, as this can discriminate and promote unfair lending.

There will be two models discussed in our example. The underwriting model $M_{UL}$ will be used for making automated underwriting decisions. The fair lending model $M_{FL}$ will be used to assess if the underwriting process was systematically fair. Given this background information, we will now review the data and modeling.

#  17.9.2 Numerical Example

We will explore fair lending risk with a synthetic mortgage lending dataset. The data can be found here:

```
semester2/datasets/mortgage_lending.csv
```

The fair lending notebook can be found here:

```
semester2/week_15_16_fair_lending_application/
IDS_hw4_fair_lending_intro.ipynb
```

This dataset includes a subset of what a typical file would look like. It includes:

+   - The demographic variable: gender

+   - The credit factor fico (for FICO score)

+   - The credit factor loan.term

+   - The loan attribute rate.type

+   - The target denied, where 1=denied, 0=approved