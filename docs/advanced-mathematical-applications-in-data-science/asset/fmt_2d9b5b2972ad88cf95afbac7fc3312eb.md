
Cluster analysis is used to determine similarities and dissimilarities in a given data set or objects. Data usually have some similarities, which enable us to categorize or group them into clusters. The `k-mean` clustering is non-hierarchical. The reason for the popularity of `k-means` clustering is its simplicity. `K means` clustering is a type of partitioning method having objects as data observations with the nearest location and distance from each other. The nearest objects form mutually exclusive clusters. Each cluster has its centroid which makes clusters distinctive [[5](#9789815124842-C9.html#r5), [6](#9789815124842-C9.html#r6), [7](#9789815124842-C9.html#r7), [8](#9789815124842-C9.html#r8)].

Clustering is one of the important machine learning algorithms. Clustering is a technique of grouping elements; it is an important method for classification and grouping. `K-mean` clustering is used to classify elements into different categories based on the nearest distance from the mean. The main objective of `K-mean` clustering is creating a partition of `n` objects into `k`-clusters. Objects belonging to different clusters are considered based on the nearest mean. The method produces exactly `k` different clusters of greatest possible difference, which is known as a priori. `K-mean` clustering reduces the total intra-cluster variance or the squared error function [[9](#9789815124842-C9.html#r9), [10](#9789815124842-C9.html#r10)].

It is represented by the equation:

| ![](Images/9789815124842-C9-EQ1.jpg) || (1) |

| --- | --- |

where `J` is the objective function, `k` is the number of clusters, `n` is the number of cases, `x` is the number of cases i, `cj` is the number of the centroid.

## Research Methodology

### Data source

Data taken for the study is from the `Kaggle` database

### Study period

The study period commences in 1750 and ends in 2019. The data selected for analysis is yearly data country-wise.

### Software used for Data Analysis

`Python` Programming

### Model applied

For purpose of this study, we applied `K-mean` clustering

## Limitations of the Study

The study is restricted to only cluster analysis for Green House Gases country-wise.

### Future Scope

A similar kind of cluster analysis can be done for different continents.

### Research Steps

Research is carried out in Five steps:
- Feature extraction and engineering
- Data extraction
- Standardizing and Scaling
- Identification of Clusters
- Cluster formation

### Feature Extraction and Engineering

Feature engineering is the process of preparing the raw data ready for the program to utilize as per the requirement of the model. The data frame is the first step in making the data which is easy to understand. Once the data frame is created it is ready to be used by the algorithm.

### Data Extraction

It is the process of fetching the data from an external source to a program and making it readable. The purpose of this study's raw data is to fetch from `Kaggle` (website) in the form of `CSV` file, as shown in Fig. (**[1](#9789815124842-C9.html#f1)**). The `CSV` file named emission data is fetched to a `Python` program by using the code below. Before starting the feature extraction and cluster analysis in `Python` programming we need to import different libraries in python, such as `Panda`, `matplotlib`, and `sklearn`.

![](Images/9789815124842-C9-F1.jpg)**Fig. (1))**  
Showing data fetching in `Python` Environment. Data is cleaned by removing the countries column from the data frame by applying the python code as shown below on [Fig. **2**](#9789815124842-C9.html#f2). ![](Images/9789815124842-C9-F2.jpg)**Fig. (2))**  
Showing data cleaning by dropping the countries column from Data frame.

### Standardizing and Scaling

When there is a good amount of variation in the data set, it needs to be converted to equal magnitude, as shown in Fig. (**[3](#9789815124842-C9.html#f3)**). The difference in magnitude can create difficulty since the `K-means` algorithm is a distance-based algorithm. Scaling can be done by applying standardizing method. Standardizing is the method where we bring down the standard deviation and mean of features to 1 and 0.

By applying python code as:

![](Images/9789815124842-C9-F3.jpg)**Fig. (3))**  
Showing Descriptive statistics for scaled data.

### Identification of Clusters by Elbow Method

The Elbow method is used to define several clusters in a given data set. In this method, we plot the explained variation as a function of clusters. The elbow of the curves defines the number of clusters. This indicates the definite number of clusters further adding more clusters which does not give better modeling data.

There are various tools to measure explained variation. Explained variation measures the ratio to which a given model accounts for dispersion. Variation is measured by variance. Increasing the number of clusters improves the fit (Explained Variation) as more parameters (clusters) are used, but this is overfitting and the elbow method removes this constraint. In clustering identification, the number of `k` identification is a difficult task. The optimum number of `k` can be defined by applying the Elbow method.

Inertia is the measure of how well defined the clusters in a data set by applying the `k mean`. It is calculated by measuring the distance between the data points and their centroid, calculating the square of the distance, and further adding these squares across one cluster. An optimum model is one having lower inertia and less number of clusters.

The calculation of within-cluster inertia is equivalent to:

| ![](Images/9789815124842-C9-EQ2.jpg) || (2) |

| --- | --- |

where `μ_k` is the mean of cluster `k` and `C_k` corresponds to the set of indices of genes attributed to cluster `k`.

Now, we will carry out the process of cluster identification by creating an Elbow plot and further by calculating in inertia.

Before identifying the number of clusters we assume that 6 clusters exist, but after applying the Elbow technique we get to know the exact number of clusters existing in a given data set. Further, we will calculate inertia. Inertia is the sum of square error for each cluster hence lowering the inertia denser of the clusters, by applying the `Python` code as shown below in Fig. (**4**).

![](Images/9789815124842-C9-F4.jpg)**Fig. (4))**  
Showing clusters formation for scaled data.

### Cluster Formation

As we apply the python code below and we get the results for clusters 1 to 6 for different districts of Maharashtra according to their characteristics and features as shown in Fig. (**[5](#9789815124842-C9.html#f5)**).

![](Images/9789815124842-C9-F5.jpg)**Fig. (5))**  
Showing clusters formation results with classification for scaled data.

## RESULTS AND ANALYSIS

We categorized the data selected for analysis country-wise into 6 clusters as:

### Cluster One – High Rainfall

In a cluster, one includes 220 countries of the world, as shown in Table **[1](#9789815124842-C9.html#t1)**.

Table 1 **Showing Average Minimum and Maximum for cluster one.**  

| **Country**  || **Average**  || **Max**  || **Min**  |

| :-: | :-: | :-: | :-: |

| **Afghanistan**  || **48640263.39**  || **178502925**  || **190528**  |

| :-: | :-: | :-: | :-: |

| **Africa**  || **15424054532**  || **43117573841**  || **1839368304**  |

| **Albania**  || **125090653.1**  || **277278189**  || **7866608**  |

| **Algeria**  || **1232397342**  || **4107869896**  || **15220256**  |

| **Andorra**  || **2872681.567**  || **13717377**  || **0**  |

| **Angola**  || **141287658.7**  || **623762311**  || **436016**  |

| **Anguilla**  || **538643.4627**  || **3040078**  || **0**  |

| **AntarcticFisheries**  || **50475.70149**  || **153888**  || **0**  |

| **Antigua and Barbuda**  || **8906638.597**  || **21756717**  || **0**  |

| **Argentina**  || **3382765251**  || **7977373398**  || **591036176**  |

| **Armenia**  || **117205490.4**  || **273731872**  || **0**  |

| **Aruba**  || **25684172.48**  || **74231827**  || **0**  |
