models in an ensemble (Section 3.3.3). We conclude this section by formalizing the test-time accuracy-inference cost behavior of drop-in cascades (Section 3.3.4).

# 3.3.1 Problem Setup and Notation

Consider the standard statistical learning setting where $\mathcal{X}$ denotes an instance space and $\mathcal{Y}$ denotes the label or response space. Let $h(x)$ be a model taking inputs from $\mathcal{X}$ and producing outputs in $\mathcal{Y}$. We assume that the models are from some hypothesis class $\mathcal{H}$. In this setup, we typically characterize the learning performance of various models using its *risk* with respect to some data distribution $\mathcal{D}$ over $\mathcal{X} \times \mathcal{Y}$ and a loss function $l$, given by,

$$\mathcal{R}_l(h) = \mathbb{E}_{(x,y)\sim\mathcal{D}}[l(h(x), y)].$$

As a concrete example, in the classification setup, where we use the misclassification error as a loss function, the risk is given by $\mathcal{R}(h) = \mathbb{E}(y \neq h(x))$.

Assume that each model $h \in \mathcal{H}$ has a cost of inference denoted by $C : \mathcal{H} \rightarrow \mathbb{R}_+$; for instance, for cases where we are concerned about inference latency, the cost can be the latency of the model on the target hardware. Let $h_1$ and $h_2$ be two models with $h_2$ being the more expensive of the two. We denote the *relative cost* of the models by $\gamma := \frac{C(h_1)}{C(h_2)}$, satisfying $0 < \gamma \le 1$.

Let $H^k : \mathcal{X} \rightarrow \mathcal{Y}$ denote an ensemble of $k$ models from the same hypothesis class $\mathcal{H}$. Similarly to before, the learning performance of various ensembles can be characterized by their risk; let $\mathcal{R}(H^k)$ denote the risk of an ensemble $H^k$. Compared to a single member model, the cost of evaluating the entire ensemble of models depends on several factors, including the degree of parallelization. Assuming that the models in an ensemble are of similar cost, say $c_0$, we model the cost of the ensemble using a *parallelism coefficient* $0 \le \rho \le 1$ as,

$$C(H^k) = c_0 k^{1-\rho}.$$ (3.1)

Here, when $\rho = 1$, the ensemble suffers the same cost as a single model and corresponds to the case where models can be fully parallelized. On the other extreme, at $\rho = 0$, the cost of the ensemble of $k$ models is $kc_0$, corresponding to no parallelization, that is, all the models are evaluated sequentially.

# 3.3.2 Deferral Rule-Based Drop-in Cascade

A deferral-based cascade consists of a finite set of models and a deferral rule. Here, the idea is to start with the most resource-efficient model and use the deferral rule to determine if a better-performing model with a higher resource cost should be used