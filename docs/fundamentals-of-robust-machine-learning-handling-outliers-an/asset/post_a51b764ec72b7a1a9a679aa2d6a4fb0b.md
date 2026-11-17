
with a neural network. The third task addresses the problem of variable importance and correlations between them. With these data science objectives in mind, we follow a sequence of steps typically used in machine learning and data science, albeit in a streamlined fashion.

### 12.2.1 Exploratory Data Analysis

When we first obtain a dataset, we do not have any idea about its contents and characteristics so we need to perform EDA. Typically, the first step is to determine whether there are any missing values in any of the columns of the dataframe.1 The Boston Housing dataset has missing values but here we will assume that some method of imputation is used to resolve this issue.

With a complete dataframe now in our possession, the next task is to examine the characteristics of the dataset. Some of these steps were shown in Chapter 4. Notably, we want to determine if there are outliers in the dataset and, if so, how many and where they are located. For example, the boxplots for the explanatory and response variables were presented in Chapter 4 to address these questions. The boxplots indicate the presence of outliers; so we will have to be extra careful about any operations performed that assume outlier-free data. Some preliminary analysis involves extraction of descriptive statistics such as the min, max, mean, median, quartiles, and standard deviation. These values are inspected to determine if standardization is required to enhance the performance and accuracy of downstream machine learning tools. The numerical ranges of the features were provided graphically in Chapter 4 which tells us that robust standardization will be needed.

Before going further, one useful step is to get a sense of the number of outliers for each variable in the dataframe. Another step is to examine the correlation coefficient matrix. The idea is to understand certain relationships between variables. Table 12.1 lists the variable names, the projected number of outliers using the 1.5-IQR edit rule (see Chapter 4), and the correlation coefficients relative to the response variable, MEDV. The number of outliers2 indicates that we will likely have to resort to outlier removal. As a result, we cannot fully trust any of these correlation values. However, we find that variables RM and LSTAT are likely to have strong correlations to MEDV. Part of the data science problem here is to figure out how to accurately compute the number of outliers and correlations. We will explore the options in the sections to follow.

Next, we examine MEDV in the form of a boxplot and histogram in Figure 12.1. When the data is represented using this type of visualization, it is possible to observe both the frequency distribution and summary statistics of MEDV, making it easier to identify patterns, trends, anomalies, and unusual characteristics in the data. The boxplot identifies a total of 40 outliers in the response variable. The histogram indicates the presence of a number of homes priced at exactly $50K which appears suspicious given the Gaussian-type distribution of the rest of the data. The reason for this is not clear at this stage but it could be due to censored data, or perhaps the values of these homes were high but unknown and they were simply assigned to $50K as a default (i.e. winsorized data as described in Chapter 4). This will create

Table 12.1 Outlier counts for the Boston Housing variables using 1.5-IQR criteria, percentage of the total data, and correlation coefficients with respect to MEDV.

| Feature set | Number of outliers | Percent (%) | Correlation coefficient (MEDV) |
|---|---|---|---|
| CRIM | 65 | 12.9% | -0.39 |
| ZN | 68 | 13.4% | 0.36 |
| INDUS | 0 | 0.0% | -0.48 |
| CHAS | N/A | N/A | 0.18 |
| NOX | 0 | 0.0% | -0.43 |
| RM | 30 | 5.9% | 0.70 |
| AGE | 0 | 0.0% | -0.38 |
| DIS | 5 | 1.0% | 0.25 |
| RAD | 0 | 0.0% | -0.38 |
| TAX | 0 | 0.0% | -0.47 |
| PTRATIO | 15 | 3.0% | -0.51 |
| B | 77 | 15.2% | 0.33 |
| LSTAT | 7 | 1.4% | -0.74 |
| MEDV | 40 | 7.9% | 1.00 |

headaches for the least squares (LS) method. We now have mounting evidence that we should resort to robust approaches.

One more check can be performed to determine the nature of the apparent outliers for two important variables. The RM variable has a strong positive correlation with MEDV (see Table 12.1) and a scatter plot confirms this, as shown in Figure 12.2. The LSTAT variable has a strong negative correlation with MEDV and a scatter plot in Figure 12.2 confirms this as well. We can observe the $50K homes along the top right and top left portions of the two plots, respectively. More outliers seem to be present for RM compared to LSTAT, but it is not clear if they are outliers or inliers at this stage. Any removal of the inliers would be a mistake so if we were to consider eliminating all $50K homes from the dataset, we may lose valuable information. Again, the idea of removing outliers before any regression is applied can be dangerous as it may lead to lower-quality models and higher prediction errors.

### 12.2.2 Neural Network Architecture

After the preliminary analysis of the data and potential outliers, it is time to decide how to proceed in building a model. For comparison purposes, LC can be used for the robust case, while for the non-robust case, LS can be used. It is possible to use standard linear regression methods but this is a particularly challenging dataset. The option of polynomial expansion of the variables exists to increase the feature space. A more powerful method to tackle this problem is to use a neural network (NN) for linear regression, as shown in Figure 12.3. It has 13 inputs, 1 output and one hidden layer comprised of 39 relu units.

![](img/f26d7f591c2a080d86425985301266a4_361_0.png)

![](img/f26d7f591c2a080d86425985301266a4_361_1.png)

Figure 12.1 Relationship between boxplot and histogram of MEDV indicating suspected outliers and a large spike at $50K.

![](img/f26d7f591c2a080d86425985301266a4_361_2.png)

![](img/f26d7f591c2a080d86425985301266a4_361_3.png)

Figure 12.2 Scatter plot of MEDV vs. RM and LSTAT indicating suspected outliers.

![](img/f26d7f591c2a080d86425985301266a4_362_0.png)

Figure 12.3 Neural network used for Boston Housing dataset.

As described in Chapter 9, this neural network creates 13 x 39 + 39 = 546 parameters which increases the parameter space dramatically. This will allow for a better fitting of the model to the data, although there is a high risk of overfitting. As a result, we need to establish a methodology to produce a regularized model to avoid overfitting.

Regularization was discussed in detail in Chapter 6. For example, reducing model complexity and the use of a ridge penalty function are effective methods to regularize models. Regularization can also be performed by controlling the number of iterations and this is how we will proceed here. Rather than letting the network converge to a set of final parameter values, an early-stopping criteria will be established so that a regularized model is produced. To accomplish this, we first divide the dataset into a training set and a test set using an 80–20 split. The resulting training set has 404 observations and the test set contains the remaining 102 observations. Then, we place the test set to one side and work with only the training set to build the model. To generalize the model, a 10-fold cross-validation (CV) scheme (as described in Chapter 6) can be used to find the optimal number of iterations with the smallest error.

The internal workings of a k-fold CV scheme are somewhat opaque to the user. An alternative, which is more transparent, is to use a related iterative method whereby the training set is randomly divided into CV training and test sets several times. In each pass, the two sets are used as if they were one fold of a k-fold CV scheme. This so-called k-randomized validations scheme is repeated a number of times, say 10 times, to get a similar effect as a 10-fold CV scheme. Accordingly, each CV training set can be processed over a large number of iterations to find the iteration at which the prediction error on the CV test set is minimized. Then, the optimal number of iterations across the 10-folds can be used to build a regularized model.

The results of this procedure are shown in Figure 12.4. The motivation behind this idea is based on the bias–variance trade-off. If we iterate too long, we end up overfitting. If we do not iterate enough, we are underfitting. The sweet spot between the two provides the optimal amount of fitting. The measurement criteria of the prediction error on each generated test set are the root-mean-square error (RMSE) and
