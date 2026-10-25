If you want even more verbose output, with details about each split, you can use the summary() method:

```
summary(bn.tree)  # print more verbose tree summary
```

```
#>
#> Call:
#> rpart(formula = y ~ top + bottom, data = bn)
#>   n= 200
#>
#>    CP nsplit rel error xerror     xstd
#> 1 0.84      0     1.00   1.14 0.0700
#> 2 0.09      1     0.16   0.19 0.0415
#> 3 0.01      2     0.07   0.12 0.0336
#>
#> Variable importance
#>    bottom      top
#>        66      34
#>
#> Node number 1: 200 observations,    complexity param=0.84
#>   predicted class=Counterfeit   expected loss=0.5   P(node) =1
#>     class counts:   100   100
#>   probabilities: 0.500 0.500
#>   left son=2 (88 obs) right son=3 (112 obs)
#>   Primary splits:
#>       bottom < 9.55 to the right, improve=71.6, (0 missing)
#>       top < 11   to the right, improve=30.7, (0 missing)
#>   Surrogate splits:
#>       top < 11   to the right, agree=0.685, adj=0.284, (0 split)
#>
#> Node number 2: 88 observations
#>   predicted class=Counterfeit   expected loss=0.0227   P(node) =0.44
#>     class counts:   86   2
#>   probabilities: 0.977 0.023
#>
#> Node number 3: 112 observations,    complexity param=0.09
#>   predicted class=Genuine   expected loss=0.125   P(node) =0.56
#>     class counts:   14   98
#>   probabilities: 0.125 0.875
#>   left son=6 (17 obs) right son=7 (95 obs)
#>   Primary splits:
#>       top < 11.1 to the right, improve=16.40, (0 missing)
#>       bottom < 9.25 to the right, improve= 2.42, (0 missing)
#>
#> Node number 6: 17 observations
#>   predicted class=Counterfeit   expected loss=0.235   P(node) =0.085
#>     class counts:   13   4
#>   probabilities: 0.765 0.235
#>
#> Node number 7: 95 observations
#>   predicted class=Genuine   expected loss=0.0105   P(node) =0.475
```