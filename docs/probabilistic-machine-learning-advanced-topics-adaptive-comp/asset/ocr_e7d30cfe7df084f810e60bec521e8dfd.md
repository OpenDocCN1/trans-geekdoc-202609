![](bbox=[0.15, 0.1, 0.85, 0.3])

Figure 19.4: Illustration of the 4 main kinds of distribution shift for a 2d binary classification problem. Adapted from Figure 1 of [al21].

The decision about which model to use depends on our assumptions about the underlying data generating process. For example, suppose X is a medical image, and Y is an image segmentation created by a human expert or an algorithm. If we change the image, we will change the annotation, and hence X -> Y. Now suppose X is a medical image and Y is the ground truth disease state of the patient, as estimated by some other means (e.g., a lab test). In this case, we have Y -> X, since changing the disease state will change the appearance of the image. As another example, suppose X is a text review of a movie, and Y is a measure of how informative the review is. Clearly we have X -> Y. Now suppose Y is the star rating of the movie, representing the degree to which the user liked it; this will affect the words that they write, and hence Y -> X.

Based on the above discussion, we can factor the joint distribution in two possible ways. One way is to define a discriminative model:

```
$p_{\boldsymbol{\theta}}(\boldsymbol{x}, \boldsymbol{y}) = p_{\boldsymbol{\psi}}(\boldsymbol{x}) p_{\boldsymbol{w}}(\boldsymbol{y} | \boldsymbol{x})$ (19.1)
```

See Figure 19.3a. Alternatively we can define a generative model:

```
$p_{\boldsymbol{\theta}}(\boldsymbol{x}, \boldsymbol{y}) = p_{\boldsymbol{\pi}}(\boldsymbol{y}) p_{\boldsymbol{\phi}}(\boldsymbol{x} | \boldsymbol{y})$ (19.2)
```

See Figure 19.3b. For each of these 2 models model types, different parts of the distribution may change from source to target. This gives rise to 4 canonical type of shift, as we discuss in Section 19.2.3.

# 19.2.3 The four main types of distribution shift

The four main types of distribution shift are summarized in Section 19.2 and are illustrated in Figure 19.4. We give more details below (see also [LP20]).

# 19.2.3.1 Covariate shift

In a causal (discriminative) model, if $p_{\psi}(\boldsymbol{x})$ changes (so $\boldsymbol{\psi}^s \neq \boldsymbol{\psi}^t$), we call it **covariate shift**, also called **domain shift**. For example, the training distribution may be clean images of coffee pots, and