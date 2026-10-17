![](bbox=[0.126, 0.113, 0.873, 0.396])

# 14.2.3 Practice Question

Create a calibration plot with five cuts for your model from the previous practice question (recall that this model should have cigarette use as the outcome and age, race_and_ethnicity, LGBT, and family_affluence as well as an interaction between family_affluence and race_and_ethnicity as independent variables). It should look like Figure 14.1.

```
# Insert your solution here:
```

# 14.3 Variable Selection and Likelihood Ratio Tests

In the last chapter, we introduced the step() function to implement stepwise variable selection. This function also works with glm objects. In this case, we use this function to implement backward selection from a larger set of covariates. We first remove any observations with NA values to ensure that our training data does not change size as the formula changes.

```
nyts_sub <- nyts %>%
dplyr::select(location, sex, grade, otherlang, grades_in_past_year,
perceived_e_cig_use, race_and_ethnicity, LGBT,
```