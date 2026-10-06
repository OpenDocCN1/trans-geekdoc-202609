# CHAPTER 1. INTRODUCTION

# 33

# Train set a

# Train set b

![](bbox=[0.125, 0.137, 0.477, 0.283])

![](bbox=[0.523, 0.137, 0.874, 0.283])

![](bbox=[0.323, 0.486, 0.676, 0.501])

overfitting. That is, a model is so complex that it will fit a particular train set very well. Every time it is trained with a different train set, the *train error* will be low, but it will likely generate very different predictions for the same test points and a much higher *test error*. Figure 1.16 illustrates the relation between overfitting and high variance with a regression problem. Given a feature $x$, two models are trained to predict $y$: i) a *complex model* (top row), and ii) a *simpler model* (bottom row). Both models are fitted with two training sets (a and b) sampled from the same distribution. The complex model fits the train data perfectly but makes very different predictions (big $\Delta$) for the same test point when using a different train set. The simpler model does not fit the data well but has a smaller $\Delta$ and a lower error on the test point as well. Visually, the function (red curve) of the complex model also varies a lot across train sets whereas the wheases of the simpler model functions look very similar.

On the other hand, if a model is too simple, it will underfit causing *highly biased* results and not being able to capture the input-output relationships. This results in a high *train error* as well.