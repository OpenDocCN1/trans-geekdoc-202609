392

10 Inference for Regression

variables $(X_1

$Y = \beta_0 + \beta_1 \cdot X_1 + \dots + \beta_p \cdot X_p + \epsilon$

$\beta_0$ is the population intercept and $eta_j$ is the population partial slope related to
regressor $X_j$. The error term $\epsilon$ accounts for the portion of $Y$ that is not explained
by the line. In some case, we assume that the expected value is $E(\epsilon) = 0$,
t standard deviation is $SD(\epsilon) = \sigma$, and the variance $Var(\epsilon) = \sigma^2$. The variance
 standard deviation are constant regardless of the value of $X_1, X_2, \dots, X_p$. If we
 to take a large number of observations from this population, we expect the
er terms sometimes to be greater than zero and other times less than zero, but
average equal to zero, or take $\sigma$ units away from zero.

# 10.4.2 Example: Coffee quality rating scores

As in the case of simple linear regression we use a random sample to estimate the
parameters in the population. To illustrate these methods, we use the coffee_quality
data frame from the modernize package. This dataset from the Coffee Quality In-
stitute contains information about coffee rating scores based on ten different at-
tributes: aroma, flavor, aftertaste, acidity, body, balance, uniformity, clean_cup, sweet-
ess, and overall. In addition, the data frame contains other information such as the
moisture_percentage and the coffee's country and continent_of_origin. We can assume
that this is a random sample.

We plan to regress total_cup_points (response variable) on the numerical explanatory
variables aroma, flavor, and moisture_percentage and the categorical explanatory vari-
with four categories: Africa, Asia, North America, and South America. Before pro-
ceding, we construct a data frame called coffee_data by keeping the variables
of interest. In addition, the variable continent_of_origin has been read into R with
type character, and we want to make it type factor. We do this by using dplyr verbs
and the command as.factor() inside mutate to make continent_of_origin
a factor with the ordering of "Africa", "Asia", "North America", and "South America".

```
coffee_data <- coffee_quality |>
select(aroma,
flavor,
moisture_percentage,
continent_of_origin,
total_cup_points) |>
mmutate(continent_of_origin = as.factor(continent_of_origin))
```

The first rows of coffee_data are shown here:

coffee_data

# A tibble: 207 x 5