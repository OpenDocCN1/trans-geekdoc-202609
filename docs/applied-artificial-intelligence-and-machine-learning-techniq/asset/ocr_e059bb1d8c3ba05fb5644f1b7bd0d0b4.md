![](bbox=[0.14, 0.08, 0.86, 0.33])

FIGURE 12.2 SVM label prediction and classification process.

![](bbox=[0.14, 0.39, 0.86, 0.58])

FIGURE 12.3 Algorithm steps for SVM classification, considered in proposed study.

# 12.4.2 K-Nearest Neighbours Algorithm (KNN)

This is a supervised learning technique that classifies input according to the categorisation of its neighbours. Since the KNN algorithm uses distance as its basis for classification, two points are more similar the closer they are to one another. The Euclidean and Manhattan methods are two distinct ways to find the distance between two places. A new point’s properties are labelled according to the points that are adjacent to it, or its neighbours. The KNN algorithm is one of the popular machine learning algorithm, and the algorithm steps are given in Table 12.1.

Prior to classification, the new element is placed in the category where the majority of the shared features occur by comparing its similarity measure to that of the neighbouring K elements. K, the total number of neighbours in this algorithm, is a positive integer. This number is calculated using the formula for Euclidean distance.

$d = \sqrt{[(x_2 - x_1)^2 + (y_2 - y_1)^2]}$ (12.4)