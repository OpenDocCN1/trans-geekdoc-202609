Then for the second step, we are going to work on a formula that is similar to the hard k-means, but we are just recalculating the means based on the responsibilities that we want to sent with it. The algorithm that we are going to use for this includes:

```
m(k) = sum[n=1..N] { r(k,n)* x(n) ] / sum[n-1..N] {
r(k,n) }
```

so, when you take the time to look at this algorithm above, you are going to see that it is similar to the weighted mean. This is going to show you that if the r(k,n) is higher, then the mean is going to be more important to the cluster of k. When you see this, it is going to show that this is going to have the biggest influence on the calculation of the mean. But if the mean is higher when you look at the algorithm, you will know that the opposite is true.

Now, with some of the information in order that we have discussed already, it is time to look at some of the coding that is needed in order to