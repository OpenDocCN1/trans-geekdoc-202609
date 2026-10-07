
## 2 example

Iris dataset in two dimensions (the weight) can be plotted as a point. But if we want to show out variation, PCA finds a new coordinate system where each point has a new (x, y) axis.

Drag the points around the visualization to see PCA coordinate system axes.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_324_0.png)

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_324_1.png)

PCA is used for reducing dimensions; it's composed of the x-values and another of the y-values.

If we're only going to see the data, the principal component with most variance is enough. The second continues leads to the variation in the data set.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_324_2.png)

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_324_3.png)

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_324_4.png)

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_324_5.png)

## 3 example

With three dimensions, PCA is more useful because it's hard to see through a cluster of data. In this example, the original data are three-dimensional. PCA rotates the axes to fix the first to the test angle.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_324_6.png)

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_324_7.png)

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_324_4.png)

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_324_5.png)

## NOTES:

PCA is not linear regression although it may look like it is, rather than attempting to predict the values. PCA is attempting to learn the relationship between x and y values quantified by a list of principal axes.

- learn the relationship between x and y values
- Find a list of principal axes

To understand PCA, the best ways are to look at the visualizations (the link is given above).

PCA has a weakness: it is highly affected by outliers in the data, but PCA is considered to be one of the most used and extremely popular.

## 10.4 PCA in Python: part 1 - Problem description

| Feature Selection | Feature Extraction |
|---|---|
| Backward Elimination | PCA |
| Forward Selection | LDA |
| Bidirectional Elimination | Kernel PCA |
| Score Comparison | |

In dimensionality reduction there are techniques: feature selection and feature extraction.

> We used feature selection in Chapter 2: Machine Learning, we implemented the backward elimination method to select the most relevant features of our feature-matrix.

Now we are using feature extraction techniques of dimensionality reduction, and PCA: principal component analysis is of one

From the independent variables of our data, PCA extracts p ≤ independent variables that explain the most variance of the dataset, regardless of the dependent variable.

- i.e. PCA extracts a smaller number of independent variables that are going to be new independent variables (like new dimensions) and these new independent variables explain the most variance of your data set.

Notice that, we are not considering the dependent variable (DV) in the PCA model, for PCA considered as an unsupervised model.

Recall, in Chapter 2 and Chapter 3 we worked with one or two independent variables, because we needed a graphic visualization of our results.

PCA will help us to visualize the results: PCA dimensionality reduction technique, we will reduce the dimension of our dataset by relevant independent variables that explain the most variance of our dataset.

Since we can reduce number of independent variables, we can end up with two or three independent variables and therefore visualize the results.

## Problem description: we apply PCA to Logistic-Regression model that we will build in Chapter 3: Classification. We are applying PCA to a classification problem.

Following a very famous dataset, well-known in the machine learning literature and that you can find on the UCI Machine Learning Repository.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_325_0.png)

Wine Data Set
Dataset tabular: Data Set Description
Abstract: Using chemical analysis to determine the origin of wines.

| Index | Malic Acid | Ash | Ash Alkalinity | Magnesium | Total_Phenols | Flavonoids | Nonflavanoid_Phenols | Proanthocyanins | Color Intensity | Hue | Customer_Segment |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0 | 14.2 | 1.7 | 14.3 | 117 | 2.6 | 1.0 | 1.75 | 0.26 | 0.28 | 5.18 | 8.06 | 1.094 |
| 1 | 17.2 | 2.1 | 11.2 | 100 | 4.5 | 2.75 | 1.26 | 0.28 | 0.31 | 4.38 | 3.85 | 1.04 | 1 |
| 2 | 13.6 | 2.7 | 14.6 | 101 | 6.2 | 0.9 | 1.2 | 0.34 | 0.25 | 5.98 | 5.03 | 1.17 | 1 |
| 3 | 14.7 | 1.9 | 15.5 | 116 | 1.3 | 0.85 | 0.49 | 0.24 | 0.21 | 2.18 | 7.5 | 0.85 | 1 |
| 4 | 13.9 | 2.2 | 15.7 | 118 | 2.5 | 1.68 | 1.13 | 0.39 | 0.32 | 4.02 | 4.34 | 0.73 | 1 |
| 5 | 11.8 | 2.1 | 11.8 | 106 | 3.8 | 2.11 | 1.42 | 0.53 | 0.37 | 3.65 | 2.05 | 0.9 | 1 |
| 6 | 14.8 | 2.4 | 14.5 | 97 | 7.6 | 2.5 | 0.92 | 0.31 | 0.19 | 5.25 | 1.52 | 1.08 | 2 |
| 7 | 14.6 | 2.4 | 14.7 | 96 | 7.5 | 2.5 | 0.92 | 0.31 | 0.19 | 5.25 | 1.52 | 1.08 | 2 |
| 8 | 17.2 | 2.1 | 11.2 | 100 | 4.5 | 2.75 | 1.26 | 0.28 | 0.31 | 4.38 | 3.85 | 1.04 | 1 |
| 9 | 13.6 | 2.7 | 14.6 | 101 | 6.2 | 0.9 | 1.2 | 0.34 | 0.25 | 5.98 | 5.03 | 1.17 | 1 |
| 10 | 14.7 | 1.9 | 15.5 | 116 | 1.3 | 0.85 | 0.49 | 0.24 | 0.21 | 2.18 | 7.5 | 0.85 | 1 |
| 11 | 13.9 | 2.2 | 15.7 | 118 | 2.5 | 1.68 | 1.13 | 0.39 | 0.32 | 4.02 | 4.34 | 0.73 | 1 |
| 12 | 11.8 | 2.1 | 11.8 | 106 | 3.8 | 2.11 | 1.42 | 0.53 | 0.37 | 3.65 | 2.05 | 0.9 | 1 |
| 13 | 14.8 | 2.4 | 14.5 | 97 | 7.6 | 2.5 | 0.92 | 0.31 | 0.19 | 5.25 | 1.52 | 1.08 | 2 |

## 10.5 PCA in Python: part 2 - Problem description

Following a very famous dataset, well-known in the machine learning literature and that you can find on the UCI Machine Learning Repository.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_325_0.png)

## Problem description: we apply PCA to Logistic-Regression model that we will build in Chapter 3: Classification. We are applying PCA to a classification problem. (Wait, the OCR text provided in the prompt seems to have repeated or merged sections in the end. I will follow the logical flow provided).

