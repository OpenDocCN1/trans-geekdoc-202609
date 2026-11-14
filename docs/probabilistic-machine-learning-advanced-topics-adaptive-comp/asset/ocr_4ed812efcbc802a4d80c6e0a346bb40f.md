as well as for avoiding overfitting. To compute the uncertainty, we will perform Bayesian inference of the parameters. To do this, we we first need to specify a prior. Choosing a suitable prior depends on the form of link function. For example, a “flat” or “uninformative” prior on the offset term $\alpha \in \mathbb{R}$ will not translate to an uninformative prior on the probability scale if we pass $\alpha$ through a sigmoid, as we discuss in Section 15.3.4. Once we have chosen the prior, we can compute the posterior using a variety of approximate inference methods. For small datasets, HMC (Section 12.5) is the easiest to use, since you just need to write down the log likelihood and log prior; we can then use autograd to compute derivatives which can be passed to the HMC engine (see e.g., [BG13] for details).

There are many standard software packages for HMC analysis of (hierarchical) GLMs, such as Bambi (https://github.com/bambinos/bambi), which is a Python wrapper on top of PyMC/BlackJAX, RStanARM (https://cran.r-project.org/web/packages/rstanarm/index.html), which is an R wrapper on top of Stan, and BRMS (https://cran.r-project.org/web/packages/brms/index.html), which is another R wrapper on top of Stan. These libraries support a convenient formula syntax, initially created in the R language, for compactly specifying the form of the model, including possible interaction terms between the inputs.

For large datasets, HMC can be slow, since it is a full batch algorithm. In such settings, variational Bayes (see e.g., [HOW11; TN13]), expectation propagation (see e.g., [KW18]), or more specialized algorithms (e.g., [HAB17]) are the best choice.

# 15.2 Linear regression

Linear regression is the simplest case of a GLM, and refers to the following model:

$p(y|x, \theta) = \mathcal{N}(y|w_0 + w^T x, \sigma^2)$ (15.39)

where $\theta = (w_0, w, \sigma^2)$ are all the parameters of the model. (In statistics, the parameters $w_0$ and $w$ are usually denoted by $\beta_0$ and $\beta$.) We gave a detailed introduction to this model in the prequel to this book, [Mur22]. In this section, we briefly discuss maximum likelihood estimation, and then focus on a Bayesian analysis.

# 15.2.1 Ordinary least squares

From Equation (15.39), we can derive the negative log likelihood of the data as follows:

$NLL(w, \sigma^2) = - \sum_{n=1}^N \log \left[ \left( \frac{1}{2\pi\sigma^2} \right)^{\frac{1}{2}} \exp \left( - \frac{1}{2\sigma^2} (y_n - w^T x_n)^2 \right) \right]$ (15.40)

$= \frac{1}{2\sigma^2} \sum_{n=1}^N (y_n - \hat{y}_n)^2 + \frac{N}{2} \log(2\pi\sigma^2)$ (15.41)

where we have defined the predicted response $\hat{y}_n \triangleq w^T x_n$. In [Mur22, Sec 11.2.2] we show that the MLE is given by

$\hat{w}_{mle} = (X^T X)^{-1} X^T y$ (15.42)