![](bbox=[0.3, 0.09, 0.7, 0.26])

Figure 25.13: Combining a VAE with a diffusion model. Here E and D are the encoder and decoder of the VAE. The diffusion model conditions on the inputs either by using concatenation or by using a cross-attention mechanism. From Figure 3 of [Rom+22]. Used with kind permission of Robin Rombach.

```
Algorithm 25.3: Standard training
Input: Model \(\hat{x}_\theta(z_t)\) to be trained
Input: Dataset \(\mathcal{D}\)
Input: Loss weight function \(w\)
1 while not converged do
    2 \(x \sim \mathcal{D}\)
    3 \(t \sim \text{Unif}(0, 1)\)
    4 \(\epsilon \sim \mathcal{N}(\mathbf{0}, \mathbf{I})\)
    5 \(z_t = \alpha_t x + \sigma_t \epsilon\)
    ...
    6 \(\tilde{x} = x\) (Clean data is target)
    7 \(\lambda_t = \log(\alpha_t^2 / \sigma_t^2)\) (Log SNR)
    8 \(L_\theta = w(\lambda_t) \|\tilde{x} - \hat{x}_\theta(z_t)\|_2^2\)
    9 \(\theta := \theta - \gamma \nabla_\theta L_\theta\)
```

```
Algorithm 25.4: Progressive distillation
Input: Trained teacher model \(\hat{x}_\eta(z_t)\)
Input: Dataset \(\mathcal{D}\)
Input: Loss weight function \(w\)
Input: Student sampling steps \(N\)
1 foreach \(K\) iterations do
    2 \(\theta := \eta\) (Assign student)
    3 while not converged do
    4 \(x \sim \mathcal{D}\)
    5 \(t \sim \text{Cat}(1, 2, \dots, N)\)
    6 \(\epsilon \sim \mathcal{N}(\mathbf{0}, \mathbf{I})\)
    7 \(z_t = \alpha_t x + \sigma_t \epsilon\)
    8 \(t' = t - 0.5/N, \quad t'' = t - 1/N\)
    9 \(z_{t'} = \alpha_{t'} \hat{x}_\eta(z_t) + \frac{\sigma_{t'}}{\sigma_t} (z_t - \alpha_t \hat{x}_\eta(z_t))\)
    10 \(z_{t''} = \dots\)
    11 \(\tilde{x} = \dots\) (Teacher is target)
    12 \(\lambda_t = \log(\alpha_t^2 / \sigma_t^2)\)
    13 \(L_\theta = w(\lambda_t) \|\tilde{x} - \hat{x}_\theta(z_t)\|_2^2\)
    14 \(\theta := \theta - \gamma \nabla_\theta L_\theta\)
    15 \(\eta := - \theta\) (Student becomes next teacher)
    16 \(N := N/2\) (Halve number of sampling steps)
```

# 25.5.4 Latent space diffusion

Another approach to speeding up diffusion models for images is to first embed the images into a lower dimensional space, and then fit the diffusion model to the embeddings. This idea has been pursued in several papers. In the latent diffusion model (LDM) of [Rom+22], they adopt a two-stage training scheme, in which they first fit the VAE, augmented with a perceptual loss, and then fit the diffusion model to