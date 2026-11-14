the variable $p$ can be one of the feature types (e.g., the number of modes). On this basis, the proposed method consists of six main steps including distance calculation, distance arrangement for obtaining order statistics, sample fraction selection ($k$), sign alteration for providing negative maximum values, the EVI estimation, and quantile modeling based on the previous sections. For simplicity, Fig. 2.2 depicts the flowchart of the main steps of the proposed method.

In the first step, one needs to calculate the distance between each feature sample with the other ones. For this reason, the well-known Euclidean distance is applied to perform this process. For two vectors $\mathbf{x}_i$ and $\mathbf{x}_j$, Eq. (2.21) represents the function of this distance:

```
$d_E(\mathbf{x}_i, \mathbf{x}_j) = (\mathbf{x}_i - \mathbf{x}_j)^T (\mathbf{x}_i - \mathbf{x}_j)$
```

+   - Step 1: Calculate the distance between $\mathbf{x}_i$ and the remaining feature/training samples $\mathbf{x}_1, ..., \mathbf{x}_{i-1}, \mathbf{x}_{i+1}, ..., \mathbf{x}_n$
+   - Step 2: Arrange the distance values in ascending order
+   - Step 3: Find the $k$-smallest distance values (SDVs)
+   - Step 4: Change the signs of the selected distance values
+   - Step 5: Estimate the EVI of the negated $k$-SDVs
+   - Step 6: Compute the absolute value of the $i^{th}$ quantile of the negated $k$-SDVs

Fig. 2.2 The main steps of the proposed NNS-EVT method in the baseline stage