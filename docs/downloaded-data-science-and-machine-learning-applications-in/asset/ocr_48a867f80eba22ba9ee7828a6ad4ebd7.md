# Table 12.4. Training hyperparameters.

| ML Algorithms | Parameters | Values |
|---|---|---|
| PLR | Polynomial degree | 4 |
| RF | Number of decision trees | 100 |
|  | Depth of decision tree | 20 |
| SVR | Kernel | rbf |
| DNN | Input layer activation function | relu |
|  | Hidden layers activation function | tanh |
|  | Kernal initializer for all layers | normal |
|  | Optimizer | adam |
|  | Batch size | 20 |
|  | Number of epochs | 50 |

RF models were developed by varying the maximum number of trees and maximum depth within the range of 50–300 and 20–50, respectively. The model with the optimal performance and enough trees to ensure randomness in the bootstrapping and tree-building stages of the RF model development. The set maximum number of trees and tree depth in this case are 100 and 20 as shown in Table 12.4. Similar hyperparameter tuning techniques were replicated for PR, SVR, and DNN and the optimal values are presented in Table 12.4.

Table 12.5 shows the mean void fraction and structure velocity model performances for the test data based on the predefined statistical error parameters for each of the ML models. All the ML models, except multiple linear regression, show an acceptable prediction for mean void fraction. Although the performance of the nonlinear models for the mean void fraction in all is above 90%, RF and DNN show superior predictive capabilities in comparison to PR and SVR. As shown in Table 12.5, DNN shows the best R² and RMSE while RF has the best APE and APPE; however, these values are within similar range for both ML algorithms. For the structure velocity, all the nonlinear models show similar capability with an RMSE of 0.1, APPE and R² ranging between 3.5–3.7% and 99.0–99.2%, respectively. The MLR model for U_TB shows acceptable performance with an RMSE and R² of 0.24 and 94.7; however, it is not comparable to the other ML models considered in this study. For this reason, the MLR models for both the mean void fraction and structure velocity are considered unsuitable for further analysis due to their poor performance in comparison to the other ML models. Figure 12.4 shows the cross plots of the predicted parameters against the test data for each of the ML models. For the void fraction, the predicted values all align with 20% of the test data for RF and DNN. Figure 12.4, eludes the poor performance of MLR