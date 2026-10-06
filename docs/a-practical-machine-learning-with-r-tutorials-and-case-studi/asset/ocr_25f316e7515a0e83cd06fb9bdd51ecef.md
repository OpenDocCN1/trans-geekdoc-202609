# 4 k-Nearest Neighbors — Getting Started

![](bbox=[0.23, 0.178, 0.8, 0.458])

**FIGURE 4.5** Predicting Wine Color with k-Nearest Neighbors (k=1)

of the magnitude labeled c is the distance between the red and the blue point (Euclidean Distance). To calculate this distance, we can use the Pythagorean theorem:

> $c^2 = a^2 + b^2$$

When we substitute $a$ and $b$ with the $Sulfur$ and $Acid$ differences between the wine we want to predict (*blue* point) and the wine symbolized by the red dot in the triangle in Figure 4.5, we can calculate the *Euclidean Distance* (*EucDist*)

```
$EucDist_i^2 = (Sulfur_i - Sulfur_p)^2 + (Acid_i - Acid_p)^2$$
$$\longleftarrow a^2 + b^2$$$
$$EucDist_i = \sqrt{(Sulfur_i - Sulfur_p)^2 + (Acid_i - Acid_p)^2} \quad (4.1)$$
```

The formula above can be used to calculate the *Euclidean Distance* between the wine we want to predict ($p$) and any other wine ($i$) in the training dataset. This is because we know the values of the predictor variables for the point we like to predict as well as the predictor values for all observations in the training dataset. Calculating *Euclidean Distances* from wine $p$ to all wines in