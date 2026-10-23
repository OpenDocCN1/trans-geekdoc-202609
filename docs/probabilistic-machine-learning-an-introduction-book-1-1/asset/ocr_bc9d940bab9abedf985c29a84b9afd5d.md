![](bbox=[0.33, 0.17, 0.78, 0.33])

Figure 19.22: Combining self-supervised learning on unlabeled data (left), supervised fine-tuning (middle), and self-training on pseudo-labeled data (right). From Figure 3 of [Che+20c]. Used with kind permission of Ting Chen

with parameters θ, from the data space X to the latent space Z. The density in data space can be written starting from the density in the latent space using the change of variables formula:

$p(x) = p(f(x)) \cdot \left| \det\left(\frac{\partial f}{\partial x}\right) \right|$  (19.58)

We can extend this to semi-supervised learning, as proposed in [Izm+20]. For class labels y ∈ {1…C}, we can specify the latent distribution, conditioned on a label k, as Gaussian with mean μ_k and covariance Σ_k: p(z|y = k) = N(z|μ_k, Σ_k). The marginal distribution of z is then a Gaussian mixture. The likelihood for labeled data is then

$p_X(x|y = k) = \mathcal{N}(f(x)|\mu_k, \Sigma_k) \cdot \left| \det\left(\frac{\partial f}{\partial x}\right) \right|$  (19.59)

and the likelihood for data with unknown label is $p(x) = \sum_k p(x|y = k)p(y = k)$.

For semi-supervised learning we can then maximize the joint likelihood of the labeled D_l and unlabeled data D_u:
$p(\mathcal{D}_\ell, \mathcal{D}_u|\theta) = \prod_{(x_i,y_i)\in\mathcal{D}_\ell} p(x_i, y_i) \prod_{x_j\in\mathcal{D}_u} p(x_j),$  (19.60)

over the parameters θ of the bijective function f, which learns a density model for a Bayes classifier. Given a test point x, the model predictive distribution is given by
$p_X(y|x) = \frac{p(x|y)p(y)}{p(x)} = \frac{\mathcal{N}(f(x)|\mu_y, \Sigma_y)}{\sum_{k=1}^C \mathcal{N}(f(x)|\mu_k, \Sigma_k)}.$  (19.61)

We can make predictions for a test point x with the Bayes decision rule $y = \arg\max_{c\in\{1,...,C\}} p(y = c|x)$.

# 19.6.7 Combining self-supervised and semi-supervised learning

It is possible to combine self-supervised and semi-supervised learning. For example, [Che+20c] using SimCLR (Sec. 19.2.3.3) to perform self-supervised representation learning on the unlabeled data, they