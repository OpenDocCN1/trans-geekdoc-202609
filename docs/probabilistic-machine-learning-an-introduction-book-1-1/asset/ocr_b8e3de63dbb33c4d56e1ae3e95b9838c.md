+   - **Well-calibrated probabilities.** Some generative classifiers, such as naive Bayes (described in Sec. [9.3](#)), make strong independence assumptions which are often not valid. This can result in very extreme posterior class probabilities (very near 0 or 1). Discriminative models, such as logistic regression, are often better calibrated in terms of their probability estimates, although they also sometimes need adjustment (see e.g., [NMC05]).

# 9.4.2 Advantages of generative classifiers

The main advantages of generative classifiers are as follows:

+   - **Easy to fit.** Generative classifiers are often very easy to fit. For example, in Sec. 9.3.2, we show how to fit a naive Bayes classifier by simple counting and averaging. By contrast, logistic regression requires solving a convex optimization problem (see Sec. 10.2.3 for the details), and neural nets require solving a non-convex optimization problem, both of which are much slower.

+   - **Can easily handle missing input features.** Sometimes some of the inputs (components of **x**) are not observed. In a generative classifier, there is a simple method for dealing with this, as we show in Sec. 9.4.3. However, in a discriminative classifier, there is no principled solution to this problem, since the model assumes that **x** is always available to be conditioned on.

+   - **Can fit classes separately.** In a generative classifier, we estimate the parameters of each class conditional density independently (as we show in Sec. 9.3.2), so we do not have to retrain the model when we add more classes. In contrast, in discriminative models, all the parameters interact, so the whole model must be retrained if we add a new class.

+   - **Can handle unlabeled training data.** It is easy to use generative models for semi-supervised learning, in which we combine labeled data \(D_{xy}=\{(x_n,y_n)\}\) and unlabeled data, \(D_x=\{x_n\}\). However, this is harder to do with discriminative models, since there is no uniquely optimal way to exploit \(D_x\).

# 9.4.3 Handling missing features

Sometimes we are missing parts of the input **x** during training and/or testing.

In a generative classifier, we can handle missing features that are missing at by marginalizing them out. (We assume that the missingness of a feature is not informative about its potential value.) For example, if we are missing the value of \(x_1\), we can compute

\[
p(y=c\mid x_{2:D},\theta) \propto p(y=c\mid\pi)\,p(x_{2:D}\mid y=c,\theta)
\tag{9.66}
\]
\[
= p(y=c\mid\pi)\sum_{x_1}p(x_1,x_{2:D}\mid y=c,\theta)
\tag{9.67}
\]

In Gaussian discriminant analysis, we can marginalize out \(x_1\) using the equations from Sec. 3.5.3. If we make the naive Bayes assumption, things are even easier, since we can just ignore the likelihood term for \(x_1\). This follows because

\[
\sum_{x_1}p(x_1,x_{2:D}\mid y=c,\theta)
=\left[\sum_{x_1}p(x_1\mid\theta_{1c})\right]\prod_{d=2}^{D}p(x_d\mid\theta_{dc})
=\prod_{d=2}^{D}p(x_d\mid\theta_{dc})
\tag{9.68}
\]