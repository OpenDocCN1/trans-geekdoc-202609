
In other words, `u[j]` points in the direction of `q[j]`. Thus, Eq. [(6.30)](#Chp006_249-291_B9780443292385000123.xhtml#deq64) suggests that while projecting `y` onto the column space of `X`, the directions `u[j]` associated with larger values of variance are weighted more heavily than the rest. *Ridge regression respects and assigns higher weights to the more informative directions, where most of the data activity takes place*. Alternatively, the less important directions, those associated with small data variance, are shrunk the most.

![Figure 6.4 The singular vector v1, which is associated with the singular value σ1 > σ2, points to the direction where most of the (variance) activity in the data space takes place. The variance in the direction of v2 is smaller.](images/B9780443292385000123/gr004.jpg)

[Figure 6.4](#Chp006_249-291_B9780443292385000123.xhtml#cf0395) The singular vector `v[1]`, which is associated with the singular value `σ[1] > σ[2]`, points to the direction where most of the (variance) activity in the data space takes place. The variance in the direction of `v[2]` is smaller.

One final comment concerning ridge regression is that the ridge solutions are not invariant under scaling of the input variables. This becomes obvious by looking at the respective equations. Thus, in practice, often the input variables are standardized to unit variances.

### Principal components regression

We have just seen that the effect of the ridge regression is to enforce a shrinking rule on the parameters, which decreases the contribution of the less important of the components `u[i]` in the respective summation. This can be considered as a soft shrinkage rule. An alternative path is to adopt a hard thresholding rule and keep only the `m` most significant directions, known as the *principal axes* or *directions*, and forget the rest by setting the respective weights equal to zero. Equivalently, we can write

```
ŷ = Σ(i=1 to m) θ̂[i] u[i]
```

where

```
θ̂[i] = u[i]^(T) y,  i = 1, 2, …, m.
```

Furthermore, employing Eq. [(6.18)](#Chp006_249-291_B9780443292385000123.xhtml#deq44) we have

```
ŷ = Σ(i=1 to m) (θ̂[i] / σ[i]) X v[i]
```

or equivalently, the weights for the expansion of the solution in terms of the input data can be expressed as

```
θ = Σ(i=1 to m) (θ̂[i] / σ[i]) v[i].
```

In other words, the prediction `ŷ` is performed in a subspace of the column space of `X`, which is spanned by the `m` principal axes, that is, the subspace where most of the data activity takes place.

## 6.6 The recursive least-squares algorithm
