Overcoming these issues includes preprocessing data, adjusting model parameters, and choosing different techniques depending on the characteristics of the dataset and the application’s needs.

# Question 9: Can SVR be sensitive to outliers, and what techniques can be used to address this issue?

Answer: Yes, SVR is sensitive to outliers because outliers distort the positioning of the regression hyperplane and decrease the accuracy of the model.

Here is a brief explanation of techniques to address this issue:

+   - **Data cleaning:** To keep away from the influence of outliers the preferred approach is to eliminate them from the dataset before training or to compute their median instead of the mean.
+   - **Robust loss functions:** When optimizing massive data, one should employ reasonable loss functions, such as Huber loss, in order to minimize the skewness of large values.
+   - **Outlier detection and handling:** As for outliers, out of them, you need to exclude or using robust estimators.
+   - **Regularization:** The regularization parameter (C) is decreased, thus aiming to reduce the level of outliers’ penalty and, as a consequence, enhance the model’s robustness.
+   - **Kernel methods:** It is recommended to use biasing functions like the RBF kernel, which are not very sensitive to the difficulties of moving their influences around while smoothing.

Thus, by applying these techniques, SVR is immune to the outliers, and hence, the model works well on unseen data