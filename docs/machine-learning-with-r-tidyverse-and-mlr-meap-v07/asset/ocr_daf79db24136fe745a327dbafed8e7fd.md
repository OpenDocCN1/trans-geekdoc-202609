![](bbox=[0.157, 0.074, 0.674, 0.219])

**Figure 11.1 Underfitting and overfitting in classification.** Examples of underfitting, optimal fitting, and overfitting are shown for a two-class classification problem. The dotted line represents a decision boundary.

Now take a look at the example in figure 11.2, which shows an example of what under and overfitting looks like for regression problems. When we underfit the data, we miss local differences in the relationship and produce a model that has high bias (makes inaccurate predictions). When we overfit the data, our model is too sensitive to local differences in the relationship and produce a model that has high variance (will make very variable predictions on new data).

> > **NOTE**  
> > The example I’ve used to labor this point is of a non-linear relationship, but the sample applies to models of linear relationships too.

![](bbox=[0.16, 0.539, 0.735, 0.698])

**Figure 11.2 Underfitting and overfitting in regression.** Examples of underfitting, optimal fitting, and overfitting are shown for a single predictor regression problem. The dotted line represents the regression line.

The principal job of regularization is to prevent algorithms from learning models that are overfit by discouraging complexity. This is achieved by penalizing model parameters that are large, shrinking them towards zero. This might sound counterintuitive; surely the model parameters learned by ordinary least squares (OLS from chapter 9) are the best as they minimize the residual error? The problem is that this is only necessarily true for the training set, and not the test set.

Consider the example in figure 11.3. In the left-side plot, imagine we only measured the two