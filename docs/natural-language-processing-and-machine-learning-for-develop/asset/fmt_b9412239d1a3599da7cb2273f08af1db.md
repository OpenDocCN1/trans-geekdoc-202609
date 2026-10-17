
import pandas as pd from sklearn import metrics from sklearn.model_selection import ShuffleSplit from sklearn.model_selection import cross_val_score  # Import the wine dataset: dataset = pd.read_csv('wine.csv') X = dataset.iloc[:, [0, 1]].values y = dataset.iloc[:, 2].values  # split dataset into training and test sets: from sklearn.model_selection import train_test_split X_train, X_test, y_train, y_test = train_test_split(X, y, test_size = 0.25, random_state = 0)  # scale the feature values between 0 and 1: from sklearn.preprocessing import StandardScaler sc = StandardScaler() X_train = sc.fit_transform(X_train) X_test = sc.transform(X_test)  # option 1: use cross validation cv=8 from sklearn.neighbors import KNeighborsClassifier classifier = KNeighborsClassifier(n_neighbors = 10, metric='minkowski', p=2) scores = cross_val_score(classifier, X_train, y_train, cv=cv) print("=> option 1 default scores:") print(scores) print()  # option 2: use a scoring parameter  # The score at each CV iteration is the score method of the estimator that can be modified via the scoring parameter: more details here: [https://scikit-learn.org/stable/modules/model_evaluation.html#scoring-parameter](https://scikit-learn.org/stable/modules/model_evaluation.html#scoring-parameter) scores = cross_val_score(classifier, X_train, y_train, cv=cv, scoring='f1_macro') print("=> option 2 f1_macro scores:") print(scores) print()  # 3) pass a cross validation iterator: # cross_val_score uses KFold or StratifiedKFold if cv is an integer: n_samples = X_train.shape[0] cv = ShuffleSplit(n_splits=10, test_size=0.3, random_state=0) print("=> option 3 ShuffleSplit scores:") print(cross_val_score(classifier, X_train, y_train, cv=cv))

Launch the code in [Listing 8.7](#ch08.xhtml#list8.7) and you will see the following output: => option 1 default scores: [0.64705882 0.76470588 0.82352941 0.82352941 0.82352941 0.8125 0.8125 0.875 0.875] => option 2 f1_macro scores: [0.63822844 0.76550117 0.80769231 0.81678322 0.81678322 0.81818182 0.81111111 0.86666667] => option 3 ShuffleSplit scores: [0.75 0.8 0.85 0.775 0.775 0.625 0.8 0.775 0.85 0.775]

## Evaluating Classifiers

Whenever you select a classifier for a dataset, it’s obviously important to evaluate the accuracy of that classifier. Some common techniques for evaluating classifiers are listed here:

* precision and recall

* ROC curve (receiver operating characteristics)

*Precision and recall* are discussed in an earlier chapter and they reproduced here for your convenience. First, let’s define the following variables:

TP = the number of true positive results FP = the number of false positive results TN = the number of true negative results FN = the number of false negative results 

Then the definitions of precision, accuracy, and recall are given by the following formulas:

precision = TP/(TN + FP) accuracy = (TP + TN)/[P + N] recall = TP/[TP + FN] 

The *receiver operating characteristics* (ROC) curve is used for visual comparison of classification models that shows the trade-off between the true positive rate and the false positive rate. The area under the ROC curve is a measure of the accuracy of the model. When a model is closer to the diagonal, it is less accurate and the model with perfect accuracy will have an area of 1.0.

The ROC curve plots the true positive rate (TPR) versus the false positive rate (FPR). Another type of curve is the PR curve that plots precision versus recall. When dealing with highly skewed datasets (strong class imbalance), precision-recall (PR) curves give better results.

## Trade-offs for ML Algorithms

This section contains a brief description of the trade-offs of various ML algorithms that were discussed earlier in chapter.

In general, there is no *a priori* way to determine which algorithm works best for a given dataset. Hence, it’s a good idea to try every model (or as many as are feasible), tune the hyperparameters accordingly, and analyze the errors carefully. If time and space are constraints, try using a subset of the original dataset (perhaps 25%), and after determining which algorithm produces the best results, use the same algorithm on the full dataset.

*kNN best cases:*

* kNN outperforms logistic regression and linear SVM when the data is not linear.

* There is no latency requirement; kNN performs well on data with few dimensions.

* Training is not required for the kNN, so new data can easily be handled by the model.

*kNN limitations:*

* kNN is not recommended for large datasets as kNN is a distance-based model: the cost of calculating the distance from query point to every point in data is very high.

* Make sure you standardize or normalize before distance measure.

* When data is imbalanced, kNN predicted values are biased toward the majority class.

* kNN doesn’t work well on large dimensional data due to the curse of dimensionality.

* Performance gets worse with heavily randomized data.

*Logistic regression best cases:*

* It’s very fast at the inference stage.

* Trained weights from logistic regression shows the importance of each feature.

* Output generated by logistic regression are probabilities, which is advantageous over models (such as SVM) that provide only labels as output.

* It’s a recommended initial model that is simple and elegant to implement.

*Logistic regression limitations:*

* It behaves poorly with highly nonlinear data.

* Outliers can adversely affect the decision boundary.

* Collinearity affects the interpretability of weights for feature importance.

*Decision trees best cases:*

* There’s no need for computation after training the model.

* There’s support for multiclass classification and regression tasks with categorical and numerical data.

* Important features can be obtained.

* Scaling, standardization, or normalization of data is not required.

*Decision trees limitations:*

* They are computationally expensive for splitting tree nodes (based on all features and requires calculation of information gain).

* Decision trees have axis parallel boundaries: they are not well-suited for smooth boundaries.

* They do not perform as well when there are unrelated variables.

*SVM best cases:*

* It works well for small(er) datasets

* SVM is less susceptible to outliers.

* There is fast inference time.

*SVM limitations:*

* Selecting the correct kernel is not simple.

* It’s computationally expensive for large data.

* It’s difficult to interpret feature importance from the weights.

This concludes the portion of the chapter pertaining to statistical terms and techniques for measuring the validity of a dataset. Now let’s look at activation functions in Machine learning, which is the topic of the next section.

## What are Activation Functions?

An activation function is (usually) a nonlinear function that introduces nonlinearity into a neural network, thereby preventing a “consolidation” of the hidden layers in neural network. Specifically, suppose that every pair of adjacent layers in a neural network involves just a matrix transformation and no activation function. Such a network is a linear system, which means that its layers can be consolidated into a much smaller system.
