# Modeling data with a linear model

Linear models are a type of statistical model used to analyze the relationship between a dependent variable and one or more independent variables. In essence, they seek to find a line that describes the relationship between these variables, allowing us to make predictions about the dependent variable based on the values of the independent variables. The equation for a simple linear model can be written as:

```
$y = \beta_0 + \beta_1x + \epsilon$$
```

where $y$ is the dependent variable, $x$ is the independent variable, $\beta_0$ and $\beta_1$ are coefficients that represent the intercept and slope of the line, respectively, and $\epsilon$ is the error term.

The output of a linear model typically includes the coefficients of the model, which describe the strength and direction of the relationship between the variables, as well as measures of the model's goodness of fit, such as the R-squared value.

Linear models have many applications in bioinformatics, including gene expression analysis, where linear models can be used to identify genes that are differentially expressed between two or more conditions, such as healthy and diseased tissues. Quantitative trait analysis where linear models can be used to identify genetic variants that are associated with complex traits, such as height or disease risk, and Metabolomics where linear models can be used to identify metabolites that are associated with a particular biological process or disease state based on their levels in biological samples.

In this recipe, we will look at putting together a linear model for numerous variables and examining the quality of the model to assess whether it is going to be useful.

# Getting ready

For this recipe, we will need the built-in `PlantGrowth` dataset, which describes plants' weights under different treatment regimes.

# How to do it...

We follow a quite terse set of commands. Building the model is one of R's strengths and is extremely easy to do:

+   1. Load in and look at a summary of the `PlantGrowth` data:
n```r
summary("PlantGrowth")nsummary(PlantGrowth)
```

+   2. Specify a linear model for expression based on the other variables:
```r
model_1 <- lm(weight - group, data = PlantGrowth)
summary(model_1)
```