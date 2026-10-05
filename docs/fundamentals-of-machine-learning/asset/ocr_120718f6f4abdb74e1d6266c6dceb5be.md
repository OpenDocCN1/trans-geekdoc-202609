# 152 | Probabilistic regression and Bayes nets

![](bbox=[0.206, 0.114, 0.755, 0.283])

Fig. 7.5 Three distribution commonly used as priors for the parameters when learning with a maximum likelihood estimate.

```
$w^{MAP} = \text{argmax}_w \log(p(x, y|w)) + \alpha||w||^2,$ (7.52)
```

```
$\alpha = \log \frac{1}{2x^2}.$ (7.53)
```

Thus, we previously discussed $L^2$ regularization corresponds to a Gaussian prior on the weights. $L^1$ regularization corresponds to a prior of an isotropic Laplace distribution

```
$p(w) = \frac{1}{2b} \exp \left( -\frac{|w|}{b} \right),$ (7.54)
```

which is more peaked towards 0 as be seen by comparison of these distributions in Fig. 7.5. The $L^1$ regularization forces more weights towards 0 compared to the $L^2$ regularization. This is another example of how a probabilistic interpretation sheds some light on techniques that have been originally introduced heuristically. A simple summary of the three priors and their resulting equivalence between MLE and MAP is shown in the table on the right of the figure.

Finally, we have discussed the common quantities of MAP and MLE in machine learning, it is good to realize that learning methods only give a **point estimate**, a single answer for the most likely values of the parameters given a specific data set from which likelihood has to be estimated. A point estimate is used to make decisions about which actions to take. However, it is possible that other sets of parameter value might only have a smaller likelihood value, and it is therefore more prudent to consider other values. For example, looking again at the example in Fig. 7.4, another strategy might be to pick a weight value in a range where variations in this value would not change the probability considerably in some range, such as values around $w_0$.

Moreover, in a Bayesian sense, all choices should be taken into account with their corresponding likelihood. This is particularly true when estimating our confidence for an estimation. In a Bayesian sense, we need to combine all possible estimates with their likelihood. Thus, a limit of the maximum estimation methods discussed earlier, which are dominating most of the current practices in machine