# 13.7 Exercises

For these exercises, we continue using the nhanes_df data.

+   1. Construct a linear model using DBP as the output and LEAD, AGE, and EVER_SMOKE as features, and print the output.
+   
+   2. Use forward stepwise selection to add possible interactions to the linear model from the previous question.
+   
+   3. Draw a QQ-plot for the model in Question 2, and describe the distribution that you observe.
+   
+   4. Report the MAE and MSE of the model developed in Question 2. Then, find the row numbers of the observations with the top 5 Cook's Distance values for this model.
+   
+   5. Look at some diagnostic plots for the model and use what you observe from these plots to choose a transformation that improves the fit of this model. Then, fit and summarize this new model with the transformation included. How do the MSE and MAE of the new model compare to the previous one? Note that your predictions will be on the transformed scale, so you'll need to convert them to the correct scale.