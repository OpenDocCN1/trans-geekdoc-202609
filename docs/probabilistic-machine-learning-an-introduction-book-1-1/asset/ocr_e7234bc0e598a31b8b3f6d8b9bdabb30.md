![](bbox=[0.35, 0.12, 0.68, 0.27])

Figure 17.17: Log-odds vs x for 3 different methods. Adapted from Figure 10 of [Tip01]. Used with kind permission of Mike Tipping.

We also need to kernelize the bias term. This can be done by kernelizing Eq. (17.119) as follows:

$\hat{w}_0 = \frac{1}{|\mathcal{S}|} \sum_{i\in\mathcal{S}} \left( \tilde{y}_i - \left(\sum_{j\in\mathcal{S}} \hat{\alpha}_j \tilde{y}_j \mathbf{x}_j \right)^\top \mathbf{x}_i \right) = \frac{1}{|\mathcal{S}|} \sum_{i\in\mathcal{S}} \left( \tilde{y}_i - \left(\sum_{j\in\mathcal{S}} \hat{\alpha}_j \tilde{y}_j \mathcal{K}(\mathbf{x}_j, \mathbf{x}_i) \right) \right)$ (17.131)

The kernel trick allows us to avoid having to deal with an explicit feature representation of our data, and allows us to easily apply classifiers to structured objects, such as strings and graphs.

# 17.5.5 Converting SVM outputs into probabilitues

An SVM classifier produces a hard-labeling, $\hat{y}(\mathbf{x}) = \operatorname{sign}(f(\mathbf{x}))$. However, we often want a measure of confidence in our prediction. One heuristic approach is to interpret $f(\mathbf{x})$ as the log-odds ratio, $\log \frac{p(y=1|\mathbf{x})}{p(y=0|\mathbf{x})}$. We can then convert the output of an SVM to a probability using

$p(y=1|\mathbf{x},\boldsymbol{\theta}) = \sigma\big(a f(\mathbf{x}) + b\big)$ (17.132)

where $a$, $b$ can be estimated by maximum likelihood on a separate validation set. (Using the training set to estimate $a$ and $b$ leads to severe overfitting.) This technique was first proposed in [Pla00], and is known as Platt scaling.

However, the resulting probabilities are not particularly well calibrated, since there is nothing in the SVM training procedure that justifies interpreting $f(\mathbf{x})$ as a log-odds ratio. To illustrate this, consider an example from [Tip01]. Suppose we have 1d data where $p(x|y=0)=\text{Unif}(0,1)$ and $p(x|y=1)=\text{Unif}(0.5,1.5)$. Since the class-conditional distributions overlap in the $[0.5,1]$ range, the log-odds of class 1 over class 0 should be zero in this region, and infinite outside this region. We sampled 1000 points from the model, and then fit a probabilistic kernel classifier (an RVM, described in Sec. 17.6.1) and an SVM with a Gaussian kernel of width 0.1. Both models can perfectly capture the decision boundary, and achieve a generalization error of 25%, which is Bayes optimal in this problem. The probabilistic output from the RVM is a good approximation to the true log-odds, but this is not the case for the SVM, as shown in Fig. 17.17.