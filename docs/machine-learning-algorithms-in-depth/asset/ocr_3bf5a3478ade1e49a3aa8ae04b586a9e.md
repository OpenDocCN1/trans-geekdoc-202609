# 7.4.1 Bayesian optimization

Rather than exploring the parameter space randomly (according to a chosen distribution), it would be great to adopt an active learning approach that selects continuous parameter values in a way that reduces uncertainty and provides a balance between exploration and exploitation. Bayesian optimization provides an automated Bayesian framework by utilizing Gaussian processes (GPs) to model the algorithm’s generalization performance (see Jasper Snoek, Hugo Larochelle, and Ryan P. Adams’s “Practical Bayesian Optimization of Machine Learning Algorithms,” Conference and Workshop on Neural Information Processing Systems, 2012).

Bayesian optimization assumes that a suitable performance function was sampled from a GP and maintains a posterior distribution for this function as observations are made: f(x) ~ GP(m(x), κ(x, x′)). To choose which hyperparameters to explore next, one can optimize the expected improvement (EI) over the current best result or the Gaussian process upper confidence bound (UCB). EI and UCB have been shown to be efficient in the number of function evaluations required to find the global optimum of multimodal black-box functions.

Bayesian optimization uses all the information available from previous evaluations of the objective function, as opposed to relying on the local gradient and Hessian approximations. This results in an automated procedure that can find an optimum of non-convex functions with relatively few evaluations, at the cost of performing more computation to determine the next point to try. This is particularly useful when evaluations are expensive to perform, such as in selecting hyperparameters for deep neural networks. The Bayesian optimization algorithm is summarized in figure 7.12.

```
1: for n = 1, 2, ... do
2:   select new x_{n+1} by optimizing acquisition function α
3:     x_{n+1} = arg max_x α(x; D_n, θ)
4:   query objective function to obtain y_{n+1} = f(x_{n+1})
5:   augment data D_{n+1} = {D_n, (x_{n+1}, y_{n+1})}
6:   update GP posterior and acquisition function
7: end for
```

# Figure 7.12 Bayesian optimization algorithm

The following listing applies Bayesian Optimization for hyperparameter search in SVM and random forest classifier (RFC).

# Listing 7.7 Bayesian optimization for SVM and RFC

```
import numpy as np
import pandas as pd

import seaborn as sns
import matplotlib.pyplot as plt

from sklearn.datasets import make_classification
from sklearn.model_selection import cross_val_score
```