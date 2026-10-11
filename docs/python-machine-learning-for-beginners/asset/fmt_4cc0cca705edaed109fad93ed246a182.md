
# Machine Learning Overview

Machine Learning evolved from computer science that primarily studies the design of algorithms that can learn from experience. To learn, they need data that has certain attributes based on which the algorithms try to find some meaningful predictive patterns. Majorly, ML tasks can be categorized as concept learning, clustering, predictive modeling, etc. The ultimate goal of ML algorithms is to be able to take decisions without any human intervention correctly. Predicting the stocks or weather is a couple of applications of ML algorithms.

There are various ML algorithms like Decision trees, Naive Bayes, Random forest, Support vector machine, K-nearest neighbor, K-means clustering, etc.

From the class of ML algorithms, the one that you will be using today is a k-nearest neighbor. Now, the question is what exactly is the K-Nearest Neighbor algorithm? So let us embark on finding out!

## What is a k-Nearest Neighbor?

The KNN or k-nearest neighbor algorithm is a supervised learning algorithm; by supervising it means that it makes use of the class labels of training data during the learning phase. It is an instance-based ML algorithm, where new data points are classified based on stored, labeled instances (data points). KNN can be used both for classification and regression; however, it is more widely used for classification purposes.

The `k` in KNN is a crucial variable also known as a hyperparameter that helps in classifying a data point accurately. More precisely, the `k` is the number of nearest neighbors you wish to take a vote from when classifying a new data point.

![Figure 1. Visualization of KNN](Images/image00243.jpeg)

You can see as the value of `k` increases from 1 to 7, the decision boundary between two classes having some data points becomes smoother.

Now the question is how does all of this magic happen, wherein every time a new data point comes in, it is classified based on the stored data points?

So, let's quickly understand it in the following ways:

*   Firstly, you load all the data and initialize the value of `k`.
*   Then, the distance between the stored data points and a new data point that you want to classify is calculated using various similarity or distance metrics like Manhattan distance (L1), Euclidean distance (L2), Cosine similarity, Bhattacharyya distance, Chebyshev distance, etc.
*   Next, the distance values are sorted either in descending or ascending order and top or lower k-nearest neighbors are determined.
*   The labels of the k-nearest neighbors are gathered, and a majority vote or a weighted vote is used for classifying the new data point. The new data point is assigned a class label based on a certain data point that has the highest score out of all the stored data points.
*   Finally, the predicted class for the new instance is returned.

The prediction can be of two types: either classification in which a class label is assigned to a new data point or regression wherein a value is assigned to the new data point. Unlike classification, in regression, the mean of all the k-nearest neighbors is assigned to the new data point.

**Drawbacks of KNN:** Firstly, complexity in searching the nearest neighbor for each new data point. Secondly, determining the value of `k` sometimes becomes a tedious task. Finally, it is also not clear which type of distance metric one should use while computing the nearest neighbors.

Enough of theory right? So, let's load, analyze and understand the data that you will be using in today's small tutorial.

## Loading the Iris Data

Iris data set consists of 150 samples having three classes namely Iris-Setosa, Iris-Versicolor, and Iris-Virginica. Four features/attributes contribute to uniquely identifying as one of the three classes are sepal-length, sepal-width, petal-length and petal-width.

Feel free to use some other public dataset or your private dataset.

Sklearn is a ML python library that is widely used for data-science related tasks. It features various classification, regression and clustering algorithms including support vector machines, random forests, gradient boosting, k-means, KNN, etc. Under sklearn you have a library called `datasets` in which you have multiple datasets that can be used for different tasks including the Iris dataset; all these datasets can be loaded out of the box. It is pretty intuitive and straightforward. So, let's quickly load the iris dataset.

```python
from sklearn.datasets import load_iris
```

`load_iris` has both the data and the class labels for each sample. Let's quickly extract all of it.

```python
data = load_iris().data
```

`data` variable will be a numpy array of shape `(150,4)` having 150 samples each having four different attributes. Each class has 50 samples each.

```python
data.shape
# (150, 4)
```

Let's extract the class labels.

```python
labels = load_iris().target
```

```python
labels.shape
# (150,)
```

Next, you have to combine the data and the class labels, and for that, you will use an excellent python library called NumPy.

```python
import numpy as np
```

Since `data` is a 2-d array, you will have to reshape the `labels` also to a 2-d array.

```python
labels = np.reshape(labels, (150, 1))
```

Now, you will use the `concatenate` function available in the numpy library, and you will use `axis=-1` which will concatenate based on the second dimension.

```python
data = np.concatenate([data, labels], axis=-1)
```

```python
data.shape
# (150, 5)
```

Next, you will import python's data analysis library called pandas which is useful when you want to arrange your data in a tabular fashion and perform some operations and manipulations on the data.

In today's tutorial, you will use pandas quite extensively.

![Dataframe creation](Images/image00244.gif)

Now, you have the dataset data frame that has both data & the class labels that you need!

Before you dive any further, remember that the `labels` variable has class labels as numeric values, but you will convert the numeric values as the flower names or species.

For doing this, you will select only the class column and replace each of the three numeric values with the corresponding species. You will use `inplace=True` which will modify the data frame `dataset`.

```python
dataset['species'].replace(0, 'Iris-setosa', inplace=True)
dataset['species'].replace(1, 'Iris-versicolor', inplace=True)
dataset['species'].replace(2, 'Iris-virginica', inplace=True)
```

Let us print the first five rows of the dataset and see what it looks like!

![Dataset head](Images/image00245.gif)

## Analyze Your Data

Let's quickly find out how all the three flowers look like when visualized and how different they are from each other not just in numbers but also in real!

![Flower visualization](Images/image00246.jpeg)

([Source](https://www.datacamp.com/community/tutorials/machine-learning-in-r#learning))

Let's visualize the data that you loaded above using a scatterplot to find out how much one variable is affected by the other variable or let's say how much correlation is between the two variables.

You will use the matplotlib library to visualize the data using a scatterplot.

```python
import matplotlib.pyplot as plt
```

Note: Are you keen on learning different ways of visualizing the data in python? Then check out any tutorial about data visualization and also study the code snippet below.

![Visualization code snippet](Images/image00247.gif)

![Scatterplot output](Images/image00248.jpeg)
