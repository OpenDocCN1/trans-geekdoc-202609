# Chapter 3

# Low-Rank approximation

# 3.1 Total Least Squares

Previously, we have covered Ordinary Least Squares (OLS), which assumes that the dependent variable y is noisy but the independent variables x are noise-free. We now discuss Total Least Squares (TLS), which arises in the case where we assume that x data is also corrupted by noise. Both LS methods want to get a model that produce an approximation closest to all the points, but they measure the distance differently. OLS tries to minimize the vertical distance between the fitted line and data points, while TLS tries to minimize the perpendicular distance.

![](bbox=[0.373, 0.506, 0.625, 0.638])

The red represents vertical distance, which OLS aims to minimize. The blue line represents perpendicular distance, which TLS aims to minimize. Note that all blue lines are perpendicular to the black line (hypothesis model), while all red lines are perpendicular to the x axis.

We might begin with a probabilistic formulation and fit the parameters via maximum likelihood estimation, as before. Suppose on the plane, we have a true model that we can recover from some data points:

```
$y_i = ax_i$$
```

and observe data points in the form

```
$$(x_i + z_{xi}, y_i + z_{yi})$$
```

where the noise terms are normally distributed, i.e. $z_{xi}, z_{yi} \overset{\textiid}}{=} \mathcal{N}(0, 1)$.

Applying the equation (1) that comes from the true model mentioned above, we rewrite (2) in the