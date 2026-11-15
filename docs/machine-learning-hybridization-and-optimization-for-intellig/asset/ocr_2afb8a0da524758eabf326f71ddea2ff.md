from various sources. The main source for worldwide data for COVID-19 cases was maintained by JHU, which we have obtained as it was hosted in their GitHub; another data set that was required was obtained from the COVID-19 India API, a crowd-sourced API, which provided details like active, confirmed, and recovered cases and also provides data on vaccinations distributed and testing done, while we would be mainly focusing on parameters such as confirmed, recovered, and actives cases.

# 3.4.3 TESTING AND TRAINING MODELS

In this subsection, we will look into various models which we have used in the chapter, and while we won’t be looking into definitions of various algorithms, we will be looking into the parameters of what we have used in the model.

# 3.4.3.1 Regression Models

For base models such as linear regression, lasso regression, and SVM, we fit the models after scaling the data without any tweaks and obtained the predictions of the models.

For models such as random forest, XGB regressor, and LGBM regressor, we had the number of estimators as 1,300 and used it for the prediction of the models.

# 3.4.3.2 Neural Network Models

For neural networks, we have used LSTM, Bi-Directional LSTM, and Encoder-Decoder LSTM:

+   i. For the univariate model, we have set the number of features as 1, and for the multivariate, we have set the feature as 4 indicating the neighboring four states’ values.
+   ii. The input shape includes length of the input data set; the time taken (in our case, 6 days); and the number of features.
+   iii. We have the total number of units as 65 and determine the final layer to have 4 units, indicating the 4 days prediction of future output. It has been trained over 1,000 epochs 30 times, and the average MSE was taken into consideration in the experiments.