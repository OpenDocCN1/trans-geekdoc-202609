> **NOTE** The general linear model is *not* the same as the *generalized linear model*, which refers to a class of models that allow different distributions for the outcome variable. I’ll talk about the generalized linear model soon.

![](bbox=[0.131, 0.173, 0.471, 0.406])

**Figure 9.4** Representing a linear model with two predictors. Combining apple content and fermentation time in our linear model can be represented as a surface. The solid lines show the residual error for each case (its vertical distance from the surface).

Do you recognize the general linear model? You saw something similar to it when we covered logistic regression in chapter 4. In fact, everything on the right-side of the equation is identical. The only difference is what was on the left-side of the equals sign. Recall that in logistic regression we predict the log odds of a case belonging to a particular class. In linear regression we simply predict the case’s value of the outcome variable.