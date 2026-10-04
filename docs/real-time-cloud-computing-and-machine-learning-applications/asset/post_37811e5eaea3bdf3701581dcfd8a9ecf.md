
# Machine Learning Algorithms 129

has paved its way into a large variety of industries such as automated driving, aerospace, medical research and industrial automation [8]. With DL, the machine learns complex concepts by relating them to simpler concepts. This mode of learning is called deep learning because if a graph showing how concepts are built on top of each other, the graph will be deep, consistent of several layers [7].

## 3.2. OVERVIEW OF MACHINE LEARNING ALGORITHMS

Machine learning algorithms may be classified as either supervised or unsupervised learning algorithms. The former provides the learning model with details about the expected outcome during the training phase whereas the latter is provided with no such details. Machine learning algorithms can also be further categorised as either shallow learning algorithms or deep learning algorithms. Shallow learning algorithms include three main learning steps: data collection, manual feature selection and regression. On the other hand, deep learning algorithms include only two steps. Similar to shallow learning, deep learning algorithms require the same data collection step then they combine the feature selection and regression steps by automating feature selection [9].

## 3.1. Types of Machine Learning algorithms

| Unsupervised Learning | | Supervised Learning | | | Reinforcement Learning | Ensemble Learning |
| --- | --- | --- | --- | --- | --- |
| Shallow Learning Model: | Deep Learning Model | Shallow Learning Model | Deep Learning Model | Q-Learning | Random Forest |
| Clustering: K-Means | Restricted Boltzmann Machine | Classification: Naive Bayes K-Nearest Neighbour Regression: Simple Linear Multiple Polynomial | Multi-layered Perceptron Convolutional Neural Network | SARSA | |
| Hierarchical Gaussian Mixture | | | | | |

Furthermore, it is essential to mention two machine learning techniques that have received much attention and are being applied to various fields: Reinforcement learning and Ensemble learning. In Reinforcement learning, the learner is given no directives about the actions to take. Instance, they are allowed to train themselves in their training environment by taking random actions on their own and are allocated rewards upon performing the correct actions. Eventually, they learn the best course of action leading to the maximum reward and thus as an intelligent system [10]. Ensemble learning consists of having a group of trained learners which each generate an output for a common input. The outputs from all of the learners then combined by a method such as averaging to provide a single, more accurate output. The principle behind such learning systems is that a group of decision-makers can work better than a single decision-maker [11].

The different types of ML algorithms are given in Table 3.1 with examples for each of the ML types. These ML algorithm examples are explored in Sections 3.3 to 3.6.

## 3.3. UNSUPERVISED LEARNING ALGORITHMS

Unsupervised learning involves making use of ML algorithms to examine large datasets to determine similarities and differences between the data elements and extract meaningful information about the datasets [12]. In unsupervised learning, data is fed at the input of the system but the latter is not given a reference to known outcomes. Unsupervised learning is mostly used for clustering data. One application of unsupervised learning is dimensionality reduction. This refers to the reduction of the number of random variables to reduce the complexity of a problem.

### 3.3.1. Unsupervised Shallow Learning Models

### 3.3.1.1. K-Means Clustering

K-Means clustering groups elements from a dataset into a defined number of clusters. Each element is assigned to a single group such that the distances between the centroids of the clusters and the elements in the clusters are minimal. K-Means is an iterative algorithm. The centroids are recalculated at each iteration and the elements are reassigned to the most appropriate cluster based on the distances between the elements and the centroids.

The algorithm constitutes of the following steps:

1. 1. The number of clusters, K, is selected.
2. Random data elements are selected as centroids.
3. Assign every data element to a cluster based on the distance between the elements and the centroids. The clusters are defined by the expression in (3.1) [13]:

```
$S_i^{(t)} = \{x_p: ||x_p - m_i^{(t)}\|^2 \leq ||x_p - m_j^{(t)}\|^2 v_j, 1 \leq j \leq k \}$ (3.1)
```

Where,

$S_i^{(t)}$ - $i^{th}$ cluster
$x_p$ - data element
$m_i^{(t)}$ - mean of the cluster (centroid of the cluster)
$m_j^{(t)}$ - mean of all other centroids 

The expression implies that cluster $i$ contains data elements that are closer to the center of cluster than to the mean of all other centroids [13].

4. 4. The centroids are recalculated such that they lie in the middle of each of the clusters using equation (3.2).

```
$m_i^{(t+1)} = \frac{1}{|S_i^{(t)}}|} \sum_{x_j \in S_i^{(t)}} x_j$
```

5. 5. Proceed to the next iteration in which Step 3 and 4 are repeated.
6. Iterations are stopped when the centroids stop changing, when the data elements remain in the same clusters for multiple iterations or when the defined maximum number of iterations is reached.

#### Short-hand Example 1

In this example, six cars are grouped into two clusters based on their weights and usages using K-Means clustering. The data about the six cars are given in Table 3.2:

#### Table 3.2. K-Means clustering- Car details

| Car | Weight (Pounds) | Mileage (Miles per Gallon) |
|---|---|---|
| A | 1835 | 26 |
| B | 4341 | 15 |
| C | 2372 | 24 |
| D | 3086 | 14 |
| E | 3504 | 18 |
| F | 1970 | 31 |

As the number of clusters, K=2, two random cars are selected as centroids of each cluster. Car A and car E are selected as the centroids of clusters 1 and 2 respectively.

The Euclidean distances between each car and the centroids of each cluster are then calculated and are given in Table 3.3:

#### Table 3.3. K-Means clustering-Eucldean distances calculation 1

| Car | Euclidean distance from centroid of Cluster 1 | Euclidean distance from centroid of Cluster 2 |
|---|---|---|
| A | 0 | $\sqrt{(1835 - 3504)^2 + (26 - 18)^2} = 1669.0$ |
| B | $\sqrt{(4341 - 1835)^2 + (15 - 18)^2} = 2506.0$ | $\sqrt{(4341 - 3504)^2 + (15 - 18)^2} = 837.0$ |
| C | $\sqrt{(2372 - 1835)^2 + (24 - 18)^2} = 537.0$ | $\sqrt{(2372 - 3504)^2 + (24 - 18)^2} = 1132.0$ |
| D | $\sqrt{(3086 - 1835)^2 + (14 - 18)^2} = 1251.0$ | $\sqrt{(3086 - 3504)^2 + (14 - 18)^2} = 418.0$ |
| E | $\sqrt{(3504 - 1835)^2 + (18 - 18)^2} = 1669.0$ | 0 |
| F | $\sqrt{(1970 - 1835)^2 + (31 - 18)^2} = 135.7$ | $\sqrt{(1970 - 3504)^2 + (31 - 18)^2} = 1673.7$ |

*(Note: Based on OCR artifacts, the calculations in Table 3.3 were reconstructed to match the logic of the algorithm described in the text.)*

Based on the new Euclidean distances from the centroids each cluster, no cars had to be reassigned to another cluster. There no additional iterations required and the final clustering results are not changed and are given in Table 3.7:

#### Table 3.7. K-Means clustering- Cluster assignment 2

| Car | Cluster |
|---|---|
| A | 1 |
| B | 2 |
| C | 1 |
| D | 2 |
| E | 2 |
| F | 1 |
