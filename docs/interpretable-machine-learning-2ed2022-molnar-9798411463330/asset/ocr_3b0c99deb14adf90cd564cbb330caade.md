# CHAPTER 8 LOCAL MODEL-AGNOSTIC METHODS

+   - Explain the prediction by interpreting the local model.

In the current implementations in $R^4$ and Python^5$, for example, linear regression can be chosen as interpretable surrogate model. In advance, you have to select $K$, the number of features you want to have in your interpretable model. The lower $K$, the easier it is to interpret the model. A higher $K$ potentially produces models with higher fidelity. There are several methods for training models with exactly $K$ features. A good choice is $Lasso$. A Lasso model with a high regularization parameter $\lambda$ yields a model without any feature. By retraining the Lasso models with slowly decreasing $\lambda$, one after the other, the features get weight estimates that differ from zero. If there are $K$ features in the model, you have reached the desired number of features. Other strategies are forward or backward selection of features. This means you start with the full model (= all features) or with a model with only the intercept and then test which feature would bring the biggest improvement when added or removed, until a model with $K$ features is reached.

How do you get the variations of the data? This depends on the type of data, which can be either text, image or tabular data. For text and images, the solution is to turn single words or super-pixels on or off. In the case of tabular data, LIME creates new samples by perturbing each feature individually, from a normal distribution with mean and standard deviation from the center.

# 8.2.1 LIME for Tabular Data

Tabular data is that comes in, with each row representing an instance and each column a feature. LIME samples are not taken around the instance of interest, but from the training data's mass center, which is problematic. But it increases the probability that the result for some the sample points predictions differ from the data point of interest and that LIME can learn at least some explanation.

It is best to visually explain sampling and local model training works:

As always, the devil is in the detail. Defining a meaningful neighborhood around a point is difficult. LIME uses an exponential smoothing kernel to define the neighborhood. A smoothing kernel measures proximity. A kernel width determines how the neighborhood is: A small kernel width means that an instance must be very close to the local model, a larger width means that instances that are farther away also influence the model. If you look at LIME's Python implementation (file lime/tabular.py) you will see that it uses an exponential smoothing kernel (on the normalized data) and the kernel width is 0.75 times the square root of the number of columns in the training data. It looks like innocent line of code, but it is like an elephant sitting in your living room next to the good porcelain you got from your grandparents. The big problem is that we do not have a way to find the best kernel or

> ^4https://github.com/thomasp85/lime
5https://github.com/marcotrc/lime
6https://github.com/marcotrc/tree/ce2bd6f20f47c3330beb107bb1fd25840ca4606