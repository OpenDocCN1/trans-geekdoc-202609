# Weight space view – GPs as Bayesian Learning Models

So why are GPs an instance of Bayesian Learning?

+   - We can also derive GPs from the Bayesian Linear Regression view
- Kernelized version of Bayesian Linear Regression (with infinite dimensional feature spaces)

So back to Bayesian linear regression....

+   - Likelihood (conditional): $p(y|X,w)=\mathcal{N}(y|\Phi w,\sigma_{y}^{2}I)$n- Prior (marginal): $p(w)=\mathcal{N}(w|\mathbf{0},\lambda^{-1}I)$n- Dimensions: $w\in\mathbb{R}^{d}$ and $Y\in\mathbb{R}^{N	imes1}$, high/infinite dimensional features $d \gg N$

As the dimensionality of the marginal variable (parameter vector) is now larger than dimensionality of cond. Variable (number of samples), we have to use Gaussian Bayes rule 1