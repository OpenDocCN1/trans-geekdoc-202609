# K-Nearest Neighbor Algorithm

To determine the “Customer Class” for C1, we will find the distance of the data points of C1 from all the other data points available to us in Table 3.2. To find the distance, we can use the Euclidean distance.

We know that for 2-dimensional data, the Euclidean distance between 2 points $(x_i, y_i)$ and $(x_j, y_j)$ is defined as:

```
$\sqrt{(x_1 - x_2)^2 + (y_1 - y_2)^2}$
```

Using this formula, we can find the distance between each customer considering “Recency” as x and “Total Amount” as y.

So, the Euclidean distance between customer C1 and A1 can be calculated as:

```
$\sqrt{(14 - 41)^2 + (7000 - 1500)^2} = \sqrt{(-27)^2 + (5500)^2} = \sqrt{729 + 30250000} = \sqrt{30250729} = 5500.0662$
```

So, we have a mechanism. However, we note that the calculation for the Euclidean distance is heavily biased towards the “Total Amount” value. This is because the “Total Amount” value is much larger than the value of “Recency”. To overcome this problem, we need to standardize our data.

# Standardizing the data

To standardize the data, we can find the z-value of each data point. The z-value can be found using the formula:

```
$z = \frac{x-\mu}{\sigma}$
```

Here, x is the data point, $\mu$, and $\sigma$ is the mean and the standard deviation of the attribute for which x is the data point:

Let us understand this practically. Let us take the attribute “Recency”. For all the data points, we can find the mean as:

```
$\mu_{Recency} = \frac{\sum_{i=1}^{n} x_i}{n} = \frac{41+10+39+27+77+50+19+19+17+30}{10} = \frac{259}{10} = 25.9$
```

Now, we can find the Standard Deviation for the data points of “Recency” as:

```
$\sigma_{Recency} = \sqrt{\frac{\sum_{i=1}^{n}(x_i-\mu)^2}{n}} = \sqrt{\frac{(41-25.9)^2+(10-25.9)^2+\dots+(30-25.9)^2}{10}} = 13.5$
```