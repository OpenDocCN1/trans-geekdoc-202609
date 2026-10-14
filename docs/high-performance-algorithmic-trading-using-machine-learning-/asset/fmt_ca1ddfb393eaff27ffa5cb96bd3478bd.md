
For the final classification algorithms (`Gradient Boosting`, `AdaBoost`, `XG Boost`, and `lightGBM`), we will explore rank among the most effective in ML, stemming from ensemble methods like bagging and boosting. These techniques, which we will examine in depth in [Chapter 7](#chap07.xhtml), Advanced Machine Learning Models for Trading, essentially enhance performance by integrating multiple models. This combination leverages the strengths of each component, resulting in a more robust and accurate predictive capability.

### Gradient Boosting Machines

Imagine a team working together to solve a complex problem. `Gradient Boosting Machines (GBMs)` work similarly, building an ensemble of decision trees step by step. Based on the principle of boosting, each tree learns from the mistakes of its predecessors, gradually improving overall prediction accuracy like a team refining its strategy through collaboration. The following are its advantages and disadvantages:

*   **Advantages**: Highly flexible and high accuracy. Can handle complex relationships and different data types
*   **Limitations**: Can overfit, computationally intensive for large datasets (>500k rows)
*   **Important parameter and range**: `learning_rate` often in the range `[0.01, 0.3]`, number of trees in the range `[100, 500]`

As shown in the following figure, it is adept at modeling nonlinear decision boundaries:

![](images/fig-5-13.png)

### AdaBoost (adaptive boosting)

This algorithm sequentially builds an ensemble of classifiers and adapts to previous errors. A boosting technique adjusts the weights of weak classifiers to form a strong classifier.

We will now examine its advantages and disadvantages:

*   **Advantages**: Increases the accuracy of simple classifiers, handles medium datasets (up to 500k rows)
*   **Limitations**: It can be computationally expensive and prone to overfitting. Sensitive to noisy data and outliers
*   **Important parameter and range**: Number of estimators (`n_estimators`) often in the range `[30, 100]`

The following graphs illustrate how `AdaBoost` uses sequential weak learners to create complex decision boundaries:

![](images/fig-5-14.png)

### XGBoost

Building upon the principles of `GBM`, `Extreme Gradient Boosting (XGBoost)` offers a highly optimized and efficient implementation. It is widely regarded as one of the most powerful ML algorithms. `XGBoost` is an advanced implementation of `GBM` that has gained immense popularity. `XGBoost` takes the concept of `GBMs` to the next level, introducing several enhancements for improved performance and efficiency.

Consider the following key features:

*   **Advantages**: High performance, efficiency, and flexibility. Handles missing values
*   **Limitations**: Can overfit if not tuned properly, suitable for datasets up to ~1M rows. Computationally expensive
*   **Important parameter and range**: `max_depth` in range `[3, 10]`, `learning_rate` in range `[0.01, 0.3]`

As a powerful implementation of `GBM`, `XGBoost` effectively classifies complex datasets, as shown in the following graph:

![](images/fig-5-15.png)

### LightGBM

Developed by Microsoft Research and designed for speed and efficiency, `LightGBM` is a gradient boosting framework that excels at handling large datasets.

The following are its key features:

*   **Advantages**: Fast, efficient, and great for handling large datasets (up to several million rows)
*   **Limitations**: Can be overfitting on small datasets, requires careful tuning
*   **Important parameter and range**: Number of leaves often in the range `[20, 40]`, `learning_rate` in the range `[0.01, 0.1]`

The following is a visual representation of how `LightGBM` creates decision boundaries for classification across different datasets:

![](images/fig-5-16.png)

These graphs demonstrate `LightGBM`'s ability to model both linear and non-linear relationships in data. In the first two graphs, we see it successfully separating two classes that are not linearly separable. The rightmost graph shows `LightGBM` creating simpler linear boundaries.

It is important to interpret all the preceding findings cautiously, as the insights gained here may not directly apply to real-world datasets.

Especially in high-dimensional spaces, where data often becomes more separable in a linear fashion, the straightforward nature of classifiers like `Naive Bayes` and linear `SVMs` could result in more effective generalization compared to more complex classifiers.

To conclude, `random forest`, `GBMs`, `AdaBoost`, `XGBoost`, and `LightGBM` are well-suited for handling complex relationships and non-linear patterns in financial data. However, they may require careful parameter tuning and can be computationally expensive.

While simpler models like `logistic regression`, `decision trees`, `kNNs`, and `Naive Bayes` may not always achieve the highest signal-to-noise ratios (as measured by the Sharpe ratio), they offer simplicity, interpretability, and robustness to outliers, making them suitable for specific scenarios.

After exploring algorithms that predict categorical labels, we turn to regression algorithms designed to predict numerical quantities.

## Regression algorithms

`Regression algorithms` are used to predict a continuous numerical value based on one or more input features. In this section, we will explore several regression algorithms, starting with simpler linear models and progressing to more complex nonlinear models. Understanding the distinction between linear and nonlinear models is essential: linear models assume a straight-line relationship between the input features and the target variable, while nonlinear models can capture more complicated, curved relationships.

To illustrate these concepts and the capabilities of different regression algorithms, we will use a toy example. This will allow us to visually observe how each algorithm attempts to model the underlying pattern in the data. Our primary goal is not to achieve optimal prediction accuracy on this specific dataset but rather to gain an intuitive understanding of each algorithm's behavior, strengths, and limitations.

By observing how these models perform on this controlled example, we can gain broader insights into their applicability to real-world regression problems, as follows:

### Linear regression

As a basic algorithm in statistical modeling, `linear regression` models the relationship between a dependent variable and one or more independent variables using a linear equation. Now, let us consider the following strengths and weaknesses:

*   **Advantages**: Simple, interpretable, and efficient for small to medium datasets
*   **Limitations**: Assumes a linear relationship, not suited for complex patterns
*   **Dataset limit**: Efficient for small to medium datasets (up to ~100k rows)
*   **Import syntax**: `from sklearn.linear_model import LinearRegression`

As a first step, we apply `linear regression` to our noisy periodic wave dataset, keeping in mind its inherent limitation in modeling non-linear patterns, illustrated as follows:

![](images/fig-5-17-reg-1-lin.png)

The graph depicts a `linear regression` model (red line) attempting to fit a noisy, periodic dataset, resulting in a straight line that poorly captures the underlying wave pattern. This highlights `linear regression`'s fundamental limitation: its inability to model non-linear relationships, as it can only produce a linear approximation of the data.

### Ridge regression

`Ridge regression` is a variation of `linear regression` designed to prevent overfitting, especially when input features are correlated. It does this by adding a penalty to the model's equation that discourages overly complex models.

Consider the following pros and cons:

*   **Advantages**: Reduces overfitting, good for correlated features
*   **Limitations**: Still assumes linear relationships, not ideal for non-linear data
*   **Key parameter**: `alpha` (regularization strength)
*   **Plausible value**: Typically, in the range `[0.1, 100]`
*   **Dataset limit**: Good for small to medium datasets (up to ~100k rows)
