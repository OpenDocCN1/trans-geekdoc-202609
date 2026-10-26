> > Historically various ‘information criteria’ have been proposed that attempt to correct for the bias of maximum likelihood by the addition of a penalty term to compensate for the over-fitting of more complex models.
> >
> > — Page 33, *Pattern Recognition and Machine Learning*, 2006.

A benefit of probabilistic model selection methods is that a test dataset is not required, meaning that all of the data can be used to fit the model, and the final model that will be used for prediction in the domain can be scored directly. A limitation of probabilistic model selection methods is that the same general statistic cannot be calculated across a range of different types of models. Instead, the metric must be carefully derived for each model.

> > It should be noted that the AIC statistic is designed for preplanned comparisons between models (as opposed to comparisons of many models during automated searches).
> >
> > — Page 493, *Applied Predictive Modeling*, 2013.

A further limitation of these selection methods is that they do not take the uncertainty of the model into account.

> > Such criteria do not take account of the uncertainty in the model parameters, however, and in practice they tend to favour overly simple models.
> >
> > — Page 33, *Pattern Recognition and Machine Learning*, 2006.

There are three statistical approaches to estimating how well a given model fits a dataset and how complex the model is. And each can be shown to be equivalent or proportional to each other, although each was derived from a different framing or field of study.

They are:

+   - Akaike Information Criterion (AIC). Derived from frequentist probability.
+   - Bayesian Information Criterion (BIC). Derived from Bayesian probability.
+   - Minimum Description Length (MDL). Derived from information theory.

Each statistic can be calculated using the log-likelihood for a model and the data. Log-likelihood comes from Maximum Likelihood Estimation (introduced in Chapter 11), a technique for finding or optimizing the parameters of a model in response to a training dataset. In Maximum Likelihood Estimation, we wish to maximize the conditional probability of observing the data ($X$) given a specific probability distribution and its parameters ($\theta$), stated formally as:

$$P(X;\theta) \tag{15.1}$$

Where $X$ is, in fact, the joint probability distribution of all observations from the problem domain from 1 to $n$.

$$P(x_1,x_2,x_3,\ldots,x_n;\theta) \tag{15.2}$$