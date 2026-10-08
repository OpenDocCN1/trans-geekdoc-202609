Steps used by K-Means clustering to process the data points:

+   1. The data centers are selected randomly by ‘K’.
2. Assigns each data point to the nearest centers that have been randomly generated.
3. Re-calculates each cluster's center.
4. If centers do not change (or have minor change), the process will be completed.

Otherwise, we'll go back to step 2. (Set a maximum amount of iterations in advance to avoid getting stuck in an infinite loop, if the center of the cluster continues to alter).
nThe following plot applies “K-Means” to a building data set. Each column in the plot shows each building's efficiency. The four measurements relate to air conditioning, heating, installed electronic appliances (refrigerators, TV) and cooking gas. For simplicity of interpretation of the results, ‘K’ can be set to value ‘2’ for clustering, wherein one cluster will be selected as an efficient building group and the other cluster as an inefficient building group. You see the place of the structures on the left as well as a couple of the building characteristics used as inputs on the right: installed electronic appliances and heating.

![](bbox=[0.183, 0.563, 0.812, 0.856])

# Artificial Neural Networks