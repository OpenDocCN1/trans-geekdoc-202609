
# Deep generative models for recommender systems 125

Note at time $t-1$, user's latent feature is $u_{t-1}$. And LSTM computes $u_t$ based on $u_{t-1}$ and $t-1$ so as to capture the evolution of user preferences. Similarly, the input to the LSTM is a set of users given this item and the latent representation of items $v_i$ can be calculated using LSTM. To handle the changing user and item features, RRRN also assumes that users have static features, which are denoted as $u_i$ and $m_i$. In with user $i$'s dynamic latent feature $u_{it}$ and static latent features $u_i$, the item $j$'s dynamic latent feature $v_{jit}$ and static latent features $v_{jt}$, the rating is predicted as:

```
$\hat{r}_{jit} = u_{it}^T v_{jit} + u_i^T v_{jt}$
```

The objective function is to learn the weights of LSTMs and the static latent features to make $r_{jit}$ close to the ground truth.

## 6.4 Deep generative models

The CTR (Section 6.2.4) is a robust model that integrates LDA and PMF into a unified framework for recommendation. Being said, the performance of CTR strongly depends on the representation capability of the LDA topic model. Unfortunately, the latent representation learned by LDA is not effective when the auxiliary information is very sparse. The previous section showed that DL models are extremely good in learning the representations of data. When it comes to recommendation, PMF and its variants still reign as the state-of-the-art techniques due to their ability to capture and learn implicit relationship between items (and users) [32]. This necessitates the integration of generative and DL models to create a unified framework that can provide the best of both worlds. To this, we introduce two most recent papers on generative DL, CDAE [13] and CVAE [14].

### 6.4.1 Collaborative denoising autoencoders

The CDAE [13] is a hierarchical Bayesian model that bridges the gap between generative models and DL for recommendation. Figure 6.8 shows the graphical structure of CDAE, which is composed of two parts: (a) a stacked DAE (AAE) [33] and (b) the PMF component. The DAE is a feedforward neural network for learning representations (or encoding) of the input data. Similar to AEs, the DAE has an input layer, a hidden layer, and an output layer. The difference between these two models lies in the input layer, where, in DAE, the input is corrupted before passed to the network. The AE is then trained to reconstruct the original corrupted version. Figure 6.8(a) shows the graphical structure of CDAE and (b) explains that $W$ denotes the weights of the neural network, $X_c$ is the corrupted data (i.e., the input layer) and $X_0$ is the original data of $J \times S$, $J$ is the number of items and $S$ is the size of vocabulary. The input $X$ is usually textual contents of items such as product reviews and images. $l$ indicates a specific layer of the neural network, $L$ is the total number of layers and $\{g_1, \dots, g_L\}$ are the intermediate layers (the function approximators) of the SDAE. The item-latent vector $v$, the user latent-vector $u$ and the observed rating $R$ are same as CTR. Algorithm 3 lines 1–9 illustrate the DAE block (i.e., the orange box in Figure 6.8) and lines 10–19 illustrate the PMF block. Here, $X_{0j}^*$ indicates the bag of words of an item $j$, and $gt_{lj}^*$ is the row of the latent $g_l$. Essentially, CDAE follows the same generative principle as the CTR that was discussed in Algorithm 2. One key difference is that, instead of LDA, the CDAE uses a DAE to embed the content information of items in a latent space (i.e., lines 11–12). One can observe that the content of the latent vector $v_i$ is drawn from $g_{l/2}$, which is the middle layer of SDAE. The objective of CDAE is defined as follows:

```
$$\arg \min_{W_{bi}} \|X_0 - X_iW_{bi}\|_F^2 + \lambda \sum_j \frac{\lambda_w}{j} \|W_{ij}\|^2$$
```

where $W_{bi}$ is the regularization parameter and $\|\cdot\|_F$ is the Frobenius norm. Similar to CTR, the posterior $P(U, V|X)$ is derived using MAP estimate:

```
$$\arg \min_{W_{bi}} \|X_0 - X_iW_{bi}\|_F^2 + \lambda \sum_j \frac{\lambda_w}{j} \|W_{ij}\|^2 \quad$$
```

![](img/6d0ce7dba01af52e1c2fae47d5b04a05_142_0.png)

The item-latent vector $v$, the user latent-vector $u$ and the observed rating $R$ are same as CTR. Algorithm 3 lines 1–9 illustrate the DAE block and lines 10–19 illustrate the PMF block. The user-item pair $(i,j)$ does- Draw $R_{ij} \sim \mathcal{N}(u_i^T v_j, C_{ij}^{-1})$
```

#### Algorithm 3: Generative process of CDAE

1. for each layer $l \in L$ of SDAE do:
2. for each column $n$ of the weight matrix $\mathbf{W}_l$ do:
3. Draw $\mathbf{W}_{l,sn} \sim \mathcal{N}(0, \lambda_w^{-1}\mathbf{I}_K)$
4. end
5. Draw bias vector $\mathbf{b}_l \sim \mathcal{N}(0, \lambda_w^{-1}\mathbf{I}_K)$
6. for each row $j$ of $\mathbf{g}$ do:
7. Draw $g_{l,js} \sim \mathcal{N}(\sigma((g_{l,js})\mathbf{W}_l + \mathbf{b}_l), \lambda_D^{-1}\mathbf{I}_K)$
8. end
9. end
10. for each item $j \in J$ do:
11. Draw input $X_{0,j^*} \sim \mathcal{N}(g_{Lj,j^*}, \lambda_v^{-1}\mathbf{I}_J)$
12. Draw the latent offset vector $\epsilon_j \sim \mathcal{N}(0, \lambda_v^{-1}\mathbf{I}_K)$
13. Set latent vector as $\mathbf{v}_j = \epsilon_j + g_{Lj/2j^*}$
14. end
15. for each user $u \in U$ do:
16. Draw $u_i \sim \mathcal{N}(0, \lambda_u^{-1}\mathbf{I}_K)$
17. end
18. for each user-item pair $(i,j)$ do:
19. Draw $R_{ij} \sim \mathcal{N}(u_i^T v_j, C_{ij}^{-1})$
20. end
```

### 6.4.2 Collaborative variational autoencoder

Although CDAE is a powerful DL model that delivers excellent performance, it is not without faults. The denoising component works by corrupting the input, which degrades representations. Second, the DAE does not have a probabilistic approach; instead, it has a frequentist approach which makes it difficult to perform Bayesian inference. To overcome these limitations, Li et al. [14] propose a model called CVAE. The graphical structure of CVAE is represented in Figure 6.9 where the top part (the red box) indicates the VAE component and the bottom part represents the PMF component. First, VAE induces stochasticity in the latent Z, which results in better representations compared to deterministic. Second, the probabilistic VAE allows the model to seamlessly integrate with other generative models like PMF. The generative process of CVAE is shown in Algorithm 4.

#### Algorithm 4: Generative process of CVAE

```
1. for each layer $l \in L$ of VAE do:
2.   for each column $n$ of the weight matrix $\mathbf{W}_l$ do:
3.     Draw $\mathbf{W}_{l,sn} \sim \mathcal{N}(0, \lambda_w^{-1}\mathbf{I}_K)$
4.   end
5.   Draw bias vector $\mathbf{b}_l \sim \mathcal{N}(0, \lambda_w^{-1}\mathbf{I}_K)$
6.   for each row $j$ of $\mathbf{g}$ do:
7.     Draw $g_{l,js} \sim \mathcal{N}(\sigma(g_{l,js}\mathbf{W}_l + \mathbf{b}_l), \lambda_d^{-1}\mathbf{I}_K)$
8.   end
9. end
10. for each item $j \in J$ do:
11.   Draw input $X_{0,j^*} \sim \mathcal{N}(g_{Lj,j^*}, \lambda_v^{-1}\mathbf{I}_J)$
12.   Draw the latent offset vector $\epsilon_j \sim \mathcal{N}(0, \lambda_v^{-1}\mathbf{I}_K)$
13.   Set latent vector as $\mathbf{v}_j = \epsilon_j + g_{Lj/2j^*}$
14. end
15. for each item $j \in J$ do:
16.   Draw $\mu_j \sim \mathcal{N}(g_lW_\mu + b_\mu, \lambda_\mu^{-1}\mathbf{I}_K)$
17.   Draw $\Sigma_j \sim \mathcal{N}(g_lW_\sigma + b_\sigma, \lambda_\sigma^{-1}\mathbf{I}_K)$
18.   Draw $Z_j \sim \mathcal{N}(\mu, \Sigma)$
19. end
20. for each user-item pair $(i,j)$ do:
21.   Draw $R_{ij} \sim \mathcal{N}(u_i^T v_j, C_{ij}^{-1})$
22. end
```

**Parameter inference**: Essentially, there are two ways to learn the parameters of CVAE: (1) a partial VI or MAP estimate. Here, we restrict our explanation to the prior. For details on the full variational estimate, readers are suggested to refer to [14]. The central inference problem of CVAE is to learn the posterior distribution $P(Z, U, V|X, R)$. However, as is the case with LDA
