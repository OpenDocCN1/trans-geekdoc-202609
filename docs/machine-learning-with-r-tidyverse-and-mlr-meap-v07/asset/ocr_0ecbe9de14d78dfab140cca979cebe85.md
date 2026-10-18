> If I want to use linear modeling and the relationship between my predictors and outcome variable are non-linear, GAMs are my go-to model. This is because of their flexibility and their ability to overcome the limitations of polynomial regression. The exception to this is if there is theoretical reason to believe there is a specific polynomial relationship (say, quadratic) in the data. In such a situation using linear regression with a polynomial term may result in a simpler model, where a GAM might overfit.



So far, I’ve show you that GAMs learn non-linear relationships between our predictor variables, and our outcome. But what about when our predictor variables are categorical? Well GAMs can handle categorical variables in two different ways.

One method is to treat categorical variables in exactly the same way we do for the general linear model, and create k-1 dummy variables that encode the effect of each level of the predictor on the outcome. When we use this method, the predicted value of a case is simply the sum of all of the smoothing functions, plus the contribution from the categorical variable effects. This method assumes independence between the categorical variable, and the continuous variables (in other words, the smoothing functions are the same across each level of the categorical variable).

The other method is to model a separate smoothing function for each level of the categorical variable. This is important in situations where there are distinct non-linear relationships between continuous variables and the outcome, at each level of a categorical variable.

> When specifying a GAM as our learner through mlr, the default method is the first approach.

GAMs are extraordinarily flexible and powerful for a huge range of machine learning problems. If you would like to delve deeper into the nuts and bolts of GAMs, I would recommend Generalized Additive Models: An Introduction with R by Simon Wood (Chapman and Hall/CRC, 2017).

I hope by now you have a basic understanding of polynomial regression and GAMs, so let’s turn this knowledge into skills by building your first non-linear regression model!