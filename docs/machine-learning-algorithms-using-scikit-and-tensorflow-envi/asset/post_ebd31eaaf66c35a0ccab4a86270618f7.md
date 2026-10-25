
Classification has already been labelled, with the key characteristics/attributes having already been divided into distinct groups.

The act of sending data into a neural network or any machine learning algorithms and allowing it to recognise patterns in the data is known as “training” a model. To build a model for classification task it needs input data or input example in the format of features and the tag or the class label of the example. The data in feature format is processed during the training phase to generate predicted output. Both the features and the labels of the training data are provided to the network or machine learning algorithm as input during training for a supervised classification type work, but only the features are fed as input to the network during testing.

During training it needs data from a number of examples. For example, to classify a person as male or female it needs to consider data (feature data or attribute data e.g., hair length, height etc. of a person) of some male persons and some female persons. Here each person is considered as an example. The set of example’s data which is also called a dataset is split into training and testing sets, which are two distinct sets of inputs. Since the model has already discovered the patterns in this collection of data, testing the classifier on the same dataset that it was trained on would be extremely biased. Instead, the dataset is divided into two sets: a training set that the classifier uses to refine its predictions, and a testing set that the classifier has never seen before. The primary objective of a classification algorithm is to determine the category of a given dataset, and these algorithms are frequently applied to forecast the results for categorical data.

An illustration of supervised categorization is shown in Figure 1. Breast cancer patients’ benign and malignant tumours are identified in the dataset. By fitting a straight line through the data, the supervised classification algorithm will try to divide tumours into two groups. Based on the straight-line categorization, subsequent data can subsequently be categorised as benign or malignant. Only two discrete outputs are shown in Figure 1, although there might be many more categories (benign, Type 1 malignant, Type 2 malignant, etc.).

Figure 1. Classification example

![](img/20813928ec98c7f6fbdbab0d52bde2f1_21_0.png)

An algorithm that performs classification on a dataset is called a classifier. There are mainly two types of classification. One is binary classification and the other type is multi-class classification:
**Binary Classifier:** The term “Binary Classifier” refers to a classification problem where there are only two possible outputs like YES or NO, PLAY or NOT TO PLAY, MALE or FEMALE etc.
**Multi-class Classifier:** A classification problem is referred to be a Multi-class Classifier if there are more than two possible outputs. Classifying images into different categories like dog, cat, horse etc., classifying words into different parts-of-speech (POS) tag, emotion detection etc. are some examples of multi-class classification.

## 2. CLASSIFICATION ALGORITHMS

Scikit-Learn makes a wide range of classification algorithms (Dada et al., 2019; Mukhamediev et al., 2015) accessible. These classifiers include:

- Naive Bayes
- K-Nearest Neighbour
- Decision Trees
- Logistic Regression
- Support Vector Machine (SVM)

### 2.1 Naive Bayes

The Bayes theorem, which makes use of prior information and naive assumptions that the input features exhibit substantial independence from one another, calculates probabilistic categorization.

As an illustration, the classifier may assign an apple to the categories of fruit, red colour, and round form, but each of these labels will be assigned separately. The most popular, quick, and straightforward machine learning classification algorithm, it performs well even with modest amounts of training data.

Mathematically, the Bayes theorem is stated as:

```
P(A|B) = P(B|A)* P(A)/ P(B)
```

where,

- P(A|B) represents the probability of happening event A, given that event B has occurred
- P(B|A) represents the probability of happening event B, given that event A has occurred
- P(A) is the probability of the event A
- P(B) is the probability of the event B

### 2.2 K-Nearest Neighbour

K-Nearest Neighbour is a straightforward machine learning algorithm that relies on the supervised learning technique. When using the K-NN algorithm, it is assumed that the new case and the existing cases can be compared and categorized into the most similar category. When all the existing data is stored, the K-NN algorithm uses similarity to determine the classification of a new data point. The utilization of the K-NN method enables speedy and precise sorting of fresh data into a suitable category. The K-NN algorithm is mainly used to solve classification problems, but it can also be used to solve regression type problems.

Machine learning used in K-Nearest Neighbour classification models is instance-based and functions as a lazy learner. It doesn’t create an internal model because it is a lazy learner. Instead, the n characteristics defined in this categorization are used to represent the data points in n-dimensional space.

The algorithm chooses the class that is most prevalent among the data point’s k nearest neighbours. The labelled points are used to label the closest unobserved data points. The k closest neighbours’ votes are tallied, and the label with the most support from those neighbours is allocated to a new location.

### 2.3 Decision Tree

Decision Tree algorithm is a machine learning algorithm for classification that tries to create a tree structure for visualising a decision-making model. The classification is based on the “if-then-else” scenario, which is equally comprehensive and mutually exclusive. By segmenting the dataset into subsets and selecting the most crucial features for classification, the model’s branches are constructed.

Divide and conquer from the top-down is used to construct the tree. The training set eventually becomes associated with an incremental decision tree as we descend. The final classification structure has nodes and leaves that resemble a tree.

To learn and create rules, singular training data units are employed consecutively. The rows that cover a rule are removed once it has been learned. Until the termination point is reached, the same procedure is carried out on the training set.

### 2.4 Logistic Regression

Logistic Regression algorithm is a machine learning algorithm to classify data. A sigmoid function is used in the logistic regression model to identify the dependencies between the input and output variables and to produce class-label predictions. In order to predict a result, it makes use of numerous independent variables.

A probability output from the sigmoid function is then evaluated with a predetermined threshold in order to assign the label to the object in the appropriate way. For binary classification techniques, it works well.

Logistic regression’s primary flaw is that it makes the assumption that the predictors are independent of one another and that the data are free of missing values. The logistic regression algorithm can be classified as binary, multinomial, or ordinal depending on the kind of output variable.

### 2.5 Random Forest

An ensemble learning technique called random forest categorization is essentially a collection of decision trees. The data from various predictors are combined through ensemble learning. It is a meta-estimator that takes into account the number of trees on various training data subsamples. Subsequently, the predictive model's accuracy is enhanced using their average. In the training phase, the classification creates a large number of decision trees, which produce output as a class, which is the mode of regression prediction of the individual trees.

### 2.6 Support Vector Machine (SVM)

Support Vector Machine (SVM) algorithm is very popular algorithm to classify data. A gap between the two classes and the training data points are represented by the support vector machine in the space. In N-dimensional space (where N is the number of features), the classifier seeks to locate a hyperplane that clearly assigns the data points to either of the classes. The margin is the set of data points from each class that are closest to the chosen hyperplane. The prediction is made to determine the data point category upon the entry of a new point. A non-probabilistic binary classifier is the SVM. By overfitting the data, the regularisation parameter utilised in SVMs facilitates optimization procedures. The classifier uses memory effectively and performs well in high-dimensional domains.

## 3. EXAMPLES OF CLASSIFICATION TASKS

Any work that requires you to group instances into two or more classes is a classification task. Identifying a cat or puppy in a photograph or a wine's quality based on characteristics like acidity and alcohol concentration are examples of categorization tasks. There are many examples of classification type task. Few examples of classification task are mentioned below.

- Handwritten Digit Recognition
- Speech Recognition
- Sentiment analysis
- Email classification (Spam or Not Spam)
- Image classification
- Text classification

You should employ several classifiers depending on the categorization task that you are dealing with. Even while multiple variable logistic regression models exist, a logistic regression model, for instance, works well for binary classification tasks.

You will get a better understanding of when to utilise each classifier as you use them more frequently. Nonetheless, it is usual practise to instantiate several classifiers, compare them to one another in terms of performance, and then choose the classifier that performs the best.
