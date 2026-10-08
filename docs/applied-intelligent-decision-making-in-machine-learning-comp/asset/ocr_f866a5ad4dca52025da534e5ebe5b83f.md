# Forecasting Air Quality in India

Year-wise data is consolidated and three clustering algorithms, namely hierarchical clustering, fuzzy C clustering, and K-means, are applied. For each set of data, the optimal number of clusters was determined to be two, using the elbow method. The overall procedure for weighted ensemble graph clustering is:

+   1. The air pollution dataset is loaded.
2. Data has to be pre-processed before applying the clustering techniques.
3. The first pre-processing step concerns the values for the chosen Air Quality Index (AQI) parameters (PM₂,₅, SO₂, O₃ and CO) which are taken and loaded in a data frame.
4. The outliers are identified and replaced with the mean value.
5. Similarly, the missing values in the data will be imputed with the mean value.
6. In the final pre-processing step, the data for the various regions in India are consolidated, based on the year.
7. The pre-processed data is then used to determine the optimum number of clusters for each set of year-wise data. The number of clusters selected for each dataset is given in Figure 6.4.

![](bbox=[0.135, 0.435, 0.858, 0.625])

(a) Hierarchical Clustering, 2016

(b) Hierarchical Clustering, 2017

![](bbox=[0.315, 0.685, 0.663, 0.865])

(c) Hierarchical Clustering, 2018

FIGURE 6.4 Optimal cluster plot of a base clustering algorithm.