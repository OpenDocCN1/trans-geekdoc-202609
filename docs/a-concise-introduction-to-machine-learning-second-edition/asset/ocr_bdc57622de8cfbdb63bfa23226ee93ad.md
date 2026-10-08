![](bbox=[0.235, 0.175, 0.769, 0.303])

(a) Original.

(b) Reconstruction with two principal components.

(c) Reconstruction with three principal components.

![](bbox=[0.209, 0.373, 0.769, 0.523])

(d) Sample locations in subspace spanned by two principal components.

(e) Sample locations in subspace spanned by three principal components.

Figure 7.4: PCA for four digits.

while its projection on the principal subspace is given by the first $K$ terms of the decomposition

```
$$\sum_{d=1}^K(\mathbf{v}_n^T \mathbf{w}_d)\mathbf{w}_d.$
```

Thus, the squared distance between a sample and its projection is the length of the remaining $D - K$ terms in the decomposition:

```
$|\sum_{d=K+1}^D(\mathbf{v}_n^T \mathbf{w}_d)\|^2 = \left(\sum_{d=K+1}^D(\mathbf{v}_n^T \mathbf{w}_d)\right)^T(\sum_{d=K+1}^D(\mathbf{v}_n^T \mathbf{w}_d)^2$
```

to $\mathbf{w}_1, \dots, \mathbf{w}_D$ being orthonormal.