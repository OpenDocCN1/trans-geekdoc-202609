where $\mathcal{X}$ is the space of feasible physical adversarial examples, $t$ is a transformation function drawn from $\mathcal{T}$, $g$ is the attack objective loss function as introduced in Chapter 2, and $r$ is the regularizer (e.g., a penalty function on unrealizable printing colors).

The optimization objective of EOT attack can be viewed as minimizing the average loss over all data transformations in $\mathcal{T}$. Instead of minimizing the average loss, Wang et al. (2021a) proposed a MinMax attack formulation that optimizes the worst-case transformation loss through

$\min_{\boldsymbol{x}\in\mathcal{X}} \max_{\boldsymbol{w}\in\mathcal{P}} \sum_{i=1}^K w_i \cdot g(t_i(\boldsymbol{x})) - \gamma \|\boldsymbol{w} - \mathbf{1}/K\|_2^2 + r(\boldsymbol{x}), \quad (4.2)$

where $K$ is the number of transformations in $\mathcal{T}$, $\boldsymbol{w}$ is a nonnegative $K$-dimensional vector in the probability simplex $\mathcal{P}$ satisfying $\sum_{i=1}^K w_i = 1$, $t_i$ is the $i$th transformation with $w_i$ being its weighting factor, $\mathbf{1}/K$ is a uniform vector, and $\gamma \ge 0$ is a regularization coefficient. If $\boldsymbol{w} = \mathbf{1}/K$, then problem (4.2) reduces to the existing EOT formulation. Using the alternating one-step projected gradient descent–ascent (APGDA) algorithm for solving (4.2), it is shown by Wang et al. (2021a) that MinMax attack leads to more robust adversarial examples against multiple data transformations than EOT. MinMax attack also offers some interpretation on the difficulty level of each transformation through the associated learned weighting factor $\{w_i\}_{i=1}^K$ while solving the min–max optimization problem. It is also used by Xu et al. (2020c) in the design of physical adversarial T-shirts that are robust to nonrigid deformations.

# 4.2 Examples of physical adversarial attacks

Here we list some studies into crafting physical adversarial examples in different scenarios. Some of the physical adversarial examples are shown in Fig. 4.1.

+   Adversarial photo (Kurakin et al., 2016): Demonstration that when feeding adversarial images obtained from cell-phone camera to an ImageNet Inception classifier, a large fraction of adversarial examples are classified incorrectly even when perceived through the camera.

+   Adversarial eyeglasses (Sharif et al., 2016): Realization through printing a pair of eyeglass frames such that when worn by the attacker whose image is supplied to a face-recognition algorithm, the eyeglasses allow her to evade being recognized or to impersonate another individual.