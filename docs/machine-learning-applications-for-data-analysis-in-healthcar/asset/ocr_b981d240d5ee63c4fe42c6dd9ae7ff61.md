The bilateral filter calculates the space and intensity distance between the center pixel and the surrounding pixels. Bigger disparities in pixel values are given less weight when calculating intensity distance. Pixels closer together are weighted more in the Euclidean distance calculation. Multiplying the intensity and distance weights yields a weighted average of nearby pixel weighs smooth. Pixel outputs are weighted averages of surrounding pixels. Similar-intensity pixels nearby weighted more (Figure 13.4).

![](bbox=[0.32, 0.28, 0.67, 0.52])

FIGURE 13.4 Bilateral filter.

Overall, the bilateral filter is used in image processing applications such as denoising, texture removal, and picture enhancement. It smoothens pictures while keeping edges and other high-frequency details.

# 13.4.4.3 FUZZY C-MEAN SEGMENTATION

Image segmentation often uses the unsupervised fuzzy c-mean segmentation (FCM) clustering algorithm. Data points can belong to several clusters with varying degrees of affiliation using the FCM method. FCM can partition images using pixel values. Each pixel’s membership value reflects its cluster affiliation.

The algorithm updates the cluster centroids and membership values iteratively until convergence, having the aim of lowering the distance between the data points and the cluster centroids. FCM is capable of dealing with visual ambiguity and overlap, making it appropriate for picture segmentation.