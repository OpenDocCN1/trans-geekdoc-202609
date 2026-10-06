# Ensemble methods: Bagging and boosting

At first glance, one might think that a bagging model (7.1) becomes more “complex” as the number of ensemble members B increase, and that we therefore run a risk of overfitting if we use many ensemble members B. However, there is nothing in (7.2) which indicate any such problem (bias remains low, variance decreases), and we confirm this by Example 7.3.

# Example 7.3: Bagging for regression (cont)

We consider the problem from Example 7.1, and explore how the model of bagging affects the “true” function value at $x_{*}$ and the predicted $\hat{y}_{bag}(x_{*})$ using different B. (Because of the bootstrap, there is a certain amount of randomness in the bagging algorithm itself. To avoid “noise”, we average the result over multiple runs of the bagging algorithm.

![](bbox=[0.142, 0.246, 0.796, 0.381])

Fig.-7.4 What we see in Figure 7.4 is that the squared error eventually reaches a plateau as $B 	o \infty$. Had there been an overfitting issue with $B 	o \infty$, the squared error would have started to increase again for large value of B.

Despite that the number of parameters in the model increases as B, the level of overfitting as $B 	o \infty$ according to Example 7.3 is the expected (and intended) behavior. It is important to understand that by the construction of bagging, *ensemble members do not make the resulting model more flexible*, but only reduce the variance. This is worth noting that the addition of an ensemble member is *not* done in order to obtain a better fit to the training data. On the contrary, each ensemble member overfits to its own perturbed version of the training data, averaging across the ensemble results in a smoothing effect which typically results in a larger training error (compared to the individual ensemble members' trainings), but also better generalization. We can also understand this by considering the limiting behavior as $B 	o \infty$. By the law of large numbers, the bagging model becomes

```
$\hat{y}_{bag}(x_{*}) = \frac{1}{B} \sum_{b=1}^{B} \hat{y}^{(b)}(x_{*}) \xrightarrow{B \to \infty} \mathbb{E}[\hat{y}(x_{*}) |\mathcal{T}]$
```

where the expectation is with respect to the randomness of the bootstrapping algorithm. As B increases we expect the bagging model to converge to the hypothetical (limited flexibility) model on the right hand side. With this in mind, in practice the choice of B is mainly made by computational constraints. The better the better, increasing B when there is no further reduction in test error is computationally wasteful.

**Be aware!** Bagging can still suffer from overfitting since each ensemble member can overfit. The only claim we have made is that the overfitting is not caused by B (not getting worse) using too many ensemble members, and,, there is no problem with taking $B \to \infty$.

# Out-of-bag error estimation

When bagging (or random forests, which we discuss below), it turns out that there is a way to estimate the new data error $E_{new}$ without cross-validation. The first observation we have to

the bootstrap might affect the bias, in that a base model trained on the original data might have a smaller bias than a model trained on a bootstrapped version of the training data. Most often, this is not an issue in practice.