![](bbox=[0.176, 0.098, 0.892, 0.215])

**Figure 6:** Clustering-based approaches.

algorithm for Gaussian mixture distribution. GMM is especially useful for cases where the underlying intensity and, therefore, image intensity distributions are overlapping and the shapes of these distributions are different. This summary allows for what was known as the soft clustering; instead of assigning each pixel a specific cluster it gives a probability of being a cluster.

# 3.4.3 Clustering fuzzy *c*-means (FCM)

The last clustering algorithm under analysis is fuzzy *c*-means (FCM), which is an extension of the *k*-means algorithm in the direction of fuzzy logic. In FCM, each pixel can belong to as many clusters as the actual number of clusters as well as possess membership values that differentiate between the significant levels of classification. This approach was helpful for division of images where the boundary between segments was quite difficult to determine and if there are areas where segments overlap, this surely helps for better representation of the pixels. A pixel intensity weighted by membership degrees enhances a cluster center update process and replaces the conventional *k*-means update process.

# 3.4.4 Mean shift clustering

A type of clustering referred to as mean shift clustering searches for modes of data distribution to produce clusters. It becomes evident due to the fact that this algorithm tends to move the data points around in an oscillatory manner towards the center of the window, which defines a density-based cluster. When the background picture density and segmentation shapes are arbitrary, mean shift was quite effective. Since the number of clusters was not forced beforehand, it can be used in pictures with numerous clusters. The results are significantly affected by the bandwidth parameter through which the window size was determined.