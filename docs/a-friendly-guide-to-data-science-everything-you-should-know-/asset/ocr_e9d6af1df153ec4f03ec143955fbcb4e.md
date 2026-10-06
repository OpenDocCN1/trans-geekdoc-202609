![](bbox=[0.12185, 0.12735, 0.87742, 0.45653])

**Figure 15-14.** Classifying two new points based on our "trained" k-NNs

k-NNs is technically a classifier, but an average can be taken among the point's nearest neighbors to be used in regression. In the case of the new points above, if the labels had been numeric values instead, we would just take the average of the three nearest points. This is pretty intuitive, too, and simple to implement. Usually, there's some work involved in finding the right k, but it works well in a lot of cases, especially with more than two features. To find the best k, you generally create a bunch of k-NNs with many different numbers and run the test on each to see which number best.

k-NNs isn't used as much as it used to be, but it's still powerful and simple when there aren't too many features. It's still used in many areas, including in financial market forecasting, some recommendation systems, and image processing.