The Greek letter Σ represents summation of values, and it is useful when a large number of values needs to be added. The letter $i$ underneath is the index of summation. It starts at $i=1$, the first value we are adding is $y_1=3$. Afterwards $i=2$, so we add $y_2=-1$ to our previous result, and so on, as shown in the equation above. The summation symbol can be very useful when adding numbers or making more complicated operations, such as defining the standard deviation.

To construct the standard deviation of a list of values, we

+   - first find the deviations of each value from their average,
- then square those deviations,
- then find the average of the squared deviations, and
- take the square root of this average to finish.

In our example, the standard deviation is given by

```
$SD = \sqrt{\frac{\sum_{i=1}^{4}(y_i-\bar{y})^2}{4}} = \sqrt{\frac{(3-2)^2+(-1-2)^2+(5-2)^2+(9-2)^2}{4}} = \sqrt{\frac{1+9+9+49}{4}} = \sqrt{17}=4.12$
```

We present another example, this using R. We use again our bowl activity with red and white balls in the bowl. We create a Boolean variable `is_red` that corresponds to TRUEs for red balls or FALSEs for white balls using these numbers, we compute the proportion (average of 1s and 0s) using the `mean()` function and the standard deviation using the `sd()` function inside `summarize())

```
bowl |>
mutate(is_red = color == "red") |>
summarize(p = mean(is_red), st_dev = sd(is_red))
```

```
# A tibble: 1 x 2
 p st_dev
dbl <dbl>
1 0.375 0.484
```

The `sd()` function actually calculates the sample standard deviation, which divides the sum of squared deviations by $n-1$ instead of $n$. The difference is noticeable for small numbers of values but almost irrelevant, for practical purposes, when using a large number of values. It is used for simplicity.