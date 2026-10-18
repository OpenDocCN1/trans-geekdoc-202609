# 2.9 Solutions to exercises

+   1. Load mtcars, convert it to a tibble and explore with `summary()`:

```
```r
library(tidyverse)

data(mtcars)

mtcarsTib <- as_tibble(mtcars)

summary(mtcarsTib)
```
```

+   2. Select all columns except `qsec` and `vs`:

```
```r
select(mtcarsTib, c(-qsec, -vs))
# or
select(mtcarsTib, c(-7, -8))
```
```

+   3. Filter for rows with cylinder numbers **not** equal to 8

```
```r
filter(mtcarsTib, cyl != 8)
```
```

+   4. Group by gear, summarize the medians of `mpg` and `disp`, and mutate a new variable that is the `mpg` median divided by the `disp` median:

```
```r
mtcarsTib %>%
  group_by(gear) %>%
  summarize(mpgMed = median(mpg), dispMed = median(disp)) %>%
  mutate(mpgOverDisp = mpgMed / dispMed)
```
```

+   5. Create a scatter plot of the `drat` and `wt` variables and color by `carb`:

```
```r
ggplot(mtcarsTib, aes(drat, wt, col = carb)) +
  geom_point()

ggplot(mtcarsTib, aes(drat, wt, col = as.factor(carb))) +
  geom_point()
```
```

+   6. Gather `vs`, `am`, `gear` and `carb` into a single key-value pair:

```
```r
gather(mtcarsTib, key = "variable", value = "value", c(vs, am, gear, carb))
# or
gather(mtcarsTib, key = "variable", value = "value", c(8:11))
```
```

+   7. Iterate over each column of mtcars, returning a logical vector:

```
```r
map_lgl(mtcars, ~sum(.) > 1000)
# or
map_lgl(mtcars, function(.) sum(.) > 1000)
```
```