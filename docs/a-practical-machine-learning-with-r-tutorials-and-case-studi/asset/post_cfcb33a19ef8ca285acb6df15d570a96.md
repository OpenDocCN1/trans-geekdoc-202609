
# How to predict the wage for the coalitions in Figure 11.6?

We mentioned before the wage prediction for Helga's wage based on three predictor variables could be calculated based on the fitting Forest model from Section 11.4:

```
CoalitionETF=predict(WModelWageRF,new_data=ObsHelga)
cat('Helga's predicted wage from Coalition ETF is:',
round(CoalitionETF[],2))
```

## Helga's predicted wage from Coalition ETF
To predict the wage for Coalition: none at the top of the flow chart in Figure 11.6, we found that no information about Helga can be used for this coalition. Because of absence of information, the mean is often a reasonable way to predict a variable. Therefore, we use the mean of the training data for the wage prediction from Coalition: none.

```
CoalitionNone=mean(DataTrainWage)
cat('Helga's predicted wage for Coalition 'none' is:',
round(CoalitionNone,2))
```

## Helga's predicted wage for Coalition 'none' is: 5.94
Generating predictions for Helga's wage for the remaining six coalitions is a bit more tricky, and we will talk about it a little later.

Instead, we use the table in Figure 11.6 to calculate SHAP values for the predictor variables. Because all possible predictor orders have been considered in the rows of the table, we can calculate the overall contribution of Educ = 17, Tenure = 18, and Female = 1 to the wage prediction as the mean of columns MargContE, MargContT and MargContF. You can find the resulting SHAP values in the "mean" row of table in Figure 11.6.

It is a very useful property of the SHAP method that the SHAP values always add to the cumulative contribution of all predictor variables:

3.94 + 2.14 + (-2.78) = 3.3
SHAP Educ=17 SHAP Tenure=18 SHAP Female=1 SHAP Cumulativ

We can use the SHAP values from the equation above to interpret the results from the SHAP approach: The fact that Helga has a high education (Educ = 18) contributes $3.94 to her predicted wage, the fact that she has a long tenure (Tenure = 18) contributes $2.14, and the fact that she is female (Female = 1)

# 11.7 SHAP Contribution of Predictor Variables

contributes negative $2.78 to her predicted wage ¹¹ All these contributions add up to 3.3 and explain why Helga's wage is $3.30 higher than the wage of an average worker.

Predicting wage for the remaining six coalitions in the chart Figure 11.6:

We have already explained that the predicted wage for Coalition: none is calculated as the mean wage from the observations in the training dataset. We also showed that the wage prediction uses all predictor variables (Coalition: ETF) could be calculated as the prediction from the analyzed machine learning model (the Random Forest Model from Section 11.4 in our case).

To calculate the predictions for the six coalitions in the flow Figure 11.6 using a very simplified approach.

To create predictions for Coalition: E, and Coalition: F, we created three new Random Forest models designed for one predictor variable each. We then fitted each of the Random Forest models to the training data for the predictor variables Educ, Tenure, and Female, respectively. Afterward, we used the three Random Forest models to create the predictions for Helga's wage based on Educ = 17 (Coalition: E), Tenure = 18 (Coalition: T), and Female = 1 (Coalition: F).

For the wage predictions for Coalition: ETF, and Coalition: F, we proceeded in a similar fashion: We created three new Random Models for two predictors and then fitted each model with the related two predictor variables from the training dataset (ET, EF, and TF). As before, we used the corresponding predictor values from the observation Helga to generate the wage predictions for the three coalitions.

The advantage of this simplified approach is that it is possible to showcase the approach in an R script (see the Digital Resource Section 11.10 for a link to a blog article that describes the approach in detail and provides the R script). The disadvantage is that this simplified approach has a conceptual and computational drawback.

The Computational Drawback: Our goal is to generate SHAP values to explain the Random Forest model from Section 11.4—the one that was used for Coalition: ETF. However, for the six coalitions that used only one or two predictor variables, we used similar but different Random Forest models because these Random Forest models were designed for one and two predictor variables. This is conceptually problematic.

The Computational Drawback: the simplified approach is not scalable.

> ¹¹The fact that Helga's reduces her wage by about $3 should not come as a surprise. The data are from 1976 and reflect sex discrimination during that time. To analyze discrimination in present times, we could use a similar methodology based on most recent data.

# 11 Interpreting Machine Learning Results

Using three predictor variables led to eight coalitions to consider. One was highly based on the *Random Forest* model we wanted to explain (Coalition: ETF), and for another one, we used the mean of the outcome variable from the training dataset as the predicted weight for which we had to design and train six new *Random Forest* models. Creating new *Random Forest* models is not a significant computational problem. However, the number of coalitions (NCitions) grows exponentially with the number of predictor variables (NpredictorVar):

```
NCitions = 2^NVar
```

For three predictor variables, we need eight coalitions, but for 20, we need 1,048,576.

We can use the SHAP values from the equation above to interpret the results from the SHAP approach: The fact that Helga has a high education (Educ = 18) contributes $3.94 to her predicted wage, the fact that she has a long tenure (Tenure = 18) contributes $2.14, and the fact that she is female (Female = 1) contributes negative $2.78 to her predicted wage ¹¹ All these contributions add up to 3.3 and explain why Helga's wage is $3.30 higher than the wage of an average worker.

Predicting wage for the remaining six coalitions in the chart Figure 11.6:

We have already explained that the predicted wage for Coalition: none is calculated as the mean wage from the observations in the training dataset. We also showed that the wage prediction uses all predictor variables (Coalition: ETF) could be calculated as the prediction from the analyzed machine learning model (the Random Forest Model from Section 11.4 in our case).

To calculate the predictions for the six coalitions in the flow Figure 11.6 using a very simplified approach.

To create predictions for Coalition: E, and Coalition: F, we created three new Random Forest models designed for one predictor variable each. We then fitted each of the Random Forest models to the training data for the predictor variables Educ, Tenure, and Female, respectively. Afterward, we used the three Random Forest models to create the predictions for Helga's wage based on Educ = 17 (Coalition: E), Tenure = 18 (Coalition: T), and Female = 1 (Coalition: F).

For the wage predictions for Coalition: ETF, and Coalition: F, we proceeded in a similar fashion: We created three new Random Models for two predictors and then fitted each model with the related two predictor variables from the training dataset (ET, EF, and TF). As before, we used the corresponding predictor values from the observation Helga to generate the wage predictions for the three coalitions.

The advantage of this simplified approach is that it is possible to showcase the approach in an R script (see the Digital Resource Section 11.10 for a link to a blog article that describes the approach in detail and provides the R script). The disadvantage is that this simplified approach has a conceptual and computational drawback.

The Computational Drawback: Our goal is to generate SHAP values to explain the Random Forest model from Section 11.4—the one that was used for Coalition: ETF. However, for the six coalitions that used only one or two predictor variables, we used similar but different Random Forest models because these Random Forest models were designed for one and two predictor variables. This is conceptually problematic.

The Computational Drawback: the simplified approach is not scalable.

> ¹¹The fact that Helga's reduces her wage by about $3 should not come as a surprise. The data are from 1976 and reflect sex discrimination during that time. To analyze discrimination in present times, we could use a similar methodology based on most recent data.

# 11 Interpreting Machine Learning Results

Using three predictor variables led to eight coalitions to consider. One was highly based on the *Random Forest* model we wanted to explain (Coalition: ETF), and for another one, we used the mean of the outcome variable from the training dataset as the predicted weight for which we had to design and train six new *Random Forest* models. Creating new *Random Forest* models is not a significant computational problem. However, the number of coalitions (NCitions) grows exponentially with the number of predictor variables (NpredictorVar):

```
NCitions = 2^NVar
```

For three predictor variables, we need eight coalitions, but for 20, we need 1,048,576.
