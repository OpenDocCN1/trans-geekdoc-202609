
are designed for these respective tasks. Even for a specific task such as denoising, model-based methods (e.g., BM3D (Dabov et al., 2007) and WNNM (Gu et al., 2014)) can handle different noise levels, whereas the learning-based method of (Jain and Seung, 2009) separately trains a different model for each level. As a result, these two categories of methods have their respective merits and drawbacks, and thus it would be attractive to investigate their integration to leverage their respective merits.

The integration of model-based methods and learning-based methods has resulted in the deep plug-and-play IR method which replaces the denoising subproblem of model-based optimization with the learning-based CNN denoiser prior. The main idea of deep plug-and-play IR is that, with the aid of variable splitting algorithms, such as the alternating direction method of multipliers (ADMM) (Boyd et al., 2011) and half-quadratic splitting (HQS) (Geman and Yang, 1995), it is possible to deal with the data term and prior term separately (Parikh et al., 2014), and particularly, the prior term only corresponds to a denoising subproblem (Danielyan et al., 2010; Heide et al., 2014; Venkatakrishnan et al., 2013) which can be solved via a deep CNN denoiser. Hence, one can treat the deep plug-and-play method as a special case of model-based methods.

Apart from deep plug-and-play methods, deep unfolding methods can also integrate model-based methods and learning-based methods. Their main difference is that the latter optimize the parameters in an end-to-end manner by minimizing the loss function over a large training set, and thus generally produce better results even with fewer iterations. Mathematically, the deep unfolding method can be modeled as

$$\begin{cases}\min_{\theta} \sum_{i=1}^{N} \mathcal{L}(\hat{\mathbf{x}}_i, \mathbf{x}_i) & \text{(14.4a)} \\ s.t.\ \hat{\mathbf{x}}_i = \arg\min_{\mathbf{x}} \frac{1}{2\sigma^2}\|\mathbf{y}_i - (\mathbf{x} \otimes \mathbf{k}) \downarrow_s\|^2 + \lambda \mathcal{R}(\mathbf{x}). & \text{(14.4b)}\end{cases}$$

In other words, the deep unfolding method aims to replace the predefined function Eq. (14.3b) with the unfolding inference Eq. (14.4b), thus one can treat it as a special case of learning-based methods. The main idea of deep unfolding IR is to first unfold the model-based energy function via a half-quadratic splitting algorithm to obtain an inference which iteratively alternates between solving two subproblems, one related to a data term and the other to a prior term, and then to treat the inference as a deep network, by replacing the solutions to the two subproblems with neural modules. Since the two subproblems correspond respectively to enforcing degradation consistency knowledge and guaranteeing denoiser prior knowledge, the deep unfolding method is well-principled with explicit degradation and prior constraints, which is a distinctive advantage over plain learning-based SISR methods. Fig. 14.1 shows an illustration of the connections between learning-based methods, model-based methods, deep plug-and-play methods, and deep unfolding methods.

The rest of this chapter is organized as follows. Since both deep plug-and-play and deep unfolding methods are highly related to variable splitting algorithms, we thus first introduce one of the most popular ones, i.e., the half quadratic splitting (HQS) algorithm, in Section 14.2. We then present the deep plug-and-play image restoration methods in Section 14.3. Specifically, we propose a highly flexible and effective CNN denoiser prior and then plug the deep denoiser prior as a modular part into the HQS algorithm to solve various image restoration problems. In Section 14.4, we provide the deep unfolding image restoration methods which can handle deblurring and superresolution with different blur kernels and scale factors via a single model. Section 14.5 shows the quantitative and qualitative results and also provides a thorough analysis of hyper-parameter setting and intermediate results to better understand the working mechanism of deep plug-and-play methods and deep unfolding methods.

![](img/fe161b7f6e96e35e7e853eece52c6dce_504_0.png)

FIGURE 14.1 An illustration of the connections between learning-based methods, model-based methods, deep plug-and-play methods, and deep unfolding methods.

## 14.2 Half quadratic splitting (HQS) algorithm

Although there exist various variable splitting algorithms to solve Eq. (14.2), the half-quadratic splitting (HQS) algorithm owes its popularity to simplicity and fast convergence. We therefore adopt HQS in this chapter. Typically, HQS tackles Eq. (14.2) by introducing an auxiliary variable z, leading to the following approximate equivalence

$E_{\mu}(\mathbf{x}, \mathbf{z}) = \frac{1}{2\sigma^2} \|\mathbf{y} - (\mathbf{z} \otimes \mathbf{k}) \downarrow_{\mathbf{s}} \|^2 + \lambda \Phi(\mathbf{x}) + \frac{\mu}{2} \|\mathbf{z} - \mathbf{x}\|^2, \qquad (14.5)$

where $\mu$ is the penalty parameter. Such a problem can be addressed by iteratively solving subproblems for $\mathbf{x}$ and $\mathbf{z}$

$\begin{cases} \mathbf{z}_k = \arg\min_{\mathbf{z}} \|\mathbf{y} - (\mathbf{z} \otimes \mathbf{k}) \downarrow_{\mathbf{s}} \|^2 + \mu \sigma^2 \|\mathbf{z} - \mathbf{x}_{k-1} \|^2, & (14.6) \\ \mathbf{x}_k = \arg\min_{\mathbf{x}} \frac{\mu}{2} \|\mathbf{z}_k - \mathbf{x}\|^2 + \lambda \Phi(\mathbf{x}). & (14.7) \end{cases}$

According to Eq. (14.6), $\mu$ should be large enough so that $\mathbf{x}$ and $\mathbf{z}$ are approximately equal to the fixed point. However, this would also result in slow convergence. Therefore, a good rule of thumb is to iteratively increase $\mu$. For convenience, in the $k$-th iteration $\mu$ is denoted by $\mu_k$.

It can be observed that the data term and the prior term are decoupled into Eq. (14.6) and Eq. (14.7), respectively. For the solution of Eq. (14.6), the fast Fourier transform (FFT) can be utilized by assuming the convolution is carried out with circular boundary conditions. Notably, it has a closed-form expression (Zhao et al., 2016)

$$\mathbf{z}_k = \mathcal{F}^{-1}\left(\frac{1}{\alpha_k}\left(\mathbf{d} - \overline{\mathcal{F}(\mathbf{k})} \odot_s \frac{(\mathcal{F}(\mathbf{k})\mathbf{d}) \Downarrow_s}{(\overline{\mathcal{F}(\mathbf{k})}\mathcal{F}(\mathbf{k})) \Downarrow_s + \alpha_k}\right)\right), \tag{14.8}$$

where d is defined as

$$\mathbf{d} = \overline{\mathcal{F}(\mathbf{k})}\mathcal{F}(\mathbf{y} \uparrow_s) + \alpha_k \mathcal{F}(\mathbf{x}_{k-1})$$

with $\alpha_k \triangleq \mu_k \sigma^2$ and where the $\mathcal{F}(\cdot)$ and $\mathcal{F}^{-1}(\cdot)$ denote FFT and inverse FFT, $\overline{\mathcal{F}(\cdot)}$ denotes the complex conjugate of $\mathcal{F}(\cdot)$; $\odot_s$ denotes the distinct block processing operator with element-wise multiplication, i.e., applying element-wise multiplication to the $s\times s$ distinct blocks of $\overline{\mathcal{F}(\mathbf{k})}$; $\Downarrow_s$ denotes the distinct block downsampler, i.e., averaging the $s\times s$ distinct blocks; $\uparrow_s$ denotes the standard $s$-fold upsampler, i.e., upsampling the spatial size by filling the new entries with zeros. For the special case of deblurring when $s = 1$, Eq. (14.8) can be concisely written as

$$\mathbf{z}_k = \mathcal{F}^{-1}\left(\frac{\overline{\mathcal{F}(\mathbf{k})}\mathcal{F}(\mathbf{y}) + \alpha_k \mathcal{F}(\mathbf{x}_{k-1})}{\overline{\mathcal{F}(\mathbf{k})}\mathcal{F}(\mathbf{k}) + \alpha_k}\right). \tag{14.9}$$

In other words, Eq. (14.8) generalizes Eq. (14.9). For the solution of Eq. (14.7), it is known that, from a Bayesian perspective, it actually corresponds to a denoising problem with noise level $\beta_k \triangleq \sqrt{\lambda/\mu_k}$ (Chan et al., 2017).

## 14.3 Deep plug-and-play image restoration

Plug-and-play IR generally involves two steps. The first step is to decouple the data term and prior term of the objective function via a certain variable splitting algorithm, resulting in an iterative scheme consisting of alternately solving a data subproblem and a prior subproblem. The second step is to solve the prior subproblem with any off-the-shelf denoisers, such as K-SVD (Elad and Aharon, 2006), nonlocal means (Buades et al., 2005), BM3D (Dabov et al., 2007). As a result, unlike traditional model-based methods, which need to specify the explicit and hand-crafted image priors, plug-and-play IR can implicitly define the prior via the denoiser. Such an advantage offers the possibility of leveraging a very deep CNN denoiser to improve effectiveness.

The plug-and-play IR can be traced back to Danielyan et al. (2010); Zoran and Weiss (2011); Venkatakrishnan et al. (2013). Danielyan et al. (2012) used Nash equilibrium to derive an iterative decoupled deblurring BM3D (IDDBM3D) method for image deblurring. In Egiazarian and Katkovnik (2015), a similar method equipped with CBM3D denoiser prior was proposed for single image superresolution (SISR). By iteratively updating a back-projection step and a CBM3D denoising step, the method has an encouraging performance for its PSNR improvement over SRCNN (Dong et al., 2016). In Danielyan et al. (2010), the augmented Lagrangian
