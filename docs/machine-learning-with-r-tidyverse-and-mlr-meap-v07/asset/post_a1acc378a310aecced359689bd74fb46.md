
much y increases when x increases by one unit? Well if we recode our apple type variable such that Gala = 0 and Braeburn = 1, we can treat apple type as a continuous variable and find how much acidity changes as we go from 0 to 1. Take a look at figure 9.5. The intercept is the value of y when x is 0, which is the mean acidity when apple type = Gala. Gala is therefore said to be our *reference level*. The slope is the change in y with a one-unit increase in x, which is the difference between the mean acidity for Gala, and the mean acidity with Braeburn. This may feel like cheating but it works, and the slope with the least squares will be the one that connects the means of the categories.

> **NOTE** Which category you choose as the reference level makes no difference to the predictions made by a model, and is the first level of the factor (the first alphabetically by default).

![](img/a22105d68c35e8d5bd3c7bafb4644881_225_0.png)

**Figure 9.5** Finding the slope between two levels of a categorical variable using a dummy variable. The apple types are recoded as 0 and 1, and treated as a continuous variable. The slope now represents the difference in means between the two apple types, and the intercept represents the mean of the reference category (Gala).

So recoding dichotomous (two-level) factors into a single dummy variable with values of 0 and 1 makes sense, but what if we have a *polytomous factor* (a factor with more than two levels)? Do we code them as 1, 2, 3, 4, and so on, and treat this as a single continuous predictor? Well this wouldn’t work because it’s unlikely that a single straight line would connect the means of the categories. Instead, we create k-1 dummy variables, where k is the number of levels of the factor.

Take a look at the example in figure 9.6. We have four types of apple (Granny Smith is my favorite), and would like to predict pH based on the apple type used to make a particular batch. To convert our four-level factor into dummy variables we:

- 1. create a table of three columns, where each column represents a dummy variable
- 2. choose a reference level (Gala, in this case)
- 3. set the value of each dummy variable to 0 for the reference level
- 4. set the value of each dummy variable to 1 for a particular factor level

![](img/a22105d68c35e8d5bd3c7bafb4644881_226_0.png)

**Figure 9.6 Recoding a polytomous categorical variable into k-1 dummy variables.** A four-level factor can be represented using three (k−1) dummy variables. The reference level (Gala) has a value of 0 for each dummy variable. The other levels have a value of 1 for a particular dummy variable. A slope is estimated for each dummy.

We’ve now turned our single variable of four levels into three distinct dummy variables that each take a value of one or zero. But how does this help us? Well each dummy variable acts as a flag in the model formula to denote which level a particular case belongs to. The full model as shown in figure 9.6 is:

$y = \beta_0 + \beta_{d1}d1 + \beta_{d2}d2 + \beta_{d3}d3 + \varepsilon$

Now, as the intercept ($\beta_0$) represents acidity when all predictors are equal to 0, this is now the mean of the reference level, Gala. The slopes in the model ($\beta_{d1}$, $\beta_{d2}$ etc.) represent the difference between the mean of the reference level, and the means of each of the other levels. If a batch of cider was made with a particular type of apple, its dummy variables will "switch on" the slope between that type of apple, and the reference class, and "switch off" the others. For example, let’s say a particular batch was made with Braeburn apples, the model would look like this:

$y = \beta_0 + \beta_{d1} \times 1 + \beta_{d2} \times 0 + \beta_{d3} \times 0 + \varepsilon$

The slopes of the other apple types are still in the model, but because their dummy variables are set to 0, they make no contribution to the predicted value!

Models we build using the general linear model can mix both continuous and categorical predictors together. When we use our model to make predictions on new data, we simply:

- 1. take the values of each of the predictor variables for that data
- 2. multiply these values with the relevant slopes learned by the model
- 3. add these values together

## Listing 9.1 Loading and exploring the Ozone dataset

```r
data(Ozone, package = "mlbench")

ozoneTib <- as_tibble(Ozone)

names(ozoneTib) <- c("Month", "Date", "Day", "Ozone", "Press_height",
"Wind", "Humid", "Temp_Sand", "Temp_Monte",
"Inv_height", "Press_grad", "Inv_temp", "Visib")

ozoneTib
```

**A tibble: 366 x 13**

Column types: Month `<fct>`, Date `<fct>`, Day `<fct>`, Ozone `<dbl>`, Press_height `<dbl>`, Wind `<dbl>`, Humid `<dbl>`, Temp_Sand `<dbl>`, Temp_Monte `<dbl>`.

| Month | Date | Day | Ozone | Press_height | Wind | Humid | Temp_Sand | Temp_Monte |
|-------|------|-----|-------|--------------|------|-------|-----------|------------|
| 1 | 1 | 4 | 3 | 5480 | 8 | 20 | NA | NA |
| 2 | 1 | 2 | 5 | 3 | 5660 | 6 | NA | 38 | NA |
| 3 | 1 | 3 | 6 | 3 | 5710 | 4 | 28 | 40 | NA |
| 4 | 1 | 4 | 7 | 5 | 5700 | 3 | 37 | 45 | NA |
| 5 | 1 | 5 | 1 | 5 | 5760 | 3 | 51 | 54 | 45.3 |
| 6 | 1 | 6 | 2 | 6 | 5720 | 4 | 69 | 35 | 49.6 |
| 7 | 1 | 7 | 3 | 4 | 5790 | 6 | 19 | 45 | 46.4 |
| 8 | 1 | 8 | 4 | 4 | 5790 | 3 | 25 | 55 | 52.7 |
| 9 | 1 | 9 | 5 | 6 | 5700 | 3 | 73 | 41 | 48.0 |
| 10 | 1 | 10 | 6 | 7 | 5700 | 3 | 59 | 44 | NA |

... with 356 more rows, and 4 more variables: Inv_height `<dbl>`, Press_grad `<dbl>`, Inv_temp `<dbl>`, Visib `<dbl>`.

At present the Month, Day, and Date variables are factors. Arguably this may make sense, but we’re going to treat them as numerics for this exercise. To do this, I use the handy `mutate_all()` function, which takes the data as the first argument and a transformation/function as the second argument. Here, I use `as.numeric` to convert all the variables into the numeric class.

> **NOTE** The `mutate_all()` function doesn’t alter the names of the variables, it just transforms them in place.

Next, I can see we have some missing data in this dataset (use `map_dbl(ozoneTib, ~sum(is.na(.)))` to see how many). Missing data is ok in our predictor variables (we’ll deal with this later using imputation), but missing data for the variable we’re trying to predict is not okay. Therefore I remove the cases without any Ozone measurement by piping the result of the `mutate_all()` call into the `filter()` function, where I remove cases with an NA value for Ozone.

> **NOTE** Could we have imputed missing data in our target variable? Yes we could have, but this has the potential to introduce bias into our model. This is because you’ll be training a model to predict values that were themselves generated by a model.

## Listing 9.2 Cleaning the data

```r
ozoneClean <- mutate_all(ozoneTib, as.numeric) %>%
  filter(is.na(Ozone) == FALSE)

ozoneClean
```

**A tibble: 361 x 13**

Column types: Month `<dbl>`, Date `<dbl>`, Day `<dbl>`, Ozone `<dbl>`, Press_height `<dbl>`, Wind `<dbl>`, Humid `<dbl>`, Temp_Sand `<dbl>`, Temp_Monte `<dbl>`, Inv_height `<dbl>`, Press_grad `<dbl>`, Inv_temp `<dbl>`, Visib `<dbl>`.

| Month | Date | Day | Ozone | Press_height | Wind | Humid | Temp_Sand | Temp_Monte |
|-------|------|-----|-------|--------------|------|-------|-----------|------------|
| 1 | 1 | 4 | 3 | 5480 | 8 | 20 | NA | NA |
| 2 | 1 | 2 | 5 | 3 | 5660 | 6 | NA | 38 | NA |
| 3 | 1 | 3 | 6 | 3 | 5710 | 4 | 28 | 40 | NA |
| 4 | 1 | 4 | 7 | 5 | 5700 | 3 | 37 | 45 | NA |
| 5 | 1 | 1 | 1 | 5 | 5760 | 3 | 51 | 54 | 45.3 |

... with 356 more rows, and 4 more variables: Inv_height `<dbl>`, Press_grad `<dbl>`, Inv_temp `<dbl>`, Visib `<dbl>`.

Let’s plot each of our predictor variables against Ozone to get an idea of the relationships in the data. I start with our usual trick of gathering the variables with the `gather()` function so we can plot them on separate facets.

> **NOTE** Remember we have to use `-Ozone` to prevent the Ozone variable from being gathered with the others.

In our `ggplot()` call, we facet by Variable, and allow the x axes of the facets to vary by setting the `scale` argument equal to "free_x". Then along with a `geom_point` layer, I add two `geom_smooth` layers. The first `geom_smooth` is given no arguments and so uses the default settings. By default, `geom_smooth` will draw a LOESS curve to the data (a curvy, local regression line) if there are fewer than 1000 cases, or a GAM curve if there are 1000 or more cases. Either will give us an idea of the shape of the relationships. The second `geom_smooth` layer specifically asks for the `lm` method (linear model), which draws a linear regression line that best fits the data. Drawing both of these will help us identify if there are relationships in the data that are non-linear.

## Listing 9.3 Plotting the data

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

The plot resulting from code listing 9.3 is shown in figure 9.7. Hmm, some of the predictors have a linear relationship with ozone levels, some have a non-linear relationship with it, and some seem to have no relationship at all!
