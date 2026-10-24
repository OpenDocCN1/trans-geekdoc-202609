where n is size of the sample. With the sample size n, sample standard deviation can be defined similarly. Explain why there is such a minor difference at defining sample variance and population variance.

# 2.6. Reason why variance and standard deviation can be computed efficiently in very large data sets.

# 2.7. Suppose that a hospital tested the age and body fat data for 18 randomly selected adults with the following results:

| age | 23 | 23 | 27 | 27 | 39 | 41 | 47 | 49 | 50 |
|---|---|---|---|---|---|---|---|---|---|
| %fat | 9.5 | 26.5 | 7.8 | 17.8 | 31.4 | 25.9 | 27.4 | 27.2 | 31.2 |
| age | 52 | 54 | 54 | 56 | 57 | 58 | 58 | 60 | 61 |
| %fat | 34.6 | 42.5 | 28.8 | 33.4 | 30.2 | 34.1 | 32.9 | 41.2 | 35.7 |

+   a. Calculate the mean, median, and standard deviation of age and %fat

+   b. Draw the boxplots for age and %fat

+   c. Draw a scatter plot and a q-q plot based on these two variables

# 2.8. Briefly outline how to compute the dissimilarity between objects described by the following:

+   a. Nominal attributes

+   b. Asymmetric binary attributes

+   c. Numeric attributes

+   d. Term-frequency vectors

# 2.9. Given two objects represented by the tuples (22, 1, 42, 10) and (20, 0, 36, 8):

+   a. Compute the Euclidean distance between the two objects

+   b. Compute the Manhattan distance between the two objects

+   c. Compute the Minkowski distance between the two objects, using h = 3

+   d. Compute the supremum distance between the two objects

# 2.10. The median is one of the most important measures in data analysis. Propose several methods for median approximation. Analyze their respective complexity under different parameter settings and decide to what extent the real value can be approximated. Moreover, suggest a heuristic strategy to balance between accuracy and complexity, and then apply it to all methods you have given.

# 2.11. It is important to define or select similarity measures in data analysis. However, there is no commonly accepted subjective similarity measure. Results can vary depending on the similarity measures used. Nonetheless, seemingly different similarity measures may be equivalent after some transformation.

Suppose we have the following 2-D data set:

| | A1 | A2 |
|---|---|---|
| x1 | 1.5 | 1.7 |
| x2 | 2 | 1.9 |
| x3 | 1.6 | 1.8 |
| x4 | 1.2 | 1.5 |
| x5 | 1.5 | 1.0 |

+   a. Consider the data as 2-D data points. Given a new data point, x = (1.4, 1.6) as a query, rank the database points based on similarity with the query using Euclidean distance, Manhattan distance, supremum distance, and cosine similarity.