# Project: Predicting House Prices with Elastic-Net

Split005=initial_split(DataHousing, prop=0.005, strata=Price, breaks=5)
DataTrain=training(Split005)
DataTest=testing(Split005)

When creating the training dataset, we use the argument prop=0.005, leading to a training dataset with about 100 observations. This is small, but in general realistic for a training dataset. However, a total of 20,699 available observations, we could have used the more common prop=0.7. In that case, we would end up with 14,489 observations for the training dataset. With such a large training dataset, the unregulated model we use later in this section would likely not lead to overfitting, and thus regularization would no longer be needed — which would defeat the purpose of this interactive

# 7.5.2 Unregularized Benchmark Model

As a benchmark, we begin with an unregulated model. In this case, a multi-variate Degree-2 Polynomial Model. It includes the variables Sqft, Bedr, and Year. They are used in their original form, and as various interaction terms:

```
Price = $eta_1Sqft + \beta_2Bedr + \beta_3Year$
$+ $eta_4Sqft^2 + \beta_5Bedr^2 + \beta_6Year^2$
$+ $eta_7SqftBedr + \beta_8SqftYear + \beta_9BedrYear$
$+ $eta_{10}Sqft^2Bedr + \beta_{11}SqftBedr^2 + \beta_{12}Sqft^2Bedr^2$
$+ $eta_{13}SqftYear^2 + \beta_{14}SqftYear^2 + \beta_{15}Year^2
$+ $eta_{16}Bedr^2Year + \beta_{17}BedrYear^2 + \beta_{18}BedrYear^2$ (7.10)
```

Afterward, we use a recipe to generate and normalize the predictors:

```
RecipeHousesMultivar=recipe(Price--, data=DataTrain) |>
step_mutate(Sqft=Sqft^2, Bedr=Bedr^2, Year=Year^2,
SqftBedr=Sqft*Bedr, SqftYear=Sqft*Year,
BedrYear=Bedr*Year, Sqft2Bedr=Sqft*Bedr,
SqftBedr2=Sqft*Bedr^2, Sqft2Bedr2=Sqft^2*Bedr,
Sqft2Year=Sqft^2*Year, SqftYear2=Sqft*Year,
Sqft2Year2=Sqft*Year^2, Bedr2Year=Bedr^2*Year,
BedrYear2=Bedr*Year^2, Bedr2Year2=Bedr^2) |>
step_normalize(all_predictors())
```

Afterward, we create the model design (ModelDesignBenchmark), the workflow