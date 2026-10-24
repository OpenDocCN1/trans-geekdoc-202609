Overall, data pre-processing is critical for ML in crop prediction because it improves the accuracy and relevance of the data used by ML algorithms.

Proper data pre-processing can help to reduce noise, bias, and errors in the data and ensure that the ML model can accurately predict crop yields based on the input data.

# 5.3.2 Model Selection for Crop Prediction

Forest of chance is a powerful ML algorithm for crop prediction that can provide accurate results with relatively low computational cost. The algorithm can handle large and complex datasets, and it is robust to noise and outliers in the data, as shown in Table 5.1.

One of the key advantages of random forest is that it can handle nonlinear relationships between the input variables and the target variable. It achieves this by building decision trees based on random subsets of the data and then combining the predictions of all trees to produce a final prediction. This approach can capture complex interactions between the variables and can lead to more accurate predictions.

Random forest also has the ability to handle missing data, which is common in agricultural datasets. The algorithm can impute missing values using techniques, such as mean imputation or regression imputation, allowing the model to be trained on a complete dataset. Another advantage of random forest is its ability to handle categorical variables.

The algorithm converts categorical variables into binary dummy variables, allowing them to be included in the model. In terms of performance metrics, random forest can achieve low values of mean absolute error and root mean square error (RMSE), indicating accurate predictions.

Coefficient of determination (R²) can also be high, indicating a strong relationship between the input variables and the target variable.

Artificial neural networks are popular algorithms for crop prediction. They are a set of algorithms inspired by the structure of the human brain and are capable of learning intricate patterns from vast amounts of data.

In crop prediction, ANNs can be used to model the relationship between various crop and environmental elements, such as soil type, climate, and precipitation, and predict crop yields.

TABLE 5.1
Result of Various Algorithms.

| Algorithm | Accuracy (%) |
|---|---|
| ANN | 92 |
| SVM | 98.5 |
| Random forest | 99.3 |
| Decision tree | 97.5 |