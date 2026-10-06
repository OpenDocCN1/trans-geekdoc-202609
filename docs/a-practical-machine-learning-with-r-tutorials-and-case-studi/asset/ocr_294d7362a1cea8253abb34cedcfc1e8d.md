# 11.7 SHAP Contribution of Predictor Variables

After all predictions for the new dataset have been created, the prediction for the Coalition: TF is the mean of the predictions from the newly created dataset. The predictions for other coalitions are calculated in a similar way.

This algorithm works well when there are not too many predictor variables, and it does not use extra computing time to fit extra Random Forest models. However, it needs to predict as many observation as in the training dataset for each coalition. Given that the number of coalitions exponentially grows with the number of predictor variables (see Equation (11.1)), this can turn into a computational problem.

To address this problem, DALEX allows you to limit the number of paths through a flow chart like the one shown in Figure 11.6. Since a path through the flowchart is the same as in the table next to it, DALEX chooses a number of rows from the table and only calculates predictions for the required coalitions. The number of rows (paths) can be set with an argument.

In the next section, you can use DALEX to interpret the predictions for the vaccination project that you used before in the interactive Section 10.4.2 to predict U.S. counties vaccination rates with a Random Forest model.

# 11.7.3 Project: Apply the SHAP Algorithms in a Project

At the end of the previous section, we explained how DALEX approximates SHAP values. Here, you will work with a real-world application that uses the same Random Forest model and the same data used in Section 10.4.2 predicting the U.S. continental counties' vaccination rates during the COVID-19 pandemic.

We will show how you can use tidymodels with the DALExtra packages to generate SHAP values to interpret the prediction results for a specific U.S. county.

Afterward, in the interactive Section 10.4.2 you can use the provided R code to create SHAP values for any country and interpret the results.

We start by reviewing the data processing for the Random Forest workflow used in Section 10.4.2.

Below, the libraries and data are loaded, and the data are split into training and testing data:

```
library(rio); library(janitor); library(tidymodels)
library(DALEX); library(DALEXTRA)
DataVax=import("https://ai.lang-analytics.com/data/DataVax.rds") |>
select(PercVacFull, PercRep,
PercAsian, PercBlack, PercHish,
```