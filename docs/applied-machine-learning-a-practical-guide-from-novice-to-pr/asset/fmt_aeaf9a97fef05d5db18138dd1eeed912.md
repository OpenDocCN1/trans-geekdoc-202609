
# Interpreting the Confusion Matrix

The confusion matrix helps you understand how well your classification model is performing in terms of its ability to predict each class correctly.

It provides detailed insight into the types of errors the model is making:

High values on the diagonal (TN and TP) indicate good performance.

High values off the diagonal (FP and FN) indicate areas where the model is making mistakes.

By examining the confusion matrix, you can gain a deeper understanding of your model's performance beyond what is provided by a single metric like accuracy. This can help you identify specific areas where the model needs improvement.

# Confusion Matrix interpretation

Figure 3-49 shows the confusion matrix from the logistic regression model.

![](OEBPS/image_rsrc568.jpg)

Figure 3-49.

Let's interpret this confusion matrix:

True Negatives (TN): 92

These are the instances where the actual class was negative (e.g., no heart disease) and the model correctly predicted it as negative.

False Positives (FP): 6

These are the instances where the actual class was negative, but the model incorrectly predicted it as positive (e.g., predicted heart disease when there was actually none).

False Negatives (FN): 1

These are the instances where the actual class was positive (e.g., malignant tumor), but the model incorrectly predicted it as negative (e.g., predicted no heart disease when there was actually heart disease).

True Positives (TP): 106

These are the instances where the actual class was positive, and the model correctly predicted it as positive.

From this confusion matrix, we can calculate several performance metrics (Accuracy, Precision, Recall, and F1 Score)

Accuracy :

The formula for accuracy is given by:

![](OEBPS/image_rsrc54T.jpg)   

In the provided example:

TN = 92

TP = 106

FP = 6

FN = 1

Plugging these values into the formula:

![](OEBPS/image_rsrc569.jpg)

This means the model correctly classified approximately 86.3% of the instances.

Precision :

The formula for Precision is given by:

![](OEBPS/image_rsrc54V.jpg)

In the provided example:

TP = 106

FP = 6

Plugging these values into the formula:

![](OEBPS/image_rsrc56A.jpg)

This means that approximately 82.6% of the instances predicted as positive by the model were actually positive.

Recall :

The formula for recall is given by:

![](OEBPS/image_rsrc54X.jpg)

In the provided example:

TP =  106

FN = 1

Plugging these values into the formula:  

![](OEBPS/image_rsrc56B.jpg)

This means that approximately 93.5% of the actual positive instances were correctly identified by the model.

F1 Score:

The formula for F1 Score is given by:

![](OEBPS/image_rsrc54Z.jpg)

In the provided example:

Precision=0.9464

Recall=0.9907

Plugging these values into the formula:

![](OEBPS/image_rsrc56C.jpg)

# Interpretation

Accuracy (96.59%) : Indicates that the model correctly predicted 96.59% of the instances, reflecting a high overall correctness in its predictions.

Precision (94.64%) : Of all the instances predicted as positive, 94.64% were actually positive. This indicates a very low level of false positives, highlighting the model's high reliability in making positive predictions.

Recall (99.07%) : The model correctly identified 99.07% of the actual positive instances. This suggests a very low level of false negatives, indicating that the model effectively captures the vast majority of positive instances.

F1 Score (96.80%) : Combines precision and recall into a single metric, providing a balanced assessment of the model's performance. The F1 Score of 96.80% suggests a high level of performance in balancing precision and recall, indicating the model's effectiveness in classifying instances into their respective classes.

# Model Evaluation

After training the machine learning model, it is important to evaluate its performance by checking the accuracy score. The accuracy score shows how well the model fits the data it was trained on, as illustrated in Figure 3-50.

![](OEBPS/image_rsrc56D.jpg)

Figure 3-50.

# Code Explanation

The function `accuracy_score(y_test, y_pred)` from the scikit-learn library is used to calculate the accuracy of a classification model. Here’s a detailed explanation:

Inputs:

y_test: This is the array of true labels for the test dataset. These labels are the actual values that you are trying to predict.

y_pred: This is the array of predicted labels that the model has generated for the test dataset. These predictions are based on the test features (X_test).

# Model Result Interpretation

The accuracy score of 0.9658536585365853 means that the model correctly predicted the class labels for approximately 96.59% of the instances in the dataset.

This indicates that out of all the predictions made by the model, about 96.59% were correct

# Decision Tree Classification Model

A Decision Tree is a robust supervised machine learning algorithm capable of handling both classification and regression tasks effectively. It functions by dividing the dataset into subsets based on specific features, aiming to construct a tree-like structure comprising decision nodes and leaf nodes. At each decision node, the algorithm assesses a feature and determines the optimal split to either maximize information gain or minimize impurity. This recursive process continues until the data is appropriately segmented or a predefined stopping criterion is satisfied.

Decision Trees are favored for their simplicity, interpretability, and versatility in handling both numerical and categorical data. They find widespread application across diverse domains such as finance, healthcare, marketing, and more. Typical uses include customer segmentation, risk assessment, and predictive modeling, making Decision Trees a valuable tool in data-driven decision-making processes.

The source code is available here: [Decision Tree Classification](https://www.google.com/url?q=https://github.com/anyasorc/appliedml/blob/main/Classification_DecisionTree.ipynb&sa=D&source=editors&ust=17200<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk>
