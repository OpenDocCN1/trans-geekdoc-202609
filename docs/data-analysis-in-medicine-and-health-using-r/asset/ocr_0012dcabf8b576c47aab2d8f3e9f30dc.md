# 8.6 Prepare Environment for Analysis

The simple logistic model is all written as:

```
$$\pi(x) = \frac{exp^{eta_0+eta_1 gcs}}{1+exp^{eta_0+eta_1 gcs}}$
```

The $\pi(x) = E(Y|x)$ represents the conditional mean of $Y$ given $x$ when the logistic distribution is used. This is also simply known as the predicted probability of death for given value gcs.

If we have decided (based on clinical expertise and literature review) that a model that could explain death counts of gcs, stroke type, sex, dm and age, then the logit model can be expanded to:

```
$$\hat{g}(x) = \hat{eta}_0+\hat{eta}_1(gcs)+\hat{eta}_2(stroketype)+\hat{eta}_3(sex)+\hat{eta}_4(dm)+\hat{eta}_5(sbp)+\hat{eta}_6(age)$
```

These are the odds for death given certain gcs, sbp and age values and specific categories of stroke type, sex, and diabetes. The probability of death is

```
$$\pi(x) = \frac{exp^{\beta_0+\beta_1(gcs)+\beta_2(stroketype)+\beta_3(sex)+\beta_4(dm)+\beta_5(sbp)+\beta_6(age)}}{1+exp^{\beta_0+\beta_1(gcs)+\beta_2(stroketype)+\beta_3(sex)+\beta_4(dm)+\beta_5(sbp)+\beta_6(age))}$
```

In many datasets, some independent variables are either discrete or nominal scale variables. Which include race, sex, treatment group, and age categories. Including them in the model is inappropriate as if they were interval scale variables. In some statistical software, these variables are represented by numbers. However, be careful; these numbers are used merely as identifiers or labels for the groups.

In this situation, assuming that one of the independent variables is obesity type, we will use method designed variables (or dummy variables). Suppose, for example, which is coded as "Class 1", "Class 2" and "Class 3". In this case, there are 3 levels or categories, hence two design variables $(D-1)$ are necessary, let's say D1 and D2. One possible coding strategy is that when the patient is in "Class 1" the two design variables would both be set to zero. In this example, "Class 1" is the reference category. When the patient is in "Class 2", then D1 is set as 1 and D2 as 0; when the patient is in "Class 3", we will then set D1 as 0 and D2 and 1. All these coding assignments can be done automatically in the software. To interpret, we must know which category is the reference.

# 8.6 Prepare Environment for Analysis

# 8.6.1 Creating an RStudio project

Start a new analysis task by creating a new RStudio Project. To this,