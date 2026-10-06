# Making base R objects "tidy" 323

```
tidy(modencodefly.eset, addPheno=TRUE)
```

This demonstrates a range of options to tidy common R objects.

# How it works...

We start with step 1 by examining some functions to tidy the common lm object, created by the lm() function. The first task is to create the object, so we perform a multiple regression with the mtcars data, and then use the tidy() function to return an object summary of the components of the model. It looks like this:

| term | estimate std.error statistic | p.value |
| <chr> | dbl | dbl | dbl |
| ## 1 (Intercept) | 47.4 | 8.81 | 5.38 0.000000882 |
| ## 2 cyl | -3.14 | 0.398 | -7.88 |
| ## 3 qsec | -0.442 | 0.398 | -1.11 0.276 |

The augment() function returns per-observation data for the model, which we want. It looks like this:

| rownames | mpg cyl qsec .fitted .resid .hat |
| <chr> | dbl | dbl | dbl | dbl | dbl |\n| ## 1 Mazda RX4 | 21 | 6 | 16.5 | 21.3 -0.292 0.0665 | ... |
| ## 2 Mazda RX4 Wag | 21 | 6 | 17.0 | 21.0 -0.0447 0.0453 ... |

The glance() function inspects the model and returns summaries in a tidy format, as follows:

| r.square adj.r.squared sigma statistic | p.value df |
| dbl | dbl | dbl | dbl | dbl |
| ## 1 | 0.719 | 3.19 | 40.7 0.000000382 2 |

The function returns an object that is useful when we want to compare models. Consider comparing these data-frame objects with the default objects.

Step 2 shows the process for the t.test object. First, we run a t-test on some random numbers, to get the object, and then we run tidy() on it. The output looks like this:

| estimate estimate estimate2 statistic | p.value |
| dbl | dbl | dbl | dbl | dbl |\n| ## 1 | 0.201 | -0.158 | -0.359 | 0.577 0.567 37.8 | |

With step 3, we run ANOVA on the iris data using the aov() function to look at the effect of petal length - in this case, when we use tidy(), we get a model-level summary, perhaps not what we were expecting, so we instead run tidy() on the result of a post hoc test from TukeyHSD().