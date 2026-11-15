applied to improve representation learning (Hjelm et al., 2019; Zhu et al., 2020a) given a dataset. However, for generating an adversarial example for a given data sample, the vanilla MINE is not applicable because it only applies to a batch of data samples (so that empirical data distributions can be used for computing MI estimates) but not to single data sample.

Per-sample MINE. Given a data sample $x$ and its perturbed sample $x + \delta$, we can construct an auxiliary distribution using their random samples or convolution outputs to compute MI via MINE as a similarity measure, denoted as “per-sample MINE”.

Random sampling. Using compressive sampling (Candès and Wakin, 2008), we perform independent Gaussian sampling of a given sample $x$ to obtain a batch of $K$ compressed samples $\{x_k, (x + \delta)_k\}_{k=1}^K$ for computing $I_\Theta(x, x + \delta)$ via MINE. We also note that random sampling is agnostic to the underlying machine learning model since it directly applies to the data sample.

Convolution layer output. When the underlying neural network model uses a convolution layer to process the input data (which is an almost granted setting for image data), we propose to use the output of the first convolution layer of a data input, denoted by conv, to obtain $K$ feature maps $\{conv(x)_k, conv(x + \delta)_k\}_{k=1}^K$ for computing $I_\Theta(x, x + \delta)$.

Unified attack formulation. We formalize the objectives for supervised and unsupervised adversarial examples using per-sample MINE. As summarized in Table 21.1, the supervised setting aims to find most similar examples causing prediction evasion, leading to an MINE maximization problem. The unsupervised setting aims to find least similar examples but having smaller training loss, leading to an MINE minimization problem. Both problems can be solved efficiently using a unified MinMax algorithm (Algorithm 7).

Supervised adversarial example. Let $(x, y)$ denote a pair of a data sample $x$ and its ground-truth label $y$. The objective of supervised adversarial example is to find a perturbation $\delta$ to $x$ such that the MI estimate $I_\Theta(x, x + \delta)$ is maximized while the prediction of $x + \delta$ is different from $y$ (or being a targeted class $y' \neq y$), which is formulated as

Maximize       $I_\Theta(x, x + \delta)$
such that $x + \delta \in [0, 1]^d, \delta \in [-\epsilon, \epsilon]^d$ and $f_x(x + \delta) \le 0. \quad (21.1)$

The constraint $x + \delta \in [0, 1]^d$ ensures that $x + \delta$ lies in the (normalized) data space of dimension $d$, and the constraint $\delta \in [-\epsilon, \epsilon]^d$ corresponds to the typical bounded $L_\infty$ perturbation norm. We include this bounded-norm