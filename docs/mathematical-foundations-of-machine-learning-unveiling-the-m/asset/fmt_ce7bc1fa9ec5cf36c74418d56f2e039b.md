
# Statistical Learning Framework

“Statistical learning” is a descriptive statistics-based learning framework categorized as supervised or unsupervised. “Supervised statistical learning” involves constructing a statistical model to predict or estimate output based on single or multiple inputs. In contrast, “unsupervised statistical learning” involves inputs without supervisory output, helping in learning data relationships and structure. Understanding statistical learning involves identifying the connection between the “predictor” (independent variables, attributes) and the “response” (dependent variable) to produce a model capable of predicting the “response variable (Y)” based on “predictor factors (X).”

![](image-n46qvym7.jpg)

`X = f(X) + ɛ where X = (X1,X2, . . .,Xp)`, where `f` is an `unknown function` & `ɛ` is `random error (reducible & irreducible)`.

Here are some fundamental concepts of Statistical Learning:

## Prediction and Inference

When there are several easily accessible inputs `X`, but the output `B` production is unknown, `f` is often treated as a black box, provided that it generates accurate predictions for `Y`. This is called `prediction`. There are circumstances in which we need to understand how `Y` is influenced as `X` changes. We want to estimate `f` in this scenario, but our objective is not simply to generate predictions for `Y`. In this situation, we want to establish and better understand the connection between `Y` and `X`. Now, `f` is not regarded as a black box since we have to understand the underlying process of the system. This is called `inference`. In everyday life, various issues can be categorized into the setting of `predictions`, the setting of `inferences`, or a `hybrid` of the two.

## Parametric and Non-parametric Techniques

The `parametric technique` can be defined as an evaluation of `f` by calculating the set parameters (a finite summary of the data) while establishing an assumption about the functional form of `f`. The mathematical equation of this technique is `f(X) = β0 + β1X1 + β2X2 + . . . + βpXp`. The `parametric models` tend to have a finite number of parameters independent of the size of the data set. This is also known as `model-based learning`. For example, `k-Gaussian models` are driven by the parametric technique.

![](image-o1tcq7i3.png)

On the other hand, the `non-parametric technique` generates an estimation of `f` based on its closeness to the data points, without making any assumptions on the functional form of `f`. The `non-parametric models` tend to have a varying number of parameters that grow proportionally with the size of the data set. This is also known as `memory-based learning`. For example, `kernel density models` are driven by a non-parametric technique.

## Predictions Accuracy and Model Interpretability

Some of the many methods used to learn from statistical data are less adaptable and extremely restrictive. When `inference` is the target, the use of easy and comparatively inflexible techniques of statistical learning has significant benefits. On the other hand, if the target is the generation of forecasts and predictions, flexible models are preferred.

The performance of the model can be estimated based on its accuracy in predicting the occurrence of an event on new input data. A more accurate model is deemed more valuable. Interpretability of the model offers insight into the input-output relationship. An interpreted model can provide insight into the capability of independent features to generate predictions for the dependent attribute. The problem occurs because, at the expense of interpretability, as model accuracy improves, so does the complexity of the model.

A more accurate model can offer a business more possibilities, advantages, time, or money. But the model accuracy needs to be optimized for such prediction. The optimization of accuracy extends the complexity of the model even further by introducing additional model parameters (and resources needed to adjust those parameters). It is much easier and quicker to interpret a model with a relatively small number of parameters. An input coefficient and an intercept term are part of a linear regression model. For instance, every single term can be explored to assess how it contributes to the production of the output. Switching to a logistic regression model provides greater authority in the context of the relationships underlying the potential transformation of a function to output, and that too should be explored along with the coefficients.

It is relatively easy to understand a decision tree of small size, but a heavily loaded decision tree needs a distinct perspective to understand why the event is predicted to occur. Furthermore, the optimized combination of several models into one prediction tends to have no significant or timely interpretation. Interpretation is deemed ancillary to model accuracy.

For example, models designed to separate and classify `spam` emails from `non-spam` emails, as well as models designed to evaluate the price of real estate.

![](image-1xuvbx4f.jpg)
