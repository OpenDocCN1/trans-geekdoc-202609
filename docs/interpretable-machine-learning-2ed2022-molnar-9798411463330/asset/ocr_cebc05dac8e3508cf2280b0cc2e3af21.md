# CHAPTER 7 GLOBAL MODEL-AGNOSTIC METHODS

![](bbox=[0.168, 0.133, 0.735, 0.388])

7.13: PDPs for temperature, humidity, and wind speed. Compared to the ALE plots, the PDPs show a smaller decrease in predicted number of bikes for high temperature or high humidity. The PDP uses all data instances to calculate the effect of high temperatures, even if they are, for example, instances with the season 'winter'. The ALE plots are more reliable.

# 7.2.5 Advantages

ALE plots are unbiased, means they still work when features are correlated. Partial dependence plots fail in this scenario because they marginalize over unlikely or even physically impossible combinations of feature values.

ALE plots are faster to compute than PDPs and scale with O(n), since the largest possible number of intervals is the number of instances with one interval per instance. The PDP requires n times the number of grid points estimations. For 20 grid points, PDPs require 20 times more predictions than the worst case ALE plot where as many intervals as instances are used.

The interpretation of ALE plots is clear. On a given value, the relative effect of changing the feature on the prediction can be read from the ALE plot. ALE plots are centered at zero. This makes their interpretation nice, because the value at each point of the ALE curve is the difference to the mean prediction. The 2D ALE plot only shows the interaction: If two features do not interact, the plot shows nothing.

The entire prediction function can be decomposed into a sum of lower-dimensional ALE functions, as explained in the chapter on functional decomposition.

All in all, in most situations I would prefer ALE plots over PDPs, because features are usually correlated to some extent.