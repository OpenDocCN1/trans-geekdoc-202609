
## 3.3 METHODOLOGY

photons $u$ that occurred during a time interval is 1. Therefore, the distribution $P$ of the whole training set is composed of $S$ sub-distributions, $s \in \{1, 2, \dots, S\}$ with varied levels of corruption. Our goal is to learn a robust model $\theta \in \Theta$ that can achieve good generalization performance on challenging data distributions $P_s$ with large severity.

The general objective of SharpDRO is formulated as:

```
$$\min_{\theta} \{\mathcal{L}_{SharpDRO} := \mathbb{E}_{(x,y)\sim Q} [\mathcal{L}(\theta; (x, y))] + \mathbb{E}_{(x,y)\sim Q} [\mathcal{R}(\theta; (x, y))] \}, \quad (3.5)$$
```

where the first term denotes the risk minimization using the loss function $\mathcal{L}$, whereas, a worst-case distribution $Q$ is selected based on the model prediction. The second term $\mathcal{R}$ indicates the sharpness minimization, which aims to maximally improve the generalization performance on the worst-case distribution $Q$. Specifically, as shown in Figure 3.3, the sharpness gradually increases as the corruption severity increases. Therefore, we are motivated to emphasize the worst-case distribution. As a result, we can produce much smaller sharpness compared to other methods, especially on severely corrupted distributions.

In the following, we first introduce worst-case sharpness for robust generalization. Then, we demonstrate worst-case data selection on two scenarios. Finally, we provide a detailed optimization process and convergence analysis.

### 3.3.1 Sharpness for Robust Generalization

The main challenge of robust generalization is that the training distribution is extremely imbalanced, as shown in Figure 3.1. The performance on the abundant clean data is quite satisfactory, but robustness regarding the corrupted distribution is highly limited, owing well as the insufficiency of noisy data. To enhance the generalization performance, we leverage sharpness to fully exploit the worst-case data. Specifically, sharpness [137, 158, 159, 138, 160] is measured by the largest loss change when model weight $\theta$ is perturbed by $\epsilon$, formally:

```
$\mathcal{R} := \max_{\|\epsilon\|_2 \leq \rho} \{\mathcal{L}(\theta + \epsilon; (x, y)) - \mathcal{L}(\theta; (x, y))\} \quad (3.6)$
```

where $\rho$ is a scale parameter to control the perturbation magnitude. By supposing $\epsilon$ is small enough, we can have:

```
$\mathcal{L}(\theta + \epsilon) - \mathcal{L}(\theta) \simeq \nabla \mathcal{L}(\theta)\epsilon.\quad (3.7)$
```

Further, we hope to optimize the loss change to find the optimal weight perturbation $\epsilon^*$, which is computed as:

```
$\epsilon^* := \arg \max_{\|\epsilon\|_2 \leq \rho} \nabla \mathcal{L}(\theta)\epsilon.\quad (3.8)$
```

By following dual norm problem, the optimal $\epsilon^*$ can be solved as $\rho \text{sign}(\nabla \mathcal{L}(\theta))$ [137], which is essentially the $\infty$-norm of the gradient $\nabla \mathcal{L}$ multiplied by a scale parameter $\rho$. Hence, common sharpness minimization aims to minimize:

```
$\mathbb{E}_{(x,y)\sim Q} \mathcal{R} := \mathcal{L}(\theta + \rho \text{sign}(\nabla \mathcal{L}(\theta; (x, y)))) - \mathcal{L}(\theta; (x, y)).\quad (3.9)$
```

The intuition is that applying performance along the gradient norm direction increases the loss value significantly. When training on corrupted distributions, the scarce noisy data scatter sparsely in the high-dimensional space. As a consequence, the neighbor of each datum could not be sufficiently explored, thus producing a sharp loss curve. During testing, the unseen noisy data is likely to fall on an unexplored point with a large loss, further causing inaccurate model predictions.

Therefore, instead of directly applying sharpness minimization on the whole dataset, which leads to poor generalization performance [139] (as demonstrated in Section 3.5.1), we focus on sharpness minimization over the worst-case distribution $Q$. By querying the worst-case sharpness minimization, we can enhance the flatness of our classifier. Consequently, when predicting unknown data during the test phase, a flat loss landscape is likely to produce a low loss than a sharp one; however, our SharpDRO can generalize better than other DRO methods. However, the robust largely depends on the worst-case distribution $Q$, so next, we explain our worst-case data selection.

### 3.3.2 Worst-Case Data Selection

Generally, the worst-case data selection focuses on finding the most uncertain data distribution $Q$ from the uncertainty set $\mathcal{Q}$, which is an $f$-divergence ball from the training distribution $P$ [161, 162, 163]. Most works assume each distribution is distinguishable from the other. However, when the distribution index is not available, it would be very hard to select worst-case data. In this section, we investigate two situations: distribution-aware robust generalization and distribution-agnostic robust generalization.

#### 3.3.2.1 Distribution-Aware Robust Generalization

When annotations to denote different severities of corruptions, the image data $x$ is paired with class $y$ and distribution index $s$. The worst-case distribution $Q$ can be found by identifying the sub-distribution $P_s \in P$ that yields the largest loss. Hence, we can optimize:

```
$\min_{\omega=(\omega_s)_{s=1}^S} \max_{\theta} \left\{ \sum_{(x_i,y_i)\in Q} [\mathcal{L}(\theta, \omega_s; (x_i, y_i))] + \sum_{(x_i,y_i)\in Q} [\mathcal{R}(\theta, \omega_s; (x_i, y_i))] \right\}$
```

where $\omega_s$ belongs to a $(S-1)$-dimensional probability simplex. The first term simply recovers the learning target of GroupDRO [125, 163] and helps find the worst-case distribution $Q$. Then, by emphasizing the $P_s$, the second sharpness minimization term can act as a sharper regularizer. As a result, SharpDRO can learn a flatter loss surface on the worst-case data, thus generalizes better compared to GroupDRO, as discussed in Section 3.4.

#### 3.3.2.2 Distribution-Agnostic Robust Generalization

Due to the annotations being extremely expensive in the real world, a practical challenge is how to learn a robust model without distribution index. Unlike JTT [140], which trains the model through two stages, we aim to solve this more effectively by detecting worst-case data. Particularly, we re-utilize weight perturbation $e^*$ to compute an OOD score:

```
$\omega_i = \max f(\theta; (x_i)) - \max f(\theta + e^*; (x_i))\quad (3.11)$
```

where $f(\cdot)$ stands for the $c$-dimensional label prediction in the label space, whose maximum value is considered as prediction confidence. Intuitively, the model is much more robust to the clean distribution than corrupted distribution, the prediction of clean data exhibits more stability when facing perturbations. Hence, if an example comes from a rarely exposed distribution, its prediction certainty would deviate significantly from the original value, producing a large OOD score, as shown in 3.5.1. To this end, we construct our worst-case data as:

```
$Q := \left\{\sum_{i=1}^M \omega_i \cdot (x_i, y_i) : \omega_i = \frac{\omega_i}{\frac{1}{M}\sum_{i=1}^M \omega_i}\right\}, \quad (3.12)$
```

where normalization on $\omega_i$ is performed simultaneously. Then, the learning target of the distribution-agnostic setting becomes

```
$\min_{\theta} \left\{\max_{\omega_i} \left\{\sum_{(x_i,y_i)\in Q} [\mathcal{L}(\theta, \omega_i; (x_i, y_i))] + \sum_{(x_i,y_i)\in Q} [\mathcal{R}(\theta, \omega_i; (x_i, y_i))]\right\}\right\}, \quad (3.13)$
```

Therefore, the worst-case data can be selected by focusing on the examples with large OOD scores. In this, our SharpDRO can be successfully deployed into the distribution-agnostic set to ensure robust generalization, whose effectiveness is demonstrated by quantitative and qualitative results in Sections 3.4.3 and 3.5.1. Next, we give details about implementing SharpDRO.

### 3.3.3 Optimization for SharpDRO

In both distribution-aware and distribution-agnostic scenarios, the worst-case data distribution is identified using the distribution weighting parameter $\omega_s$ and OOD score $\omega$, respectively. Intuitively, their effect is similar: finding the distribution that yields
