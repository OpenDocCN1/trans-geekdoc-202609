the same as the one explained in detail in the previous chapter (see Section 4.7.3):

```
library(tidymodels)
RecipeMockup=recipe(Grade-StudyTime, data=DataMockup)

ModelDesignLinReg=linear_reg() |
  set_engine("lm") |
  set_mode("regression")

WFMockup=workflow() |
  add_recipe(RecipeMockup) |
  add_model(ModelDesignLinReg) |
  fit(DataMockup)
```

+   1. Define and save the recipe that indicates which variable is the outcome and which the predictor variable, together with the argument. Note that we do not add any step, commands for data pre-processing since we can use the mockup data as is.

+   2. Define the model design in three steps to determine:
   i) The name of the machine learning model (linear_reg).
   ii) The R package used for model (lm).
   iii) The model used which is either "classification" or "regression".

+   3. Add the recipe and the model design to the workflow and fit the workflow to the data.

Note that we did not split the data into training and testing data. Consistently, we fit the workflow with the complete dataset DataMockup as the training dataset. This is only acceptable because our example is a mockup. In a real-world application splitting into training and testing data is an absolute to avoid overfitting (more on overfitting Chapter 6).

Fitting the workflow with fit(DataMockup) is when the parameters for the model design are calculated and saved within the workflow model WFModel-Mockup. A (workflow) model where the values for the parameters have been determined is called a fitted model. A fitted model can be used for prediction.