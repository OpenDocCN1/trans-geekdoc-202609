where $\Delta$ is the matrix of the Euclidean distance between the sample points, and $\alpha$ is a constant in the range (0, 1). After the transformation of (13.23), the distance between the samples of the same class does not change, but the distance between different classes of data increases, so that more similar data can be obtained when seeking the nearest neighbours. After finding $\Delta'$, the $K$ nearest neighbours of LLE can be found by $\Delta'$, and the low-dimensional representation of the data set is obtained by using the basic framework of the algorithm.

# **13.3.1.3 S-LE**

S-LE is a supervised learning algorithm for the LE algorithm. The main idea is that the nearest neighbour sets of similar data and neighbour sets of different classes of data are first solved.

```
$AS(x_i) = \frac{1}{N} \sum_{j=1}^{N} \exp \left(-\frac{\|x_i - x_j\|^2}{\beta}\right)$ (13.24)
```

```
$N_w(x_i) = \left\{ x_j \middle| y_i = y_i, \exp \left(-\frac{\|x_i - x_j\|^2}{\beta}\right) > AS(x_i) \right\}$ (13.25)
```

```
$N_b(x_i) = \left\{ x_j \middle| y_i \neq y_i, \exp \left(-\frac{\|x_i - x_j\|^2}{\beta}\right) > AS(x_i) \right\}$ . (13.26)
```

Then, two adjacency matrices are obtained according to these two adjacent sets, and two optimisation functions are obtained as follows:

```
$W_{w,ij} = \begin{cases} \exp \left(-\frac{\|x_i-x_j\|^2}{\beta}\right) & \text{if } x_j \in N_w(x_i) \text{ or } x_i \in N_w(x_j) \\ 0 & \text{otherwise} \end{cases}$ (13.27)
```

```
$W_{b,ij} = \begin{cases} 1 & \text{if } x_j \in N_b(x_i) \text{ or } x_i \in N_b(x_j) \\ 0 & \text{otherwise} . \end{cases}$ (13.28)
```

Let $x_i'$ be a low-dimensional representation of $x_i$. Then, for each sample point, there is an objective function

```
$\min \frac{1}{2} \sum_{i,j} \|x_i' - x_j'\|^2 W_{w,ij}$ (13.29)
```

```
$\max \frac{1}{2} \sum_{i,j} \|x_i' - x_j'\|^2 W_{b,ij}$ . (13.30)
```

Let $Z = [x_1'$, $\dots$, $x_N']^T$. Then, the objective functions (13.29), (13.30) can be rewritten as

```
$\min \text{ tr } (Z^T L_w Z)$ (13.31)
```

```
$\max \text{ tr } (Z^T L_b Z)$ (13.32)
```