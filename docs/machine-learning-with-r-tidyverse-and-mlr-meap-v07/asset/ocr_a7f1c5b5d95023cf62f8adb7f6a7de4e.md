# Listing 9.2 Cleaning the data

```
```r
ozoneClean <- mutate_all(ozoneTib, as.numeric) %>%
  filter(is.na(Ozone) == FALSE)

ozoneClean

# A tibble: 361 x 13
  Month  Date   Day Ozone Press_height  Wind Humid Temp_Sand Temp_Monte
  <dbl> <dbl> <dbl> <dbl>        <dbl> <dbl> <dbl>     <dbl>      <dbl>
1     1     1     4     3         5480     8    20        NA         NA
2     1     2     5     3         5660     6    NA        38         NA
3     1     3     6     3         5710     4    28        40         NA
4     1     4     7     5         5700     3    37        45         NA
5     1     1     1     5         5760     3    51        54       45.3
# ... with 356 more rows, and 4 more variables: Inv_height <dbl>,
#   Press_grad <dbl>, Inv_temp <dbl>, Visib <dbl>
```
```

Let’s plot each of our predictor variables against Ozone to get an idea of the relationships in the data. I start with our usual trick of gathering the variables with the `gather()` function so we can plot them on separate facets.

> **NOTE** Remember we have to use `-Ozone` to prevent the Ozone variable from being gathered with the others.

In our `ggplot()` call, we facet by Variable, and allow the x axes of the facets to vary by setting the `scale` argument equal to "free_x". Then along with a geom_point layer, I add two geom_smooth layers. The first geom_smooth is given no arguments and so uses the default settings. By default, geom_smooth will draw a LOESS curve to the data (a curvy, local regression line) if there are fewer than 1000 cases, or a GAM curve if there are 1000 or more cases. Either will give us an idea of the shape of the relationships. The second geom_smooth layer specifically asks for the lm method (linear model), which draws a linear regression line that best fits the data. Drawing both of these will help us identify if there are relationships in the data that are non-linear.

# Listing 9.3 Plotting the data

```
```r
ozoneUntidy <- gather(ozoneClean, key = "Variable",
                      value = "Value", -Ozone)

ggplot(ozoneUntidy, aes(Value, Ozone)) +
  facet_wrap(~ Variable, scale = "free_x") +
  geom_point() +
  geom_smooth() +
  geom_smooth(method = "lm", col = "red") +
  theme_bw()
```
```

The plot resulting from code listing 9.3 is shown in figure 9.7. Hmm, some of the predictors have a linear relationship with ozone levels, some have a non-linear relationship with it, and some seem to have no relationship at all!