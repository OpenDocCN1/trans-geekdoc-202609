# # Chapter 1

# # Regression, Validation

# ## 1.1 Regression

Our goal in machine learning is to extract a *relationship* from data. In **regression** tasks, the relationship takes the form of a function $y = f(\mathbf{x})$, where $y \in \mathbb{R}$ is some quantity that can be predicted from an input $\mathbf{x} \in \mathbb{R}^d$, which should for the time being thought of as some collection of numerical measurements. The true relationship $f$ is unknown, and our aim is to recover it as well as we can from data. Our end product is a function $\hat{h}(\mathbf{x})$, called the **hypothesis**, which should approximate $f$. We assume that we have access to a dataset $\mathcal{\mathcal{D}} = \{(\mathbf{x}_i, y_i)\}_{i=1}^n$; where each pair $(\mathbf{x}_i, y_i)$ is an example (possibly noisy or otherwise) of the input-output mapping to be learned. Since learning arbitrary functions is intractable, we restrict ourselves to some **hypothesis class** $\mathcal{H}$ of allowable functions. we typically employ a **parametric model**, meaning that there is some finite-dimensional vector $\mathbf{w} \in \mathbb{R}^d$, the elements of which are known as **parameters** or **weights**, that controls the behavior of the function. That is,

> $h_{\mathbf{w}}(\mathbf{x}) = g(\mathbf{x})$$

for other function $g$. The hypothesis is the set of all functions induced by the possible choices of the parameters $\mathbf{w}$:

> $\mathcal{H} = \{h_{\mathbf{w}} \mid \mathbf{w} \in \mathbb{R}^d\}$

After designating a **cost function** $L$, which measures how poorly the prediction $\hat{y}$ of the hypothesis match the true output $y$, we can proceed to search for the parameters that best fit the data by minimizing this function:

> $\mathbf{w}^* = \arg \min_{\mathbf{w}} L(\mathbf{w})$$

# ## 1.2 Ordinary least squares

Ordinary least squares is one of the simplest regression problems, but it is well-understood and practically useful. It is a **linear regression** problem, which means that we take $h_{\mathbf{w}}(\mathbf{x}) = \mathbf{x}^T \mathbf{w}$. We want

> $y_i \approx \hat{y}_i = h_{\mathbf{w}}(\mathbf{x}_i) = \mathbf{x}_i^T \mathbf{w}$