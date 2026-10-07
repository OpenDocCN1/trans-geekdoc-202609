possible values of x, you always get 1, but if you integrate the likelihood function over all possible values of $	heta$, the result can be any positive value.

![](bbox=[0.252, 0.131, 0.747, 0.335])

Figure 9-20. A model parametric function (top left), and some derivatives: a PDF (lower left), a likelihood function (top right) and a log likelihood function (lower right)

Given a dataset **X**, a common task is to estimate the most likely values for the model parameters. To do this, you must find the values that maximize the likelihood function, given **X**. In example, if you observed a single instance $x=2.5$, the *maximum likelihood estimate* (MLE) of $	heta$. If a prior probability distribution $g$ over $	heta$, it is possible to take it into account by maximizing $l(\theta)g(\theta)$ rather than just maximizing $l(\theta)$. This is called maximum a-posteriori (MAP) estimation. Since MAP constraints the parameter values, you can think of it as a regularized version of MLE.

Notice that it is equivalent to maximize the likelihood function or to maximize its logarithm (represented in the lower right hand side of **Figure 9-20**); indeed, the logarithm is a strictly increasing function, so if $	heta$ maximizes the log likelihood, it maximizes the likelihood. It turns out that it is much easier to maximize the log likelihood, if you observed independent instances $x^{(1)}$ to $x^{(n)}$, you would need to find the value of $	heta$ that maximizes the product of the individual likelihood functions. It is equivalent, and much simpler, to maximize the sum (not product) of the log likelihood functions, thanks to the magic of the logarithm which converts products into sums: $\log(ab)=\log(a)+\log(b)$.

Once you have estimated $\theta$, the value of $\theta$ that maximizes the likelihood function, then you are ready to compute the AIC and BIC: $L = l(\theta, \mathbf{X})$. This is the value which is used to compute of it as a measure of how well the model fits the data.

To compare the AIC and BIC, just call the $bic(\cdot)$ or $aic(\cdot)$ methods: