# Responsive Gene Discovery

![](bbox=[0.219, 0.086, 0.781, 0.283])

Fig. 2.23. Next step of using the K-means for the toy data set. (A) The two centres have been updated. (B) New membership functions assigned to data points.

After these new updates, two cluster centres stopped change. A learning process was thus terminated.

Table 2.7. The membership function values in two steps of using the K-means algorithm for a data set of seven data points and two clusters shown in Fig. 2.22.

| Step 1 | | | Step 2 | | |
|---|---|---|---||
| x | $f_1(A)$ | $f_1(B)$ | x | $f_2(A)$ | $f_2(B)$ |
| 1 | 1 | 0 | 1 | 1 | 0 |
| 2 | 1 | 0 | 2 | 1 | 0 |
| 3 | 0 | 1 | 3 | 1 | 0 |
| 4 | 0 | 1 | 4 | 0 | 1 |
| 5 | 0 | 1 | 5 | 0 | 1 |
| 6 | 0 | 1 | 6 | 0 | 1 |
| 7 | 0 | 1 | 7 | 0 | 1 |

The R function for the K-means algorithm is kmeans and its syntax is shown below, where x is a matrix and centers is the parameter for specifying the number of clusters,

```
kmeans(x, centers, ...)
```

Figure 2.24 shows the application of a data set of two clusters. A K-model was constructed on this data set and indeed revealed this cluster structure. Suppose the data set was saved in a variable named by x. The code below was used to apply the kmeans function to the data set,

```
model=kmeans(x, centers=2)
```