
By applying SelectFromModel along with logistic regression, it selects features that carry great importance.

- Decision Tree Classifier: Decision trees evaluate the significance of features based on how effectively they divide the data. Features that result in splits are considered more significant. The ExtraTreesClassifier, which is a type of decision tree, combines outcomes from multiple trees to determine feature selection.

- Principal Component Analysis: PCA is a technique used to reduce the dimensionality of data by transforming it into a new coordinate system. In this system, the largest deviations in the data projections align with the initial principal components. PCA achieves this by minimizing features while preserving a massive portion of the original dataset variability. The process involves projecting the data onto components that are derived from linear combinations of the original features. The result is a set of components or uncorrelated features that capture most of the data variance.

In summary, employing selection methods like selection based on variance, model-based selection, and PCA are essential for enhancing the effectiveness and efficiency of learning models. These approaches can boost the performance of models, highlight key aspects, and simplify data complexity [8].

### 3.9.4 Oversampling for Imbalanced Datasets

When it comes to classification tasks, datasets often suffer from an imbalance, where one class outweighs the other significantly. This disparity can lead the model to lean towards the majority class, resulting in biased performance and poor accuracy predictions for the minority class. To tackle this issue, oversampling techniques like the synthetic minority oversampling technique (SMOTE) are employed to equalize the class distribution. SMOTE allows for the creation of samples specifically for the underrepresented class within a dataset. Instead of simply duplicating existing minority class instances, SMOTE generates new synthetic samples through interpolation between existing data points. This process involves selecting points and generating additional samples along the lines connecting these points to their neighbouring instances. By doing so, SMOTE effectively boosts the representation of the minority class, leading to a more balanced dataset overall.

To determine how classes are distributed, the approach begins by examining the initial dataset. In cases of imbalance, the minority class may be underrepresented, leading to a flawed model. Subsequently, SMOTE is applied to the dataset to generate additional instances of the minority class. This adjustment helps create a foundation for training by balancing the number of samples across classes. The modified dataset, with an equal number of samples for each class after SMOTE, is utilized for further analysis or model training. This balance boosts the model's performance and reduces bias by enhancing its ability to generalize across all classes. With the support of the newly generated synthetic samples, the model gains insights into the minority class, improving prediction accuracy and overall robustness.

SMOTE is an approach to address imbalanced classes in datasets. By generating examples, it ensures that the model is trained on a dataset, leading to improved performance for both majority and minority classes. This technique is crucial for developing unbiased and precise models, especially in scenarios where outcomes can be significantly influenced by class imbalance [9].

## 3.10 MODEL EVALUATION AND VISUALIZATION

### 3.10.1 TRAINING AND TESTING THE MODEL

The model evaluation process starts with training a classification model on a dataset. In this instance, we use a random forest classifier, which combines multiple decision trees and merges their results to boost accuracy and reliability. We split the dataset into training and testing parts using a set test size, making sure we can assess the model on data it has not seen before.

Once we have trained the model, we make predictions on the test set. We then gauge the model's performance using accuracy, which shows how many predictions were correct out of all the predictions made. The classifier function gives back the trained model, predictions, actual labels, and accuracy score.

### 3.10.2 CONFUSION MATRIX CALCULATION

A confusion matrix helps us check how well a classification model works. It breaks down the model's guesses in detail, showing true positives, true negatives, false positives, and false negatives. To figure out these numbers, the confusion_matrix function compares the labels the model predicted to the real labels.

Here is how the confusion matrix is set up:

- **True Positives (TP):** Instances where the model correctly predicted the positive class.
- **True Negatives (TN):** Instances where the model correctly predicted the negative class.
- **False Positives (FP):** Instances where the model incorrectly predicted the positive class.
- **False Negatives (FN):** Instances where the model incorrectly predicted the negative class.

These values are used to construct a matrix that visually represents the performance of the model.

### 3.10.3 VISUALIZATION OF THE CONFUSION MATRIX

To understand the confusion matrix better, we show it as a heat map. The plot_confusion_matrix function creates this visual. The heat map gives us a clear picture of how well the model works. Each box in the matrix shows how many times the model predicted a class compared to the actual class.

We can display the matrix with or without normalization. Normalization changes the values to percentages, which helps when comparing different datasets or models. The function uses colours to make things clearer, and it puts the exact numbers in each box for more detail.

To wrap up, evaluating a model involves three steps: training it, getting its predictions, and checking how well it used a confusion matrix. This matrix sheds light on what the model does well and where it falls short. Seeing it makes it easier to grasp the results. This method gives us a full picture of how good the classification model is and ensures a comprehensive evaluation of the classification model's performance.

### 3.10.4 Feature Selection and Classification

The first step in the process is to get the dataset ready. This involves cleaning up any missing data. Next, we use the SVC to choose features. It finds and keeps the most important traits for sorting. After that, we balance the picked features using SMOTE. We do this to fix any class imbalance in the dataset. This step ensures the classifier has a balanced dataset to work with.

The random forest classifier, trained on balanced data, classifies the samples. To evaluate the model's performance, we calculate its accuracy score and analyse the data using a confusion matrix. This matrix, which we visualize with normalization, gives us insight into the model's strong and weak points by showing true positives, true negatives, false positives, and false negatives. This thorough assessment helps us understand how well the model works and spot areas we can make better. Figure 3.1 illustrates the normalized confusion matrix for SVC feature selection with random forest classification.

![](img/402dddaf38ede9d8a9b9be4ba7a9004a_70_0.png)

**FIGURE 3.1** Normalized confusion matrix for SVC feature selection with random forest classification.

In the same way, once we get the dataset ready and clean it up, we use a logistic classifier to pick out the best features. This classifier checks which features are most likely to predict the outcome, which helps us narrow down the dataset to the most useful variables. After this, we balance the dataset again using SMOTE. This makes sure the classifier learns from an even spread of classes.

The balanced dataset serves as input to train a random forest classifier. We measure the classifier's performance using accuracy and create a normalized confusion matrix to assess the model's classification abilities. The confusion matrix, which we visualize with normalization, shows how well the model differentiates between classes, including true positives, true negatives, false positives, and false negatives. This evaluation gives us a clear picture of how the model performs and points out areas we can improve and optimize. The normalized confusion matrix for logistic feature selection with random forest classification is shown in Figure 3.2.

A decision tree model helps pick out key features after the dataset is ready and cleaned up. This method checks how important different traits are, making it easier to spot the ones that matter the most for predicting outcomes. By focusing on the most influential factors, the classification process becomes more productive and effective, thanks to the chosen features.

![](img/402dddaf38ede9d8a9b9be4ba7a9004a_71_0.png)

FIGURE 3.2 Normalized confusion matrix for logistic feature selection with random forest classification.
