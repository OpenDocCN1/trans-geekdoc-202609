# # Uninformative Gradients

![](bbox=[0.097, 0.165, 0.597, 0.458])

Perfectly 1

Perfectly 0

$\min_{G} \max_{D} \mathbb{E}_{P_x} \log D(x) + \mathbb{E}_{P_z} \log(1 - D(G(z)))$
n$\approx \mathbb{E}_{P_x} \log(1) + \mathbb{E}_{P_z} \log(1)$

Not very informative..

+   - Other GAN formulations exists that (partially) fix this problem
  - Wasserstein GAN