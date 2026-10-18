> **SIDEBAR**
> 
> where *ln* is the natural logarithm and *p* (incorrect) is the proportion of incorrectly classified cases.
> 
> The case weights are calculated as:

# EQUATION 8.2

$$\text{case weight} = \begin{cases}\text{initial weight} \times e^{-\text{model weight}}, & \text{if correctly classified} \\ \text{initial weight} \times e^{\text{model weight}}, & \text{if incorrectly classified}\end{cases}$$

> **SIDEBAR**
> 
> This notation simply means for cases correctly classified, we use the formula on the top, and for cases incorrectly classified we use the formula on the bottom. Notice the only subtle difference is that the model weight is negative for cases that were correctly classified. Plug some numbers into these formulas. You’ll find the formula for correctly classified cases decreases their weight, while the formula for incorrectly classified cases increases it.

# LEARNING FROM THE PREVIOUS MODELS' RESIDUALS: GRADIENT BOOSTING

Gradient boosting is very similar to adaptive boosting, only differing in the way it corrects the mistakes of the previous models. Rather than weighting the cases differently depending on the accuracy of their classification, subsequent models try to predict the *residuals* of the previous ensemble of models.

A residual, or residual error, is the difference between the true value ("observed" value) and the value predicted by a model. This is easier to understand when thinking about predicting a continuous variable (regression). Imagine you’re trying to predict how much debt a person has. If an individual has a real debt of £2500, but our model predicts they have a debt of £2100, the residual is £400. It’s called a residual because it’s the error left over after the model has made its prediction.

It’s a bit harder to think of a residual for a classification model, but we can quantify the residual error of a classification model as:

+   - proportion of all cases incorrectly classified
+   - the *log loss*

The proportion of cases that were misclassified is pretty self-explanatory. The log loss is similar, but more greatly penalizes a model that makes incorrect classifications *confidently*. If your friend tells you with "absolute certainty" that Helsinki is the capital of Sweden (it’s not), you’d think