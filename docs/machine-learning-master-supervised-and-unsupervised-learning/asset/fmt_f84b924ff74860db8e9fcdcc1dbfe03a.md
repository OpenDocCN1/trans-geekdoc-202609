
# Re-sampling methods

Re-sampling is a simple technique of rearranging data samples. Rearranging of data samples ensures that the model will perform well on the dataset which is not seen before. In other words, we can say that the re-sampling will ensure that the model will work perfectly during training and testing. The different re-sampling methods are:

## Random split

The random split method is used to split the data randomly into training, testing, and validation sets. It helps prevent the biased sampling of the dataset. The test dataset is used for the model evaluation purpose. The validation set consists of completely unseen data samples that are not seen in tuning and feature selection also. This is used for a final evaluation of the model.

## Time-based split

Sometimes random split does not work for some specific type of datasets. For example, if we are training the model for weather forecasting, the random split will not work properly. There is the possibility that it will jumble the dataset into different patterns. For such type of dataset time split is the perfect solution.

## k-fold cross-validation

The cross-validation technique is the extended version of the random split method in which the dataset is randomly shuffled and then finally split into `k` different groups.

Therefore `k` groups are considered as testing sets and other groups are considered as training sets. The model is tested on the testing groups and this process will continue for all the `k` groups. At the end of the process `k` different results will be available for `k` different groups and the best model will be selected based on the highest score of the model.

## Bootstrap

This method is close to the random splitting method because it follows the same concept. In the first step, the size of the sample will be selected and generally, it will be equivalent to the size of the original dataset. In the second step, randomly the sample data points will be selected from the original datasets and then finally added to the bootstrap sample. The same process must be repeated `N` number of times and here `N` depends on the sample size. The bootstrap sample contains multiple instances of the same data points.

# Probabilistic measures

Probabilistic measures do not only measure the performance of the model but also considers the complexity of the model. The other important point is that the performance of the model is calculated on the training set only and a test set is not required for the performance evaluation. The different probabilistic measures are:

## Akaike Information Criterion (AIC)

This is a well-known fact that no machine learning model is a hundred per cent accurate. There is always a possibility of information loss and this information loss can be measured by Kulback-Liebler measure. KL measures the difference in the probability distribution of two variables. Hirotugu Akaike is a statistician and he considered the relationship between KL information and the maximum likelihood. He developed a new concept of information criterion Hence Akaike’s information criterion is used to measure the information loss. This method helps choose the best method between two different methods according to the lost information. It can be calculated as:

![](image-dbipij7j.jpg)

Here,

- `L` = Maximum likelihood of the model.
- `N` = Number of data points in the training dataset
- `K` = Number of independent variables.

## Bayesian Information Criterion (BIC)

The concept of BIC was derived from the Bayesian probability concept and it is the best suitable method for models which are trained under the maximum likelihood estimation. The formula for calculating BIC is:

```
BIC = K * log (N) - 2 log
```

Here,

- `L` = Maximum likelihood of the model.
- `N` = Number of data-points in the trainingPro dataset.
- `K` = Number of independent variables.

BIC is suitable when the size of the dataset is not very small.

## Minimum Description Length (MDL)

As the name suggests, MDL can find the minimum number of bits that are required to represent such a type of model. The concept of MDL is derived from the concept information theory and it deals with the quantities such as entropy that measures the average number of bits required to represent an event from a probability distribution or a random variable. MDL can be represented with the help of the following formula:

```
MDL = L(h) + L(D | h)      (6)
```

Here,

- `D` = Predictions made by the model
- `L(h)` = Number of bits required to represent the model
- `L(D | h)` = Number of bits required to represent the predictions from the model

# Model evaluation

Model evaluation is a method for checking the correctness of the model on the test dataset and it plays a big role in academic machine learning in research and industrial settings. The main aim of model evaluation is to estimate the accuracy of the model for unseen datasets or testing datasets. There are different metrics for evaluating the performance of the model but finding the right evaluation metric is always a difficult task and it also depends on the problem that we are trying to solve. A clear understanding of a variety of evaluating parameters can be helpful for the evaluators to understand the problem statement. Now we will discuss all the evaluation metrics in detail.

The evaluation parameters are divided into different categories:

- Classification metrics
- Regression metrics
- Clustering metrics

## Classification metrics

To check the accuracy of every classification model, a confusion matrix is constructed which gives a clear idea of how many test cases are classified correctly. To understand this, let us discuss the confusion matrix:

In the confusion matrix, yes represents the positive classes and 0 or No represents the negative classes and here is the confusion matrix.

There are different ways of representing classification metrics which are discussed as follows:

### Accuracy

Accuracy is the simplest metric for the representation of classification. It can be defined as several test cases correctly classified and divided by the total number of test cases. The formula for calculating the accuracy is:

```
Accuracy = (TP + TN) / (TP + TN + FP + FN)
```

This is the most suitable method for checking the performance of the model if the datasets are unbalanced.

### Precision

Precision is used to find the correctness of the classification and it can be calculated using the following formula:

```
Precision = TP / (TP+FP)
```

This equation represents the ratio between correct positive classifications to the total number of predicted positive classifications. if the fraction value is greater it means higher the precision. A higher precision value represents that model can classify the positive classes appropriately.

### Recall

Recall tells us how many numbers of positive cases are correctly identified out of the total number of positive cases. It can be calculated using the following formula:

```
Recall = TP / (TP + FN)
```

### F1 Score

F1 score is the mean value of recall and precision. Hence it balances the strengths of recall and precision. This is the most suitable evaluation metric where human lives are involved. It can be calculated using the following formula:

![](image-f3ov1pi0.jpg)

### AUC curve

AUC curve is a graph between the true positive rate and the false-positive rate. AUC-ROC stands for Area under the Receiver Operating Characteristics. If it covers more area it means the performance of the model is higher. If the curve is somewhere near the 50% diagonal line, it suggests that the model randomly predicts the output variable.

![](image-40nq0140.jpg)

Figure 4.5: AUC –ROC Curve.
