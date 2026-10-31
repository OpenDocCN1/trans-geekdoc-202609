approach changes categorization and regression tree construction. RFR outperforms support vector machines (SVM) and other ML models [91]. It just requires two parameters: the number of variables in the random subset at each node and the number of trees in the forest, making it user-friendly and overfit-resistant. Values for these parameters seldom matter [92]. In practical implementation, the dataset is divided into distinct segments corresponding to each input variable. The computation of the sum of squared error (SSE) involves the evaluation of anticipated and actual values at each of the given locations. Following that, the minimum sum of squared errors (SSE) value of the node is computed, as described in the reference [93].

# 4.1.3 K-Nearest Neighbors (KNN)

KNN algorithm is a well-established nonparametric method that aims to point the k-nearest data points to a query and categorize them using a majority vote. [94]. The method is widely recognized and utilized in modern computer programming techniques due to its efficacy, simplicity, and intuitive nature [95, 96]. A significant benefit of the KNN algorithm is its independence from a dedicated training phase as it highlights the capacity of KNN to classify data points without prior knowledge of the statistical properties of the training examples [97, 98].

# 4.2 Training and Evaluation of ML Models

To conduct the training and testing of the aforementioned models, the dataset containing circular and noncircular types is partitioned into training and testing sets. The division is done in a ratio of 8:2, where 80% of the data is allocated for training the models and the remaining 20% is utilized for evaluation purposes. The models were constructed using the Scikit-learn library in Python. Within this framework, the process of optimizing hyperparameters was accomplished by employing grid search cross-validation, a methodical approach to fine-tuning parameters. The predictive framework encompasses the development of two distinct submodules, each meticulously tailored to the specific geometry of the specimen circular or noncircular. The sub-models were diligently designed to effectively depict the complexities inherent in their corresponding specimen types. Additionally, a comprehensive final prediction model was developed. The integrated model demonstrates the capacity to independently identify the geometric characteristics of the input specimen, distinguishing between circular and noncircular shapes. It then proceeds to direct the input to the appropriate submodule. The utilization of a dual submodule technique in this study serves to enhance the versatility and adaptability of the model, hence providing accurate predictions over a variety of specimen geometries. The final

Table 4 ML models hyperparameters for circular and noncircular specimens

| Type | ML models | Hyperparameters | Values |
|---|---|---|---|
| Circular specimens | XGBoost | Learning rate | 0.2 |
|  |  | max-depth | 3 |
|  |  | n-estimators | 100 |
|  | KNN | n-neighbors | 3 |
|  |  | Weights | Distance |
|  | RFR | Max-depth | 5 |
|  |  | Min samples split | 2 |
|  |  | n-estimators | 100 |
| Noncircular specimens | XGBoost | Learning-rate | 0.2 |
|  |  | Max-depth | 3 |
|  |  | n-estimators | 300 |
|  | KNN | n-neighbors | 3 |
|  |  | Weights | Distance |
|  | RFR | Max-depth | 5 |
|  |  | Min-samples-split | 2 |
|  |  | n-estimators | 100 |

prediction model incorporates the six outputs for circular specimens and eight outputs for noncircular specimens produced from the ML model. The procedure is depicted in Fig. 1. There were separate testing and training for circular and noncircular data points. The hyperparameter values for the machine learning models are presented in Table 4.

# 4.2.1 Evaluation Metrics

In this study, the key evaluation metrics, namely $R^2$, $MAE$, $MSE$, and $RMSE$, were utilized to assess the performance of the developed predictive models. The $R^2$ metric measures the model's ability to explain the variability in the data, with higher values indicating a better fit. The $MAE$ matric quantifies the average magnitude of errors between predicted and actual values, offering a straightforward measure of accuracy. A lower $MAE$ implies better model performance. On the other hand, $MSE$ matric represents the average of the squared difference between the original and predicted values in the data set. It measures the variance of the residuals. Lastly, the $RMSE$ is similar to $MAE$ but places a greater penalty on larger errors, providing insights into the spread of prediction errors. A lower value of $MSE$ and $RMSE$ suggests that the model's predictions are generally close to actual values. These metrics collectively help evaluate the model's explanatory power, accuracy, and precision, enabling informed decisions about its effectiveness. Equations 8–11 illustrate the expressions