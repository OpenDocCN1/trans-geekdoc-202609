# 7.7 PROTOTYPES AND CRITISMS

```
$k(x, x') = exp(-\gamma ||x - x'||^2)$
```

$||x-x'||^2$ is the Euclidean distance between two points and $\gamma$ is a scaling parameter. The value of the kernel decreases with the distance between the two points and ranges between zero and one: Zero when the two points are infinitely far apart; one when the two points are equal.

We combine the MMD2 measure, the kernel and greedy search in an algorithm for finding prototypes:

+   - Start with an empty list of prototypes.
- While the number of prototypes is below the chosen number m:
  - For each point in the dataset, check how much MMD2 is reduced when the point is added to the list of prototypes. Add the data point that minimizes the MMD2 to the list.
- Return the list of prototypes.

The remaining ingredient for finding criticisms is the witness function, which tells us how much two density estimates differ at a particular point. It can be estimated using:

```
$witness(x) = \frac{1}{n}\sum_{i=1}^n k(x, x_i) - \frac{1}{m}\sum_{j=1}^m k(x, z_j)$
```

For two datasets (with the same features), the witness function gives you the means of evaluating the point x fits better. To find criticisms, we look for extreme values of the witness function in positive and negative directions. The first term in the witness function is the average proximity between point x and the data, respectively, the second term is the average proximity between point x and the prototypes. If the witness function for a point x is close to zero, the density function of the data and the distribution of the prototypes are close together, which means that the distribution of prototypes resembles the distribution of the data at x. A negative witness function at point x means the prototype distribution overestimates the data distribution (for example if we select a prototype but there are only a few data points nearby); a positive witness function at point x means that prototype distribution underestimates the data distribution (for example if there are many data points around x we have not selected any prototypes nearby).

To give you more intuition, let us retrieve the prototypes from the plot beforehand and display the witness function for a manually selected points. The labels in the following plot show the value of the witness function for various points marked as triangles. Only the point in the middle has a high absolute value and is a good candidate for a criticism.

The witness function allows us to explicitly search for data instances that are not well represented by the prototypes.ing are points with high absolute value in the witness function. Like prototypes, criticisms are also found through greedy search. But instead of