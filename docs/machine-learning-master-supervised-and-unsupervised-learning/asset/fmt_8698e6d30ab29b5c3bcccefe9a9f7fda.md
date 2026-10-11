
# Support Vector Regression

SVM algorithm is used for classification and regression. If this algorithm is used to solve the regression problem then it is called Support Vector Regression. This algorithm works for continuous variables. There are some keywords that are used for support vector regression that is also shown in Figure 4.10.

![](image-vsqae769.jpg)
**Figure 4.10: Support vector machine regression**

- **Kernel**: This function is used to map the low dimensional data into high dimensional data.
- **Hyper Plane**: In SVM, this line is used to separate the two different classes. But in support vector regression, this line is used to predict the continuous variables and it tries to cover all the data points.
- **Boundary Line**: Boundary lines are the two lines that are far from the hyperplane and it is used to create a margin for the data points.
- **Support Vector**: These are the data points that are nearest to the hyperplane.

# Decision Tree Regression

This is another algorithm that is used for classification and regression-related problem. This algorithm is able to deal with categorical and numerical data. As name suggests, this algorithm builds a tree structure in which internal node of the tree represents the test attributes and each branch is representing the results of the test and the leaf node represents the final output or decision. When we start constructing a tree then the first node is called root node or parent node and parent node is split into two parts: left child node and right child node.

# Ridge Regression

A linear or polynomial regression sometimes fails if there is a high correlation between the independent variables. To solve such problems, ridge regression can be used. This is an extended and robust version of linear regression and in this small amount of bias is introduced which is helpful for long term predictions. The amount of bias that is added in the model is known as the ridge regression penalty. This penalty can be computed by multiplying the lambda with the squared weight of the features. This method is also referred to as regularization technique and can be used for reducing the complexity of the model and it is also called L2 regularization.

# Lasso Regression

It is a technique for regularization which is also helpful for reducing the complexity of the model. This method is the same as ridge regression except that the penalty term contains only the absolute weights instead of the square of weights. Since it takes absolute values, hence, it can shrink the slope to 0, whereas ridge regression can only shrink it near to 0. It is also referred to as L1 regularization.

# Classification

Classification is a supervised machine learning algorithm that is used to categorize different classes. The common classification related applications are speech recognition, face recognition, document verification, and so on. The classification problem can be related to the binary or multiclass classification problems. Many algorithms are available which are used for classification purposes and it is already shown in Figure 4.11. Let's discuss some of the classification algorithms:

## Naive Bayes Classifier

This method is based on the Bayes' Theorem and it works on an assumption that the presence of a particular feature in a class is unrelated to the presence of any other feature. This algorithm is easy to build and it is very helpful for the large-sized datasets. This algorithm is also called as Generative Learning.

## Nearest Neighbor algorithm

It is another supervised classification algorithm that uses the concept of proximity or sameness. This algorithm uses a bunch of labeled points for the learning purpose and then further use them for labeling of other points. If the algorithm wants to label other new points then it looks at the labeled points which are closer to the new points. Closeness can be expressed as a dissimilarity function. The algorithm will check the new points with k number of the neighborhood points and finally assign the label according to the points that the neighbors have. The same concept is explained in Figure 4.12.

![](image-o73meqvz.jpg)
**Figure 4.11: Example of nearest neighbor algorithm**

But always using the geometric distance for finding the nearest m-neighbor doesn't work because sometimes input data can be available in text form. In that case, finding the geometric distance is not a suitable approach. Hence, we need to choose other parameters as the distance metrics.

## Logistic Regression

Logistic regression is sometimes referred to as predictive learning model. This method is suitable when more than one independent variable is used to determine the value of a dependent variable. The main goal of the logistic regression is to find the best fitting model which can describe the characteristics of the independent variable and dependent variable. This method is better than nearest neighbor because it's able to explain the quantities features which lead to classification.

## Decision Trees

This is another algorithm that is used for classification and regression-related problems. This algorithm can deal with categorical and numerical data. As the name suggests, this algorithm builds a tree structure in which the internal node of the tree represents the test attributes and each branch represents the results of the test and the leaf node represents the final output or decision. When we start constructing a tree then the first node is called root node or parent node and the parent node is split into two parts: left child node and right child node.

## Neural Network

A neural network consists of neurons and these neurons are arranged in layers that can convert the input vectors into some output vectors. Each unit of the neuron works as an input and then applies a non-linear function on the input and finally its passes the output to the layer. Generally, this network is a feed-forward network in which a unit feeds its output to all the units of the next layers but there is no possibility of feeding the output back to the previous layers.

# Unsupervised learning

Unsupervised learning algorithms are those algorithms where you have input values or input data but there are no corresponding output variables. The main goal of unsupervised learning is to understand the structure of the data or the distribution of the data and these algorithms help the learners to understand more about the data. In unsupervised learning, there is no concept of teachers. Algorithms have their own choice to learn and explore more about the data. In unsupervised learning, data is neither classified nor labeled and the algorithm will work without any guidance. Here, the task of the machine is to group unsorted information according to similarities, patterns, and differences without any prior training of data as shown in Figure 4.13.

![](image-lqidp82n.jpg)
**Figure 4.12: Overall process of unsupervised learning**

The different types of unsupervised machine learning algorithms are available which we will discuss now:

## Hierarchical Clustering

These algorithms can build the hierarchy of clusters. In the beginning, the data is assigned to the nearest cluster, and if two clusters are close to each other then they will be merged. This algorithm will end if there is only one cluster left.
