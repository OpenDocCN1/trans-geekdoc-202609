![](bbox=[0.129, 0.065, 0.871, 0.315])

When we have multiple predictors, a slope is estimated for each (using OLS), and the contributions of each variable are added together linearly, along with the model intercept (which is now the value of $y$ when each predictor = 0). The slopes in linear regression tell us how the outcome variable changes for a one-unit increase in each predictor, *while holding all other predictors constant*. In other words, the slopes tell us how the outcome changes when we change the predictor variables, one at a time. For example, our two-predictor cider model would look like this:

$$y = \beta_0 + \beta_{apples} \times apples + \beta_{fermentation} \times fermentation + \varepsilon$$

> **NOTE**
> 
> You will sometimes see linear regression with a single predictor and regression with multiple predictors described as *simple linear regression* and *multiple regression*, respectively. I find this distinction a little unnecessary however, as we rarely work with only a single predictor!

When we have two predictors, our line becomes a surface/plane. You can see this illustrated for our cider example in figure 9.4. When we have more than two predictors, our plane becomes a hyperplane. Indeed, our straight line equation can be generalized to any number of predictors as:

$$y = \beta_0 + \beta_1 x_1 + \beta_2 x_2 \ldots \beta_k x_k + \varepsilon$$

where there are $k$ predictors in the model. This is called the *general linear model*, and is the central equation to all linear models. If you’re coming from a traditional statistical modeling background, you may be familiar with $t$ tests and analysis of variance. These approaches all use the general linear model to represent the relationships between the predictor variables and the outcome.