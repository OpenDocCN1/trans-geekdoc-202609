
Finding Stable Vision Concept Transformers. Motivated by [5], we propose a method called Denoised Diffusion Smoothing (DDS) to obtain SVCTs. The process is as follows: we use randomized smoothing to the VCT and then apply a denoised diffusion probabilistic model to the perturbed input. With this processing, we can transform a VCT into an SVCT, and its corresponding concept module becomes a stable concept module. Specifically, for a given input image x, its corresponding token embedding is X. We add some randomized Gaussian noise to X, i.e., \(\tilde{X} = X + S\), where \(S \sim \mathcal{N}(0, \sigma^2 I_{d_{model} \times n})\). Then we will use some denoised diffusion models to denoise \(\tilde{X}\) to get \(\hat{X}\). We then take the obtained \(\hat{X}\) as a new input to get concept feature \(f_c(\hat{X})\) in (1) and go through the remaining structures of the VCT to get the final prediction.

Specifically, for a given input X, randomized smoothing is done by augmenting the data points of an image by adding additive Gaussian noise to the image, which we can denote as \(X_{rs} \sim \mathcal{N}(X, \sigma^2 \mathbf{I})\). Diffusion models rely on a particular form of noise modeling, denoted as \(X_t \sim \mathcal{N}(\sqrt{\beta_t}X, (1-\beta_t)\mathbf{I})\). Where \(\beta_t\) is a constant related to time step t. Thus, if we want to use a diffusion model for randomized smoothing, we need to establish a link between the parameters of the two noise models. The DDS model used in this paper multiplies \(X_{rs}\) by the factor \(\sqrt{\beta_t}\), thus satisfying the requirement of the noise mean, and accordingly, in order to satisfy the requirement of the variance, we can obtain the equation \(\sigma^2 = \frac{1-\beta_t}{\beta_t}\). As the time step changes, \(\sigma^2\) changes as \(\beta_t\) changes because \(\beta_t\) is a constant with respect to the time step. But it can be computed at every time step, and by using this, we are able to obtain \(X_{t^*} = \sqrt{\beta_{t^*}}(X + S)\), where \(S \sim \mathcal{N}(0, \sigma^2 \mathbf{I})\). Such a form of noise is consistent with the form on which the diffusion model depends, and we can use the diffusion model on \(X_{t^*}\) to obtain denoised sample \(\hat{X} = \text{denoise}(X_{t^*}; t^*)\). In this paper, we repeat this process several times to improve robustness.

In the following, we show that \(\tilde{w} = f_c(\hat{X})\) is a stable concept feature satisfying Definition 2 if \(\sigma^2\) satisfies some condition. Before showing the results, we first provide some notations. For input image x, we denote \(\tilde{w}_{i*}\) as the i-th largest component in \(\tilde{w}(x)\). Let \(k_0 = \lfloor(1-\beta)k\rfloor + 1\) as the minimum number of changes on \(\tilde{w}(x)\) to make it violate the \(\beta\)-top-k overlapping ratio with \(\tilde{w}(x)\). Let S denote the set of last \(k_0\) components in top-k indices and the top \(k_0\) components out of top-k indices. Then, we can prove the following upper bound. The details of the algorithm are in Algorithm 1.

```
Algorithm 1. SVCTs via Denoised Diffusion Smoothing

1: Input: X; A standard deviation \(\sigma > 0\).
2: \(t^*\), find t s.t. \(\frac{1-\beta_t}{\beta_t} = \sigma^2\).
3: \(X_{t^*} = \sqrt{\beta_{t^*}}(\tilde{X} + \mathcal{N}(0, \sigma^2 \mathbf{I}))\).
4: \(\hat{X} = \text{denoise}(X_{t^*}; t^*)\).
5: \(w = f_c(\hat{X})\), where \(f_c\) is in (1).
6: Return: Concept feature vector w.
```

**Theorem 2.** Consider the function \(\tilde{w}(X) = f_c(T(X + S))\), where \(f_c\) as the function in \((1)\), \(T\) as the denoised diffusion model and \(S \sim \mathcal{N}(0, \sigma^2 I_{d_{model} \times n})\). Then, it is an \((R, D_\alpha, \gamma, \beta, k, \| . \|_2)\)-stable concept module for VCTs for any \(\alpha > 1\) if for any input image \(x\) we have

```
\(\sigma^2 \ge \max\{\alpha R^2/2(\frac{\alpha}{\alpha-1}\ln(2k_0(\sum_{i\in S}\tilde{w}_i^{*\alpha})^{\frac{1}{\alpha}}+\)
\((2k_0)^{\frac{1}{\alpha}}\sum_{i\notin S}\tilde{w}_{i^+}-\frac{1}{\alpha-1}\ln(2k_0)),\alpha R^2/2\gamma\}.\)
```

![](img/f56761e6196132d5b74909d98468408f_387_0.png)

**Fig. 3.** Results of concept visualization. From left to right: one sample from each dataset, concept visualization results before perturbation, and concept visualization results after perturbation. Clear and enlarged pictures are shown in the Appendix L.

## 4 Experiments

### 4.1 Experimental Settings

**Datasets.** We conducted experiments on four medical datasets, including Human Against Machine with 10,015 training images (HAM10000) dataset [19], Covid19-CT dataset [25], BloodMNIST dataset [22], and Optical coherence tomography (OCT) 2,017 dataset [9]. Details are in Appendix G.

| Method | HAM10000 | Covid19-CT | BloodMNIST | OCT2017 |
| :--- | :--- | :--- | :--- | :--- |
| Standard (No interpretability) | 99.13% | 81.62% | 97.05% | 99.70% |
| Label-Free CBM (LF-CBM) | 93.61% | 79.75% | 94.97% | 97.50% |
| Post-hoc CBM (P-CBM) | 97.60% | 76.26% | 94.83% | 98.60% |
| Vision Concept Transformer (VCT) | 99.00% | 80.62% | 96.21% | 99.10% |
| Stable VCT (SVCT) | 99.05% | 81.37% | 96.96% | 99.50% |
| $\rho_u = 8/255$ - LF-CBM | 90.08% | 67.98% | 80.53% | 91.88% |
| $\rho_u = 8/255$ - P-CBM | 90.96% | 70.66% | 77.55% | 91.70% |
| $\rho_u = 8/255$ - VCT | 95.80% | 69.78% | 89.45% | 96.80% |
| $\rho_u = 8/255$ - SVCT | 97.97% | 74.45% | 94.07% | 98.70% |
| $\rho_u = 10/255$ - LF-CBM | 88.70% | 65.12% | 75.63% | 90.58% |
| $\rho_u = 10/255$ - P-CBM | 90.21% | 66.32% | 74.27% | 90.10% |
| $\rho_u = 10/255$ - VCT | 95.28% | 68.85% | 87.71% | 96.25% |
| $\rho_u = 10/255$ - SVCT | 97.24% | 71.65% | 92.65% | 98.48% |

Baselines. In this paper, the standard model is ViT [3], which accomplishes the classification task by extracting image features, but the model itself is not interpretable. The baseline model is label-free CBM [15], which uses ViT as the backbone to generate a conceptual bottleneck layer and finally makes predictions through a linear layer.

| Method | HAM10000 CFS | HAM10000 CPCS | Covid19-CT CFS | Covid19-CT CPCS | BloodMNIST CFS | BloodMNIST CPCS | OCT2017 CFS | OCT2017 CPCS |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| $\rho_u = 6/255$ - LF-CBM | 0.3335 | 0.9405 | 0.6022 | 0.8117 | 0.5328 | 0.8511 | 0.3798 | 0.9254 |
| $\rho_u = 6/255$ - VCT | 0.3361 | 0.9394 | 0.6761 | 0.7650 | 0.5432 | 0.8436 | 0.3625 | 0.9314 |
| $\rho_u = 6/255$ - SVCT | 0.1354 | 0.9900 | 0.5555 | 0.8359 | 0.3589 | 0.9320 | 0.3257 | 0.9468 |
| $\rho_u = 8/255$ - LF-CBM | 0.3719 | 0.9256 | 0.6707 | 0.7710 | 0.6280 | 0.7947 | 0.3941 | 0.9196 |
| $\rho_u = 8/255$ - VCT | 0.4109 | 0.9098 | 0.8114 | 0.6743 | 0.7162 | 0.7328 | 0.3812 | 0.9240 |
| $\rho_u = 8/255$ - SVCT | 0.1555 | 0.9867 | 0.6446 | 0.7818 | 0.4383 | 0.8977 | 0.3459 | 0.9387 |
| $\rho_u = 10/255$ - LF-CBM | 0.4027 | 0.9123 | 0.7224 | 0.7336 | 0.6906 | 0.7545 | 0.4055 | 0.9145 |
| $\rho_u = 10/255$ - VCT | 0.4637 | 0.8844 | 0.8943 | 0.6155 | 0.8057 | 0.6670 | 0.3949 | 0.9179 |
| $\rho_u = 10/255$ - SVCT | 0.1725 | 0.9836 | 0.7096 | 0.7389 | 0.5058 | 0.8625 | 0.3620 | 0.9321 |

Perturbations. Perturbation refers to small changes or modifications made to input data. In this paper, we introduce perturbations to input images with different radius $\rho_u$ to assess the stability and robustness of the SVCT model. The range of perturbation radii \(\rho_u\) is [6/255, 10/255]. We employ the PGD [13] algorithm to craft adversarial examples with a step size of 2/255 and a total of 10 steps. As a default, we set the standard deviation \(S = 8/255\) for the Gaussian noise in our method. All results are the average score running 10 times to reduce variance.

**Evaluation Metrics.** To demonstrate the utility of our approach, we report the classification accuracy on test data for classification tasks. We evaluate our model's stability using Concept Faithfulness Score (CFS) and Concept Perturbation Cosine Similarity (CPCS). CFS measures the stability of model interpretability between two concept weight vectors using Euclidean distance; we use \(c_1\) to represent the concept weight vector without perturbation and \(c_2\) to represent the concept weight vector after the perturbation. Then CFS is defined as \(\text{CFS} = ||c_2 - c_1|| / ||c_1||\). CPCS measures the cosine similarity between two concept weight vectors, which is defined as \(\text{CPCS} = c_1 \cdot c_2 / ||c_1|| ||c_2||\). The smaller the value of CFS, the less the conceptual weights change after being perturbed, and the more stable the model interpretability is. The closer the value of CPCS is to 1, the higher the similarity of conceptual weights before and after perturbation and the more stable interpretability of the model. More experimental details are in the Appendix G.

![](img/f56761e6196132d5b74909d98468408f_389_0.png)

### 4.2 Utility Evaluation

Table 1 presents the accuracy results of our proposed SVCT method and the baseline approach on four datasets with different levels of perturbations. The table clearly shows that our method maintains a consistently high accuracy across all datasets without any noticeable variation or loss. This highlights the robustness of our approach in terms of accuracy preservation. Compared to Label-free CBM, our model can maintain higher accuracy while guaranteeing
