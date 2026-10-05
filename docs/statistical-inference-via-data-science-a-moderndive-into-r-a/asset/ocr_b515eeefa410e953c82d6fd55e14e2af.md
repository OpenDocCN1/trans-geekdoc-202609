# 8.2 Estimation with the bootstrap

```
percentile_ci <- bootstrap_means |
get_confidence_interval(level = 0.95, type = "percentile")
percentile_ci
```

```
# A tibble: 1 x 2
lower_ci upper_ci
<dbl> <dbl>
1 3.61198 3.756
```

Alternatively, we can visualize the interval (3.61, 3.76) by piping the bootstrap_means data frame into the visualize() function and adding a shade_confidence_interval() layer. We set the endpoints to be percentile_ci.

```
visualize(bootstrap_means) +
shade_confidence_interval(endpoints = percentile_ci)
```

![](bbox=[0.104, 0.435, 0.895, 0.653])

FIGURE 8.21: Percentile method 95% confidence interval shaded corresponding to potential values.

Observe in Figure 8.21 that 95% of the sample means stored in the stat variable bootstrap_means fall between the two endpoints marked with the darker lines, 2.5% of the sample means to the left of the shaded area and 2.5% of the sample means to the right. You also have the option to change the colors of the shading using the color and fill arguments.

The infer package has incorporated a shorter named function shade_ci() that produces the same results. Try out the following code: