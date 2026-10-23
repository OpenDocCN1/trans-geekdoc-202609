# A.8.1 Supervised learning

For supervised learning, we denote the observed features (also called inputs or **covariates**) by **x** ∈ 𝒳. Often 𝒳 = ℝ^D, meaning the features are real-valued. (Note that this includes the case of discrete-valued inputs, which can be represented as one-hot vectors.) Sometimes we compute manually-specified features of the input; we denote these by φ(**x**). We also have outputs (also called **targets** or **response variables**) **y** ∈ 𝒴 that we wish to predict. Our task is to learn a conditional probability distribution p(**y**|**x**, **θ**), where **θ** are the parameters of the model. If 𝒴 = {1,…,C}, we call this **classification**. If 𝒴 = ℝ^C, we call this **regression** (often C = 1, so we are just predicting a scalar response).

The parameters **θ** are estimated from **training data**, denoted by 𝒟 = {(**x**_n, **y**_n) : n ∈ {1,…,N}} (so N is the number of training cases). If 𝒳 = ℝ^D, we can store the training inputs in an N × D **design matrix** denoted by **X**. If 𝒴 = ℝ^C, we can store the training outputs in an N × C matrix **Y**. If 𝒴 = {1,…,C}, we can represent each class label as a C-dimensional bit vector, with one element turned on (this is known as a **one-hot encoding**), so we can store the training outputs in an N × C binary matrix **Y**.

# A.8.2 Unsupervised learning and generative models

Unsupervised learning is usually formalized as the task of unconditional density estimation, namely modeling p(**x**|**θ**). In some cases, we want to perform conditional density estimation; we denote the values we are conditioning on by **c**, so the model becomes p(**x**|**c**, **θ**). This is similar to supervised learning, except that **x** is usually high dimensional (e.g., an image) and **c** is usually low dimensional (e.g., a class label or a text description).

In some models, we have **latent variables**, also called **hidden variables**, which are never observed in the training data. We call such models **latent variable models** (LVM). We denote the latent variables for data case n by **z**_n ∈ 𝒵. Sometimes latent variables are known as **hidden variables**, and are denoted by **h**_n. By contrast, the **visible variables** will be denoted by **v**_n. Typically the latent variables are continuous or discrete, i.e., 𝒵 = ℝ^L or 𝒵 = {1,…,K}.

Most LVMs have the form p(**x**_n, **z**_n|**θ**); such models can be used for unsupervised learning. However, LVMs can also be used for supervised learning. In particular, we can either create a generative (unconditional) model of the form p(**x**_n, **y**_n, **z**_n|**θ**), or a discriminative (conditional) model of the form p(**y**_n, **z**_n|**x**_n, **θ**).

# A.8.3 Bayesian inference

When working with Bayesian inference, we write the prior over the parameters as p(**θ**|φ), where φ are the hyperparameters. For conjugate models, the posterior has the same form as the prior (by definition). We can therefore just update the hyperparameters from their prior value, 	ilde{φ}, to their posterior value, \hat{φ}.

In variational inference (Sec. 7.7.3), we use **ξ** to represent the parameters of the variational posterior, i.e., p(**θ**|𝒟) ≈ q(**θ**|**ξ**). We optimize the ELBO wrt **ξ** to make this a good approximation.

When performing Monte Carlo sampling, we use a s subscript or superscript to denote a sample (e.g., **θ**_s or **θ**^s).