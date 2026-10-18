
In this section, I’ll show you how we can take the general linear model we learned about in the previous chapter, and extend it to include non-linear, polynomial relationships between predictor variables and the outcome variable.

Linear regression makes the strong assumption that there is a linear relationship between predictor variables and the outcome. Sometimes real-world variables do have linear relationships, or can be sufficiently approximated by one, but often they are not. So surely the general linear model falls down when faced with non-linear relationships, right? After all, it’s called the general linear model and uses the equation of a straight line. Well, it turns out that the general linear model is surprisingly flexible, and that we can use it to model polynomial relationships.

Recall from high school math, that a polynomial equation is just an equation with multiple terms (single numbers or variables). If all the terms in the equation are raised to the power of 1 (an exponent of 1), in other words they are all equal to themselves, the equation is a first degree polynomial. If the highest exponent in the equation is 2, in other words one or some of the terms are squared but there are no higher exponents, the equation is a second degree polynomial or quadratic polynomial. If the highest exponent is 3, the equation is a cubic polynomial, and if the highest exponent is 4, the equation is a quartic polynomial.

> Although there are names for higher degree polynomials, people usually just call them “nth degree” polynomials. This is, of course, unless you want to sound super precocious!

1. y = x¹ (linear)
2. y = x² (quadratic)
3. y = x³ (cubic)
4. y = x⁴ (quartic)

The shape of these functions is shown for values of x between -30 and 30 in figure 10.1. When the exponent is 1, the function is a straight line, but when the exponent is greater than one, the function is curvy.

![](img/a22105d68c35e8d5bd3c7bafb4644881_251_0.png)

Figure 10.1 Shapes of polynomial functions from the first to the fourth degree. When the x variable is raised to the first power, the equation models a straight line. As we increase the power that x is raised to, the equations model lines with varying degrees of flexibility.

We can use this to our advantage: if the relationships between our predictor variables and our outcome variable have a curved relationship, we might be able to model this relationship by including nth degree polynomials in our model definition.

Think back to our cider example in the last chapter. Imagine that instead of a linear relationship between apple content and cider batch pH, we have a downward curvilinear relationship like the one illustrated in figure 10.2. A straight line no longer models this relationship very well, and predictions made by such a model are likely to have high bias. Instead, we can better model this relationship by including a quadratic term in our model definition.

![](img/a22105d68c35e8d5bd3c7bafb4644881_251_1.png)

Figure 10.2 Comparing the fit of linear and quadratic fits to an imaginary non-linear relationship between apple content and cider acidity.

The formula for the model shown in figure 10.2 would be:

$$y = \beta_{apples} \times apples + \beta_{apples^2} \times apples^2 + \epsilon$$

where $\beta_{apples^2}$ is the “slope” for the $apples^2$ term, which is more easily understood as how much the line curves as apple content increases (larger absolute values result in a more extreme curve). For a single predictor variable, we can generalize this for any $n^{th}$ degree polynomial relationship as:

$$y = \beta_0 + \beta_1 x + \beta_2 x^2 + \ldots + \beta_n x^n + \epsilon$$

where $n$ is the highest degree of polynomial you’re modeling. Notice that when performing polynomial regression, it’s usual to include all the lower degree terms for that predictor variable as well. For example, if you’re modeling a quartic relationship between two variables, you would include $x$, $x^2$, $x^3$ and $x^4$ terms in your model definition. Why is this? If we don’t include the lower-degree terms in the model, the *vertex* of the curve, the part of it that flattens out (either at the top or bottom of the curve, depending on which direction it curves), is forced to pass through $x = 0$. This might be a reasonable constraint to place on the model, but it usually isn’t. Instead, if we include the lower degree terms in the model, the curve doesn’t need to pass through $x = 0$ and can “wiggle around” more to (hopefully) fit the data better. This is illustrated in figure 10.3.

![](img/a22105d68c35e8d5bd3c7bafb4644881_252_0.png)

**Figure 10.3 Comparing the shape of polynomial functions that do and do not include the first degree term.** Vertical dotted lines indicate the position of each function’s vertex on the x axis.

Just like we saw in the last chapter, when the model is given new data, it multiplies the values of the predictor variables (including the specified exponents) by their slopes, then adds them all together with the intercept to get the predicted value. The model we’re using is still the general linear model, because we’re *linearly* combining the model terms (adding them together).

## 10.2 When we need even more flexibility: splines and generalized additive models

When using polynomial terms in linear regression, the higher the degree of polynomial we use the more flexible our model will be. High-degree polynomials allow us to capture complicated non-linear relationships in the data, but are therefore more likely to overfit the training set. Sometimes, increasing the degree of the polynomials doesn’t help anyway, as the relationship between predictor variable and outcome variable may not be the same across the range of the predictor variable. In such situations, instead of using high-degree polynomials, we can use *splines*. In this section I’ll explain what splines are, how we can use them, and how they relate to polynomials and a set of models called *generalized additive models* (GAMs).

A spline is a *piecewise* polynomial function. This means that it splits the predictor variable up into regions, and fits a separate polynomial within each region, which connect to each other via *knots*. A knot is a position along the predictor variable that divides the regions within which the separate polynomials are fit. The polynomial curves in each region of the predictor pass through the knots that delimit that region. This allows complex non-linear relationships that are not constant across the range of the predictor variable to be modeled. This is illustrated in figure 10.4 using our cider example.

![](img/a22105d68c35e8d5bd3c7bafb4644881_253_0.png)

**Figure 10.4 Fitting a spline to a non-linear relationship. The solid dots indicate the knots. Individual polynomial functions fit the data between the knots and connect to each other through them.**

Using splines is a great way of modeling complicated relationships such as the one shown in figure 10.4, but has some limitations:

- the position and number of the knots need to be chosen manually. Both choices can make a big impact on the shape of the spline. The choice of knot position is typically either at obvious regions of change in the data, or at regular intervals across the predictor, such as at the quartiles.
- the degree of the polynomials between knots needs to be chosen. We usually use cubic splines or higher, because these ensure that the polynomials connect with each other smoothly through the knots (quadratic polynomials may leave the spline disconnected at the knots!).
- it can become difficult to combine splines of different predictors together.

So can we do better than simple spline regression? Absolutely. The solution is *generalized additive models* (GAMs). GAMs extend the general linear model such that instead of:

$$y = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \ldots + \beta_k x_k + \epsilon$$

they take the form:

$$y = \beta_0 + f_1(x_1) + f_2(x_2) + \ldots + f_k(x_k) + \epsilon$$

where each $f(x)$ represents a function of a particular predictor variable. These functions can be any sort of smoothing function, but will typically be a combination of multiple splines.

> **NOTE** Can you see that the general linear model is a special case of the generalized additive model, where the function for each predictor variable is the *identity function* ($f(x) = x$)? We can go one step further then and say that the *generalized linear model* is a special case of the *generalized additive model*. This is because we can also use different link functions with GAMs that allow us to use them to predict categorical variables (as in logistic regression) or count variables.

### 10.2.1 How do GAMs learn their smoothing functions

The most common method of constructing these smoothing functions is to use splines as *basis functions*. Basis functions are simple functions that can be combined to form a more complex function. Take a look at figure 10.5. The non-linear relationship between the x and y variables is modelled as a weighted sum of three splines. In other words, at each value of x, we sum the contributions from each of these basis functions to give us the function that models the relationship (the dotted line). The overall function is a *weighted sum* because each basis function has a corresponding weight, determining how much it contributes to the final function.
