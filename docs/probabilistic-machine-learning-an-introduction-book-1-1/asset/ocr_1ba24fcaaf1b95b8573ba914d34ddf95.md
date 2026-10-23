# 3.7. *Mixture models*

+   - If the corruption is due to additive noise (as in Fig. [3.18a](#)), we can set **W** = **I**. The resulting MAP estimate can be used for **image denoising**, as in Fig. [3.18b](#).
+   - If the corruption is due to blurring (as in Fig. [3.18c](#)), we can set **W** to be a fixed convolutional kernel [KF09b]. The resulting MAP estimate can be used for **image deblurring**, as in Fig. [3.18d](#).
+   - If the corruption is due to occlusion (as in Fig. [3.18e](#)), we can set **W** to be a diagonal matrix, with 0s in the locations corresponding to the occluders. The resulting MAP estimate can be used for **image inpainting**, as in Fig. [3.18f](#).

Thus we see that the linear-Gaussian likelihood model is surprisingly flexible. Given the model, our goal is to invert it, by computing the MAP estimate $\hat{\mathbf{z}} = \arg\max_{\mathbf{z}} p(\mathbf{z}|\mathbf{y})$. However, the problem of inverting this model is ill-posed, since there are many possible latent images **z** that map to the same observed image **y**. Therefore we need to use a prior to regularize the inversion process.

In [ZWW11], they propose to use a GMM prior of the form $p(\mathbf{z}) = \sum_k p(c = k)\mathcal{N}(\mathbf{z}|\boldsymbol{\mu}_k, \boldsymbol{\Sigma}_k)$, using $K = 200$ mixture components, which they fit a dataset of 2M clean image patches. The full joint model therefore has the form

$$p(c = k, \mathbf{z}, \mathbf{y}|\boldsymbol{\theta}) = p(c = k)\mathcal{N}(\mathbf{z}|\boldsymbol{\mu}_k, \boldsymbol{\Sigma}_k)\mathcal{N}(\mathbf{y}|\mathbf{Wz}, \sigma^2\mathbf{I}) \tag{3.121}$$

To compute the marginal MAP estimate $\arg\max_{\mathbf{z}} p(\mathbf{z}|\mathbf{y})$, we can use the approximation

$$p(\mathbf{z}|\mathbf{y}) \approx p(\mathbf{z}|\mathbf{y}, c^*) \propto \mathcal{N}(\mathbf{z}|\boldsymbol{\mu}_{c^*}, \boldsymbol{\Sigma}_{c^*})\mathcal{N}(\mathbf{y}|\mathbf{Wz}, \sigma^2\mathbf{I}) \tag{3.122}$$

If we know $c^*$m we can compute the above using Bayes rule for Gaussians in Eq. (3.102). To compute the MAP mixture component, $c^*$, we can use Eq. (3.105) to get

$$c^* = \arg\max_c p(c) p(\mathbf{y}|c) = \arg\max_c p(c)\mathcal{N}(\mathbf{y}|\mathbf{W}\boldsymbol{\mu}_c, \sigma^2\mathbf{I} + \mathbf{W}\boldsymbol{\Sigma}_c\mathbf{W}^{\mathsf{T}}) \tag{3.123}$$

See Fig. 3.18 for some examples of this process in action.

If the corruption is not known, it is called a “blind inverse problem”, which is significantly harder. See e.g., [Ani+18; XC19; Wan+20c] for some relevant works.

# 3.7.2  Mixtures of Bernoullis

If the data is binary valued, we can use a **mixture of Bernoullis**, where each mixture component has the following form:

$$p(\mathbf{y}|\mathbf{z}=k,\boldsymbol{\theta}) = \prod_{d=1}^{D} \operatorname{Ber}(y_d|\mu_{dk}) = \prod_{d=1}^{D} \mu_{dk}^{y_d}(1-\mu_{dk})^{1-y_d} \tag{3.124}$$

Here $\mu_{dk}$ is the probability that bit $d$ turns on in cluster $k$.

For example, consider building an unsupervised density model for the famous **MNIST** dataset [LeC+98; YB19]. This is a dataset of 60k training images of size $28 \times 28 \times 1$ (the final dimension of size 1 means the images are gray scale) illustrating handwritten digits from 10 categories; see Fig. 3.19a for an illustration of the data. There are 60k training examples and 10k test examples.