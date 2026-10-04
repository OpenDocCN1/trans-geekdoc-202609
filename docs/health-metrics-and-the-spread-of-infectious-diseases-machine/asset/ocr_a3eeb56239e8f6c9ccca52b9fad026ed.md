# B

![](bbox=[0.278, 0.115, 0.722, 0.243])

**Figure 12.9** Representation of Euclidean Distance between Points A and B

```
# helper function for calculating euclidian distance metric
eclidean_distance <- function(longitude, latitude,
  long_com, lat_com) {
  long_distances <- (longitude - long_com[i])^2
  lat_distances <- lat_com[1])^2
  return((long_distances + lat_distances) * 0.5)
}
```

There are other type of distance metrics that can be used, such as the **Manhattan** distance, which calculates the sum of the absolute differences between the coordinates of two points, the **Mahalanobis** distance, which considers the correlation between the variables, and the **Chebyshev** distance, which calculates the maximum difference between the coordinates of two points.

# 12.5.2 Spatial Autocorrelation

Spatial autocorrelation refers to the principle that spatial data points close to each other are more likely to have similar values than those apart. By analysing the spatial distribution of cases, areas with high spatial indicated clusters where infections spread is particularly intense.

Using tools like **Moran's I** and its variants, infection hotspots can be detected by identifying areas where high case cluster together. To check the presence of spatial autocorrelation the **Global Moran's** law is used:

> $I = \frac{N \sum_{i=1}^{N} \sum_{j=1}^{N} w_{ij}(x_i - \bar{x})(x_j - \bar{x})}{W \sum_{i=1}^{N} (x_i - \bar{x})^2}$$ (12.2)

Where $x_i$ and $x_j$ are the values of the variable of interest at location $i$ and $j$, $ar{x}$ is the mean value and $N$ indicates the number of spatial units, and $w_{ij}$ are the spatial weight between locations.

I measures the degree to which infection is clustered, dispersed or randomly distributed, with values ranging from -1 indicating perfect dispersion to +1 indicating perfect spatial clustering. A value of 0 indicates no spatial autocorrelation, suggesting a random spatial pattern.