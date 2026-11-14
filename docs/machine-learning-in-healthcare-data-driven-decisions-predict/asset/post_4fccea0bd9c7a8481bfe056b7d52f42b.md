
Table 5: Details about the hyperparameter tuning model.

| Model name | Hyperparameter tuning |
| :--- | :--- |
| Decision tree | – Max depth: None, 5, 20, 15, 20, 25, 30.<br>– Min_samples_split and min_samples_leaf: several candidate values were tested.<br>– Criterion: Evaluated both ‘gini’ and ‘entropy.’<br>– Class weight: None, balanced. |
| Random forest | – N_estimators: 100, 200, 300, and 500.<br>– Max_depth: None, 10, 20, 30.<br>– Min_samples_split and min_samples_leaf: Several small integer values were tested.<br>bootstrap and max features: Evaluated settings include auto, ‘sqrt’, and ‘log2.’ |
| XGBoost | – N_estimators: Ranging from 100 to 500.<br>– Max_depth: Between 3 and 9.<br>– Learning rate: Between 0.01 and 0.3.<br>– Subsample, colsample_bytree, min_child_weight, and gamma: Multiple candidate values were tested. |

## 4.2.1 Selective Feature-Based Approach

This approach gives us the optimum feature set containing 96 features, which maximizes our ML accuracy. We get 81.01% accuracy, whereas in our previous study, only the time domain gives us the best accuracy of 78.75%. The details about the result of the selective feature-based approach appear in Table 6. In Figure 8, we observe that XGBoost obtains the highest accuracy with 96 features. Similarly, the RF model achieves the highest accuracy between 80 features and 90 features; conversely, the DT shows the worst performance and picks its accuracy around 70–80 features.

### Holistic Feature-Based Approach

The detailed result of the holistic feature-based approach appears in Table 7. Figure 9 demonstrates the accuracy versus the number of features for XGBoost, RF, and DT. From the figure, we observe that RF and XGBoost perform the highest, i.e., 79.89%.

We observe in Figure 9 that XGBoost shows stable performance, improving up to 140 features. RF improves with features but shows fluctuations after 100 features – DT shows the worst performance, with high variability and a maximum accuracy of 77.65%.

![](img/106ef0dba620d314f9842503e8ef40c8_332_0.png)

Figure 8: Impact of selected feature count on accuracy in the selective approach, showing how subsets affect model performance to find the optimum set.

Table 6: Accuracy obtained by models using the selective feature-based approach.

| Model | Accuracy (%) | Precision | Recall | F1-score |
| :--- | :--- | :--- | :--- | :--- |
| DT | 77.51% | 0.74 | 0.77 | 0.74 |
| RF | 80.20% | 0.76 | 0.80 | 0.77 |
| XGBoost | 81.01% | 0.77 | 0.81 | 0.78 |

Table 7: Model accuracy performance on holistic feature-based approach.

| Model | Accuracy (%) | Precision | Recall | F1-score |
| :--- | :--- | :--- | :--- | :--- |
| DT | 77.62% | 0.74 | 0.77 | 0.75 |
| RF | 79.89% | 0.75 | 0.79 | 0.75 |
| XGBoost | 79.89% | 0.75 | 0.79 | 0.77 |

## 4.3 Comparison Between Time-Domain and Signal-Domain ML Models

We compare our previously applied method with our new approach in the mixed domain. In Figure 10, we graphically demonstrate the model's performance in different approaches. We observe that SVM and LR show a clear improvement in accuracy when derived features (especially from the signal domain) are used – SVM jumps from 72.56% to 79.80%, and LR from 74.11% to 77.65%. DT, RF, and XGBoost models also benefit from the mixed domain approaches. XGBoost shows 81.01% with the selective feature-based approach, indicating this approach captures some more useful patterns. In both groups, the baseline time-domain features perform the worst, highlighting the value of enhanced feature engineering. In feature engineering, the FFT extracts frequency-based characteristics from signals, revealing hidden periodicities and noise patterns that time-domain features may miss. The recursive feature elimination systematically helps remove irrelevant and redundant features, ensuring our models focus only on the most informative inputs that boost classification. So, we observe that our new approach helps us improve our prediction accuracy.

Accuracy vs Number of Features for Selected Models

- Decision Tree
- Random Forest
- XGBoost

Accuracy (%)

Number of Features

Figure 9: Relationship between the number of selected features and classification accuracy in the holistic feature-based approach, highlighting the feature subset that achieves optimal performance.

Tree-Based Models Feature Comparison

![](img/106ef0dba620d314f9842503e8ef40c8_335_0.png)

SVM & LR Feature Comparison

![](img/106ef0dba620d314f9842503e8ef40c8_335_1.png)

Figure 10: Comparison of model performance using our proposed time-domain and signal-domain features versus previous work that relied solely on raw time-domain data. Right: Performance comparison between our selective and holistic approaches on mixed-domain features and the baseline from previous work.

## 4.4 Neural Network Models

In this section, we explore the neural network (NN) models in time-domain features to further improve the accuracy of the emotion classification model. We use two NN models: FNN and BiLSTM.

The FNN model initially gives 77.47% testing accuracy. Similarly, BiLSTM gives 72.23%. Then we try a different approach where we first balance the dataset using the random oversampling method. After that, we train the ML and NN models. We observe that only LightGBM improves its accuracy using random oversampling, but other ML models show degrading results compared to their previous performance. The detail about the accuracy is shown in Figure 11. Figure 12 shows a model-wise comparison of accuracy performance. XGBoost recorded an accuracy of 81.01%, which is the highest among the machine learning models. Among the neural network models, the Feedforward Neural Network (FNN) is the best performer with an accuracy of 97%.

The detailed NN model approach is given below:

### Preprocessing

We do the necessary preprocessing before fitting the data into the models. We remove unnecessary columns from the dataset before feature selection and encode the target columns into numeric values using LabelEncoder. Then, we use StandardScaler to normalize the features. It helps the model run faster during the training time. We use SelectKBest with a score function (f_classif) to select the top 60 features from the dataset for feature selection. We split the data into training, validation, and testing parts.

### Feedforward Neural Network (FNN)

We build the FNN architecture with three hidden layers containing different neurons. The first hidden layer contains 512 neurons, the second layer contains 256, and the third hidden layer contains 128 neurons. In the first hidden layer, we use the leaky ReLU activation function, and on the output layer, we choose the Softmax activation function. We use the Adam optimizer with a learning rate of 0.00005 and categorical cross-entropy as the loss function. We define a very low learning rate so that it helps smooth convergence during training. If for 10 consecutive epochs there is no improvement, then we automatically run early stopping. We run different epochs from 100 to 1,000 to know their accuracy. This model gives the highest accuracy at 600 epochs, 97%.

### Bidirectional Long Short-Term Memory (BiLSTM)

The BiLSTM model performs best when we use a two-hidden-layer configuration, where the first hidden layer contains 128 neurons and the second hidden layer contains 64 neurons. We set a 50% dropout rate to avoid overfitting. We get the best accuracy at 800 epochs, which is 96.12%.

Model Accuracy Comparison: With vs Without Oversampling

| Model | Without Oversampling | With Oversampling |
| :--- | :--- | :--- |
| SVM | 72.56% | 70.54% |
| Logistic Regression (LR) | 74.11% | 67.92% |
| Decision Tree (DT) | 74.92% | 67.45% |
| Random Forest (RF) | 78.75% | 75.25% |
| LightGBM | 77.81% | 76.40% |
| XGBoost | 78.41% | 77.14% |
| BiLSTM | 77.47% | 72.23% |
| FNN | 97% | 96.12% |

Figure 11: Effect of oversampling on model performance.
