is equivalent to working with 1's and 0's. In particular, adding all the 1's and 0's is\equivalent to counting how many red balls are in the bowl.

We compute this using the sum() function inside the summarize() function. Recall from Section 3.3 that summarize() takes a data frame with many rows and returns a data frame with a single row containing summary statistics such as the sum():

```
bowl |>
mmutate(is_red = (color == "red")) |>
summarize(num_red = sum(is_red))
```

```
# A tibble: 1 x 1
num_red
<int>
1 900
```

The sum() has added all the 1's and 0's and has effectively counted the number of red balls. There are 900 red balls in the bowl. Since the bowl contains 2400 balls, the proportion of red balls is 900/2400 = 0.375. We could ask R to find the proportion directly by replacing the sum() for the mean() function inside summarize(). The average of 1's and 0's is precisely the proportion of red balls in the bowl:

```
bowl |>
mmutate(is_red = (color == "red")) |>
sumize(prop_red = mean(is_red))
```

```
# A tibble: 1 x 1
prop_red
<dbl>
1 0.375
```

This code works well but can be simplified once more. Instead of creating a new Boolean variable, is_red before finding the proportion, we could write both steps simultaneously in a single line of code:

```
bowl |>
sumize(prop_red = mean(color == "red"))
```

```
# A tibble: 1 x 1
prop_red
<dbl>
1 0.375
```