
### 6.2.2.4 Backward Selection Algorithm

The backward selection algorithm is a feature selection method that starts with a whole collection of features before eliminating them one at a time, iteratively [11], based on how they affect a model's performance.

The steps in the backward selection method are as follows:

- 1) Initialization: Start with a complete feature set.
- 2) Feature evaluation: To evaluate the model's effectiveness, consider all the components.
- 3) Feature selection: Choose the feature that has the least impact on the performance of the model. This might be achieved by deleting each part separately and comparing the model's performance with and without the features.
- 4) Model training: Train a model using the remaining set of features.
- 5) Feature removal: Take the chosen feature out of the current list of features.
- 6) Termination: Up until a stopping requirement is satisfied, repeat steps 3 to 5. This requirement could be a minimum improvement in performance, a minimum number of features, or a limited number of iterations.

Every machine learning model that can handle a variable number of features can employ the backward selection approach. It can be applied, for instance, to decision trees, neural networks, logistic regression, and linear regression. Moreover, it can be adjusted to handle features that are continuous, categorical, and binary.

A potential issue is that the backward selection technique did not always select the best subset of features. However it frequently yields a decent approximation of the ideal subset of traits and is computationally effective. Another problem is that it could be susceptible to the choice of stopping criterion, as the model's performance might not always get better as features are eliminated. To ensure the reliability of the findings, it is crucial to carefully select the stopping criterion and do sensitivity analysis.

## 6.2.3 Embedded Method

A feature selection method called the embedded strategy incorporates the feature selection step into the machine learning algorithm's training process [12]. In other words, the algorithm is trained while the features are chosen, and the chosen features are then applied to the final model. This is in contrast to other methods, such as the filter method, which performs feature selection before training the model.

There are various types of embedded feature selection methods, but some of the most commonly used methods are:

- 1) LASSO (Least Absolute Shrinkage and Selection Operator): It is a regularization technique that modifies the model's loss function by adding a penalty term. The model is encouraged by this penalty term to set the coefficients of the less significant features to zero, so choosing just the most significant characteristics.
- 2) Ridge Regression: Another regularization method that increases the loss function's penalty term is ridge regression. In contrast, the penalty component in ridge regression pushes the model to reduce all feature coefficients, though not necessarily to zero. If all aspects are significant, this may improve performance; but, if some features are less significant than others, it may also lead to overfitting.
- 3) Elastic Net: Elastic net, a hybrid of LASSO and ridge regression, uses both penalty terms to balance the sparsity of LASSO and the stability of ridge regression.
- 4) Decision Trees: Decision trees are a nonparametric method that can be applied to both classification and regression applications. The decision tree's splitting criterion can be based on feature importance, successfully selecting the most significant characteristics.
- 5) Random Forest: An ensemble technique that mixes various decision trees is called random forest. In a random forest, the significance scores for each tree are pooled to get the final feature importance. Each tree is trained on a random subset of features.

### 6.2.3.1 Least Absolute Shrinkage and Selection Operator

Least Absolute Shrinkage and Selection Operator, sometimes known as LASSO, is a regularization technique frequently used in linear regression models. By doing feature selection and feature shrinkage simultaneously, LASSO aids in overcoming some of the drawbacks of conventional regression models. As a result, LASSO can recognise and choose the most crucial features in a dataset while lessening the influence of minor features.

A penalty term is incorporated [13] into a linear regression model's cost function to implement LASSO. The punishment term is a multiple of the total absolute value of the regression coefficients. The regularization parameter, or lambda, is a hyperparameter that regulates the severity of the penalty. The penalty component becomes more important as lambda rises, leading to a sparser model with fewer non-zero coefficients.

The capacity to execute feature selection is LASSO's key benefit. By introducing a penalty factor in the cost function, the LASSO algorithm essentially forces the coefficients of less important features to be zero. The outcome is a model that is simpler and easier to understand because LASSO can find and delete elements that are not helpful for predicting the target variable. Moreover, LASSO models are computationally effective due to their sparsity, especially for high-dimensional datasets with numerous features.

The fact that LASSO can manage associated features is an additional benefit. Correlated characteristics can lead to unstable and inaccurate coefficients in conventional regression models. LASSO solves this issue by decreasing the coefficients of associated features towards zero, effectively choosing just one feature to represent the collection of correlated data.

LASSO, however, also has certain drawbacks. It first assumes that the qualities and the aim variable have a linear connection. LASSO might not work well if the relationship is not linear. Furthermore, LASSO makes the assumption that each feature is equally significant, which may not be true for all datasets. Last but not least, selecting the ideal value of the regularization parameter lambda can be difficult because it necessitates cross-validation and can be computationally costly.

As a result, LASSO is an effective regularization method that can enhance the functionality and interpretability of linear regression models. It is a well-liked option for high-dimensional datasets since it can handle correlated features and perform feature selection. When using it to solve real-world issues, though, it's important to carefully analyze its presumptions and limitations.

### 6.2.3.2 Advantages

- 1) More Accuracy: By determining the features that are most pertinent to the current issue, embedded feature selection procedures may increase the model's accuracy. The model may then perform better in terms of generalization, be more accurate, and display less overfitting.

- 2) Reduced Dimensionality: Embedded feature selection approaches can help decrease the dimensionality of the data by selecting the most important features. This might enhance the model's functionality and reduce its computational complexity.

- 3) Faster Training: By including feature selection into the model-training process, embedded feature selection strategies can cut down on the time and computational resources needed to train a model. This can be particularly useful for big datasets with lots of dimensions.

- 4) Model Interpretability: By choosing characteristics that are more significant and pertinent to the issue at hand, embedded feature selection approaches might increase the model's interpretability. This can make the behavior of the model more understandable to consumers.

- 5) Robustness: By identifying the most important features even in the presence of noise, embedded feature selection methods can increase the model's resistance to noise and outliers in the data.

### 6.2.3.3 Disadvantages

- 1) Bias: Embedded feature selection approaches can bias the model by selecting only a subset of the available characteristics. This may cause the model to overlook crucial traits that were not picked.

- 2) Overfitting: The model could still be overfit to the training set of data even when utilizing embedded feature selection approaches. Poor generalization performance may result if the chosen features are too closely related to the training data.

- 3) Complexity: The implementation of embedded feature selection methods may be more difficult than traditional feature selection techniques. This can make it more challenging to understand and apply in practical settings.

- 4) Limited to specific algorithms: Embedded feature selection methods are typically limited to certain types of algorithms, such as linear models or decision trees. This can limit their applicability to other types of models.
