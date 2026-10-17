# ### 14.1.2 Ionosphere Dataset

In this tutorial we will use the Ionosphere Dataset. This dataset involves the prediction of structure in the atmosphere. The baseline performance on the problem is approximately 64%. You can learn more about it in Appendix A, Section A.9. Download the dataset and save it into your current working directory with the filename ionosphere.csv.

# ## 14.2 Tutorial

This tutorial is broken down into 4 parts:

+   1. Euclidean Distance.
+   2. Best Matching Unit.
+   3. Training Codebook Vectors.
+   4. Ionosphere Case Study.

These steps will lay the foundation for implementing and applying the LVQ algorithm to your own predictive modeling problems.

# ### 14.2.1 Euclidean Distance

The first step needed is to calculate the distance between two rows in a dataset. We will use Euclidean distance, first introduced in Chapter 13. The calculation of Euclidean distance can be summarized as:

\( distance = \sqrt{\sum_{i=1}^{n}(x1_i - x2_i)^2} \) (14.1)

Where x1 is the first row of data, x2 is the second row of data and i is the index for a specific column as we sum across all columns. With Euclidean distance, the smaller the value, the more similar two records will be. A value of 0 means that there is no difference between two records. Below is a function named euclidean_distance() that implements this in Python.

```
# calculate the Euclidean distance between two vectors
def euclidean_distance(row1, row2):
    distance = 0.0
    for i in range(len(row1)-1):
        distance += (row1[i] - row2[i])**2
    return sqr(distance)
```

Listing 14.1: Function To Calculate the Euclidean Distance Between Rows.

You can see that the function assumes that the last column in each row is an output value which is ignored from the distance calculation. We can test this distance function with a small contrived classification dataset. We will use this dataset a few times as we construct the elements needed for the LVQ algorithm.