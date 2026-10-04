# Example: Detecting Interaction Effects with Contour Plots

predictors setting up the values for the coefficients $eta_0$, $eta_1$, $eta_2$, and $eta_3$, and the predictors $x_1$ and $x_2$ and the error term $\epsilon$.

Load the necessary libraries and set the seed for reproducibility.

```
library(tidyverse)
set.seed(123)
```

Simulate the data ready for interaction effects.

```
beta0<- rep(0,200)
beta1<- rep(1,200)
beta2<- rep(1,200)
```

Then, simulate the predictors $x_1$ and $x_2$ and the error term $\epsilon$ for 200 observations.

```
x1<- runif(200, min = 0, max = 1)
x2 <- runif(200, min = 0, max = 1)
e <- rnorm(200)
```

Then for each of the three cases we simulate a $eta_3$ based on antagonism, interaction, or synergy with values -10, 0, and 10.

# ### Case 1: Antagonism

```
beta3 <- rep(-10,200)
```

Assemble the values for the predictors into the equation, to obtaining the response variable $y$. This will be our synthetic "observed" data.

```
y1 = beta0 + beta1*x1 + beta2*x2 + beta3*(x1*x2) + e
```

Apply a linear model to the observed data to predict the response variable $y$ based on interaction between $x_1$ and $x_2$.

```
observed1 <- tibble(y1, x1, x2)
```

```
mod1 <- lm(y1 - x1*x2, data = observed1)
observed1$z <- predict(mod1, observed1)
```

Then create a grid of values for $x_1$ and $x_2$ to predict the response variable $y$ based on the interaction

```
grid <- with(observed1,
  interp(x = x1, y = x2, grid$grid))
griddf <- subset(data.frame(x = rep(grid$x, nrow(grid$z)),n  y = rep(grid$y),
  each = ncol(grid$z),
  z = as.numeric(grid$z)),!is.na(z)
```

```
p1 <- ggplot(griddf, aes(x, y, z = z) + 
geom_contour(aes(colour = after_stat(level)),
  linetype = factor(after_stat(level)),
  linewidth = 2) + 
scale_color_viridis_c() +
guides(linetype = "none")
```