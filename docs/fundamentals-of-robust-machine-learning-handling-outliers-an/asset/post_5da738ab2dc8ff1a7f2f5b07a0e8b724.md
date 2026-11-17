
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
from sklearn.cluster import DBSCAN
from sklearn.ensemble import IsolationForest
from scipy.stats import norm, multivariate_normal

## b) Generate the data with three clusters using a Gaussian mixture model.

```python
# Generate data using Gaussian mixture model
dataset = 1
m1 = [-4,3]
m2 = [7,7]
m3 = [1,7]
cov1 = [[1.5, 1], [1, 1.5]]
cov2 = [[2, -1], [-1, 2]]
cov3 = [[0.8,0.5],[0.5,0.8]]
np.random.seed(np.random.randint(100))
x = np.random.multivariate_normal(m1, \
    cov1, size=(150,))
y = np.random.multivariate_normal(m2, \
    cov2, size=(300,))
z = np.random.multivariate_normal(m3, \
    cov3, size=(120,))
trainx = np.concatenate((x, y, z), axis=0)
print('The dimensions of the trainx are: ', trainx.shape)
```

## c) Plot the raw data before anomaly detection.

```python
plt.figure(figsize=(4, 4))
plt.scatter(trainx[:, 0], trainx[:, 1], marker='.')
plt.axis('equal')
plt.xlabel('X-Axis', fontsize=16)
plt.ylabel('Y-Axis', fontsize=16)
plt.show()
```

## d) Insert four anomalies into the data and plot the results.

```python
# Insert anomalies to be detected
trainx[0] = [20, -1]
trainx[1] = [21, -1]
trainx[2] = [-5, 15]
trainx[3] = [15, 15]
plt.figure(figsize=(4, 4))
plt.scatter(trainx[:, 0], trainx[:, 1], marker='.')
plt.axis('equal')
plt.xlabel('X-Axis', fontsize=16)
plt.ylabel('Y-Axis', fontsize=16)
plt.show()
```

- e) Run DBSCAN and adjust the radius (eps) and the minimum number of samples (min_samples) until the results are correct.

```python
# DBSCAN code starts here
print("Running DBSCAN on dataset", dataset)
eps, MinPts = 4.5, 10
db = DBSCAN(eps=eps, min_samples=MinPts).fit(trainx)
outlierDB = db.labels_
cats = pd.Series(outlierDB).value_counts()
print("Number of anomalies found:", cats[-1])
if (cats[-1] > 4):
    print("Adjust eps and MinPts to improve results")
```

- f) Plot the results to determine if the four anomalies were found. If not, adjust (eps) and (min_samples) as needed.

```python
# Plot DBSCAN results
DBrows_with_anomalies = \
    np.where(db.labels_ == -1)[0]
xdblot = []
ydblot = []
for i in DBrows_with_anomalies:
    xdblot.append(trainx[i, 0])
    ydblot.append(trainx[i, 1])
plt.figure(figsize=(4, 4))
plt.scatter(trainx[:, 0], trainx[:, 1], \
    marker='.', color='lightgray')
plt.scatter(xdblot, ydblot, marker='.', \
    color='black')
print("DBSCAN found", cats[-1], "anomalies")
plt.title("DBSCAN Outliers Detected")
plt.show()
```

## 11.2 (Project) In this project, you will run Isolation Forest using the same synthetically created data with anomalies inserted manually as in the first project.

- a) Run Isolation Forest by setting the contamination parameter.

```python
# Isolation Forest code starts here
print("Running IF on dataset ", dataset)
threshold = 0.1
IF = IsolationForest(contamination=threshold)
IF.fit(trainx)
anomaly_score = IF.decision_function(trainx)
outlierIF = IF.predict(trainx)
rows_to_delete = np.where(outlierIF < 0)
count = 0
IFrows_with_anomalies = []
for i in range(len(outlierIF)):
    if outlierIF[i] == -1:
        count += 1
        IFrows_with_anomalies.append(i)
print("Number of anomalies found:", count)
if (count > 6):
    print("Adjust threshold to improve results")
```

- b) Plot the results and adjust the contamination parameter, if needed.

```python
# Plot IF results
xifplot = []
yifplot = []
for i in IFrows_with_anomalies:
    xifplot.append(trainx[i, 0])
    yifplot.append(trainx[i, 1])
plt.figure(figsize=(4, 4))
plt.scatter(trainx[:, 0], trainx[:, 1], marker='.', \
    color='lightgray')
plt.scatter(xifplot, yifplot, marker='.', \
    color='black')
plt.title("Isolation Forest Outliers Detected")
plt.show()
```

## 11.3 (Advanced Project) In this project, you will run a prototype version of MADmax using the same synthetically created data with anomalies inserted manually as in the previous projects. The code uses only k-medians and k-NN algorithms to find outliers. The k-NM improvements are not included in this version.

- a) To begin this project, you will need the k-medians code from Chapter 1 Problem 1.5(b). Enter that code into your notebook.

- b) Next, run the following code to generate mini-clusters.

```python
# Create mini-clusters for MADmax
m = 30
n = trainx.shape[0]
K = int(n / m)
print("Number of mini-clusters:", K)
cluster, cost, medians = KMedians(trainx, K)
```

### c) Next, compute the value of MADmax from the mini-clusters.

```python
# Find the value of MADmax
def MAD(x):
    return(np.median(np.abs(x - np.median(x))))
MADset = np.zeros(K)
for i in range(K):
    mini_cluster = trainx[cluster == i]
    distL2 = np.sqrt(((mini_cluster - \
    medians[i, :]) ** 2).sum(axis=1))
    mini_cluster_MAD = MAD(distL2)
    MADset[i] = mini_cluster_MAD
MADmax = np.max(MADset)
print('The value of MADmax is ', format(MADmax, '.3f'))
```

### d) Finally, enter the MADmax code to find and plot the outliers.

```python
# Prototype MADmax code: kMedians+k-NN (without k-NM)
print("Running MADmax on dataset ", dataset)
plt.figure(figsize=(4, 4))
plt.scatter(trainx[:, 0], trainx[:, 1], marker='.', \
    color='lightgray')
min_size = 5  # Deal with small mini-clusters
count_outliers = 0

kNN = 25     # internal parameter
Cfactor = 6.8 # internal parameter
Afactor = 11.0 # internal parameter

for i in range(K):
    mini_cluster = trainx[cluster == i]
    distL2 = np.sqrt(((mini_cluster - \
    medians[i, :]) ** 2).sum(axis=1))
    mini_cluster_size = mini_cluster.shape[0]
    for j in range(mini_cluster_size):
        if (distL2[j] > Cfactor * MADmax \
        or mini_cluster_size < min_size):
            out_distL1 = (np.abs(trainx - \
            mini_cluster[j, :])).sum(axis=1)
            sort_dist = np.sort(out_distL1)
            if (np.mean(sort_dist[1:kNN]) > \
            Afactor * MADmax):
                count_outliers += 1
                plt.scatter(mini_cluster[j, 0], \
                mini_cluster[j, 1], marker='.', \
                color='black')
print("Total outliers:", count_outliers)
plt.title('MADmax Anomalies Detected', fontsize=15)
plt.show()
```

- e) Use the following new data to rerun all three anomaly detection methods: DBSCAN, IF, and MADmax. Do not adjust the parameter values. Compare the results.

```python
dataset = 2
m1 = [0, 3]
m2 = [7, 7]
m3 = [3, 7]
cov1 = [[6, 2], [2, 6]]
cov2 = [[5, -1], [-1, 5]]
cov3 = [[7, 1.0], [1.0, 7]]
np.random.seed(np.random.randint(100))
x = np.random.multivariate_normal(m1, \
cov1, size=(150,))
y = np.random.multivariate_normal(m2, \
cov2, size=(300,))
z = np.random.multivariate_normal(m3, \
cov3, size=(120,))
trainx = np.concatenate((x, y, z), axis=0)
trainx[0] = [20, -1]
trainx[1] = [21, -1]
trainx[2] = [-5, 15]
trainx[3] = [15, 15]
print("Re-run DBSCAN, IF and MADmax")
```

- f) Use the following new data to rerun all three anomaly detection methods: DBSCAN, IF, and MADmax. Do not adjust the parameter values. Compare the results.

```python
dataset = 3
m1 = [3, 5]
m2 = [10, 10]
m3 = [15, 15]
cov1 = [[6, 3], [3, 3]]
cov2 = [[6, 3], [3, 3]]
cov3 = [[6, 3], [3, 3]]
np.random.seed(np.random.randint(100))
x = np.random.multivariate_normal(m1, \
cov1, size=(1200,))
y = np.random.multivariate_normal(m2, \
cov2, size=(1500,))
z = np.random.multivariate_normal(m3, \
cov3, size=(1200,))
trainx = np.concatenate((x, y, z), axis=0)
trainx[0] = [20, -1]
trainx[1] = [21, -1]
trainx[2] = [-5, 15]
trainx[3] = [15, 15]
print("Re-run DBSCAN, IF and MADMax")
```

## Reference

Aggarwal, C.C. (2017). Outlier Analysis, 2e. Springer.

## 12 Case Studies in Data Science

### 12.1 Introduction

In this chapter, we consider robust data science using the algorithms and procedures described in the previous chapters. The focus here is to compare the log-cosh (LC) methods with the traditional log-likelihood methods, namely least squares (LS) and cross-entropy (CE), using two well-known datasets. In particular, we compare the competing approaches on linear regression, logistic regression, and neural networks. Examples include the Boston Housing and Titanic datasets. Data science problems of model building, prediction, and feature importance are addressed in the context of datasets with outliers. In each case, an outlier-centric approach is taken to demonstrate the enormous advantages of conducting data science in this manner. In addition, future directions for work in this area are described, namely, time series analysis of climate change and explainable artificial intelligence (XAI).

### 12.2 Example: Boston Housing Dataset

The Boston Housing dataset was used throughout this book to evaluate and compare different forms of machine learning. The dataset itself has 506 observations with 13 explanatory variables that factor into the median home prices in the Boston area, circa 1970–1975. The response variable and the 13 explanatory variables were all defined in Chapter 6. It is of particular interest to us in this book because it is also known to have many outliers. Housing prices vary considerably in an area or region and therefore the median price is often quoted, rather than the average price or a specific price, to account for outliers. For the moment, assume that the actual number of outliers is unknown but their existence is known. The question is, how do we handle a dataset when we know it may have potentially harmful outliers?

Three data science tasks will be carried out using this dataset. The first is to perform exploratory data analysis (EDA) to understand the dataset in some detail. The second is to build an accurate, compact model for prediction purposes, as was the case for most of the problems in this book. With the model, it will be possible to predict the median price of any home in the region provided that the needed information in terms of the explanatory variables is given. The model will be generated using linear regression
