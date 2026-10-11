
# Exercise 3.2

Replace the missing values in the `deck` column of the Titanic dataset with the most frequently occurring categories in that column. Plot a bar plot for the updated `deck` column.

**Solution:**
![](Image00502.jpg)

# Exercise 4.1

## Question 1

Which of the following feature types should you retain in the dataset?

1. Features with low Variance
2. Features with high Variance

| C.  |
| --- |
| D.  |

**Answer:** D

## Question 2

Which of the following features should you remove from the dataset?

1. Features with high mutual correlation
2. Features with low mutual correlation

| C.  |
| --- |
| D.  |

**Answer:** A

## Question 3

Which of the following feature selection method does not depend upon the output label?

1. Feature selection based on Model performance
2. Feature selection based on recursive elimination

| C.  |
| --- |
| D.  |

**Answer:** C

# Exercise 4.2

Using the `winequalit-white` dataset from the `Dataset and Source Codes` folder, apply the recursive elimination technique for feature selection.

**Solution:**
![](Image00503.jpg)

# Exercise 5.1

## Question 1

Which of the following is an example of a regression output?

1. True
2. Red

| C.  |
| --- |
| D.  |

**Answer:** C

## Question 2

Which of the following algorithm is a lazy algorithm?

1. Random Forest
2. KNN

| C.  |
| --- |
| D.  |

**Answer:** B

## Question 3

Which of the following algorithm is not a regression metric?

1. Accuracy
2. Recall

| C.  |
| --- |
| D.  |

**Answer:** D

# Exercise 5.2

Using the `Diamonds` dataset from the Seaborn library, train a regression algorithm of your choice, which predicts the price of the diamond. Perform all the preprocessing steps.

**Solution:**
![](Image00504.jpg)

# Exercise 6.1

## Question 1

Which of the following is not an example of classification outputs?

1. True
2. Red

| C.  |
| --- |
| D.  |

**Answer:** D

## Question 2

Which of the following metrics is used for unbalanced classification datasets?

1. Accuracy
2. F1

| C.  |
| --- |
| D.  |

**Answer:** C

## Question 3

Which of the following function is used to convert categorical values to one-hot encoded numerical values?

1. `pd.get_onehot()`
2. `pd.get_dummies()`

| C.  |
| --- |
| D.  |

**Answer:** B

# Exercise 6.2

Using the `iris` dataset from the Seaborn library, train a classification algorithm of your choice, which predicts the specie of the iris plant. Perform all the preprocessing steps.

**Solution:**
![](Image00505.jpg)

# Exercise 7.1

## Question 1

Which of the following is a supervised machine learning algorithm?

1. K-Means Clustering
2. Hierarchical Clustering

| C.  |
| --- |
| D.  |

**Answer:** D

## Question 2

In K-Means clustering, the inertia tells us?

1. the distance between data points within a cluster
2. output labels for the data points

| C.  |
| --- |
| D.  |

**Answer:** C

## Question 3

In hierarchical clustering, in the case of vertical dendrograms, the number of clusters is equal to the number of ______ lines that the ______ line passes through?

1. horizontal, vertical
2. vertical, horizontal

| C.  |
| --- |
| D.  |

**Answer:** B

# Exercise 7.2

Apply K-Means clustering on the `banknote.csv` dataset available in the Datasets folder in this GitHub repository (`https://bit.ly/3nhAJBi`). Find the optimal number of clusters and then print the clustered dataset. The following script imports the dataset and prints the first five rows of the dataset.

![](Image00506.jpg)

# Exercise 8.1

## Question 1

Which of the following are the benefits of dimensionality reduction?

1. Data Visualization
2. Faster training time for statistical algorithms

| C.  |
| --- |
| D.  |

**Answer:** C

## Question 2

In PCA, dimensionality reduction depends upon the:

1. Features set only
2. Labels set only

| C.  |
| --- |
| D.  |

**Answer:** A

## Question 3

LDA is a ______ dimensionality reduction technique

1. Unsupervised
2. Semi-Supervised

| C.  |
| --- |
| D.  |

**Answer:** C

# Exercise 8.2

Apply principal component analysis for dimensionality reduction on the `customer_churn.csv` dataset from the Datasets folder in this GitHub repository (`https://bit.ly/3nhAJBi`). Print the accuracy using two principal components. Also, plot the results on a test set using the two principal components.

**Solution:**
![](Image00507.jpg)
![](Image00508.jpg)
![](Image00509.jpg)

# Exercise 9.1

## Question 1

With grid search, you can ______

1. Test all parameters for a model by default
2. Test only lists of specified parameters

| C.  |
| --- |
| D.  |

**Answer:** B

## Question 2

Learning curves can be used to study the:

1. Bias of a trained algorithm
2. Variance of a trained algorithm

| C.  |
| --- |
| D.  |

**Answer:** C

## Question 3

Which pickle method can be used to save a trained machine learning model:

1. `save()`
2. `register()`

| C.  |
| --- |
| D.  |

**Answer:** D

# Exercise 9.2

Use the Grid Search to find the parameters of the `RandomForestClassifier` algorithm, which return the highest classification accuracy for classifying the `banknote.csv` dataset:

![](Image00510.jpg)

**Solution:**
![](Image00511.jpg)
![](Image00512.jpg)

# Exercise 10.1

## Question 1

Which attribute of the `TfidfVectorizer` vectorizer is used to define the minimum word count?

1. `min_word`
2. `min_count`

| C.  |
| --- |
| D.  |

**Answer:** C

## Question 2

Which method of the `RandomForestClassifier` object is used to train the algorithm on the input data?

1. `train()`
2. `fit()`

| C.  |
| --- |
| D.  |

**Answer:** B

## Question 3

Sentimental analysis with `RandomForestClassifier` is a type of ______ learning problem.

1. Supervised
2. Unsupervised

| C.  |
| --- |
| D.  |

**Answer:** A

# Exercise 10.2

Import the `spam.csv` file from the resources folder. The dataset contains ham and spam text messages. Write a Python application that uses Scikit-Learn to classify ham and spam messages in the dataset. Column `v1` contains a text label, while column `v2` contains the text of the message.

**Solution:**
![](Image00513.jpg)
![](Image00514.jpg)

# Exercise 11.1

## Question 1

A colored image has ______ channels:

1. 1
2. 2

| C.  |
| --- |
| D.  |

**Answer:** C

## Question 2

You need to convert an image into a ______ dimensional array before you can use Scikit-learn to train models on image data?

1. 1
2. 2

| C.  |
| --- |
| D.  |

**Answer:** A

## Question 3

To convert a one-dimensional numpy array into a two-dimensional array or matrix, which method can be used?

1. `np.tomatrix()`
2. `pd.convert2d`

| C.  |
| --- |
| D.  |

**Answer:** C

# Exercise 11.2

Divide the following image dataset into 80 percent training and 20 percent test sets. Train the model on the training set and make predictions on the test set. Print the accuracy and confusion matrix for the model performance.

![](Image00515.jpg)

**Solution:**
![](Image00516.jpg)
![](Image00517.jpg)
