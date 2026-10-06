# Whole brain volume Six brain structures 86 brain structures

![](bbox=[0.172, 0.103, 0.786, 0.303])

**Figure 3.1** Brain volumes for predicting the age of preterm babies from MRI scans. Left: whole brain volume as a single feature; middle: six main structures; right: detailed segmentation resulting in 86 features.

and predicted target values

```
$L(w) = \frac{1}{2}\sum_{i=1}^{N}(y_i - \hat{y}_i)^2, \quad (3.1)$
```

where

$\hat{y}_i = w_0 + w_1x_1 + ... + w_Dx_i$.

In our biomedical example, each sample denoted by index $i$ is a brain MRI scan, and the feature vector $\mathbf{x}_i$ is composed of volumes of brain structures calculated from that scan. Each feature, denoted by index $k$, represents a volume of a particular brain structure, and the target value $y_i$ is the true GA of the baby at the time of the scan.

# Matrix representation

Next, we will construct a feature matrix for regression. Note that we have $D$ features but $D+1$ weights. The weight $w_0$ is not multiplied by a feature and is often called a **bias** or **intercept**. In order to simplify the equations, we will define a new feature $x_0 = 1$. The model will simplify to

```
$\hat{y} = \sum_{k=0}^{D} w_kx_k$.
```

Construction of a feature matrix is described in Sect. 2.1.3. If we add the feature $x_0$, the feature matrix will become