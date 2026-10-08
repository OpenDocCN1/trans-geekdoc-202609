
Wang, J., Y. Song, T. Leung, C. Rosenberg, J. Wang, J. Philbin, B. Chen, and Y. Wu. 2014. Learning fine-grained image similarity with deep ranking. In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, San Juan, Rico, pp. 1386–1393.

Zhang, H., W, Ni, M. Zhao, Y. Liu, and Y. Yang. 2014. A hybrid recommendation approach for network teaching resources based on knowledge-tree. In Proceedings of the 33rd Chinese Control Conference. IEEE, Nanjing, China, pp. 3450–3455.

Zhao, W., R. Wu, and H. Liu. 2016. Paper recommendation based on the knowledge gap between a researcher’s background knowledge and research target. Information Processing & Management 52(5):976–988.

![](img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_122_0.png)

# 6 Forecasting Air Quality in India through an Ensemble Clustering Technique

J. Anuradha, S. Vandhana, and Sasya I. Reddi

- 6.1 Introduction............................................................................... 113
- 6.2 Related Works............................................................................... 115
- 6.2.1 Air Quality Prediction............................................................... 115
- 6.2.2 Ensemble Modeling...................................................................... 116
- 6.2.2.1 Variants of Ensemble Models.................................................. 118
- 6.2.3 Ensemble Clustering.................................................................... 119
- 6.3 Dataset Descriptions...................................................................... 120
- 6.4 Methodology.................................................................................. 120
- 6.4.1 Final Cluster Labeling......................................................................... 125
- 6.4.2 METIS Function....................................................................... 126
- 6.4.2.1 METIS Algorithm...................................................................... 126
- 6.4.3 Phases.................................................................................... 128
- 6.4.4 Advantages............................................................................... 128
- 6.5 Experimental Results..................................................................... 130
- 6.5.1 Silhouette Coefficient.................................................................. 130
- 6.5.2 Calinski-Harabasz Index............................................................... 131
- 6.5.3 Davies-Bouldin Index.................................................................. 132
- 6.6 Conclusion................................................................................ 133
References........................................................................................... 134

# 6.1 INTRODUCTION

Air pollution has been a major cause of various diseases in recent years. The quality of air (outdoor air quality) manifested worldwide deaths of 4.2 million in the year 2016. Prolonged exposure to particulate matter (PM) of diameter less than 2.5 microns can prove to be fatal (WHO 2018). It causes cardiovascular and respiratory diseases and cancers. It is one of the incremental problems affecting all countries in the world.

Rather than affecting human health directly, air pollutants can cause long-term damage to the environment which results in climate change and an indirect threat to health and well-being. Besides exposure to PM, health can be drastically affected by exposure to ozone (O3) as well. One of the main factors of asthma morbidity and mortality is ozone, which can cause reduced lung function, lung cancer, and breathing problems. The air pollutants NOx and PM2.5 have several correlated activities shown by Dai, Luo, Qin, and Peng (2014). One of the main components of nitrate aerosols is NO2. Epidemiological studies have shown NO2 to reduced lung function. In a few cities in North America and Europe, the concentration levels of NO2 are being monitored regularly. SO2 has been known to aggravate chronic bronchitis and asthma, make people more vulnerable to respiratory tract infections, and respiratory tract inflammation and eye irritation. On days when the concentration levels of SO2 are higher, the number of cases of cardiac diseases or mortality is higher, as stated by the WHO (2018).

The National Wildlife Federation of the USA in the late 1960s developed the Environmental Quality Index (EQI), of which the Air Quality plays an integral part. Many researchers have concentrated on air quality and applied the methods of classification, clustering, prediction, and forecasting for the well-being of humans. Upon clustering or grouping, one can find the exact shape of data or patterns that it is falling in and can we take the control measures that reduce the effect on human health in the future.

Various data research involves clustering as a key step, as it aims at separating information into clusters or classes on the basis of a certain measure of similarity. The final objective is to place the data points in some cluster which are similar to each other and that differ in separate clusters. It is well that different clustering methods when applied to the same set of data can discover different patterns. This is because, due to the optimization of different criteria, each algorithm has its own bias. Another challenge of clustering is related to the validation of the results when ground truth is not available.

Clustering ensembles have appeared in recent years as a strategy for solving some the clustering problems, as shown by Ghosh and Acharya (2011) and Strehl and Ghosh (2012). An ensemble clustering method is described by its two components:

- Generation of diverse partitions;
- Combining partitions into a final clustering using a consensus function.

The same algorithm with different initializations or the same data with bootstrap samples or algorithms make a clustering ensemble. A clustering ensemble offers a solution to various challenges that are inherent to clustering. By using consensus through several clustering tests, more reliable and robust solutions can be provided. Different samples may induce variance which can lead to spurious structures, which also merge due to various biases and can be averaged out by the consensus function.

A subspace clustering can also be viewed as a weighted cluster array, where each cluster represents the importance of its features using a weight vector. In the subspace clustering ensemble, the clusters and the weight vectors given by the base subspace clusters are used in the consensus function. The final consensus clustering Forecasting Air Quality in India can be improved by evaluating the relevance of the base clustering (and the assignments of weights accordingly) as shown by Li, Ding, and Jordan (2007). To the best of our knowledge, Nock and Nielsen (2006) were the first to explore how to use how to use.
