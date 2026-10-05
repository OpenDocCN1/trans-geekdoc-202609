# 2.4. MULTIVARIATE GAUSSIANS

Now let's take a Riemann sum to find the probability that Z takes a value in T(R’):

```
$P(\mathbf{Z} \subseteq T(\mathbf{R}')) = \int_{T(\mathbf{R}')} f_{\mathbf{Z}}(z_1, z_2) \ dz_1 dz_2$$
$$\approx \sum_{T(\mathbf{R}')} f_{\mathbf{Z}}(\mathbf{Ru}) \ \Delta A$$
$$\sum \sum_{\mathbf{R}'} f_{\mathbf{Z}}(\mathbf{Ru}) | |det(\mathbf{R}')| \Delta u_1 \Delta u_2$
```

The change of variables in the last step: we sum over the squares in U space, instead of parallelograms in R space.

So far, we have shown that (for any dimension n)

```
$P(\mathbf{U} \subseteq \mathbf{R}') = \int_{\dots} \int_{\mathbf{R}'} f_{\mathbf{U}}(\mathbf{u}) du_1 du_2 \dots du_n$$
$$P(\mathbf{Z} \subseteq T(\mathbf{R}')) = \int_{\dots} \int_{\mathbf{R}'} f_{\mathbf{Z}}(\mathbf{Ru}) |det(\mathbf{R})| du_1 du_2 \dots du_n$
```

Notice that these two probabilities are equivalent! The probability that U values in R’ must equal the probability that the transformed random vector Z takes a value in the transformed region T(R’).

Therefore, we can say

```
$P(\mathbf{U} \subseteq \mathbf{R}') = \int_{\dots} \int_{\mathbf{R}'} f_{\mathbf{U}}(\mathbf{u}) du_1 du_2 \dots du_n$$
$$= \int_{\dots} \int_{\mathbf{R}'} f_{\mathbf{Z}}(\mathbf{Ru}) |det(\mathbf{R})| du_1 du_2 \dots du_n$$
$$= P(\mathbf{Z} \subseteq T(\mathbf{R}')) $
```

We conclude that

```
$f_{\mathbf{U}}(\mathbf{u}) = f_{\mathbf{Z}}(\mathbf{Ru}) |det(\mathbf{R})|
```

An identical argument allows us to state that

```
$f_{\mathbf{Z}}(\mathbf{z}) = f_{\mathbf{U}}(\mathbf{R}^{-1}\mathbf{z}) |det(\mathbf{R}^{-1})| = \frac{1}{|det(\mathbf{R})|} f_{\mathbf{U}}(\mathbf{R}^{-1}\mathbf{z})_i$
```

Since the densities for all the U_i are i.i.d, and U = $\mathbf{R}^{-1}\mathbf{Z}$, we can write the joint density function of Z as

```
$f_{\mathbf{Z}}(\mathbf{z}) = \frac{1}{|det(\mathbf{R})|}$
= \frac{1}{|det(\mathbf{R})|} \prod_{i=1}^n f_{\mathbf{U}}(\mathbf{R}^{-1}\mathbf{z})_i$$
= \frac{1}{|det(\mathbf{R})|} (\sqrt{2\pi})^n$$
= \frac{1}{|det(\mathbf{R})|} (\sqrt{2\pi})^n e^{-\frac{1}{2}\mathbf{z}^T\mathbf{R}^T\mathbf{R}^{-1}\mathbf{z}}$$
= \frac{1}{|det(\mathbf{R})|} (\sqrt{2\pi})^n e^{-\frac{1}{2}\mathbf{z}^T(\mathbf{RR})^{-T}\mathbf{z}}$
```